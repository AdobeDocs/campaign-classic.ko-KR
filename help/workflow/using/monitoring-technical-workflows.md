---
solution: Campaign Classic
product: campaign
title: 기술 워크플로우 모니터링
description: 기술 워크플로우 모니터링
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 8%

---


# 기술 워크플로우 모니터링 {#monitoring-technical-workflows}

기술 워크플로우는 모니터링되어야 하며 작업이 실패할 때 조치를 취해야 합니다.

다른 캠페인 프로세스를 모니터링하는 추가 방법은 [이 페이지](../../production/using/monitoring-guidelines.md)에 있습니다.

## 인스턴스 모니터링 대시보드 {#instance-monitoring-dashboard}

인스턴스 모니터링 대시보드는 **[!UICONTROL Monitoring]** 탭을 통해 액세스할 수 있습니다.

![](assets/monitoring_technical_workflows1.png)

시스템 표시기 및 핵심 파일에서 빨간색으로 강조 표시된 표시기가 없는지 확인합니다. 이러한 경우에 일부 사용자는 다음을 수행해야 합니다.

* 필요한 프로세스가 항상 실행되고 있는지 확인합니다.
* 모든 절차가 너무 오래되지 않았는지 확인하고
* 다른 프로세스의 로그 파일에 경고와 반복적인 오류가 없는지 확인합니다.

## 기술 워크플로우 {#technical-workflows}

기술 워크플로우는 **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**&#x200B;에서 사용할 수 있습니다.

기술 워크플로우에 따라 아래 절차에 따라 모든 것이 예상대로 작동되는지 확인하십시오.

각 기술 워크플로우의 기능을 더 잘 이해하려면 이 [섹션](../../workflow/using/about-technical-workflows.md)을 참조하십시오.

**[!UICONTROL Database Cleanup workflow (‘cleanup’)]**&#x200B;의 경우:

1. **[!UICONTROL Database Cleanup]** 작업 과정이 매일 성공적으로 실행되고 완료되는지 확인합니다. 자세한 정보는 이 [페이지](../../workflow/using/delivery.md)를 참조하십시오.
1. 저널을 통해 경과 시간이 시간에 따라 상대적으로 일정하며 다른 워크플로우에 영향을 주지 않는지 확인합니다.
1. 자세한 내용은 이 [페이지](../../production/using/database-cleanup-workflow.md)를 확인하십시오.

**[!UICONTROL Tracking workflow (‘tracking’)]**&#x200B;의 경우:

추적 워크플로우가 예약대로(기본적으로 매 시간마다) 실행되고 저널이 반복 오류를 강조 표시하지 않는지 확인합니다. 자세한 정보는 이 [섹션](../../workflow/using/delivery.md)을 참조하십시오.

**[!UICONTROL Deliverability update (‘deliverabilityUpdate’)]**&#x200B;의 경우:

1. **[!UICONTROL Deliverability update]** 작업 과정이 매일 성공적으로 실행되고 완료되는지 확인합니다. 자세한 정보는 이 [페이지](../../workflow/using/delivery.md)를 참조하십시오.
1. 규칙이 정기적으로 업데이트되고 있는지 저널에서 확인합니다.

**[!UICONTROL Campaign process ('operationMgt', 'deliveryMgt', ...)]**&#x200B;의 경우:

1. **[!UICONTROL Campaign process]** 폴더 아래에 있는 모든 워크플로우를 확인합니다. 자세한 정보는 이 [페이지](../../workflow/using/about-technical-workflows.md)를 참조하십시오.
1. 워크플로우가 예약대로 실행되고 저널에 반복 오류가 강조 표시되지 않는지 확인합니다.

## 워크플로 감독 {#workflow-supervision}

**[!UICONTROL Workflow supervisors]** 그룹에는 실패에 대한 정보를 유지해야 하고 제때에 조치를 취할 수 있는 연산자가 포함되어야 합니다.

![](assets/monitoring_technical_workflows3.png)

문제가 발생할 경우 경고를 생성하여 올바른 그룹으로 보내야 합니다.

각 연산자의 이메일 주소가 올바른지 확인하십시오.

일일 데이터 가져오기 같은 플랫폼을 계속 작동하도록 하기 위해 실행 중인 모든 워크플로우는 &quot;프로덕션&quot;(확인란)으로 선언되고 굵게 표시되어야 합니다.

## 워크플로 유지 관리 목록 {#workflow-maintenance-list}

모든 사용자 지정 기술 워크플로우는 다음을 포함하는 워크시트에 문서화해야 합니다.

* 워크플로우의 이름 및 위치.
* 목적.
* 예약 및 종속성.
* 모니터링 담당 연산자
* 오류 발생 시 수행할 작업에 대한 지침입니다.

![](assets/monitoring_technical_workflows4.png)

## 모니터링 계획 및 자동화 {#planning-and-automation-of-monitoring}

워크플로우 모니터링을 계획하면 효율성이 향상됩니다. 일부 작업은 매일 수행해야 하고 다른 작업은 주별 또는 월별 중에 수행할 수 있습니다.

반복별로 이름이 지정된 폴더의 워크플로우를 설정하고 실행 예약별로 정렬하면 모니터링 효율성이 높아집니다.

모니터링 자동화를 통해 리소스 오버헤드를 줄이고 적절한 빈도로 작업을 예약할 수 있습니다.

특정 작업이 실패하거나 중요한 테이블이 너무 클 때마다 이메일을 보내는 모니터링 워크플로우를 만들 수 있습니다.

기능 영역 또는 시스템 전체 전체의 모든 워크플로우를 모니터링할 수 있도록 보기를 만들 수 있습니다.

Adobe Campaign 작업 또는 보고서 기능을 사용하여 언제든지 최신 On-Demand 문서를 작성할 수도 있습니다.
