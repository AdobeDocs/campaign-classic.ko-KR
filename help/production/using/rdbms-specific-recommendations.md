---
title: RDBMS 특정 추천
seo-title: RDBMS 특정 추천
description: RDBMS 특정 추천
seo-description: null
page-status-flag: never-activated
uuid: 637c1b5a-0484-4734-a012-eb4ba8036263
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: b2219912-5570-45d2-8b52-52486e29d008
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8fd9949ec03b7c2cdf88a9d5fcf5c8d8fd85f7d0

---


# RDBMS 특정 추천{#rdbms-specific-recommendations}

유지 관리 계획을 설정하는 데 도움이 되도록 이 섹션에는 Adobe Campaign에서 지원하는 다양한 RDBMS 엔진에 적용된 몇 가지 권장 사항/우수 사례가 나열됩니다. 하지만 권장 사항일 뿐입니다. 내부 절차와 제약 조건을 준수하면서 필요에 맞게 조정하는 것은 귀하에게 달려 있습니다. 데이터베이스 관리자는 이러한 계획을 작성 및 실행할 책임이 있습니다.

## PostgreSQL {#postgresql}

### 큰 테이블 검색 {#detecting-large-tables}

1. 다음 뷰를 데이터베이스에 추가할 수 있습니다.

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

1. 다음 명령을 실행하면 큰 테이블 및 인덱스를 찾을 수 있습니다.

   ```
   select * from uvSpace;
   ```

### 간단한 유지 관리 {#simple-maintenance}

PostgreSQL에서 사용할 수 있는 일반적인 명령은 **진공** 완전 **및**&#x200B;다시 인덱스입니다.

다음은 이러한 두 명령을 사용하여 정기적으로 실행되는 SQL 유지 관리 계획의 일반적인 예입니다.

```
vacuum full nmsdelivery;
 reindex table nmsdelivery;
 
 vacuum full nmsdeliverystat;
 reindex table nmsdeliverystat;
 
 vacuum full xtkworkflow;
 reindex table xtkworkflow;
 
 vacuum full xtkworkflowevent;
 reindex table xtkworkflowevent;
 
 vacuum full xtkworkflowjob;
 reindex table xtkworkflowjob;
 
 vacuum full xtkworkflowlog;
 reindex table xtkworkflowlog;
 
 vacuum full xtkworkflowtask;
 reindex table xtkworkflowtask;
 
 vacuum full xtkjoblog;
 reindex table xtkjoblog;
 
 vacuum full xtkjob;
 reindex table xtkjob;
 
 vacuum full nmsaddress;
 reindex table nmsaddress;

 vacuum full nmsdeliverypart;
 reindex table nmsdeliverypart;
 
 vacuum full nmsmirrorpageinfo;
 reindex table nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe에서는 작은 표로 시작하는 것이 좋습니다.이 방법으로 큰 테이블에서 프로세스가 실패하는 경우(실패 위험이 가장 높은 경우), 유지 관리의 일부가 완료됩니다.
>* Adobe는 중요한 업데이트를 적용할 수 있는 데이터 모델별 테이블을 추가하는 명령을 다시 수행합니다. 일별 데이터 복제 흐름이 많을 경우 **NmsRecipient** 의 경우일 수 있습니다.
>* 진공청소기 **및** 다시 색인 **** 명령은 테이블을 잠가 유지 관리가 진행되는 동안 일부 프로세스를 일시 중지합니다.
>* 매우 큰 테이블(일반적으로 5Gb 이상)의 경우 **진공** 완전비효율적으로 되어 매우 오랜 시간이 걸릴 수 있습니다. YyyNmsBroadLogXxx 표에 사용하지 않는 **것이 좋습니다** .
>* 이 유지 관리 작업은 Adobe Campaign 워크플로우에서 **[!UICONTROL SQL]** 활동을 사용하여 구현할 수 있습니다(자세한 내용은 [이 섹션을](../../workflow/using/executing-a-workflow.md#architecture)참조하십시오). 백업 창과 충돌하지 않는 낮은 작업 시간에 대한 유지 관리를 예약해야 합니다.
>



### 데이터베이스 다시 작성 {#rebuilding-a-database}

PostgreSQL은 **공백이 가득** 차서 정상적인 프로덕션을 방지하기 때문에 온라인 테이블 재빌드를 쉽게 수행할 수 없습니다. 즉, 테이블이 사용되지 않을 때 유지 관리가 수행되어야 합니다. 다음 중 하나를 수행할 수 있습니다.

* adobe Campaign 플랫폼이 중지되면 유지 관리 작업을 수행합니다.
* 다시 빌드되는 표에 작성할 수 있는 다양한 Adobe Campaign 하위 서비스를 중지합니다(워크플로우 프로세스를 중지하려면&#x200B;**nlserver stop wfserver instance_name** ).

다음은 필요한 DDL을 생성하기 위해 특정 함수를 사용하는 테이블 조각 모음의 예입니다. 다음 SQL을 사용하여 두 개의 새 함수를 만들 수 있습니다.GenRebuildTablePart1 **및** GenRebuildTablePart2 ****- 테이블을 다시 만드는 데 필요한 DDL을 생성하는 데 사용할 수 있습니다.

* 첫 번째 함수를 사용하면 원본 테이블의 복사본인 작업 테이블(*_tmp***여기)을 만들 수 있습니다.
* 그런 다음 두 번째 함수는 원래 테이블을 삭제하고 작업 테이블 및 인덱스의 이름을 변경합니다.
* 한 함수 대신 두 함수를 사용하면 첫 번째 함수가 실패할 경우 원본 테이블을 삭제할 위험이 없습니다.

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

다음 예는 **진공청소기/다시 빌드** 명령을 사용하는 대신 필요한 테이블을 다시 빌드하는 워크플로우에서 사용할 수 있습니다.

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

Oracle 버전에 가장 적합한 절차에 대해서는 데이터베이스 관리자에게 문의하십시오.

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>Microsoft SQL Server의 경우 이 [페이지에](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html)설명된 유지 관리 계획을 사용할 수 있습니다.

아래 예는 Microsoft SQL Server 2005와 관련이 있습니다. 다른 버전을 사용하는 경우 데이터베이스 관리자에게 문의하여 유지 관리 절차에 대해 알아보십시오.

1. 먼저 관리자 권한으로 로그인하여 Microsoft SQL Server Management Studio에 연결합니다.
1. 폴더로 이동하여 마우스 오른쪽 단추를 클릭하고 **[!UICONTROL Management > Maintenance Plans]** 선택합니다 **[!UICONTROL Maintenance Plan Wizard]**
1. 첫 번째 페이지가 나타나면 **[!UICONTROL Next]** 클릭합니다.
1. 생성할 유지 관리 계획 유형을 선택합니다(각 작업에 대해 별도의 일정 또는 전체 계획에 대한 단일 일정). 그런 다음 **[!UICONTROL Change...]** 단추를 누릅니다.
1. 창에서 **[!UICONTROL Job schedule properties]** 원하는 실행 설정을 선택하고 **[!UICONTROL OK]** 을 클릭한 다음 을 클릭합니다 **[!UICONTROL Next]** .
1. 수행할 유지 관리 작업을 선택한 다음 을 클릭합니다 **[!UICONTROL Next]** .

   >[!NOTE]
   >
   >아래에 표시된 유지 관리 작업 이상을 수행하는 것이 좋습니다. 데이터베이스 정리 워크플로우에서 이미 수행되고 있지만 통계 업데이트 작업을 선택할 수도 있습니다.

1. 드롭다운 목록에서 **[!UICONTROL Database Check Integrity]** 작업을 실행할 데이터베이스를 선택합니다.
1. 데이터베이스를 선택하고 을 **[!UICONTROL OK]** 클릭한 다음 을 **[!UICONTROL Next]** 클릭합니다.
1. 데이터베이스에 할당된 최대 크기를 구성한 다음 을 클릭합니다 **[!UICONTROL Next]** .

   >[!NOTE]
   >
   >데이터베이스 크기가 이 임계값을 초과하는 경우 유지 관리 계획은 사용하지 않은 데이터를 삭제하여 공간을 확보하려고 합니다.

1. 인덱스를 다시 구성하거나 다시 구성합니다.

   * 인덱스 조각화 비율이 10%에서 40% 사이인 경우 다시 구성하는 것이 좋습니다.

      재구성할 데이터베이스 및 개체(표 또는 보기)를 선택한 다음 을 클릭합니다 **[!UICONTROL Next]** .

      >[!NOTE]
      >
      >구성에 따라 이전에 선택한 테이블 또는 데이터베이스의 모든 테이블을 선택할 수 있습니다.

   * 인덱스 조각화 비율이 40%보다 높은 경우 다시 구성하는 것이 좋습니다.

      인덱스 다시 작성 작업에 적용할 옵션을 선택한 다음 을 클릭합니다 **[!UICONTROL Next]** .

      >[!NOTE]
      >
      >재구축 인덱스 프로세스는 프로세서 사용 측면에서 더욱 제한적이며 데이터베이스 리소스를 잠급니다. 다시 구성하는 동안 색인을 사용할 수 있게 하려면 **[!UICONTROL Keep index online while reindexing]** 옵션을 확인합니다.

1. 활동 보고서에 표시할 옵션을 선택한 다음 을 클릭합니다 **[!UICONTROL Next]** .
1. 유지 관리 계획에 대해 구성된 작업 목록을 선택한 다음 을 클릭합니다 **[!UICONTROL Finish]** .

   유지 관리 계획의 요약 및 다양한 단계의 상태가 표시됩니다.

1. 유지 관리 계획이 완료되면 을 클릭합니다 **[!UICONTROL Close]** .
1. Microsoft SQL Server 탐색기에서 **[!UICONTROL Management > Maintenance Plans]** 폴더를 두 번 클릭합니다.
1. Adobe Campaign 유지 관리 계획을 선택합니다.워크플로우에서는 다양한 단계가 자세히 설명되어 있습니다.

   객체가 **[!UICONTROL SQL Server Agent > Jobs]** 폴더에 생성되었습니다. 이 개체를 사용하면 유지 관리 계획을 시작할 수 있습니다. 이 예에서는 모든 유지 관리 작업이 동일한 계획의 일부이므로 개체가 하나만 있습니다.

   >[!CAUTION]
   >
   >이 개체를 실행하려면 Microsoft SQL Server 에이전트가 활성화되어 있어야 합니다.

**작업 테이블에 대해 별도의 데이터베이스 구성**

>[!NOTE]
>
>이 구성은 선택 사항입니다.

WdbcOptions **_TempDbName** 옵션을 사용하면 Microsoft SQL Server에서 작업 테이블에 대해 별도의 데이터베이스를 구성할 수 있습니다. 백업 및 복제를 최적화합니다.

이 옵션은 작업 테이블(예: 워크플로우 실행 중에 만들어진 테이블)을 다른 데이터베이스에 만들려는 경우에 사용할 수 있습니다.

이 옵션을 &quot;tempdb.dbo&quot;로 설정하면 작업 테이블이 Microsoft SQL Server의 기본 임시 데이터베이스에 생성됩니다. 데이터베이스 관리자가 tempdb 데이터베이스에 대한 쓰기 액세스를 허용해야 합니다.

이 옵션을 설정하면 Adobe Campaign에 구성된 모든 Microsoft SQL Server 데이터베이스(기본 데이터베이스 및 외부 계정)에 사용됩니다. 두 개의 외부 계정이 동일한 서버를 공유하는 경우 tempdb가 고유하므로 충돌이 발생할 수 있습니다. 동일한 방식으로 두 Campaign 인스턴스가 동일한 MSSQL 서버를 사용하는 경우 동일한 tempdb를 사용하는 경우 충돌이 발생할 수 있습니다.
