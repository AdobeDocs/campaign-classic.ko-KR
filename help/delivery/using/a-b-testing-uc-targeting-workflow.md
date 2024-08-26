---
product: campaign
title: 타겟팅 워크플로 만들기
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법에 대해 알아봅니다
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%

---

# AB 테스트: 타겟팅 워크플로우 만들기 {#step-1--creating-a-targeting-workflow}

캠페인의 **[!UICONTROL Targeting and Workflows]** 탭에서 워크플로우를 만들어야 합니다. **[!UICONTROL Query]** 활동, 두 개의 **[!UICONTROL Email delivery]** 활동에 연결된 **[!UICONTROL Split]** 활동, **[!UICONTROL Wait]** 활동, **[!UICONTROL JavaScript code]** 활동 및 **[!UICONTROL Delivery]** 활동으로 구성됩니다.

1. 아직 만들지 않은 경우 캠페인을 만드십시오. 자세한 내용은 [이 섹션](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)을 참조하세요.

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. **[!UICONTROL Targeting and Workflows]** 탭으로 이동합니다.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 기존 워크플로우의 레이블을 변경하거나 **[!UICONTROL Add]**&#x200B;을(를) 클릭하여 새 워크플로우를 만듭니다. 자세한 내용은 [이 섹션](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)을(를) 참조하십시오.

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 마우스를 사용하여 **[!UICONTROL Query]**(**[!UICONTROL Target]** 탭), **[!UICONTROL Split]**(**[!UICONTROL Target]** 탭), 두 개의 **[!UICONTROL Email deliveries]**(**[!UICONTROL Deliveries]** 탭), **[!UICONTROL Wait]** 활동(**[!UICONTROL Flow Control]** 탭), **[!UICONTROL JavaScript code]** 활동(**[!UICONTROL Actions]** 탭) 및 **[!UICONTROL Delivery]** 활동(**[!UICONTROL Actions]** 탭)을 포함하는 활동을 워크플로 다이어그램으로 끌어서 놓습니다.

![](assets/use_case_abtesting_targetwkfl_004.png)

이제 모집단 샘플을 구성할 수 있습니다. [자세히 알아보기](a-b-testing-uc-population-samples.md).
