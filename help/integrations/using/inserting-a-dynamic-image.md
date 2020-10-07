---
title: 동적 이미지 삽입
seo-title: 동적 이미지 삽입
description: 동적 이미지 삽입
seo-description: null
page-status-flag: never-activated
uuid: 4acc905e-625c-45aa-bb70-7dde22911aa0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: f6e4d22b-4ad3-4a1e-8a6f-3bdfc1da0535
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 3%

---


# Target 동적 컨텐츠 삽입 {#inserting-a-dynamic-image}

본 가이드에서는 Target의 동적 오퍼를 Adobe Campaign의 이메일에 통합하는 방법을 설명합니다.

받는 사람의 국가에 따라 동적으로 변경되는 이미지 블록이 포함되는 배달을 만들고 싶습니다. 데이터는 각 mbox 요청과 함께 전송되며 방문자의 IP 주소에 따라 달라집니다.

이 이메일에서 다음 사용자 경험에 따라 이미지 중 하나가 동적으로 달라지길 바랍니다.

* 프랑스에서 이메일이 열립니다.
* 이 이메일은 미국에서 열립니다.
* 이러한 조건이 적용되지 않으면 기본 이미지가 표시됩니다.

![](assets/target_4.png)

이를 수행하려면 Adobe Campaign 및 Target에서 다음 단계를 수행해야 합니다.

1. [이메일에 동적 오퍼 삽입](../../integrations/using/inserting-a-dynamic-image.md#inserting-dynamic-offer)
1. [리디렉션 오퍼 만들기](../../integrations/using/inserting-a-dynamic-image.md#create-redirect-offers)
1. [대상자 만들기](../../integrations/using/inserting-a-dynamic-image.md#audiences-target)
1. [경험 타깃팅 활동 만들기](../../integrations/using/inserting-a-dynamic-image.md#creating-targeting-activity)
1. [이메일 미리 보기 및 보내기](../../integrations/using/inserting-a-dynamic-image.md#preview-send-email)

## 이메일에 동적 오퍼 삽입 {#inserting-dynamic-offer}

Adobe Campaign에서 이메일의 타겟 및 컨텐츠 정의를 완료하면 Target의 동적 이미지를 삽입할 수 있습니다.

이렇게 하려면 기본 이미지의 URL, 위치 이름 및 Target으로 전송할 필드를 지정합니다.

Adobe Campaign에서는 Target의 동적 이미지를 이메일에 삽입하는 두 가지 방법이 있습니다.

* 디지털 컨텐츠 편집기를 사용하는 경우 기존 이미지를 선택하고 도구 모음에서 **[!UICONTROL Insert]** > **[!UICONTROL Dynamic image served by Adobe Target]** 를 선택합니다.

   ![](assets/target_5.png)

* 표준 편집기를 사용하는 경우 이미지를 삽입할 위치에 커서를 놓고 개인화 드롭다운 메뉴에서 **[!UICONTROL Include]** > **[!UICONTROL Dynamic image served by Adobe Target...]** 을 선택합니다.

   ![](assets/target_12.png)

### 이미지 매개 변수 정의 {#defining-image-parameters}

* URL **[!UICONTROL Default image]**:조건이 충족되지 않을 때 표시되는 이미지입니다. 자산 라이브러리에서 이미지를 선택할 수도 있습니다.
* The **[!UICONTROL Target location]**:동적 오퍼 위치의 이름을 입력합니다. Target 활동에서 이 위치를 선택해야 합니다.
* The **[!UICONTROL Landing Page]**:기본 이미지를 기본 랜딩 페이지로 리디렉션하려는 경우. 이 URL은 기본 이미지가 최종 이메일에 표시되고 선택 사항인 경우에만 해당됩니다.
* The **[!UICONTROL Additional decision parameters]**:Adobe Target 세그먼트에 정의된 필드와 Adobe Campaign 필드 사이의 매핑을 지정합니다. 사용된 Adobe Campaign 필드는 rawbox에 지정되어 있어야 합니다. 이 예에서는 국가 필드를 추가했습니다.

Adobe Target의 설정에서 Enterprise 권한을 사용하는 경우 이 필드에 해당 속성을 추가합니다. 이 [페이지에서 Enterprise Target 권한에 대해 자세히 알아보십시오](https://docs.adobe.com/content/help/en/target/using/administer/manage-users/enterprise/properties-overview.html).

![](assets/target_13.png)

## 리디렉션 오퍼 만들기 {#create-redirect-offers}

Target에서 다양한 버전의 오퍼를 만들 수 있습니다. 각 사용자 경험에 따라 리디렉션 오퍼를 만들고 표시할 이미지를 지정할 수 있습니다.

이 경우 두 개의 리디렉션 오퍼가 필요하며, 세 번째 리디렉션 오퍼는 Adobe Campaign에서 정의됩니다.

1. Target Standard에서 새 리디렉션 오퍼를 만들려면 **[!UICONTROL Content]** 탭에서 을 클릭합니다 **[!UICONTROL Code offers]**.

1. **[!UICONTROL Create]**&#x200B;을(를) 클릭한 뒤 **[!UICONTROL Redirect Offer]**&#x200B;을(를) 클릭합니다.

   ![](assets/target_9.png)

1. 오퍼 이름과 이미지의 URL을 입력합니다.

   ![](assets/target_6.png)

1. 나머지 리디렉션 오퍼에 대해 동일한 절차를 따르십시오. 자세한 정보는 이 [페이지](https://docs.adobe.com/help/en/target/using/experiences/offers/offer-redirect.html)를 참조하십시오.

## 대상자 만들기 {#audiences-target}

Target에서는 오퍼를 방문하는 사용자가 전달될 다른 콘텐트로 분류될 두 대상을 만들어야 합니다. 각 대상에 대해 규칙을 추가하여 오퍼를 볼 수 있는 사용자를 정의합니다.

1. Target에서 새 대상을 만들려면 **[!UICONTROL Audiences]** 탭에서 을 클릭합니다 **[!UICONTROL Create Audience]**.

   ![](assets/audiences_1.png)

1. 대상에 이름을 추가합니다.

   ![](assets/audiences_2.png)

1. 범주 **[!UICONTROL Add a rule]** 를 클릭하고 선택합니다. 규칙은 특정 기준을 사용하여 방문자를 타깃팅합니다. 조건을 추가하거나 다른 카테고리에 새 규칙을 만들어 규칙을 세분화할 수 있습니다.

1. 나머지 대상에 대해 동일한 절차를 따르십시오.

## 경험 타깃팅 활동 만들기 {#creating-targeting-activity}

Target에서 경험 타깃팅 활동을 만들고, 다른 경험을 정의하고, 해당 오퍼와 연결해야 합니다.

### 대상 정의 {#defining-the-audience}

1. 경험 타깃팅 활동을 만들려면 **[!UICONTROL Activities]** 탭에서 을 **[!UICONTROL Create Activity]** 클릭합니다 **[!UICONTROL Experience Targeting]**.

   ![](assets/target_10.png)

1. 다음으로 **[!UICONTROL Form]** 선택합니다 **[!UICONTROL Experience Composer]**.

1. 단추를 클릭하여 대상을 **[!UICONTROL Change audience]** 선택합니다.

   ![](assets/target_10_2.png)

1. 이전 단계에서 만든 대상을 선택합니다.

   ![](assets/target_10_3.png)

1. 을 클릭하여 다른 경험을 만듭니다 **[!UICONTROL Add Experience Targeting]**.

### 위치 및 컨텐츠 정의 {#defining-location-content}

각 대상을 위한 컨텐츠를 추가합니다.

1. Adobe Campaign에 동적 오퍼를 삽입할 때 선택한 위치 이름을 선택합니다.

   ![](assets/target_15.png)

1. 드롭다운 단추를 클릭하고 선택합니다 **[!UICONTROL Change Redirect Offer]**.

   ![](assets/target_content.png)

1. 이전에 만든 리디렉션 오퍼를 선택합니다.

   ![](assets/target_content_2.png)

1. 두 번째 경험에 대해 동일한 단계를 수행합니다.

### 활동 정의 {#defining-activity}

창에 활동이 요약되어 **[!UICONTROL Target]** 있습니다. 필요한 경우 다른 경험을 추가할 수 있습니다.

![](assets/target_experience.png)

이 **[!UICONTROL Goal & Settings]** 창에서는 우선 순위, 목표 또는 기간을 설정하여 활동을 개인화할 수 있습니다.

이 **[!UICONTROL Reporting Settings]** 섹션에서는 작업을 선택하고 목표가 달성되는 시기를 결정할 매개 변수를 편집할 수 있습니다.

![](assets/target_experience_2.png)

## Campaign Classic에서 이메일 미리 보기 및 보내기 {#preview-send-email}

이제 Adobe Campaign에서 이메일을 미리 보고 다른 수신자에게 이메일을 렌더링할 수 있습니다. 만들어진 여러 경험에 따라 이미지가 바뀝니다. To learn more on email creation, refer to this [page](../../delivery/using/defining-the-email-content.md).

이제 Target의 동적 오퍼가 포함된 이메일을 보낼 준비가 되었습니다.

![](assets/target_20.png)
