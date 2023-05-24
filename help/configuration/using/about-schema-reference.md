---
product: campaign
title: Adobe Campaign Classic의 스키마 참조 정보
description: Adobe Campaign Classic 데이터베이스의 개념 데이터 모델을 확장하기 위해 확장 스키마를 구성하는 방법을 알아봅니다
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Schema Extension
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 7%

---

# 스키마 참조 정보{#about-schema-reference}

이 장에서는 Adobe Campaign 데이터베이스의 개념 데이터 모델을 확장하기 위해 확장 스키마를 구성하는 방법에 대해 설명합니다.

Campaign 기본 제공 테이블과 상호 작용에 대한 자세한 내용은 [Campaign Classic 데이터 모델](https://helpx.adobe.com/kr/campaign/kb/acc-datamodel.html).

애플리케이션에 포함된 데이터의 물리적 및 논리적 구조는 XML에 설명되어 있습니다. 라고 하는 Adobe Campaign 고유의 문법을 따릅니다. **스키마**.

스키마는 데이터베이스 테이블과 연관된 XML 문서입니다. 데이터 구조를 정의하고 테이블의 SQL 정의를 설명합니다.

* 테이블 이름
* 필드
* 인덱스
* 다른 테이블과의 링크

또한 데이터를 저장하는 데 사용되는 XML 구조에 대해서도 설명합니다.

* 요소 및 속성
* 요소의 계층
* 요소 및 속성 유형
* 기본값
* 레이블, 설명 및 기타 등록 정보.

스키마를 사용하면 데이터베이스에서 엔티티를 정의할 수 있습니다. 각 엔티티에 대한 스키마가 있습니다.

다음 그림은 Adobe Campaign 데이터 시스템의 스키마 위치를 보여 줍니다.

![](assets/reference_schema_intro.png)

## 스키마 구문 {#syntax-of-schemas}

스키마의 루트 요소는 **`<srcschema>`**. 여기에는 **`<element>`** 및 **`<attribute>`** 하위 요소.

첫 번째 **`<element>`** 하위 요소는 엔티티 루트와 일치합니다.

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">  
    <attribute name="lastName"/>
    <attribute name="email"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

>[!NOTE]
>
>엔티티의 루트 요소는 스키마와 동일한 이름을 갖습니다.

![](assets/s_ncs_configuration_schema_and_entity.png)

다음 **`<element>`** 태그는 엔티티 요소의 이름을 정의합니다. **`<attribute>`** 스키마 태그는 의 속성 이름을 정의합니다. **`<element>`** 태그가 연결되어 있습니다.

## 스키마 식별 {#identification-of-a-schema}

데이터 스키마는 이름 및 네임스페이스로 식별됩니다.

네임스페이스를 사용하면 관심 영역별로 스키마 세트를 그룹화할 수 있습니다. 예를 들어 **cus** 네임스페이스는 고객별 구성(**고객**).

스키마의 식별 키는 네임스페이스와 콜론으로 구분된 이름을 사용하여 빌드된 문자열입니다. 예: **cus:recipient**.

>[!IMPORTANT]
>
>네임스페이스 이름은 간결해야 하며 XML 이름 지정 규칙에 따라 승인된 문자만 포함해야 합니다.
>
>식별자는 숫자로 시작할 수 없습니다.
>
>다음 네임스페이스는 Adobe Campaign 애플리케이션 작업에 필요한 시스템 엔터티의 설명을 위해 예약되므로 사용하지 않아야 합니다. **xtk**, **nl**, **nms**, **ncm**, **임시**, **ncl**, **crm**, **xxl**.

