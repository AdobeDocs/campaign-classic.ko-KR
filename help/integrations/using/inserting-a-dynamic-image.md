---
product: campaign
title: 동적 이미지 삽입
description: 동적 이미지 삽입
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 6177f57b-534c-4d86-8f73-d96980c48a77
source-git-commit: b6e24c63ece12f25b7dafe3fede9e38b3aab2427
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 3%

---

# Target 다이내믹 콘텐츠 삽입 {#inserting-a-dynamic-image}

![](../../assets/common.svg)

이 페이지에서는 Adobe Target의 다이내믹 오퍼를 Adobe Campaign의 이메일에 통합하는 방법을 알아봅니다.

목표는 수신자의 국가에 따라 동적으로 변경되는 이미지 블록으로 게재를 만드는 것입니다. 데이터는 각 mbox 요청과 함께 전송되며 수신자의 IP 주소에 따라 달라집니다.

이 메시지에서 이미지는 다음과 같은 사용자 경험에 따라 동적으로 달라질 수 있습니다.

* 이메일이 프랑스에서 오픈되었습니다.
* 이메일은 미국에서 열립니다.
* 이러한 조건이 적용되지 않으면 기본 이미지가 표시됩니다.

![](assets/target_4.png)

이렇게 하려면 다음 단계를 적용합니다.

1. [이메일에 동적 오퍼 삽입](../../integrations/using/inserting-a-dynamic-image.md#inserting-dynamic-offer)
1. [리디렉션 오퍼 만들기](../../integrations/using/inserting-a-dynamic-image.md#create-redirect-offers)
1. [대상자 만들기](../../integrations/using/inserting-a-dynamic-image.md#audiences-target)
1. [경험 타깃팅 활동 만들기](../../integrations/using/inserting-a-dynamic-image.md#creating-targeting-activity)
1. [이메일 미리 보기 및 보내기](../../integrations/using/inserting-a-dynamic-image.md#preview-send-email)

## 이메일에 동적 오퍼 삽입 {#inserting-dynamic-offer}

Adobe Campaign에서 이메일의 타겟과 콘텐츠를 정의했으면 Target에서 동적 이미지를 삽입할 수 있습니다.

이렇게 하려면 기본 이미지의 URL, 위치 이름 및 Target으로 전송할 필드를 지정합니다.

Adobe Campaign에서는 Target의 동적 이미지를 이메일에 삽입하는 두 가지 방법이 있습니다.

* 디지털 콘텐츠 편집기를 사용하는 경우 기존 이미지를 선택하고 을 선택합니다 **[!UICONTROL Insert]** > **[!UICONTROL Dynamic image served by Adobe Target]** 을 클릭합니다.

   ![](assets/target_5.png)

* 표준 편집기를 사용하는 경우 이미지를 삽입할 위치에 커서를 놓고 을 선택합니다 **[!UICONTROL Include]** > **[!UICONTROL Dynamic image served by Adobe Target...]** 개인화 드롭다운 메뉴에서 을(를) 선택합니다.

   ![](assets/target_12.png)

### 이미지 매개 변수 정의 {#defining-image-parameters}

* 다음 **[!UICONTROL Default image]**&#x200B;의 URL: 조건이 충족되지 않았을 때 표시되는 이미지입니다. 자산 라이브러리에서 이미지를 선택할 수도 있습니다.
* 다음 **[!UICONTROL Target location]**: 동적 오퍼의 위치 이름을 입력합니다. Target 활동에서 이 위치를 선택해야 합니다.
* 다음 **[!UICONTROL Landing Page]**: 기본 이미지가 기본 랜딩 페이지로 리디렉션되도록 하는 경우. 이 URL은 기본 이미지가 최종 이메일에 표시되는 경우에만 해당되며 선택 사항입니다.
* 다음 **[!UICONTROL Additional decision parameters]**: Adobe Target 세그먼트에 정의된 필드와 Adobe Campaign 필드 간의 매핑을 지정합니다. 사용된 Adobe Campaign 필드는 rawbox에 지정했어야 합니다. 이 예제에서는 국가 필드를 추가했습니다.

Adobe Target의 설정에서 Enterprise 권한을 사용하는 경우 이 필드에 해당 속성을 추가합니다. 에서 엔터프라이즈 권한 Target에 대해 자세히 알아보기 [이 페이지](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html).

![](assets/target_13.png)

## 리디렉션 오퍼 만들기 {#create-redirect-offers}

Target에서 오퍼의 다른 버전을 만들 수 있습니다. 각 사용자 경험에 따라 리디렉션 오퍼를 만들고 표시할 이미지를 지정할 수 있습니다.

이 경우 두 개의 리디렉션 오퍼가 필요하며, 세 번째 리디렉션 오퍼(기본 오퍼)는 Adobe Campaign에서 정의해야 합니다.

1. Target Standard에서 새 리디렉션 오퍼를 만들려면 **[!UICONTROL Content]** 탭을 클릭하고 **[!UICONTROL Code offers]**.

1. **[!UICONTROL Create]**&#x200B;을(를) 클릭한 뒤 **[!UICONTROL Redirect Offer]**&#x200B;을(를) 클릭합니다.

   ![](assets/target_9.png)

1. 오퍼 이름과 이미지 URL을 입력합니다.

   ![](assets/target_6.png)

1. 나머지 리디렉션 오퍼에 대해서도 동일한 절차를 수행합니다. 자세한 정보는 이 [페이지](https://experienceleague.adobe.com/docs/target/using/experiences/offers/offer-redirect.html)를 참조하십시오.

## 대상자 만들기 {#audiences-target}

Target에서 오퍼를 방문하는 사람을 전달할 다른 콘텐츠에 대해 분류할 두 대상을 만들어야 합니다. 각 대상자에 대해 규칙을 추가하여 오퍼를 볼 수 있는 사람을 정의합니다.

1. Target에서 새 대상을 만들려면 **[!UICONTROL Audiences]** 탭을 클릭하고 **[!UICONTROL Create Audience]**.

   ![](assets/audiences_1.png)

1. 대상에 이름을 추가합니다.

   ![](assets/audiences_2.png)

1. 클릭 **[!UICONTROL Add a rule]** 범주를 선택합니다. 규칙은 특정 기준을 사용하여 방문자를 타깃팅합니다. 조건을 추가하거나 다른 범주에서 새 규칙을 만들어 규칙을 세분화할 수 있습니다.

1. 나머지 대상에 대해서도 동일한 절차를 따르십시오.

## 경험 타깃팅 활동 만들기 {#creating-targeting-activity}

Target 시 경험 타깃팅 활동을 만들고, 다양한 경험을 정의하고, 해당 오퍼와 연결해야 합니다.

### 대상자 정의 {#defining-the-audience}

1. 경험 타깃팅 활동을 만들려면 **[!UICONTROL Activities]** 탭을 클릭하고 **[!UICONTROL Create Activity]** 그러면 **[!UICONTROL Experience Targeting]**.

   ![](assets/target_10.png)

1. 선택 **[!UICONTROL Form]** 다음으로: **[!UICONTROL Experience Composer]**.

1. 다음을 클릭하여 대상 선택 **[!UICONTROL Change audience]** 단추를 클릭합니다.

   ![](assets/target_10_2.png)

1. 이전 단계에서 만든 대상자를 선택합니다.

   ![](assets/target_10_3.png)

1. 다음을 클릭하여 다른 경험 만들기 **[!UICONTROL Add Experience Targeting]**.

### 위치 및 콘텐츠 정의 {#defining-location-content}

각 대상자에 대한 콘텐츠를 추가합니다.

1. Adobe Campaign에서 동적 오퍼를 삽입할 때 선택한 위치 이름을 선택합니다.

   ![](assets/target_15.png)

1. 드롭다운 버튼을 클릭하고 을(를) 선택합니다. **[!UICONTROL Change Redirect Offer]**.

   ![](assets/target_content.png)

1. 이전에 만든 리디렉션 오퍼를 선택합니다.

   ![](assets/target_content_2.png)

1. 두 번째 경험에 대해서도 동일한 단계를 수행합니다.

### 활동 정의 {#defining-activity}

다음 **[!UICONTROL Target]** 창에 활동이 요약됩니다. 필요한 경우 다른 경험을 추가할 수 있습니다.

![](assets/target_experience.png)

다음 **[!UICONTROL Goal & Settings]** 창을 사용하면 우선순위, 목표 또는 기간을 설정하여 활동을 개인화할 수 있습니다.

다음 **[!UICONTROL Reporting Settings]** 섹션 에서는 작업을 선택하고 목표 달성 시기를 결정할 매개 변수를 편집할 수 있습니다.

![](assets/target_experience_2.png)

## 이메일 미리 보기 및 보내기 {#preview-send-email}

이제 Adobe Campaign에서 이메일을 미리 보고 다른 수신자에서 해당 렌더링을 테스트할 수 있습니다. 생성된 다양한 경험에 따라 이미지가 변경되는 것을 볼 수 있습니다. 이메일 만들기에 대한 자세한 내용은 다음을 참조하십시오. [페이지](../../delivery/using/defining-the-email-content.md).

이제 Target의 다이내믹 오퍼를 포함하여 이메일을 보낼 준비가 되었습니다.

![](assets/target_20.png)
