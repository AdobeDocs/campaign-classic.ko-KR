---
title: 메시지 센터 서비스 수준
seo-title: 메시지 센터 서비스 수준
description: 메시지 센터 서비스 수준
seo-description: null
page-status-flag: never-activated
uuid: 8e363706-292b-40db-97bc-d41b41910556
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: e46a4e87-6c02-4b9c-bf6d-bb4e785e78fa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 메시지 센터 서비스 수준{#message-center-service-level}

이 보고서는 트랜잭션 메시지와 관련된 배달 통계와 오류 분류를 표시합니다. 오류 유형을 클릭하여 세부 사항을 표시할 수 있습니다. 기술 관리자를 대상으로 하는 이 보고서는 제어 인스턴스의 **[!UICONTROL Monitoring]** 우주를 통해서도 액세스할 수 있습니다.

![](assets/mc_reports_1.png)

이 보고서에서 전체 통계 또는 특정 실행 인스턴스에 상대적인 통계를 표시하도록 선택할 수 있습니다. 채널별 및 특정 기간 동안 데이터를 필터링할 수도 있습니다. 섹션에 표시되는 표시기는 선택한 기간 동안 계산됩니다. **[!UICONTROL Indicators over the period]**

* **[!UICONTROL Incoming (throughput event/h)]** :메시지 센터 큐에 입력된 평균 시간별 이벤트 수입니다.
* **[!UICONTROL Incoming (event vol)]** :메시지 센터 큐에 입력한 이벤트 수입니다.
* **[!UICONTROL Outgoing (throughput msg/h)]** :성공적인 나가는 메시지 센터 이벤트(배달로 전송)의 평균 시간별 수입니다.
* **[!UICONTROL Outgoing (msg vol)]** :성공적인 나가는 메시지 센터 이벤트 수(배달로 전송).
* **[!UICONTROL Average sending time (seconds)]** :성공적으로 처리된 이벤트에 대해 메시지 센터에서 보낸 평균 시간입니다. 계산은 처리 시간과 데이터 전송 시간을 고려합니다.
* **[!UICONTROL Error rate]** :메시지 센터 큐를 입력한 이벤트 수와 오류가 있는 이벤트 수 비교 다음 오류가 고려됩니다.라우팅 오류, 만료된 이벤트(대기열에 너무 긴 이벤트), 배달 오류, 배달(격리 등)에 의해 무시됨.

>[!NOTE]
>
>배포 마법사에서 경고(주황색) 및 경고(빨간색) 표시기 임계값을 구성할 수 있습니다. 임계값 [모니터링을 참조하십시오](../../message-center/using/monitoring-thresholds.md).

