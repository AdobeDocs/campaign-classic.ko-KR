---
product: campaign
title: 메시지 센터 서비스 수준
description: 메시지 센터 서비스 수준 보고서에 대해 자세히 알아보기
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 3%

---

# 메시지 센터 서비스 수준 {#message-center-service-level}



이 보고서에는 트랜잭션 메시지와 관련된 게재 통계와 오류 분류가 표시됩니다. 오류 유형을 클릭하여 세부 정보를 표시할 수 있습니다.

기술 관리자를 대상으로 하는 이 보고서는 컨트롤 인스턴스의 **[!UICONTROL Monitoring]** 탭을 통해서도 액세스할 수 있습니다.

![](assets/mc_reports_1.png)

이 보고서에서 전체 통계 또는 특정 실행 인스턴스와 관련된 통계를 표시하도록 선택할 수 있습니다. 또한 특정 기간 동안 채널 및 을 기준으로 데이터를 필터링할 수도 있습니다.

**[!UICONTROL Indicators over the period]** 섹션에 표시된 지표는 선택한 기간 동안 계산됩니다.

* **[!UICONTROL Incoming (throughput event/h)]** : 메시지 센터 큐에 입력된 평균 시간당 이벤트 수입니다.
* **[!UICONTROL Incoming (event vol)]** : 메시지 센터 큐에 입력된 이벤트 수입니다.
* **[!UICONTROL Outgoing (throughput msg/h)]** : 배달에서 보낸 성공한 송신 메시지 센터 이벤트의 평균 시간당 수입니다.
* **[!UICONTROL Outgoing (msg vol)]** : 배달에서 보낸 성공한 송신 메시지 센터 이벤트 수입니다.
* **[!UICONTROL Average sending time (seconds)]** : 메시지 센터에서 성공적으로 처리된 이벤트에 대한 평균 체류 시간입니다. 계산에는 처리 시간과 mta 전송 시간이 고려됩니다.
* **[!UICONTROL Error rate]** : 메시지 센터 대기열에 입력한 이벤트 수와 비교하여 오류가 있는 이벤트 수입니다. 라우팅 오류, 만료된 이벤트(큐에 너무 오래 있는 이벤트), 게재 오류, 게재에서 무시된 오류(격리 등) 등이 고려됩니다.

>[!NOTE]
>
>경고(주황색) 및 경고(빨간색) 표시기 임계값은 배포 마법사에서 구성할 수 있습니다. [임계값 모니터링](../../message-center/using/additional-configurations.md#monitoring-thresholds)을 참조하세요.
