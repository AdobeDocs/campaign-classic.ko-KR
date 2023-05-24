---
product: campaign
title: 예약
description: 예약 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 30a9bd2a-afb1-481c-ab5f-5acebd9cbb5a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 10%

---

# 예약 {#scheduler}



다음 **스케줄러** 은 예약에 의해 지정된 시간에 전환을 활성화하는 영구 작업입니다.

**[!UICONTROL Scheduler]** 활동은 시작을 예약하는 것으로 생각해야 합니다. 차트 내에서의 활동 위치 지정 규칙은 **[!UICONTROL Start]** 활동과 동일합니다. 이 활동에는 인바운드 전환이 없어야 합니다.

## 모범 사례 {#best-practices}

* 워크플로우가 전체 시스템 성능을 저해하고 데이터베이스에 블록을 만들 수 있으므로 워크플로우를 15분마다 이상 실행하도록 예약하지 마십시오.

* 두 개 이상 사용하지 않음 **[!UICONTROL Scheduler]** 워크플로우의 분기별 활동. 다음을 참조하십시오 [활동 사용](workflow-best-practices.md#using-activities).

* 예약 활동을 사용하면 워크플로우가 여러 번 동시에 실행될 수 있습니다. 예를 들어 스케줄러가 한 시간마다 워크플로우 실행을 트리거하도록 할 수 있지만 경우에 따라 전체 워크플로우를 실행하는 데 한 시간 이상이 걸립니다.

   워크플로우가 이미 실행 중인 경우 실행을 건너뛸 수 있습니다. 워크플로우의 동시 실행을 방지하는 방법에 대한 자세한 내용은 다음을 참조하십시오. [이 페이지](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions).

* 워크플로우가 가져오기 와 같은 장기 작업을 실행하거나 wfserver 모듈이 잠시 중지된 경우 몇 시간 후에 전환을 활성화할 수 있습니다. 이 경우, 스케줄러가 활성화한 태스크의 실행을 일정 시간 범위로 제한할 필요가 있을 수 있다.

## 스케줄러 활동 구성 {#configuring-scheduler-activity}

스케줄러는 전환의 활성화 일정을 정의합니다. 이를 구성하려면 그래픽 개체를 두 번 클릭한 다음 을 클릭합니다 **[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

마법사를 사용하여 활동의 빈도와 유효 기간을 정의할 수 있습니다. 구성 단계는 다음과 같습니다.

1. 활성화 빈도를 선택하고 **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_scheduler2.png)

1. 활성화 시간 및 일을 지정합니다. 이 단계의 매개 변수는 이전 단계에서 선택한 빈도에 따라 다릅니다. 하루에 여러 번 활동을 시작하도록 선택하는 경우 구성 옵션은 다음과 같습니다.

   ![](assets/s_user_segmentation_scheduler3.png)

1. 일정의 유효 기간을 정의하거나 실행할 횟수를 지정합니다.

   ![](assets/s_user_segmentation_scheduler4.png)

1. 구성을 확인하고 **[!UICONTROL Finish]** 저장.

   ![](assets/s_user_segmentation_scheduler5.png)
