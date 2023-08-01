---
product: campaign
title: 오퍼 카테고리 만들기
description: 오퍼 카테고리 만들기
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: ed97a1b5-c870-4b67-98b6-16adc316fd46
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 3%

---

# 오퍼 카테고리 만들기{#creating-offer-categories}



오퍼 범주를 만드는 작업은 다음에서만 수행할 수 있습니다. **[!UICONTROL Design]** 환경. 이 템플릿은에서 자동으로 배포됩니다. **[!UICONTROL Live]** 포함된 생성/수정된 오퍼가 승인될 때 환경(즉, 사용 가능함). 기본적으로 **[!UICONTROL Design]** 환경에는 모든 오퍼를 받는 범주가 포함되어 있습니다. 하위 범주를 만들어 카탈로그 오퍼에 계층을 추가할 수 있습니다.

각 카테고리에 대해 자격 날짜, 즉 카테고리에 포함된 오퍼가 더 이상 타겟에 제시되지 않을 수 있는 기간을 정의할 수 있습니다. 예를 들어, 제품을 더 잘 노출하기 위해 오퍼 엔진에서 특정 카테고리의 오퍼를 우선 순위로 선택하도록 하려면 카테고리에 곱하기 가중치를 추가하여 주어진 기간 동안 가중치를 늘릴 수 있습니다.

추가 범주를 만들려면 다음 단계를 적용합니다.

1. 로 이동 **[!UICONTROL Offer catalog]** 폴더를 삭제합니다.

   ![](assets/offer_cat_create_001.png)

1. 마우스 오른쪽 버튼을 클릭하고 선택 **[!UICONTROL Create a new "Offer category" folder]** 을 클릭합니다.

   ![](assets/offer_cat_create_002.png)

1. 카테고리 이름을 다시 지정합니다. 나중에 다음을 사용하여 레이블을 편집할 수 있습니다. **[!UICONTROL General]** 탭.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >이 단계를 반복하여 필요한 만큼 범주를 만듭니다.

   그런 다음 필요에 따라 다음을 수행할 수 있습니다.

   * 다음에서 자격 일자 할당 **[!UICONTROL Eligibility]** 탭.

     ![](assets/offer_cat_create_004.png)

   * 이 범주 내에서 오퍼를 선택하는 데 사용할 수 있는 키워드를 입력하십시오. **[!UICONTROL Themes]** 필드.

     ![](assets/offer_cat_create_005.png)

     >[!NOTE]
     >
     >오퍼 엔진을 호출할 때 테마나 범주가 매개 변수와 일치하는 카탈로그의 부분만 선택됩니다.

   * 를 통해 주어진 기간 동안 범주의 오퍼 가중치를 일시적으로 &quot;증폭&quot; **[!UICONTROL Multiplier weight]** 필드.

     ![](assets/offer_cat_create_006.png)

자격 규칙에 대한 요약은 범주에 포함된 오퍼의 대시보드에서 사용할 수 있습니다. 이러한 코드를 보려면 **[!UICONTROL Schedule and eligibility rules of the offer]** 링크를 클릭합니다.

![](assets/offer_create_006.png)
