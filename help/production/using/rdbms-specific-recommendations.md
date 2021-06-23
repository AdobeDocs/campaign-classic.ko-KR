---
product: campaign
title: RDBMS 특정 권장 사항
description: RDBMS 특정 권장 사항
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: a586d70b-1b7f-47c2-a821-635098a70e45
source-git-commit: 0e0912c68d132919eeac9b91b93960e70011153e
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 1%

---

# RDBMS 특정 권장 사항{#rdbms-specific-recommendations}

유지 관리 계획을 설정하는 데 도움이 되도록 이 섹션에는 Adobe Campaign에서 지원하는 다양한 RDBMS 엔진에 맞는 몇 가지 권장 사항과 모범 사례가 나와 있습니다. 하지만 이는 권장 사항일 뿐입니다. 내부 절차와 제한 조건을 유지하면서 필요에 맞게 조정하는 것은 여러분에게 달려 있습니다. 데이터베이스 관리자는 이러한 계획을 작성하고 실행할 책임이 있습니다.

## PostgreSQL {#postgresql}

### 큰 테이블 검색 {#detecting-large-tables}

1. 데이터베이스에 다음 보기를 추가할 수 있습니다.

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

1. 이 쿼리를 실행하여 큰 테이블 및 인덱스를 찾을 수 있습니다.

   ```
   SELECT * FROM uvSpace;
   ```

   또는 이 쿼리를 실행하여 모든 인덱스 크기를 전체적으로 확인할 수 있습니다.

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

### 간편한 유지 관리 {#simple-maintenance}

PostgreSQL에서는 다음과 같은 일반적인 키워드를 사용할 수 있습니다.

* 진공(전체, 분석, 세부 정보)
* 다시 색인화

VACUUM 작업을 실행하고 분석 및 시간을 수행하려면 다음 구문을 사용할 수 있습니다.

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) <table>;
```

ANALYZE 문을 생략하지 않는 것이 좋습니다. 그렇지 않으면, 진공 테이블은 통계가 없는 상태로 남게 됩니다. 이유는 새 테이블이 만들어진 후 이전 테이블이 삭제되기 때문입니다. 따라서 테이블의 OID(객체 ID)가 변경되지만 통계가 계산되지 않습니다. 따라서 즉시 성능 문제가 발생합니다.

다음은 정기적으로 실행되는 SQL 유지 관리 계획의 일반적인 예입니다.

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdelivery;
REINDEX TABLE nmsdelivery;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverystat;
REINDEX TABLE nmsdeliverystat;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflow;
REINDEX TABLE xtkworkflow;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowevent;
REINDEX TABLE xtkworkflowevent;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowjob;
REINDEX TABLE xtkworkflowjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowlog;
REINDEX TABLE xtkworkflowlog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowtask;
REINDEX TABLE xtkworkflowtask;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjoblog;
REINDEX TABLE xtkjoblog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjob;
REINDEX TABLE xtkjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsaddress;
REINDEX TABLE nmsaddress;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverypart;
REINDEX TABLE nmsdeliverypart;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsmirrorpageinfo;
REINDEX TABLE nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe은 더 작은 표로 시작하는 것이 좋습니다.이 방법으로 큰 테이블에서 프로세스가 실패하는 경우(실패 위험이 가장 높은 경우) 유지 관리의 적어도 일부가 완료되었습니다.
>* Adobe은 데이터 모델에 해당하는 테이블을 추가하여 중요한 업데이트를 적용할 수 있습니다. 일별 데이터 복제 흐름이 큰 경우 **NmsRecipient**&#x200B;에 해당할 수 있습니다.
>* VACUUM 및 REINDEX 문은 테이블을 잠가 유지 관리가 수행되는 동안 일부 프로세스를 일시 중지합니다.
>* 매우 큰 테이블(일반적으로 5Gb 이상)의 경우, INVACUM FULL 문은 매우 비효율적이고 오랜 시간이 걸릴 수 있습니다. Adobe은 **YyyNmsBroadLogXxx** 테이블에 사용하지 않는 것이 좋습니다.
>* 이 유지 관리 작업은 **[!UICONTROL SQL]** 활동을 사용하여 Adobe Campaign 워크플로우에서 구현할 수 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/architecture.md)을 참조하십시오. 백업 윈도우와 충돌하지 않는 낮은 작업 시간에 대한 유지 관리를 예약해야 합니다.

>



### 데이터베이스 다시 구축 {#rebuilding-a-database}

PostgreSQL은 INVACUUM FULL 문이 테이블을 잠근 상태이므로 온라인 테이블 재작성을 수행하는 쉬운 방법을 제공하지 않으므로, 일반 생산이 방지됩니다. 즉, 테이블을 사용하지 않을 때는 유지 관리를 수행해야 합니다. 다음 중 하나를 수행할 수 있습니다.

* Adobe Campaign 플랫폼이 중지되면 유지 관리를 수행합니다.
* 다시 빌드하고 있는 표에 쓸 수 있는 다양한 Adobe Campaign 하위 서비스를 중지합니다(**nlserver stop wfserver instance_name**).

다음은 필요한 DDL을 생성하기 위해 특정 함수를 사용하는 테이블 조각 모음의 예입니다. 다음 SQL을 사용하면 두 개의 새 함수를 만들 수 있습니다.**GenRebuildTablePart1** 및 **GenRebuildTablePart2**&#x200B;를 사용하여 테이블을 다시 작성하는 데 필요한 DDL을 생성하는 데 사용할 수 있습니다.

* 첫 번째 함수를 사용하면 원래 테이블의 복사본인 작업 테이블(**_tmp** 여기)을 만들 수 있습니다.
* 그런 다음 두 번째 함수는 원래 테이블을 삭제하고 작업 테이블과 해당 인덱스의 이름을 변경합니다.
* 한 함수 대신 두 함수를 사용하면 첫 번째 함수가 실패하면 원래 테이블을 삭제할 위험이 없습니다.

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

다음 예제에서는 워크플로우에서 **진공/rebuild** 명령을 사용하지 않고 필요한 테이블을 다시 빌드할 수 있습니다.

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

사용 중인 Oracle 버전에 가장 적합한 절차에 대해서는 데이터베이스 관리자에게 문의하십시오.

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>Microsoft SQL Server의 경우 [이 페이지](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html)에 자세히 설명된 유지 관리 계획을 사용할 수 있습니다.

아래 예제는 Microsoft SQL Server 2005입니다. 다른 버전을 사용 중인 경우 데이터베이스 관리자에게 문의하여 유지 관리 절차에 대해 알아보십시오.

1. 먼저 Microsoft SQL Server Management Studio에 연결하여 관리자 권한을 사용하여 로그인합니다.
1. **[!UICONTROL Management > Maintenance Plans]** 폴더로 이동하여 해당 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Maintenance Plan Wizard]** 을 선택합니다.
1. 첫 번째 페이지가 나타나면 **[!UICONTROL Next]** 을 클릭합니다.
1. 생성할 유지 관리 계획 유형(각 작업에 대해 별도의 일정 또는 전체 계획에 대한 단일 일정)을 선택한 다음 **[!UICONTROL Change...]** 버튼을 클릭합니다.
1. **[!UICONTROL Job schedule properties]** 창에서 원하는 실행 설정을 선택하고 **[!UICONTROL OK]** 를 클릭한 다음 **[!UICONTROL Next]** 를 클릭합니다.
1. 수행할 유지 관리 작업을 선택한 다음 **[!UICONTROL Next]** 을 클릭합니다.

   >[!NOTE]
   >
   >아래에 표시된 유지 관리 작업 이상을 수행하는 것이 좋습니다. 통계 업데이트 작업은 데이터베이스 정리 워크플로우에서 이미 수행되지만 선택할 수도 있습니다.

1. 드롭다운 목록에서 **[!UICONTROL Database Check Integrity]** 작업을 실행할 데이터베이스를 선택합니다.
1. 데이터베이스를 선택하고 **[!UICONTROL OK]** 을 클릭한 다음 **[!UICONTROL Next]** 를 클릭합니다.
1. 데이터베이스에 할당된 최대 크기를 구성한 다음 **[!UICONTROL Next]**&#x200B;을 클릭합니다.

   >[!NOTE]
   >
   >데이터베이스 크기가 이 임계값을 초과하는 경우 유지 관리 계획에서 사용하지 않은 데이터를 삭제하여 공간을 확보하려고 합니다.

1. 인덱스를 재구성하거나 다시 작성합니다.

   * 인덱스 단편화 비율이 10%와 40% 사이인 경우 재구성이 권장됩니다.

      재구성할 데이터베이스 및 개체(테이블 또는 뷰)를 선택한 다음 **[!UICONTROL Next]**&#x200B;을 클릭합니다.

      >[!NOTE]
      >
      >구성에 따라 이전에 선택한 테이블 또는 데이터베이스의 모든 테이블을 선택할 수 있습니다.

   * 인덱스 단편화 비율이 40%보다 높은 경우 다시 작성하는 것이 좋습니다.

      인덱스 다시 작성 작업에 적용할 옵션을 선택한 다음 **[!UICONTROL Next]**&#x200B;을 클릭합니다.

      >[!NOTE]
      >
      >인덱스 재구축 프로세스는 프로세서 사용 측면에서 더욱 제한적이며 데이터베이스 리소스를 잠급니다. 다시 작성하는 동안 인덱스를 사용할 수 있도록 하려면 **[!UICONTROL Keep index online while reindexing]** 옵션을 선택합니다.

1. 활동 보고서에 표시할 옵션을 선택한 다음 **[!UICONTROL Next]** 을 클릭합니다.
1. 유지 관리 계획에 대해 구성된 작업 목록을 확인한 다음 **[!UICONTROL Finish]** 을 클릭합니다.

   유지 관리 계획 및 여러 단계의 상태에 대한 요약이 표시됩니다.

1. 유지 관리 계획이 완료되면 **[!UICONTROL Close]** 을 클릭합니다.
1. Microsoft SQL Server 탐색기에서 **[!UICONTROL Management > Maintenance Plans]** 폴더를 두 번 클릭합니다.
1. Adobe Campaign 유지 관리 계획을 선택합니다.다양한 단계는 워크플로우에 자세히 설명되어 있습니다.

   **[!UICONTROL SQL Server Agent > Jobs]** 폴더에 개체가 생성되었습니다. 이 개체를 사용하면 유지 관리 계획을 시작할 수 있습니다. 이 예제에서는 모든 유지 관리 작업이 동일한 계획의 일부이므로 개체가 하나만 있습니다.

   >[!IMPORTANT]
   >
   >이 개체를 실행하려면 Microsoft SQL Server 에이전트를 활성화해야 합니다.

**작업 테이블에 대해 별도의 데이터베이스 구성**

>[!NOTE]
>
>이 구성은 선택 사항입니다.

**WdbcOptions_TempDbName** 옵션을 사용하면 Microsoft SQL Server에서 작업 테이블에 대해 별도의 데이터베이스를 구성할 수 있습니다. 백업 및 복제를 최적화합니다.

이 옵션은 작업 테이블(예: 워크플로우를 실행하는 동안 만든 테이블)을 다른 데이터베이스에서 만들려면 사용할 수 있습니다.

옵션을 &quot;tempdb.dbo&quot;로 설정하면 작업 테이블이 Microsoft SQL Server의 기본 임시 데이터베이스에 생성됩니다. 데이터베이스 관리자가 tempdb 데이터베이스에 대한 쓰기 액세스를 허용해야 합니다.

이 옵션을 설정하면 Adobe Campaign에 구성된 모든 Microsoft SQL Server 데이터베이스(기본 데이터베이스 및 외부 계정)에서 사용됩니다. 두 외부 계정이 동일한 서버를 공유하는 경우 tempdb가 고유하므로 충돌이 발생할 수 있습니다. 동일한 방법으로 두 Campaign 인스턴스가 동일한 MSSQL 서버를 사용하는 경우 동일한 tempdb를 사용하는 경우 충돌이 발생할 수 있습니다.
