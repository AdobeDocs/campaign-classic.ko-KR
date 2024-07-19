---
product: campaign
title: 오퍼 카테고리 만들기
description: 오퍼 카테고리 만들기
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: ed97a1b5-c870-4b67-98b6-16adc316fd46
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# 오퍼 카테고리 만들기{#creating-offer-categories}



오퍼 범주를 만드는 작업은 **[!UICONTROL Design]** 환경에서만 수행할 수 있습니다. 포함된 생성/수정된 오퍼가 승인되면 이 오퍼는 **[!UICONTROL Live]** 환경(즉, 사용 가능)에 자동으로 배포됩니다. 기본적으로 **[!UICONTROL Design]** 환경에는 모든 오퍼를 받을 범주가 포함되어 있습니다. 하위 범주를 만들어 카탈로그 오퍼에 계층을 추가할 수 있습니다.

각 카테고리에 대해 자격 날짜, 즉 카테고리에 포함된 오퍼가 더 이상 타겟에 제시되지 않을 수 있는 기간을 정의할 수 있습니다. 예를 들어, 제품을 더 잘 노출하기 위해 오퍼 엔진에서 특정 카테고리의 오퍼를 우선 순위로 선택하도록 하려면 카테고리에 곱하기 가중치를 추가하여 주어진 기간 동안 가중치를 늘릴 수 있습니다.

추가 범주를 만들려면 다음 단계를 적용합니다.

1. **[!UICONTROL Offer catalog]** 폴더로 이동합니다.

   ![](assets/offer_cat_create_001.png)

1. 마우스 오른쪽 단추를 클릭하고 드롭다운 목록에서 **[!UICONTROL Create a new "Offer category" folder]**&#x200B;을(를) 선택합니다.

   ![](assets/offer_cat_create_002.png)

1. 카테고리 이름을 다시 지정합니다. 나중에 **[!UICONTROL General]** 탭을 사용하여 레이블을 편집할 수 있습니다.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >이 단계를 반복하여 필요한 만큼 범주를 만듭니다.

   그런 다음 필요에 따라 다음을 수행할 수 있습니다.

   * **[!UICONTROL Eligibility]** 탭에서 자격 날짜를 할당하십시오.

     ![](assets/offer_cat_create_004.png)

   * **[!UICONTROL Themes]** 필드를 사용하여 이 범주 내에서 오퍼를 선택하는 데 사용할 수 있는 키워드를 입력하십시오.

     ![](assets/offer_cat_create_005.png)

     >[!NOTE]
     >
     >오퍼 엔진을 호출할 때 테마나 범주가 매개 변수와 일치하는 카탈로그의 부분만 선택됩니다.

   * **[!UICONTROL Multiplier weight]** 필드를 통해 지정된 기간 동안 범주의 오퍼 가중치를 일시적으로 &quot;증폭&quot;합니다.

     ![](assets/offer_cat_create_006.png)

자격 규칙에 대한 요약은 범주에 포함된 오퍼의 대시보드에서 사용할 수 있습니다. 이를 보려면 **[!UICONTROL Schedule and eligibility rules of the offer]** 링크를 클릭하십시오.

![](assets/offer_create_006.png)
