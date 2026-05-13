---
product: campaign
title: Adobe Campaign 및 Adobe Analytics 작업
description: Adobe Campaign 및 Adobe Analytics 작업
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 985cf088-7546-4875-8e11-cafe5bd3e323
TQID: https://experienceleague.adobe.com/YuvP0m31wL-WlocUXU3rWovOiwLiA5XrEsnBLlW3nY8
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: d5ef99fa-df0c-4153-bf94-105ad0724167
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 209
ht-degree: 12%

---

# Adobe Campaign 및 Adobe Analytics 작업 {#adobe-analytics-connector-gs}

Adobe Analytics 커넥터를 사용하면 Adobe Campaign 및 Adobe Analytics이 **[!UICONTROL Web Analytics connectors]** 패키지를 통해 상호 작용할 수 있습니다. 캠페인 후 사용자 행동에 대한 세그먼트 형태로 데이터를 Adobe Campaign에 전달합니다. 반대로 Adobe Campaign에서 게재한 캠페인의 지표와 특성을 Adobe Analytics으로 보냅니다.

## 보호 기능 및 사전 요구 사항 {#adobe-analytics-connector-guardrails}

Adobe Campaign-Adobe Analytics 커넥터 작업을 시작하기 전에 다음 보호 기능 및 사전 요구 사항을 고려하십시오.

* 이 통합을 위해 IMS(Adobe Identity Management System)를 사용하여 Campaign에 연결해야 합니다. [자세히 알아보기](../../integrations/using/about-adobe-id.md).

* Adobe Analytics 커넥터는 트랜잭션 메시지(메시지 센터)와 호환되지 않습니다.

* Web Analytics 커넥터 추가 기능은 전용 패키지를 통해 환경에 설치해야 합니다.

   * 하이브리드 및 온-프레미스 구현의 경우 이 [페이지](adobe-analytics-provisioning.md)에서 자세히 설명하는 프로비저닝 단계를 따라야 합니다.
   * Hoster 또는 Managed Cloud Services 사용자는 Adobe에 문의하여 Campaign을 Adobe Experience Cloud 서비스 및 솔루션에 연결합니다.


## 구성 및 사용 {#adobe-analytics-connector-usage}

이 통합을 사용하려면 [이 페이지](oauth-technical-account.md)에 자세히 설명된 대로 Adobe 기술 계정을 만들어야 합니다.

[Adobe Campaign v8 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}에서 Adobe Analytics 및 Adobe Campaign을 사용하여 작업하는 방법을 알아보세요.
