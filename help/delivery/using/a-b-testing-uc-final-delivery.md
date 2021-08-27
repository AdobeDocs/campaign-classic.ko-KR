---
product: campaign
title: 최종 게재 정의
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법을 알아봅니다.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 9%

---

# 최종 게재 정의 {#step-6--defining-the-final-delivery}

![](../../assets/common.svg)

스크립트가 만들어져서 A/B 테스트 승자를 선택하면 최종 게재의 매개 변수를 정의할 수 있습니다.

1. **[!UICONTROL JavaScript code]** 활동을 나머지 **[!UICONTROL Delivery]** 활동에 연결합니다.
1. **[!UICONTROL Delivery]** 활동을 엽니다.
1. **[!UICONTROL Generate an outbound transition]** 옵션의 선택을 취소하여 이 활동으로 워크플로우를 완료합니다.
1. 다른 옵션은 기본값으로 둡니다.

   ![](assets/ab_test_final_delivery.png)

전환(**[!UICONTROL Javascript Code]** 활동을 통해 정의됨)에 지정된 게재를 준비하면 다음 단계에 설명된 대로 승인하고 전송을 시작할 수 있습니다.

이제 워크플로우를 시작할 수 있습니다. [자세히 알아보기](a-b-testing-uc-start-workflow.md)
