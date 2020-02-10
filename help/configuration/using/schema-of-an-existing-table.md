---
title: 기존 테이블의 스키마
seo-title: 기존 테이블의 스키마
description: 기존 테이블의 스키마
seo-description: null
page-status-flag: never-activated
uuid: cb766259-8ed7-40a1-8df7-75a8a3f9986d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6877d94d-d6e5-4080-a537-ef1bb6e6f8cf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# 기존 테이블의 스키마{#schema-of-an-existing-table}

## 개요 {#overview}

응용 프로그램이 기존 테이블, SQL 보기 또는 원격 데이터베이스의 데이터에 액세스해야 하는 경우 다음 데이터를 사용하여 Adobe Campaign에서 해당 스키마를 만듭니다.

* 테이블 이름:&quot;sqltable&quot; 속성과 함께 테이블 이름(깜박임이 사용될 때 해당 별칭 포함)을 입력합니다.
* 스키마 키:조정 필드 참조,
* 색인:쿼리를 생성하는 데 사용됩니다.
* XML 구조에서의 필드 및 위치:애플리케이션에 사용된 필드만 채웁니다.
* 링크:if there are joins with the other tables of the base.

## 구현 {#implementation}

해당 스키마를 만들려면 다음 단계를 적용합니다.

1. Adobe Campaign 트리의 **[!UICONTROL Administration>Configuration>Data schemas]** 노드를 편집하고 을 클릭합니다 **[!UICONTROL New]** .
1. 옵션을 **[!UICONTROL Access data from an existing table or an SQL view]** 선택하고 을 클릭합니다 **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. 표 또는 기존 보기를 선택합니다.

   ![](assets/s_ncs_configuration_select_table.png)

1. 필요에 맞게 스키마 컨텐츠를 조정할 수 있습니다.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   테이블 생성 SQL 스크립트를 생성하지 않으려면 `<srcSchema>` 루트 요소에 view=&quot;true&quot; 속성으로 스키마를 채워야 합니다.

**예** :

```
<srcSchema name="recipient" namespace="cus" view="true">
  <element name="recipient" sqltable="dbsrv.recipient">
    <key name="email">
      <keyfield xpath="@email"/>
    </key>   
    <attribute name="email" type="string" length="80" sqlname="email"/>
  </element>
</srcSchema>
```

## 외부 데이터베이스 액세스 {#accessing-an-external-database}

통합 **데이터 액세스 - FDA** 옵션을 사용하면 외부 데이터베이스에 저장된 데이터에 액세스할 수 있습니다.

외부 데이터베이스의 데이터에 액세스하기 위해 스키마에 대해 수행되는 구성은 [이 페이지에서](../../platform/using/accessing-an-external-database.md#creating-the-data-schema)자세히 설명합니다.
