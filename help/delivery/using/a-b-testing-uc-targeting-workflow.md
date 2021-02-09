---
solution: Campaign Classic
product: campaign
title: 타겟팅 워크플로우 만들기
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법을 살펴볼 수 있습니다.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 9%

---


# 타겟팅 워크플로우 만들기 {#step-1--creating-a-targeting-workflow}

캠페인의 **[!UICONTROL Targeting and Workflows]** 탭에서 워크플로우를 만들어야 합니다. **[!UICONTROL Query]** 활동, 두 개의 **[!UICONTROL Email delivery]** 활동, **[!UICONTROL Wait]** 활동, **[!UICONTROL JavaScript code]** 활동 및 **[!UICONTROL Delivery]** 활동으로 구성됩니다.**[!UICONTROL Split]**

1. 아직 캠페인을 만들지 않은 경우 캠페인을 만드십시오(자세한 내용은 이 [섹션](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign) 참조).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. **[!UICONTROL Targeting and Workflows]** 탭으로 이동합니다. 

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 기존 작업 과정의 레이블을 변경하거나 **[!UICONTROL Add]**&#x200B;을 클릭하여 새 작업 흐름을 만듭니다(자세한 내용은 이 [섹션](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population) 참조).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 마우스를 사용하여 **[!UICONTROL Query]**(**[!UICONTROL Target]** 탭), **[!UICONTROL Split]**(**[!UICONTROL Target]** 탭), 2개의 **[!UICONTROL Email deliveries]**(**[!UICONTROL Deliveries]** 탭), **[!UICONTROL Wait]** 활동(**[!UICONTROL Flow Control]** 탭), **[!UICONTROL JavaScript code]** 활동(**[!UICONTROL Actions]** 탭) 및 **[!UICONTROL Delivery]** 탭을 포함하여 작업을 작업 다이어그램으로 드래그하여 놓습니다./> 활동(**[!UICONTROL Actions]** 탭).

![](assets/use_case_abtesting_targetwkfl_004.png)
