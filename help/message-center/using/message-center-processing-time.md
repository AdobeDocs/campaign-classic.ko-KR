---
title: 메시지 센터 처리 시간
seo-title: 메시지 센터 처리 시간
description: 메시지 센터 처리 시간
seo-description: null
page-status-flag: never-activated
uuid: 06aca2c2-33c0-4839-bee4-fd838c49ce76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: d1f591d2-95e8-4d99-bc60-955c96b532eb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 메시지 센터 처리 시간{#message-center-processing-time}

이 보고서는 실시간 큐와 관련된 기본 표시기를 표시합니다. 기술 관리자를 대상으로 하는 이 보고서는 제어 인스턴스의 **[!UICONTROL Monitoring]** 우주를 통해서도 액세스할 수 있습니다.

![](assets/mc_reports_2.png)

보고서의 경우와 마찬가지로 전체 통계 또는 특정 실행 인스턴스에 관련된 통계를 표시하도록 선택할 수 있습니다. **[!UICONTROL Message Center service level]** 채널별 및 특정 기간 동안 데이터를 필터링할 수도 있습니다. 섹션에 표시되는 표시기는 선택한 기간 동안 계산됩니다. **[!UICONTROL Indicators over the period]**

* **[!UICONTROL Average queuing time]** :메시지 센터에서 이벤트를 성공적으로 처리한 평균 시간입니다. 처리 시간만 고려됩니다.
* **[!UICONTROL Average message sending time (s)]** :메시지 센터에서 이벤트를 성공적으로 처리한 평균 시간입니다. 데이터 배달 시간만 고려됩니다.
* **[!UICONTROL Average processing time (s)]** :메시지 센터에서 이벤트를 성공적으로 처리한 평균 시간입니다. 계산은 처리 시간과 데이터 전송 시간을 고려합니다.
* **[!UICONTROL Maximum number of queued events]** :지정된 순간에 메시지 센터 큐에 있는 최대 이벤트 수입니다.
* **[!UICONTROL Minimum number of queued events]** :지정된 순간에 메시지 센터 큐에 있는 최소 이벤트 수입니다.
* **[!UICONTROL Average number of queued events]** :지정된 순간에 메시지 센터 큐에 있는 평균 이벤트 수입니다.

>[!NOTE]
>
>Adobe Campaign 배포 마법사에서 경고(주황색) 및 경고(빨간색) 표시기 임계값을 구성할 수 있습니다. 임계값 [모니터링을 참조하십시오](../../message-center/using/monitoring-thresholds.md).

