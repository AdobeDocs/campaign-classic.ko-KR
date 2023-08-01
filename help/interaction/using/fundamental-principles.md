---
product: campaign
title: 기본 원칙
description: 기본 원칙
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: b13ecfc9-1723-42b2-ab30-d5637cc3d0dd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 2%

---

# 기본 원칙{#fundamental-principles}



## 환경 배포 {#deploying-environments}

오퍼를 관리할 때 사용되는 각 타겟팅 차원에는 두 가지 환경이 있습니다.

* 오퍼 관리자가 오퍼를 만들고 분류하고, 편집하고, 사용할 수 있도록 승인 프로세스를 시작하는 디자인 환경입니다. 각 카테고리에 대한 규칙, 오퍼가 표시될 수 있는 오퍼 공간 및 오퍼의 자격 조건을 정의하는 데 사용되는 사전 정의된 필터 도 이 환경에서 정의됩니다.

  범주는 온라인 환경에서 수동으로 게시할 수도 있습니다.

  오퍼 승인 프로세스는 다음에 자세히 설명되어 있습니다. [오퍼 승인 및 활성화](../../interaction/using/approving-and-activating-an-offer.md) 섹션.

* 디자인 환경의 승인된 오퍼와 디자인 환경에 구성된 다양한 오퍼 공간, 필터, 카테고리 및 규칙이 모두 있는 라이브 환경을 찾을 수 있습니다. 오퍼 엔진을 호출하는 동안 엔진은 항상 라이브 환경의 오퍼를 사용합니다.

오퍼는 승인 프로세스 중에 선택한 오퍼 공간에만 배포됩니다. 따라서, 오퍼는 라이브 상태이지만 라이브 상태인 오퍼 공간에서는 사용할 수 없습니다.

![](assets/architecture_interaction1.png)

## 상호 작용 유형 및 연락 방법 {#interaction-types-and-contact-methods}

상호 작용에는 인바운드 상호 작용(연락처에 의해 시작됨)과 아웃바운드 상호 작용(오퍼 디자이너에 의해 시작됨)의 두 가지 유형이 있습니다.

이러한 두 가지 유형의 상호 작용은 단일 모드(단일 연락처에 대해 오퍼가 계산됨) 또는 배치 모드(연락처 세트에 대해 오퍼가 계산됨)에서 수행할 수 있습니다. 일반적으로 인바운드 상호 작용은 단일 모드에서 수행되고 아웃바운드 상호 작용은 배치 모드에서 수행됩니다. 그럼에도 불구하고 아웃바운드 상호 작용이 단일 모드에서 수행되는 등의 트랜잭션 메시지에 대한 특정 예외가 있을 수 있습니다(참조) [이 섹션](../../message-center/using/about-transactional-messaging.md)).

오퍼가 표시될 수 있거나 표시되어야 하는 즉시(수행되는 구성에 따라) 오퍼 엔진은 연락처에 대해 받은 데이터와 애플리케이션에 지정된 대로 적용할 수 있는 다른 규칙을 결합하여 사용 가능한 연락처 중 연락처에 대해 가능한 최상의 오퍼를 자동으로 계산합니다.

![](assets/architecture_interaction2.png)
