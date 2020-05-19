---
title: 데이터 농축
seo-title: 데이터 농축
description: 데이터 농축
seo-description: null
page-status-flag: never-activated
uuid: 3f65a8a2-b3e1-4c4c-9653-b8a7c4d7557a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: f87da08f-68b9-4e2b-821f-b3ff20e390f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1aca6758bc787f91ae28d7d5add875edf04541e8
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 0%

---


# 데이터 농축{#enriching-data}

## 데이터 농축에 대한 정보 {#about-enriching-data}

이 사용 사례 세부 사항은 타깃팅 워크플로우에서 **[!UICONTROL Enrichment]** 활동을 사용할 수 있습니다. 활동 사용에 대한 자세한 내용은 **[!UICONTROL Enrichment]** 다음을 참조하십시오. [농축](../../workflow/using/enrichment.md).

사용자 지정 날짜를 사용하여 이메일 배달을 향상시키는 방법에 대한 사용 사례도 [이 섹션에 나와 있습니다](../../workflow/using/email-enrichment-with-custom-date-fields.md).

마케팅 데이터베이스의 연락처는 웹 애플리케이션을 통해 경쟁업체에 참가하라는 초대장을 보냅니다. 대회 결과는 **[!UICONTROL Competition results]** 테이블에서 회수되었다. 이 표는 연락처 테이블(**[!UICONTROL Recipients]**)에 연결되어 있습니다. 테이블에는 **[!UICONTROL Competition results]** 다음 필드가 포함되어 있습니다.

* 대회 이름(@game)
* 시험버전 번호(@trial)
* 점수(@score)

![](assets/uc1_enrich_1.png)

테이블에서 찾은 연락처 **[!UICONTROL Recipients]** 는 테이블의 여러 행에 연결할 수 **[!UICONTROL Competition results]** 있습니다. 이 두 테이블 간의 관계는 1n형 형식입니다. 수신자에 대한 결과 로그의 예는 다음과 같습니다.

![](assets/uc1_enrich_2.png)

이 기능의 목적은 최고 점수에 따라 최신 경쟁업체에 참여하는 사람에게 개인화된 배송 서비스를 제공하기 위한 것입니다. 점수가 가장 높은 사람은 1등, 점수가 가장 높은 사람은 1등, 점수가 높은 사람은 4등 모두 &#39;쪽지&#39;를 말한다.

이 사용 사례를 설정하기 위해 다음 타깃팅 워크플로우를 만들었습니다.

![](assets/uc1_enrich_3.png)

워크플로우를 만들려면 다음 단계를 적용합니다.

1. 두 **[!UICONTROL Query]** 가지 활동 및 한 가지 **[!UICONTROL Intersection]** 활동이 마지막 경쟁업체에 가입한 신규 가입자를 대상으로 추가됩니다.
1. 이 **[!UICONTROL Enrichment]** 활동을 통해 표에 저장된 데이터를 추가할 수 **[!UICONTROL Competition results]** 있습니다. Adobe **[!UICONTROL Score]** 의 전달 개인화가 발생하는 필드가 워크플로우의 작업 표에 추가됩니다.
1. 이 **[!UICONTROL Split]** 유형 활동을 통해 점수를 기준으로 수신자 하위 세트를 만들 수 있습니다.
1. 각 하위 세트에 대해 유형 활동이 **[!UICONTROL Delivery]** 추가됩니다.

## 1단계: 타깃팅 {#step-1--targeting}

첫 번째 쿼리를 통해 지난 6개월 동안 데이터베이스에 추가된 수신자를 타깃팅할 수 있습니다.

![](assets/uc1_enrich_4.png)

두 번째 질문은 마지막 경쟁업체에 참가한 수신자를 타게팅할 수 있도록 합니다.

![](assets/uc1_enrich_5.png)

그런 다음 지난 6개월 이내에 데이터베이스에 추가된 수신자와 마지막 경쟁업체에 가입한 수신자를 타게팅하기 위해 유형 활동이 추가됩니다. **[!UICONTROL Intersection]**

## 2단계: 농축 {#step-2--enrichment}

이 예에서는 테이블에 저장된 필드에 따라 배달 **[!UICONTROL Score]** 을 개인화하고자 **[!UICONTROL Competition results]** 합니다. 이 표는 받는 사람 테이블과의 1n형 관계입니다. 이 **[!UICONTROL Enrichment]** 활동을 통해 필터링 차원에 연결된 테이블의 데이터를 워크플로의 작업 테이블에 추가할 수 있습니다.

1. 농축활동 편집 화면에서 선택한 다음 **[!UICONTROL Add data]**&#x200B;을 **[!UICONTROL Data linked to the filtering dimension]** 클릭합니다 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_6.png)

1. 그런 다음 **[!UICONTROL Data linked to the filtering dimension]** 옵션을 선택하고 **[!UICONTROL Competition results]** 표를 선택한 다음 을 클릭합니다 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_7.png)

1. ID와 레이블을 입력하고 필드에서 **[!UICONTROL Limit the line count]** 옵션을 **[!UICONTROL Data collected]** 선택합니다. 필드에서 **[!UICONTROL Lines to retrieve]** &#39;1&#39;을 값으로 선택합니다. 각 수신자의 경우 데이터 연계 강화 활동은 워크플로우의 작업 테이블에 **[!UICONTROL Competition results]** 한 줄을 추가합니다. 클릭 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_8.png)

1. 이 예에서는 마지막 경쟁업체에서만 받는 사람의 최고 점수를 복구하려고 합니다. 이렇게 하려면 필드에 필터를 추가하여 이전 대회와 관련된 모든 줄을 **[!UICONTROL Competition name]** 제외합니다. 클릭 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_9.png)

1. 화면으로 **[!UICONTROL Sort]** 이동하고 **[!UICONTROL Add]** 단추를 클릭하고 **[!UICONTROL Score]** 필드를 선택한 다음 열의 상자를 **[!UICONTROL descending]** 선택하여 필드 항목을 내림차순으로 **[!UICONTROL Score]** 정렬합니다. 받는 사람마다, 우라늄 농축은 마지막 게임의 최고 점수와 일치하는 라인을 추가합니다. 클릭 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_10.png)

1. 창에서 **[!UICONTROL Data to add]** 필드 **[!UICONTROL Score]** 를 두 번 클릭합니다. 각 수신자의 경우, 우라늄 농축은 **[!UICONTROL Score]** 필드만 추가합니다. 클릭 **[!UICONTROL Finish]**.

   ![](assets/uc1_enrich_11.png)

농축활동의 인바운드 전환을 마우스 오른쪽 단추로 클릭하고 선택합니다 **[!UICONTROL Display the target]**. 작업 테이블에는 다음 데이터가 포함되어 있습니다.

![](assets/uc1_enrich_13.png)

연결된 스키마:

![](assets/uc1_enrich_15.png)

농축활동의 아웃바운드 전환으로 이 작업을 갱신합니다. 받는 사람 점수에 연결된 데이터가 추가되었음을 확인할 수 있습니다. 각 수신자의 최고 점수가 복구되었습니다.

![](assets/uc1_enrich_12.png)

일치하는 스키마도 향상되었습니다.

![](assets/uc1_enrich_14.png)

## 3단계: 분할 및 전달 {#step-3--split-and-delivery}

점수를 기준으로 받는 사람을 정렬하기 위해, 농축된 후에 **[!UICONTROL Split]** 활동이 추가됩니다.

![](assets/uc1_enrich_18.png)

1. 첫 번째(**우승자**) 하위 세트가 점수가 가장 높은 받는 사람을 포함하도록 정의되었습니다. 이렇게 하려면 레코드 수의 제한을 정의하고, 점수에 내림차순 정렬을 적용하고, 레코드 수를 1로 제한합니다.

   ![](assets/uc1_enrich_16.png)

1. 두 번째(**두 번째**&#x200B;자리) 하위 집합에는 두 번째 높은 점수가 있는 받는 사람이 포함됩니다. 구성은 첫 번째 하위 세트에 대해 동일합니다.

   ![](assets/uc1_enrich_17.png)

1. 세 번째(**패자**) 하위 집합에는 다른 모든 받는 사람이 포함됩니다. 두 개의 최고 점수를 **[!UICONTROL General]** 달성하지 못한 모든 수신자를 타게팅하려면 탭으로 **[!UICONTROL Generate complement]** 가서 확인란을 선택합니다.

   ![](assets/uc1_enrich_19.png)

1. 각 하위 세트에 대해 다른 배달 템플릿을 사용하여 각 하위 세트에 대한 유형 활동을 추가합니다. **[!UICONTROL Delivery]**

   ![](assets/uc1_enrich_20.png)

