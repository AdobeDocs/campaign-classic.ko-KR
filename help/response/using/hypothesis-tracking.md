---
product: campaign
title: 가설 추적
description: Campaign Response Manager에서 가설을 추적하는 방법을 알아봅니다
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# 가설 추적{#hypothesis-tracking}

![](../../assets/v7-only.svg)

가설 계산의 결과는 Adobe Campaign 플랫폼의 다양한 수준에서 사용할 수 있습니다. 가설 및 대상 모집단 반응에 의해 계산된 지표는 실제 가설을 통해 볼 수 있고, 캠페인 및 게재를 통해 사용할 수 있는 가설 보고서에서도 볼 수 있습니다.

## 가설 결과 {#hypothesis-results}

### 지표 {#indicators}

가설이 계산되면 몇 가지 측정 지표가 자동으로 업데이트됩니다. 이러한 기능은 **[!UICONTROL General]** 가설 탭.

![](assets/response_hypothesis_delivery_example_010.png)

이러한 지표는 다음과 같습니다.

* **응답자 연락처 수**: 가설과 일치하는 접촉된 개인 수입니다.
* **연락 응답률**: 응답자 연락처 수/게재 중 연락된 총 사용자 수.
* **응답자 컨트롤 그룹 연락처 수**: 가설과 일치하는 컨트롤 그룹 수입니다.
* **컨트롤 그룹의 응답률**: 응답자 컨트롤 그룹 수/게재 제어 그룹의 총 수입니다.
* **반응 수**: 개인, 가설 및 트랜잭션 테이블 간의 관계를 포함하는 테이블의 레코드 수입니다.

전체 지표 목록을 보려면 **[!UICONTROL Display the list]** 링크:

![](assets/response_hypothesis_indicators_002.png)

다음 정보는 표시기에서 제공합니다.

* **연락된 모집단 총 매출액**: 연락된 개인 수에 대한 총 금액입니다.
* **컨트롤 그룹의 총 매출액**: 컨트롤 그룹 수에 대한 총 금액입니다.
* **연락처당 평균 매출액**: 총 금액/연락 횟수
* **컨트롤 그룹의 평균 매출**: 합계 금액/통제 그룹.
* **연락처당 총 마진 수**: 접촉된 총 매출입니다.
* **컨트롤 그룹의 총 여백**: 컨트롤 그룹에 대한 총 여백.
* **연락처당 평균 여백**: 총 마진/연락 횟수.
* **컨트롤 그룹의 평균 여백**: 전체 여백/컨트롤 그룹
* **추가 매출**: (접촉된 평균 수익 - 통제 그룹의 평균 매출)*연락 횟수
* **추가 여백**: (접촉된 평균 마진 - 통제 그룹의 평균 마진) / 연락 횟수
* **연락처당 평균 비용**: 계산된 납품 원가/담당자 수
* **ROI**: 게재의 계산된 비용 / 연락처당 총 마진 수
* **효과적인 ROI**: 계산된 납품 원가/추가 마진.
* **유의**: 은 캠페인 중요도에 따라 0~3 값을 포함합니다.

### 반응 {#reactions}

를 통해 가설을 통해 수신자의 반응을 볼 수 있습니다 **[!UICONTROL Reactions]** 탭.

1. 가설 계산이 완료되면 로 이동하십시오. **[!UICONTROL Campaign management > Measurement hypotheses]** 노드 아래에 나열된 상태로 남아 있습니다.
1. 원하는 가설을 선택하고 을(를) 클릭합니다 **[!UICONTROL Reactions]** 탭하여 마케팅 캠페인 다음에 구매할 수 있는 수신자 목록을 볼 수 있습니다.

   ![](assets/response_hypothesis_reactions_001.png)

## 보고서 {#reports}

다음 **[!UICONTROL Hypothesis report]** 캠페인 및 게재에서 수행된 가설 결과를 볼 수 있습니다. 이 보고서에는 가설을 통해 계산된 지표가 포함되어 있습니다(자세한 내용은 [지표](#indicators)).

* **캠페인 수준에서**: 를 클릭합니다. **[!UICONTROL Reports]** 관련 캠페인의 링크를 선택하고 **[!UICONTROL Hypothesis report]**. 이 보고서에는 각 게재에 대해 계산된 가설 및 캠페인 게재 목록이 포함되어 있습니다.

   ![](assets/response_hypothesis_campaign_report_001.png)

* **게재 수준에서**: 보고서에 액세스하려면 관련 게재를 열고 **[!UICONTROL Reports]** 에서 **[!UICONTROL Summary]** 탭을 선택하고 을(를) 선택합니다 **[!UICONTROL Hypothesis report]**. 동일한 게재에 대해 여러 가설이 계산되면 보고서에 모든 가설이 포함됩니다.

   ![](assets/response_hypothesis_delivery_report_001.png)
