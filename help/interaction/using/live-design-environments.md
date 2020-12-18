---
solution: Campaign Classic
product: campaign
title: 라이브/디자인 환경
description: 라이브/디자인 환경
audience: interaction
content-type: reference
topic-tags: managing-environments
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---


# 라이브/디자인 환경{#live-design-environments}

## 운영 원칙 {#operating-principle}

상호 작용은 두 가지 유형의 오퍼 환경에서 작동합니다.

* **[!UICONTROL Design]** 편집 중이며 변경할 수 있는 오퍼가 포함된 환경을 제공합니다. 이 오퍼는 승인 주기를 거치지 않았으며 연락처에 배달되지 않습니다.
* **[!UICONTROL Live]** 승인된 오퍼가 연락처에 표시될 때 포함된 환경을 제공합니다. 이 환경의 오퍼는 읽기 전용입니다.

![](assets/offer_environments_overview_001.png)

각 **[!UICONTROL Design]** 환경은 **[!UICONTROL Live]** 환경에 연결되어 있습니다. 오퍼가 완료되면 컨텐트와 자격 조건 규칙은 승인 주기에 적용됩니다. 이 주기가 완료되면 관련 오퍼가 자동으로 **[!UICONTROL Live]** 환경에 배포됩니다. 지금부터 배송이 가능합니다

기본적으로 상호 작용은 **[!UICONTROL Design]** 환경과 **[!UICONTROL Live]** 환경이 연결되어 있습니다. 두 환경 모두 즉시 받는 사람 테이블을 대상으로 하도록 사전 구성되어 있습니다.

>[!NOTE]
>
>다른 테이블(익명 오퍼의 방문자 테이블 또는 특정 받는 사람 테이블)을 타깃팅하려면 대상 매핑 마법사를 사용하여 환경을 만들어야 합니다. 자세한 내용은 [오퍼 환경 만들기](#creating-an-offer-environment)를 참조하십시오.

![](assets/offer_environments_overview_002.png)

오퍼 관리자와 배달 관리자는 환경에 대한 다양한 뷰를 이용할 수 있습니다. 배달 관리자는 **[!UICONTROL Live]** 오퍼 환경만 보고 오퍼를 사용하여 전달할 수 있습니다. 오퍼 관리자는 **[!UICONTROL Design]** 환경을 보고 변경하고 **[!UICONTROL Live]** 환경을 볼 수 있습니다. 자세한 내용은 [연산자 프로필](../../interaction/using/operator-profiles.md)을 참조하십시오.

## 오퍼 환경 만들기 {#creating-an-offer-environment}

기본적으로 상호 작용은 수신자 테이블(식별된 오퍼)을 대상으로 하기 위해 사전 구성된 환경을 제공합니다. 다른 테이블(익명의 오퍼나 특정 수신자 테이블의 방문자 테이블)을 타깃팅하려면 다음 구성을 적용해야 합니다.

1. 커서를 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]** 노드에 놓습니다. 사용할 배달 매핑(**[!UICONTROL Visitors]**(익명 오퍼를 사용하려면) 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**&#x200B;를 선택합니다.

   ![](assets/offer_env_anonymous_001.png)

1. 마법사의 다음 화면으로 진행하려면 **[!UICONTROL Next]**&#x200B;을 클릭하고 **[!UICONTROL Generate a storage schema for propositions]** 상자를 선택한 다음 **[!UICONTROL Save]**&#x200B;를 클릭합니다.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >상자가 이미 선택되어 있으면 선택을 취소하고 다시 선택합니다.

1. Adobe Campaign은 이전에 활성화된 대상 매핑의 타깃팅 정보와 함께 두 개의 환경(**[!UICONTROL Design]** 및 **[!UICONTROL Live]** )을 만듭니다. 환경은 타깃팅 정보로 미리 구성되어 있습니다.

   **[!UICONTROL Visitor]** 매핑을 활성화한 경우 **[!UICONTROL Environment dedicated to incoming anonymous interactions]** 상자가 환경의 **[!UICONTROL General]** 탭에서 자동으로 체크 인됩니다.

   이 옵션을 사용하면 익명의 상호 작용 특정 함수(특히 환경 오퍼 공간을 구성할 때)를 활성화할 수 있습니다. &quot;식별된&quot; 환경에서 &quot;익명&quot; 환경으로 전환할 수 있는 옵션을 구성할 수도 있습니다.

   예를 들어 수신자 환경 오퍼 공간(식별된 연락처)을 방문자 환경(식별되지 않은 연락처)과 일치하는 오퍼 공간과 연결할 수 있습니다. 이 방법으로 식별되었는지 여부에 따라 연락처에서 다양한 오퍼를 사용할 수 있습니다. 자세한 내용은 [오퍼 공간 만들기](../../interaction/using/creating-offer-spaces.md)를 참조하십시오.

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>인바운드 채널의 익명 인터랙션에 대한 자세한 내용은 [익명 상호 작용](../../interaction/using/anonymous-interactions.md)을 참조하십시오.

