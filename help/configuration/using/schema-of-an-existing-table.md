---
solution: Campaign Classic
product: campaign
title: 기존 테이블의 스키마
description: 기존 테이블의 스키마
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 9%

---


# 기존 테이블의 스키마{#schema-of-an-existing-table}

## 개요 {#overview}

응용 프로그램에서 기존 테이블, SQL 보기 또는 원격 데이터베이스의 데이터에 액세스해야 하는 경우 다음 데이터로 Adobe Campaign에서 해당 스키마를 만듭니다.

* 테이블 이름:&quot;sqltable&quot; 속성을 사용하여 테이블 이름(깜박임이 사용될 때 해당 별칭 포함)을 입력합니다.
* 스키마 키:조정 필드 참조,
* 색인:쿼리를 생성하는 데 사용됩니다.
* XML 구조에서의 필드 및 위치:애플리케이션에 사용된 필드만 채웁니다.
* 링크:기본 테이블의 다른 테이블과 조인이 있는 경우

## 구현 {#implementation}

해당 스키마를 생성하려면 다음 단계를 적용합니다.

1. Adobe Campaign 트리의 **[!UICONTROL Administration>Configuration>Data schemas]** 노드를 편집하고 **[!UICONTROL New]** 을 클릭합니다.
1. **[!UICONTROL Access data from an existing table or an SQL view]** 옵션을 선택하고 **[!UICONTROL Next]** 을 클릭합니다.

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. 표 또는 기존 보기를 선택합니다.

   ![](assets/s_ncs_configuration_select_table.png)

1. 필요에 맞게 스키마 컨텐츠를 조정할 수 있습니다.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   테이블 생성 SQL 스크립트를 생성하지 않으려면 `<srcSchema>` 루트 요소의 view=&quot;true&quot; 속성으로 스키마를 채워야 합니다.

**예제** :

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

## 외부 데이터베이스 액세스{#accessing-an-external-database}

**통합 데이터 액세스 - FDA** 옵션을 사용하면 외부 데이터베이스에 저장된 데이터에 액세스할 수 있습니다.

외부 데이터베이스의 데이터에 액세스하기 위해 스키마에 적용할 구성은 [이 페이지](../../installation/using/creating-data-schema.md)에 자세히 설명되어 있습니다.
