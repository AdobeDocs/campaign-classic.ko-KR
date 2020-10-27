---
title: 오퍼 카테고리 만들기
seo-title: 오퍼 카테고리 만들기
description: 오퍼 카테고리 만들기
seo-description: null
page-status-flag: never-activated
uuid: 5ac0ae5e-1731-4699-b4ef-f3867ad0ab58
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: a9fad813-3256-4a00-ba74-7dbaba9e8e23
translation-type: tm+mt
source-git-commit: 8fc3e793ec544948049fc122b44b6bffdebecba0
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 4%

---


# 오퍼 카테고리 만들기{#creating-offer-categories}

오퍼 카테고리는 **[!UICONTROL Design]** 환경에서만 만들 수 있습니다. 이 오퍼는 작성/수정된 오퍼가 승인되면 **[!UICONTROL Live]** 환경에 자동으로 배포됩니다(즉, 사용 가능하도록 함). 기본적으로 환경에는 모든 오퍼를 수신할 카테고리가 **[!UICONTROL Design]** 포함됩니다. 카탈로그 오퍼에 계층을 추가하기 위해 하위 카테고리를 만들 수 있습니다.

각 카테고리에 대해 자격 조건 날짜를 정의할 수 있습니다. 예를 들어 카테고리에 포함된 오퍼가 더 이상 대상에 표시되지 않을 수 있습니다. 특정 카테고리의 오퍼를 오퍼 엔진에서 우선순위로 선택하도록 하려는 경우 예를 들어 제품을 더 잘 노출하려면 카테고리에 가중치를 추가하여 지정된 기간 동안의 가중치를 높일 수 있습니다.

추가 범주를 만들려면 다음 단계를 적용합니다.

1. Go to the **[!UICONTROL Offer catalog]** folder.

   ![](assets/offer_cat_create_001.png)

1. 마우스 오른쪽 버튼을 클릭하고 드롭다운 목록 **[!UICONTROL Create a new "Offer category" folder]** 에서 선택합니다.

   ![](assets/offer_cat_create_002.png)

1. 카테고리의 이름을 다시 지정합니다. 나중에 **[!UICONTROL General]** 탭을 사용하여 레이블을 편집할 수 있습니다.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >필요한 만큼의 카테고리를 만들려면 이 단계를 반복합니다.

   이후 필요에 따라 다음을 수행할 수 있습니다.

   * 탭에서 자격 조건 날짜를 **[!UICONTROL Eligibility]** 지정합니다.

      ![](assets/offer_cat_create_004.png)

   * 이 카테고리 내에서 필드를 사용하여 오퍼를 선택하는 데 사용할 수 있는 주요 단어를 **[!UICONTROL Themes]** 입력합니다.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >오퍼 엔진을 호출할 때 테마나 카테고리가 매개 변수와 일치하는 카탈로그의 일부만 선택됩니다.

   * 특정 기간 동안 **[!UICONTROL Multiplier weight]** 필드를 통해 카테고리의 오퍼 가중치를 일시적으로 &quot;증폭&quot;합니다.

      ![](assets/offer_cat_create_006.png)

카테고리에 포함된 오퍼의 대시보드에서 자격 조건 규칙 요약 정보를 사용할 수 있습니다. 이를 보려면 해당 **[!UICONTROL Schedule and eligibility rules of the offer]** 링크를 클릭합니다.

![](assets/offer_create_006.png)

