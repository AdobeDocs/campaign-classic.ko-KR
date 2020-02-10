---
title: Adobe Campaign Classic 데이터 모델 정보
description: 이 문서에서는 Adobe Campaign Classic 데이터 모델의 기본 사항에 대해 설명합니다.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2ce2a1a55e244180a4e62d6f3b5a5ed5bb8aff6e

---


# Campaign Classic 데이터 모델 정보{#about-data-model}

이 섹션에서는 Adobe Campaign Classic 데이터 모델의 기본 사항에 대해 설명하고 Campaign 내장 테이블 및 상호 작용을 더 잘 파악합니다.

Adobe Campaign 데이터베이스의 개념 데이터 모델은 내장된 테이블 및 상호 작용 세트로 구성됩니다.

각 테이블에 대한 설명에 액세스하려면 **[!UICONTROL Admin > Configuration > Data schemas]**&#x200B;목록에서 리소스를 선택하고 **[!UICONTROL Documentation]** 탭을 클릭합니다.

![](assets/data-model_documentation-tab.png)

기본 Campaign Classic 데이터 모델 설명에 대한 자세한 내용은 이 [문서를](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html)참조하십시오.

응용 프로그램에 포함된 데이터의 물리적 및 논리적 구조는 XML에 설명되어 있습니다. 스키마라고 하는 Adobe Campaign에 대한 문법을 따릅니다. Adobe Campaign 스키마에 대한 자세한 내용은 이 [섹션을](../../configuration/using/about-schema-reference.md)참조하십시오.

## 개요 {#data-model-overview}

Adobe Campaign은 함께 연결된 테이블을 포함하는 관계형 데이터베이스에 의존합니다.

Adobe Campaign 데이터 모델의 기본 구조는 다음과 같습니다.

## 수신자 테이블 {#recipient-table}

데이터 모델은 기본적으로 받는 사람 테이블(NmsRecipient)인 기본 테이블을&#x200B;**사용합니다**. 이 표를 사용하면 모든 마케팅 프로필을 저장할 수 있습니다.

수신자 표에 대한 자세한 내용은 이 [섹션을](../../configuration/using/default-recipient-table.md)참조하십시오.

## 배달 테이블 {#delivery-table}

또한 데이터 모델에는 모든 마케팅 활동을 저장하기 위한 전용 부품이 포함되어 있습니다. 일반적으로 배달 테이블(NmsDelivery)**입니다**. 이 표의 각 레코드는 배달 작업 또는 배달 템플릿을 나타냅니다. 여기에는 타겟, 컨텐츠 등과 같은 전달 수행에 필요한 모든 매개 변수가 포함되어 있습니다.

## 테이블 로그 {#log-tables}

데이터 모델의 다른 부분에서 캠페인 실행과 관련된 모든 로그를 일시적으로 저장할 수 있습니다.

배달 로그는 모든 채널에서 받는 사람 또는 장치로 보내는 모든 메시지입니다. 기본 배달 로그 테이블(**NmsBroadLog**)에는 모든 받는 사람의 배달 로그가 포함되어 있습니다.
기본 추적 로그 테이블(**NmsTrackingLog**)은 모든 받는 사람의 추적 로그를 저장합니다. 추적 로그는 이메일 열기 및 클릭 수와 같은 수신자의 반응을 나타냅니다. 각 반응은 추적 로그에 해당합니다.
배달 로그 및 추적 로그는 Adobe Campaign에 지정되고 수정할 수 있는 특정 기간 후에 삭제됩니다. 따라서 로그를 정기적으로 내보내는 것이 좋습니다.

## 기술 표 {#technical-tables}

마지막으로, 데이터 모델의 일부는 연산자 및 사용자 권한(NmsGroup), 폴더(**XtkFolder**)를 포함하여 응용 프로그램 프로세스에 사용되는 기술 데이터로&#x200B;**구성됩니다**.