---
product: campaign
title: Adobe Experience Cloud과 대상 공유
description: Adobe Experience Cloud과 대상 공유
feature: Audiences
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 50%

---

# Adobe Experience Cloud과 대상 공유 {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>Adobe Experience Cloud 솔루션으로 대상을 공유하려면 Adobe Identity Management 시스템을 구현해야 합니다. [IMS에 대해 자세히 알아보기](../../integrations/using/about-adobe-id.md).

Adobe Campaign을 사용하면 Adobe Experience Cloud 서비스와 대상자 및 세그먼트를 공유할 수 있습니다. 두 가지 옵션을 사용할 수 있습니다.

1. Adobe Experience Platform 세그먼트 데이터를 Adobe Campaign으로 보냅니다. 이 통합을 구현하려면 Real-time Customer Data Platform을 Campaign(RTCDP)에 연결해야 합니다. [이 섹션에서 자세히 알아보기](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=ko){target="_blank"}.

1. **Adobe Campaign**&#x200B;을(를) **Experience Cloud 대상** 또는 **Adobe Audience Manager**&#x200B;과(와) 통합합니다. 그러면 다음을 수행할 수 있습니다:

   * 다양한 Adobe Experience Cloud 솔루션의 공유 대상자/세그먼트를 Adobe Campaign으로 가져옵니다. Adobe Campaign의 목록을 통해 대상자를 가져올 수 있습니다.

   * Adobe Experience Cloud 공유 대상자 양식으로 목록을 내보냅니다. 이러한 대상자는 사용하고 있는 여러 Adobe Experience Cloud 솔루션에서 사용할 수 있습니다. 대상자는 워크플로에서 타겟팅한 후 전용 **[!UICONTROL Update shared audience]** 활동을 사용하여 내보낼 수 있습니다.

이 통합은 두 가지 유형의 Adobe Experience Cloud ID를 지원합니다:

* **방문자 ID**: 이 유형의 식별자는 Adobe Experience Cloud 방문자를 Adobe Campaign 수신자와 조정합니다.
* **선언 ID**: 이 유형의 식별자는 모든 유형의 데이터를 Adobe Campaign 데이터베이스의 요소와 조정합니다. Adobe Campaign에서는 사전 정의된 조정 키로 표시됩니다.

  >[!NOTE]
  >
  > 선언된 ID 데이터 소스는 Experience Cloud Assets 통합에도 사용할 수 있습니다.
  >
