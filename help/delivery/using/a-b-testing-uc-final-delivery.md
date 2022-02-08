---
product: campaign
title: 최종 게재 정의
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법을 알아봅니다
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 90c52ec144a6a3c1b534a80507e38fa3ed64fc83
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 9%

---

# 최종 게재 정의 {#step-6--defining-the-final-delivery}

![](../../assets/common.svg)

스크립트가 만들어져서 A/B 테스트 승자를 선택하면 최종 게재의 매개 변수를 정의할 수 있습니다.

1. 연결 **[!UICONTROL JavaScript code]** 나머지 작업에 대한 활동 **[!UICONTROL Delivery]** 활동.
1. 를 엽니다. **[!UICONTROL Delivery]** 활동.
1. 선택을 취소하고 **[!UICONTROL Generate an outbound transition]** 이 활동으로 워크플로우를 완료하는 선택 사항입니다.
1. 다른 옵션은 기본값으로 둡니다.

   ![](assets/ab_test_final_delivery.png)

전환에서 지정된 게재를 준비하여( **[!UICONTROL Javascript Code]** 활동)을 만들 때, 다음 단계에 설명된 대로 승인하고 전송을 시작할 수 있습니다.

이제 워크플로우를 시작할 수 있습니다. [자세히 알아보기](a-b-testing-uc-start-workflow.md)
