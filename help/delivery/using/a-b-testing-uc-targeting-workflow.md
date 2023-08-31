---
product: campaign
title: 타기팅 워크플로우 만들기
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법에 대해 알아봅니다
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 8%

---

# AB 테스트: 타겟팅 워크플로우 만들기 {#step-1--creating-a-targeting-workflow}

에서 워크플로우를 만들어야 합니다. **[!UICONTROL Targeting and Workflows]** 캠페인의 탭입니다. Id는 **[!UICONTROL Query]** 활동, a **[!UICONTROL Split]** 두 개에 연결된 활동 **[!UICONTROL Email delivery]** 활동, a **[!UICONTROL Wait]** 활동, a **[!UICONTROL JavaScript code]** 활동 및 **[!UICONTROL Delivery]** 활동.

1. 캠페인을 아직 만들지 않은 경우 캠페인을 만듭니다(자세한 내용은 다음을 참조하십시오.) [이 섹션](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. **[!UICONTROL Targeting and Workflows]** 탭으로 이동합니다. 

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 기존 워크플로우의 레이블을 변경하거나 **[!UICONTROL Add]** 새 템플릿을 만들려면(자세한 내용은 다음을 참조하십시오.) [이 섹션](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 마우스를 사용하여 활동을 워크플로 다이어그램으로 끌어서 놓습니다. **[!UICONTROL Query]** (**[!UICONTROL Target]** tab), a **[!UICONTROL Split]** (**[!UICONTROL Target]** tab), 2 **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** tab), a **[!UICONTROL Wait]** 활동(**[!UICONTROL Flow Control]** tab), a **[!UICONTROL JavaScript code]** 활동(**[!UICONTROL Actions]** tab) 및 **[!UICONTROL Delivery]** 활동(**[!UICONTROL Actions]** 탭).

![](assets/use_case_abtesting_targetwkfl_004.png)

이제 모집단 샘플을 구성할 수 있습니다. [자세히 알아보기](a-b-testing-uc-population-samples.md)
