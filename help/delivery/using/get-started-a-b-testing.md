---
product: campaign
title: A/B 테스트 시작
description: Campaign의 A/B 테스트에 대해 자세히 알아보기
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: A/B Testing
role: User
exl-id: ae046ef6-d850-4222-b82c-8ef5b3da7037
TQID: https://experienceleague.adobe.com/uqiRMLevklMVBiKDSdSy0309jsIBRr05w3mBgOF-RE8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 363
ht-degree: 3%

---

# A/B 테스트 시작 {#get-started-a-b-testing}


A/B 테스트를 통해 여러 버전의 게재를 서로 비교하여 어떤 것이 타겟팅된 모집단에 가장 큰 영향을 주는지 식별할 수 있습니다.

이렇게 하려면 먼저 게재의 여러 변형을 정의해야 합니다. 그런 다음 각 변형은 선택 기준에 따라 더 나은 성과를 결정하기 위해 모집단 샘플로 전송됩니다(열기, 스팸 불만, 특정 링크 클릭 등).

아래 예에서는 게재 대상이 두 그룹으로 분할되었으며, 각 그룹은 타겟팅된 모집단의 50%를 나타냅니다. 각 그룹은 두 개의 서로 다른 프로모션 오퍼와 함께 두 가지 버전의 게재를 받습니다. 게재가 전송되면 프로모션 오퍼의 클릭 수에 따라 변형 A가 더 잘 수행되었다고 판단됩니다.

![](assets/a-b-testing-schema.png)

Campaign Classic을 사용하면 A/B 테스트가 워크플로우를 통해 구현되며, 워크플로우에서 타겟팅할 모집단과 각 변형을 받을 그룹을 지정합니다([a/b 테스트 구성](configuring-a-b-testing.md) 참조).

주요 단계는 다음과 같습니다.

1. 원하는 모집단을 **Target**&#x200B;합니다.
1. **모집단을 분할하고** 게재의 변형을 테스트할 하위 집합으로 분할합니다.

   예를 들어 게재의 한 버전을 대상 모집단의 작은 부분에 보내고 다른 버전을 나머지 모집단에 보낼 수 있습니다. 이렇게 하면 일반적으로 고객에게 전송되는 게재가 아니라 새 버전의 게재를 테스트할 수 있습니다. 타겟팅된 모집단을 3개의 그룹으로 분할하여 세 가지 다른 버전의 게재를 보낼 수도 있습니다.

1. 각 하위 집합에 해당하는 게재의 **여러 버전을 만듭니다**. 테스트할 변형은 제목, 메시지 콘텐츠, 발신자 이름 등이 될 수 있습니다.
1. 워크플로우를 시작한 다음 **게재 로그**&#x200B;를 사용하여 각 변형으로 하위 집합의 동작을 분석합니다.

>[!NOTE]
>
>또한 워크플로우를 사용하면 더 나은 성과를 거둔 게재 변형을 자동으로 식별한 다음 나머지 모집단으로 보내어 프로세스를 자동화할 수 있습니다. 자세한 정보는 이 전용 [사용 사례](a-b-testing-use-case.md)를 참조하세요.
