---
product: campaign
title: 프레젠테이션 규칙
description: 프레젠테이션 규칙
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: f9dd9ad6-48da-4a80-9405-109a433a1ed5
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 1%

---

# 프레젠테이션 규칙{#presentation-rules}



## 프레젠테이션 규칙 만들기 {#creating-a-presentation-rule}

저희 데이터베이스에 유럽, 아프리카, 미국, 캐나다에 대한 몇 가지 여행 제안이 있습니다. 캐나다 여행에 대한 오퍼를 보내고 싶지만, 수신자가 이 유형의 오퍼를 거부하는 경우 다시 보내고 싶지 않습니다

캐나다 여행은 수신자 당 한 번만 제공되고 거부되면 다시 제공되지 않도록 규칙을 구성할 예정입니다.

1. Adobe Campaign 트리에서 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** 노드.
1. 새로 만들기 **[!UICONTROL Offer presentation]** 규칙을 입력합니다.

   ![](assets/offer_typology_example_001.png)

1. 필요한 경우 레이블 및 설명을 변경합니다.

   ![](assets/offer_typology_example_002.png)

1. 다음을 선택합니다. **[!UICONTROL All channels]** 모든 채널로 규칙을 확장하는 옵션입니다.

   ![](assets/offer_typology_example_003.png)

1. 다음을 클릭합니다. **[!UICONTROL Edit expression]** 링크 및 선택 **[!UICONTROL Category]** 노드를 표현식으로 사용하십시오.

   ![](assets/offer_typology_example_004.png)

1. 캐나다의 여행 오퍼와 일치하는 카테고리를 선택하고 **[!UICONTROL OK]** 을 눌러 쿼리 창을 닫습니다.

   ![](assets/offer_typology_example_005.png)

1. 다음에서 **[!UICONTROL Offer presentation]** 탭에서 환경에 구성된 차원과 동일한 차원을 선택합니다.

   ![](assets/offer_typology_example_006.png)

1. 규칙을 적용할 기간을 지정합니다.

   ![](assets/offer_typology_example_007.png)

1. 이미 캐나다 여행을 거부한 수신자가 유사한 다른 오퍼를 받지 않도록 제안을 1개로 제한합니다.

   ![](assets/offer_typology_example_008.png)

1. 다음 항목 선택 **[!UICONTROL Offers for the same category]** 에서 모든 오퍼를 제외하도록 필터링 **캐나다** 범주.

   ![](assets/offer_typology_example_020.png)

1. 다음 항목 선택 **[!UICONTROL Rejected propositions]** 수신자가 거부한 제안만 고려하도록 필터링합니다.

   ![](assets/offer_typology_example_021.png)

1. 이 규칙을 적용할 수신자를 선택합니다.

   이 예제에서는 **빈번한 여행자** 수신자.

   ![](assets/offer_typology_example_009.png)

1. 오퍼 유형화에서 규칙을 참조합니다.

   ![](assets/offer_typology_example_013.png)

1. 오퍼 환경으로 이동, (**환경 - 수신자** 이 경우)에서 드롭다운 목록을 사용하여 방금 만든 새 유형화를 참조하십시오. **[!UICONTROL Eligibility]** 탭.

   ![](assets/offer_typology_example_014.png)

## 프레젠테이션 규칙 적용 {#applying-the-presentation-rule}

다음은 이전에 만든 유형화 규칙의 적용 예입니다.

우리는 캐나다 카테고리에 속하는 첫 번째 오퍼 제안을 보내려고 합니다. 수신자가 오퍼를 한 번 거부하면 다시 오퍼가 제공되지 않습니다.

1. 다음에서 **빈번한 여행자** 수신자 폴더, 프로필 중 하나를 선택하여 해당 오퍼를 확인합니다. 다음 중 하나를 클릭합니다. **[!UICONTROL Propositions]** 탭을 클릭한 다음 **[!UICONTROL Preview]** 탭.

   이 예제에서는 **팀 램지** 의 일부인 오퍼에 적격입니다. **아메리카** 범주.

   ![](assets/offer_typology_example_015.png)

1. 을(를) 타겟팅할 이메일 게재를 만드는 것부터 시작하십시오. **빈번한 여행자** 오퍼가 있는 수신자.
1. 오퍼 엔진 호출 매개 변수를 선택합니다.

   이 예에서는 **미국 여행** 선택한 카테고리에 다음이 포함됩니다. **캐나다** 및 **미국** 하위 범주.

   ![](assets/offer_typology_example_016.png)

1. 메시지 본문에 오퍼를 삽입하고 게재를 보냅니다. 자세한 내용은 다음을 참조하십시오. [아웃바운드 채널 기본 정보](../../interaction/using/about-outbound-channels.md).

   수신자가 적격한 오퍼를 수신했습니다.

1. 수용자는 제안 기록에 나타난 바와 같이 캐나다 제안을 거부하였다.

   ![](assets/offer_typology_example_018.png)

1. 이제 적격한 오퍼를 확인합니다.

   캐나다에 대한 오퍼가 선택되지 않았음을 알 수 있습니다.

   ![](assets/offer_typology_example_019.png)
