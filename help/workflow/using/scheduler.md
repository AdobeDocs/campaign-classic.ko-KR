---
solution: Campaign Classic
product: campaign
title: 예약
description: 스케줄러 워크플로우 활동에 대해 자세히 알아보기
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 10%

---


# 예약 {#scheduler}

**스케줄러**&#x200B;은 일정에 지정된 시간에 전환을 활성화하는 지속적인 작업입니다.

**[!UICONTROL Scheduler]** 활동은 시작을 예약하는 것으로 생각해야 합니다. 차트 내에서의 활동 위치 지정 규칙은 **[!UICONTROL Start]** 활동과 동일합니다. 이 활동에는 인바운드 전환이 없어야 합니다.

## 권장사항 {#best-practices}

* 전체 시스템 성능을 저해할 수 있고 데이터베이스에서 블록을 만들기 때문에 15분마다 이상 워크플로우를 예약하지 마십시오.

* 워크플로우에서 분기당 두 개 이상의 **[!UICONTROL Scheduler]** 활동을 사용하지 마십시오. [활동 사용](../../workflow/using/workflow-best-practices.md#using-activities)을 참조하십시오.

* 스케줄러 활동을 사용하면 동시에 실행되는 여러 워크플로우가 있을 수 있습니다. 예를 들어 스케줄러가 매시간마다 워크플로우 실행을 트리거하도록 할 수 있지만, 때로 전체 워크플로우의 실행에는 1시간 이상이 걸립니다.

   워크플로우가 이미 실행 중인 경우 실행을 건너뛸 수 있습니다. 워크플로우의 동시 실행을 방지하는 방법에 대한 자세한 내용은 [이 페이지](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)를 참조하십시오.

* 워크플로우가 가져오기와 같은 장기 작업을 실행하는 경우 또는 잠시 동안 wfserver 모듈이 중지된 경우 몇 시간 후에 전환을 활성화할 수 있습니다. 이 경우 스케줄러가 활성화한 작업의 실행을 특정 시간 범위로 제한해야 할 수 있습니다.

## 스케줄러 작업 {#configuring-scheduler-activity} 구성

스케줄러는 전환의 활성화 일정을 정의합니다. 구성하려면 그래픽 개체를 두 번 클릭한 다음 **[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

마법사를 사용하여 활동의 빈도 및 유효성 기간을 정의할 수 있습니다. 구성 단계는 다음과 같습니다.

1. 활성화 빈도를 선택하고 **[!UICONTROL Next]**&#x200B;을 클릭합니다.

   ![](assets/s_user_segmentation_scheduler2.png)

1. 활성화 시간과 요일을 지정합니다. 이 단계의 매개 변수는 이전 단계에서 선택한 빈도에 따라 다릅니다. 하루에 여러 번 활동을 시작하도록 선택하는 경우 구성 옵션은 다음과 같습니다.

   ![](assets/s_user_segmentation_scheduler3.png)

1. 일정의 유효 기간을 정의하거나, 실행할 횟수를 지정합니다.

   ![](assets/s_user_segmentation_scheduler4.png)

1. 구성을 확인하고 **[!UICONTROL Finish]**&#x200B;을 클릭하여 저장합니다.

   ![](assets/s_user_segmentation_scheduler5.png)
