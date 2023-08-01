---
product: campaign
title: 오퍼 만들기
description: 오퍼 만들기
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: c6dd2709-06e3-4227-bbec-99f3d80144fe
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 3%

---

# 오퍼 만들기{#creating-an-offer}



## 오퍼 만들기 {#creating-the-offer}

오퍼를 만들려면 다음 단계를 적용합니다.

1. 로 이동 **[!UICONTROL Campaigns]** 탭을 클릭하고 **[!UICONTROL Offers]** 링크를 클릭합니다.

   ![](assets/offer_create_001.png)

1. **[!UICONTROL Create]** 버튼을 클릭합니다.

   ![](assets/offer_create_005.png)

1. 레이블을 변경하고 오퍼가 속해야 하는 범주를 선택합니다.

   ![](assets/offer_create_002.png)

1. 클릭 **[!UICONTROL Save]** 을 클릭하여 오퍼를 만듭니다.

   ![](assets/offer_create_003.png)

   오퍼는 플랫폼에서 사용할 수 있으며 해당 콘텐츠를 구성할 수 있습니다.

   ![](assets/offer_create_004.png)

## 오퍼 자격 구성 {#configuring-offer-eligibility}

다음에서 **[!UICONTROL Eligibility]** 탭에서 오퍼가 유효하고 표시할 수 있는 기간, 대상에 적용할 필터 및 오퍼 가중치를 정의합니다.

### 오퍼의 자격 기간 정의 {#defining-the-eligibility-period-of-an-offer}

오퍼의 자격 기간을 정의하려면 드롭다운 목록을 사용하고 달력에서 시작 및 종료 날짜를 선택합니다.

![](assets/offer_eligibility_create_002.png)

이 날짜 외에는 오퍼가 상호 작용 엔진에 의해 선택되지 않습니다. 오퍼 범주에 대한 자격 날짜를 구성한 경우 가장 제한적인 기간이 적용됩니다.

### 대상에 대한 필터 {#filters-on-the-target}

오퍼 대상에 필터를 적용할 수 있습니다.

이렇게 하려면 **[!UICONTROL Edit query]** 을(를) 연결하고 적용할 필터를 선택합니다. (참조: [이 섹션](../../platform/using/steps-to-create-a-query.md#step-4---filter-data)).

![](assets/offer_eligibility_create_003.png)

미리 정의된 필터가 이미 만들어진 경우 사용자 필터 목록에서 해당 필터를 선택할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [사전 정의된 필터 만들기](../../interaction/using/creating-predefined-filters.md).

![](assets/offer_eligibility_create_004.png)

### 오퍼 가중치 {#offer-weight}

엔진이 대상이 적합한 여러 오퍼 중에서 결정할 수 있도록 하려면 오퍼에 하나 이상의 가중치를 할당해야 합니다. 필요한 경우 대상에 필터를 적용하거나 가중치가 적용될 오퍼 공간을 제한할 수도 있습니다. 가중치가 더 낮은 오퍼보다 가중치가 더 큰 오퍼가 선호될 것입니다.

예를 들어 기간, 특정 타겟 또는 오퍼 공간을 구분하도록 동일한 오퍼에 대해 여러 개의 가중치를 구성할 수 있습니다.

예를 들어, 오퍼는 18~25세의 연락처에 대해 A의 가중치를 가질 수 있고, 해당 범위 이상의 연락처에 대해 B의 가중치를 가질 수 있다. 여름 내내 오퍼를 받을 수 있다면 7월에 A의 가중치를, 8월에 B의 가중치를 가질 수도 있다.

>[!NOTE]
>
>할당된 가중치는 오퍼가 속한 카테고리의 매개 변수에 따라 일시적으로 수정할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [오퍼 카테고리 만들기](../../interaction/using/creating-offer-categories.md).

오퍼에 가중치를 만들려면 다음 단계를 적용합니다.

1. **[!UICONTROL Add]**&#x200B;를 클릭합니다.

   ![](assets/offer_weight_create_001.png)

1. 레이블을 변경하고 가중치를 할당합니다. 기본적으로 1입니다.

   ![](assets/offer_weight_create_006.png)

   >[!IMPORTANT]
   >
   >가중치를 입력하지 않으면(0) 타겟은 오퍼에 적합한 것으로 간주되지 않습니다.

1. 주어진 기간에 가중치를 적용하려면 자격 일자를 정의합니다.

   ![](assets/offer_weight_create_002.png)

1. 필요한 경우 가중치를 특정 오퍼 공간으로 제한합니다.

   ![](assets/offer_weight_create_003.png)

1. 대상에 필터를 적용합니다.

   ![](assets/offer_weight_create_004.png)

1. 클릭 **[!UICONTROL OK]** 무게를 줄이려면

   ![](assets/offer_weight_create_005.png)

   >[!NOTE]
   >
   >타겟이 선택한 오퍼에 대해 여러 가중치에 적격인 경우, 엔진은 최상의(가장 높은) 가중치를 유지합니다. 오퍼 엔진을 호출할 때 오퍼는 연락처당 최대 한 번까지 선택됩니다.

### 오퍼 자격 규칙 요약 {#a-summary-of-offer-eligibility-rules}

구성이 완료되면 자격 규칙에 대한 요약을 오퍼 대시보드에서 사용할 수 있습니다.

보려면 **[!UICONTROL Schedule and eligibility rules]** 링크를 클릭합니다.

![](assets/offer_eligibility_create_005.png)

## 오퍼 콘텐츠 만들기 {#creating-the-offer-content}

1. 다음을 클릭합니다. **[!UICONTROL Edit]** 탭을 클릭한 다음 **[!UICONTROL Content]** 탭.

   ![](assets/offer_content_create_001.png)

1. 오퍼 컨텐츠의 다양한 필드를 작성합니다.

   * **[!UICONTROL Title]** : 오퍼에 표시할 제목을 지정합니다. 경고: 오퍼의 레이블을 참조하지 않는데, 이는 오퍼에 정의되어 있습니다. **[!UICONTROL General]** 탭.
   * **[!UICONTROL Destination URL]** : 오퍼의 URL을 지정합니다. 올바르게 처리하려면 &quot;http://&quot; 또는 &quot;https://&quot;로 시작해야 합니다.
   * **[!UICONTROL Image URL]** : 오퍼 이미지에 대한 URL 또는 액세스 경로를 지정합니다.
   * **[!UICONTROL HTML content]** / **[!UICONTROL Text content]** : 원하는 탭에 오퍼의 본문을 입력합니다. 추적을 생성하려면 다음을 수행합니다 **[!UICONTROL HTML content]** 은(는) HTML 요소로 구성되어야 하며 `<div>` 요소를 입력합니다. 예를 들어, `<table>` HTML 페이지의 요소는 다음과 같습니다.

   ```
      <div> 
       <table>
        <tr>
         <th>Month</th>
         <th>Savings</th>   
        </tr>   
        <tr>    
         <td>January</td>
         <td>$100</td>   
        </tr> 
       </table> 
      </div>
   ```

   수락 URL 정의는에 나와 있습니다. [제안이 수락될 때의 상태 구성](../../interaction/using/creating-offer-spaces.md#configuring-the-status-when-the-proposition-is-accepted) 섹션.

   ![](assets/offer_content_create_002.png)

   오퍼 공간 구성 중에 정의된 필수 필드를 찾으려면 **[!UICONTROL Content definitions]** 링크를 클릭하여 목록을 표시합니다. 자세한 내용은 다음을 참조하십시오. [오퍼 공간 만들기](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_content_create_003.png)

   이 예에서 오퍼는 제목, 이미지, HTML 컨텐츠 및 대상 URL을 포함해야 합니다.

## 오퍼 미리 보기 {#previewing-the-offer}

오퍼 콘텐츠를 구성하는 즉시, 수신자에게 표시될 오퍼를 미리 볼 수 있습니다. 방법은 다음과 같습니다.

1. 다음을 클릭합니다. **[!UICONTROL Preview]** 탭.

   ![](assets/offer_preview_create_001.png)

1. 보려는 오퍼의 표현을 선택합니다.

   ![](assets/offer_preview_create_002.png)

1. 오퍼 콘텐츠를 개인화한 경우 오퍼 타겟을 선택하여 개인화를 확인하십시오.

   ![](assets/offer_preview_create_003.png)

## 오퍼에 대한 가설 만들기 {#creating-a-hypothesis-on-an-offer}

오퍼 제안에 대한 가설을 생성할 수 있습니다. 이렇게 하면 관련 제품에 대해 수행된 구매에 대한 오퍼의 영향을 결정할 수 있습니다.

>[!NOTE]
>
>이러한 가설은 응답 관리자를 통해 수행됩니다. 사용권 계약을 확인하십시오.

오퍼 제안에 대해 수행되는 가설은 다음 항목에서 참조됩니다 **[!UICONTROL Measure]** 탭.

가설 만들기는 다음에서 자세히 설명합니다. [이 페이지](../../response/using/about-response-manager.md).

![](assets/offer_hypothesis_001.png)
