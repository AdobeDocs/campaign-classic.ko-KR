---
product: campaign
title: 구현 단계
description: Campaign 상호 작용 모듈에 대한 구현 단계
feature: Interaction, Offers
exl-id: 82b88ab7-6a95-4bb3-b8b3-abea0fdd4ca0
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 2%

---

# 구현 단계{#implementation-steps}

![](../../assets/v7-only.svg)

## 상호 작용 구성 {#configuring-interaction}

>[!NOTE]
>
>다음 단계는 **관리자** 프로필 및 디자인 환경에서만 사용할 수 있습니다.

1. 사용자 프로필 만들기 자세한 내용은 [운영자 프로필](../../interaction/using/operator-profiles.md).
1. 타겟팅 차원으로 오퍼 환경 만들기 자세한 내용은 [오퍼 환경 만들기](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. 각 환경에 대한 유형화 규칙 만들기 자세한 내용은 [오퍼 프레젠테이션 규칙 만들기 및 참조](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule).
1. 각 환경에 대한 오퍼 공간 만들기 및 렌더링 기능 구성 자세한 내용은 [오퍼 공간 만들기](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >식별된 모드의 단일 채널로 공간이 정의된 경우 이 스페이스의 고급 매개 변수를 지정해야 합니다.

1. 하나 또는 여러 오퍼를 제공하고 업데이트하기 위해 인바운드 상호 작용에 대한 오퍼 엔진 구성

   다양한 통합 모드는 [인바운드 채널 정보](../../interaction/using/about-inbound-channels.md).

   >[!NOTE]
   >
   >인바운드 웹 채널에 공간을 만들 때 오퍼가 표시될 사이트에서 구성도 필요합니다.

## 오퍼 카탈로그 관리 {#managing-the-offer-catalog-}

>[!NOTE]
>
>다음 단계는 **오퍼 관리자**.

1. 디자인 환경에서 오퍼 카테고리 만들기. 자세한 내용은 [오퍼 카테고리 만들기](../../interaction/using/creating-offer-categories.md).
1. 디자인 환경에서 오퍼 만들기 자세한 내용은 [오퍼 만들기](../../interaction/using/creating-an-offer.md).
1. 게재 관리자의 라이브 환경에서 사용할 수 있도록 하기 위해 하나 또는 여러 공간에 오퍼를 승인 및 게시합니다. 자세한 내용은 [오퍼 승인 및 활성화](../../interaction/using/approving-and-activating-an-offer.md).

## 오퍼 카탈로그 사용 {#using-the-offer-catalog-}

>[!NOTE]
>
>다음 단계는 **게재 관리자** 프로필 참조. 라이브 환경에서만 오퍼를 편집할 수 있습니다.

1. 캠페인 만들기.
1. 캠페인 또는 캠페인 게재의 오퍼 참조. 자세한 내용은 [아웃바운드 채널 기본 정보](../../interaction/using/about-outbound-channels.md).
