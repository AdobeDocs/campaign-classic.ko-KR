---
product: campaign
title: 오퍼 카테고리 만들기
description: 오퍼 카테고리 만들기
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: ed97a1b5-c870-4b67-98b6-16adc316fd46
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---

# 오퍼 카테고리 만들기{#creating-offer-categories}

![](../../assets/v7-only.svg)

오퍼 카테고리 만들기는 **[!UICONTROL Design]** 환경. 이 워크플로우는 **[!UICONTROL Live]** 환경 (즉, 오퍼가 포함된 작성/수정된 오퍼가 승인될 때 사용 가능함). 기본적으로 **[!UICONTROL Design]** 환경에는 모든 오퍼를 받을 카테고리가 포함되어 있습니다. 카탈로그 오퍼에 계층 구조를 추가하도록 하위 카테고리를 만들 수 있습니다.

각 카테고리에 대해 자격 날짜를 정의할 수 있습니다. 즉, 카테고리에 포함된 오퍼가 더 이상 해당 대상에 표시되지 않는 기간을 넘어서면 됩니다. 특정 카테고리의 오퍼를 오퍼 엔진에서 우선순위로 선택하려는 경우 예를 들어 제품을 더 잘 노출하려면 카테고리에 곱하는 가중치를 추가하여 지정된 기간 동안의 가중치를 높일 수 있습니다.

추가 카테고리를 만들려면 다음 단계를 적용합니다.

1. 로 이동합니다. **[!UICONTROL Offer catalog]** 폴더를 입력합니다.

   ![](assets/offer_cat_create_001.png)

1. 마우스 오른쪽 단추를 클릭하고 을 선택합니다 **[!UICONTROL Create a new "Offer category" folder]** 드롭다운 목록에서 을 선택합니다.

   ![](assets/offer_cat_create_002.png)

1. 카테고리의 이름을 다시 지정합니다. 레이블을 나중에 **[!UICONTROL General]** 탭.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >필요한 만큼 카테고리를 만들려면 이 단계를 반복합니다.

   그런 다음 필요에 따라 다음을 수행할 수 있습니다.

   * 자격 일자를 다음 위치에서 지정합니다. **[!UICONTROL Eligibility]** 탭.

      ![](assets/offer_cat_create_004.png)

   * 을 사용하여 이 카테고리 내에서 오퍼를 선택하는 데 사용할 수 있는 주요 단어를 입력합니다. **[!UICONTROL Themes]** 필드.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >오퍼 엔진을 호출할 때 테마 또는 카테고리가 매개 변수와 일치하는 카탈로그의 부분만 선택됩니다.

   * 을 통해 지정된 기간 동안 카테고리의 오퍼 가중치를 일시적으로 &quot;증가&quot;합니다. **[!UICONTROL Multiplier weight]** 필드.

      ![](assets/offer_cat_create_006.png)

자격 규칙 요약은 카테고리에 포함된 오퍼의 대시보드에서 사용할 수 있습니다. 이를 보려면 **[!UICONTROL Schedule and eligibility rules of the offer]** 링크를 클릭합니다.

![](assets/offer_create_006.png)
