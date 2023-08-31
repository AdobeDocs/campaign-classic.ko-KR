---
product: campaign
title: AB 테스트 사용 사례
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법에 대해 알아봅니다
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: A/B Testing
role: User
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 5%

---

# AB 테스트: A/B 테스트 이 사용 사례 {#ab-testing-use-case}

이 사용 사례에서는 타겟팅 워크플로우를 통해 두 개의 이메일 게재 콘텐츠를 비교하려고 합니다. 메시지와 텍스트는 두 게재에서 동일합니다. 레이아웃만 변경됩니다.

대상 모집단은 두 개의 테스트 그룹과 나머지 모집단, 이렇게 세 개로 나뉩니다. 다른 버전의 게재가 각 테스트 그룹으로 전송됩니다.

게재 후 최상의 공개 요금 결과를 수집하기 전에 5일 대기 기간이 구성됩니다. 그런 다음 점수가 가장 높은 게재 콘텐츠는 스크립트로 복구되고 테스트 그룹으로 사용되지 않은 모집단으로 전송됩니다.

가장 적합한 게재를 결정하는 기준은 사용자의 요구 사항에 맞게 변경될 수 있습니다. 열람율, 클릭스루 비율, 구독률, 반응성 등이 될 수 있습니다.

또한 테스트는 두 게재에만 관련된 이 사용 사례에 자세히 설명되어 있지만 필요한 만큼 버전을 테스트할 수 있습니다. 워크플로우에 활동을 추가하기만 하면 됩니다.

이 사용 사례를 수행하는 주요 단계는 다음과 같습니다.

* [1단계: 타겟팅 워크플로우 만들기](a-b-testing-uc-targeting-workflow.md)
* [2단계: 모집단 샘플 구성](a-b-testing-uc-population-samples.md)
* [3단계: 두 개의 게재 템플릿 만들기](a-b-testing-uc-delivery-templates.md)
* [4단계: 워크플로우에서 게재 구성](a-b-testing-uc-configuring-deliveries.md)
* [5단계: 스크립트 만들기](a-b-testing-uc-script.md)
* [6단계: 최종 게재 정의](a-b-testing-uc-final-delivery.md)
* [7단계: 워크플로우 시작](a-b-testing-uc-start-workflow.md)
* [8단계: 결과 분석](a-b-testing-uc-analyzing.md)

**관련 항목:**

* [A/B 테스트 시작](get-started-a-b-testing.md)
* [A/B 테스트 구성](configuring-a-b-testing.md)
