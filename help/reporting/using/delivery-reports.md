---
product: campaign
title: 게재 보고서
description: 게재 보고서
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Reporting, Monitoring
exl-id: 74feb13f-0994-4a6a-ae4f-2538b07cc9c0
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1461'
ht-degree: 8%

---

# 게재 보고서 {#delivery-reports}



게재 개요에서 액세스할 수 있는 다양한 보고서를 통해 게재 실행을 추적할 수 있습니다. 보고서를 표시하려면 다음 절차를 적용합니다.

1. **[!UICONTROL Campaigns]** 탭으로 이동하여 **[!UICONTROL Delivery]** 링크를 클릭하여 게재 목록을 표시합니다.
1. 세부 정보를 표시하려면 표시할 게재명을 클릭합니다.

   ![](assets/s_ncs_user_detailled_report.png)

1. **[!UICONTROL Summary]** 탭을 선택하고 **[!UICONTROL Reports]** 링크를 클릭하여 게재와 관련된 보고서에 액세스합니다.

   ![](assets/s_ncs_user_detailled_report2.png)

   기본적으로 다음 보고서를 사용할 수 있습니다.

   * **[!UICONTROL Delivery throughput]** : [게재 처리량](../../reporting/using/global-reports.md#delivery-throughput)을(를) 참조하세요.
   * **[!UICONTROL Sharing to social networks]** : [소셜 네트워크에 공유](../../reporting/using/global-reports.md#sharing-to-social-networks)를 참조하세요.
   * **[!UICONTROL Statistics on sharing activities]** : [공유 활동에 대한 통계](../../reporting/using/global-reports.md#statistics-on-sharing-activities)를 참조하세요.
   * **[!UICONTROL Hot clicks]** : [핫 클릭](#hot-clicks)을 참조하세요.
   * **[!UICONTROL Tracking statistics]** : [추적 통계](#tracking-statistics)를 참조하세요.
   * **[!UICONTROL URLs and click streams]** : [URL 및 클릭 스트림](#urls-and-click-streams)을 참조하세요.
   * **[!UICONTROL Tracking indicators]** : [추적 표시기](#tracking-indicators)를 참조하세요.
   * **[!UICONTROL Non-deliverables and bounces]** : [게재 불가 및 바운스](../../reporting/using/global-reports.md#non-deliverables-and-bounces)를 참조하세요.
   * **[!UICONTROL User activities]** : [사용자 활동](../../reporting/using/global-reports.md#user-activities)을 참조하세요.
   * **[!UICONTROL Delivery summary]** : [게재 요약](#delivery-summary)을 참조하세요.
   * **[!UICONTROL Subscription tracking]** : [구독 추적](../../reporting/using/global-reports.md#subscription-tracking)을 참조하세요.
   * **[!UICONTROL Delivery statistics]** : [게재 통계](../../reporting/using/global-reports.md#delivery-statistics)를 참조하세요.
   * **[!UICONTROL Breakdown of opens]** : [열기 분석](../../reporting/using/global-reports.md#breakdown-of-opens)을 참조하세요.

## 지표 추적 {#tracking-indicators}

이 보고서는 게재를 받을 때 수신자의 행동을 추적하기 위한 주요 지표를 결합합니다. 이렇게 하면 게재 및 수신 통계, 열람율 및 클릭스루 비율, 생성된 클릭스트림, 웹 추적 및 소셜 네트워크에 대한 공유 활동에 액세스할 수 있습니다.

>[!NOTE]
>
>텍스트 형식의 전자 메일에 연결된 오류 여백으로 인해 메시지 열기를 기반으로 계산된 값은 항상 예상 값입니다. **[!UICONTROL Distinct opens/Sum of opens for the population reached]** 표시기는 이 오류 여백을 고려합니다. 열기 추적에 대한 자세한 내용은 [열기 추적](../../reporting/using/indicator-calculation.md#tracking-opens-)을 참조하세요.

![](assets/s_ncs_user_tracking_synth_report.png)

**[!UICONTROL 1. Delivery statistics]**

* **[!UICONTROL Messages to deliver]** : 게재 분석 후 게재할 총 메시지 수
* **[!UICONTROL Success]** : 성공적으로 처리된 메시지 수입니다.

**[!UICONTROL 2. Reception statistics]**

>[!NOTE]
>
>관련 백분율은 성공적으로 전달된 메시지 수를 기반으로 계산됩니다.

* **[!UICONTROL Distinct opens for the population reached]** : 메시지를 한 번 이상 연 대상 받는 사람 수 예상. 링크를 클릭하려면 이메일을 열어야 하므로 추적된 URL에 대한 클릭 수가 고려됩니다.
* **[!UICONTROL Sum of opens for the population reached]** : 타깃팅된 수신자의 총 열람 수 예상.
* **[!UICONTROL Clicks on opt-out link]** : 구독 취소 링크의 클릭 수입니다.
* **[!UICONTROL Clicks on the mirror page link]** : 미러 페이지 링크를 클릭한 횟수. 고려하려면 게재 마법사(추적된 URL)에서 링크를 이와 같이 정의해야 합니다. 이 [페이지](../../delivery/using/about-delivery-monitoring.md)를 참조하세요.
* **[!UICONTROL Estimation of forwards]** : 타겟팅된 수신자가 전달한 전자 메일 수 예상. 이 값은 고유 사람 수와 이메일을 클릭한 고유 수신자 수를 빼서 계산합니다.

  >[!NOTE]
  >
  >고유 사용자와 대상 받는 사람 간의 차이에 대한 자세한 내용은 [대상 사용자/받는 사람](../../reporting/using/indicator-calculation.md#targeted-persons---recipients)을 참조하세요.

**[!UICONTROL 3. Open and click-through rate]**

이 값 표에는 인터넷 도메인별 게재, 열기, 클릭 수 및 원시 재활동 분류가 표시됩니다. 다음 지표가 사용됩니다.

* **[!UICONTROL Sent]** : 이 도메인에서 보낸 총 메시지 수입니다.
* **[!UICONTROL Complaints]** : 받는 사람이 원치 않는 것으로 보고한 이 도메인에 대한 메시지 수입니다. 이 비율은 이 도메인에서 보낸 총 메시지 수를 기반으로 계산됩니다.
* **[!UICONTROL Opens]** : 이 도메인에 대해 최소 한 번 이상 메시지를 연 고유한 타겟팅된 받는 사람 수 이 비율은 이 도메인에서 보낸 총 메시지 수를 기반으로 계산됩니다.
* **[!UICONTROL Clicks]** : 동일한 게재를 한 번 이상 클릭한 고유한 타깃팅된 수신자 수입니다. 이 비율은 이 도메인에서 보낸 총 메시지 수를 기반으로 계산됩니다
* **[!UICONTROL Raw reactivity]** : 게재를 한 번 이상 클릭한 수신자 수와 게재를 한 번 이상 연 수신자 수의 비율입니다.

>[!NOTE]
>
>이 보고서에 표시되는 도메인 이름은 큐브 수준에서 사용되는 항목별 목록에 정의됩니다. 기본 도메인을 변경, 추가 또는 제거하려면 **[!UICONTROL Domains]** 항목별 목록을 편집하고 값과 별칭을 수정합니다. 자세한 정보는 [이 섹션](../../platform/using/managing-enumerations.md)을 참조하세요. **[!UICONTROL Others]** 범주에 항목별 목록의 값에 속하지 않는 도메인 이름이 포함되어 있습니다.

**[!UICONTROL 4. Generated click streams]**

>[!NOTE]
>
>관련 백분율은 성공적으로 전달된 메시지 수를 기반으로 계산됩니다.

* **[!UICONTROL Distinct clicks for the population reached]** : 한 번 이상 게재를 클릭한 고유한 사람 수입니다.
* **[!UICONTROL Cumulated clicks]** : 구독 취소 링크 및 미러 페이지를 제외한 타깃팅된 수신자의 총 클릭 수입니다.
* **[!UICONTROL Recipient clicks]** : 동일한 게재를 한 번 이상 클릭한 고유한 타깃팅된 수신자 수입니다.
* **[!UICONTROL Estimated recipient reactivity]** : 게재를 한 번 이상 클릭한 수신자 수와 게재를 한 번 이상 연 것으로 예상되는 수신자 수의 비율입니다. 옵트아웃 및 미러 페이지 링크에 대한 클릭은 고려되지 않습니다.

**[!UICONTROL 5. Web tracking]**

* **[!UICONTROL Visited pages]** : 메시지를 받은 후 방문한 웹 페이지 수입니다.
* **[!UICONTROL Transactions]** : 메시지 수신 후 구매 횟수.
* **[!UICONTROL Total amount]** : 메시지 수신 후 총 구매 금액.
* **[!UICONTROL Average transaction amount]** : 개별 게재 수신자의 평균 구매 횟수입니다.
* **[!UICONTROL Articles]** : 게재 수신자가 구매한 문서 수입니다.
* **[!UICONTROL Average count of articles per transaction]** : 개별 수신자가 수행한 구매당 평균 항목 수입니다.
* **[!UICONTROL Average amount per message]** : 메시지당 생성된 평균 구매 금액입니다.

  >[!NOTE]
  >
  >방문 페이지, 거래, 금액 또는 문서를 고려하려면 웹 추적 태그를 일치하는 웹 페이지에 삽입해야 합니다. 웹 추적 구성이 [이 섹션](../../configuration/using/about-web-tracking.md)에 표시됩니다.

**[!UICONTROL 6. Sharing activities to email and social networks]**

이 섹션에는 각 소셜 네트워크에서 공유되는 메시지 수가 표시됩니다. 자세한 내용은 [소셜 네트워크에 공유](../../reporting/using/global-reports.md#sharing-to-social-networks)를 참조하세요.

## URL 및 클릭 스트림 {#urls-and-click-streams}

이 보고서는 게재 후 방문한 페이지 목록을 보여줍니다.

![](assets/s_ncs_user_url_report.png)

표시할 점수 차트, 시간 필터(작업 실행 이후, 실행 후 처음 6시간 등)를 선택하여 이 보고서의 내용을 구성할 수 있습니다. 및 데이터 표시 모드(레이블별, URL별, 범주별)입니다. **[!UICONTROL Refresh]**&#x200B;을(를) 클릭하여 선택 내용을 확인합니다.

보고서의 상단 섹션에는 다음 비율이 표시됩니다.

* **[!UICONTROL Reactivity]** : 게재를 연 예상 대상 받는 사람 수와 관련하여 게재를 클릭한 대상 받는 사람 수의 비율입니다. 옵트아웃 링크 및 미러 페이지의 클릭 수는 고려되지 않습니다.

  >[!NOTE]
  >
  >열기 추적에 대한 자세한 내용은 [열기 추적](../../reporting/using/indicator-calculation.md#tracking-opens-)을 참조하세요.

* **[!UICONTROL Distinct clicks]** : 게재에서 최소 한 번 이상 클릭한 고유 사용자 수(구독 취소 링크 및 미러 페이지 제외). 표시되는 비율은 성공적으로 게재된 메시지 수를 기반으로 계산됩니다.
* **[!UICONTROL Cumulated clicks]** : 대상 수신자의 총 클릭 수(구독 취소 링크 및 미러 페이지 제외) 표시된 비율은 성공적으로 전달된 메시지 수를 기반으로 계산됩니다.

**[!UICONTROL Platform average]** : 각 비율(반응성, 개별 클릭 수 및 누적된 클릭 수) 아래에 표시되는 이 평균 비율은 이전 6개월 동안 전송된 게재에 대해 계산됩니다. 유형화가 동일한 게재 및 동일한 채널의 게재만 고려됩니다. 증명이 제외됩니다.

중앙 테이블은 다음 정보를 제공합니다.

* **[!UICONTROL Clicks]** : 링크당 누적된 클릭 수입니다.
* **[!UICONTROL Clicks (in %)]** : 누적된 총 클릭 수와 관련하여 링크당 클릭 수를 분류합니다.

**[!UICONTROL Breakdown of clicks in time]**

이 차트는 하루에 누적된 클릭수의 분류를 보여 줍니다.

## 게재 요약 {#delivery-summary}

이 보고서는 게재에 대한 모든 기본 정보를 제공합니다.

![](assets/s_ncs_user_synth_report.png)

**[!UICONTROL Target population]**

이 섹션에는 두 개의 표시기가 있습니다.

* **[!UICONTROL Initial population]** : 게재를 대상으로 하는 총 수신자 수입니다.
* **[!UICONTROL Messages rejected by the rule]** : 유형화 규칙을 적용할 때 분석 중에 무시된 주소 수: 주소 누락, 격리됨, 차단 목록 등 유형화 규칙에 대한 자세한 내용은 이 [페이지](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies)를 참조하세요.

**[!UICONTROL Causes of exclusion]**

중간 차트는 분석 중에 거부된 메시지의 규칙별 분류를 보여 줍니다.

**[!UICONTROL Delivery statistics]**

이 섹션에는 다음 지표가 포함됩니다.

* **[!UICONTROL Messages to be delivered]** : 게재 분석 후 게재할 총 메시지 수
* **[!UICONTROL Success]** : 성공적으로 처리된 메시지 수입니다. 결합된 비율은 게재될 메시지 수에 대한 비율입니다.
* **[!UICONTROL Errors]** : 게재 및 자동 반동 처리 중 누적된 총 오류 수. 결합된 비율은 게재될 메시지 수에 대한 비율입니다.
* **[!UICONTROL New quarantines]** : 게재 실패 후 격리된 주소 수(사용자 알 수 없음, 잘못된 도메인). 결합된 비율은 게재될 메시지 수에 대한 비율입니다.

## 핫 클릭 {#hot-clicks}

이 보고서에는 메시지 콘텐츠(HTML 및/또는 텍스트)와 각 링크의 링크 클릭 비율이 표시됩니다. 개인 맞춤화 블록 구독 취소 링크, 미러 페이지 링크 및 오퍼 링크는 총 누적 클릭 수 계산에 포함되지만 보고서에는 표시되지 않습니다.

>[!NOTE]
>
>게재에 오퍼(상호 작용)가 포함된 경우 오퍼에 대한 클릭 비율을 표시하는 상자가 보고서 위 부분에 나타납니다.

![](assets/s_ncs_user_clic_report.png)

## 추적 통계 {#tracking-statistics}

이 보고서는 열기, 클릭 및 트랜잭션에 대한 통계를 제공합니다.

![](assets/s_ncs_user_stat_report.png)

게재의 마케팅 효과를 추적할 수 있습니다. 시간표(1시간, 3시간 또는 24시간 보기 등)를 변경하여 값이 표시되는 방식을 구성할 수 있습니다. **[!UICONTROL Refresh]**&#x200B;을(를) 클릭하여 선택 내용을 확인합니다.

이 보고서는 게재가 최대 효율에 도달하는 데 필요한 시간을 표시하는 값 테이블과 파레토 차트를 제공합니다. 다음 지표가 사용됩니다.

* **[!UICONTROL Opens]** : 열려 있는 총 메시지 수의 비율에 도달하는 데 필요한 시간을 예상합니다. 텍스트 형식의 이메일은 고려되지 않습니다. 열기 추적에 대한 자세한 내용은 [열기 추적](../../reporting/using/indicator-calculation.md#tracking-opens-)을 참조하세요.
* **[!UICONTROL Clicks]** : 기록된 총 클릭 수의 비율에 도달하는 데 필요한 시간을 예상합니다. 옵트아웃 링크 및 미러 페이지 클릭 수는 고려되지 않습니다.
* **[!UICONTROL Transactions]** : 메시지 수신 후 총 트랜잭션 수의 비율에 도달하는 데 필요한 시간입니다. 트랜잭션을 고려하려면 트랜잭션 유형 웹 추적 태그를 일치하는 웹 페이지에 삽입해야 합니다. 웹 추적 구성이 [이 섹션](../../configuration/using/about-web-tracking.md)에 표시됩니다.
