---
product: campaign
title: Adobe Campaign의 스키마 구조 이해
description: 스키마 구조
feature: Custom Resources
role: Developer
audience: configuration
content-type: reference
level: Intermediate, Experienced
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
TQID: 'https://experienceleague.adobe.com/dFZ38qRKX-4vTEYS9GosS5TdW-XhnoIq8ckbjnNEJmo'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: a2002dba-5e37-4dff-8e04-1cc3ec73558c
    internal-label: Custom resources
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 6%
---
# 스키마 구조 이해 {#schema-structure}

이 페이지에는 Adobe Campaign 데이터 유형이 각 데이터베이스 관리 시스템의 데이터 유형에 매핑되는 방법이 나열됩니다.

Campaign v7에서 v8로 전환하는 과정의 일부로 Campaign Classic 설명서 세트가 간소화 및 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다. 스키마 구조에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/developer/schemas-forms/schema-structure){target=_blank}를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/developer/schemas-forms/schema-structure){target=_blank}

## Adobe Campaign/DBMS 데이터 유형 매핑 {#mapping-the-types-of-adobe-campaign-dbms-data}

아래 표에는 다른 데이터베이스 관리 시스템에 대해 Adobe Campaign에서 생성한 데이터 유형에 대한 매핑이 나와 있습니다.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 문자열<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2(유니코드인 경우 NVARCHAR2)<br /> </td> 
  </tr> 
  <tr> 
   <td> 부울<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> 숫자(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 바이트<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> 숫자(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 짧음<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> 숫자(5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Double<br /> </td> 
   <td> 배정밀도<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> <br /> 길 </td> 
   <td> 정수<br /> </td> 
   <td> NUMBER(10)<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NUMBER(20)<br /> </td> 
  </tr> 
  <tr> 
   <td> 날짜<br /> </td> 
   <td> 날짜<br /> </td> 
   <td> 날짜<br /> </td> 
  </tr> 
  <tr> 
   <td> 시간<br /> </td> 
   <td> 시간<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetime<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> 날짜<br /> </td> 
  </tr> 
  <tr> 
   <td> Datatimenotz<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> 날짜<br /> </td> 
  </tr> 
  <tr> 
   <td> Timespan<br /> </td> 
   <td> 배정밀도<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> 메모<br /> </td> 
   <td> 텍스트<br /> </td> 
   <td> CLOB(유니코드인 경우 NCLOB)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 자세히 알아보기

자세한 내용은 다음 링크를 참조하십시오.

* [스키마 시작하기](about-schema-reference.md)
* [데이터베이스 매핑](database-mapping.md)
* [링크 관리](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"}(Campaign v8 설명서)
* [키 관리](database-keys.md)
