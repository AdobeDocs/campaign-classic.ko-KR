---
title: SQL 데이터 관리
seo-title: SQL 데이터 관리
description: SQL 데이터 관리
seo-description: null
page-status-flag: never-activated
uuid: b6057496-2dd5-4289-96df-98378e4f0ae7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 18d6f5e1-308f-4080-b7c4-ebf836f74842
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7bcf222f41c0e40368644b76197b07f2ded699f0

---


# SQL 데이터 관리{#sql-data-management}

SQL **데이터 관리** 활동을 사용하면 작업 테이블을 만들고 채울 고유한 SQL 스크립트를 작성할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

활동을 구성하기 전에 다음 전제 조건이 충족되었는지 확인하십시오.

* 활동은 원격 데이터 소스에서만 사용할 수 있습니다. 따라서 **[!UICONTROL FDA]** (Federated Data Access) 패키지가 인스턴스에 설치되어 있어야 합니다( [이 섹션](../../platform/using/about-fda.md)참조).
* 아웃바운드 스키마는 데이터베이스에 존재해야 하며 FDA 데이터베이스에 연결되어 있어야 합니다(데이터 스키마에 대한 자세한 내용은 [이 섹션을](../../configuration/using/about-schema-reference.md)참조하십시오).
* 워크플로우를 실행하는 연산자는 **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** 명명된 권한을 가져야 합니다. For more on named rights, refer to [this section](../../platform/using/access-management.md#named-rights).

## SQL 데이터 관리 작업 구성 {#configuring-the-sql-data-management-activity}

1. 활동을 **[!UICONTROL Label]**&#x200B;지정합니다.
1. 사용할 **[!UICONTROL External account]** 항목을 선택한 다음 이 외부 계정에 **[!UICONTROL Outbound schema]** 연결된 항목을 선택합니다.

   >[!CAUTION]
   >
   >아웃바운드 스키마가 수정되었으며 편집할 수 없습니다.

1. SQL 스크립트를 추가합니다.

   >[!CAUTION]
   >
   >SQL 스크립트 작성기가 SQL 스크립트가 제대로 작동하는지 확인하고 해당 참조(필드 이름 등)가 작동하는지 확인하는 것은 SQL 스크립트 작성자의 책임입니다. 는 아웃바운드 스키마와 일치합니다.

   기존 SQL 코드를 로드하려면 **[!UICONTROL The SQL script is contained in an entity stored in the database]** 옵션을 선택합니다. SQL 스크립트를 만들어 **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]** 메뉴에 저장해야 합니다.

   그렇지 않으면 전용 영역에 SQL 스크립트를 입력하거나 복사하여 붙여 넣습니다.

   ![](assets/sql_datamanagement.png)

   활동에서는 스크립트에서 다음 변수를 사용할 수 있습니다.

   * **activity.tableName**:아웃바운드 작업 테이블의 SQL 이름입니다.
   * **task.incomingTransitionByName(&#39;name&#39;).tableName**:사용할 들어오는 전환이 가져오는 작업 테이블의 SQL 이름(해당 이름으로 전환 식별).

      >[!NOTE]
      >
      >(&#39;name&#39;) 값은 전환 속성의 **[!UICONTROL Name]** 필드에 해당합니다.

1. SQL 스크립트에 아웃바운드 작업 테이블을 만드는 명령이 이미 포함되어 있는 경우 **[!UICONTROL Automatically create work table]** 옵션을 선택 취소합니다. 그렇지 않으면 워크플로우가 실행되면 작업 테이블이 자동으로 생성됩니다.
1. 을 **[!UICONTROL Ok]** 클릭하여 활동 구성을 확인합니다.

이제 활동이 구성됩니다. 워크플로우에서 실행할 준비가 되었습니다.

>[!CAUTION]
>
>활동이 실행되면 아웃바운드 전환 레코드 수가 표시만 됩니다. SQL 스크립트의 복잡성 수준에 따라 달라질 수 있습니다.
>  
>활동이 다시 시작되는 경우 실행 상태와 관계없이 전체 스크립트가 처음부터 실행됩니다.

## SQL 스크립트 샘플 {#sql-script-samples}

>[!NOTE]
>
>이 섹션의 스크립트 샘플은 PostgreSQL에서 실행되어야 합니다.

아래 스크립트를 사용하면 작업 테이블을 만들고 동일한 작업 테이블에 데이터를 삽입할 수 있습니다.

```
CREATE UNLOGGED TABLE <%= activity.tableName %> (
  iRecipientId INTEGER DEFAULT 0,
  sFirstName VARCHAR(100),
  sMiddleName VARCHAR(100),
  sLastName VARCHAR(100),
  sEmail VARCHAR(100)
);

INSERT INTO <%= activity.tableName %>
SELECT iRecipientId, sFirstName, sMiddleName, sLastName, sEmail
FROM nmsRecipient
GROUP BY iRecipientId, sFirstName, sMiddleName, sLastName, sEmail;
```

아래 스크립트를 사용하면 CTAS 작업(CREATE TABLE AS SELECT)을 수행하고 작업 테이블 인덱스를 만들 수 있습니다.

```
CREATE TABLE <%= activity.tableName %>
AS SELECT iRecipientId, sEmail, sFirstName, sLastName, sMiddleName
FROM nmsRecipient
WHERE sEmail IS NOT NULL
GROUP BY iRecipientId, sEmail, sFirstName, sLastName, sMiddleName;

CREATE INDEX ON <%= activity.tableName %> (sEmail);

ANALYZE <%= activity.tableName %> (sEmail);
```

아래 스크립트를 사용하면 두 개의 작업 테이블을 병합할 수 있습니다.

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```

