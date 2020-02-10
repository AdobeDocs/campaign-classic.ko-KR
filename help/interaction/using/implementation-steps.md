---
title: 구현 단계
seo-title: 구현 단계
description: 구현 단계
seo-description: null
page-status-flag: never-activated
uuid: 11582071-00a2-4245-af3e-bc81174ce223
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: general-operation
discoiquuid: 7f79c0d8-77b0-4cc6-a888-7dbd32d2f3b6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 구현 단계{#implementation-steps}

## 상호 작용 구성 {#configuring-interaction}

>[!NOTE]
>
>다음 단계는 관리자 **프로필과 디자인** 환경에서만 수행해야 합니다.

1. 사용자 프로필 만들기. 자세한 내용은 연산자 프로필을 [참조하십시오](../../interaction/using/operator-profiles.md).
1. 타깃팅 차원으로 오퍼 환경 만들기 자세한 내용은 오퍼 [환경](../../interaction/using/live-design-environments.md#creating-an-offer-environment)만들기를 참조하십시오.
1. 각 환경에 대한 유형 규칙 만들기 자세한 내용은 오퍼 프레젠테이션 규칙 [만들기 및 참조를 참조하십시오](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule).
1. 각 환경에 대한 오퍼 공간을 만들고 렌더링 기능을 구성합니다. 자세한 내용은 오퍼 공간 [만들기를 참조하십시오](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >식별된 모드에서 단일 채널로 공간이 정의된 경우 이 공간에 대한 고급 매개 변수를 지정해야 합니다.

1. 하나 또는 여러 오퍼를 표시하고 업데이트하기 위해 인바운드 상호 작용에 대한 오퍼 엔진 구성

   다양한 통합 모드는 인바운드 채널 [정보에서](../../interaction/using/about-inbound-channels.md)자세히 설명합니다.

   >[!NOTE]
   >
   >인바운드 웹 채널에 공간이 만들어지면 오퍼가 표시되는 사이트에서도 구성이 필요합니다.

## 오퍼 카탈로그 관리 {#managing-the-offer-catalog-}

>[!NOTE]
>
>다음 단계는 오퍼 관리자가 수행해야 **합니다**.

1. 디자인 환경에서 오퍼 카테고리 만들기 자세한 내용은 오퍼 [카테고리](../../interaction/using/creating-offer-categories.md)만들기를 참조하십시오.
1. 디자인 환경에서 오퍼 만들기 자세한 내용은 오퍼 [만들기를](../../interaction/using/creating-an-offer.md)참조하십시오.
1. 전달 관리자를 위한 라이브 환경에서 오퍼를 사용할 수 있도록 하나 또는 여러 개의 공간에 오퍼를 승인 및 게시할 수 있습니다. 자세한 내용은 오퍼 [승인 및 활성화를](../../interaction/using/approving-and-activating-an-offer.md)참조하십시오.

## 오퍼 카탈로그 사용 {#using-the-offer-catalog-}

>[!NOTE]
>
>다음 단계는 배달 관리자 **프로필에** 의해 수행됩니다. 라이브 환경에서만 오퍼를 편집할 수 있습니다.

1. 캠페인 만들기를 참조하십시오.
1. 캠페인 또는 캠페인 전달의 오퍼를 참조합니다. 자세한 내용은 아웃바운드 [채널](../../interaction/using/about-outbound-channels.md)정보를 참조하십시오.

