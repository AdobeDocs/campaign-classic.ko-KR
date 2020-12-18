---
solution: Campaign Classic
product: campaign
title: 워크플로우 시작
description: 워크플로우를 시작하고 워크플로우 작업 도구 모음 및 마우스 오른쪽 단추 클릭 메뉴를 검색하는 방법을 알아봅니다.
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 2%

---


# 워크플로우 시작 {#starting-a-workflow}

워크플로우는 항상 수동으로 시작됩니다. 시작할 때 스케줄러([스케줄러](../../workflow/using/scheduler.md) 참조) 또는 활동 예약을 통해 지정된 정보에 따라 비활성 상태로 유지될 수 있습니다.

타깃팅 워크플로우 실행과 관련된 작업(시작, 중지, 일시 중지 등) **비동기** 프로세스:주문은 기록되며 서버가 해당 주문을 적용하는 즉시 효력을 발휘합니다.

도구 모음에서 워크플로우 실행을 시작 및 추적할 수 있습니다.

**[!UICONTROL Actions]** 메뉴 및 마우스 오른쪽 단추 클릭 메뉴에 있는 옵션 목록은 아래에 자세히 나와 있습니다.

>[!IMPORTANT]
>
>연산자가 워크플로우(시작, 중지, 일시 중지 등)에서 작업을 수행할 때 작업은 바로 실행되지 않고 대신 대기열에 배치하여 [워크플로우 모듈](../../workflow/using/architecture.md)에서 처리합니다.

## 작업 도구 모음 {#actions-toolbar}

도구 모음 단추는 이 [섹션](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)에 자세히 설명되어 있습니다. **[!UICONTROL Actions]** 단추를 사용하면 선택한 워크플로우에서 작업을 수행하기 위한 추가 실행 옵션에 액세스할 수 있습니다. **[!UICONTROL File > Actions]** 메뉴를 사용하거나 워크플로우를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Actions]**&#x200B;을 선택할 수도 있습니다.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   이 작업을 통해 워크플로우의 실행을 시작할 수 있습니다.**완료**, **편집 중** 또는 **일시 중지됨**&#x200B;이(가) **시작**&#x200B;으로 상태를 변경하는 작업 과정입니다. 그러면 워크플로우 엔진이 이 워크플로우의 실행을 처리합니다. 워크플로가 일시 중지된 경우 다시 시작되며, 그렇지 않은 경우 워크플로우가 처음부터 시작되고 초기 활동이 활성화됩니다.

   시작은 비동기 프로세스입니다.요청이 저장되고 워크플로 서버에서 가능한 한 빨리 처리됩니다.

* **[!UICONTROL Pause]**

   이 작업은 워크플로우의 상태를 **Paused**&#x200B;로 설정합니다. 워크플로우가 다시 시작될 때까지 활동이 활성화되지 않습니다.그러나 진행 중인 작업이 일시 중지되지 않습니다.

* **[!UICONTROL Stop]**

   이 작업은 현재 실행 중인 워크플로우를 중지합니다. 인스턴스의 상태는 **Finished**&#x200B;로 설정됩니다. 진행 중인 작업이 가능한 경우 중지됩니다. 가져오기 및 SQL 쿼리는 즉시 취소됩니다.

   정지는 비동기 프로세스입니다. 요청이 등록되면 워크플로 서버 또는 서버가 진행 중인 작업을 취소합니다. 따라서 워크플로 인스턴스를 중지하면 시간이 걸릴 수 있습니다. 특히 워크플로가 여러 서버에서 실행 중인 경우 각 서버에서 진행 중인 작업을 취소하도록 제어해야 합니다.

* **[!UICONTROL Restart]**

   이 작업이 중지되면 워크플로우가 다시 시작됩니다. 대부분의 경우 빠르게 다시 시작할 수 있습니다. 또한 정지에 일정한 시간이 걸릴 때 재시작을 자동화하는 것도 유용합니다.워크플로가 중지될 때 &#39;중지&#39; 명령을 사용할 수 없기 때문입니다.

   **[!UICONTROL Start / Pause / Stop / Restart]** 작업은 도구 모음의 실행 아이콘을 통해 사용할 수도 있습니다. 자세한 정보는 이 [섹션](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow)을 참조하십시오.

* **[!UICONTROL Purge history]**

   이 작업을 통해 워크플로우 내역을 삭제할 수 있습니다. 자세한 내용은 [로그 제거](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs)를 참조하십시오.

* **[!UICONTROL Start in simulation mode]**

   이 옵션을 사용하면 실제 모드와 반대로 시뮬레이션 모드에서 워크플로우를 시작할 수 있습니다. 즉, 이 모드를 활성화하면 데이터베이스나 파일 시스템에 영향을 주지 않는 활동만 실행됩니다(예:**[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]** 등. 영향을 주는 활동(예:**[!UICONTROL Export]**, **[!UICONTROL Import]** 등) 이후의 모든 것(동일한 분기에 있음)은 실행되지 않습니다.

* **[!UICONTROL Execute pending tasks now]**

   이 작업을 사용하면 모든 보류 중인 작업을 가능한 한 빨리 시작할 수 있습니다. 특정 작업을 시작하려면 해당 활동을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Execute pending task(s) now]**&#x200B;을 선택합니다.

* **[!UICONTROL Unconditional stop]**

   이 옵션은 워크플로 상태를 **[!UICONTROL Finished]**&#x200B;으로 변경합니다. 이 작업은 몇 분 후에 일반 정지 프로세스가 실패하는 경우에만 마지막 방법으로 사용해야 합니다. 진행 중인 실제 워크플로 작업이 없는 경우에만 무조건적인 정지를 사용하십시오.

   >[!CAUTION]
   >
   >이 옵션은 전문가 사용자용으로 예약되어 있습니다.

* **[!UICONTROL Save as template]**

   이 작업을 수행하면 선택한 워크플로우를 기반으로 새 워크플로우 템플릿이 만들어집니다. 저장할 폴더(**[!UICONTROL Folder]** 필드)를 지정해야 합니다.

   **[!UICONTROL Mass update of selected lines]** 및 **[!UICONTROL Merge selected lines]** 옵션은 모든 **[!UICONTROL Actions]** 메뉴에서 사용할 수 있는 범용 플랫폼 옵션입니다. 자세한 정보는 이 [섹션](../../platform/using/updating-data.md)을 참조하십시오.

## {#right-click-menu} 메뉴를 마우스 오른쪽 단추로 클릭합니다.

하나 이상의 워크플로우 활동을 선택한 경우 마우스 오른쪽 버튼을 클릭하여 선택한 내용에 따라 작업을 수행할 수 있습니다.

![](assets/contextual_menu.png)

마우스 오른쪽 단추 클릭 메뉴에서 다음 옵션을 사용할 수 있습니다.

**[!UICONTROL Open]**:이 옵션을 사용하면 활동 속성에 액세스할 수 있습니다.

**[!UICONTROL Display logs:]** 이 옵션을 사용하면 선택한 활동에 대한 작업 실행 로그를 볼 수 있습니다. [로그 표시](../../workflow/using/monitoring-workflow-execution.md#displaying-logs)를 참조하십시오.

**[!UICONTROL Execute pending task(s) now:]** 이 작업을 사용하면 가능한 빨리 보류 중인 작업을 시작할 수 있습니다.

**[!UICONTROL Workflow restart from a task:]** 이 옵션을 사용하면 이전에 이 활동에 저장된 결과를 사용하여 워크플로우를 다시 시작할 수 있습니다.

**[!UICONTROL Cut/Copy/Paste/Delete:]** 이러한 옵션을 사용하면 활동을 잘라내거나 복사, 붙여넣기 및 삭제할 수 있습니다.

**[!UICONTROL Copy as bitmap:]** 이 옵션을 사용하면 모든 활동의 스크린샷을 만들 수 있습니다.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** 이러한 옵션은 활동 속성의  **[!UICONTROL Advanced]** 탭에서도 사용할 수 있습니다. 이 내용은 [실행](../../workflow/using/advanced-parameters.md#execution)에 자세히 설명되어 있습니다.

**[!UICONTROL Save / Cancel:]** 워크플로우에 대한 변경 내용을 저장하거나 취소할 수 있습니다.

>[!NOTE]
>
>활동 그룹을 선택하고 이러한 명령 중 하나를 해당 그룹에 적용할 수 있습니다.

마우스 오른쪽 단추 클릭 메뉴는 이 [섹션](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow)에도 자세히 설명되어 있습니다.
