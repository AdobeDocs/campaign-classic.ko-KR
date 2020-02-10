---
title: 예약
seo-title: 예약
description: 예약
seo-description: null
page-status-flag: never-activated
uuid: e814b978-2edd-442e-9334-9633bc9ec63a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 093dbe8a-494f-4fe7-8614-3bf58486e34c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7c4e4c7d7433f782f810fdc2ecdeeedacd72b6c6

---


# 예약{#scheduler}

스케줄러는 **일정에** 의해 지정된 시간에 전환을 활성화하는 지속적인 작업입니다.

활동은 **[!UICONTROL Scheduler]** 예약된 시작으로 간주되어야 합니다. 차트 내의 활동 배치 규칙은 **[!UICONTROL Start]** 활동과 동일합니다. 이 활동에는 인바운드 전환이 없어야 합니다.

전체 시스템 성능이 저하되고 데이터베이스에 블록을 만들 수 있으므로 워크플로우를 15분 이상 실행하지 않는 것이 좋습니다.

워크플로우를 구축할 때는 분기당 두 개 이상의 **[!UICONTROL Scheduler]** 활동을 사용하지 마십시오. 자세한 내용은 다음을 참조하십시오.활동 [사용](../../workflow/using/workflow-best-practices.md#using-activities).

스케줄러는 전환의 활성화 일정을 정의합니다. 구성하려면 그래픽 개체를 두 번 클릭한 다음 **[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

마법사를 사용하여 활동의 빈도 및 유효 기간을 정의할 수 있습니다. 구성 단계는 다음과 같습니다.

1. 활성화 빈도를 선택하고 을 **[!UICONTROL Next]**&#x200B;클릭합니다.

   ![](assets/s_user_segmentation_scheduler2.png)

1. 정품 인증 시간 및 요일 이 단계의 매개 변수는 이전 단계에서 선택한 빈도에 따라 달라집니다. 하루에 여러 번 활동을 시작하도록 선택하는 경우 구성 옵션은 다음과 같습니다.

   ![](assets/s_user_segmentation_scheduler3.png)

1. 스케줄의 유효 기간을 정의하거나 실행할 횟수를 지정합니다.

   ![](assets/s_user_segmentation_scheduler4.png)

1. 구성을 확인하고 클릭하여 **[!UICONTROL Finish]** 저장합니다.

   ![](assets/s_user_segmentation_scheduler5.png)

스케줄러 활동을 사용하면 워크플로우가 동시에 실행되도록 할 수 있습니다. 예를 들어 스케줄러가 매시간마다 워크플로우 실행을 트리거하도록 할 수 있지만, 전체 워크플로우의 실행은 한 시간 이상 걸립니다. 워크플로우가 이미 실행 중인 경우 실행을 건너뛸 수 있습니다. 워크플로우의 동시 실행을 방지하는 방법에 대한 자세한 내용은 [이 페이지를](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-execution)참조하십시오.

워크플로우가 가져오기와 같은 장기 작업을 실행하는 경우 또는 잠시 동안 wfserver 모듈이 중지된 경우 몇 시간 후에 전환을 활성화할 수도 있습니다. 이 경우 스케줄러가 활성화한 작업의 실행을 특정 시간 범위로 제한해야 할 수 있습니다.
