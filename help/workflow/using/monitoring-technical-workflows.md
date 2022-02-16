---
product: campaign
title: 기술 워크플로우 모니터링
description: 기술 워크플로우 모니터링
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 5e77d196-5c71-438e-8dae-10c6a6e4f29c
source-git-commit: 1a4fd75a90667e57149772497a7b1bd14b251db3
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 5%

---

# 기술 워크플로우 모니터링 {#monitoring-technical-workflows}

![](../../assets/common.svg)

기술 워크플로우를 모니터링해야 하며 실패한 경우 작업을 수행해야 합니다.

다양한 캠페인 프로세스를 모니터링하는 추가 방법은 [이 페이지](../../production/using/monitoring-guidelines.md).

## 인스턴스 모니터링 대시보드 {#instance-monitoring-dashboard}

인스턴스 모니터링 대시보드는 **[!UICONTROL Monitoring]** 탭.

![](assets/monitoring_technical_workflows1.png)

시스템 표시기 및 핵심 파일에서 빨간색으로 강조 표시된 표시기가 없는지 확인합니다. 이 경우 및 일부가 다음과 같은 경우 다음을 수행해야 합니다.

* 필요한 프로세스가 항상 실행 중인지 확인합니다.
* 프로세스 중 어느 것도 너무 오래되지 않았는지 확인합니다.
* 다른 프로세스의 로그 파일에 경고와 반복 오류가 없는지 확인합니다.

## 기술 워크플로우 {#technical-workflows}

기술 워크플로우는 **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

기술 워크플로우에 따라 아래 자세한 단계에 따라 모든 것이 예상대로 작동하는지 확인합니다.

각 기술 워크플로우가 수행해야 하는 작업을 더 잘 이해하려면 다음 문서를 참조하십시오 [섹션](about-technical-workflows.md).

대상 **[!UICONTROL Database Cleanup workflow (‘cleanup’)]**:

1. 다음을 확인하십시오. **[!UICONTROL Database Cleanup]** 워크플로우가 매일 성공적으로 실행되고 완료됩니다. 자세한 내용은 다음을 참조하십시오 [페이지](../../production/using/database-cleanup-workflow.md)..
1. 저널을 확인하여 경과 시간이 시간에 따라 상대적으로 일정하며 다른 워크플로우를 방해하지 않는지 확인합니다.

대상 **[!UICONTROL Tracking workflow (‘tracking’)]**:

추적 워크플로우가 예약된 대로(기본적으로 매시간) 실행되는지 그리고 저널에 반복 오류가 강조 표시되지 않는지 확인합니다. 자세한 정보는 이 [섹션](delivery.md)을 참조하십시오.

대상 **[!UICONTROL Deliverability update (‘deliverabilityUpdate’)]**:

1. 다음을 확인하십시오. **[!UICONTROL Deliverability update]** 워크플로우가 매일 성공적으로 실행되고 완료됩니다.
1. 규칙이 정기적으로 업데이트되는지 저널에서 확인합니다.

대상 **[!UICONTROL Campaign process ('operationMgt', 'deliveryMgt', ...)]**:

1. 아래에 있는 모든 워크플로우 보기 **[!UICONTROL Campaign process]** 폴더를 입력합니다. 자세한 정보는 이 [페이지](about-technical-workflows.md)를 참조하십시오.
1. 워크플로우가 예약됨으로 실행되며 저널에 재귀 오류가 강조 표시되지 않는지 확인합니다.

## 워크플로우 감독 {#workflow-supervision}

다음 **[!UICONTROL Workflow supervisors]** 그룹은 실패에 대해 계속 알고 있어야 하고 누가 제시간에 행동을 취할 수 있는지를 알고 있어야 하는 연산자를 포함해야 합니다.

![](assets/monitoring_technical_workflows3.png)

문제가 발생할 경우 경고를 생성하여 올바른 그룹으로 보내야 합니다.

각 연산자에 올바른 이메일 주소가 있는지 확인합니다.

일별 데이터 가져오기와 같이 플랫폼이 계속 작동하도록 하기 위해 실행해야 하는 모든 워크플로우는 &quot;프로덕션&quot;(확인란)으로 선언되고 굵게 표시됩니다.

## 워크플로우 유지 관리 목록 {#workflow-maintenance-list}

모든 사용자 지정 기술 워크플로우는 다음을 포함하는 워크시트에 문서화해야 합니다.

* 워크플로우의 이름 및 위치입니다.
* 목적.
* 일정 및 종속성.
* 모니터링을 담당하는 연산자입니다.
* 오류 발생 시 수행할 작업에 대한 지침입니다.

![](assets/monitoring_technical_workflows4.png)

## 모니터링 계획 및 자동화 {#planning-and-automation-of-monitoring}

계획 워크플로우 모니터링은 효율성을 향상시킵니다. 일부 작업은 매일 수행해야 하는 반면 다른 작업은 주별 또는 월별 작업을 수행할 수 있습니다.

반복으로 명명된 폴더에 워크플로우를 설정하고 실행 일정별로 정렬하면 모니터링 효율성이 향상됩니다.

모니터링 자동화는 리소스 오버헤드를 줄이고 작업이 적절한 빈도로 예약되도록 합니다.

특정 작업이 실패하거나 중요한 테이블이 너무 커질 때마다 이메일을 보내는 모니터링 워크플로우를 작성할 수 있습니다.

기능 영역 또는 시스템 전체의 모든 워크플로우를 모니터링할 수 있도록 보기를 만들 수 있습니다.

Adobe Campaign 작업이나 보고서 기능을 사용하여 항상 최신 상태로 주문형 설명서를 작성할 수도 있습니다.
