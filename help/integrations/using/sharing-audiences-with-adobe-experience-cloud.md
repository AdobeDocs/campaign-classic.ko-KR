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
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---


# Sharing audiences with Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!NOTE]
>
>이 통합을 사용하려면 IMS가 구현되어야 합니다. IMS에 대한 섹션 [을 참조하십시오.](../../integrations/using/about-adobe-id.md).

Adobe Campaign을 사용하면 Adobe Experience Cloud 솔루션 및 핵심 서비스와 고객/세그먼트를 교환하고 공유할 수 있습니다. 이를 위해서는 **Adobe Campaign** 를 **사람 코어 서비스** ( **프로필 및 대상 핵심 서비스라고도 함**)나 Adobe Audience Manager과통합해야 합니다. 그러면 다음 작업을 수행할 수 있습니다.

* 다른 Adobe Experience Cloud 솔루션의 공유 대상/세그먼트를 Adobe Campaign으로 가져올 수 있습니다. 대상은 Adobe Campaign의 목록을 통해 가져올 수 있습니다.
* Adobe Experience Cloud 공유 대상의 형태로 목록을 내보냅니다. 이러한 대상은 사용하는 다른 Adobe Experience Cloud 솔루션에서 사용할 수 있습니다. 전용 **[!UICONTROL Update shared audience]** 활동을 사용하여 워크플로우에서 타깃팅 후 대상을 내보낼 수 있습니다.

>[!CAUTION]
>
>데이터 유형에 따라 Adobe Campaign에서 대상을 가져오는 경우 법적 제한이 적용될 수 있습니다.

통합은 두 가지 유형의 Adobe Experience Cloud ID를 지원합니다.

* **방문자 ID**:이 유형의 식별자는 Adobe Experience Cloud 방문자를 Adobe Campaign 받는 사람과 화해시킵니다.
* **선언된 ID**:이 유형의 식별자는 모든 유형의 데이터를 Adobe Campaign 데이터베이스의 요소와 조정합니다. Adobe Campaign에 사전 정의된 조정 키로 표시됩니다.
