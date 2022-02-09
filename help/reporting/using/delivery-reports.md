---
product: campaign
title: 게재 보고서
description: 게재 보고서
feature: Reporting
exl-id: 74feb13f-0994-4a6a-ae4f-2538b07cc9c0
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '1443'
ht-degree: 2%

---

# 게재 보고서 {#delivery-reports}

![](../../assets/common.svg)

게재 개요에서 액세스할 수 있는 다양한 보고서를 통해 게재 실행을 추적할 수 있습니다. 보고서를 표시하려면 다음 절차를 적용합니다.

1. 로 이동합니다. **[!UICONTROL Campaigns]** 탭을 클릭하고 **[!UICONTROL Delivery]** 게재 목록을 표시하는 링크입니다.
1. 세부 사항을 표시하려면 표시할 게재 이름을 클릭합니다.

   ![](assets/s_ncs_user_detailled_report.png)

1. 을(를) 선택합니다 **[!UICONTROL Summary]** 탭을 클릭하고 **[!UICONTROL Reports]** 를 눌러 게재와 관련된 보고서에 액세스합니다.

   ![](assets/s_ncs_user_detailled_report2.png)

   기본적으로 다음 보고서를 사용할 수 있습니다.

   * **[!UICONTROL Delivery throughput]** : 참조 [게재 처리량](../../reporting/using/global-reports.md#delivery-throughput).
   * **[!UICONTROL Sharing to social networks]** : 참조 [소셜 네트워크에 공유](../../reporting/using/global-reports.md#sharing-to-social-networks).
   * **[!UICONTROL Statistics on sharing activities]** : 참조 [활동 공유에 대한 통계](../../reporting/using/global-reports.md#statistics-on-sharing-activities).
   * **[!UICONTROL Hot clicks]** : 참조 [핫 클릭](#hot-clicks).
   * **[!UICONTROL Tracking statistics]** : 참조 [통계 추적](#tracking-statistics)
   * **[!UICONTROL URLs and click streams]** : 참조 [URL 및 클릭 스트림](#urls-and-click-streams).
   * **[!UICONTROL Tracking indicators]** : 참조 [지표 추적](#tracking-indicators).
   * **[!UICONTROL Non-deliverables and bounces]** : 참조 [게재 불가 및 이탈](../../reporting/using/global-reports.md#non-deliverables-and-bounces).
   * **[!UICONTROL User activities]** : 참조 [사용자 활동](../../reporting/using/global-reports.md#user-activities).
   * **[!UICONTROL Delivery summary]** : 참조 [게재 요약](#delivery-summary).
   * **[!UICONTROL Subscription tracking]** : 참조 [구독 추적](../../reporting/using/global-reports.md#subscription-tracking).
   * **[!UICONTROL Delivery statistics]** : 참조 [게재 통계](../../reporting/using/global-reports.md#delivery-statistics).
   * **[!UICONTROL Breakdown of opens]** : 참조 [열기 분류](../../reporting/using/global-reports.md#breakdown-of-opens).

## 지표 추적 {#tracking-indicators}

이 보고서는 게재를 받을 때 수신자의 동작을 추적하기 위한 주요 지표를 결합합니다. 게재 및 수신 통계, 열기 및 클릭스루 비율, 생성된 클릭 스트림, 웹 추적 및 소셜 네트워크에 대한 활동 공유를 제공합니다.

>[!NOTE]
>
>텍스트 형식의 전자 메일에 연결된 오류의 여분으로 인해 메시지 열기를 기반으로 계산된 값은 항상 예측됩니다. 다음 **[!UICONTROL Distinct opens/Sum of opens for the population reached]** 지표들은 이 오차 마진을 고려한다. 열기 추적에 대한 자세한 내용은 [추적 열기](../../reporting/using/indicator-calculation.md#tracking-opens-).

![](assets/s_ncs_user_tracking_synth_report.png)

**[!UICONTROL 1. Delivery statistics]**

* **[!UICONTROL Messages to deliver]** : 게재 분석 후 게재할 총 메시지 수입니다.
* **[!UICONTROL Success]** : 성공적으로 처리된 메시지 수입니다.

**[!UICONTROL 2. Reception statistics]**

>[!NOTE]
>
>관련 백분율은 성공적으로 전달된 메시지 수를 기반으로 계산됩니다.

* **[!UICONTROL Distinct opens for the population reached]** : 메시지를 한 번 이상 연 타겟팅된 수신자 수 예측 구독 취소 링크 및 미러 페이지의 클릭이 고려됩니다.
* **[!UICONTROL Sum of opens for the population reached]** : 타겟팅된 수신자의 총 열기 수 예측
* **[!UICONTROL Clicks on opt-out link]** : 구독 취소 링크에 대한 클릭 수입니다.
* **[!UICONTROL Clicks on the mirror page link]** : 미러 페이지에 대한 링크에 대한 클릭 수입니다. 고려하려면 게재 마법사(추적된 URL)에서 링크는 다음과 같이 정의해야 합니다. 다음을 참조하십시오 [페이지](../../delivery/using/about-delivery-monitoring.md).
* **[!UICONTROL Estimation of forwards]** : 타겟팅된 수신자가 발송한 전자 메일 수의 예측입니다. 이 값은 개별 사용자의 수와 이메일을 클릭한 개별 수신자 수를 뺀 값을 계산합니다.

   >[!NOTE]
   >
   >개별 사용자와 타겟팅된 수신자 간의 차이에 대한 자세한 내용은 [대상 개인/수신자](../../reporting/using/indicator-calculation.md#targeted-persons---recipients).

**[!UICONTROL 3. Open and click-through rate]**

이 값 표는 인터넷 도메인별 게재, 열기, 클릭 수 및 원시 반응성 분류를 보여줍니다. 다음 표시기가 사용됩니다.

* **[!UICONTROL Sent]** : 이 도메인에서 보낸 총 메시지 수입니다.
* **[!UICONTROL Complaints]** : 수신자가 원치 않는다고 보고한 이 도메인에 대한 메시지 수입니다. 이 비율은 이 도메인에서 보낸 총 메시지 수를 기반으로 계산됩니다.
* **[!UICONTROL Opens]** : 메시지를 한 번 이상 연 해당 도메인의 개별 대상 수신자 수입니다. 이 비율은 이 도메인에서 보낸 총 메시지 수를 기반으로 계산됩니다.
* **[!UICONTROL Clicks]** : 동일한 게재에서 최소 한 번 이상 클릭한 개별 대상 수신자 수입니다. 이 비율은 이 도메인에서 보낸 총 메시지 수를 기반으로 계산됩니다
* **[!UICONTROL Raw reactivity]** : 게재를 한 번 이상 클릭한 수신자 수의 백분율로, 게재를 한 번 이상 연 수신자 수와 비교됩니다.

>[!NOTE]
>
>이 보고서에 표시되는 도메인 이름은 큐브 수준에서 사용되는 항목별 목록에서 정의됩니다. 기본 도메인을 변경하거나 추가하려면 **[!UICONTROL Domains]** 항목화된 목록 및 값 및 별칭을 수정합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../platform/using/managing-enumerations.md)을 참조하십시오. 다음 **[!UICONTROL Others]** 카테고리에는 항목별 목록 값에 속하지 않는 도메인 이름이 포함되어 있습니다.

**[!UICONTROL 4. Generated click streams]**

>[!NOTE]
>
>관련 백분율은 성공적으로 전달된 메시지 수를 기반으로 계산됩니다.

* **[!UICONTROL Distinct clicks for the population reached]** : 게재를 한 번 이상 클릭한 개별 사용자 수입니다.
* **[!UICONTROL Cumulated clicks]** : 구독 취소 링크 및 미러 페이지를 제외하고 타겟팅된 수신자의 총 클릭 수입니다.
* **[!UICONTROL Recipient clicks]** : 동일한 게재에서 최소 한 번 이상 클릭한 개별 대상 수신자 수입니다.
* **[!UICONTROL Estimated recipient reactivity]** : 게재에서 한 번 이상 클릭한 수신자 수의 비율을 게재를 한 번 이상 연 예상 수신자 수와 비교하여 보여줍니다. 옵트아웃 및 미러 페이지 링크의 클릭은 고려되지 않습니다.

**[!UICONTROL 5. Web tracking]**

* **[!UICONTROL Visited pages]** : 메시지 수신 후 방문한 웹 페이지 수입니다.
* **[!UICONTROL Transactions]** : 메시지 수신 후 구매 횟수.
* **[!UICONTROL Total amount]** : 메시지 수신에 따른 총 구매 금액입니다.
* **[!UICONTROL Average transaction amount]** : 개별 게재 수신자의 평균 구매
* **[!UICONTROL Articles]** : 게재 수신자가 구입한 문서 수입니다.
* **[!UICONTROL Average count of articles per transaction]** : 개별 수신자가 수행한 구매당 평균 항목 수입니다.
* **[!UICONTROL Average amount per message]** : 메시지당 생성된 평균 구매 금액입니다.

   >[!NOTE]
   >
   >방문한 페이지, 거래, 금액 또는 문서를 고려하여 웹 추적 태그를 일치하는 웹 페이지에 삽입해야 합니다. 웹 추적 구성은 [이 섹션](../../configuration/using/about-web-tracking.md).

**[!UICONTROL 6. Sharing activities to email and social networks]**

이 섹션에서는 각 소셜 네트워크에서 공유되는 메시지 수를 보여줍니다. 자세한 내용은 [소셜 네트워크에 공유](../../reporting/using/global-reports.md#sharing-to-social-networks).

## URL 및 클릭 스트림 {#urls-and-click-streams}

이 보고서는 게재 후 방문한 페이지 목록을 보여줍니다.

![](assets/s_ncs_user_url_report.png)

다음을 선택하여 이 보고서의 컨텐츠를 구성할 수 있습니다. 표시할 점수 차트, 시간 필터(작업 시작 이후 시작 후 처음 6시간 이상) 및 데이터 표시 모드(레이블별, URL별, 카테고리별)입니다. **[!UICONTROL Refresh]**&#x200B;을(를) 클릭하여 선택 항목을 확인합니다.

다음 비율은 보고서의 위쪽 섹션에 표시됩니다.

* **[!UICONTROL Reactivity]** : 게재를 연 타겟팅된 수신자 예상 수와 관련하여 게재를 클릭한 타겟팅된 수신자 수의 비율입니다. 옵트아웃 링크와 미러 페이지의 클릭은 고려되지 않습니다.

   >[!NOTE]
   >
   >열기 추적에 대한 자세한 내용은 [추적 열기](../../reporting/using/indicator-calculation.md#tracking-opens-).

* **[!UICONTROL Distinct clicks]** : 게재에서 한 번 이상(구독 취소 링크 및 미러 페이지 제외) 클릭한 개별 사용자 수입니다. 표시된 비율은 성공적으로 전달된 메시지 수를 기준으로 계산됩니다.
* **[!UICONTROL Cumulated clicks]** : 타겟팅된 수신자별 총 클릭 수(구독 취소 링크 및 미러 페이지 제외). 표시된 비율은 성공적으로 전달된 메시지 수를 기준으로 계산됩니다.

**[!UICONTROL Platform average]** : 각 비율(반복, 개별 클릭 및 누적 클릭)에 따라 표시되는 이 평균 비율은 이전 6개월 동안 전송된 게재에 대해 계산됩니다. 유형화와 동일한 채널의 게재 만 고려합니다. 증명을 제외합니다.

중앙 테이블은 다음 정보를 제공합니다.

* **[!UICONTROL Clicks]** : 링크당 누적 클릭 수.
* **[!UICONTROL Clicks (in %)]** : 누적 클릭 수와 관련된 링크당 클릭 수의 분류

**[!UICONTROL Breakdown of clicks in time]**

이 차트는 일별 누적 클릭 수를 보여줍니다.

## 게재 요약 {#delivery-summary}

이 보고서는 게재에 대한 모든 주요 정보를 제공합니다.

![](assets/s_ncs_user_synth_report.png)

**[!UICONTROL Target population]**

이 섹션에는 두 개의 지표가 있습니다.

* **[!UICONTROL Initial population]** : 게재가 타겟팅한 총 수신자 수입니다.
* **[!UICONTROL Messages rejected by the rule]** : 유형화 규칙을 적용할 때 분석 중에 무시된 주소 수입니다. 주소가 누락됨, 격리됨, 차단 목록 등 유형화 규칙에 대한 자세한 내용은 다음을 참조하십시오 [페이지](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

**[!UICONTROL Causes of exclusion]**

중간 차트는 분석 중에 거부된 메시지 규칙당 분류를 보여줍니다.

**[!UICONTROL Delivery statistics]**

이 섹션에는 다음 표시기가 포함됩니다.

* **[!UICONTROL Messages to be delivered]** : 게재 분석 후 게재할 총 메시지 수입니다.
* **[!UICONTROL Success]** : 성공적으로 처리된 메시지 수입니다. 연관된 비율은 배달할 메시지 수와 비율 입니다.
* **[!UICONTROL Errors]** : 게재 및 자동 리바운드 처리 중에 누적된 총 오류 수입니다. 연관된 비율은 배달할 메시지 수와 비율 입니다.
* **[!UICONTROL New quarantines]** : 실패한 게재 후 격리된 주소 수(사용자 알 수 없음, 잘못된 도메인). 연관된 비율은 배달할 메시지 수와 비율 입니다.

## 핫 클릭 {#hot-clicks}

이 보고서는 각 링크에 대한 클릭 비율( HTML 및/또는 텍스트)을 포함하는 메시지 콘텐츠를 보여줍니다. 개인화 블록은 구독 취소 링크, 미러 페이지 링크 및 오퍼 링크를 총 누적 클릭 수에 고려하지만 보고서에 표시되지 않습니다.

>[!NOTE]
>
>게재에 오퍼(상호 작용)가 포함되어 있으면 보고서 위 부분에 오퍼에 대한 클릭 비율을 표시하는 상자가 표시됩니다.

![](assets/s_ncs_user_clic_report.png)

## 통계 추적 {#tracking-statistics}

이 보고서는 열기, 클릭 및 트랜잭션에 대한 통계를 제공합니다.

![](assets/s_ncs_user_stat_report.png)

게재의 마케팅 영향을 추적할 수 있습니다. 시간 표시줄(1시간, 3시간 또는 24시간 보기 등)을 변경하여 값이 표시되는 방식을 구성할 수 있습니다. **[!UICONTROL Refresh]**&#x200B;을(를) 클릭하여 선택 항목을 확인합니다.

이 보고서는 배달을 최대 효율에 도달하는 데 필요한 시간을 표시하는 값 테이블 및 파레토 차트를 제공합니다. 다음 표시기가 사용됩니다.

* **[!UICONTROL Opens]** : 연 총 메시지 수의 백분율에 도달하는 데 필요한 시간을 예측합니다. 텍스트 형식의 이메일은 고려되지 않습니다. 열기 추적에 대한 자세한 내용은 [추적 열기](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]** : 기록된 총 클릭 수의 백분율에 도달하는 데 필요한 시간의 예측. 옵트아웃 링크 및 미러 페이지의 클릭은 고려되지 않습니다.
* **[!UICONTROL Transactions]** : 메시지 수신 후 총 트랜잭션 수의 백분율을 달성하는 데 필요한 시간입니다. 트랜잭션을 고려하려면 트랜잭션 유형 웹 추적 태그를 일치하는 웹 페이지에 삽입해야 합니다. 웹 추적 구성은 [이 섹션](../../configuration/using/about-web-tracking.md).
