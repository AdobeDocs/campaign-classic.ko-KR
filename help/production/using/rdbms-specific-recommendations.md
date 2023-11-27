---
product: campaign
title: RDBMS 특정 권장 사항
description: RDBMS 특정 권장 사항
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
badge-v7-prem: label="온-프레미스 및 하이브리드" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: a586d70b-1b7f-47c2-a821-635098a70e45
source-git-commit: 624978901943b4c74f50c20298c9596f73b25b1b
workflow-type: tm+mt
source-wordcount: '1256'
ht-degree: 3%

---

# RDBMS 특정 권장 사항{#rdbms-specific-recommendations}



유지 관리 계획을 설정하는 데 도움이 되도록 이 섹션에는 Adobe Campaign이 지원하는 다양한 RDBMS 엔진에 적용되는 몇 가지 권장 사항과 모범 사례가 나와 있습니다. 하지만 이는 권장 사항일 뿐입니다. 내부 절차와 제약 조건을 준수하면서 필요에 맞게 조정하는 것은 여러분에게 달려 있습니다. 데이터베이스 관리자는 이러한 계획을 작성하고 실행할 책임이 있습니다.

## PostgreSQL {#postgresql}

### 큰 테이블 검색 중 {#detecting-large-tables}

1. 데이터베이스에 다음 뷰를 추가할 수 있습니다.

   ```
   create or replace view uvSpace
    as
    SELECT c1.relname AS tablename, c2.relname AS indexname, c2.relpages * 8 / 1024 AS size_mbytes, c2.relfilenode AS filename, 0 AS row_count
    FROM pg_class c1, pg_class c2, pg_index i
    WHERE c1.oid = i.indrelid AND i.indexrelid = c2.oid
    UNION 
    SELECT pg_class.relname AS tablename, NULL::"unknown" AS indexname, pg_class.relpages * 8 / 1024 AS size_mbytes, pg_class.relfilenode AS filename, cast(pg_class.reltuples as integer) AS row_count
    FROM pg_class
    WHERE pg_class.relkind = 'r'::"char"
    ORDER BY 3 DESC, 1, 2 DESC;
   ```

1. 이 쿼리를 실행하여 큰 테이블과 색인을 찾을 수 있습니다.

   ```
   SELECT * FROM uvSpace;
   ```

   또는 예를 들어 이 쿼리를 실행하여 모든 색인 크기를 집합적으로 볼 수 있습니다.

   ```
   SELECT
      tablename,
      sum(size_mbytes) AS "sizeMB_all",
      (
         SELECT sum(size_mbytes)
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_data",
      (
         SELECT sum(size_mbytes)
         FROM uvspace 
         AS uv2 
         WHERE
            INDEXNAME IS NOT NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_index",
      (
         SELECT ROW_COUNT
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS ROWS FROM uvspace AS uv1
      GROUP BY tablename
      ORDER BY 2 DESC
   ```

### 간단한 유지 관리 {#simple-maintenance}

>[!IMPORTANT]
>
>Adobe은 Campaign Adobe이 호스팅하는 데이터베이스 설정에서 VACUUM FULL을 실행하지 않도록 강력히 제안합니다. 제안된 유지 관리 지침은 온-프레미스 설치에만 해당됩니다. 사용자 지정 테이블 구현 및 스키마의 경우 VACUUM이 모니터링 없이 정지된 쿼리를 발생시키는 테이블만 잠글 수 있으므로 자체 위험이 있는 VACUUM FULL을 사용합니다. 경우에 따라 전체 데이터베이스를 잠글 수 있습니다.

PostgreSQL에서는 다음과 같은 일반적인 키워드를 사용할 수 있습니다.

* 진공(가득 참, 분석, 장황함)

VACUUM 작업을 실행하고 분석하고 시간을 지정하려면 다음 구문을 사용할 수 있습니다.

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) <table>;
```

ANALYZE 문을 생략하지 않는 것이 좋습니다. 그렇지 않으면 빈 테이블이 통계 없이 유지됩니다. 그 이유는 새 테이블을 만든 다음 이전 테이블을 삭제하기 때문입니다. 따라서 테이블의 OID(객체 ID)는 변경되지만 통계는 계산되지 않습니다. 따라서 성능 문제가 즉시 발생합니다.

다음은 정기적으로 실행되는 SQL 유지 관리 계획의 일반적인 예입니다.

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdelivery;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverystat;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflow;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowevent;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowlog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowtask;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjoblog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsaddress;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverypart;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe은 작은 테이블로 시작하는 것을 권장합니다. 이런 식으로, 프로세스가 큰 테이블(실패 위험이 가장 높은 테이블)에서 실패할 경우 적어도 일부의 유지 관리가 완료되었습니다.
>* Adobe은 중요 업데이트가 발생할 수 있는 데이터 모델에 특정한 테이블을 추가할 것을 권장합니다. 다음과 같은 경우에 해당됩니다. **NmsRecipient** 일별 데이터 복제 흐름이 큰 경우.
>* VACUUM 문은 유지 관리가 수행되는 동안 일부 프로세스를 일시 중지하는 테이블을 잠급니다.
>* 매우 큰 테이블(일반적으로 5Gb 이상)의 경우 VACUUM FULL 문은 매우 비효율적이며 시간이 오래 걸릴 수 있습니다. Adobe은 다음 작업에 사용하지 않는 것이 좋습니다. **YyyNmsBroadLogXxx** 테이블.
>* 이 유지 관리 작업은 Adobe Campaign 워크플로에서 **[!UICONTROL SQL]** 활동. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/architecture.md)을 참조하십시오. 백업 윈도우와 충돌하지 않는 짧은 작업 시간 동안 유지 관리를 예약해야 합니다.
>

### 데이터베이스 재구축 {#rebuilding-a-database}

PostgreSQL은 VACUUM FULL 문이 테이블을 잠그므로 온라인 테이블 재구성을 수행하는 쉬운 방법을 제공하지 않으므로 일반 프로덕션을 수행할 수 없습니다. 이는 표를 사용하지 않을 때 유지 관리를 수행해야 함을 의미한다. 다음 중 하나를 수행할 수 있습니다.

* Adobe Campaign 플랫폼이 중지되면 유지 관리를 수행합니다.
* 다시 작성 중인 테이블에 작성할 수 있는 다양한 Adobe Campaign 하위 서비스 중지(**nlserver stop wfserver instance_name** (워크플로 프로세스를 중지하려면)

다음은 필요한 DDL을 생성하기 위해 특정 함수를 사용하는 테이블 조각 모음의 예입니다. 다음 SQL을 사용하여 두 개의 새 함수를 생성할 수 있습니다. **GenRebuildTablePart1** 및 **GenRebuildTablePart2**: 테이블을 다시 만드는 데 필요한 DDL을 생성하는 데 사용할 수 있습니다.

* 첫 번째 기능을 사용하면 원래 테이블의 복사본인 작업 테이블(** _tmp**을 만들 수 있습니다.
* 그런 다음 두 번째 함수는 원래 테이블을 삭제하고 작업 테이블과 해당 인덱스의 이름을 바꿉니다.
* 한 함수 대신 두 함수를 사용한다는 것은 첫 번째 함수가 실패하면 원래 테이블을 삭제할 위험이 없다는 것을 의미합니다.

```
 -- --------------------------------------------------------------------------
 -- Generate the CREATE TABLE DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenTableDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecFld RECORD;
 vstrDDL text;
 vstrFields text;
 vstrNsTable text;
 vstrTableSpace text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 SELECT
 pg_catalog.quote_ident(n.nspname) || '.' || pg_catalog.quote_ident(c.relname),
 pg_catalog.quote_ident(t.spcname)
 INTO
 vstrNsTable, vstrTableSpace
 FROM
 pg_namespace n, pg_class c left outer join pg_tablespace t on c.reltablespace = t.oid
 WHERE
 n.oid = c.relnamespace AND
 c.relname = vstrTable;
 
 vstrDDL = 'CREATE TABLE ' || vstrNsTable || '_tmp(';
 
 vstrFields = ;
 FOR vrecFld IN
 SELECT
 pg_catalog.quote_ident(a.attname) ||
 ' ' || t.typname ||
 case when t.typname='varchar' then '(' || cast(a.atttypmod-4 as text) || ')'
 when t.typname='numeric' then '(' || cast((a.atttypmod-4)/65536 as text) || ',' || cast((a.atttypmod-4)%65536 as text) || ')'
 else end ||
 case when a.attnotnull then ' not null' else end ||
 case when a.atthasdef then ' default '|| d.adsrc else end as DDL
 FROM
 pg_type t, pg_class c, pg_attribute a LEFT OUTER JOIN pg_attrdef d ON d.adrelid=a.attrelid and d.adnum=a.attnum
 WHERE 
 a.attnum > 0 AND
 a.attrelid = c.oid AND
 t.oid = a.atttypid AND
 c.relname = vstrTable
 ORDER BY
 a.attnum
 LOOP
 IF vstrFields <> THEN
 vstrFields = vstrFields || ',' || chr(10) || ' ';
 ELSE
 vstrFields = vstrFields || chr(10) || ' ';
 END IF;
 vstrFields = vstrFields || vrecFld.DDL;
 END LOOP;
 
 vstrDDL = vstrDDL || vstrFields || chr(10) || ')';
 if vstrTableSpace <> then
 vstrDDL = vstrDDL || ' TABLESPACE ' || vstrTableSpace;
 end if;
 vstrDDL = vstrDDL || ';' || chr(10);
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the CREATE INDEX DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 viFld integer;
 vstrFld text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
 SELECT
 i.indkey, i.indisunique,
 pg_catalog.quote_ident(c.relname) as tablename,
 pg_catalog.quote_ident(ic.relname) as indexname,
 pg_catalog.quote_ident(t.spcname) as tablespace
 FROM
 pg_class c, pg_index i, pg_class ic left outer join pg_tablespace t on ic.reltablespace = t.oid
 WHERE
 i.indexrelid = ic.oid AND
 i.indrelid = c.oid AND
 c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'CREATE ';
  if vrecIndex.indisunique then
  vstrDDL = vstrDDL || 'UNIQUE ';
  end if;
  vstrDDL = vstrDDL ||
   'INDEX ' ||vrecIndex.indexname || '_tmp ON ' ||
   vrecIndex.tablename || '_tmp(';
 
  FOR viFld IN array_lower(vrecIndex.indkey, 1) .. array_upper(vrecIndex.indkey, 1) LOOP
  SELECT pg_catalog.quote_ident(a.attname) INTO vstrFld 
  FROM 
   pg_attribute a, pg_class c
  WHERE 
   a.attnum = vrecIndex.indkey[viFld] AND
   a.attrelid = c.oid AND c.relname=vstrTable;
  
  vstrDDL = vstrDDL || vstrFld;
  if viFld <> array_upper(vrecIndex.indkey, 1) then
   vstrDDL = vstrDDL || ', ';
  end if;
  END LOOP;
  vstrDDL = vstrDDL || ')';
 
  if vrecIndex.tablespace <> then
  vstrDDL = vstrDDL || 'TABLESPACE ' || vrecIndex.tablespace;
  end if;
  vstrDDL = vstrDDL || ';' || chr(10);
 
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the ALTER INDEX RENAME for a table
 -- --------------------------------------------------------------------------
 create or replace function GenRenameIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
  SELECT
  pg_catalog.quote_ident(n.nspname) as namespace,
  pg_catalog.quote_ident(ic.relname) as indexname
  FROM
  pg_namespace n, pg_class c, pg_index i, pg_class ic
  WHERE
  i.indexrelid = ic.oid AND
  n.oid = ic.relnamespace AND
  i.indrelid = c.oid AND
  c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'ALTER INDEX ' || vrecIndex.namespace || '.' || vrecIndex.indexname ||
    '_tmp RENAME TO ' || vrecIndex.indexname ||
    ';' || chr(10);
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Build a copy of a table, with index
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart1(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = ;
 
 SELECT GenTableDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 vstrDDL = vstrDDL|| 'INSERT INTO ' || vstrTable || '_tmp SELECT * FROM ' || vstrTable || ';'||chr(10);
 SELECT GenIndexDDL(vstrTable) INTO vstrTmp;
 
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 vstrDDL = vstrDDL|| 'VACUUM ANALYSE '|| vstrTable || '_tmp;' ||chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
 
 -- --------------------------------------------------------------------------
 -- Drop the original table and rename the copy
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart2(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = 'DROP TABLE ' || vstrTable||';'|| chr(10);
 vstrDDL = vstrDDL|| 'ALTER TABLE ' || vstrTable || '_tmp RENAME TO ' || vstrTable ||';'|| chr(10);
 
 SELECT GenRenameIndexDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
```

다음 예제는 워크플로우에서 를 사용하는 대신 필요한 테이블을 다시 빌드하는 데 사용할 수 있습니다. **진공/다시 빌드** 명령:

```
function sqlGetMemo(strSql)
 {
 var res = sqlSelect("s, m:memo", strSql);
 return res.s.m.toString();
 }

 function RebuildTable(strTable)
 {
 // Rebuild a table_tmp
 var strSql = sqlGetMemo("select GenRebuildTablePart1('"+strTable+"')");
 logInfo("Rebuilding table '"+strTable+"'...");
 // logInfo(strSql);
 sqlExec(strSql);
 
 // If fails, there is an exception thrown and so we do not delete the original table
 strSql = sqlGetMemo("select GenRebuildTablePart2('"+strTable+"')");
 logInfo("Swapping table '"+strTable+"'...");
 //logInfo(strSql);
 sqlExec(strSql);
 }
 
 RebuildTable('nmsrecipient');
 RebuildTable('nmsrcpgrlrel');
 // ... other tables here
```

## Oracle {#oracle}

사용 중인 Oracle 버전에 가장 적합한 절차에 대해 알아보려면 데이터베이스 관리자에게 문의하십시오.

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>Microsoft SQL Server의 경우 다음에서 자세히 설명하는 유지 관리 계획을 사용할 수 있습니다. [이 페이지](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html).

아래 예제는 Microsoft SQL Server 2005입니다. 다른 버전을 사용하는 경우 데이터베이스 관리자에게 문의하여 유지 관리 절차에 대해 알아보십시오.

1. 먼저 관리자 권한이 있는 로그인을 사용하여 Microsoft SQL Server Management Studio에 연결합니다.
1. 로 이동 **[!UICONTROL Management > Maintenance Plans]** 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Maintenance Plan Wizard]**.
1. 클릭 **[!UICONTROL Next]** 첫 번째 페이지가 나타나면
1. 생성할 유지 관리 계획 유형(각 작업에 대한 별도의 스케줄 또는 전체 계획에 대한 단일 스케줄)을 선택한 다음 **[!UICONTROL Change...]** 단추를 클릭합니다.
1. 다음에서 **[!UICONTROL Job schedule properties]** 창에서 원하는 실행 설정을 선택하고 **[!UICONTROL OK]**&#x200B;을 클릭한 다음 을 클릭합니다 **[!UICONTROL Next]**.
1. 수행할 유지 관리 작업을 선택한 다음 **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >아래 표시된 유지 관리 작업 이상을 수행하는 것이 좋습니다. 통계 업데이트 작업은 데이터베이스 정리 워크플로우에서 이미 수행되었지만 선택할 수도 있습니다.

1. 드롭다운 목록에서 를 실행할 데이터베이스를 선택합니다 **[!UICONTROL Database Check Integrity]** 작업.
1. 데이터베이스를 선택하고 **[!UICONTROL OK]**&#x200B;을 클릭한 다음 을 클릭합니다 **[!UICONTROL Next]**.
1. 데이터베이스에 할당된 최대 크기를 구성한 다음 **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >데이터베이스 크기가 이 임계값을 초과하는 경우 유지 관리 계획에서 사용하지 않는 데이터를 삭제하여 공간을 확보합니다.

1. 인덱스 재구성 또는 재구축:

   * 지수 단편화율이 10%에서 40% 사이이면 개편을 권고하고 있다.

     재구성할 데이터베이스 및 개체(테이블 또는 뷰)를 선택한 다음 **[!UICONTROL Next]**.

     >[!NOTE]
     >
     >구성에 따라 이전에 선택한 테이블이나 데이터베이스의 모든 테이블을 선택할 수 있습니다.

   * 인덱스 단편화 비율이 40%보다 높으면 다시 빌드하는 것이 좋습니다.

     인덱스 다시 작성 작업에 적용할 옵션을 선택한 다음 **[!UICONTROL Next]**.

     >[!NOTE]
     >
     >인덱스 재구축 프로세스는 프로세서 사용 측면에서 더 엄격하며 데이터베이스 리소스를 잠급니다. 다음 항목 선택 **[!UICONTROL Keep index online while reindexing]** 다시 작성 중에 인덱스를 사용할 수 있도록 하려면 옵션을 선택합니다.

1. 활동 보고서에 표시할 옵션을 선택한 다음 를 클릭합니다 **[!UICONTROL Next]**.
1. 유지 관리 계획에 대해 구성된 작업 목록을 확인한 다음 **[!UICONTROL Finish]**.

   유지 관리 계획 및 여러 단계의 상태에 대한 요약이 표시됩니다.

1. 유지 관리 계획이 완료되면 다음을 클릭하십시오. **[!UICONTROL Close]**.
1. Microsoft SQL Server 탐색기에서 **[!UICONTROL Management > Maintenance Plans]** 폴더를 삭제합니다.
1. Adobe Campaign 유지 관리 계획을 선택합니다. 여러 단계가 워크플로우에 자세히 설명되어 있습니다.

   에서 개체가 생성되었습니다. **[!UICONTROL SQL Server Agent > Jobs]** 폴더를 삭제합니다. 이 객체를 사용하여 유지 관리 계획을 시작할 수 있습니다. 이 예제에서는 모든 유지 관리 작업이 동일한 플랜의 일부이므로 하나의 객체만 있습니다.

   >[!IMPORTANT]
   >
   >이 개체를 실행하려면 Microsoft SQL Server 에이전트를 사용하도록 설정해야 합니다.

**작업 테이블에 대해 별도의 데이터베이스 구성**

>[!NOTE]
>
>이 구성은 선택 사항입니다.

다음 **WdbcOptions_TempDbName** 옵션을 사용하면 Microsoft SQL Server의 작업 테이블에 대해 별도의 데이터베이스를 구성할 수 있습니다. 따라서 백업 및 복제 작업이 최적화됩니다.

이 옵션은 작업 테이블(예: 워크플로우 실행 중에 생성된 테이블)을 다른 데이터베이스에 작성하려는 경우 사용할 수 있습니다.

옵션을 &quot;tempdb.dbo.&quot;로 설정하면 작업 테이블이 Microsoft SQL Server의 기본 임시 데이터베이스에 만들어집니다. 데이터베이스 관리자는 tempdb 데이터베이스에 대한 쓰기 액세스를 허용해야 합니다.

이 옵션을 설정하면 Adobe Campaign에 구성된 모든 Microsoft SQL Server 데이터베이스(주 데이터베이스 및 외부 계정)에서 이 옵션이 사용됩니다. 두 외부 계정이 동일한 서버를 공유하는 경우 tempdb가 고유하므로 충돌이 발생할 수 있습니다. 같은 방식으로 두 Campaign 인스턴스가 동일한 MSSQL 서버를 사용하는 경우 동일한 tempdb를 사용하는 경우 충돌이 발생할 수 있습니다.
