---
solution: Campaign Classic
product: campaign
title: SQL 데이터 관리
description: SQL 데이터 관리 워크플로 작업에 대한 자세한 내용
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 3%

---


# SQL 데이터 관리{#sql-data-management}

**SQL 데이터 관리** 활동을 통해 자신의 SQL 스크립트를 작성하여 작업 테이블을 만들고 채울 수 있습니다.

## 사전 요구 사항 {#prerequisites}

활동을 구성하기 전에 다음 전제 조건이 충족되었는지 확인하십시오.

* 작업은 원격 데이터 소스에서만 사용할 수 있습니다. 그러므로 **[!UICONTROL FDA]**(Federated Data Access) 패키지가 인스턴스에 설치되어 있어야 합니다. [자세히 알아보기](../../installation/using/about-fda.md)
* 아웃바운드 스키마가 데이터베이스에 존재해야 하며 FDA 데이터베이스에 연결되어 있어야 합니다. [자세히 알아보기](../../configuration/using/about-schema-reference.md)
* 작업 과정을 실행하는 연산자에게는 오른쪽의 **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]**&#x200B;이(가) 있어야 합니다. [자세히 알아보기](../../platform/using/access-management.md#named-rights)

## SQL 데이터 관리 작업 {#configuring-the-sql-data-management-activity} 구성

1. 활동 **[!UICONTROL Label]**&#x200B;을(를) 지정합니다.
1. 사용할 **[!UICONTROL External account]**&#x200B;을 선택하고 이 외부 계정에 연결된 **[!UICONTROL Outbound schema]**&#x200B;을 선택합니다.

   >[!CAUTION]
   >
   >아웃바운드 스키마가 수정되었으며 편집할 수 없습니다.

1. SQL 스크립트를 추가합니다.

   >[!CAUTION]
   >
   >SQL 스크립트가 제대로 작동하는지 확인하고 SQL 스크립트의 참조(필드 이름 등)가 있는지 확인하는 것은 SQL 스크립트 작성자의 책임입니다. 는 아웃바운드 스키마에 부합합니다.

   기존 SQL 코드를 로드하려면 **[!UICONTROL The SQL script is contained in an entity stored in the database]** 옵션을 선택합니다. SQL 스크립트는 **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]** 메뉴에서 만들고 저장해야 합니다.

   그렇지 않은 경우 전용 영역에 SQL 스크립트를 입력하거나 복사하여 붙여 넣습니다.

   ![](assets/sql_datamanagement.png)

   활동에서는 스크립트에서 다음 변수를 사용할 수 있습니다.

   * **activity.tableName**:아웃바운드 작업 테이블의 SQL 이름입니다.
   * **task.incomingTransitionByName(&#39;name&#39;).tableName**:사용할 들어오는 전환이 포함하는 작업 테이블의 SQL 이름(전환이 이름으로 식별됨).

      >[!NOTE]
      >
      >(&#39;name&#39;) 값은 전환 속성의 **[!UICONTROL Name]** 필드에 해당합니다.

1. SQL 스크립트에 아웃바운드 작업 테이블을 만드는 명령이 이미 포함되어 있으면 **[!UICONTROL Automatically create work table]** 옵션을 선택 해제합니다. 그렇지 않으면 작업 테이블이 워크플로우가 실행되면 자동으로 만들어집니다.
1. **[!UICONTROL Ok]**&#x200B;을 클릭하여 활동 구성을 확인합니다.

이제 활동이 구성됩니다. 워크플로우에서 실행할 준비가 되었습니다.

>[!CAUTION]
>
>활동이 실행되면 아웃바운드 전환 레코드 수가 표시만 됩니다. SQL 스크립트의 복잡도에 따라 다를 수 있습니다.
>  
>활동을 다시 시작하면 실행 상태와 관계없이 전체 스크립트가 처음부터 실행됩니다.

## SQL 스크립트 샘플 {#sql-script-samples}

>[!NOTE]
>
>이 섹션의 스크립트 샘플은 PostgreSQL에서 실행되도록 되어 있습니다.

아래 스크립트를 사용하면 작업 테이블을 만들고 데이터를 동일한 작업 테이블에 삽입할 수 있습니다.

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

아래 스크립트에서는 CTAS 작업(CREATE TABLE AS SELECT)을 수행하고 작업 테이블 인덱스를 만들 수 있습니다.

```
CREATE TABLE <%= activity.tableName %>
AS SELECT iRecipientId, sEmail, sFirstName, sLastName, sMiddleName
FROM nmsRecipient
WHERE sEmail IS NOT NULL
GROUP BY iRecipientId, sEmail, sFirstName, sLastName, sMiddleName;

CREATE INDEX ON <%= activity.tableName %> (sEmail);

ANALYZE <%= activity.tableName %> (sEmail);
```

아래 스크립트에서는 두 개의 작업 테이블을 병합할 수 있습니다.

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```

