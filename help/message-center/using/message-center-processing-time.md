---
product: campaign
title: 메시지 센터 처리 시간
description: 메시지 센터 처리 시간 보고서에 대해 자세히 알아보기
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# 메시지 센터 처리 시간 {#message-center-processing-time}



이 보고서에는 실시간 대기열과 관련된 주요 지표가 표시됩니다.

기술 관리자를 대상으로 하는 이 보고서는 컨트롤 인스턴스의 **[!UICONTROL Monitoring]** 탭을 통해서도 액세스할 수 있습니다.

![](assets/mc_reports_2.png)

**[!UICONTROL Message Center service level]** 보고서와 마찬가지로 전체 통계 또는 특정 실행 인스턴스와 관련된 통계를 표시하도록 선택할 수 있습니다. 또한 특정 기간 동안 채널 및 을 기준으로 데이터를 필터링할 수도 있습니다.

**[!UICONTROL Indicators over the period]** 섹션에 표시된 지표는 선택한 기간 동안 계산됩니다.

* **[!UICONTROL Average queuing time]** : 이벤트를 성공적으로 처리한 메시지 센터에서 보낸 평균 시간입니다. 처리 시간만 고려됩니다.
* **[!UICONTROL Average message sending time (s)]** : 이벤트를 성공적으로 처리한 메시지 센터에서 보낸 평균 시간입니다. mta 게재 시간만 고려합니다.
* **[!UICONTROL Average processing time (s)]** : 이벤트를 성공적으로 처리한 메시지 센터에서 보낸 평균 시간입니다. 계산에는 처리 시간과 mta 전송 시간이 고려됩니다.
* **[!UICONTROL Maximum number of queued events]** : 지정된 시점에 메시지 센터 큐에 있는 최대 이벤트 수입니다.
* **[!UICONTROL Minimum number of queued events]** : 지정된 시점에 메시지 센터 큐에 있는 최소 이벤트 수입니다.
* **[!UICONTROL Average number of queued events]** : 지정된 시점에 메시지 센터 큐에 있는 평균 이벤트 수입니다.

>[!NOTE]
>
>경고(주황색) 및 경고(빨간색) 표시기 임계값은 Adobe Campaign 배포 마법사에서 구성할 수 있습니다. [임계값 모니터링](../../message-center/using/additional-configurations.md#monitoring-thresholds)을 참조하세요.
