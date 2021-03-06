---
product: campaign
title: 오퍼 프레젠테이션 관리
description: 오퍼 프레젠테이션 관리
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: 6158ffaa-cb08-4f77-82b8-b3e5e1bf7fd7
source-git-commit: d835da6c7b55d9bf70b6b5dc58880718e12211d5
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 0%

---

# 오퍼 프레젠테이션 관리{#managing-offer-presentation}

![](../../assets/common.svg)

## 프레젠테이션 규칙 개요 {#presentation-rules-overview}

상호 작용을 통해 프레젠테이션 규칙을 사용하여 오퍼 proposition의 흐름을 제어할 수 있습니다. 상호 작용에 고유한 이러한 규칙은 유형화 규칙입니다. 수신자에게 이미 수행된 proposition 내역을 기반으로 오퍼를 제외할 수 있습니다. 환경에서 참조됩니다

## 오퍼 프레젠테이션 규칙 만들기 및 참조 {#creating-and-referencing-an-offer-presentation-rule}

1. 로 이동합니다. **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** 노드 아래에 있어야 합니다.
1. 유형화 규칙을 만들고 **[!UICONTROL Offer presentation]** 유형.

   ![](assets/offer_typology_001.png)

1. 규칙을 적용할 채널을 지정합니다.

   ![](assets/offer_typology_002.png)

1. 규칙의 애플리케이션 기준을 구성합니다. 자세한 내용은 [프레젠테이션 규칙 설정](#presentation-rule-settings).
1. 로 이동합니다. **[!UICONTROL Administration]** > **[!UICONTROL Campaign execution]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typologies]** 노드 및 모두를 그룹화하는 유형화 만들기 **[!UICONTROL Offer presentation]** 유형 규칙.

   ![](assets/offer_typology_003.png)

1. 유형화가 만들어지면 유형화 규칙에 커서를 놓고 방금 생성한 유형화로 그룹화합니다.

   ![](assets/offer_typology_004.png)

1. 오퍼 환경에서 드롭다운 목록을 사용하여 유형화를 참조합니다.

   ![](assets/offer_typology_005.png)

## 프레젠테이션 규칙 설정 {#presentation-rule-settings}

### 애플리케이션 기준 {#application-criteria-}

에서 사용할 수 있는 애플리케이션 기준 **[!UICONTROL General]** 탭에서는 프레젠테이션 규칙이 적용될 오퍼를 지정할 수 있습니다. 이렇게 하려면 아래에 설명된 대로 쿼리를 만들고 관련 오퍼를 선택해야 합니다.

1. 유형화 규칙에서 **[!UICONTROL Edit the rule application conditions...]** 링크를 클릭하여 쿼리를 만듭니다.

   ![](assets/offer_typology_006.png)

1. 쿼리 창에서 유형화 규칙을 적용할 오퍼에 필터를 적용할 수 있습니다.

   예를 들어 오퍼 카테고리를 선택할 수 있습니다.

   ![](assets/offer_typology_008.png)

### 오퍼 차원 {#offer-dimensions}

에서 **[!UICONTROL Offer presentation]** 탭에서 프레젠테이션 규칙에 대해 환경에 구성된 치수와 동일한 치수를 지정해야 합니다.

다음 **[!UICONTROL Targeting dimension]** 수신자 테이블과 일치합니다(기본적으로 nms:recipients)에게 제공할 제안입니다. 다음 **[!UICONTROL Storage dimension]** 타겟팅 차원에 연결된 제안 내역이 포함된 표와 일치합니다(기본적으로:nms:propRcp).

![](assets/offer_typology_009.png)

>[!NOTE]
>
>비표준 테이블을 사용할 수도 있습니다. 특정 타겟팅 차원을 사용하려면 대상 매핑을 사용하여 테이블과 전용 환경을 만들어야 합니다. 자세한 내용은 [오퍼 환경 만들기](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

### 기간 {#period}

이 기간은 오퍼 프레젠테이션 날짜에 시작되는 슬라이딩 기간입니다. 오퍼 제안 유효성에 대한 시간 제한을 설정합니다. 이 기간 이후에는 제안을 제공해도 규칙이 적용되지 않습니다.

기간이 시작됩니다 **n** 제안 날짜 및 종료일 전 일 수 **n** 그 다음 날 **n** 는 **[!UICONTROL Period considered]** 필드:

* 인바운드 공간의 경우 제안 날짜는 오퍼 프레젠테이션 날짜입니다.
* 아웃바운드 공간의 경우 제안 날짜는 게재 연락 날짜(예: 타겟팅 워크플로우에 입력한 게재 날짜)입니다.

화살표를 사용하여 일 수를 변경하거나 기간(예: &quot;2d6h&quot;)을 직접 입력합니다.

![](assets/offer_typology_010.png)

### 제안 수 {#number-of-propositions}

관련 오퍼가 제외되기 전에 수행할 수 있는 최대 제안 수를 설정할 수 있습니다.

오퍼 제안 수를 변경하려면 화살표를 사용합니다.

![](assets/offer_typology_011.png)

## 프로필 및 수신자 정의 {#defining-propositions-and-recipients}

다음 **[!UICONTROL Propositions to count]** 섹션에 정의된 오퍼를 제외시킬 수신자와 제안을 모두 지정할 수 있습니다 **[!UICONTROL General]** Tab 키를 누릅니다.

### 프로필 필터링 {#filtering-propositions}

필터링 기준을 선택하여 채널, 관련 오퍼 또는 이전에 지정된 proposition의 상태에 따라 제안을 제외할 수 있습니다.

![](assets/offer_typology_014.png)

이러한 기준은 프레젠테이션 규칙의 가장 빈번한 적용을 나타냅니다. 다른 기준을 사용하려면 **[!UICONTROL Limit propositions...]** 링크를 클릭합니다. 자세한 내용은 [Proposition에 대한 쿼리 만들기](#creating-a-query-on-propositions) 섹션을 참조하십시오.

* **채널에서 필터링**

   **[!UICONTROL On the same channel only]** : 에서는 **[!UICONTROL General]** 탭.

   예를 들어, **[!UICONTROL General]** 탭은 이메일입니다. 규칙이 적용되는 오퍼가 지금까지 웹 채널에서만 제공된 경우 상호 작용 엔진은 오퍼를 이메일 게재에 제공할 수 있습니다. 그러나 오퍼가 이메일로 제공되면 상호 작용 엔진은 오퍼를 표시할 다른 채널을 선택합니다.

   >[!NOTE]
   >
   >우리는 공간이 아니라 채널에 대해 이야기하고 있습니다. 규칙이 웹 채널에서 오퍼를 제외해야 하는 경우, 두 개의 공백(예: 배너와 페이지 본문)으로 웹 사이트에 제공하도록 지정된 오퍼가 이전에 이미 제공된 경우에는 사이트에 표시되지 않습니다.
   >
   >오퍼 프레젠테이션을 포함하는 워크플로우의 경우, 규칙이 **[!UICONTROL All channels]**.

* **오퍼에 대해 필터링**

   이 필터를 사용하면 특정 오퍼 세트로 카운트할 오퍼 위치를 제한할 수 있습니다.

   **[!UICONTROL All offers]** : 기본값. 오퍼에 필터가 적용되지 않습니다.

   **[!UICONTROL Offer being presented]** : 에 지정된 오퍼 **[!UICONTROL General]** 탭이 이미 표시된 경우 제외됩니다.

   **[!UICONTROL Offers from the same category]** : 동일한 카테고리의 오퍼가 이미 제공된 경우 오퍼가 제외됩니다.

   **[!UICONTROL The offers which the rule applies to]** : 에서 여러 오퍼가 정의된 경우 **[!UICONTROL General]** 탭에서 이 오퍼 집합의 각 오퍼 제안을 고려하며, 제안 임계값에 도달하면 모든 오퍼의 제외에서 끝납니다.

   예를 들어, 오퍼 2, 3 및 5는 **[!UICONTROL General]** 탭. 최대 프로필 수는 2로 설정됩니다. 오퍼가 각각 2와 5개씩 표시되면 카운트되는 포지션의 수는 2개가 됩니다. 따라서, 오퍼 3은 제공되지 않습니다.

* **제안 상태 필터링**

   이 필터를 사용하면 제안 내역에서 고려할 오퍼 포지션의 가장 빈번한 상태를 선택할 수 있습니다.

   **[!UICONTROL Regardless of the proposition status]** : 기본값. 제안 상태에 필터가 적용되지 않습니다.

   **[!UICONTROL Accepted or rejected propositions]** : 수락되었거나 거부된 이전에 표시된 오퍼를 제외할 수 있습니다.

   **[!UICONTROL Accepted propositions]** : 수락된 이전에 제공한 오퍼를 제외할 수 있습니다.

   **[!UICONTROL Rejected propositions]** : 거부된 이전에 표시된 오퍼를 제외할 수 있습니다.

### 수신자 정의 {#defining-recipients}

수신자를 지정하려면 **[!UICONTROL Edit the query from the targeting dimension...]** 을 링크하고 규칙에 관련된 수신자를 선택합니다.

![](assets/offer_typology_012.png)

### Proposition에 대한 쿼리 만들기 {#creating-a-query-on-propositions}

쿼리를 통해 계산할 proposition을 지정하려면 **[!UICONTROL Limit propositions...]** 를 연결하고 고려할 기준을 지정합니다.

다음 예제에서는 두 개의 프레젠테이션 후에 계산되는 프로젝트가 **특별 오퍼** 카테고리, 대상 **콜 센터** 스페이스(무게 미만) **20년**.

![](assets/offer_typology_013.png)
