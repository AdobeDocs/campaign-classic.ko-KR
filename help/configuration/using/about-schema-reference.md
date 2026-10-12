---
product: campaign
title: Adobe Campaign에서 스키마 시작
description: 스키마로 작업하고 Adobe Campaign 데이터베이스의 개념적 데이터 모델을 확장하는 방법을 알아봅니다
feature: Schema Extension
role: Developer
level: Intermediate, Experienced
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
TQID: 'https://experienceleague.adobe.com/ikQVjdkvhTM-361S7mcpRYsuhpqjHxX-Y-9wdRCYldg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 3%
---
# 스키마 시작하기 {#about-schema-reference}

## 스키마란? {#what-is-a-schema}

이 장에서는 Adobe Campaign 데이터베이스의 개념 데이터 모델을 확장하기 위해 확장 스키마를 구성하는 방법에 대해 설명합니다.

Campaign 기본 제공 테이블과 상호 작용에 대한 자세한 내용은 [Campaign Classic 데이터 모델](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/developer/datamodel){target="_blank"}(Campaign v8 설명서)을 참조하세요.

Adobe Campaign에서 애플리케이션에 포함된 데이터의 물리적 및 논리적 구조는 XML에 설명되어 있습니다. **스키마**&#x200B;은(는) 데이터베이스 테이블과 연결된 XML 문서입니다. 데이터 구조를 정의하고 테이블의 SQL 정의를 설명합니다.

* 테이블 이름
* 필드
* 색인
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

Campaign v7에서 v8로 전환하는 과정의 일부로 Campaign Classic 설명서 세트가 간소화 및 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다. 스키마의 구문 및 식별에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/developer/schemas-forms/schemas){target=_blank}를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/developer/schemas-forms/schemas){target=_blank}
