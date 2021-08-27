---
product: campaign
title: 타기팅 워크플로우 만들기
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법을 알아봅니다.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 10%

---

# 타기팅 워크플로우 만들기 {#step-1--creating-a-targeting-workflow}

![](../../assets/common.svg)

캠페인의 **[!UICONTROL Targeting and Workflows]** 탭에서 워크플로우를 만들어야 합니다. **[!UICONTROL Query]** 활동, 두 개의 **[!UICONTROL Email delivery]** 활동, **[!UICONTROL Wait]** 활동, **[!UICONTROL JavaScript code]** 활동 및 **[!UICONTROL Delivery]** 활동으로 구성됩니다.**[!UICONTROL Split]**

1. 아직 작성하지 않았다면 캠페인을 만드십시오(자세한 내용은 [이 섹션](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign) 참조).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. **[!UICONTROL Targeting and Workflows]** 탭으로 이동합니다. 

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 기존 워크플로우의 레이블을 변경하거나 **[!UICONTROL Add]** 을(를) 클릭하여 새 워크플로우를 만듭니다(자세한 내용은 [이 섹션](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population) 참조).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. **[!UICONTROL Query]** (**[!UICONTROL Target]** 탭), **[!UICONTROL Split]** (**[!UICONTROL Target]** 탭), 두 개의 **[!UICONTROL Email deliveries]**(**[!UICONTROL Deliveries]** 탭), **[!UICONTROL Wait]** 활동(**[!UICONTROL Flow Control]** 탭), **[!UICONTROL JavaScript code]** 활동(**[!UICONTROL Actions]** 탭), **[!UICONTROL Delivery]** 활동(**[!UICONTROL Actions]** 탭)을 포함하는 활동을 마우스를 사용하여 워크플로우 다이어그램에 끌어다 놓습니다.

![](assets/use_case_abtesting_targetwkfl_004.png)

이제 모집단 샘플을 구성할 수 있습니다. [자세히 알아보기](a-b-testing-uc-population-samples.md)
