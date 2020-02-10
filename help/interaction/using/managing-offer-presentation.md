---
title: 오퍼 프레젠테이션 관리
seo-title: 오퍼 프레젠테이션 관리
description: 오퍼 프레젠테이션 관리
seo-description: null
page-status-flag: never-activated
uuid: cf4614b9-a322-4170-aa6d-4f138f8ca2d2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: f6e44634-3a13-480e-ab44-f3c744054a96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 오퍼 프레젠테이션 관리{#managing-offer-presentation}

## 프레젠테이션 규칙 개요 {#presentation-rules-overview}

상호 작용을 통해 프레젠테이션 규칙을 사용하여 오퍼 제안의 흐름을 제어할 수 있습니다. 이러한 규칙은 상호 작용과 관련이 있으며 유형 규칙입니다. 이 매개 변수를 사용하면 이미 수신자에게 수행한 제안의 내역을 기반으로 오퍼를 제외시킬 수 있습니다. 이러한 항목은 환경에서 참조됩니다.

## 오퍼 프레젠테이션 규칙 만들기 및 참조 {#creating-and-referencing-an-offer-presentation-rule}

1. > **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** 노드로 이동합니다.
1. 유형 규칙을 만들고 **[!UICONTROL Offer presentation]** 유형을 선택합니다.

   ![](assets/offer_typology_001.png)

1. 규칙을 적용할 채널을 지정합니다.

   ![](assets/offer_typology_002.png)

1. 규칙의 응용 프로그램 기준을 구성합니다. 자세한 내용은 프레젠테이션 [규칙 설정을](#presentation-rule-settings)참조하십시오.
1. > **[!UICONTROL Administration]** > **[!UICONTROL Campaign execution]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typologies]** 노드로 이동하여 모든 **[!UICONTROL Offer presentation]** 유형 규칙을 그룹화하는 유형을 만듭니다.

   ![](assets/offer_typology_003.png)

1. 유형이 생성되면, 커서를 Typical 규칙 위에 놓고 방금 만든 TypeLogics에 그룹화합니다.

   ![](assets/offer_typology_004.png)

1. 오퍼 환경에서 드롭다운 목록을 사용하여 유형을 참조합니다.

   ![](assets/offer_typology_005.png)

## 프레젠테이션 규칙 설정 {#presentation-rule-settings}

### 애플리케이션 기준 {#application-criteria-}

탭에서 사용할 수 있는 응용 프로그램 기준을 **[!UICONTROL General]** 사용하면 프레젠테이션 규칙이 적용될 오퍼를 지정할 수 있습니다. 이렇게 하려면 아래 설명된 대로 쿼리를 만들고 관련 오퍼를 선택해야 합니다.

1. 분류 규칙에서 링크를 클릭하여 쿼리를 만듭니다. **[!UICONTROL Edit the rule application conditions...]**

   ![](assets/offer_typology_006.png)

1. 쿼리 창에서 유형 규칙을 적용하려는 오퍼에 필터를 적용할 수 있습니다.

   예를 들어 오퍼 카테고리를 선택할 수 있습니다.

   ![](assets/offer_typology_008.png)

### 오퍼 차원 {#offer-dimensions}

이 **[!UICONTROL Offer presentation]** 탭에서 환경에 구성된 것과 동일한 프레젠테이션 규칙의 크기를 지정해야 합니다.

이 **[!UICONTROL Targeting dimension]** 표는 받는 사람 표와 일치합니다(기본적으로:nms:recipient)를 참조하십시오. 타깃팅 차원과 연결된 제안 내역이 포함된 표와 **[!UICONTROL Storage dimension]** 일치합니다(기본적으로:nms:provisionRcp).

![](assets/offer_typology_009.png)

>[!NOTE]
>
>비표준 표를 사용할 수도 있습니다. 특정 타깃팅 차원을 사용하려면 타겟 매핑을 사용하여 전용 환경뿐만 아니라 테이블을 생성해야 합니다. 자세한 내용은 오퍼 [환경](../../interaction/using/live-design-environments.md#creating-an-offer-environment)만들기를 참조하십시오.

### 기간 {#period}

이 기간은 제안 프레젠테이션 날짜에 시작되는 슬라이딩 기간입니다. 오퍼 제안의 유효성에 대한 시간 제한을 설정합니다. 이 기간 이후에 이루어진 제안 제안에는 이 규칙이 적용되지 않습니다.

기간은 제안 날짜 **전** **일** 후 **n일 후에** 시작되며, 여기서 **[!UICONTROL Period considered]** n은필드에 입력된 숫자에 해당합니다.

* 인바운드 공간의 경우 제안 날짜는 오퍼 프레젠테이션 날짜입니다.
* 아웃바운드 공간의 경우 제안 날짜는 배달 연락처 날짜입니다(예: 타깃팅 워크플로우에 입력된 배달 날짜).

화살표를 사용하여 일 수를 변경하거나 마침표(&quot;2d 6h&quot;와 같이)를 직접 입력합니다.

![](assets/offer_typology_010.png)

### 제안 수 {#number-of-propositions}

해당 오퍼가 제외되거나 제외되기 전에 수행할 수 있는 최대 개수의 제안을 설정할 수 있습니다.

화살표를 사용하여 오퍼 제안 수를 변경합니다.

![](assets/offer_typology_011.png)

## 프로필 및 수신자 정의 {#defining-propositions-and-recipients}

이 **[!UICONTROL Propositions to count]** **[!UICONTROL General]** 섹션에서는 제안 내역에 특정 횟수가 표시되는 경우 탭에 정의된 오퍼를 제외시킬 수신자와 제안을 모두 지정할 수 있습니다.

### 프로필 필터링 {#filtering-propositions}

필터링 기준을 선택하여 채널, 관련 오퍼 또는 이전에 할당된 속성의 상태를 기준으로 제안을 제외할 수 있습니다.

![](assets/offer_typology_014.png)

이러한 기준은 프레젠테이션 규칙의 가장 빈번한 응용 프로그램을 나타냅니다. 다른 기준을 사용하려면 **[!UICONTROL Limit propositions...]** 링크를 사용하여 쿼리를 만들 수 있습니다. 자세한 내용은 제안 관련 [쿼리 만들기 섹션을](#creating-a-query-on-propositions) 참조하십시오.

* **채널에서 필터링**

   **[!UICONTROL On the same channel only]** :을 사용하면 **[!UICONTROL General]** 탭에 지정된 채널에서 오퍼 제안을 제외할 수 있습니다.

   예를 들어, **[!UICONTROL General]** 탭에서 규칙에 지정된 채널은 이메일입니다. 규칙이 적용되는 오퍼가 지금까지 웹 채널에서만 제공된 경우 상호 작용 엔진은 오퍼를 이메일 배달로 제공할 수 있습니다. 그러나 오퍼가 이메일로 표시되면 상호 작용 엔진은 오퍼를 표시할 다른 채널을 선택합니다.

   >[!NOTE]
   >
   >우리는 공간이 아니라 채널에 대해 이야기하고 있습니다. 규칙이 웹 채널에서 오퍼를 제외해야 하는 경우, 두 개의 공백(예: 배너와 페이지 본문)으로 웹 사이트에 제시될 오퍼가 이전에 이미 제공된 경우 사이트에 표시되지 않습니다.
   >
   >오퍼 프레젠테이션과 관련된 워크플로우의 경우, 규칙이 **[!UICONTROL All channels]**

* **오퍼 필터링**

   이 필터를 사용하면 특정 오퍼 세트로 카운트되도록 오퍼 제안을 제한할 수 있습니다.

   **[!UICONTROL All offers]** :기본값. 오퍼에 필터가 적용되지 않습니다.

   **[!UICONTROL Offer being presented]** :탭에 지정된 오퍼는 이미 제공된 경우 **[!UICONTROL General]** 제외됩니다.

   **[!UICONTROL Offers from the same category]** :오퍼는 동일한 카테고리의 오퍼가 이미 제공된 경우 제외됩니다.

   **[!UICONTROL The offers which the rule applies to]** :여러 오퍼가 **[!UICONTROL General]** 탭에 정의되면 이 오퍼 세트의 각 오퍼 제안이 고려되고 제안 임계값에 도달하는 경우 모든 오퍼의 제외로 끝납니다.

   예를 들어, 오퍼는 **[!UICONTROL General]** 탭에 정의됩니다. 최대 제안 수는 2로 설정됩니다. 2와 5개의 오퍼가 각각 한 번 제공되면, 계산되는 제안의 수는 2개가 됩니다. 결과적으로, 오퍼 3은 제공되지 않습니다.

* **제안 상태 필터링**

   이 필터를 사용하면 제안 내역에 고려될 오퍼 제안에 대해 가장 빈번한 상태를 선택할 수 있습니다.

   **[!UICONTROL Regardless of the proposition status]** :기본값. 제안 상태에 필터가 적용되지 않습니다.

   **[!UICONTROL Accepted or rejected propositions]** :수락되거나 거부된 이전에 제공된 오퍼를 제외시킬 수 있습니다.

   **[!UICONTROL Accepted propositions]** :수락된 이전에 제공된 오퍼를 제외시킬 수 있습니다.

   **[!UICONTROL Rejected propositions]** :거부되었던 이전에 제공된 오퍼를 제외시킬 수 있습니다.

### 수신자 정의 {#defining-recipients}

수신자를 지정하려면 링크를 클릭하고 규칙에서 관련된 수신자를 선택합니다. **[!UICONTROL Edit the query from the targeting dimension...]**

![](assets/offer_typology_012.png)

### 제안 관련 쿼리 만들기 {#creating-a-query-on-propositions}

쿼리를 통해 카운트할 제안을 지정하려면 **[!UICONTROL Limit propositions...]** 링크를 클릭하고 고려할 기준을 지정합니다.

다음 예제에서는 두 개의 프레젠테이션 후에 카운트될 **제안이** 콜 센터 **공간의 특별 오퍼** 카테고리에 있는 **20**&#x200B;미만가중치입니다.

![](assets/offer_typology_013.png)

