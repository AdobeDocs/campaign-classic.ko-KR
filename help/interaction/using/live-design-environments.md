---
product: campaign
title: 라이브/디자인 환경
description: 라이브/디자인 환경
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: 965c4a6a-6535-454d-bd37-e9c8312b4d13
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---

# 라이브/디자인 환경{#live-design-environments}



## 운영 원칙 {#operating-principle}

상호 작용은 다음 두 가지 유형의 오퍼 환경에서 작동합니다.

* **[!UICONTROL Design]** 편집 중이며 변경할 수 있는 오퍼를 포함하는 오퍼 환경을 제공합니다. 이 오퍼는 승인 주기를 거치지 않았고 연락처에 배달되지 않았습니다.
* **[!UICONTROL Live]** 연락처에 표시될 때 승인된 오퍼를 포함하는 환경을 제공합니다. 이 환경의 오퍼는 읽기 전용입니다.

![](assets/offer_environments_overview_001.png)

각 **[!UICONTROL Design]** 환경이 **[!UICONTROL Live]** 환경. 오퍼가 완료되면 해당 컨텐츠 및 자격 규칙은 승인 주기에 적용됩니다. 이 주기가 완료되면 관련 오퍼가 자동으로 **[!UICONTROL Live]** 환경. 지금부터 배송이 가능합니다

기본적으로 상호 작용은 **[!UICONTROL Design]** 환경 및 **[!UICONTROL Live]** 환경에 연결된 환경. 두 환경은 기본 제공 수신자 테이블을 타겟으로 미리 구성되어 있습니다.

>[!NOTE]
>
>다른 테이블(익명의 오퍼나 특정 수신자 테이블의 방문자 테이블)을 타깃팅하려면 대상 매핑 마법사를 사용하여 환경을 만들어야 합니다. 자세한 내용은 [오퍼 환경 만들기](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

오퍼 관리자와 게재 관리자는 환경에 대한 다양한 보기에 액세스할 수 있습니다. 게재 관리자는 **[!UICONTROL Live]** 오퍼 환경을 제공하고 오퍼를 사용하여 제공합니다. 오퍼 관리자는 **[!UICONTROL Design]** 환경 및 보기 **[!UICONTROL Live]** 환경. 자세한 내용은 [운영자 프로필](../../interaction/using/operator-profiles.md).

## 오퍼 환경 만들기 {#creating-an-offer-environment}

기본적으로 상호 작용은 수신자 테이블(식별된 오퍼)을 타깃팅할 사전 구성된 환경과 함께 제공됩니다. 다른 테이블(익명의 오퍼나 특정 수신자 테이블의 방문자 테이블)을 타깃팅하려면 다음 구성을 적용해야 합니다.

1. 커서를 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]** 노드 아래에 있어야 합니다. 사용할 게재 매핑(**[!UICONTROL Visitors]** 익명 오퍼를 사용하려면) **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. 클릭 **[!UICONTROL Next]** 마법사의 다음 화면으로 진행하려면 **[!UICONTROL Generate a storage schema for propositions]** 상자를 클릭하고 **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >확인란이 이미 선택되어 있다면 선택을 취소하고 다시 선택합니다.

1. Adobe Campaign은 두 가지 환경을 만듭니다(**[!UICONTROL Design]** 및 **[!UICONTROL Live]** )을 사용하십시오. 환경은 타깃팅 정보로 미리 구성되어 있습니다.

   활성화한 경우 **[!UICONTROL Visitor]** 매핑, **[!UICONTROL Environment dedicated to incoming anonymous interactions]** 이 상자는 환경의 **[!UICONTROL General]** 탭.

   이 옵션을 사용하면 특히 환경 오퍼 공간을 구성할 때 익명의 상호 작용 특정 기능을 활성화할 수 있습니다. 식별된&quot; 환경에서 &quot;익명&quot; 환경으로 전환할 수 있는 옵션을 구성할 수도 있습니다.

   예를 들어, 수신자 환경 오퍼 공간(식별된 연락처)을 방문자 환경(식별되지 않은 연락처)과 일치하는 오퍼 공간과 연결할 수 있습니다. 이러한 방식으로 연락처가 식별되는지 여부에 따라 연락처에서 다른 오퍼를 사용할 수 있습니다. 자세한 내용은 [오퍼 공간 만들기](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>인바운드 채널에서 익명의 상호 작용에 대한 자세한 내용은 [익명의 상호 작용](../../interaction/using/anonymous-interactions.md).
