---
solution: Campaign Classic
product: campaign
title: A/B 테스트 구성
description: Campaign Classic에서 A/B 테스트를 구성하는 방법을 알아봅니다.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: a341980e9d940857388bb2755e5eaa74824cf6ea
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---


# A/B 테스트 구성 {#configuring-a-b-testing}

이 섹션에서는 A/B 테스트를 수행하는 워크플로우를 작성하는 방법에 대해 자세히 설명합니다.

1. 새 워크플로우를 만든 다음 원하는 모집단을 타깃팅하도록 [쿼리](../../workflow/using/query.md) 활동을 구성합니다.

1. [분할](../../workflow/using/split.md) 활동을 추가하여 타깃팅된 모집단을 여러 하위 세트로 나눕니다.

1. 활동을 연 다음 필요에 따라 각 하위 세트를 구성합니다. **[!UICONTROL Split]** 활동을 구성하는 방법에 대한 자세한 내용은 [이 섹션](../../workflow/using/split.md)을 참조하십시오.

   이 예에서는 각 대상을 타깃팅된 인구의 10%에게 제공하여 뉴스레터에 대한 2개의 새 주제를 테스트하려고 합니다.

   ![](assets/ab-testing-split.png)

1. 현재 제목과 함께 뉴스레터를 나머지 모집단에 보내려면 전환을 추가합니다. 이렇게 하려면 **[!UICONTROL General]** 탭에서 **[!UICONTROL Generate complement]** 옵션을 활성화합니다.

   ![](assets/ab-testing-complement.png)

1. 각 하위 세트에 대해 테스트할 배달 버전을 추가합니다.

   ![](assets/ab-testing-delivery.png)

이제 워크플로우를 시작할 수 있습니다. 배달이 전송되면 배달 로그에 있는 3개의 하위 세트의 동작을 추적하여 가장 성공적인 피사체를 확인할 수 있습니다.

또한 워크플로우에서는 더 나은 성과를 거둔 배달 변형을 자동으로 식별하여 나머지 모집단에게 보내 프로세스를 자동화할 수 있습니다. 자세한 내용은 이 전용 [사용 사례](../../delivery/using/a-b-testing-use-case.md)를 참조하십시오.
