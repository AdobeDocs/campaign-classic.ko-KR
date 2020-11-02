---
title: Adobe Experience Cloud과 대상 공유
seo-title: Adobe Experience Cloud과 대상 공유
description: Adobe Experience Cloud과 대상 공유
seo-description: null
page-status-flag: never-activated
uuid: 24ac3463-69ab-48b4-85e0-4fe1948bf5ed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 8f295058-5a78-4512-9bdf-d5f022457e10
translation-type: tm+mt
source-git-commit: 4b98c23f4120cbea6dd54cd68b61202e74bee3e1
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# Sharing audiences with Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>Adobe Experience Cloud 솔루션과 대상을 공유하려면 Adobe Identity Management 시스템을 구현해야 합니다. [IMS에 대한 자세한 내용.](../../integrations/using/about-adobe-id.md).

Adobe Campaign을 사용하면 Adobe Experience Cloud 솔루션 및 핵심 서비스와 대상 및 세그먼트를 공유할 수 있습니다. 두 가지 옵션을 사용할 수 있습니다.

1. Adobe Experience Platform 세그먼트 데이터를 Adobe Campaign으로 보냅니다. 이러한 통합을 구현하려면 실시간 고객 데이터 플랫폼을 캠페인(RTCDP)에 연결해야 합니다. [이 섹션에서 자세한 내용을 살펴보십시오](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).


1. 프로필 및 대상 핵심 서비스라고도 하는 **사용자 코어 서비스****또는 Adobe Audience Manager과** Adobe Campaign **를**&#x200B;통합합니다. 그러면 다음 작업을 수행할 수 있습니다.

   * 다른 Adobe Experience Cloud 솔루션의 공유 대상/세그먼트를 Adobe Campaign으로 가져올 수 있습니다. 대상은 Adobe Campaign의 목록을 통해 가져올 수 있습니다.

   * Adobe Experience Cloud 공유 대상의 형태로 목록을 내보냅니다. 이러한 대상은 사용하는 다른 Adobe Experience Cloud 솔루션에서 사용할 수 있습니다. 전용 **[!UICONTROL Update shared audience]** 활동을 사용하여 워크플로우에서 타깃팅 후 대상을 내보낼 수 있습니다.

이 통합은 두 가지 유형의 Adobe Experience Cloud ID를 지원합니다.

* **방문자 ID**:이 유형의 식별자는 Adobe Experience Cloud 방문자를 Adobe Campaign 받는 사람과 화해시킵니다.
* **선언된 ID**:이 유형의 식별자는 모든 유형의 데이터를 Adobe Campaign 데이터베이스의 요소와 조정합니다. Adobe Campaign에 사전 정의된 조정 키로 표시됩니다.
