---
product: campaign
title: 워크플로우 시작
description: 워크플로우를 시작하고 워크플로우 작업 을 검색하는 방법 도구 모음 및 마우스 오른쪽 버튼 클릭 메뉴
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 2%

---

# 워크플로우 시작 {#starting-a-workflow}



워크플로우는 항상 수동으로 시작됩니다. 그러나 시작되면 스케줄러를 통해 지정된 정보에 따라 비활성 상태로 유지될 수 있습니다(참조) [스케줄러](scheduler.md)) 또는 활동 일정 조정.

타겟팅 워크플로우 실행(실행, 중지, 일시 중지 등)과 관련된 작업 은(는) **비동기** 프로세스: 주문이 기록되며 서버가 주문을 적용할 수 있는 즉시 적용됩니다.

도구 모음을 사용하여 워크플로우 실행을 시작하고 추적할 수 있습니다.

에서 사용할 수 있는 옵션 목록 **[!UICONTROL Actions]** 메뉴 및 마우스 오른쪽 버튼 클릭 메뉴는 아래에 자세히 설명되어 있습니다.

>[!IMPORTANT]
>
>운영자가 워크플로우에서 작업(시작, 중지, 일시 중지 등)을 수행할 때 작업이 즉시 실행되지 않고 대신 를 통해 처리되도록 큐에 배치됩니다. [워크플로 모듈](architecture.md).

## 작업 도구 모음 {#actions-toolbar}

도구 모음 단추는 다음에서 자세히 설명합니다. [섹션](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). 다음 **[!UICONTROL Actions]** 버튼을 사용하면 선택한 워크플로우에 적용되는 추가 실행 옵션에 액세스할 수 있습니다. 다음을 사용할 수도 있습니다 **[!UICONTROL File > Actions]** 메뉴 또는 워크플로를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   이 작업을 사용하면 다음과 같은 워크플로우 실행을 시작할 수 있습니다. **완료됨**, **편집 중** 또는 **일시 중지됨** 상태를 다음으로 변경 **시작됨**. 그런 다음 워크플로우 엔진이 이 워크플로우의 실행을 처리합니다. 워크플로우가 일시 중지된 경우에는 다시 시작되고, 그렇지 않으면 워크플로우가 처음부터 시작되고 초기 활동이 활성화됩니다.

   시작은 비동기 프로세스입니다. 요청이 저장되고 워크플로우 서버에서 가능한 한 빨리 처리됩니다.

* **[!UICONTROL Pause]**

   이 작업은 워크플로우의 상태를 다음으로 설정합니다. **일시 중지됨**. 워크플로우가 다시 시작될 때까지 활동이 활성화되지 않지만 진행 중인 작업은 일시 중지되지 않습니다.

* **[!UICONTROL Stop]**

   이 작업은 현재 실행 중인 워크플로우를 중지합니다. 인스턴스의 상태가 다음으로 설정됨 **완료됨**. 진행 중인 작업은 가능한 경우 중지됩니다. 가져오기 및 SQL 쿼리가 즉시 취소됩니다.

   >[!IMPORTANT]
   >
   >워크플로를 중지하는 것은 비동기 프로세스입니다. 요청이 등록된 다음 워크플로 서버 또는 서버가 진행 중인 작업을 취소합니다. 따라서 워크플로 인스턴스를 중지하는 데 시간이 걸릴 수 있습니다. 특히 워크플로가 여러 서버에서 실행 중인 경우 각 서버에서 진행 중인 작업을 취소하도록 제어해야 합니다. 문제가 발생하지 않도록 하려면 중지 작업이 완료될 때까지 기다린 후 동일한 워크플로우에서 여러 중지 요청을 수행하지 마십시오.

* **[!UICONTROL Restart]**

   이 작업은 중지된 후 워크플로우를 다시 시작합니다. 대부분의 경우 이를 통해 보다 빠르게 다시 시작할 수 있습니다. 중지하는 데 일정 시간이 걸리는 경우 다시 시작을 자동화하는 것도 유용합니다. 워크플로우를 중지하는 동안에는 &#39;중지&#39; 명령을 사용할 수 없기 때문입니다.

   다음 **[!UICONTROL Start / Pause / Stop / Restart]** 작업은 도구 모음의 실행 아이콘을 통해서도 사용할 수 있습니다. 자세한 정보는 이 [섹션](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow)을 참조하십시오.

* **[!UICONTROL Purge history]**

   이 작업을 통해 워크플로우 내역을 제거할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [로그 삭제](monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

   이 옵션을 사용하면 실제 모드가 아닌 시뮬레이션 모드에서 워크플로우를 시작할 수 있습니다. 즉, 이 모드를 활성화하면 데이터베이스나 파일 시스템에 영향을 주지 않는 작업만 실행됩니다(예: **[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]**&#x200B;등). 영향을 미치는 활동(예: **[!UICONTROL Export]**, **[!UICONTROL Import]**&#x200B;등) (같은 분기에서) 그 뒤에 있는 것은 실행되지 않습니다.

* **[!UICONTROL Execute pending tasks now]**

   이 작업을 수행하면 보류 중인 모든 작업을 가능한 한 빨리 시작할 수 있습니다. 특정 작업을 시작하려면 해당 활동을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Unconditional stop]**

   이 옵션을 사용하면 워크플로 상태가 다음으로 변경됩니다. **[!UICONTROL Finished]**. 이 작업은 몇 분 후에 일반 중지 프로세스가 실패하는 경우에만 마지막 수단으로 사용해야 합니다. 진행 중인 실제 워크플로 작업이 없는 경우에만 무조건적 중지를 사용하십시오.

   >[!CAUTION]
   >
   >이 옵션은 전문가 사용자용으로 예약되어 있습니다.

* **[!UICONTROL Save as template]**

   이 작업은 선택한 워크플로우를 기반으로 새 워크플로우 템플릿을 만듭니다. 폴더를 저장할 폴더를 지정해야 합니다( **[!UICONTROL Folder]** field).

   다음 **[!UICONTROL Mass update of selected lines]** 및 **[!UICONTROL Merge selected lines]** 옵션은 모든 곳에서 사용할 수 있는 일반 플랫폼 옵션입니다 **[!UICONTROL Actions]** 메뉴 아래의 제품에서 사용할 수 있습니다. 자세한 정보는 이 [섹션](../../platform/using/updating-data.md)을 참조하십시오.

## 마우스 오른쪽 버튼 클릭 메뉴 {#right-click-menu}

하나 이상의 워크플로우 활동을 선택한 경우 마우스 오른쪽 버튼을 클릭하여 선택 작업을 수행할 수 있습니다.

![](assets/contextual_menu.png)

마우스 오른쪽 버튼 클릭 메뉴에서 사용할 수 있는 옵션은 다음과 같습니다.

**[!UICONTROL Open]**: 이 옵션을 사용하면 활동 속성에 액세스할 수 있습니다.

**[!UICONTROL Display logs:]** 이 옵션을 사용하면 선택한 활동에 대한 작업 실행 로그를 볼 수 있습니다. 을(를) 참조하십시오 [로그 표시](monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** 이 작업을 사용하면 보류 중인 작업을 가능한 한 빨리 시작할 수 있습니다.

**[!UICONTROL Workflow restart from a task:]** 이 옵션을 사용하면 이 활동에 대해 이전에 저장된 결과를 사용하여 워크플로우를 다시 시작할 수 있습니다.

**[!UICONTROL Cut/Copy/Paste/Delete:]** 이러한 옵션을 사용하면 활동을 잘라내기, 복사, 붙여넣기 및 삭제할 수 있습니다.

**[!UICONTROL Copy as bitmap:]** 이 옵션을 사용하면 모든 활동의 스크린샷을 찍을 수 있습니다.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** 이러한 옵션은 **[!UICONTROL Advanced]** 활동 속성의 탭입니다. 자세한 내용은 다음과 같습니다 [실행](advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** 워크플로우에 대한 변경 사항을 저장하거나 취소할 수 있습니다.

>[!NOTE]
>
>활동 그룹을 선택하고 이러한 명령 중 하나를 적용할 수 있습니다.

마우스 오른쪽 버튼 클릭 메뉴도 여기에 자세히 설명되어 있습니다 [섹션](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).
