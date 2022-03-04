---
product: campaign
title: 게재 구성
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법을 알아봅니다
feature: A/B Testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# 워크플로우에서 게재 구성 {#step-4--configuring-the-deliveries-in-the-workflow}

![](../../assets/common.svg)

한 번 [모집단 생성](a-b-testing-uc-population-samples.md)를 설정하는 것이 좋습니다. 이 사용 사례에서 처음 두 게재를 사용하면 모집단 A와 B로 다른 콘텐츠를 전송할 수 있습니다. 세 번째 게재는 폴백 게재입니다. A 또는 B에 속하지 않는 수신자에게 전송됩니다. 해당 컨텐츠는 스크립트로 계산되며, 어떤 점수가 가장 높은 공개 비율에 따라 A 또는 B와 동일합니다. 게재 A 및 B의 결과를 확인하려면 세 번째 게재에 대한 대기 기간을 구성해야 합니다. 이것이 세 번째 게재에 가 포함되는 이유입니다 **[!UICONTROL Wait]** 활동.

1. 로 이동합니다. **[!UICONTROL Split]** 활동 및 활동 링크를 통해 모집단 A로 지정되는 전환을 워크플로우에 이미 있는 이메일 게재 중 하나에 연결합니다.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. 게재를 두 번 클릭하여 엽니다.
1. 드롭다운 목록에서 게재 A에 사용할 템플릿을 선택합니다.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. 클릭 **[!UICONTROL Continue]** 게재를 보려면 저장한 다음,

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. 전환 연결 **[!UICONTROL Split]** 활동(모집단 B가 두 번째 이메일 게재로 지정됨).

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. 게재를 열고 게재 B에서 템플릿을 선택한 다음 게재를 저장합니다.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. 나머지 모집단에 대해 지정된 전환을 **[!UICONTROL Wait]** 활동.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. 를 엽니다. **[!UICONTROL Wait]** 활동을 수행하고 5일 대기 기간을 구성합니다.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. 링크 **[!UICONTROL Wait]** 활동 대상 **[!UICONTROL JavaScript code]** 활동.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

이제 스크립트를 만들 수 있습니다. [자세히 알아보기](a-b-testing-uc-script.md)
