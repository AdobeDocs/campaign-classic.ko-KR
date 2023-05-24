---
product: campaign
title: 인바운드 채널에 대한 오퍼
description: 인바운드 채널에 대한 오퍼
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: 90afced3-465d-4370-8a33-51a7e4356135
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '2088'
ht-degree: 1%

---

# 인바운드 채널에 대한 오퍼{#offers-on-an-inbound-channel}



## 익명 방문자에게 오퍼 제공 {#presenting-an-offer-to-an-anonymous-visitor}

Neobank 사이트에서는 페이지를 검색하는 식별되지 않은 방문자를 대상으로 한 오퍼를 웹 사이트에 표시하려고 합니다.

이 상호 작용을 설정하려면 다음을 수행합니다.

1. [익명 환경 만들기](#creating-an-anonymous-environment)
1. [익명 오퍼 공간 만들기](#creating-anonymous-offer-spaces)
1. [오퍼 카테고리 및 테마 만들기](#creating-an-offer-category-and-a-theme)
1. [익명 오퍼를 만듭니다.](#creating-anonymous-offers)
1. [웹 사이트에서 웹 오퍼 공간 구성](#configure-the-web-offer-space-on-the-website)

### 익명 환경 만들기 {#creating-an-anonymous-environment}

다음에 설명된 절차를 따르십시오. [오퍼 환경 만들기](../../interaction/using/live-design-environments.md#creating-an-offer-environment) 을(를) 기반으로 익명 환경을 만들려면 **방문자 수**&#39; 차원.

새 환경이 포함된 트리 구조를 가져옵니다.

![](assets/offer_env_anonymous_003.png)

### 익명 오퍼 공간 만들기 {#creating-anonymous-offer-spaces}

1. 익명 환경(**방문자 수**) 로 이동합니다. **[!UICONTROL Administration]** > **[!UICONTROL Spaces]** 노드.
1. 클릭 **[!UICONTROL New]** 호출 채널을 만듭니다.

   ![](assets/offer_inbound_anonymous_example_010.png)

   >[!NOTE]
   >
   >공백은 익명 환경에 자동으로 연결됩니다.

1. 레이블을 변경하고 **[!UICONTROL Inbound Web]** 채널. 다음 사항도 확인해야 합니다. **[!UICONTROL Enable unitary mode]** 상자.

   ![](assets/offer_inbound_anonymous_example_006.png)

1. 공간에 사용되는 오퍼 콘텐츠 필드를 선택하고 관련 상자를 선택하여 필요에 따라 지정합니다.

   이러한 방식으로, 다음 요소 중 하나가 누락된 오퍼는 이 공간에 적합하지 않습니다.

   * 제목
   * HTML 콘텐츠
   * 이미지 URL
   * 대상 URL

   ![](assets/offer_inbound_anonymous_example_030.png)

1. HTML 렌더링 함수를 편집합니다. 예를 들어 다음과 같습니다.

   ```
   function (imageUrl, targetUrl, shortContent, htmlSource){
         var html = "<p><b>" + shortContent + "</b></p>";
         html += "<p>" + htmlSource + "</p>";
         html += "<a _urlType='11' href='" + targetUrl + "'><img src='" + encodeURI(imageUrl) + "'/></a>";
         return html;
       }   
   ```

   >[!IMPORTANT]
   >
   >렌더링 함수는 오퍼가 올바르게 표시되도록 스페이스에 사용된 필드의 이름을 이전에 선택한 순서대로 지정해야 합니다.

   ![](assets/offer_inbound_anonymous_example_031.png)

1. 오퍼 공간을 저장합니다.

### 오퍼 카테고리 및 테마 만들기 {#creating-an-offer-category-and-a-theme}

1. 로 이동 **[!UICONTROL Offer catalog]** 방금 생성한 환경 내의 노드입니다.
1. 마우스 오른쪽 단추 클릭 **[!UICONTROL Offer catalog]** 노드 및 선택 **[!UICONTROL Create a new 'Offer category' folder]**.

   새 범주 이름 지정, **금융 제품** 예.

1. 범주로 이동 **[!UICONTROL Eligibility]** 탭하고 입력 **파이낸싱** 를 테마로 지정한 다음 변경 내용을 저장합니다.

   ![](assets/offer_inbound_anonymous_example_023.png)

### 익명 오퍼 만들기 {#creating-anonymous-offers}

1. 방금 만든 카테고리로 이동합니다.
1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

   ![](assets/offer_inbound_anonymous_example_013.png)

1. 기본 제공 익명 오퍼 템플릿 또는 이전에 만든 템플릿을 선택합니다.

   ![](assets/offer_inbound_anonymous_example_014.png)

1. 레이블을 변경하고 오퍼를 저장합니다.

   ![](assets/offer_inbound_anonymous_example_015.png)

1. 로 이동 **[!UICONTROL Eligibility]** 을 탭하고 애플리케이션 컨텍스트에 따라 오퍼의 가중치를 지정합니다.

   이 예에서는 오퍼가 연말까지 우선 순위로 사이트의 홈 페이지에 표시되도록 구성됩니다.

   ![](assets/offer_inbound_anonymous_example_016.png)

1. 로 이동 **[!UICONTROL Content]** 을 탭하고 오퍼의 콘텐츠를 정의합니다.

   >[!NOTE]
   >
   >다음을 선택할 수 있습니다. **[!UICONTROL Content definitions]** 웹 공간에 필요한 요소 목록을 표시합니다.

   ![](assets/offer_inbound_anonymous_example_017.png)

1. 두 번째 오퍼를 만듭니다.

   ![](assets/offer_inbound_anonymous_example_018.png)

1. 로 이동 **[!UICONTROL Eligibility]** 을 탭하고 첫 번째 오퍼와 동일한 가중치를 적용합니다.
1. 각 오퍼와 승인된 오퍼 공간을 온라인 환경에서 사용할 수 있도록 하려면 각 오퍼에 대한 승인 주기를 실행합니다.

### 웹 사이트에서 웹 오퍼 공간 구성 {#configure-the-web-offer-space-on-the-website}

방금 구성한 오퍼가 웹 사이트에 표시되도록 하려면 사이트의 HTML 페이지에 JavaScript 코드를 삽입하여 상호 작용 엔진을 호출합니다(자세한 내용은 다음을 참조하십시오.) [인바운드 채널 정보](../../interaction/using/about-inbound-channels.md)).

1. HTML 페이지로 이동하여 이전에 만든 익명 오퍼 공간의 내부 이름과 일치하는 값이 있는 @id 속성을 삽입합니다( 참조). [익명 오퍼 공간 만들기](#creating-anonymous-offer-spaces)), 앞에 **i_**.

   ![](assets/offer_inbound_anonymous_example_019.png)

1. 호출 URL을 삽입합니다.

   ![](assets/offer_inbound_anonymous_example_020.png)

   위의 파란색 URL 상자는 인스턴스 이름, 환경의 내부 이름에 해당합니다( 참조). [익명 환경 만들기](#creating-an-anonymous-environment)) 및 카테고리에 연결된 테마([오퍼 카테고리 및 테마 만들기](#creating-an-offer-category-and-a-theme)). 후자는 선택 사항입니다.

방문자가 웹 사이트의 홈 페이지에 액세스하면 는 **파이낸싱** 테마는 HTML 페이지에 구성된 대로 표시됩니다.

![](assets/offer_inbound_anonymous_example_022.png)

페이지를 여러 번 방문하는 사용자는 둘 다 동일한 가중치가 할당되었으므로 카테고리에 있는 하나 또는 다른 오퍼를 보게 됩니다.

## 연락처가 확인되지 않은 경우 익명 환경으로 전환 {#switching-to-an-anonymous-environment-in-case-of-unidentified-contacts}

Neobank 회사는 두 개의 다른 타겟에 대한 마케팅 오퍼를 생성하려고 합니다. 익명 웹 사이트 브라우저에 대한 일반 오퍼를 표시하려고 합니다. 이 사용자 중 한 명이 Neobank에서 제공한 식별자를 가진 고객으로 밝혀지면 회사는 그들이 로그온하는 즉시 개인화된 오퍼를 받기를 원합니다.

이 사례 연구는 다음 시나리오를 기반으로 합니다.

1. 방문자가 로그온하지 않고 Neobank 웹 사이트를 탐색합니다.

   ![](assets/offer_inbound_fallback_example_050.png)

   세 개의 익명 오퍼가 페이지에 표시됩니다. **최상의 오퍼** 는 Neobank 제품에 대한 오퍼와 Neobank 파트너의 오퍼 하나를 제공합니다.

   ![](assets/offer_inbound_fallback_example_051.png)

1. Neobank 고객인 사용자는 자격 증명으로 로그온합니다.

   ![](assets/offer_inbound_fallback_example_052.png)

   세 가지 개인화된 오퍼가 표시됩니다.

   ![](assets/offer_inbound_fallback_example_053.png)

이 사례 연구를 구현하려면 익명 상호 작용용 및 특히 식별된 연락처에 대해 구성된 오퍼가 있는 두 개의 오퍼 환경이 있어야 합니다. 연락처가 로그온되지 않아 식별되지 않으면 식별된 오퍼 환경이 자동으로 익명 오퍼 환경으로 전환되도록 구성됩니다.

다음 단계를 적용합니다.

* 다음 단계를 사용하여 익명 인바운드 상호 작용과 관련된 오퍼 카탈로그를 만듭니다.

   1. [익명 연락처를 위한 환경 만들기](#creating-an-environment-for-anonymous-contacts)
   1. [익명 환경에 대한 오퍼 공간 구성](#configuring-offer-spaces-for-the-anonymous-environment)
   1. [익명 환경에서 오퍼 카테고리 만들기](#creating-offer-categories-in-an-anonymous-environment)
   1. [익명 방문자를 위한 오퍼 만들기](#creating-offers-for-anonymous-visitors)

* 다음 단계를 사용하여 식별된 인바운드 상호 작용과 관련된 오퍼 카탈로그를 만듭니다.

   1. [식별된 환경에서 오퍼 공간 구성](#configure-the-offer-spaces-in-the-identified-environment)
   1. [식별된 환경에서 오퍼 카테고리 만들기](#creating-offer-categories-in-an-identified-environment)
   1. [개인화된 오퍼 만들기](#creating-personalized-offers)

* 오퍼 엔진에 대한 호출을 구성합니다.

   1. [웹 페이지에서 오퍼 공간 구성](#configuring-offer-spaces-on-the-web-page)
   1. [식별된 오퍼 공간의 고급 설정 지정](#specifying-the-advanced-settings-of-the-identified-offer-spaces)

### 익명 연락처를 위한 환경 만들기 {#creating-an-environment-for-anonymous-contacts}

1. 게재 매핑 마법사( )를 통해 익명 인바운드 상호 작용을 위한 오퍼 환경을 만듭니다.**방문자** 매핑). 자세한 내용은 다음을 참조하십시오. [오퍼 환경 만들기](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

   ![](assets/offer_env_anonymous_003.png)

### 익명 환경에 대한 오퍼 공간 구성 {#configuring-offer-spaces-for-the-anonymous-environment}

웹 사이트에 표시되어야 하는 오퍼는 다음 두 가지 다른 범주에 속합니다. **최상의 오퍼** 및 **파트너**. 이 예제에서는 각 카테고리에 대한 특정 오퍼 공간을 만듭니다.

일치하는 오퍼 공간을 만들려면 **최상의 오퍼** 범주, 다음 프로세스를 적용합니다.

1. Adobe Campaign 트리에서 방금 만든 익명 환경으로 이동하여 오퍼 공간을 추가합니다.

   ![](assets/offer_inbound_fallback_example_023.png)

1. 새로 만들기 **[!UICONTROL Inbound web]** 공백 입력.

   ![](assets/offer_inbound_fallback_example_024.png)

1. 레이블 입력: **웹 모범 익명 오퍼** 예.
1. 이 오퍼 공간에 사용되는 오퍼 콘텐츠 필드를 추가하고 렌더링 기능을 구성합니다.

   ![](assets/offer_inbound_fallback_example_025.png)

   >[!IMPORTANT]
   >
   >렌더링 함수는 오퍼가 올바르게 표시되도록 스페이스에 사용된 필드의 이름을 이전에 선택한 순서대로 지정해야 합니다.

1. 동일한 프로세스를 사용하여 일치하는 인바운드 웹 채널 오퍼 공간을 만듭니다. **파트너** 범주.

   ![](assets/offer_inbound_fallback_example_026.png)

### 익명 환경에서 오퍼 카테고리 만들기 {#creating-offer-categories-in-an-anonymous-environment}

먼저 두 개의 오퍼 카테고리를 만듭니다. **최상의 오퍼** 범주 및 **파트너** 범주. 각 카테고리에는 익명 연락처에 대한 두 개의 오퍼가 포함됩니다.

1. 로 이동 **[!UICONTROL Offer catalog]** 방금 생성한 익명 환경에서.
1. 추가 **[!UICONTROL Offer category]** 폴더 **최상의 오퍼** 레이블로.

   ![](assets/offer_inbound_fallback_example_027.png)

1. 을 사용하여 두 번째 카테고리 만들기 **파트너** 레이블로.

   ![](assets/offer_inbound_fallback_example_028.png)

### 익명 방문자를 위한 오퍼 만들기 {#creating-offers-for-anonymous-visitors}

이제 위에서 만든 각 범주에서 두 개의 오퍼를 만듭니다.

1. 로 이동 **최상의 오퍼** 카테고리에 추가하고 익명 오퍼를 만듭니다.

   ![](assets/offer_inbound_fallback_example_029.png)

1. 로 이동 **[!UICONTROL Eligibility]** 을 탭하고 애플리케이션 컨텍스트에 따라 오퍼의 가중치를 지정합니다.

   ![](assets/offer_inbound_fallback_example_030.png)

1. 로 이동 **[!UICONTROL Content]** 을 탭하고 오퍼의 콘텐츠를 정의합니다.

   ![](assets/offer_inbound_fallback_example_032.png)

1. 에서 두 번째 오퍼를 만듭니다. **최상의 오퍼** 범주.

   ![](assets/offer_inbound_fallback_example_031.png)

1. 로 이동 **파트너** 카테고리에 추가하고 익명 오퍼를 만듭니다.
1. 로 이동 **[!UICONTROL Content]** 을 탭하고 오퍼의 콘텐츠를 정의합니다.

   ![](assets/offer_inbound_fallback_example_033.png)

1. 로 이동 **[!UICONTROL Eligibility]** 을 탭하고 애플리케이션 컨텍스트에 따라 오퍼의 가중치를 지정합니다.

   ![](assets/offer_inbound_fallback_example_034.png)

1. 에 대한 두 번째 오퍼 만들기 **파트너** 범주.

   ![](assets/offer_inbound_fallback_example_035.png)

1. 로 이동 **[!UICONTROL Eligibility]** 을 탭하고 이 카테고리의 첫 번째 오퍼에 적용한 것과 동일한 가중치를 적용하여 오퍼가 웹 사이트에 연속적으로 표시되도록 합니다.

   ![](assets/offer_inbound_fallback_example_036.png)

1. 각 오퍼에 대한 승인 주기를 실행하여 실행을 시작합니다. 콘텐츠를 승인할 때 를 활성화합니다. **파트너** 또는 **최상의 오퍼** 오퍼에 따르면 오퍼 공간입니다.

### 식별된 환경에서 오퍼 공간 구성 {#configure-the-offer-spaces-in-the-identified-environment}

웹 사이트에 제공할 오퍼는 다음 두 가지 범주에서 가져옵니다. **최상의 오퍼** 및 **파트너**. 이 예제에서는 각 카테고리에 대해 특정 공간을 만들려고 합니다.

두 개의 오퍼 공간을 만들려면 익명 오퍼 공간에 대해 와 동일한 절차를 적용합니다. 을(를) 참조하십시오 [익명 환경에 대한 오퍼 공간 구성](#configuring-offer-spaces-for-the-anonymous-environment).

1. Adobe Campaign 트리에서 방금 만든 환경으로 이동하여 추가합니다 **최상의 오퍼** 및 **파트너** 오퍼 스페이스.
1. 다음에 자세히 설명된 프로세스 적용 [익명 환경에 대한 오퍼 공간 구성](#configuring-offer-spaces-for-the-anonymous-environment).

   ![](assets/offer_inbound_fallback_example_005.png)

1. 다음 항목 선택 **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]** 옵션을 선택합니다.

   ![](assets/offer_inbound_fallback_example_006.png)

1. 드롭다운 목록을 사용하여 이전에 만든 익명 웹 오퍼 공간을 선택합니다( 참조). [익명 환경에 대한 오퍼 공간 구성](#configuring-offer-spaces-for-the-anonymous-environment)).

   ![](assets/offer_inbound_fallback_example_007.png)

### 식별된 오퍼 공간의 고급 설정 지정 {#specifying-the-advanced-settings-of-the-identified-offer-spaces}

이 예제에서 연락처 식별은 Adobe Campaign 데이터베이스의 이메일 주소 덕분에 발생합니다. 스페이스에 수신자 이메일을 추가하려면 다음 프로세스를 적용합니다.

1. 식별된 환경에서 오퍼 공간 폴더로 이동합니다.
1. 다음 항목 선택 **최상의 오퍼** 오퍼 스페이스 및 클릭 **[!UICONTROL Advanced parameters]**.

   ![](assets/offer_inbound_fallback_example_044.png)

1. **[!UICONTROL Target identification]** 탭에서 **[!UICONTROL Add]**&#x200B;을(를) 클릭합니다 .

   ![](assets/offer_inbound_fallback_example_046.png)

1. 클릭 **[!UICONTROL Edit expression]**&#x200B;를 클릭하고 수신자 테이블로 이동한 다음 **[!UICONTROL Email]** 필드.

   ![](assets/offer_inbound_fallback_example_047.png)

1. 클릭 **[!UICONTROL OK]** 닫으려면 다음을 수행하십시오. **[!UICONTROL Advanced parameters]** 창 및 구성 완료 **최상의 오퍼** 오퍼 공간.
1. 에 동일한 프로세스 적용 **파트너** 오퍼 공간.

   ![](assets/offer_inbound_fallback_example_048.png)

### 식별된 환경에서 오퍼 카테고리 만들기 {#creating-offer-categories-in-an-identified-environment}

두 개의 개별 카테고리를 만듭니다. **최상의 오퍼** 범주 및 **파트너** 카테고리(각 항목에는 두 개의 개인화된 오퍼가 있음)

1. 로 이동 **[!UICONTROL Offer catalogs]** 식별된 환경의 노드
1. 익명 환경에서와 같이 두 개의 을 추가합니다 **[!UICONTROL Offer category]** 폴더 **최상의 오퍼** 및 **파트너** 레이블로 사용됩니다.

   ![](assets/offer_inbound_fallback_example_009.png)

### 개인화된 오퍼 만들기 {#creating-personalized-offers}

각 카테고리에 대해 두 개의 개인화된 오퍼, 즉 네 개의 오퍼를 만들려고 합니다.

1. 로 이동 **최상의 오퍼** 카테고리에 추가하고 첫 번째 개인화된 오퍼를 만듭니다.

   ![](assets/offer_inbound_fallback_example_011.png)

1. 로 이동 **[!UICONTROL Eligibility]** 을 탭하고 애플리케이션 컨텍스트에 따라 오퍼의 가중치를 지정합니다.

   ![](assets/offer_inbound_fallback_example_012.png)

1. 로 이동 **[!UICONTROL Content]** 을 탭하고 오퍼의 콘텐츠를 정의합니다.

   ![](assets/offer_inbound_fallback_example_013.png)

1. 에서 두 번째 오퍼를 만듭니다. **최상의 오퍼** 범주.

   ![](assets/offer_inbound_fallback_example_014.png)

1. 로 이동 **파트너** 카테고리에 추가하고 개인화된 오퍼를 만듭니다.

   ![](assets/offer_inbound_fallback_example_015.png)

1. 로 이동 **[!UICONTROL Eligibility]** 을 탭하고 애플리케이션 컨텍스트에 따라 오퍼의 가중치를 지정합니다.

   ![](assets/offer_inbound_fallback_example_016.png)

1. 에 대한 두 번째 오퍼 만들기 **파트너** 범주.

   ![](assets/offer_inbound_fallback_example_017.png)

1. 로 이동 **[!UICONTROL Eligibility]** 을 탭하고 이 카테고리의 첫 번째 오퍼에 적용한 것과 동일한 가중치를 적용하여 오퍼가 웹 사이트에 연속적으로 표시되도록 합니다.
1. 각 오퍼에 대한 승인 주기를 실행하여 업데이트를 시작합니다. 콘텐츠 승인 중 활성화 **파트너** 또는 **최상의 오퍼** 오퍼 스페이스.

### 웹 페이지에서 오퍼 공간 구성 {#configuring-offer-spaces-on-the-web-page}

Neobank 회사의 웹 사이트에는 3개의 오퍼 공간이 있습니다. 2개의 은행 관련 오퍼는 **최상의 오퍼** 카테고리 및 의 오퍼에 대한 카테고리 **파트너** 범주.

![](assets/offer_inbound_fallback_example_038.png)

웹 사이트의 HTML 페이지에서 이러한 오퍼 공간을 구성하려면 다음 프로세스를 적용합니다.

1. HTML 페이지의 콘텐츠에 3을 삽입합니다.

   값이 웹 사이트의 다양한 오퍼 공간에서 오퍼를 호출할 수 있도록 해 주는 @id 속성을 가진 요소입니다.

   ![](assets/offer_inbound_fallback_example_039.png)

1. 그런 다음 속성 값을 정의하는 스크립트를 삽입합니다.

   ![](assets/offer_inbound_fallback_example_040.png)

   이 예에서는 **ContBO1** 및 **ContBO2** 값 받기 **OsWebBestOfferIdentified**, 즉 의 내부 이름입니다. **최상의 오퍼** 식별된 환경에서 이전에 만든 오퍼 공간입니다. 다음 **캣베스트 오퍼** 및 **CatBestOfferAnonym** 값은 의 내부 이름과 일치합니다. **최상의 오퍼** 익명 및 식별된 환경에 대한 카테고리입니다.

   ![](assets/offer_inbound_fallback_example_041.png)

   마찬가지로 **ContPtn** 수신 **OSWebPartnerIdentified** 값: 의 내부 이름과 일치 **파트너** 식별된 환경에서 오퍼 공간을 만들었습니다. **CatPartner** 및 **CatPartnerAnonym** 의 내부 이름과 일치 **파트너** 익명 및 식별된 환경에 대한 카테고리입니다.

   ![](assets/offer_inbound_fallback_example_042.png)

1. Neobank 사이트에 로그온하는 사용자를 식별할 수 있는 정보를 **interactionTarget** 변수를 채우는 방법에 따라 페이지를 순서대로 표시합니다.

   ![](assets/offer_inbound_fallback_example_043.png)

   개인의 식별은 브라우저 쿠키, URL의 읽기 매개 변수, 이메일 또는 개인의 식별자를 기반으로 할 수 있습니다. 기본 키가 아닌 수신자 테이블의 필드를 사용하는 경우 공간의 고급 매개 변수에서 정의해야 합니다( 참조) [식별된 오퍼 공간의 고급 설정 지정](#specifying-the-advanced-settings-of-the-identified-offer-spaces)).

1. 호출 URL을 삽입합니다.

   ![](assets/offer_inbound_fallback_example_049.png)

   URL에는 다음이 포함됩니다. **EnvNeobankRecip**, 식별된 환경의 내부 이름입니다.

웹 페이지를 열면 스크립트를 사용하여 상호 작용 엔진을 호출하여 웹 페이지의 관련 공간에 오퍼 콘텐츠를 표시할 수 있습니다. Adobe Campaign 서버에 대한 단일 호출에서 엔진은 선택할 환경, 오퍼 공간 및 범주를 결정합니다.

이 예에서 엔진은 식별된 환경(**EnvNeobankIdnRecip**). 오퍼 공간(**OSWebBestOfferIdentified**) 및 **최상의 오퍼** 범주(**캣베스트 오퍼**)을 참조하십시오.**OSWebPartnerIdentified**) 오퍼 공간 및 **파트너** 범주(**CatPartner**)을 클릭하여 사이트에서 세 번째 오퍼 공간을 만듭니다.

엔진에서 수신자를 식별할 수 없으면 식별된 오퍼 공간에서 참조된 익명 오퍼 공간으로 전환하고 익명 범주(**CatPartner** 및 **CatPartnerAnonym**)를 입력합니다.
