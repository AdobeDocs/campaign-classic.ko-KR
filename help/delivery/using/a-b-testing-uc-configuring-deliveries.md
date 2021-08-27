---
product: campaign
title: 게재 구성
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법을 알아봅니다
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# 워크플로우에서 게재 구성 {#step-4--configuring-the-deliveries-in-the-workflow}

![](../../assets/common.svg)

[모집단이 만들어지면](a-b-testing-uc-population-samples.md) 게재를 구성할 수 있습니다. 이 사용 사례에서 처음 두 게재를 사용하면 모집단 A와 B로 다른 콘텐츠를 전송할 수 있습니다. 세 번째 게재는 폴백 게재입니다. A 또는 B에 속하지 않는 수신자에게 전송됩니다. 해당 컨텐츠는 스크립트로 계산되며, 어떤 점수가 가장 높은 공개 비율에 따라 A 또는 B와 동일합니다. 게재 A와 B의 결과를 확인하려면 세 번째 게재에 대한 대기 기간을 구성해야 합니다. 세 번째 게재에 **[!UICONTROL Wait]** 활동이 포함된 이유입니다.

1. **[!UICONTROL Split]** 활동으로 이동하고 모집단 A로 지정되는 전환을 워크플로우에 이미 있는 이메일 게재 중 하나에 연결합니다.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. 게재를 두 번 클릭하여 엽니다.
1. 드롭다운 목록에서 게재 A에 사용할 템플릿을 선택합니다.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. **[!UICONTROL Continue]** 을 클릭하여 게재를 본 다음 저장합니다.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. 모집단 B로 지정되는 **[!UICONTROL Split]** 활동의 전환을 두 번째 이메일 게재에 연결합니다.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. 게재를 열고 게재 B에서 템플릿을 선택한 다음 게재를 저장합니다.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. 나머지 모집단에 대해 지정된 전환을 **[!UICONTROL Wait]** 활동에 연결합니다.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. **[!UICONTROL Wait]** 활동을 열고 5일 대기 기간을 구성합니다.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. **[!UICONTROL Wait]** 활동을 **[!UICONTROL JavaScript code]** 활동에 연결합니다.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

이제 스크립트를 만들 수 있습니다. [자세히 알아보기](a-b-testing-uc-script.md)
