---
solution: Campaign Classic
product: campaign
title: 데이터 강화
description: 강화된 워크플로우 활동에 대한 자세한 내용
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 1%

---


# 데이터 강화{#enriching-data}

## 데이터 농축 정보 {#about-enriching-data}

이 사용 사례 세부 사항은 타깃팅 워크플로우에서 **[!UICONTROL Enrichment]** 활동을 사용할 수 있습니다. **[!UICONTROL Enrichment]** 활동 사용에 대한 자세한 내용은 다음을 참조하십시오.[데이터 연계 강화](../../workflow/using/enrichment.md).

사용자 지정 날짜를 사용하여 이메일 배달을 향상시키는 방법에 대한 사용 사례는 [이 섹션](../../workflow/using/email-enrichment-with-custom-date-fields.md)에서도 사용할 수 있습니다.

마케팅 데이터베이스의 연락처는 웹 애플리케이션을 통해 경쟁에 참여하도록 초대장을 보냅니다. 대회 결과는 **[!UICONTROL Competition results]** 표에서 복구됩니다. 이 테이블은 연락처 테이블(**[!UICONTROL Recipients]**)에 연결되어 있습니다. **[!UICONTROL Competition results]** 표에는 다음 필드가 포함되어 있습니다.

* 경쟁 이름(@game)
* 시험버전 번호(@trial)
* 점수(@score)

![](assets/uc1_enrich_1.png)

**[!UICONTROL Recipients]** 테이블에 있는 연락처를 **[!UICONTROL Competition results]** 테이블의 여러 줄에 연결할 수 있습니다. 이 두 테이블 간의 관계는 1n 유형입니다. 수신자에 대한 결과 로그의 예는 다음과 같습니다.

![](assets/uc1_enrich_2.png)

이 기능의 목적은 최고 점수에 따라 최신 경쟁업체에 참여한 고객에게 개인화된 배송 서비스를 제공하기 위한 것입니다. 점수가 가장 높은 사람은 1등, 점수가 두 번째 받는 사람은 위로상을, 나머지 사람은 다음번엔 더 행운을 기원하라는 메시지를 받는다.

이 사용 사례를 설정하기 위해 다음 타깃팅 워크플로우를 만들었습니다.

![](assets/uc1_enrich_3.png)

워크플로우를 만들려면 다음 단계를 적용합니다.

1. 2개의 **[!UICONTROL Query]** 활동 및 1개의 **[!UICONTROL Intersection]** 활동이 마지막 경쟁에 들어온 새 가입자를 대상으로 추가됩니다.
1. **[!UICONTROL Enrichment]** 활동을 통해 **[!UICONTROL Competition results]** 테이블에 저장된 데이터를 추가할 수 있습니다. 배달 개인화가 발생하는 **[!UICONTROL Score]** 필드가 워크플로우의 작업 표에 추가됩니다.
1. **[!UICONTROL Split]** 유형 활동을 통해 점수를 기준으로 수신자 하위 세트를 만들 수 있습니다.
1. 각 하위 세트에 대해 **[!UICONTROL Delivery]** 유형 활동이 추가됩니다.

## 1단계:{#step-1--targeting} 타깃팅

첫 번째 쿼리를 사용하면 지난 6개월 동안 데이터베이스에 추가된 받는 사람을 대상으로 할 수 있습니다.

![](assets/uc1_enrich_4.png)

두 번째 쿼리는 마지막 경쟁에 참가한 수신자를 대상으로 합니다.

![](assets/uc1_enrich_5.png)

그런 다음 지난 6개월 이내에 데이터베이스에 추가된 수신자와 마지막 경쟁업체에 가입한 수신자를 대상으로 **[!UICONTROL Intersection]** 유형 활동이 추가됩니다.

## 2단계:데이터 농축 {#step-2--enrichment}

이 예에서는 **[!UICONTROL Competition results]** 테이블에 저장된 **[!UICONTROL Score]** 필드에 따라 배달을 개인화하려고 합니다. 이 테이블은 받는 사람 테이블과 1n개의 유형 관계를 갖습니다. **[!UICONTROL Enrichment]** 활동을 통해 필터링 차원에 연결된 테이블의 데이터를 워크플로의 작업 테이블에 추가할 수 있습니다.

1. 농축활동 편집 화면에서 **[!UICONTROL Add data]**, **[!UICONTROL Data linked to the filtering dimension]**&#x200B;을 선택하고 **[!UICONTROL Next]**&#x200B;를 클릭합니다.

   ![](assets/uc1_enrich_6.png)

1. 그런 다음 **[!UICONTROL Data linked to the filtering dimension]** 옵션을 선택하고 **[!UICONTROL Competition results]** 테이블을 선택하고 **[!UICONTROL Next]**&#x200B;를 클릭합니다.

   ![](assets/uc1_enrich_7.png)

1. ID와 레이블을 입력하고 **[!UICONTROL Data collected]** 필드에서 **[!UICONTROL Limit the line count]** 옵션을 선택합니다. **[!UICONTROL Lines to retrieve]** 필드에서 &#39;1&#39;을 값으로 선택합니다. 각 수신자의 경우 데이터 연계 강화 작업은 워크플로우의 작업 테이블에 **[!UICONTROL Competition results]** 테이블의 한 줄을 추가합니다. **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/uc1_enrich_8.png)

1. 이 예에서는 받는 사람의 최고 점수를 회수하지만 마지막 경쟁에서만 회수하려고 합니다. 이렇게 하려면 **[!UICONTROL Competition name]** 필드에 필터를 추가하여 이전 대회와 관련된 모든 행을 제외합니다. **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/uc1_enrich_9.png)

1. **[!UICONTROL Sort]** 화면으로 이동하고 **[!UICONTROL Add]** 단추를 클릭하고 **[!UICONTROL Score]** 필드를 선택한 다음 **[!UICONTROL descending]** 열의 상자를 선택하여 **[!UICONTROL Score]** 필드의 항목을 내림차순으로 정렬합니다. 받는 사람마다 우라늄 농축은 마지막 게임의 최고 점수와 일치하는 라인을 추가합니다. **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/uc1_enrich_10.png)

1. **[!UICONTROL Data to add]** 창에서 **[!UICONTROL Score]** 필드를 두 번 클릭합니다. 각 수신자에게 데이터 연계 강화 활동은 **[!UICONTROL Score]** 필드만 추가합니다. **[!UICONTROL Finish]**&#x200B;을(를) 클릭합니다.

   ![](assets/uc1_enrich_11.png)

농축활동의 인바운드 전환을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Display the target]**&#x200B;을 선택합니다. 작업 테이블에는 다음 데이터가 포함되어 있습니다.

![](assets/uc1_enrich_13.png)

연결된 스키마:

![](assets/uc1_enrich_15.png)

농축 활동의 아웃바운드 전환으로 이 작업을 갱신합니다. 받는 사람 점수에 연결된 데이터가 추가되었음을 확인할 수 있습니다. 각 수신자의 최고 점수가 복구되었습니다.

![](assets/uc1_enrich_12.png)

일치하는 스키마도 개선되었습니다.

![](assets/uc1_enrich_14.png)

## 3단계:분할 및 배달 {#step-3--split-and-delivery}

점수를 기준으로 수신자를 정렬하기 위해 농축된 후 **[!UICONTROL Split]** 활동이 추가됩니다.

![](assets/uc1_enrich_18.png)

1. 점수가 가장 높은 수신자를 포함하도록 첫 번째(**우승자**) 하위 세트가 정의되었습니다. 이렇게 하려면 레코드 수의 제한을 정의하고, 점수에 내림차순 정렬을 적용하고, 레코드 수를 1로 제한합니다.

   ![](assets/uc1_enrich_16.png)

1. 두 번째 (**두 번째 위치**) 하위 집합에는 두 번째 높은 점수가 있는 받는 사람이 포함됩니다. 구성은 첫 번째 하위 세트에 대해 동일합니다.

   ![](assets/uc1_enrich_17.png)

1. 세 번째(**패자**) 하위 집합에는 다른 받는 사람이 모두 포함됩니다. **[!UICONTROL General]** 탭으로 이동한 후 **[!UICONTROL Generate complement]** 상자를 선택하여 두 개의 가장 높은 점수를 달성하지 못한 모든 수신자를 타게팅합니다.

   ![](assets/uc1_enrich_19.png)

1. 각 하위 세트에 대해 다른 배달 템플릿을 사용하여 각 하위 세트에 대해 **[!UICONTROL Delivery]** 유형 활동을 추가합니다.

   ![](assets/uc1_enrich_20.png)

