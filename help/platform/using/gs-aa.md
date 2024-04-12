---
product: campaign
title: Adobe Campaign 및 Adobe Analytics 작업
description: Adobe Campaign 및 Adobe Analytics 작업
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 985cf088-7546-4875-8e11-cafe5bd3e323
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 23%

---

# Adobe Campaign 및 Adobe Analytics 작업 {#adobe-analytics-connector-gs}

Adobe Analytics 커넥터를 사용하면 Adobe Campaign 및 Adobe Analytics이 **[!UICONTROL Web Analytics connectors]** 패키지를 통해 상호 작용할 수 있습니다. 캠페인 후 사용자 행동에 대한 세그먼트 형태로 데이터를 Adobe Campaign에 전달합니다. 반대로 Adobe Campaign에서 게재한 캠페인의 지표와 특성을 Adobe Analytics으로 보냅니다.

## 보호 기능 및 사전 요구 사항 {#adobe-analytics-connector-guardrails}

Adobe Campaign-Adobe Analytics 커넥터 작업을 시작하기 전에 다음 보호 기능 및 사전 요구 사항을 고려하십시오.

* 이 통합을 위해 IMS(Adobe Identity Management System)를 사용하여 Campaign에 연결해야 합니다. [자세히 알아보기](../../integrations/using/about-adobe-id.md)

* Adobe Analytics 커넥터는 트랜잭션 메시지(메시지 센터)와 호환되지 않습니다.

* Web Analytics 커넥터 추가 기능은 전용 패키지를 통해 환경에 설치해야 합니다.

   * 하이브리드 및 온프레미스 구현의 경우 이 [페이지](../../platform/using/adobe-analytics-provisioning.md)에서 자세히 설명하는 프로비저닝 단계를 따라야 합니다.
   * Hoster 또는 Managed Cloud Service 사용자는 Adobe에 문의하여 Campaign을 Adobe Experience Cloud 서비스 및 솔루션에 연결합니다.


## 구성 및 사용 {#adobe-analytics-connector-usage}

에서 Adobe Campaign 및 Adobe Analytics을 사용하여 작업하는 방법을 알아봅니다. [Adobe Campaign v8 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}.
