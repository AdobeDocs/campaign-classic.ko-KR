---
product: campaign
title: 최종 게재 정의
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법에 대해 알아봅니다
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: A/B Testing
role: User
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 5%

---

# AB 테스트: 최종 게재 정의 {#step-6--defining-the-final-delivery}

A/B 테스트 승자를 선택하는 스크립트가 만들어지면 최종 게재의 매개 변수를 정의할 수 있습니다.

1. **[!UICONTROL JavaScript code]** 활동을 나머지 **[!UICONTROL Delivery]** 활동에 연결합니다.
1. **[!UICONTROL Delivery]** 활동을 엽니다.
1. 이 활동으로 워크플로우를 완료하려면 **[!UICONTROL Generate an outbound transition]** 옵션을 선택 취소하십시오.
1. 다른 옵션은 기본값으로 둡니다.

   ![](assets/ab_test_final_delivery.png)

**[!UICONTROL Javascript Code]** 활동을 통해 정의된 전환에 지정된 게재를 준비하면 다음 단계에 설명된 대로 이를 승인하고 전송을 시작할 수 있습니다.

이제 워크플로우를 시작할 수 있습니다. [자세히 알아보기](a-b-testing-uc-start-workflow.md).
