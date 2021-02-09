---
solution: Campaign Classic
product: campaign
title: A/B 테스트 시작
description: Campaign Classic의 A/B 테스트에 대해 자세히 알아보십시오.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---


# {#get-started-a-b-testing} A/B 테스트 시작하기

A/B 테스트를 사용하면 타깃팅된 모집단에게 가장 큰 영향을 줄 버전을 식별하기 위해 서로 다른 버전의 전달을 비교할 수 있습니다.

이렇게 하려면 먼저 게재의 여러 변형을 정의해야 합니다. 그런 다음 각 변형이 모집단 샘플로 전송되어 선택한 기준(열기, 스팸 불만, 특정 링크 클릭 수 등)에 따라 더 나은 결과를 결정합니다.

아래 예에서, 전달 대상은 타깃팅된 인구의 50%를 나타내는 두 개의 그룹으로 분할되었습니다. 각 그룹은 2개의 서로 다른 프로모션 오퍼와 함께 2개의 전달 버전을 받습니다. 배달이 전송되면 변형 A가 프로모션 오퍼에 대한 클릭 수를 기준으로 더 나은 성과를 수행한 것으로 결론을 내렸습니다.

![](assets/a-b-testing-schema.png)

Campaign Classic에서 A/B 테스트는 각 변형을 받을 그룹과 타깃팅할 모집단을 지정하는 워크플로우를 통해 구현됩니다([Configuring a/b testing](../../delivery/using/configuring-a-b-testing.md) 참조).

주요 단계는 다음과 같습니다.

1. **원하는** 인구를 타깃팅합니다.
1. **게재의** 변형을 테스트할 하위 세트로 채우기를 분할합니다.

   예를 들어 한 버전의 전달을 타깃팅된 인구의 일부에 보내고 다른 버전을 나머지 모집단으로 보낼 수 있습니다. 이를 통해 고객에게 일반적으로 발송되는 게재와 달리 새로운 버전의 제공을 테스트할 수 있습니다. 3개의 서로 다른 버전의 제공을 보내기 위해 타깃팅된 모집단을 3개의 그룹으로 나눌 수도 있습니다.

1. **각** 하위 세트에 해당하는 게재의 여러 버전을 만듭니다. 테스트할 변형은 제목, 메시지 내용, 발신자 이름 등이 될 수 있습니다.
1. 워크플로우를 시작한 다음 **배달 로그**&#x200B;를 사용하여 각 변형이 있는 하위 세트의 동작을 분석합니다.

>[!NOTE]
>
>또한 워크플로우에서는 더 나은 성과를 거둔 배달 변형을 자동으로 식별하여 나머지 모집단에게 보내 프로세스를 자동화할 수 있습니다. 자세한 내용은 이 전용 [사용 사례](../../delivery/using/a-b-testing-use-case.md)를 참조하십시오.
