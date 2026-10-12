---
product: campaign
title: 데이터베이스 구조 업데이트
description: 데이터베이스 구조 업데이트
feature: Configuration
role: Developer
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
TQID: 'https://experienceleague.adobe.com/y4P6bZcEyVIdfI4LHMivPIRVzb1Z4sV7ewISWqk29F0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
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
source-wordcount: '156'
ht-degree: 8%
---
# 데이터베이스 구조 업데이트{#updating-the-database-structure}

스키마에 대한 수정 사항을 적용하려면 **[!UICONTROL Tools > Advanced > Update database structure]**&#x200B;을(를) 통해 사용 가능한 Database Update Assistant를 실행하십시오. Campaign Classic v7에서 도우미는 다음 옵션도 제공합니다.

**[!UICONTROL Add stored procedures]** 및 **[!UICONTROL Import initialization data]** 옵션은 데이터베이스를 만들 때 실행되는 초기 SQL 스크립트와 데이터 패키지를 시작하는 데 사용됩니다.

외부 데이터 패키지에서 데이터 세트를 가져올 수 있습니다. 이렇게 하려면 **[!UICONTROL Import a package]**&#x200B;을(를) 선택하고 패키지의 XML 파일을 입력하십시오.

Campaign v7에서 v8로 전환하는 과정의 일부로 Campaign Classic 설명서 세트가 간소화 및 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다. 데이터베이스 업데이트 도우미에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/update-database-structure){target=_blank}를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/update-database-structure){target=_blank}
