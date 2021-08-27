---
product: campaign
title: 오퍼 만들기
description: 오퍼 만들기
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: c6dd2709-06e3-4227-bbec-99f3d80144fe
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 2%

---

# 오퍼 만들기{#creating-an-offer}

![](../../assets/v7-only.svg)

## 오퍼 만들기 {#creating-the-offer}

오퍼를 만들려면 다음 단계를 적용합니다.

1. **[!UICONTROL Campaigns]** 탭으로 이동하여 **[!UICONTROL Offers]** 링크를 클릭합니다.

   ![](assets/offer_create_001.png)

1. **[!UICONTROL Create]** 버튼을 클릭합니다.

   ![](assets/offer_create_005.png)

1. 레이블을 변경하고 오퍼가 속해야 하는 카테고리를 선택합니다.

   ![](assets/offer_create_002.png)

1. **[!UICONTROL Save]** 을 클릭하여 오퍼를 만듭니다.

   ![](assets/offer_create_003.png)

   오퍼는 플랫폼에서 사용할 수 있으며 해당 콘텐츠를 구성할 수 있습니다.

   ![](assets/offer_create_004.png)

## 오퍼 자격 구성 {#configuring-offer-eligibility}

**[!UICONTROL Eligibility]** 탭에서 오퍼가 유효한 기간을 정의하고 오퍼를 표시할 수 있습니다. 이 필터는 대상에 적용할 필터와 오퍼 가중치입니다.

### 오퍼의 자격 기간 정의 {#defining-the-eligibility-period-of-an-offer}

오퍼의 자격 기간을 정의하려면 드롭다운 목록을 사용하고 달력에서 시작 및 종료 날짜를 선택합니다.

![](assets/offer_eligibility_create_002.png)

이 날짜 이외에는 상호 작용 엔진에서 오퍼를 선택하지 않습니다. 오퍼 카테고리에 대한 자격 날짜도 구성한 경우 가장 제한적인 기간이 적용됩니다.

### 타겟의 필터 {#filters-on-the-target}

필터를 오퍼 타겟에 적용할 수 있습니다.

이렇게 하려면 **[!UICONTROL Edit query]** 링크를 클릭하고 적용할 필터를 선택합니다. ([이 섹션](../../platform/using/steps-to-create-a-query.md#step-4---filter-data) 참조).

![](assets/offer_eligibility_create_003.png)

사전 정의된 필터가 이미 만들어진 경우 사용자 필터 목록에서 해당 필터를 선택할 수 있습니다. 자세한 내용은 [사전 정의된 필터 만들기](../../interaction/using/creating-predefined-filters.md)를 참조하십시오.

![](assets/offer_eligibility_create_004.png)

### 오퍼 가중치 {#offer-weight}

엔진이 Target이 사용할 수 있는 여러 오퍼 중에서 결정하도록 하려면 오퍼에 하나 이상의 가중치를 지정해야 합니다. 필요한 경우 필터를 대상에 적용하거나 가중치가 적용될 오퍼 공간을 제한할 수도 있습니다. 가중치가 더 큰 오퍼는 더 적은 무게의 오퍼보다 선호될 것이다.

예를 들어 동일한 오퍼에 대해 여러 가중치를 구성할 수 있습니다. 예를 들어 지원 기간, 특정 타겟 또는 오퍼 공간을 구별할 수 있습니다.

예를 들어, 오퍼는 18~25세 사이의 연락처에 대해 A 중량이고 해당 범위 이상의 연락처에 대해서는 B 중량일 수 있습니다. 만약 제안이 여름 내내 자격이 된다면, 그것은 또한 7월에 A의 중량과 8월에 B의 중량을 가질 수 있습니다.

>[!NOTE]
>
>지정된 가중치는 오퍼가 속한 카테고리의 매개 변수에 따라 일시적으로 수정할 수 있습니다. 자세한 내용은 [오퍼 카테고리 만들기](../../interaction/using/creating-offer-categories.md)를 참조하십시오.

오퍼에서 가중치를 만들려면 다음 단계를 적용합니다.

1. **[!UICONTROL Add]**&#x200B;를 클릭합니다.

   ![](assets/offer_weight_create_001.png)

1. 레이블을 변경하고 가중치를 지정합니다. 기본적으로 1입니다.

   ![](assets/offer_weight_create_006.png)

   >[!IMPORTANT]
   >
   >가중치를 입력하지 않으면(0) 오퍼에 적합한 것으로 간주되지 않습니다.

1. 특정 기간에 대해 가중치를 적용하려면 자격 일자를 정의합니다.

   ![](assets/offer_weight_create_002.png)

1. 필요한 경우 가중치를 특정 오퍼 공간으로 제한합니다.

   ![](assets/offer_weight_create_003.png)

1. 대상에 필터를 적용합니다.

   ![](assets/offer_weight_create_004.png)

1. **[!UICONTROL OK]** 을 클릭하여 가중치를 저장합니다.

   ![](assets/offer_weight_create_005.png)

   >[!NOTE]
   >
   >선택한 오퍼에 대해 대상이 다중 가중치에 적합한 경우 엔진이 가장 높은(가장 높은) 가중치를 유지합니다. 오퍼 엔진을 호출하면 오퍼가 연락처당 최대 한 번 선택됩니다.

### 오퍼 자격 규칙 요약 {#a-summary-of-offer-eligibility-rules}

구성이 완료되면 오퍼 대시보드에서 자격 규칙 요약을 사용할 수 있습니다.

보려면 **[!UICONTROL Schedule and eligibility rules]** 링크를 클릭합니다.

![](assets/offer_eligibility_create_005.png)

## 오퍼 컨텐츠 만들기 {#creating-the-offer-content}

1. **[!UICONTROL Edit]** 탭을 클릭한 다음 **[!UICONTROL Content]** 탭을 클릭합니다.

   ![](assets/offer_content_create_001.png)

1. 오퍼 컨텐츠의 다양한 필드를 작성합니다.

   * **[!UICONTROL Title]** : 오퍼에 표시할 제목을 지정합니다. 경고: 이것은 **[!UICONTROL General]** 탭에 정의된 오퍼의 레이블을 참조하지 않습니다.
   * **[!UICONTROL Destination URL]** : 오퍼의 URL을 지정합니다. 올바르게 처리하려면 &quot;http://&quot; 또는 &quot;https://&quot;으로 시작해야 합니다.
   * **[!UICONTROL Image URL]** : 오퍼 이미지에 대한 URL 또는 액세스 경로를 지정합니다.
   * **[!UICONTROL HTML content]** /  **[!UICONTROL Text content]** : 원하는 탭에 오퍼 본문을 입력합니다. 추적을 생성하려면 **[!UICONTROL HTML content]** 을 `<div>` 유형 요소로 묶을 수 있는 HTML 요소로 구성해야 합니다. 예를 들어 HTML 페이지에서 `<table>` 요소의 결과는 다음과 같습니다.

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

   수락 URL 정의는 [제안이 수락될 때 상태 구성](../../interaction/using/creating-offer-spaces.md#configuring-the-status-when-the-proposition-is-accepted) 섹션에 나와 있습니다.

   ![](assets/offer_content_create_002.png)

   오퍼 공간 구성 중에 정의된 필수 필드를 찾으려면 **[!UICONTROL Content definitions]** 링크를 클릭하여 목록을 표시합니다. 자세한 내용은 [오퍼 공간 만들기](../../interaction/using/creating-offer-spaces.md)를 참조하십시오.

   ![](assets/offer_content_create_003.png)

   이 예에서 오퍼에는 제목, 이미지, HTML 콘텐츠 및 대상 URL이 포함되어야 합니다.

## 오퍼 미리 보기 {#previewing-the-offer}

오퍼 컨텐츠가 구성되면 수신자에 대해 표시될 오퍼를 미리 볼 수 있습니다. 방법은 다음과 같습니다.

1. **[!UICONTROL Preview]** 탭을 클릭합니다.

   ![](assets/offer_preview_create_001.png)

1. 보려는 오퍼 표현을 선택합니다.

   ![](assets/offer_preview_create_002.png)

1. 오퍼 콘텐츠를 개인화한 경우 개인화할 오퍼 대상을 선택합니다.

   ![](assets/offer_preview_create_003.png)

## 오퍼에 가설 만들기 {#creating-a-hypothesis-on-an-offer}

오퍼 제안에 대한 가설을 만들 수 있습니다. 오퍼가 해당 제품에 대해 수행된 구매에 미치는 영향을 파악할 수 있습니다.

>[!NOTE]
>
>이러한 가설이 응답 관리자를 통해 수행됩니다. 사용권 계약을 확인하십시오.

오퍼 제안에 대해 수행된 가설이 **[!UICONTROL Measure]** 탭에서 참조됩니다.

가설 만들기는 [이 페이지](../../response/using/about-response-manager.md)에 자세히 설명되어 있습니다.

![](assets/offer_hypothesis_001.png)
