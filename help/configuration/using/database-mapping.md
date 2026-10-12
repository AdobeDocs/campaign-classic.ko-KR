---
product: campaign
title: 데이터베이스 매핑
description: 데이터베이스 매핑
feature: Configuration, Instance Settings
role: Developer
exl-id: 728b509f-2755-48df-8b12-449b7044e317
TQID: 'https://experienceleague.adobe.com/d3oQ8zJVsjVdj9PZ30rQ8hEuern1l3ZlMAWrbymhnvs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 6%
---
# 데이터베이스 매핑{#database-mapping}

이 페이지에서는 스키마 필드에서 인덱스를 선언하는 방법을 설명합니다.

Campaign v7에서 v8로 전환하는 과정의 일부로 Campaign Classic 설명서 세트가 간소화 및 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다. 스키마의 SQL 매핑에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/developer/schemas-forms/database-mapping){target=_blank}를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/developer/schemas-forms/database-mapping){target=_blank}

## 인덱싱된 필드 {#indexed-fields}

인덱스를 사용하면 애플리케이션에서 사용되는 SQL 쿼리의 성능을 최적화할 수 있습니다.

인덱스는 데이터 스키마의 기본 요소에서 선언됩니다.

```sql
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

색인은 다음 규칙을 따릅니다.

* 인덱스는 테이블에서 하나 이상의 필드를 참조할 수 있습니다
* **unique** 특성에 &quot;true&quot; 값이 포함된 경우 인덱스가 모든 필드에서 고유할 수 있습니다(중복 방지).
* 인덱스의 SQL 이름은 테이블의 SQL 이름과 인덱스의 이름에서 결정됩니다

>[!NOTE]
>
>* 표준으로 색인은 스키마의 기본 요소에서 선언된 첫 번째 요소입니다.
>
>* 인덱스는 테이블 매핑(표준 또는 FDA) 중에 자동으로 만들어집니다.

**예**:

* 이메일 주소 및 구/군/시에 색인 추가:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* &quot;id&quot; 이름 필드에 고유 인덱스 추가:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

## 자세히 알아보기

자세한 내용은 다음 링크를 참조하십시오.

* [스키마 시작하기](about-schema-reference.md)
* [스키마 구조](schema-structure.md)
* [키 관리](database-keys.md)
* [링크 관리](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"}(Campaign v8 설명서)
