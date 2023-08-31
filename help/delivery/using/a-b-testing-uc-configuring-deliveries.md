---
product: campaign
title: 게재 구성
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법에 대해 알아봅니다
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: A/B Testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 1%

---

# AB 테스트: 워크플로우에서 게재 구성 {#step-4--configuring-the-deliveries-in-the-workflow}

한 번 [모집단을 만듭니다.](a-b-testing-uc-population-samples.md), 게재를 구성할 수 있습니다. 이 사용 사례에서 처음 두 게재를 사용하면 모집단 A와 B에 서로 다른 콘텐츠를 보낼 수 있습니다. 세 번째 게재는 폴백 게재입니다. A와 B에 속하지 않는 수신자에게 전송됩니다. 콘텐츠는 스크립트로 계산되며, 가장 높은 공개 비율을 득점한 항목에 따라 A 또는 B 중 하나와 동일합니다. 게재 A와 B의 결과를 알아보기 위해 세 번째 게재의 대기 기간을 구성해야 합니다. 세 번째 게재에 다음이 포함된 이유입니다. **[!UICONTROL Wait]** 활동.

1. 로 이동 **[!UICONTROL Split]** 활동을 실행하고 모집단 A로 지정된 전환을 워크플로우에 이미 있는 이메일 게재 중 하나에 연결합니다.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. 게재를 두 번 클릭하여 엽니다.
1. 드롭다운 목록을 사용하여 게재 A에 대한 템플릿을 선택합니다.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. 클릭 **[!UICONTROL Continue]** 게재를 보고 저장합니다.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. 의 전환 연결 **[!UICONTROL Split]** 활동이 두 번째 이메일 게재로 모집단 B를 지정했습니다.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. 게재를 열고 게재 B에서 템플릿을 선택한 다음 게재를 저장합니다.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. 나머지 모집단으로 지정된 전환을 **[!UICONTROL Wait]** 활동.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. 를 엽니다. **[!UICONTROL Wait]** 활동을 수행하고 5일 대기 기간을 구성합니다.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. 링크 **[!UICONTROL Wait]** 에 대한 활동 **[!UICONTROL JavaScript code]** 활동.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

이제 스크립트를 만들 수 있습니다. [자세히 알아보기](a-b-testing-uc-script.md)
