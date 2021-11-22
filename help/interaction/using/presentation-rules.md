---
product: campaign
title: 프레젠테이션 규칙
description: 프레젠테이션 규칙
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: f9dd9ad6-48da-4a80-9405-109a433a1ed5
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 1%

---

# 프레젠테이션 규칙{#presentation-rules}

![](../../assets/v7-only.svg)

## 프레젠테이션 규칙 만들기 {#creating-a-presentation-rule}

저희 데이터베이스에는 유럽, 아프리카, 미국, 캐나다를 위한 몇 가지 여행상품이 있습니다. 캐나다로 여행을 위한 오퍼를 보내려고 하는데, 수신자가 이러한 유형의 오퍼를 거부하면 다시 보내지 않습니다

캐나다로의 여행은 수신자당 한 번만 제공되도록 규칙을 구성하려고 하며, 거부된 경우 다시 제공되지 않습니다.

1. Adobe Campaign 트리에서 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** 노드 아래에 있어야 합니다.
1. 새 만들기 **[!UICONTROL Offer presentation]** 유형 규칙입니다.

   ![](assets/offer_typology_example_001.png)

1. 필요한 경우 레이블과 설명을 변경합니다.

   ![](assets/offer_typology_example_002.png)

1. 을(를) 선택합니다 **[!UICONTROL All channels]** 규칙을 모든 채널로 확장하는 옵션입니다.

   ![](assets/offer_typology_example_003.png)

1. 을(를) 클릭합니다. **[!UICONTROL Edit expression]** 링크 및 선택 **[!UICONTROL Category]** 노드를 표현식으로 사용합니다.

   ![](assets/offer_typology_example_004.png)

1. 캐나다에 대한 여행 오퍼와 일치하는 카테고리를 선택하고 을 클릭합니다 **[!UICONTROL OK]** 을 눌러 쿼리 창을 닫습니다.

   ![](assets/offer_typology_example_005.png)

1. 에서 **[!UICONTROL Offer presentation]** 탭에서 환경에 구성된 차원과 동일한 차원을 선택합니다.

   ![](assets/offer_typology_example_006.png)

1. 규칙을 적용할 기간을 지정합니다.

   ![](assets/offer_typology_example_007.png)

1. 캐나다 여행을 이미 거부한 수신자가 다른 유사한 오퍼를 받지 않도록 제안을 하나로 제한합니다.

   ![](assets/offer_typology_example_008.png)

1. 을(를) 선택합니다 **[!UICONTROL Offers for the same category]** 에서 모든 오퍼를 제외하도록 필터링 **캐나다** 카테고리.

   ![](assets/offer_typology_example_020.png)

1. 을(를) 선택합니다 **[!UICONTROL Rejected propositions]** 수신자가 거부한 프로필만 고려하도록 필터링합니다.

   ![](assets/offer_typology_example_021.png)

1. 이 규칙을 적용할 수신자를 선택합니다.

   이 예제에서는 **빈번한 여행자들** 수신자.

   ![](assets/offer_typology_example_009.png)

1. 오퍼 유형화에서 규칙을 참조합니다.

   ![](assets/offer_typology_example_013.png)

1. 오퍼 환경으로 이동(**환경 - 수신자** 의 드롭다운 목록을 사용하여 방금 만든 새 유형화를 및에 참조합니다. **[!UICONTROL Eligibility]** 탭.

   ![](assets/offer_typology_example_014.png)

## 프레젠테이션 규칙 적용 {#applying-the-presentation-rule}

다음은 이전에 만든 유형화 규칙의 애플리케이션 예입니다.

캐나다 카테고리에 속하는 첫 번째 제안 제안을 보내려고 합니다. 수신자가 오퍼를 한 번 거부하면 다시 제공하지 않습니다.

1. 에서 **빈번한 여행자들** 수신자 폴더에서 프로필 중 하나를 선택하여 자격이 있는 오퍼를 확인합니다. 를 클릭합니다. **[!UICONTROL Propositions]** 탭을 클릭한 다음 **[!UICONTROL Preview]** 탭.

   이 예제에서는 **팀 램지** 은 **아메리카** 카테고리.

   ![](assets/offer_typology_example_015.png)

1. 먼저 을(를) 타겟팅하는 이메일 게재를 만듭니다 **빈번한 여행자들** 오퍼가 있는 수신자.
1. 오퍼 엔진 호출 업 매개 변수를 선택합니다.

   이 예제에서는 **미국의 여행** 카테고리가 선택되며, 여기에는 이 카테고리가 포함됩니다 **캐나다** 및 **미국** 하위 카테고리.

   ![](assets/offer_typology_example_016.png)

1. 메시지 본문에 오퍼를 삽입하고 게재를 보냅니다. 자세한 내용은 [아웃바운드 채널 기본 정보](../../interaction/using/about-outbound-channels.md).

   수신자가 자격이 되는 오퍼를 수신했습니다.

1. 제안 내역에 표시된 대로 수신자는 캐나다 오퍼를 거부했습니다.

   ![](assets/offer_typology_example_018.png)

1. 이제 자격이 되는 오퍼를 확인합니다.

   캐나다에 대한 오퍼가 선택되지 않은 것을 볼 수 있습니다.

   ![](assets/offer_typology_example_019.png)

**관련 항목**

* [여러 채널에서 오퍼를 관리하고 중복성을 제어합니다](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Manageoffersandcontrolredundancyacrosschannels)
