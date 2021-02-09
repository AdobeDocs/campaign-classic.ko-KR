---
solution: Campaign Classic
product: campaign
title: 이 사용 사례 정보
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법을 살펴볼 수 있습니다.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# 이 사용 사례 {#about-use-case} 정보

이 경우 타깃팅 워크플로우를 통해 두 개의 이메일 배달 컨텐츠를 비교하려고 합니다. 메시지와 텍스트는 두 배달에서 동일합니다.레이아웃만 변경됩니다.

타깃팅된 인구는 3으로 나누어집니다.두 개의 테스트 그룹과 나머지 모집단. 각 테스트 그룹에 다른 버전의 배달이 전송됩니다.

배달을 수행한 후 최적 공개 비율의 결과를 수집하기 전에 5일 대기 기간이 구성됩니다. 점수가 가장 높은 전달 내용은 스크립트로 복구되고 테스트 그룹으로 사용되지 않은 모집단으로 전송됩니다.

가장 적합한 배달을 결정하는 기준은 귀하의 요구 사항에 맞게 변경될 수 있습니다. 개방 비율, 클릭스루 비율, 가입 비율, 재활동 등이 될 수 있습니다.

또한 이 사용 사례에 자세히 설명된 테스트는 2회의 게재에만 해당되지만 필요한 만큼 여러 버전을 테스트할 수 있습니다. 워크플로우에 활동을 추가하면 됩니다.

이 사용 사례를 수행하는 주요 단계는 다음과 같습니다.

* [1단계:타깃팅 워크플로우 만들기](#step-1--creating-a-targeting-workflow)
* [2단계:모집단 샘플 구성](#step-2--configuring-population-samples)
* [3단계:2개의 배달 템플릿 만들기](#step-3--creating-two-delivery-templates)
* [4단계:워크플로우에서 배달 구성](#step-4--configuring-the-deliveries-in-the-workflow)
* [5단계:스크립트 만들기](#step-5--creating-the-script)
* [7단계:워크플로우 시작](#step-7--starting-the-workflow)
* [8단계:결과를 분석합니다](#step-8--analyzing-the-result).

**관련 항목:**

* [A/B 테스트 시작](../../delivery/using/get-started-a-b-testing.md)
* [A/B 테스트 구성](../../delivery/using/configuring-a-b-testing.md)
