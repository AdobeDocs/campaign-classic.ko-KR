---
product: campaign
title: 메시지 센터 처리 시간
description: 메시지 센터 처리 시간 보고서에 대해 자세히 알아보기
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 4%

---

# 메시지 센터 처리 시간 {#message-center-processing-time}



이 보고서에는 실시간 대기열과 관련된 주요 지표가 표시됩니다.

기술 관리자를 대상으로 하는 이 보고서는 **[!UICONTROL Monitoring]** 컨트롤 인스턴스의 탭입니다.

![](assets/mc_reports_2.png)

다음과 같습니다. **[!UICONTROL Message Center service level]** 보고서에서는 전체 통계를 표시하거나 특정 실행 인스턴스와 관련된 통계를 표시하도록 선택할 수 있습니다. 또한 특정 기간 동안 채널 및 을 기준으로 데이터를 필터링할 수도 있습니다.

다음에 표시되는 표시기 **[!UICONTROL Indicators over the period]** 섹션은 선택한 기간 동안 계산됩니다.

* **[!UICONTROL Average queuing time]** : 성공적으로 처리된 이벤트가 메시지 센터에서 소비된 평균 시간입니다. 처리 시간만 고려됩니다.
* **[!UICONTROL Average message sending time (s)]** : 성공적으로 처리된 이벤트가 메시지 센터에서 소비된 평균 시간입니다. mta 게재 시간만 고려합니다.
* **[!UICONTROL Average processing time (s)]** : 성공적으로 처리된 이벤트가 메시지 센터에서 소비된 평균 시간입니다. 계산에는 처리 시간과 mta 전송 시간이 고려됩니다.
* **[!UICONTROL Maximum number of queued events]** : 지정된 시점에 메시지 센터 큐에 있는 최대 이벤트 수입니다.
* **[!UICONTROL Minimum number of queued events]** : 지정된 시점에 메시지 센터 큐에 있는 최소 이벤트 수입니다.
* **[!UICONTROL Average number of queued events]** : 지정된 시점에 메시지 센터 대기열에 있는 평균 이벤트 수입니다.

>[!NOTE]
>
>경고(주황색) 및 경고(빨간색) 표시기 임계값은 Adobe Campaign 배포 마법사에서 구성할 수 있습니다. 을(를) 참조하십시오 [임계값 모니터링](../../message-center/using/additional-configurations.md#monitoring-thresholds).
