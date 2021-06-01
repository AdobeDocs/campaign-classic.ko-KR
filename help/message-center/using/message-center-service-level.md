---
solution: Campaign Classic
product: campaign
title: 메시지 센터 서비스 수준
description: 메시지 센터 서비스 수준 보고서에 대해 자세히 알아보십시오.
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
source-git-commit: d39b15b0efc6cbd6ab24e074713be6f8fc90e5fc
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 3%

---

# 메시지 센터 서비스 수준 {#message-center-service-level}

이 보고서는 트랜잭션 메시지와 관련된 게재 통계 및 오류 분류를 표시합니다. 오류 유형을 클릭하여 세부 정보를 표시할 수 있습니다.

기술 관리자를 대상으로 하는 이 보고서는 제어 인스턴스의 **[!UICONTROL Monitoring]** 탭을 통해 액세스할 수도 있습니다.

![](assets/mc_reports_1.png)

이 보고서에서 전체 통계 또는 특정 실행 인스턴스에 대한 상대적 통계를 표시하도록 선택할 수 있습니다. 채널별로 및 특정 기간 동안 데이터를 필터링할 수도 있습니다.

**[!UICONTROL Indicators over the period]** 섹션에 표시되는 표시기는 선택한 기간 동안 계산됩니다.

* **[!UICONTROL Incoming (throughput event/h)]** :메시지 센터 큐에 입력된 평균 시간별 이벤트 수
* **[!UICONTROL Incoming (event vol)]** :메시지 센터 큐에 입력한 이벤트 수입니다.
* **[!UICONTROL Outgoing (throughput msg/h)]** :성공적으로 보내는 메시지 센터 이벤트(게재에서 보낸)의 평균 시간별 수입니다.
* **[!UICONTROL Outgoing (msg vol)]** :발신 성공 메시지 센터 이벤트 수(게재에서 전송됨).
* **[!UICONTROL Average sending time (seconds)]** :성공적으로 처리된 이벤트에 대한 메시지 센터에서 보낸 평균 시간입니다. 계산에는 처리 시간 및 데이터 전송 시간이 고려됩니다.
* **[!UICONTROL Error rate]** :오류가 있는 이벤트 수를 메시지 센터 큐에 입력한 이벤트 수와 비교한 것입니다. 다음 오류가 고려됩니다.라우팅 오류, 만료된 이벤트(큐에 너무 오래 있는 이벤트), 게재 오류, 게재에 의해 무시된 배달(격리 등)

>[!NOTE]
>
>배포 마법사에서 경고(주황색) 및 경고(빨간색) 표시기 임계값을 구성할 수 있습니다. [임계값 모니터링](../../message-center/using/additional-configurations.md#monitoring-thresholds)을 참조하십시오.
