---
title: Adobe Campaign Classic 데이터 모델 정보
description: 이 문서에서는 Adobe Campaign Classic 데이터 모델의 기본 사항에 대해 설명합니다.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# 사용자 지정 수신자 테이블 사용{#custom-recipient-table}

Adobe Campaign 데이터 모델을 디자인할 때 [즉시 사용할 수 있는 수신자 테이블을](../../configuration/using/default-recipient-table.md)사용하거나 비표준 수신자 테이블을 만들어 마케팅 프로필을 저장할 수 있습니다.

실제로 데이터 모델이 수신자 중심 구조에 맞지 않는 경우 Adobe Campaign 내에서 다른 테이블을 타깃팅 차원으로 설정할 수 있습니다. 예를 들어 단순히 수신자가 아닌 가정, 계정(휴대폰 등) 및 회사/사이트를 대상으로 해야 하는 경우 이 문제가 관련이 있을 수 있습니다.

>[!NOTE]
>
>이 경우 새 [대상 매핑을](../../configuration/using/target-mapping.md)만들어야 합니다.

사용자 지정 수신자 테이블을 사용할 때 필요한 모든 원칙과 단계는 이 [섹션에](../../configuration/using/about-custom-recipient-table.md)자세히 설명되어 있습니다.

사용자 지정 수신자 테이블을 사용하면 다음과 같은 이점이 있습니다.

## 유연한 데이터 모델 {#flexible-data-model}

수신자 테이블 필드의 대부분이 필요하지 않거나 데이터 모델이 수신자 중심의 것이 아닌 경우 즉시 사용 가능한 수신자 테이블은 사용할 수 없습니다.

## 확장성 {#scalability}

큰 볼륨은 효율적인 디자인을 위해 필드가 거의 없는 효율적인 표를 필요로 합니다. 곧바로 사용할 수 있는 수신자 테이블에는 쓸모없는 필드가 너무 많아 성능에 영향을 줄 수 있고 효율성이 떨어집니다.

## 데이터 위치 {#data-location}

데이터가 외부 기존 마케팅 데이터베이스에 있을 경우 즉시 사용 가능한 수신자 테이블을 사용하는 데 너무 많은 노력이 필요할 수 있습니다. 기존 구조를 기반으로 새 구조를 만드는 것이 더 쉽습니다.

## 간편한 마이그레이션 {#easy-migration}

업그레이드 시 모든 익스텐션이 여전히 유효한지 확인하기 위해 유지 관리가 필요하지 않습니다.

>[!IMPORTANT]
>
>사용자 지정 수신자 테이블 사용은 고급 사용자를 위해 예약되어 있으며 일부 제한이 적용됩니다. 자세한 내용은 이 섹션을 참조하십시오.
