---
product: campaign
title: 가설 추적
description: 캠페인 응답 관리자에서 가설을 추적하는 방법에 대해 알아보기
feature: Campaigns, Monitoring, Reporting
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 1%

---

# 가설 추적{#hypothesis-tracking}



가설 계산의 결과는 Adobe Campaign 플랫폼의 다양한 수준에서 사용할 수 있습니다. 가설 및 타겟 모집단 반응에 의해 계산된 지표는 실제 가설을 통해 볼 수 있을 뿐만 아니라 캠페인 및 게재를 통해 사용할 수 있는 가설 보고서에서도 볼 수 있습니다.

## 가설 결과 {#hypothesis-results}

### 지표 {#indicators}

가설이 계산되면 몇 가지 측정 지표가 자동으로 업데이트됩니다. 다음에서 사용할 수 있습니다. **[!UICONTROL General]** 가설의 탭입니다.

![](assets/response_hypothesis_delivery_example_010.png)

이러한 지표는 다음과 같습니다.

* **응답자 연락처 수**: 가설과 일치하는 연락한 개인 수.
* **연락한 응답률**: 응답자 연락처 수/게재 중 연락한 총 직원입니다.
* **응답자 컨트롤 그룹 연락처 수**: 가설과 일치하는 컨트롤 그룹 수입니다.
* **컨트롤 그룹의 응답률**: 응답자 컨트롤 그룹 수 / 총 게재 컨트롤 그룹 수
* **반응 수**: 개인, 가설 및 트랜잭션 표 간의 관계를 포함하는 테이블의 레코드 수입니다.

전체 표시기 목록을 보려면 **[!UICONTROL Display the list]** 링크:

![](assets/response_hypothesis_indicators_002.png)

다음 정보는 표시기에서 제공됩니다.

* **연락한 인구의 총 수익**: 연락한 개인 수에 대한 총 금액입니다.
* **컨트롤 그룹의 총 수익**: 컨트롤 그룹 수에 대한 총액.
* **연락처당 평균 수익**: 총 금액 / 연락
* **컨트롤 그룹의 평균 수익**: 총 금액/컨트롤 그룹.
* **연락처당 총 이익**: 연락한 총 이익
* **컨트롤 그룹의 총 이익**: 컨트롤 그룹에 대한 총 이익
* **연락처당 평균 이익**: 총 이익 / 연락
* **컨트롤 그룹의 평균 이익**: 총 여백/컨트롤 그룹.
* **추가 수익**: (연락한 평균 수익 - 컨트롤 그룹의 평균 수익)&#42;연락한 수
* **추가 이익**: (연락처의 평균 이익-컨트롤 그룹의 평균 이익)/연락한 수
* **연락처당 평균 비용**: 계산된 배달 비용 / 연락처 수
* **ROI**: 계산된 게재 비용 / 연락처당 총 이익
* **효과적인 ROI**: 계산된 게재 비용 / 추가 마진.
* **중요도**: 캠페인 중요도에 따라 0~3 값이 포함됩니다.

### 반응 {#reactions}

다음을 통해 가설에 대한 수신자의 반응을 볼 수 있습니다. **[!UICONTROL Reactions]** 탭.

1. 가설 계산이 완료되면 **[!UICONTROL Campaign management > Measurement hypotheses]** Adobe Campaign 트리의 노드입니다.
1. 원하는 가설을 선택하고 **[!UICONTROL Reactions]** 마케팅 캠페인 후에 구매할 가능성이 있는 수신자 목록을 보려면 탭입니다.

   ![](assets/response_hypothesis_reactions_001.png)

## 보고서 {#reports}

다음 **[!UICONTROL Hypothesis report]** 캠페인 및 게재에 대해 수행된 가설 결과를 볼 수 있습니다. 이 보고서에는 가설에 의해 계산된 지표가 포함되어 있습니다(자세한 내용은 다음을 참조하십시오.) [지표](#indicators)).

* **캠페인 수준에서**: 다음 클릭: **[!UICONTROL Reports]** 관련 캠페인의 링크 및 선택 **[!UICONTROL Hypothesis report]**. 이 보고서에는 캠페인 게재 목록과 각 게재에 대해 계산된 가설이 포함되어 있습니다.

  ![](assets/response_hypothesis_campaign_report_001.png)

* **게재 수준**: 보고서에 액세스하려면 관련 게재를 열고 다음을 클릭합니다. **[!UICONTROL Reports]** 다음에서 **[!UICONTROL Summary]** 탭을 클릭하고 다음을 선택합니다. **[!UICONTROL Hypothesis report]**. 동일한 게재에 대해 여러 가설이 계산되었다면 보고서에는 모든 가설이 포함될 것이다.

  ![](assets/response_hypothesis_delivery_report_001.png)
