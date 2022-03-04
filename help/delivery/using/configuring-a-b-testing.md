---
product: campaign
title: A/B 테스트 구성
description: Campaign Classic에서 A/B 테스트를 구성하는 방법을 알아봅니다.
feature: A/B Testing
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 3%

---

# A/B 테스트 구성 {#configuring-a-b-testing}

![](../../assets/common.svg)

이 섹션에서는 A/B 테스트를 수행하는 워크플로우를 작성하는 방법에 대해 자세히 설명합니다.

1. 새 워크플로우를 만든 다음 [쿼리](../../workflow/using/query.md) 활동을 통해 원하는 모집단을 타겟팅할 수 있습니다.

1. 추가 [분할](../../workflow/using/split.md) 활동을 통해 타겟팅된 모집단을 여러 하위 집합으로 분할합니다.

1. 활동을 열고 필요에 따라 각 하위 세트를 구성합니다. 구성 방법에 대한 자세한 내용 **[!UICONTROL Split]** 활동, [이 섹션](../../workflow/using/split.md).

   이 예에서는 각 뉴스레터를 대상으로 타겟팅된 모집단의 10%에게 제시하여 2개의 새 주제를 테스트하려고 합니다.

   ![](assets/ab-testing-split.png)

1. 현재 주제와 함께 Newsletter를 나머지 모집단으로 보내려면 전환을 추가합니다. 이렇게 하려면 를 활성화합니다 **[!UICONTROL Generate complement]** 옵션 **[!UICONTROL General]** 탭.

   ![](assets/ab-testing-complement.png)

1. 각 하위 세트에 대해 테스트할 게재 버전을 추가합니다.

   ![](assets/ab-testing-delivery.png)

이제 워크플로우를 시작할 수 있습니다. 게재가 전송되면 가장 성공적인 주체를 확인하기 위해 게재 로그에서 세 개의 하위 세트의 동작을 추적할 수 있습니다.

또한 워크플로우를 사용하면 보다 잘 수행된 게재 변형을 자동으로 식별한 다음 나머지 모집단으로 전송하여 프로세스를 자동화할 수 있습니다. 자세한 내용은 이 전용 페이지를 참조하십시오 [사용 사례](a-b-testing-use-case.md).
