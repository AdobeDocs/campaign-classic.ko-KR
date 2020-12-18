---
solution: Campaign Classic
product: campaign
title: 익명의 상호 작용
description: 익명의 상호 작용
audience: interaction
content-type: reference
topic-tags: unitary-interactions
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 1%

---


# 익명의 상호 작용{#anonymous-interactions}

![](assets/do-not-localize/how-to-video.png) 이  [](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com) 비디오를 통해 식별된 타겟과 익명 타겟에 오퍼가 어떻게 제공되는지 간략하게 살펴볼 수 있습니다.

## 익명 상호 작용 {#targeting-and-storing-an-environment-for-anonymous-interactions}에 대한 환경 타깃팅 및 저장

기본적으로 상호 작용은 수신자 테이블(식별된 오퍼)을 대상으로 하기 위해 사전 구성된 환경을 제공합니다. 다른 테이블(익명 오퍼의 방문자 테이블 또는 특정 수신자 테이블의 방문자 테이블)을 타깃팅하려면 대상 매핑 마법사를 사용하여 환경을 만들어야 합니다. 자세한 내용은 [오퍼 환경 만들기](../../interaction/using/live-design-environments.md#creating-an-offer-environment)를 참조하십시오.

매핑 만들기 마법사를 통해 익명 환경을 만들면 환경의 **[!UICONTROL Environment dedicated to incoming anonymous interactions]** 탭에서 **[!UICONTROL General]** 상자가 자동으로 선택됩니다.

**[!UICONTROL Targeting dimension]**&#x200B;은(는) 자동으로 완료됩니다. 기본적으로 방문자 테이블로 연결됩니다.

**[!UICONTROL Visitor folder]** 필드가 나타납니다. **[!UICONTROL Visitors]** 폴더에 연결하는 것이 자동으로 완료됩니다. 이 필드에서 방문자 프로필을 저장할 위치를 선택할 수 있습니다.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>예를 들어 하나 이상의 브랜드에 대해 제공되는 익명의 오퍼의 경우 여러 유형의 방문자를 필터링하려면 각 브랜드에 대한 환경을 만들고 각 환경에 대해 **[!UICONTROL Visitors]** 유형 폴더를 만들어야 합니다.

## 익명 상호 작용 {#offer-catalog-for-anonymous-interactions} 제공 카탈로그

아웃바운드 상호 작용과 마찬가지로 인바운드 상호 작용은 카테고리와 오퍼로 구성된 오퍼 카탈로그에서 구성됩니다.

카테고리 및 공백을 만들려면 식별된 방문자에 대해 동일한 프로세스를 적용합니다(오퍼 카테고리 만들기[ 및 ](../../interaction/using/creating-offer-categories.md)오퍼 환경 만들기[ 참조).](../../interaction/using/live-design-environments.md#creating-an-offer-environment)

## 익명의 방문자 {#anonymous-visitors}

익명의 방문자가 연결되면 쿠키 식별 프로세스에 제출될 수 있습니다. 이 암시적 인식은 방문자의 브라우저 기록을 기반으로 합니다.

이 단계 동안 쿠키로 복구한 데이터와 데이터베이스의 데이터 간에 비교가 수행됩니다. 어떤 경우에는 방문자가 인식되어(그런 다음 암시적으로 식별됨), 다른 경우, 그는 인식되지 않으며, 따라서 익명 상태로 남아 있습니다.

이 분석을 실행하려면 오퍼 공간에 대해 **[!UICONTROL Implicitly identify the individual based on their browser history]** 옵션을 선택합니다.

![](assets/identification_anonymous_visitors.png)

## 식별되지 않은 익명 방문자 {#processing-unidentified-anonymous-visitors} 처리

분석 후 익명의 방문자가 식별되지 않으면 해당 데이터를 지정된 공간에 저장할 수 있습니다. 이렇게 하면 지정된 분류 규칙과 일치하는 이 유형의 방문자를 대상으로 하는 오퍼를 제안할 수 있습니다.

연락처를 식별할 수 있는 요소가 없거나, 암시적으로 식별할 수 있는 연락처에 식별된 오퍼를 제안하지 않으려는 경우, 익명 환경에서 폴백을 수행하도록 선택할 수 있습니다.

이렇게 하려면 **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**&#x200B;을 선택한 다음 오퍼 공간을 지정할 때 **[!UICONTROL Linked anonymous space]**&#x200B;에서 이러한 식별되지 않은 방문자에게 전용 환경을 지정합니다.

![](assets/anonymous_to_anonymous_environment.png)

