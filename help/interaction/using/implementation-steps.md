---
solution: Campaign Classic
product: campaign
title: 구현 단계
description: 구현 단계
audience: interaction
content-type: reference
topic-tags: general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 3%

---


# 구현 단계{#implementation-steps}

## 상호 작용 구성 {#configuring-interaction}

>[!NOTE]
>
>다음 단계는 **Administrator** 프로필에 의해 수행되고 디자인 환경에서만 수행해야 합니다.

1. 사용자 프로필 만들기. 자세한 내용은 [연산자 프로필](../../interaction/using/operator-profiles.md)을 참조하십시오.
1. 타깃팅 차원을 기준으로 오퍼 환경 만들기. 자세한 내용은 [오퍼 환경 만들기](../../interaction/using/live-design-environments.md#creating-an-offer-environment)를 참조하십시오.
1. 각 환경에 대한 유형 규칙 만들기 자세한 내용은 [오퍼 프레젠테이션 규칙 만들기 및 참조](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule)를 참조하십시오.
1. 각 환경에 대한 오퍼 공간을 만들고 렌더링 기능을 구성합니다. 자세한 내용은 [오퍼 공간 만들기](../../interaction/using/creating-offer-spaces.md)를 참조하십시오.

   >[!NOTE]
   >
   >식별된 모드에서 단일 채널로 공백이 정의된 경우 이 공간에 대한 고급 매개 변수를 지정해야 합니다.

1. 하나 이상의 오퍼를 표시하고 업데이트하려면 인바운드 상호 작용에 대한 오퍼 엔진 구성을 참조하십시오.

   다양한 통합 모드는 [인바운드 채널 정보](../../interaction/using/about-inbound-channels.md)에 자세히 설명되어 있습니다.

   >[!NOTE]
   >
   >인바운드 웹 채널에 공간이 생성되면 오퍼가 표시될 사이트에서도 구성이 필요합니다.

## 오퍼 카탈로그 관리 {#managing-the-offer-catalog-}

>[!NOTE]
>
>다음 단계는 **오퍼 관리자**&#x200B;에서 수행해야 합니다.

1. 디자인 환경에서 오퍼 카테고리 만들기. 자세한 내용은 [오퍼 카테고리 만들기](../../interaction/using/creating-offer-categories.md)를 참조하십시오.
1. 디자인 환경에서 오퍼 만들기 자세한 내용은 [오퍼 만들기](../../interaction/using/creating-an-offer.md)를 참조하십시오.
1. 배달 관리자의 라이브 환경에서 오퍼를 사용할 수 있도록 하기 위해 하나 이상의 공간에 오퍼를 승인 및 게시합니다. 자세한 내용은 [오퍼](../../interaction/using/approving-and-activating-an-offer.md)의 승인 및 활성화를 참조하십시오.

## 오퍼 카탈로그 사용 {#using-the-offer-catalog-}

>[!NOTE]
>
>다음 단계는 **배달 관리자** 프로필에 의해 수행해야 합니다. 라이브 환경에서만 오퍼를 편집할 수 있습니다.

1. 캠페인 만들기.
1. 캠페인 또는 캠페인 전달의 오퍼 참조 자세한 내용은 [아웃바운드 채널 정보](../../interaction/using/about-outbound-channels.md)를 참조하십시오.

