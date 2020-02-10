---
title: Adobe Campaign Classic 수신자 테이블 사용
description: 데이터 모델을 디자인할 때 Adobe Campaign Classic에서 즉시 사용 가능한 수신자 테이블을 사용하는 방법을 알아봅니다.
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


# 데이터 모델 확장{#extending-data-model}

Adobe Campaign을 시작할 때 기본 데이터 모델을 평가하여 마케팅 데이터를 저장하는 데 가장 적합한 표를 확인해야 합니다.

관련 있는 경우 이 [섹션에](../../configuration/using/default-recipient-table.md)설명된 것과 같이 기본 수신자 테이블을 기본 필드와 함께 사용할 수 있습니다.

필요한 경우 두 가지 메커니즘으로 확장할 수 있습니다.

* 새 필드를 사용하여 기존 테이블을 확장합니다. 예를 들어 새 &quot;충성도&quot; 필드를 수신자 테이블에 추가할 수 있습니다.
* 새 테이블(예: &quot;구매&quot; 테이블)을 만들어 데이터베이스의 각 프로필에서 수행한 모든 구매를 나열하고 이를 수신자 테이블에 연결합니다.

개념 데이터 모델을 확장하도록 확장 스키마를 구성하는 방법에 대한 자세한 내용은 스키마 [에디션](../../configuration/using/about-schema-edition.md)정보를 참조하십시오.

>[!IMPORTANT]
>
>데이터 모델 확장은 고급 사용자를 위해 예약되어 있습니다.
