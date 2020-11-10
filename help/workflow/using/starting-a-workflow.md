---
title: 워크플로우 시작
description: 워크플로우 시작 방법 및 워크플로우 작업 도구 모음 및 마우스 오른쪽 단추 클릭 메뉴 검색
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 2%

---


# 워크플로우 시작 {#starting-a-workflow}

워크플로우는 항상 수동으로 시작됩니다. 시작될 때 스케줄러(스케줄러 참조) 또는 활동 예약을 통해 지정한 정보에 따라 비활성 상태로 유지될 수 [](../../workflow/using/scheduler.md)있습니다.

워크플로우 실행(실행, 중지, 일시 중지 등) 타깃팅과 관련된 작업 은 **비동기** 프로세스입니다.주문은 기록되며 서버가 해당 주문을 적용하는 즉시 적용됩니다.

도구 모음에서 워크플로우 실행을 시작 및 추적할 수 있습니다.

메뉴 및 마우스 오른쪽 단추 클릭 메뉴에서 사용할 수 있는 옵션 **[!UICONTROL Actions]** 목록은 아래에 자세히 설명되어 있습니다.

>[!IMPORTANT]
>
>연산자가 워크플로우(시작, 중지, 일시 중지 등)에서 작업을 수행하는 경우 작업은 바로 실행되지 않고 대신 [워크플로우 모듈에서](../../workflow/using/architecture.md)처리하기 위해 대기열에 배치됩니다.

## 작업 도구 모음 {#actions-toolbar}

도구 모음 단추는 이 [섹션에 자세히 설명되어 있습니다](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). 이 **[!UICONTROL Actions]** 단추를 사용하면 선택한 워크플로우에서 작업을 수행하기 위한 추가 실행 옵션에 액세스할 수 있습니다. 메뉴를 사용하거나 워크플로우를 마우스 오른쪽 버튼으로 클릭하고 선택할 수도 있습니다 **[!UICONTROL File > Actions]** **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   이 작업을 사용하면 워크플로우 실행을 시작할 수 있습니다.[ **마침**], [편집 **** ] **또는 [일시 중지됨** ]이 **진행 중인**&#x200B;작업 과정은 상태를 [시작됨]으로변경합니다. 그러면 워크플로우 엔진이 이 워크플로우의 실행을 처리합니다. 워크플로가 일시 중지되면 다시 시작되며, 그렇지 않으면 워크플로가 처음부터 시작되고 초기 활동이 활성화됩니다.

   시작은 비동기 프로세스입니다.요청이 저장되고 워크플로 서버에서 가능한 한 빨리 처리됩니다.

* **[!UICONTROL Pause]**

   이 작업은 워크플로우의 상태를 **일시 중지됨으로 설정합니다**. 워크플로가 다시 시작될 때까지 활동이 활성화되지 않습니다.하지만 진행 중인 작업이 일시 중지되지 않습니다.

* **[!UICONTROL Stop]**

   이 작업은 현재 실행 중인 워크플로우를 중지합니다. 인스턴스의 상태는 [마침]으로 **설정됩니다**. 진행 중인 작업이 가능한 경우 중지됩니다. 가져오기 및 SQL 쿼리는 즉시 취소됩니다.

   중지는 비동기 프로세스입니다. 요청이 등록되면 워크플로 서버나 서버가 진행 중인 작업을 취소합니다. 따라서 워크플로우 인스턴스를 중지하면 시간이 걸릴 수 있습니다. 특히 워크플로우가 여러 서버에서 실행 중인 경우 각 서버에서 제어하여 진행 중인 작업을 취소해야 합니다.

* **[!UICONTROL Restart]**

   이 작업이 중지되면 워크플로우가 다시 시작됩니다. 대부분의 경우 빠르게 다시 시작할 수 있습니다. 또한 정지에 일정한 시간이 걸릴 때 재시작을 자동화하는 것도 유용합니다.워크플로가 중지될 때 &#39;중지&#39; 명령을 사용할 수 없기 때문입니다.

   작업 **[!UICONTROL Start / Pause / Stop / Restart]** 은 도구 모음의 실행 아이콘을 통해서도 사용할 수 있습니다. 자세한 정보는 이 [섹션](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow)을 참조하십시오.

* **[!UICONTROL Purge history]**

   이 작업을 통해 워크플로우 내역을 삭제할 수 있습니다. 자세한 내용은 로그 [제거를 참조하십시오](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

   이 옵션을 사용하면 실제 모드와 반대로 시뮬레이션 모드에서 워크플로우를 시작할 수 있습니다. 즉, 이 모드를 활성화하면 데이터베이스나 파일 시스템에 영향을 주지 않는 작업만 실행됩니다(예: **[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]**&#x200B;등). 영향을 주는 활동(예: **[!UICONTROL Export]**, **[!UICONTROL Import]**&#x200B;등) 뿐만 아니라 그 다음(같은 분기)도 실행되지 않습니다.

* **[!UICONTROL Execute pending tasks now]**

   이 작업을 사용하면 모든 보류 중인 작업을 가능한 한 빨리 시작할 수 있습니다. 특정 작업을 시작하려면 해당 활동을 마우스 오른쪽 단추로 클릭하고 선택합니다 **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Unconditional stop]**

   이 옵션은 워크플로우 상태를 로 변경합니다 **[!UICONTROL Finished]**. 이 작업은 몇 분 후에 일반 정지 프로세스가 실패하는 경우에만 마지막 방법으로 사용해야 합니다. 진행 중인 실제 워크플로 작업이 없는 경우에만 무조건적인 중지를 사용하십시오.

   >[!CAUTION]
   >
   >이 옵션은 전문가 사용자용으로 예약되어 있습니다.

* **[!UICONTROL Save as template]**

   이 작업을 수행하면 선택한 워크플로우를 기반으로 새 워크플로우 템플릿이 만들어집니다. 저장할 폴더( **[!UICONTROL Folder]** 필드)를 지정해야 합니다.

   모든 메뉴 **[!UICONTROL Mass update of selected lines]** 에서 사용할 수 있는 일반 플랫폼 **[!UICONTROL Merge selected lines]** 옵션이 **[!UICONTROL Actions]** 있습니다. 자세한 정보는 이 [섹션](../../platform/using/updating-data.md)을 참조하십시오.

## 마우스 오른쪽 단추 클릭 메뉴 {#right-click-menu}

하나 이상의 워크플로우 활동을 선택한 경우 마우스 오른쪽 버튼을 클릭하여 선택한 내용에 따라 작업을 수행할 수 있습니다.

![](assets/contextual_menu.png)

마우스 오른쪽 단추 클릭 메뉴에서 다음 옵션을 사용할 수 있습니다.

**[!UICONTROL Open]**:이 옵션을 사용하면 활동 속성에 액세스할 수 있습니다.

**[!UICONTROL Display logs:]** 이 옵션을 사용하면 선택한 활동에 대한 작업 실행 로그를 볼 수 있습니다. 로그 [표시를 참조하십시오](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** 이 작업을 사용하면 가능한 한 빨리 보류 중인 작업을 시작할 수 있습니다.

**[!UICONTROL Workflow restart from a task:]** 이 옵션을 사용하면 이전에 이 활동에 대해 저장된 결과를 사용하여 워크플로우를 다시 시작할 수 있습니다.

**[!UICONTROL Cut/Copy/Paste/Delete:]** 이러한 옵션을 사용하면 활동을 잘라내기, 복사, 붙여넣기 및 삭제할 수 있습니다.

**[!UICONTROL Copy as bitmap:]** 이 옵션을 사용하면 모든 활동의 스크린샷을 만들 수 있습니다.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** 이러한 옵션은 활동 속성의 **[!UICONTROL Advanced]** 탭에서도 사용할 수 있습니다. 자세한 내용은 [Execution](../../workflow/using/advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** 워크플로우 변경 사항을 저장하거나 취소할 수 있습니다.

>[!NOTE]
>
>활동 그룹을 선택하고 이러한 명령 중 하나를 적용할 수 있습니다.

오른쪽 클릭 메뉴는 이 [섹션에 자세히 설명되어 있습니다](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).
