---
product: campaign
title: 기존 테이블의 스키마
description: 기존 테이블의 스키마
feature: Custom Resources
role: Data Engineer, Developer
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 7%

---

# 기존 테이블의 스키마{#schema-of-an-existing-table}

## 개요 {#overview}

응용 프로그램이 기존 테이블의 데이터, SQL 뷰 또는 원격 데이터베이스의 데이터에 액세스해야 하는 경우 다음 데이터를 사용하여 Adobe Campaign에서 해당 스키마를 만듭니다.

* 테이블 이름: &quot;sqltable&quot; 특성이 있는 테이블 이름(dblink를 사용할 때 해당 별칭과 함께) 입력,
* 스키마 키: 조정 필드 참조,
* 색인: 쿼리 생성에 사용,
* XML 구조의 필드 및 위치: 응용 프로그램에 사용되는 필드만 채웁니다.
* 링크: 기준의 다른 테이블과 조인이 있는 경우.

## 구현 {#implementation}

해당 스키마를 생성하려면 다음 단계를 적용합니다.

1. Adobe Campaign 트리의 **[!UICONTROL Administration>Configuration>Data schemas]** 노드를 편집하고 **[!UICONTROL New]** 을(를) 클릭합니다.
1. **[!UICONTROL Access data from an existing table or an SQL view]** 옵션을 선택하고 **[!UICONTROL Next]** 을(를) 클릭합니다.

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. 테이블 또는 기존 뷰를 선택합니다.

   ![](assets/s_ncs_configuration_select_table.png)

1. 필요에 따라 스키마 콘텐츠를 조정합니다.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   테이블 생성 SQL 스크립트를 생성하지 않으려면 `<srcSchema>` 루트 요소에서 view=&quot;true&quot; 특성으로 스키마를 채워야 합니다.

**예**:

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

**페더레이션 데이터 액세스 - FDA** 옵션을 사용하면 외부 데이터베이스에 저장된 데이터에 액세스할 수 있습니다.

외부 데이터베이스의 데이터에 액세스하기 위해 스키마에 포함할 구성이 [이 페이지](../../installation/using/creating-data-schema.md)에 자세히 설명되어 있습니다.
