---
title: 인바운드 채널의 오퍼
seo-title: 인바운드 채널의 오퍼
description: 인바운드 채널의 오퍼
seo-description: null
page-status-flag: never-activated
uuid: 45cfc990-da38-451b-b65e-e9703e443a4d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: case-study
discoiquuid: 63245348-0402-4929-9c4f-71f01f97758e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: aa0eb7acfb5d3b622475544735aed37d6beea892

---


# 인바운드 채널의 오퍼{#offers-on-an-inbound-channel}

## 익명의 방문자에게 오퍼 제시 {#presenting-an-offer-to-an-anonymous-visitor}

니오뱅크 사이트는 해당 페이지를 탐색하는 확인되지 않은 방문자를 대상으로 한 오퍼를 웹 사이트에 표시하려고 합니다.

이 상호 작용을 설정하려면 다음을 수행합니다.

1. [익명의 환경 만들기](#creating-an-anonymous-environment)
1. [익명 오퍼 공간 만들기](#creating-anonymous-offer-spaces)
1. [오퍼 카테고리 및 테마 만들기](#creating-an-offer-category-and-a-theme)
1. [익명의 오퍼 만들기](#creating-anonymous-offers)
1. [웹 사이트에서 웹 오퍼 공간 구성](#configure-the-web-offer-space-on-the-website)

### 익명 환경 만들기 {#creating-an-anonymous-environment}

오퍼 환경 [](../../interaction/using/live-design-environments.md#creating-an-offer-environment) 만들기에 설명된 절차에 따라 방문자의 차원을 기반으로 익명 환경을 **만듭니다**.

새 환경이 포함된 트리 구조가 표시됩니다.

![](assets/offer_env_anonymous_003.png)

### 익명 오퍼 공간 만들기 {#creating-anonymous-offer-spaces}

1. 익명 환경(**방문자**)에서 **[!UICONTROL Administration]** > **[!UICONTROL Spaces]** 노드로 이동합니다.
1. 을 **[!UICONTROL New]** 클릭하여 콜 채널을 만듭니다.

   ![](assets/offer_inbound_anonymous_example_010.png)

   >[!NOTE]
   >
   >공백은 익명의 환경에 자동으로 연결됩니다.

1. 레이블을 변경하고 **[!UICONTROL Inbound Web]** 채널을 선택합니다. 또한 **[!UICONTROL Enable unitary mode]** 상자를 체크하셔야 합니다

   ![](assets/offer_inbound_anonymous_example_006.png)

1. 공간에 사용된 오퍼 컨텐츠 필드를 선택하고 관련 상자를 선택하여 필요에 따라 지정합니다.

   이렇게 하면 다음 요소 중 하나가 누락된 오퍼가 이 공간에 적용되지 않습니다.

   * 제목
   * HTML 컨텐츠
   * 이미지 URL
   * 대상 URL
   ![](assets/offer_inbound_anonymous_example_030.png)

1. 다음과 같이 HTML 렌더링 함수를 편집합니다.

   ```
   function (imageUrl, targetUrl, shortContent, htmlSource){
         var html = "<p><b>" + shortContent + "</b></p>";
         html += "<p>" + htmlSource + "</p>";
         html += "<a _urlType='11' href='" + targetUrl + "'><img src='" + encodeURI(imageUrl) + "'/></a>";
         return html;
       }   
   ```

   >[!CAUTION]
   >
   >렌더링 함수는 오퍼가 올바르게 표시되도록 이전에 선택한 순서대로 공간에 사용된 필드의 이름을 지정해야 합니다.

   ![](assets/offer_inbound_anonymous_example_031.png)

1. 오퍼 공간을 저장합니다.

### 오퍼 카테고리 및 테마 만들기 {#creating-an-offer-category-and-a-theme}

1. 방금 만든 환경 내의 **[!UICONTROL Offer catalog]** 노드로 이동합니다.
1. 노드를 마우스 오른쪽 단추로 **[!UICONTROL Offer catalog]** 클릭하고 **[!UICONTROL Create a new 'Offer category' folder]**&#x200B;선택합니다.

   예를 들어 새 카테고리, **금융 제품의** 이름을 지정합니다.

1. 카테고리 탭으로 **[!UICONTROL Eligibility]** 이동하여 **파이낸싱** (Finance)을 테마로 입력한 다음 변경 사항을 저장합니다.

   ![](assets/offer_inbound_anonymous_example_023.png)

### 익명 오퍼 만들기 {#creating-anonymous-offers}

1. 방금 만든 카테고리로 이동합니다.
1. 클릭 **[!UICONTROL New]**.

   ![](assets/offer_inbound_anonymous_example_013.png)

1. 즉시 사용 가능한 익명 오퍼 템플릿 또는 이전에 만든 템플릿을 선택합니다.

   ![](assets/offer_inbound_anonymous_example_014.png)

1. 레이블을 변경하고 오퍼를 저장합니다.

   ![](assets/offer_inbound_anonymous_example_015.png)

1. 탭으로 이동하여 해당 애플리케이션 컨텍스트에 따라 오퍼의 가중치를 지정합니다. **[!UICONTROL Eligibility]**

   이 예에서 오퍼는 연말에 대한 우선 순위로 사이트의 홈 페이지에 표시되도록 구성됩니다.

   ![](assets/offer_inbound_anonymous_example_016.png)

1. 탭으로 이동하여 오퍼 컨텐츠를 정의합니다. **[!UICONTROL Content]**

   >[!NOTE]
   >
   >웹 공간에 필요한 요소 목록을 **[!UICONTROL Content definitions]** 표시하도록 선택할 수 있습니다.

   ![](assets/offer_inbound_anonymous_example_017.png)

1. 두 번째 오퍼를 만듭니다.

   ![](assets/offer_inbound_anonymous_example_018.png)

1. 탭으로 이동하여 첫 번째 오퍼에 대해 동일한 가중치를 적용합니다. **[!UICONTROL Eligibility]**
1. 각 오퍼에 대한 승인 주기를 실행하여 승인 오퍼 공간과 온라인 환경에서 사용할 수 있도록 합니다.

### 웹 사이트에서 웹 오퍼 공간 구성 {#configure-the-web-offer-space-on-the-website}

방금 구성한 오퍼를 웹 사이트에 표시하려면 JavaScript 코드를 사이트의 HTML 페이지에 삽입하여 상호 작용 엔진을 호출합니다. 이 경우 자세한 내용은 인바운드 채널 [정보를](../../interaction/using/about-inbound-channels.md)참조하십시오.

1. HTML 페이지로 이동하여 이전에 만든 익명 오퍼 공간의 내부 이름과 일치하는 값을 포함하는 @id 속성을 삽입합니다([익명 오퍼 공간 [만들기](#creating-anonymous-offer-spaces)참조)( **i_**).

   ![](assets/offer_inbound_anonymous_example_019.png)

1. 호출 URL을 삽입합니다.

   ![](assets/offer_inbound_anonymous_example_020.png)

   위의 파란색 URL 상자는 인스턴스 이름, 환경의 내부 이름(익명 [환경](#creating-an-anonymous-environment)만들기 참조) 및 카테고리에 연결된 테마(오퍼 카테고리 및 테마[만들기)](#creating-an-offer-category-and-a-theme)에 해당합니다. 후자는 선택 사항입니다.

방문자가 웹 사이트의 홈 페이지에 액세스하면 **금융** 테마가 있는 오퍼가 HTML 페이지에 구성된 대로 표시됩니다.

![](assets/offer_inbound_anonymous_example_022.png)

페이지를 여러 번 방문하는 사용자는 동일한 가중치가 할당되었으므로 카테고리에서 하나 또는 다른 오퍼를 보게 됩니다.

## 확인되지 않은 연락처의 경우 익명 환경으로 전환 {#switching-to-an-anonymous-environment-in-case-of-unidentified-contacts}

Neobank 회사는 두 개의 서로 다른 대상에 대한 마케팅 오퍼를 만들려고 합니다. 익명의 웹 사이트 브라우저에 대한 일반 오퍼를 표시하려고 합니다. 이러한 사용자 중 한 명이 Neobank에서 제공하는 식별자를 가진 고객인 경우, Adobe는 로그인하는 즉시 개인화된 제안을 수신하기를 원합니다.

이 사례 조사는 다음 시나리오를 기반으로 합니다.

1. 방문자는 로그온하지 않고 Neobank 웹 사이트를 탐색합니다.

   ![](assets/offer_inbound_fallback_example_050.png)

   세 개의 익명의 오퍼가 페이지에 표시됩니다.Neobank **제품에 대한 두 개의** Best Offer와 Neobank 파트너로부터 한 가지 제안

   ![](assets/offer_inbound_fallback_example_051.png)

1. Neobank 고객인 사용자는 자신의 자격 증명을 사용하여 로그온합니다.

   ![](assets/offer_inbound_fallback_example_052.png)

   3개의 개인화된 오퍼가 표시됩니다.

   ![](assets/offer_inbound_fallback_example_053.png)

이 사례 연구를 구현하려면 두 가지 오퍼 환경이 필요합니다.하나는 익명의 상호 작용과, 다른 하나는 식별된 연락처에 대해 특별히 구성된 오퍼가 있는 것입니다. 식별된 오퍼 환경은 연락처가 로그인되어 있지 않아 식별되지 않는 경우 자동으로 익명 오퍼 환경으로 전환되도록 구성됩니다.

다음 단계를 적용합니다.

* 다음 단계를 사용하여 익명 인바운드 상호 작용에 대한 오퍼 카탈로그를 만듭니다.

   1. [익명의 연락처를 위한 환경 만들기](#creating-an-environment-for-anonymous-contacts)
   1. [익명 환경에 대한 오퍼 공간 구성](#configuring-offer-spaces-for-the-anonymous-environment)
   1. [익명 환경에서 오퍼 카테고리 만들기](#creating-offer-categories-in-an-anonymous-environment)
   1. [익명의 방문자를 위한 오퍼 만들기](#creating-offers-for-anonymous-visitors)

* 다음 단계를 사용하여 식별된 인바운드 인터랙션별 오퍼 카탈로그를 만듭니다.

   1. [식별된 환경에서 오퍼 공간 구성](#configure-the-offer-spaces-in-the-identified-environment)
   1. [식별된 환경에서 오퍼 카테고리 만들기](#creating-offer-categories-in-an-identified-environment)
   1. [개인화된 제안 만들기](#creating-personalized-offers)

* 오퍼 엔진에 대한 호출을 구성합니다.

   1. [웹 페이지에서 오퍼 공간 구성](#configuring-offer-spaces-on-the-web-page)
   1. [식별된 오퍼 공간의 고급 설정 지정](#specifying-the-advanced-settings-of-the-identified-offer-spaces)

### 익명의 연락처를 위한 환경 만들기 {#creating-an-environment-for-anonymous-contacts}

1. 배달 매핑 마법사를 통해 익명 인바운드 상호 작용에 대한 오퍼 환경을 만듭니다(방문자&#x200B;**매핑** ). 자세한 내용은 오퍼 [환경](../../interaction/using/live-design-environments.md#creating-an-offer-environment)만들기를 참조하십시오.

   ![](assets/offer_env_anonymous_003.png)

### 익명 환경에 대한 오퍼 공간 구성 {#configuring-offer-spaces-for-the-anonymous-environment}

웹 사이트에서 제공해야 하는 오퍼는 다음 두 가지 카테고리에 속합니다.최고의 **오퍼** 및 **파트너**. 이 예에서는 각 카테고리에 대한 특정 오퍼 공간을 만듭니다.

최적 오퍼 카테고리와 일치하는 오퍼 **공간을** 만들려면 다음 프로세스를 적용합니다.

1. Adobe Campaign 트리에서 방금 만든 익명 환경으로 이동하여 오퍼 공간을 추가합니다.

   ![](assets/offer_inbound_fallback_example_023.png)

1. 새 **[!UICONTROL Inbound web]** 문자 공간을 만듭니다.

   ![](assets/offer_inbound_fallback_example_024.png)

1. 레이블 입력:예를 **들어 웹 최고의 익명의** 오퍼를 참조하십시오.
1. 이 오퍼 공간에 사용된 오퍼 컨텐츠 필드를 추가하고 렌더링 기능을 구성합니다.

   ![](assets/offer_inbound_fallback_example_025.png)

   >[!CAUTION]
   >
   >렌더링 함수는 오퍼가 올바르게 표시되도록 이전에 선택한 순서대로 공간에 사용된 필드의 이름을 지정해야 합니다.

1. 동일한 프로세스를 사용하여 파트너 카테고리와 일치하는 인바운드 웹 채널 오퍼 공간을 **만듭니다** .

   ![](assets/offer_inbound_fallback_example_026.png)

### 익명 환경에서 오퍼 카테고리 만들기 {#creating-offer-categories-in-an-anonymous-environment}

먼저 두 가지 오퍼 카테고리를 만듭니다.우수 **오퍼** 카테고리 및 파트너 **카테고리** . 각 부문에는 익명의 연락처에 대한 두 개의 오퍼가 포함됩니다.

1. 방금 만든 익명 **[!UICONTROL Offer catalog]** 환경에서 로 이동합니다.
1. 최상의 오퍼가 **[!UICONTROL Offer category]** 있는 **** 폴더를 레이블로 추가합니다.

   ![](assets/offer_inbound_fallback_example_027.png)

1. Partner를 레이블로 **사용하여** 두 번째 카테고리를 만듭니다.

   ![](assets/offer_inbound_fallback_example_028.png)

### 익명의 방문자를 위한 오퍼 만들기 {#creating-offers-for-anonymous-visitors}

이제 위에 만든 각 카테고리에 두 개의 오퍼를 만듭니다.

1. 최상의 오퍼 **카테고리로** 이동하여 익명 오퍼를 만듭니다.

   ![](assets/offer_inbound_fallback_example_029.png)

1. 탭으로 이동하여 해당 애플리케이션 컨텍스트에 따라 오퍼의 가중치를 지정합니다. **[!UICONTROL Eligibility]**

   ![](assets/offer_inbound_fallback_example_030.png)

1. 탭으로 이동하여 오퍼 컨텐츠를 정의합니다. **[!UICONTROL Content]**

   ![](assets/offer_inbound_fallback_example_032.png)

1. 최적 오퍼 카테고리에서 두 번째 **오퍼를** 만듭니다.

   ![](assets/offer_inbound_fallback_example_031.png)

1. 파트너 **카테고리로** 이동하여 익명 오퍼를 만듭니다.
1. 탭으로 이동하여 오퍼 컨텐츠를 정의합니다. **[!UICONTROL Content]**

   ![](assets/offer_inbound_fallback_example_033.png)

1. 탭으로 이동하여 해당 애플리케이션 컨텍스트에 따라 오퍼의 가중치를 지정합니다. **[!UICONTROL Eligibility]**

   ![](assets/offer_inbound_fallback_example_034.png)

1. 파트너 카테고리에 대한 두 번째 오퍼를 **만듭니다** .

   ![](assets/offer_inbound_fallback_example_035.png)

1. 이 **[!UICONTROL Eligibility]** 탭으로 이동하여 오퍼가 웹 사이트에 연속적으로 표시되도록 이 카테고리의 첫 번째 오퍼에 적용한 것과 동일한 두께를 적용합니다.

   ![](assets/offer_inbound_fallback_example_036.png)

1. 각 오퍼에 대한 승인 주기를 실행하여 라이브로 만듭니다. 컨텐츠를 승인할 때 오퍼에 따라 **파트너** 또는 **최고 오퍼** 공간을 활성화합니다.

### 식별된 환경에서 오퍼 공간 구성 {#configure-the-offer-spaces-in-the-identified-environment}

웹 사이트에서 제공할 오퍼는 다음 두 가지 카테고리에서 가져옵니다.최고의 **오퍼** 및 **파트너**. 이 예에서는 각 카테고리에 대한 특정 공간을 만듭니다.

두 오퍼 공간을 만들려면 익명 오퍼 공간에 대해 동일한 절차를 적용합니다. 익명 [환경을](#configuring-offer-spaces-for-the-anonymous-environment)위한 오퍼 공간 구성을 참조하십시오.

1. Adobe Campaign 트리에서 방금 만든 환경으로 이동하여 베스트 오퍼 및 **파트너** 오퍼 **공간을** 추가합니다.
1. 익명 환경에 [](#configuring-offer-spaces-for-the-anonymous-environment)대한 오퍼 공간 구성에서 자세히 설명된 프로세스를 적용합니다.

   ![](assets/offer_inbound_fallback_example_005.png)

1. 옵션을 **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]** 선택합니다.

   ![](assets/offer_inbound_fallback_example_006.png)

1. 드롭다운 목록을 사용하여 이전에 만든 익명의 웹 오퍼 공간을 선택합니다(익명 [환경의](#configuring-offer-spaces-for-the-anonymous-environment)오퍼 공간 구성 참조).

   ![](assets/offer_inbound_fallback_example_007.png)

### 식별된 오퍼 공간의 고급 설정 지정 {#specifying-the-advanced-settings-of-the-identified-offer-spaces}

이 예에서는 Adobe Campaign 데이터베이스의 이메일 주소 덕분에 담당자 식별이 이루어집니다. 받는 사람 이메일을 스페이스에 추가하려면 다음 프로세스를 적용합니다.

1. 식별된 환경에서 오퍼 공간 폴더로 이동합니다.
1. [최고 **오퍼** ] 공간을 선택하고 을 클릭합니다 **[!UICONTROL Advanced parameters]**.

   ![](assets/offer_inbound_fallback_example_044.png)

1. 탭에서 을 **[!UICONTROL Target identification]** 클릭합니다 **[!UICONTROL Add]**.

   ![](assets/offer_inbound_fallback_example_046.png)

1. 을 **[!UICONTROL Edit expression]**&#x200B;클릭하고 수신자 테이블로 이동한 다음 **[!UICONTROL Email]** 필드를 선택합니다.

   ![](assets/offer_inbound_fallback_example_047.png)

1. 을 클릭하여 **[!UICONTROL OK]** 창을 닫고 우수 오퍼 **[!UICONTROL Advanced parameters]** 오퍼 공간 구성을 **** 마칩니다.
1. 파트너 오퍼 공간에 동일한 프로세스를 **적용합니다** .

   ![](assets/offer_inbound_fallback_example_048.png)

### 식별된 환경에서 오퍼 카테고리 만들기 {#creating-offer-categories-in-an-identified-environment}

두 개의 개별 카테고리를 만들 예정입니다.최고 **오퍼** 카테고리 및 파트너 **카테고리는 각각** 두 개의 개인화된 오퍼가 있습니다.

1. 식별된 환경의 **[!UICONTROL Offer catalogs]** 노드로 이동합니다.
1. 익명의 환경에서처럼, 베스트 오퍼 및 파트너가 **[!UICONTROL Offer category]** 레이블로 **두 개의****폴더를** 추가합니다.

   ![](assets/offer_inbound_fallback_example_009.png)

### 개인화된 제안 만들기 {#creating-personalized-offers}

각 카테고리에 대해 두 개의 개인화된 제안(예: 네 개의 제안)을 만들고 싶습니다.

1. 최고 오퍼 **카테고리로** 이동하여 첫 번째 맞춤형 오퍼를 만듭니다.

   ![](assets/offer_inbound_fallback_example_011.png)

1. 탭으로 이동하여 해당 애플리케이션 컨텍스트에 따라 오퍼의 가중치를 지정합니다. **[!UICONTROL Eligibility]**

   ![](assets/offer_inbound_fallback_example_012.png)

1. 탭으로 이동하여 오퍼 컨텐츠를 정의합니다. **[!UICONTROL Content]**

   ![](assets/offer_inbound_fallback_example_013.png)

1. 최적 오퍼 카테고리에서 두 번째 **오퍼를** 만듭니다.

   ![](assets/offer_inbound_fallback_example_014.png)

1. 파트너 **카테고리로** 이동하여 개인화된 오퍼를 만듭니다.

   ![](assets/offer_inbound_fallback_example_015.png)

1. 탭으로 이동하여 해당 애플리케이션 컨텍스트에 따라 오퍼의 가중치를 지정합니다. **[!UICONTROL Eligibility]**

   ![](assets/offer_inbound_fallback_example_016.png)

1. 파트너 카테고리에 대한 두 번째 오퍼를 **만듭니다** .

   ![](assets/offer_inbound_fallback_example_017.png)

1. 이 **[!UICONTROL Eligibility]** 탭으로 이동하여 오퍼가 웹 사이트에 연속적으로 표시되도록 이 카테고리의 첫 번째 오퍼에 적용한 것과 동일한 두께를 적용합니다.
1. 각 오퍼에 대한 승인 주기를 실행하여 업데이트를 시작합니다. 컨텐츠 승인 중에 파트너 **또는** 우수 **오퍼** 공간을 활성화하십시오.

### 웹 페이지에서 오퍼 공간 구성 {#configuring-offer-spaces-on-the-web-page}

Neobank 회사의 웹 사이트에는 다음과 같은 세 가지 오퍼를 위한 공백이 있습니다.은행 관련 프로모션의 경우 두 개, **파트너** 카테고리의 오퍼에 대한 **두 개** .

![](assets/offer_inbound_fallback_example_038.png)

웹 사이트의 HTML 페이지에서 이러한 오퍼 공간을 구성하려면 다음 프로세스를 적용합니다.

1. HTML 페이지의 컨텐츠에 3개를 삽입합니다.

   값이 @id인 요소를 사용하여 웹 사이트의 다양한 오퍼 공간에서 오퍼를 호출할 수 있습니다.

   ![](assets/offer_inbound_fallback_example_039.png)

1. 그런 다음 속성 값을 정의하는 스크립트를 삽입합니다.

   ![](assets/offer_inbound_fallback_example_040.png)

   이 예에서 ContBO1 **** 및 **ContBO2** 는 **OsWebBestOfferIdentified**&#x200B;값을 받습니다 **. 즉, 이전에 식별된 환경에서** 생성된 Best Offer 오퍼의 내부 이름을 받습니다. CatBestOffer **및** CatBestOfferAnniguym **값은** 익명 및 식별된 환경을 위한 Best Offer **** 범주의 내부 이름과 일치합니다.

   ![](assets/offer_inbound_fallback_example_041.png)

   마찬가지로 **ContPtn은** 식별된 **환경에서 생성된 Partner** 오퍼 공간의 내부 이름과 일치하는 **** OSWebPartnerIdentified 값을 받습니다. **CatPartner** 및 **CatPartnerAnunknown은** 익명 및 식별된 환경의 **Partner 카테고리의 내부 이름과** 일치합니다.

   ![](assets/offer_inbound_fallback_example_042.png)

1. Neobank 사이트에 로그온하는 사람을 식별할 수 있는 정보를 interactionTarget 변수에 **할당합니다** .

   ![](assets/offer_inbound_fallback_example_043.png)

   개인 ID는 브라우저 쿠키, URL의 읽기 매개 변수, 이메일 또는 개인 식별자를 기반으로 할 수 있습니다. 기본 키가 아닌 수신자 테이블의 필드를 사용하는 경우 공간의 고급 매개 변수에 정의해야 합니다(식별된 오퍼 공간의 [고급 설정 지정 참조](#specifying-the-advanced-settings-of-the-identified-offer-spaces)).

1. 호출 URL을 삽입합니다.

   ![](assets/offer_inbound_fallback_example_049.png)

   URL에는 식별된 **환경의**&#x200B;내부 이름인 EnvNeobankRecip가 포함됩니다.

웹 페이지를 열 때;스크립트를 사용하면 상호 작용 엔진을 호출하여 웹 페이지의 관련 공간에 오퍼 컨텐츠를 표시할 수 있습니다. Adobe Campaign 서버에 대한 단일 호출에서 엔진은 선택할 환경, 오퍼 공간 및 카테고리를 결정합니다.

이 예에서 엔진은 식별된 환경(EnvNeobankIdnRecipe)을&#x200B;**인식합니다**. 이 오퍼는 오퍼 공간(**OSWebBestOfferIdentified**) 및 **가장 좋은 오퍼** 카테고리(CatBestOffer **)를 식별하며, 웹 페이지에 있는 첫 번째 및 두 번째 오퍼에 대한** CatBestOffer ************)와 (OSWosteve 파트너식별된 파트너) 오퍼와 카테고리 사이트에서 세 번째 오퍼 공간을 위한 CatPartner를 중단합니다.

엔진이 받는 사람을 식별할 수 없는 경우, 엔진은 식별된 오퍼 공간에서 참조되는 익명의 오퍼 공백과 스크립트에 지정된 익명 카테고리(**CatPartner** 및 **CatPartnerAnunsored**)로 전환합니다.
