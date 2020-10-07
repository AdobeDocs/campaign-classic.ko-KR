---
title: 오퍼 엔진
seo-title: 오퍼 엔진
description: 오퍼 엔진
seo-description: null
page-status-flag: never-activated
uuid: a8f6056a-80e6-4f9f-81f5-563c98d11d28
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 08987595-e80c-4197-ad1e-9aa7cfc7c3eb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 5%

---


# 오퍼 엔진{#offer-engine}

이 **[!UICONTROL Offer engine]** 활동을 사용하면 배달 전에 오퍼 엔진에 대한 호출을 정의할 수 있습니다.

이러한 활동은 게재 전에 엔진에서 계산된 오퍼로 인바운드 모집단 데이터를 증가시켜 엔진 호출을 통한 농축활동과 동일한 원리로 작동합니다.

![](assets/int_offerengine_activity2.png)

쿼리를 구성한 후(이 [섹션](../../workflow/using/query.md)참조):

1. 활동을 추가하고 **[!UICONTROL Offer engine]** 엽니다.
1. 다양한 사용 가능한 필드를 작성하여 오퍼 엔진 매개 변수(오퍼 공간, 카테고리 또는 테마, 연락처 날짜, 보관할 오퍼 수)를 지정합니다. 엔진은 이러한 매개 변수에 따라 추가할 오퍼를 자동으로 계산합니다.

   >[!CAUTION]
   >
   >이 활동을 사용하는 경우 게재에 사용된 오퍼 옵션만 저장됩니다.

   ![](assets/int_offerengine_activity1.png)

1. 그런 다음 선택한 채널에 해당하는 배달 활동을 구성합니다. 크로스 [채널 전달을 참조하십시오](../../workflow/using/cross-channel-deliveries.md).

