---
product: campaign
title: 익명의 상호 작용
description: 익명의 상호 작용
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a8face46-a933-4f2c-8299-ccb66f05967d
source-git-commit: 8b970705f0da6a9e09de9fadb3e1a8c5f4814f9f
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 1%

---

# 익명의 상호 작용{#anonymous-interactions}

![](../../assets/v7-only.svg)

![](assets/do-not-localize/how-to-video.png) 식별된  [](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com) 타겟과 익명의 타겟에게 오퍼가 전달되는 방법에 대한 개요를 보려면 이 비디오를 시청하십시오.

## 익명의 상호 작용을 위한 환경 타겟팅 및 저장 {#targeting-and-storing-an-environment-for-anonymous-interactions}

기본적으로 상호 작용은 수신자 테이블(식별된 오퍼)을 타깃팅할 사전 구성된 환경과 함께 제공됩니다. 다른 테이블(익명의 오퍼나 특정 수신자 테이블의 방문자 테이블)을 타깃팅하려면 대상 매핑 마법사를 사용하여 환경을 만들어야 합니다. 자세한 내용은 [오퍼 환경 만들기](../../interaction/using/live-design-environments.md#creating-an-offer-environment)를 참조하십시오.

매핑 생성 마법사를 통해 익명 환경을 만들면 환경의 **[!UICONTROL General]** 탭에서 **[!UICONTROL Environment dedicated to incoming anonymous interactions]** 상자가 자동으로 선택됩니다.

**[!UICONTROL Targeting dimension]**&#x200B;이(가) 자동으로 완료됩니다. 기본적으로 방문자 테이블로 연결됩니다.

**[!UICONTROL Visitor folder]** 필드가 나타납니다. **[!UICONTROL Visitors]** 폴더에 연결하도록 자동으로 완료됩니다. 이 필드에서는 방문자 프로필을 저장할 위치를 선택할 수 있습니다.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>예를 들어 하나 이상의 브랜드에 대해 제공되는 익명 오퍼의 경우 여러 유형의 방문자를 필터링하려면 각 브랜드에 대한 환경을 만들고 각 환경에 대해 **[!UICONTROL Visitors]** 유형 폴더를 만들어야 합니다.

## 익명의 상호 작용에 대한 오퍼 카탈로그 {#offer-catalog-for-anonymous-interactions}

아웃바운드 상호 작용과 마찬가지로 인바운드 상호 작용은 카테고리 및 오퍼로 구성된 오퍼 카탈로그에서 구성됩니다.

카테고리 및 공백을 만들려면 식별된 방문자에 대해 와 동일한 프로세스를 적용합니다( [오퍼 카테고리 만들기](../../interaction/using/creating-offer-categories.md) 및 [오퍼 환경 만들기](../../interaction/using/live-design-environments.md#creating-an-offer-environment) 참조).

## 익명의 방문자 {#anonymous-visitors}

익명의 방문자가 연결되면 쿠키 식별 프로세스에 전송될 수 있습니다. 이 암시적 인식은 방문자의 브라우저 기록을 기반으로 합니다.

이 단계에서는 쿠키로 복구된 데이터와 데이터베이스의 데이터 간에 비교됩니다. 어떤 경우에는 방문자가 인식됩니다(그런 다음 암시적으로 식별됨). 다른 경우 방문자가 인식되지 않으며 따라서 익명 상태로 유지됩니다.

이 분석을 실행하려면 오퍼 공간에 대해 **[!UICONTROL Implicitly identify the individual based on their browser history]** 옵션을 선택합니다.

![](assets/identification_anonymous_visitors.png)

## 식별되지 않은 익명 방문자 처리 {#processing-unidentified-anonymous-visitors}

분석 후 익명의 방문자가 식별되지 않으면 해당 공간에 데이터를 저장할 수 있습니다. 이렇게 하면 지정된 유형화 규칙과 일치하는 이 유형의 방문자를 대상으로 특정 오퍼를 제안할 수 있습니다.

연락처를 식별할 수 있는 요소가 없거나, 암묵적으로 식별할 수 있는 연락처에 식별된 오퍼를 제안하지 않으려는 경우 익명 환경에서 대체 작업을 수행하도록 선택할 수 있습니다.

이렇게 하려면 **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]** 을(를) 선택한 다음 오퍼 공간을 지정할 때 **[!UICONTROL Linked anonymous space]**&#x200B;에서 식별되지 않은 이러한 방문자에 대한 전용 환경을 지정합니다.

![](assets/anonymous_to_anonymous_environment.png)
