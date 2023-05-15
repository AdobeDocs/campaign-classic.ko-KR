---
product: campaign
title: 데이터 강화
description: 데이터 보강 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Enrichment Activity
exl-id: ab786cf1-74a4-4185-a63d-84e776a2f776
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 1%

---

# 데이터 강화{#enriching-data}



## 데이터 강화 정보 {#about-enriching-data}

이 사용 사례 세부 사항에서는 **[!UICONTROL Enrichment]** 활동 을 만들 수 있습니다. 사용 방법에 대한 자세한 내용 **[!UICONTROL Enrichment]** 활동, 다음을 참조하십시오. [데이터 보강](enrichment.md).

사용자 지정 날짜로 이메일 게재를 보강하는 방법에 대한 사용 사례도 다음 위치에서 사용할 수 있습니다. [이 섹션](email-enrichment-with-custom-date-fields.md).

마케팅 데이터베이스에 있는 연락처는 웹 애플리케이션을 통해 대회에 참가하도록 초대장을 보냅니다. 그 대회의 결과는 **[!UICONTROL Competition results]** 테이블. 이 테이블은 연락처 테이블(**[!UICONTROL Recipients]**). 다음 **[!UICONTROL Competition results]** 표에는 다음 필드가 포함되어 있습니다.

* 경쟁 이름(@game)
* 체험판 번호(@trial)
* 점수(@score)

![](assets/uc1_enrich_1.png)

에 있는 연락처 **[!UICONTROL Recipients]** 표는 **[!UICONTROL Competition results]** 테이블. 이 두 테이블 간의 관계는 1-n 형식입니다. 다음은 수신자에 대한 결과 로그의 예입니다.

![](assets/uc1_enrich_2.png)

이 사용 사례의 목적은 가장 높은 점수를 기준으로 최신 경쟁에 참여한 사람에게 개인화된 게재를 전송하는 것입니다. 점수가 가장 높은 사람은 1등. 점수가 가장 높은 사람은 위로상을, 점수가 높은 사람은 그 다음 차례가 되면 &#39;더 행운을 빈다&#39;메시지를 받는다.

이 사용 사례를 설정하기 위해 다음 타겟팅 워크플로우를 만들었습니다.

![](assets/uc1_enrich_3.png)

워크플로우를 만들려면 다음 단계를 적용합니다.

1. 2 **[!UICONTROL Query]** 활동 및 하나 **[!UICONTROL Intersection]** 이 활동은 마지막 대회에 참가한 신규 구독자를 타겟으로 추가됩니다.
1. 다음 **[!UICONTROL Enrichment]** 활동을 통해 **[!UICONTROL Competition results]** 테이블. 다음 **[!UICONTROL Score]** 게재 개인화가 발생할 필드가 워크플로우의 작업 테이블에 추가됩니다.
1. 다음 **[!UICONTROL Split]** 유형 활동을 통해 점수를 기반으로 수신자 하위 세트를 만들 수 있습니다.
1. 각 하위 세트에 대해 **[!UICONTROL Delivery]** 유형 활동이 추가됩니다.

## 1단계: 타깃팅 {#step-1--targeting}

첫 번째 쿼리를 사용하면 지난 6개월 내에 데이터베이스에 추가된 수신자를 타겟팅할 수 있습니다.

![](assets/uc1_enrich_4.png)

두 번째 쿼리는 마지막 경쟁에 참가한 수신자를 타겟팅할 수 있도록 합니다.

![](assets/uc1_enrich_5.png)

An **[!UICONTROL Intersection]** 그런 다음 유형 활동이 추가되어 지난 6개월 내에 데이터베이스에 추가된 수신자와 마지막 경쟁사에 참가한 사용자를 타겟팅합니다.

## 2단계: 데이터 보강 {#step-2--enrichment}

이 예에서는 **[!UICONTROL Score]** 에 저장된 필드 **[!UICONTROL Competition results]** 테이블. 이 테이블에는 수신자 테이블과 1n 유형의 관계가 있습니다. 다음 **[!UICONTROL Enrichment]** 활동을 사용하면 필터링 차원에 연결된 테이블의 데이터를 워크플로우의 작업 테이블에 추가할 수 있습니다.

1. 데이터 보강 활동의 편집 화면에서 **[!UICONTROL Add data]**, 그런 다음 **[!UICONTROL Data linked to the filtering dimension]** 을(를) 클릭합니다. **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_6.png)

1. 그런 다음 **[!UICONTROL Data linked to the filtering dimension]** 옵션을 선택하고 **[!UICONTROL Competition results]** 표를 클릭하고 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_7.png)

1. ID와 레이블을 입력하고 **[!UICONTROL Limit the line count]** 옵션 **[!UICONTROL Data collected]** 필드. 에서 **[!UICONTROL Lines to retrieve]** 필드에서 &#39;1&#39;을 값으로 선택합니다. 각 수신자에 대해 데이터 보강 활동에서는 **[!UICONTROL Competition results]** 표의 맨 위에 워크플로우 작업 표를 추가합니다. **[!UICONTROL Next]**&#x200B;를 클릭합니다.

   ![](assets/uc1_enrich_8.png)

1. 이 예에서는 수신자의 가장 높은 점수를 복구하려고 하지만 마지막 경쟁에서만 복구하려고 합니다. 이렇게 하려면 필터를 **[!UICONTROL Competition name]** 이전 대회와 관련된 모든 줄을 제외하는 필드입니다. **[!UICONTROL Next]**&#x200B;를 클릭합니다.

   ![](assets/uc1_enrich_9.png)

1. 로 이동합니다. **[!UICONTROL Sort]** 화면에서 을 클릭하고 **[!UICONTROL Add]** 버튼을 클릭하고 **[!UICONTROL Score]** 필드를 입력하고 **[!UICONTROL descending]** 열을 사용하여 **[!UICONTROL Score]** 필드를 내림차순으로 표시합니다. 각 수신자에 대해 데이터 보강 활동은 마지막 게임에서 가장 높은 점수를 매기는 줄을 추가합니다. **[!UICONTROL Next]**&#x200B;를 클릭합니다.

   ![](assets/uc1_enrich_10.png)

1. 에서 **[!UICONTROL Data to add]** 창을 두 번 클릭합니다 **[!UICONTROL Score]** 필드. 각 수신자에 대해 데이터 보강 활동에는 **[!UICONTROL Score]** 필드. **[!UICONTROL Finish]**&#x200B;를 클릭합니다.

   ![](assets/uc1_enrich_11.png)

데이터 보강 활동의 인바운드 전환을 마우스 오른쪽 단추로 클릭하고 을(를) 선택합니다 **[!UICONTROL Display the target]**. 작업 표에는 다음 데이터가 포함되어 있습니다.

![](assets/uc1_enrich_13.png)

연결된 스키마는 다음과 같습니다.

![](assets/uc1_enrich_15.png)

데이터 보강 활동의 아웃바운드 전환에서 이 작업을 갱신합니다. 수신자 점수에 연결된 데이터가 추가되었음을 알 수 있습니다. 각 수신자의 가장 높은 점수를 복구했습니다.

![](assets/uc1_enrich_12.png)

일치하는 스키마도 보강되었습니다.

![](assets/uc1_enrich_14.png)

## 3단계: 분할 및 전달 {#step-3--split-and-delivery}

점수를 기준으로 수신자를 정렬하려면 **[!UICONTROL Split]** 활동은 보강 후에 추가됩니다.

![](assets/uc1_enrich_18.png)

1. 첫 번째 (**승자**) 하위 세트가 점수가 가장 높은 수신자를 포함하도록 정의되어 있습니다. 이렇게 하려면 레코드 수의 제한을 정의하고, 점수에 내림차순 정렬을 적용하고 레코드 수를 1로 제한합니다.

   ![](assets/uc1_enrich_16.png)

1. 두 번째 (**2위**) 하위 집합에는 두 번째로 높은 점수가 있는 수신자가 포함됩니다. 구성은 첫 번째 하위 세트에 대해 와 동일합니다.

   ![](assets/uc1_enrich_17.png)

1. 세 번째(**패자**) 하위 집합에는 다른 모든 수신자가 포함됩니다. 로 이동합니다. **[!UICONTROL General]** 탭을 선택하고 다음을 확인합니다 **[!UICONTROL Generate complement]** 상자 를 추가하여 두 개의 가장 높은 점수를 달성하지 못한 모든 수신자를 타겟팅합니다.

   ![](assets/uc1_enrich_19.png)

1. 추가 **[!UICONTROL Delivery]** 각 하위 세트에 대해 다른 게재 템플릿을 사용하여 활동을 입력합니다.

   ![](assets/uc1_enrich_20.png)
