---
product: campaign
title: 기본 원칙
description: 기본 원칙
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: b13ecfc9-1723-42b2-ab30-d5637cc3d0dd
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 1%

---

# 기본 원칙{#fundamental-principles}



## 환경 배포 {#deploying-environments}

오퍼를 관리할 때 사용되는 각 타깃팅 차원에 대해 두 개의 환경이 있습니다.

* 오퍼 관리자가 오퍼를 만들고 분류하고 편집하고 승인 프로세스를 시작하여 오퍼를 사용할 수 있는 디자인 환경입니다. 각 카테고리에 대한 규칙, 오퍼를 표시할 수 있는 오퍼 공간 및 오퍼의 자격 조건을 정의하는 데 사용되는 사전 정의된 필터도 이 환경에서 정의됩니다.

   카테고리를 온라인 환경에서 수동으로 게시할 수도 있습니다.

   오퍼 승인 프로세스는 [오퍼 승인 및 활성화](../../interaction/using/approving-and-activating-an-offer.md) 섹션을 참조하십시오.

* 디자인 환경에서 승인된 오퍼가 포함된 라이브 환경과, 디자인 환경에 구성된 다양한 오퍼 공간, 필터, 카테고리 및 규칙을 모두 찾을 수 있습니다. 오퍼 엔진에 대한 호출 동안 엔진은 항상 라이브 환경의 오퍼를 사용합니다.

오퍼는 승인 프로세스 중에 선택한 오퍼 공간에만 배포됩니다. 따라서 오퍼는 라이브될 수 있지만 라이브이기도 한 오퍼 공간에서 사용할 수 없습니다.

![](assets/architecture_interaction1.png)

## 상호 작용 유형 및 연락처 메서드 {#interaction-types-and-contact-methods}

다음 두 가지 유형의 상호 작용이 있습니다. 연락처에 의해 시작된 인바운드 상호 작용 및 아웃바운드 상호 작용(오퍼 디자이너에서 시작).

이러한 두 가지 유형의 상호 작용은 단일 모드(단일 연락처에 대해 오퍼가 계산됨) 또는 배치 모드(연락 집합에 대해 오퍼가 계산됨)에서 수행할 수 있습니다. 일반적으로 인바운드 상호 작용은 단일 모드에서 수행되고 아웃바운드 상호 작용은 배치 모드에서 수행됩니다. 하지만 아웃바운드 상호 작용을 단일 모드에서 수행하는 트랜잭션 메시지와 같은 특정 예외 사항이 있을 수 있습니다( 참조) [이 섹션](../../message-center/using/about-transactional-messaging.md)).

오퍼를 제공할 수 있거나 제공해야 하는 즉시(수행된 구성에 따라) 오퍼 엔진이 중간 역할을 합니다. 연락처에 대해 수신한 데이터와 애플리케이션에 지정된 대로 적용할 수 있는 다양한 규칙을 결합하여 사용할 수 있는 연락 중 가장 적합한 오퍼를 자동으로 계산합니다.

![](assets/architecture_interaction2.png)
