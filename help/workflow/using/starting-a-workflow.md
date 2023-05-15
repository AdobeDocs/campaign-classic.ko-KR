---
product: campaign
title: 워크플로우 시작
description: 워크플로우를 시작하고 워크플로우 작업 도구 모음 및 마우스 오른쪽 단추 클릭 메뉴를 검색하는 방법을 알아봅니다
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 2%

---

# 워크플로우 시작 {#starting-a-workflow}



워크플로우는 항상 수동으로 시작됩니다. 시작되면 스케줄러 를 통해 지정된 정보에 따라 비활성 상태로 유지될 수 있습니다( 참조) [스케줄러](scheduler.md)) 또는 활동 예약을 참조하십시오.

타겟팅 워크플로우 실행(실행, 중지, 일시 중지 등)과 관련된 작업 is **비동기** 프로세스: 주문은 기록되며 서버가 적용되는 즉시 적용됩니다.

도구 모음에서 워크플로우 실행을 시작 및 추적할 수 있습니다.

에서 사용할 수 있는 옵션 목록 **[!UICONTROL Actions]** 메뉴 및 마우스 오른쪽 단추 클릭 메뉴가 아래에 자세히 설명되어 있습니다.

>[!IMPORTANT]
>
>연산자가 워크플로우(시작, 중지, 일시 중지 등)에서 작업을 수행할 때 작업이 바로 실행되지 않고 대신 큐에 배치되어 워크플로우에서 처리합니다 [워크플로우 모듈](architecture.md).

## 작업 도구 모음 {#actions-toolbar}

도구 모음 단추는 여기에 자세히 설명되어 있습니다 [섹션](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). 다음 **[!UICONTROL Actions]** 버튼을 사용하면 선택한 워크플로우에서 작업을 수행할 수 있는 추가 실행 옵션에 액세스할 수 있습니다. 를 사용할 수도 있습니다 **[!UICONTROL File > Actions]** 메뉴를 클릭하거나 워크플로우를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   이 작업을 통해 워크플로우 실행을 시작할 수 있습니다. 워크플로우인 **완료됨**, **편집 중** 또는 **일시 중지됨** 상태 변경 **시작됨**. 그런 다음 워크플로우 엔진이 이 워크플로우의 실행을 처리합니다. 워크플로우가 일시 중지된 경우에는 다시 시작되고, 그렇지 않으면 워크플로우가 시작부터 시작되고 초기 활동이 활성화됩니다.

   시작하는 것은 비동기 프로세스입니다. 요청이 저장되고 워크플로우 서버에 의해 가능한 한 빨리 처리됩니다.

* **[!UICONTROL Pause]**

   이 작업은 워크플로우의 상태를 로 설정합니다. **일시 중지됨**. 워크플로우를 다시 시작할 때까지 활동이 활성화되지 않습니다. 그러나 진행 중인 작업은 일시 중지되지 않습니다.

* **[!UICONTROL Stop]**

   이 작업은 현재 실행 중인 워크플로우를 중지합니다. 인스턴스의 상태가 **완료됨**. 진행 중인 작업이 가능한 경우 중지됩니다. 가져오기 및 SQL 쿼리는 즉시 취소됩니다.

   >[!IMPORTANT]
   >
   >워크플로우를 중지하는 것은 비동기 프로세스입니다. 요청이 등록되면 워크플로 서버나 서버가 진행 중인 작업을 취소합니다. 따라서 워크플로우 인스턴스를 중지하면 시간이 걸릴 수 있습니다. 특히 워크플로우가 여러 서버에서 실행 중인 경우 각 서버가 제어하여 진행 중인 작업을 취소해야 합니다. 문제가 발생하지 않도록 하려면 중지 작업이 완료될 때까지 기다렸다가 동일한 워크플로우에서 여러 중지 요청을 수행하지 마십시오.

* **[!UICONTROL Restart]**

   이 작업이 중지되고 워크플로우가 다시 시작됩니다. 대부분의 경우 보다 신속하게 다시 시작할 수 있습니다. 또한 일정 시간이 걸리는 중지 시 다시 시작을 자동화하는 것이 유용합니다. 워크플로우가 중지되는 경우 &#39;중지&#39; 명령을 사용할 수 없기 때문입니다.

   다음 **[!UICONTROL Start / Pause / Stop / Restart]** 작업은 도구 모음의 실행 아이콘을 통해 사용할 수도 있습니다. 자세한 정보는 이 [섹션](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow)을 참조하십시오.

* **[!UICONTROL Purge history]**

   이 작업을 통해 워크플로우 내역을 삭제할 수 있습니다. 자세한 내용은 [로그 제거](monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

   이 옵션을 사용하면 실제 모드와 대조적으로 시뮬레이션 모드에서 워크플로우를 시작할 수 있습니다. 즉, 이 모드를 활성화하면 데이터베이스나 파일 시스템에 영향을 주지 않는 활동만 실행됩니다(예: **[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]**&#x200B;등) 영향을 주는 활동(예: **[!UICONTROL Export]**, **[!UICONTROL Import]**&#x200B;등) 또한 그 다음(동일한 분기에 있음)도 실행되지 않습니다.

* **[!UICONTROL Execute pending tasks now]**

   이 작업을 수행하면 보류 중인 모든 작업을 가능한 한 빨리 시작할 수 있습니다. 특정 작업을 시작하려면 해당 활동을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Unconditional stop]**

   이 옵션은 워크플로우 상태를 **[!UICONTROL Finished]**. 이 작업은 몇 분 후에 일반 정지 프로세스가 실패하는 경우에만 마지막 수단으로 사용해야 합니다. 진행 중인 실제 워크플로우 작업이 없는 경우에만 무조건적 정지를 사용하십시오.

   >[!CAUTION]
   >
   >이 옵션은 전문가 사용자를 위해 예약되어 있습니다.

* **[!UICONTROL Save as template]**

   이 작업은 선택한 워크플로우를 기반으로 새 워크플로우 템플릿을 만듭니다. 저장할 폴더( **[!UICONTROL Folder]** 필드)만 로드하는 것입니다.

   다음 **[!UICONTROL Mass update of selected lines]** 및 **[!UICONTROL Merge selected lines]** 모든 옵션을 사용할 수 있는 범용 플랫폼 옵션 **[!UICONTROL Actions]** 메뉴 아래의 제품에서 사용할 수 있습니다. 자세한 정보는 이 [섹션](../../platform/using/updating-data.md)을 참조하십시오.

## 마우스 오른쪽 단추 클릭 메뉴 {#right-click-menu}

하나 이상의 워크플로우 활동을 선택한 경우 마우스 오른쪽 단추를 클릭하여 선택 사항에 따라 작업할 수 있습니다.

![](assets/contextual_menu.png)

마우스 오른쪽 단추 클릭 메뉴에서 다음 옵션을 사용할 수 있습니다.

**[!UICONTROL Open]**: 이 옵션을 사용하면 활동 속성에 액세스할 수 있습니다.

**[!UICONTROL Display logs:]** 이 옵션을 사용하면 선택한 활동에 대한 작업 실행 로그를 볼 수 있습니다. 을(를) 참조하십시오. [로그 표시](monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** 이 작업을 수행하면 보류 중인 작업을 가능한 한 빨리 시작할 수 있습니다.

**[!UICONTROL Workflow restart from a task:]** 이 옵션을 사용하면 이전에 이 활동에 저장된 결과를 사용하여 워크플로우를 다시 시작할 수 있습니다.

**[!UICONTROL Cut/Copy/Paste/Delete:]** 이러한 옵션을 사용하면 활동을 잘라내기, 복사, 붙여넣기 및 삭제할 수 있습니다.

**[!UICONTROL Copy as bitmap:]** 이 옵션을 사용하면 모든 활동의 스크린샷을 만들 수 있습니다.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** 다음 옵션도 **[!UICONTROL Advanced]** 활동 속성의 탭입니다. 자세한 내용은 [실행](advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** 워크플로우 변경 사항을 저장하거나 취소할 수 있습니다.

>[!NOTE]
>
>활동 그룹을 선택하고 이러한 명령 중 하나를 해당 그룹에 적용할 수 있습니다.

마우스 오른쪽 단추 클릭 메뉴도 여기에 자세히 설명되어 있습니다 [섹션](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).
