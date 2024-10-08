---
product: campaign
title: 익명의 상호 작용
description: 익명의 상호 작용
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a8face46-a933-4f2c-8299-ccb66f05967d
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 1%

---

# 익명의 상호 작용{#anonymous-interactions}



![](assets/do-not-localize/how-to-video.png) 이 [비디오](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com)를 시청하여 확인 및 익명 대상에 오퍼가 전달되는 방식에 대한 개요를 살펴보십시오.

## 익명 상호 작용을 위한 환경 타겟팅 및 저장 {#targeting-and-storing-an-environment-for-anonymous-interactions}

기본적으로 상호 작용은 수신자 테이블(식별된 오퍼)을 타겟팅하기 위해 사전 구성된 환경과 함께 제공됩니다. 다른 테이블(익명 오퍼의 방문자 테이블 또는 특정 수신자 테이블)을 타겟팅하려면 target 매핑 도우미를 사용하여 환경을 만들어야 합니다. 자세한 내용은 [오퍼 환경 만들기](../../interaction/using/live-design-environments.md#creating-an-offer-environment)를 참조하십시오.

매핑 생성 도우미를 통해 익명 환경을 만들면 환경의 **[!UICONTROL General]** 탭에서 **[!UICONTROL Environment dedicated to incoming anonymous interactions]** 상자가 자동으로 선택됩니다.

**[!UICONTROL Targeting dimension]**&#x200B;이(가) 자동으로 완료되었습니다. 기본적으로 방문자 테이블에 연결됩니다.

**[!UICONTROL Visitor folder]** 필드가 나타납니다. **[!UICONTROL Visitors]** 폴더에 연결하려면 자동으로 완료됩니다. 이 필드에서는 방문자 프로필을 저장할 위치를 선택할 수 있습니다.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>여러 유형의 방문자를 필터링하려면(예를 들어 하나 이상의 브랜드에 대해 제공된 익명 오퍼의 경우) 각 브랜드에 대한 환경을 만들고 각 환경에 대해 **[!UICONTROL Visitors]** 유형 폴더를 만들어야 합니다.

## 익명 상호 작용을 위한 오퍼 카탈로그 {#offer-catalog-for-anonymous-interactions}

인바운드 상호 작용은 아웃바운드 상호 작용과 마찬가지로 범주와 오퍼로 구성된 오퍼 카탈로그로 구성됩니다.

범주 및 공백을 만들려면 식별된 방문자에 대해 동일한 프로세스를 적용합니다([오퍼 범주 만들기](../../interaction/using/creating-offer-categories.md) 및 [오퍼 환경 만들기](../../interaction/using/live-design-environments.md#creating-an-offer-environment) 참조).

## 익명 방문자 {#anonymous-visitors}

익명 방문자는 연결 시 쿠키 식별 프로세스에 제출할 수 있습니다. 이러한 암시적 인식은 방문자의 브라우저 기록을 기반으로 합니다.

이 단계에서는 쿠키로 복구한 데이터와 데이터베이스의 데이터를 비교합니다. 경우에 따라 방문자가 인식되며(그런 다음 암묵적으로 식별됨), 다른 경우에는 인식되지 않으므로 익명으로 유지됩니다.

이 분석을 실행하려면 오퍼 공간에 대해 **[!UICONTROL Implicitly identify the individual based on their browser history]** 옵션을 선택하십시오.

![](assets/identification_anonymous_visitors.png)

## 미확인된 익명 방문자 처리 중 {#processing-unidentified-anonymous-visitors}

분석 후 익명의 방문자가 식별되지 않으면 주어진 공간에 데이터를 저장할 수 있습니다. 이렇게 하면 지정된 유형화 규칙과 일치하는 이 유형의 방문자를 특별히 겨냥한 오퍼를 제안할 수 있습니다.

연락처를 식별할 수 있는 요소가 없거나 암시적으로 식별할 수 있는 연락처에 식별된 오퍼를 제안하고 싶지 않은 경우 익명 환경에서 대체 항목을 수행하도록 선택할 수 있습니다.

이렇게 하려면 **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**&#x200B;을(를) 확인한 다음 오퍼 공간을 지정할 때 **[!UICONTROL Linked anonymous space]**&#x200B;에서 이러한 미확인 방문자 전용 환경을 지정하십시오.

![](assets/anonymous_to_anonymous_environment.png)
