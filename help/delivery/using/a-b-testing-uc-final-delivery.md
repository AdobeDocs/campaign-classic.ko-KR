---
solution: Campaign Classic
product: campaign
title: 최종 배달 정의
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법을 살펴볼 수 있습니다.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---


# 최종 배달 정의 {#step-6--defining-the-final-delivery}

A/B 테스트 우승자를 선택하기 위해 스크립트가 만들어지면 최종 전달의 매개 변수를 정의할 수 있습니다.

1. **[!UICONTROL JavaScript code]** 활동을 나머지 **[!UICONTROL Delivery]** 활동에 연결합니다.
1. **[!UICONTROL Delivery]** 활동을 엽니다.
1. **[!UICONTROL Generate an outbound transition]** 옵션의 선택을 취소하여 이 활동과 함께 워크플로우를 완료합니다.
1. 다른 옵션을 기본값으로 둡니다.

   ![](assets/ab_test_final_delivery.png)

전환(**[!UICONTROL Javascript Code]** 활동을 통해 정의됨)에 지정된 배달을 준비하면 다음 단계에 설명된 대로 승인하고 전송을 시작할 수 있습니다.
