---
title: 라이브/디자인 환경
seo-title: 라이브/디자인 환경
description: 라이브/디자인 환경
seo-description: null
page-status-flag: never-activated
uuid: 38ee2f6a-e446-4ac6-b962-40b648eeaf66
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 3cea2be4-4da4-4ebd-a241-1bbaa5abb16e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 3%

---


# 라이브/디자인 환경{#live-design-environments}

## 운영 원칙 {#operating-principle}

상호 작용은 두 가지 유형의 오퍼 환경에서 작동합니다.

* **[!UICONTROL Design]** 오퍼를 제공합니다. 이러한 오퍼는 승인 주기를 거치지 않고 연락처에 배달되지 않습니다.
* **[!UICONTROL Live]** 오퍼를 제공합니다. 이 환경의 오퍼는 읽기 전용입니다.

![](assets/offer_environments_overview_001.png)

각 **[!UICONTROL Design]** 환경은 **[!UICONTROL Live]** 환경에 연결됩니다. 오퍼가 완료되면 해당 컨텐츠 및 자격 조건 규칙이 승인 주기에 적용됩니다. 이 주기가 완료되면 관련 오퍼가 자동으로 **[!UICONTROL Live]** 환경에 배포됩니다. 이 시점부터 배달이 가능합니다

기본적으로 상호 작용은 **[!UICONTROL Design]** 환경과 연결된 **[!UICONTROL Live]** 환경이 함께 제공됩니다. 두 환경 모두 기본적으로 받는 사람 테이블을 타깃팅하도록 미리 구성되어 있습니다.

>[!NOTE]
>
>다른 테이블(익명 오퍼나 특정 수신자 테이블의 방문자 테이블)을 타깃팅하려면 대상 매핑 마법사를 사용하여 환경을 만들어야 합니다. 자세한 내용은 오퍼 환경 [만들기를 참조하십시오](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

오퍼 관리자와 배달 관리자는 환경에 대한 다양한 뷰를 이용할 수 있습니다. 전달 관리자는 오퍼 환경만 보고 오퍼를 사용하여 전달할 수 있습니다. **[!UICONTROL Live]** 오퍼 관리자는 **[!UICONTROL Design]** 환경을 보고 변경하고 환경을 볼 수 **[!UICONTROL Live]** 있습니다. For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).

## 오퍼 환경 만들기 {#creating-an-offer-environment}

기본적으로 상호 작용은 수신자 테이블(식별된 오퍼)을 대상으로 하기 위해 사전 구성된 환경을 제공합니다. 다른 테이블(익명 오퍼나 특정 수신자 테이블의 방문자 테이블)을 타깃팅하려면 다음 구성을 적용해야 합니다.

1. 커서를 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]** 노드 위에 놓습니다. 사용할 배달 매핑을 마우스 오른쪽 단추로 클릭(익명 오퍼를&#x200B;**[!UICONTROL Visitors]** 사용하려는 경우)하고 **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**&#x200B;을 선택합니다.

   ![](assets/offer_env_anonymous_001.png)

1. 마법사 **[!UICONTROL Next]** 의 다음 화면으로 이동하려면 을 클릭하고 **[!UICONTROL Generate a storage schema for propositions]** 상자를 선택한 다음 을 클릭합니다 **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >상자가 이미 선택되어 있으면 선택을 취소한 다음 다시 선택합니다.

1. Adobe Campaign은 이전에 활성화된 대상 매핑의&#x200B;**[!UICONTROL Design]** 타깃팅 정보를 사용하여 두 개의 환경(및 **[!UICONTROL Live]** )을 만듭니다. 환경은 타깃팅 정보로 미리 구성되어 있습니다.

   매핑을 활성화한 **[!UICONTROL Visitor]** 경우, 환경 **[!UICONTROL Environment dedicated to incoming anonymous interactions]** 의 **[!UICONTROL General]** 탭에서 상자가 자동으로 체크 인됩니다.

   이 옵션을 사용하면 환경 오퍼 공간을 구성할 때 익명 상호 작용 특정 기능을 활성화할 수 있습니다. &quot;식별된&quot; 환경에서 &quot;익명&quot; 환경으로 전환할 수 있도록 해주는 옵션을 구성할 수도 있습니다.

   예를 들어 수신자 환경 오퍼 공간(식별된 연락처)을 방문자 환경과 일치하는 오퍼 공간(식별되지 않은 연락처)과 연결할 수 있습니다. 이러한 방식으로 연락처는 s/C가 식별되었는지 여부에 따라 다른 오퍼를 사용할 수 있습니다. 자세한 내용은 오퍼 공간 [만들기를 참조하십시오](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>인바운드 채널의 익명 인터랙션에 대한 자세한 내용은 [익명 인터랙션을 참조하십시오](../../interaction/using/anonymous-interactions.md).

