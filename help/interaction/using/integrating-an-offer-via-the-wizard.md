---
product: campaign
title: 마법사를 통해 오퍼 통합
description: 마법사를 통해 오퍼 통합
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
exl-id: 64aea8b9-7f06-4db0-a3e6-6a0e17c3ddcb
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 4%

---

# 마법사를 통해 오퍼 통합{#integrating-an-offer-via-the-wizard}



게재를 만들 때 오퍼를 통합하는 방법에는 두 가지가 있습니다.

* 게재 본문에서 오퍼 엔진 호출.
* 캠페인의 게재 개요를 통해 오퍼 참조. 이 방법은 일반적으로 종이 캠페인에 사용됩니다.

## 오퍼 엔진에 대한 호출을 사용하여 게재 {#delivering-with-a-call-to-the-offer-engine}

마케팅 캠페인 중에 오퍼를 제시하려면 선택한 채널을 기반으로 클래식 게재 작업을 만들면 됩니다. 오퍼 엔진은 게재 콘텐츠가 정의될 때 **[!UICONTROL Offers]** 아이콘 을 도구 모음에서 사용할 수 있습니다.

![](assets/offer_delivery_009.png)

DM 게재에 대해 자세히 알아보기 [이 섹션에서](../../delivery/using/about-direct-mail-channel.md). 마케팅 캠페인에 대해 자세히 알아보기 [이 섹션에서](../../campaign/using/setting-up-marketing-campaigns.md).

### 게재에 오퍼를 삽입하는 주요 단계 {#main-steps-for-inserting-an-offer-into-a-delivery}

게재에 오퍼 제안을 삽입하려면 다음 단계를 적용합니다.

1. 게재 창에서 오퍼 아이콘을 클릭합니다.

   ![](assets/offer_delivery_001.png)

1. 오퍼 환경과 일치하는 공간을 선택합니다.

   ![](assets/offer_delivery_002.png)

1. 엔진의 오퍼 선택을 세분화하려면 표시할 오퍼가 속한 범주 또는 하나/여러 테마를 선택합니다. 제한 사항이 오버로드되지 않도록 한 번에 이러한 필드 중 하나만 사용하는 것이 좋습니다.

   ![](assets/offer_delivery_003.png)

   ![](assets/offer_delivery_004.png)

1. 게재 본문에 삽입할 오퍼 수를 지정합니다.

   ![](assets/offer_delivery_005.png)

1. 다음 항목 선택 **[!UICONTROL Exclude non-eligible recipients]** 필요한 경우 옵션을 선택합니다. 자세한 내용은 다음을 참조하십시오. [오퍼 엔진 호출을 위한 매개변수](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_006.png)

1. 필요한 경우 **[!UICONTROL Do not display anything if no offers are selected]** 옵션을 선택합니다. 자세한 내용은 다음을 참조하십시오. [오퍼 엔진 호출을 위한 매개변수](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_007.png)

1. 병합 필드를 사용하여 게재 콘텐츠에 속성을 삽입합니다. 사용 가능한 제안 수는 엔진 호출이 구성되는 방식에 따라 다르며 오퍼 순서는 오퍼의 우선 순위에 따라 다릅니다.

   ![](assets/offer_delivery_008.png)

1. 콘텐츠를 완료하고 평소대로 게재를 보냅니다.

   ![](assets/offer_delivery_010.png)

### 오퍼 엔진 호출을 위한 매개변수 {#parameters-for-calling-offer-engine}

* **[!UICONTROL Space]** : 오퍼 엔진을 활성화하기 위해 선택해야 하는 오퍼 환경의 공간입니다.
* **[!UICONTROL Category]** : 오퍼가 정렬되는 특정 폴더입니다. 카테고리를 지정하지 않으면 테마를 선택하지 않은 경우 환경에 포함된 모든 오퍼가 오퍼 엔진에서 고려됩니다.
* **[!UICONTROL Themes]** : 카테고리에 업스트림으로 정의된 주요 단어. 필터 역할을 하며 카테고리 세트에서 오퍼를 선택하여 표시할 오퍼 수를 구체화할 수 있습니다.
* **[!UICONTROL Number of propositions]** : 엔진에서 반환하여 게재 본문에 삽입할 수 있는 오퍼 수입니다. 오퍼가 메시지에 삽입되지 않으면 오퍼가 계속 생성되지만 표시되지 않습니다.
* **[!UICONTROL Exclude non-eligible recipients]** : 이 옵션을 사용하면 적격 제안이 충분하지 않은 수신자를 제외하는 기능을 활성화하거나 비활성화할 수 있습니다. 적격 제안 수는 요청된 제안 수보다 적을 수 있습니다. 이 상자를 선택하면 제안이 충분하지 않은 수신자는 게재에서 제외됩니다. 이 옵션을 선택하지 않으면 이러한 수신자는 제외되지 않지만 요청된 제안 수는 없습니다.
* **[!UICONTROL Do not display anything if no offer is selected]** : 이 옵션을 사용하면 제안 중 하나가 없는 경우 메시지를 처리하는 방법을 선택할 수 있습니다. 이 상자를 선택하면 누락된 제안의 표현이 표시되지 않고 이 제안에 대한 메시지에 콘텐츠가 표시되지 않습니다. 상자를 선택하지 않으면 보내는 동안 메시지 자체가 취소되고 수신자는 더 이상 메시지를 받지 않습니다.

### 게재에 오퍼 제안 삽입 {#inserting-an-offer-proposition-into-a-delivery}

표시되는 오퍼 표현은 병합 필드를 통해 게재 본문에 삽입됩니다. 제안 수는 오퍼 엔진 호출의 매개 변수에 정의됩니다.

오퍼의 필드를 사용하여 게재를 개인화하거나, 이메일의 경우 렌더링 기능을 사용할 수 있습니다.

![](assets/offer_delivery_011.png)

## 게재 개요 제공 {#delivering-with-delivery-outlines}

게재 개요를 사용하여 게재에 오퍼를 표시할 수도 있습니다.

게재 개요에 대한 자세한 내용은 다음을 참조하십시오. [Campaign - MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline) 가이드.

1. 새 캠페인을 만들거나 기존 캠페인에 액세스합니다.
1. 캠페인의 을 통해 게재 개요에 액세스 **[!UICONTROL Edit]** > **[!UICONTROL Documents]** 탭.
1. 아웃라인을 추가한 다음 아웃라인을 마우스 오른쪽 버튼으로 클릭하고 를 선택하여 원하는 만큼 오퍼를 삽입합니다 **[!UICONTROL New]** > **[!UICONTROL Offer]**&#x200B;을 클릭한 다음 캠페인을 저장합니다.

   ![](assets/int_compo_offre1.png)

1. 액세스 권한이 있는 게재 아웃라인(예: DM 게재)을 포함하는 게재를 만듭니다.
1. 게재를 편집할 때 **[!UICONTROL Select a delivery outline]**.

   >[!NOTE]
   >
   >게재 유형에 따라 이 옵션은에서 찾을 수 있습니다. **[!UICONTROL Properties]** > **[!UICONTROL Advanced]** 메뉴(예: 이메일 게재)

   ![](assets/int_compo_offre2.png)

1. 사용 **[!UICONTROL Offers]** 버튼을 클릭하면 게재에 표시할 오퍼 수뿐만 아니라 오퍼 공간을 구성할 수 있습니다.

   ![](assets/int_compo_offre3.png)

1. 개인화 필드를 사용하여 게재 본문에 제안을 추가합니다(자세한 내용은 다음을 참조하십시오.) [게재에 오퍼 제안 삽입](#inserting-an-offer-proposition-into-a-delivery) 섹션) 또는 DM 게재의 경우 추출 파일 형식을 편집하여.

   제안은 게재 개요에서 참조된 오퍼에서 선택됩니다.

   >[!NOTE]
   >
   >오퍼 등급 및 가중치와 관련된 정보는 오퍼가 게재에서 직접 생성된 경우에만 제안 테이블에 저장됩니다.
