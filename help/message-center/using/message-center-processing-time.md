---
product: campaign
title: 메시지 센터 처리 시간
description: 메시지 센터 처리 시간 보고서에 대해 자세히 알아보십시오 .
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# 메시지 센터 처리 시간 {#message-center-processing-time}

![](../../assets/v7-only.svg)

이 보고서에는 실시간 큐와 관련된 기본 표시기가 표시됩니다.

기술 관리자를 대상으로 하는 이 보고서는 **[!UICONTROL Monitoring]** 탭에서 사용할 수 있습니다.

![](assets/mc_reports_2.png)

그냥 **[!UICONTROL Message Center service level]** 보고서에서 전체 통계 또는 특정 실행 인스턴스에 대한 상대적 통계를 표시하도록 선택할 수 있습니다. 채널별로 및 특정 기간 동안 데이터를 필터링할 수도 있습니다.

에 표시되는 표시기 **[!UICONTROL Indicators over the period]** 섹션은 선택한 기간 동안 계산됩니다.

* **[!UICONTROL Average queuing time]** : 메시지 센터에서 이벤트를 성공적으로 처리한 평균 시간입니다. 처리 시간만 고려합니다.
* **[!UICONTROL Average message sending time (s)]** : 메시지 센터에서 이벤트를 성공적으로 처리한 평균 시간입니다. mta 배달 시간만 고려합니다.
* **[!UICONTROL Average processing time (s)]** : 메시지 센터에서 이벤트를 성공적으로 처리한 평균 시간입니다. 계산에는 처리 시간 및 데이터 전송 시간이 고려됩니다.
* **[!UICONTROL Maximum number of queued events]** : 지정된 시간에 메시지 센터 큐에 있는 최대 이벤트 수입니다.
* **[!UICONTROL Minimum number of queued events]** : 지정된 시간에 메시지 센터 큐에 있는 최소 이벤트 수입니다.
* **[!UICONTROL Average number of queued events]** : 지정된 시간에 메시지 센터 큐에 있는 평균 이벤트 수입니다.

>[!NOTE]
>
>Adobe Campaign 배포 마법사에서 경고(주황색) 및 경고(빨간색) 표시기 임계값을 구성할 수 있습니다. 을(를) 참조하십시오. [임계값 모니터링](../../message-center/using/additional-configurations.md#monitoring-thresholds).
