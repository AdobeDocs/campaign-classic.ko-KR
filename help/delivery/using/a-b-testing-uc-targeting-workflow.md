---
product: campaign
title: 타기팅 워크플로우 만들기
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법을 알아봅니다
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 10%

---

# 타기팅 워크플로우 만들기 {#step-1--creating-a-targeting-workflow}



에서 워크플로우를 만들어야 합니다 **[!UICONTROL Targeting and Workflows]** 캠페인의 탭입니다. 그건.. **[!UICONTROL Query]** 활동, **[!UICONTROL Split]** 두 개 연결된 활동 **[!UICONTROL Email delivery]** 활동, **[!UICONTROL Wait]** 활동, **[!UICONTROL JavaScript code]** 활동 및 **[!UICONTROL Delivery]** 활동.

1. 아직 작성하지 않았다면 캠페인을 만드십시오(자세한 내용은 다음을 참조하십시오.) [이 섹션](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. **[!UICONTROL Targeting and Workflows]** 탭으로 이동합니다. 

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 기존 워크플로우의 레이블을 변경하거나 **[!UICONTROL Add]** 새 항목을 만들려면(자세한 내용은) [이 섹션](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 마우스를 사용하여 활동을 워크플로우 다이어그램으로 끌어서 놓습니다. 여기에는 **[!UICONTROL Query]** (**[!UICONTROL Target]** 탭), **[!UICONTROL Split]** (**[!UICONTROL Target]** 탭), 두 개 **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** 탭), **[!UICONTROL Wait]** 활동 (**[!UICONTROL Flow Control]** 탭), **[!UICONTROL JavaScript code]** 활동 (**[!UICONTROL Actions]** 탭) 및 **[!UICONTROL Delivery]** 활동 (**[!UICONTROL Actions]** 탭).

![](assets/use_case_abtesting_targetwkfl_004.png)

이제 모집단 샘플을 구성할 수 있습니다. [자세히 알아보기](a-b-testing-uc-population-samples.md)
