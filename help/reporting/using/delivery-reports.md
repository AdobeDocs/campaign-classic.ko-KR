---
title: 배달 보고서
seo-title: 배달 보고서
description: 배달 보고서
seo-description: null
page-status-flag: never-activated
uuid: 83ea834e-08f7-441b-8f15-a25ec07c4aab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
discoiquuid: cc832666-ad18-49ce-afcc-f9169b683ae8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f7655cd93a7dc8ecd35cd379da350ad279cae725

---


# 배달 보고서 {#delivery-reports}

배달 개요에서 액세스할 수 있는 다양한 보고서를 통해 배달 실행을 추적할 수 있습니다. 보고서를 표시하려면 다음 절차를 적용합니다.

1. 우주로 **[!UICONTROL Campaigns]** 이동하고 **[!UICONTROL Delivery]** 링크를 클릭하여 배달 목록을 표시합니다.
1. 표시할 게재의 이름을 클릭하여 세부 사항을 표시합니다.

   ![](assets/s_ncs_user_detailled_report.png)

1. 탭을 선택하고 **[!UICONTROL Summary]** **[!UICONTROL Reports]** 링크를 클릭하여 게재와 관련된 보고서에 액세스합니다.

   ![](assets/s_ncs_user_detailled_report2.png)

   기본적으로 다음 보고서를 사용할 수 있습니다.

   * **[!UICONTROL Delivery throughput]** :전달 [처리량을 참조하십시오](#delivery-throughput).
   * **[!UICONTROL Sharing to social networks]** :소셜 [네트워크에](#sharing-to-social-networks)공유를 참조하십시오.
   * **[!UICONTROL Statistics on sharing activities]** :공유 [활동에](#statistics-on-sharing-activities)대한 통계를 참조하십시오.
   * **[!UICONTROL Hot clicks]** :핫 [클릭](#hot-clicks)참조
   * **[!UICONTROL Tracking statistics]** :추적 [통계 참조](#tracking-statistics)
   * **[!UICONTROL URLs and click streams]** :url을 [참조하고 스트림을](#urls-and-click-streams)클릭합니다.
   * **[!UICONTROL Tracking indicators]** :추적 [표시기를](#tracking-indicators)참조하십시오.
   * **[!UICONTROL Non-deliverables and bounces]** :비 [산출물 및 바운스를 참조하십시오](#non-deliverables-and-bounces).
   * **[!UICONTROL User activities]** :사용자 [활동을](#user-activities)참조하십시오.
   * **[!UICONTROL Delivery summary]** :배달 [요약을 참조하십시오](#delivery-summary).
   * **[!UICONTROL Subscription tracking]** :구독 [추적을](#subscription-tracking)참조하십시오.
   * **[!UICONTROL Delivery statistics]** :게재 [통계를](#delivery-statistics)참조하십시오.
   * **[!UICONTROL Breakdown of opens]** :의 [분류를](#breakdown-of-opens)참조하십시오.

## 지표 추적 {#tracking-indicators}

이 보고서는 전달 시 받는 사람의 행동을 추적하기 위한 주요 지표를 결합합니다. 전달 및 수신 통계, 열기 및 클릭스루 비율, 생성된 클릭 스트림, 웹 추적 및 소셜 네트워크에 활동 공유 등을 이용할 수 있습니다.

>[!NOTE]
>
>텍스트 형식의 이메일에 연결된 오류 여백으로 인해 메시지 열기를 기반으로 계산되는 값은 항상 예측됩니다. 지표들은 이 오차를 고려한다 **[!UICONTROL Distinct opens/Sum of opens for the population reached]** . 열림 추적에 대한 자세한 내용은 추적 [열기를](#tracking-opens-)참조하십시오.

![](assets/s_ncs_user_tracking_synth_report.png)

**[!UICONTROL 1. Delivery statistics]**

* **[!UICONTROL Messages to deliver]** :배달 분석 후 배달될 총 메시지 수입니다.
* **[!UICONTROL Success]** :성공적으로 처리된 메시지 수입니다.

**[!UICONTROL 2. Reception statistics]**

>[!NOTE]
>
>관련 비율은 성공적으로 전달된 메시지 수를 기준으로 계산됩니다.

* **[!UICONTROL Distinct opens for the population reached]** :메시지를 한 번 이상 연 대상 받는 사람 수 추계 구독 취소 링크 및 미러 페이지의 클릭이 고려됩니다.
* **[!UICONTROL Sum of opens for the population reached]** :대상화된 수신자의 총 열기 수 추정
* **[!UICONTROL Clicks on opt-out link]** :구독 취소 링크에 대한 클릭 수입니다.
* **[!UICONTROL Clicks on the mirror page link]** :미러 페이지에 대한 링크 클릭 수입니다. 고려하려면, 링크를 배달 마법사(추적된 URL)에서 이렇게 정의해야 합니다. 이 [페이지를](../../delivery/using/monitoring-a-delivery.md)참조하십시오.
* **[!UICONTROL Estimation of forwards]** :타깃팅된 받는 사람이 발송한 이메일 수 추정 이 값은 개별 사용자 수와 이메일을 클릭한 개별 받는 사람 수를 뺀 값으로 계산됩니다.

   >[!NOTE]
   >
   >개별 사용자와 타깃팅된 수신자 간의 차이에 대한 자세한 내용은 타깃팅된 개인/ [수신자를](#targeted-persons---recipients)참조하십시오.

**[!UICONTROL 3. Open and click-through rate]**

이 값 표는 인터넷 도메인별 배달, 열기, 클릭 및 원시 재활동의 분류를 보여줍니다. 다음 지표가 사용됩니다.

* **[!UICONTROL Sent]** :이 도메인에서 보낸 총 메시지 수입니다.
* **[!UICONTROL Complaints]** :받는 사람이 원하지 않는 것으로 보고된 이 도메인의 메시지 수입니다. 비율은 이 도메인에서 보낸 총 메시지 수를 기준으로 계산됩니다.
* **[!UICONTROL Opens]** :메시지를 한 번 이상 연 이 도메인의 타깃팅된 개별 받는 사람 수입니다. 비율은 이 도메인에서 보낸 총 메시지 수를 기준으로 계산됩니다.
* **[!UICONTROL Clicks]** :동일한 배달을 한 번 이상 클릭한 대상화된 받는 사람 수입니다. 비율은 이 도메인에서 보낸 총 메시지 수를 기준으로 계산됩니다
* **[!UICONTROL Raw reactivity]** :배달을 한 번 이상 클릭한 받는 사람 수의 백분율과 배달을 한 번 이상 연 받는 사람 수입니다.

>[!NOTE]
>
>이 보고서에 표시되는 도메인 이름은 큐브 수준에서 사용되는 항목별 목록에 정의됩니다. 기본 도메인을 변경하거나 추가하거나 제거하려면 항목별 목록을 편집하고 값과 별칭을 수정합니다. **[!UICONTROL Domains]** For more on this, refer to [this section](../../platform/using/managing-enumerations.md). 카테고리에는 항목별 목록의 값에 속하지 않는 도메인 이름이 포함되어 있습니다. **[!UICONTROL Others]**

**[!UICONTROL 4. Generated click streams]**

>[!NOTE]
>
>관련 비율은 성공적으로 전달된 메시지 수를 기준으로 계산됩니다.

* **[!UICONTROL Distinct clicks for the population reached]** :적어도 한 번 이상 배달을 클릭한 별개의 사람 수입니다.
* **[!UICONTROL Cumulated clicks]** :구독 취소 링크 및 미러 페이지를 제외하고 대상화된 수신자의 총 클릭 수입니다.
* **[!UICONTROL Recipient clicks]** :동일한 배달을 한 번 이상 클릭한 대상화된 받는 사람 수입니다.
* **[!UICONTROL Estimated recipient reactivity]** :배달에서 한 번 이상 클릭한 받는 사람 수와 배달을 한 번 이상 연 예상 받는 사람 수의 비율입니다. 옵트아웃 및 미러 페이지 링크 클릭은 고려되지 않습니다.

**[!UICONTROL 5. Web tracking]**

* **[!UICONTROL Visited pages]** :메시지 수신 후 방문한 웹 페이지 수입니다.
* **[!UICONTROL Transactions]** :메시지 수신에 따른 구매 횟수입니다.
* **[!UICONTROL Total amount]** :메시지 수신에 따른 총 구매 금액.
* **[!UICONTROL Average transaction amount]** :개별 배달 수신자가 구매한 평균 구매
* **[!UICONTROL Articles]** :배달 받는 사람이 구매한 아티클 수입니다.
* **[!UICONTROL Average count of articles per transaction]** :개별 수신자가 구매당 평균 항목 수입니다.
* **[!UICONTROL Average amount per message]** :메시지당 생성된 평균 구매 수량.

   >[!NOTE]
   >
   >방문한 페이지, 거래, 금액 또는 아티클을 고려하려면 웹 추적 태그를 일치하는 웹 페이지에 삽입해야 합니다. 웹 추적 구성은 [이 섹션에](../../configuration/using/about-web-tracking.md)설명되어 있습니다.

**[!UICONTROL 6. Sharing activities to email and social networks]**

이 섹션에는 각 소셜 네트워크에서 공유된 메시지 수가 표시됩니다. 자세한 내용은 소셜 네트워크에 [공유를 참조하십시오](#sharing-to-social-networks).

## URL 및 클릭 스트림 {#urls-and-click-streams}

이 보고서는 배달 후 방문한 페이지 목록을 보여줍니다.

![](assets/s_ncs_user_url_report.png)

다음을 선택하여 이 보고서의 컨텐츠를 구성할 수 있습니다.표시할 점수 차트, 시간 필터(작업 시작 이후 시작 후 처음 6시간 이상) 데이터 표시 모드(레이블별, URL, 범주별)에 대한 자세한 내용은 [이 페이지를](../../delivery/using/monitoring-a-delivery.md)참조하십시오. 을 **[!UICONTROL Refresh]** 클릭하여 선택을 확인합니다.

보고서의 상단 섹션에 다음 비율이 표시됩니다.

* **[!UICONTROL Reactivity]** :배달을 연 대상 받는 사람의 예상 수와 관련하여 배달을 클릭한 대상 받는 사람의 수입니다. 옵트아웃 링크 및 미러 페이지의 클릭은 고려되지 않습니다.

   >[!NOTE]
   >
   >열림 추적에 대한 자세한 내용은 추적 [열기를](#tracking-opens-)참조하십시오.

* **[!UICONTROL Distinct clicks]** :배달에서 한 번 이상(가입 해지 링크 및 미러 페이지 제외) 클릭한 별개의 사람 수입니다. 표시된 비율은 성공적으로 배달된 메시지 수를 기준으로 계산됩니다.
* **[!UICONTROL Cumulated clicks]** :대상화된 수신자의 총 클릭 수(가입 해지 링크 및 미러 페이지 제외). 표시된 비율은 성공적으로 전달된 메시지 수를 기준으로 계산됩니다.

**[!UICONTROL Platform average]** :각 비율(재활동, 고유 클릭 및 누적 클릭)에 따라 표시되는 이 평균 비율은 이전 6개월 동안 전송된 배달에 대해 계산됩니다. 동일한 유형 및 동일한 채널에서의 전달만 고려됩니다. 교정쇄는 제외됩니다.

중앙 테이블은 다음 정보를 제공합니다.

* **[!UICONTROL Clicks]** :링크당 누적 클릭 수.
* **[!UICONTROL Clicks (in %)]** :누적된 총 클릭 수와 관련하여 링크당 클릭 수 분류

**[!UICONTROL Breakdown of clicks in time]**

이 차트는 일별 누적 클릭 수 분류를 보여줍니다.

## 게재 요약 {#delivery-summary}

이 보고서는 배달에 대한 모든 주요 정보를 제공합니다.

![](assets/s_ncs_user_synth_report.png)

**[!UICONTROL Target population]**

이 섹션에는 다음 두 가지 지표가 있습니다.

* **[!UICONTROL Initial population]** :배달이 타깃팅한 총 받는 사람 수입니다.
* **[!UICONTROL Messages rejected by the rule]** :유형 규칙을 적용할 때 분석 중에 무시된 주소 수:주소 누락, 격리, 블랙리스트에 추가된 등 유형 규칙에 대한 자세한 내용은 이 [페이지를](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies)참조하십시오.

**[!UICONTROL Causes of exclusion]**

중간 차트는 분석 중에 거부된 메시지 규칙별 분류를 보여줍니다.

**[!UICONTROL Delivery statistics]**

이 섹션에는 다음 지표가 포함되어 있습니다.

* **[!UICONTROL Messages to be delivered]** :배달 분석 후 배달될 총 메시지 수입니다.
* **[!UICONTROL Success]** :성공적으로 처리된 메시지 수입니다. 연결된 비율은 배달할 메시지 수와 비례합니다.
* **[!UICONTROL Errors]** :배달 및 자동 반올림 처리 중에 누적된 총 오류 수입니다. 연결된 비율은 배달할 메시지 수와 비례합니다.
* **[!UICONTROL New quarantines]** :배달 실패 후 격리된 주소 수(사용자를 알 수 없음, 잘못된 도메인). 연결된 비율은 배달할 메시지 수와 비례합니다.

## 핫 클릭 {#hot-clicks}

이 보고서는 각 링크에 대한 클릭 비율의 메시지 내용(HTML 및/또는 텍스트)을 표시합니다. 개인화는 가입 해지 링크, 미러 페이지 링크 및 오퍼 링크를 모두 합산한 클릭 수에 고려하지만 보고서에 표시되지 않습니다.

>[!NOTE]
>
>게재에 오퍼(상호 작용)가 포함되어 있는 경우 보고서 위 부분에 오퍼에 대한 클릭 비율이 표시된 상자가 나타납니다.

![](assets/s_ncs_user_clic_report.png)

## 추적 통계 {#tracking-statistics}

이 보고서는 열기, 클릭 및 거래에 대한 통계를 제공합니다.

![](assets/s_ncs_user_stat_report.png)

게재의 마케팅 효과를 추적할 수 있습니다. 시간 간격(1시간, 3시간 또는 24시간 보기 등)을 변경하여 값이 표시되는 방식을 구성할 수 있습니다. 을 **[!UICONTROL Refresh]** 클릭하여 선택을 확인합니다.

이 보고서는 배달을 최대한 효율적으로 하는 데 필요한 시간을 표시하는 값 및 파레토 차트를 제공합니다. 다음 지표가 사용됩니다.

* **[!UICONTROL Opens]** :연 총 메시지 수의 비율에 도달하는 데 필요한 시간을 예상합니다. 텍스트 형식의 이메일은 고려되지 않습니다. 열림 추적에 대한 자세한 내용은 추적 [열기를](#tracking-opens-)참조하십시오.
* **[!UICONTROL Clicks]** :기록된 총 클릭 수의 비율에 도달하는 데 필요한 시간의 예상 옵트아웃 링크를 클릭해도 미러 페이지가 고려되지 않습니다.
* **[!UICONTROL Transactions]** :메시지 수신 후 총 트랜잭션 수의 백분율을 달성하는 데 필요한 시간입니다. 트랜잭션을 고려하려면 트랜잭션 유형 웹 추적 태그를 일치하는 웹 페이지에 삽입해야 합니다. 웹 추적 구성은 [이 섹션에](../../configuration/using/about-web-tracking.md)설명되어 있습니다.
