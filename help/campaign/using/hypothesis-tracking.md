---
solution: Campaign Classic
product: campaign
title: 가설 추적
description: 가설 추적
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 1%

---


# 가설 추적{#hypothesis-tracking}

가설 계산의 결과는 Adobe Campaign 플랫폼의 다양한 수준에서 사용할 수 있습니다.가설을 통해 계산된 지표와 목표 모집단 반응은 실제 가설을 통해서도 볼 수 있고, 캠페인 및 제공을 통해 사용할 수 있는 가설을 통해서도 볼 수 있습니다.

## 가설 결과 {#hypothesis-results}

### 표시기 {#indicators}

가설이 계산되면 여러 측정 표시기가 자동으로 업데이트됩니다. 이러한 내용은 가설 **[!UICONTROL General]** 탭에서 사용할 수 있습니다.

![](assets/response_hypothesis_delivery_example_010.png)

이러한 지표는 다음과 같습니다.

* **응답자 연락처** 수:가설과 일치하는 접촉 개인의 수.
* **연결된 응답률**:응답자 연락처 수/배달 중 총 연락 인원 수.
* **응답자 제어 그룹 연락처 수**:가설과 일치하는 제어 그룹 수입니다.
* **제어 그룹의 응답률**:응답자 제어 그룹 수/전달 제어 그룹의 총 수입니다.
* **반응 수**:개인, 가설 및 트랜잭션 테이블 간의 관계를 포함하는 테이블의 레코드 수입니다.

표시기의 전체 목록을 보려면 **[!UICONTROL Display the list]** 링크를 클릭합니다.

![](assets/response_hypothesis_indicators_002.png)

다음 정보는 표시기에서 제공합니다.

* **연결된 인구의 총 매출액**:연결된 개인 수에 대한 총 금액.
* **제어 그룹의 총 매출**:제어 그룹 수에 대한 합계 금액입니다.
* **연락처당 평균 매출액**:총 금액/접촉됨.
* **제어 그룹의 평균 매출**:합계 금액/제어 그룹.
* **연락처당 총 여백**:총 접촉 마진.
* **제어 그룹의 총 여백**:제어 그룹에 대한 총 여백.
* **연락처당 평균 마진**:총 여백/접촉됨.
* **제어 그룹의 평균 여백**:전체 여백/제어 그룹
* **추가 매출액**:(접촉된 평균 수익 제어 그룹의 평균 매출)*접촉 수
* **추가 여백**:(접촉 평균 마진-제어 그룹의 평균 마진)/접촉 수
* **연락처당 평균 비용**:계산된 배달 비용/연락처 수입니다.
* **ROI**:배달의 계산된 비용/연락처당 총 마진 수
* **효과적인 ROI**:계산된 배달 비용/추가 마진.
* **중요도**:은 캠페인 중요도에 따라 0에서 3까지의 값을 포함합니다.

### 반응 {#reactions}

**[!UICONTROL Reactions]** 탭을 통해 가설을 받는 사람의 반응을 볼 수 있습니다.

1. 가설 계산이 완료되면 Adobe Campaign 트리의 **[!UICONTROL Campaign management > Measurement hypotheses]** 노드로 이동합니다.
1. 원하는 가설을 선택하고 **[!UICONTROL Reactions]** 탭을 클릭하여 마케팅 캠페인 다음에 제품을 구입할 가능성이 있는 수신자 목록을 봅니다.

   ![](assets/response_hypothesis_reactions_001.png)

## 보고서 {#reports}

**[!UICONTROL Hypothesis report]**&#x200B;을 사용하면 캠페인 및 게재에 대해 수행된 가설을 볼 수 있습니다. 이 보고서에는 가설을 통해 계산된 지표가 포함되어 있습니다(자세한 내용은 [지표](#indicators) 참조).

* **캠페인 수준에서**:관련  **[!UICONTROL Reports]** 캠페인의 링크를 클릭하고 해당 캠페인을 선택합니다  **[!UICONTROL Hypothesis report]**. 이 보고서에는 각 게재에 대해 계산된 가설 및 캠페인 배달 목록이 포함되어 있습니다.

   ![](assets/response_hypothesis_campaign_report_001.png)

* **배달 수준에서**:보고서에 액세스하려면 관련 제공을 열고 탭 **[!UICONTROL Reports]** 에서 을  **[!UICONTROL Summary]** 클릭하고 을 선택합니다  **[!UICONTROL Hypothesis report]**. 동일한 전달을 위해 여러 가지 가설을 계산하면 보고서에 모든 가설이 포함됩니다.

   ![](assets/response_hypothesis_delivery_report_001.png)
