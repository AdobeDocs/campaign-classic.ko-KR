---
product: campaign
title: 워크플로 시작
description: 워크플로우를 시작하고 워크플로우 작업 을 검색하는 방법 도구 모음 및 마우스 오른쪽 버튼 클릭 메뉴
feature: Workflows
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: 7453db63a0ed2c617e9f7e4cbfa3480b3ed5020d
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 1%

---

# 워크플로 시작 {#starting-a-workflow}



워크플로우는 항상 수동으로 시작됩니다. 그러나 시작되면 스케줄러([스케줄러](scheduler.md) 참조) 또는 활동 예약을 통해 지정된 정보에 따라 비활성 상태로 유지될 수 있습니다.

타겟팅 워크플로우 실행(실행, 중지, 일시 중지 등)과 관련된 작업 **비동기** 프로세스: 순서가 기록되며 서버가 이 순서를 적용할 수 있게 되면 즉시 적용됩니다.

도구 모음을 사용하여 워크플로우 실행을 시작하고 추적할 수 있습니다.

**[!UICONTROL Actions]** 메뉴 및 마우스 오른쪽 단추 클릭 메뉴에서 사용할 수 있는 옵션 목록은 아래에 자세히 설명되어 있습니다.

>[!IMPORTANT]
>
>연산자가 워크플로우에서 작업(시작, 중지, 일시 중지 등)을 수행할 때 작업이 즉시 실행되지 않고 대신 [워크플로우 모듈](architecture.md)에서 처리되도록 큐에 배치됩니다.

## 작업 도구 모음 {#actions-toolbar}

도구 모음 단추는 이 [섹션](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)에 자세히 설명되어 있습니다. **[!UICONTROL Actions]** 단추를 사용하면 선택한 워크플로우에 적용되는 추가 실행 옵션에 액세스할 수 있습니다. **[!UICONTROL File > Actions]** 메뉴를 사용하거나 워크플로를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Actions]**&#x200B;을(를) 선택할 수도 있습니다.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

  이 작업을 통해 워크플로 실행을 시작할 수 있습니다. **완료됨**, **편집 중** 또는 **일시 중지됨**&#x200B;인 워크플로는 상태를 **시작됨**(으)로 변경합니다. 그런 다음 워크플로우 엔진이 이 워크플로우의 실행을 처리합니다. 워크플로우가 일시 중지된 경우에는 다시 시작되고, 그렇지 않으면 워크플로우가 처음부터 시작되고 초기 활동이 활성화됩니다.

  시작은 비동기 프로세스입니다. 요청이 저장되고 워크플로우 서버에서 가능한 한 빨리 처리됩니다.

* **[!UICONTROL Pause]**

  이 작업은 워크플로우의 상태를 **일시 중지됨**(으)로 설정합니다. 워크플로우가 다시 시작될 때까지 활동이 활성화되지 않지만 진행 중인 작업은 일시 중지되지 않습니다.

* **[!UICONTROL Stop]**

  이 작업은 현재 실행 중인 워크플로우를 중지합니다. 인스턴스의 상태가 **완료됨**(으)로 설정되어 있습니다. 진행 중인 작업은 가능한 경우 중지됩니다. 가져오기 및 SQL 쿼리가 즉시 취소됩니다.

  >[!IMPORTANT]
  >
  >워크플로를 중지하는 것은 비동기 프로세스입니다. 요청이 등록된 다음 워크플로 서버 또는 서버가 진행 중인 작업을 취소합니다. 따라서 워크플로 인스턴스를 중지하는 데 시간이 걸릴 수 있습니다. 특히 워크플로가 여러 서버에서 실행 중인 경우 각 서버에서 진행 중인 작업을 취소하도록 제어해야 합니다. 문제가 발생하지 않도록 하려면 중지 작업이 완료될 때까지 기다린 후 동일한 워크플로우에서 여러 중지 요청을 수행하지 마십시오.

* **[!UICONTROL Unconditional stop]**

  이 옵션은 워크플로 상태를 **[!UICONTROL Finished]**(으)로 변경합니다. 이 작업은 몇 분 후에 일반 중지 프로세스가 실패하는 경우에만 마지막 수단으로 사용해야 합니다. 진행 중인 실제 워크플로 작업이 없는 경우에만 무조건적 중지를 사용하십시오.

  >[!CAUTION]
  >
  >무조건부 중지는 관리자 사용자로 제한됩니다.

* **[!UICONTROL Restart]**

  이 작업은 중지된 후 워크플로우를 다시 시작합니다. 대부분의 경우 이를 통해 보다 빠르게 다시 시작할 수 있습니다. 중지하는 데 일정 시간이 걸리는 경우 다시 시작을 자동화하는 것도 유용합니다. 워크플로우를 중지하는 동안에는 &#39;중지&#39; 명령을 사용할 수 없기 때문입니다.

  도구 모음의 실행 아이콘을 통해서도 **[!UICONTROL Start / Pause / Stop / Restart]** 작업을 사용할 수 있습니다. 자세한 정보는 이 [섹션](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow)을 참조하십시오.

  **다시 시작** 작업은 **실행**, **중지** 및 **시작** 작업과 비교하여 워크플로 인스턴스 변수를 지우지 않습니다(시작 작업 시 발생하는 인스턴스 변수 지우기). 워크플로우를 다시 시작할 때 인스턴스 변수를 보존된 값과 함께 사용할 수 있습니다. 이를 지우려면 다음 중 하나를 수행합니다.
   * **중지** 및 **시작** 작업을 수행합니다.
   * 워크플로우 실행이 끝나면 아래 javascript 코드를 추가합니다.

     ```
     var wkf = xtk.workflow.load(instance.id)
     wkf.variables='<variables/>'
     wkf.save()
     ```

* **[!UICONTROL Purge history]**

  이 작업을 통해 워크플로우 내역을 제거할 수 있습니다. 자세한 내용은 [로그 제거](monitoring-workflow-execution.md#purging-the-logs)를 참조하세요.

* **[!UICONTROL Start in simulation mode]**

  이 옵션을 사용하면 실제 모드가 아닌 시뮬레이션 모드에서 워크플로우를 시작할 수 있습니다. 즉, 이 모드를 활성화하면 데이터베이스 또는 파일 시스템에 영향을 주지 않는 작업만 실행됩니다(예: **[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]** 등). 영향을 미치는 활동(예: **[!UICONTROL Export]**, **[!UICONTROL Import]** 등) (같은 분기에서) 그 뒤에 있는 것은 실행되지 않습니다.

* **[!UICONTROL Execute pending tasks now]**

  이 작업을 수행하면 보류 중인 모든 작업을 가능한 한 빨리 시작할 수 있습니다. 특정 작업을 시작하려면 해당 활동을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Execute pending task(s) now]**&#x200B;을(를) 선택합니다.

* **[!UICONTROL Save as template]**

  이 작업은 선택한 워크플로우를 기반으로 새 워크플로우 템플릿을 만듭니다. **[!UICONTROL Folder]** 필드에 폴더를 저장할 폴더를 지정해야 합니다.

  **[!UICONTROL Mass update of selected lines]** 및 **[!UICONTROL Merge selected lines]** 옵션은 모든 **[!UICONTROL Actions]** 메뉴에서 사용할 수 있는 일반 플랫폼 옵션입니다. 자세한 정보는 이 [섹션](../../platform/using/updating-data.md)을 참조하십시오.


## 워크플로우 실행 우수 사례 {#workflow-execution-best-practices}

**워크플로우가 전체 시스템 성능을 방해하고 데이터베이스에 블록을 만들 수 있으므로 워크플로우를 15분 이상 실행하도록 예약하지 마십시오**.

**워크플로를 일시 중지된 상태로 두지 마십시오**. 임시 워크플로우를 만드는 경우 해당 워크플로우를 올바르게 완료할 수 있고 **[!UICONTROL paused]** 상태로 유지하지 않는지 확인하십시오. 일시 중지된 경우 임시 테이블을 유지해야 하므로 데이터베이스 크기를 늘려야 합니다. 워크플로 속성 아래에 워크플로 감독자를 할당하여 워크플로가 실패하거나 시스템에서 일시 중지된 경우 경고를 보냅니다.

워크플로우가 일시 중지된 상태가 되지 않도록 하려면 다음 작업을 수행하십시오.

* 예기치 않은 오류가 없는지 정기적으로 워크플로우를 확인하십시오.
* 대규모 워크플로우를 여러 다른 워크플로우로 분할하는 등 가능한 한 워크플로우를 단순하게 유지합니다. **[!UICONTROL External signal]** 활동을 사용하면 다른 워크플로우의 실행에 따라 실행을 트리거할 수 있습니다.
* 워크플로우에서 흐름이 있는 활동을 비활성화하여 스레드를 열어 두고 많은 공간을 사용할 수 있는 많은 임시 테이블로 이어지지 않도록 하십시오. 워크플로우에 **[!UICONTROL Do not enable]** 또는 **[!UICONTROL Enable but do not execute]** 상태의 활동을 유지하지 마십시오.

**사용하지 않는 워크플로 중지**. 계속 실행되는 워크플로우는 데이터베이스에 대한 연결을 유지합니다.

**가장 드문 경우에만 무조건적 중지를 사용합니다**. 이 옵션은 관리자 사용자로 제한됩니다. 이 작업을 정기적으로 사용하지 마십시오. 워크플로우에서 생성된 연결을 데이터베이스에 대해 완전히 종료하지 않으면 성능이 저하됩니다.

**동일한 워크플로우에서 여러 중지 요청을 수행하지 마십시오**. 워크플로를 중지하는 것은 비동기 프로세스입니다. 요청이 등록된 다음 워크플로 서버 또는 서버가 진행 중인 작업을 취소합니다. 따라서 워크플로 인스턴스를 중지하는 데 시간이 걸릴 수 있습니다. 특히 워크플로가 여러 서버에서 실행 중인 경우 각 서버에서 진행 중인 작업을 취소하도록 제어해야 합니다. 문제가 발생하지 않도록 하려면 중지 작업이 완료될 때까지 기다린 후 워크플로우를 여러 번 중지하지 마십시오.

## 마우스 오른쪽 버튼 클릭 메뉴 {#right-click-menu}

하나 이상의 워크플로우 활동을 선택한 경우 마우스 오른쪽 버튼을 클릭하여 선택 작업을 수행할 수 있습니다.

![](assets/contextual_menu.png)

마우스 오른쪽 버튼 클릭 메뉴에서 사용할 수 있는 옵션은 다음과 같습니다.

**[!UICONTROL Open]**: 이 옵션을 사용하면 활동 속성에 액세스할 수 있습니다.

**[!UICONTROL Display logs:]** 이 옵션을 사용하면 선택한 활동에 대한 작업 실행 로그를 볼 수 있습니다. [로그 표시](monitoring-workflow-execution.md#displaying-logs)를 참조하세요.

**[!UICONTROL Execute pending task(s) now:]** 이 작업을 사용하면 보류 중인 작업을 가능한 한 빨리 시작할 수 있습니다.

**[!UICONTROL Workflow restart from a task:]** 이 옵션을 사용하면 이 활동에 대해 이전에 저장된 결과를 사용하여 워크플로우를 다시 시작할 수 있습니다.

**[!UICONTROL Cut/Copy/Paste/Delete:]** 이러한 옵션을 사용하면 활동을 잘라내고, 복사하고, 붙여 넣고, 삭제할 수 있습니다.

**[!UICONTROL Copy as bitmap:]** 이 옵션을 사용하면 모든 활동의 스크린샷을 찍을 수 있습니다.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** 이러한 옵션은 활동 속성의 **[!UICONTROL Advanced]** 탭에서도 사용할 수 있습니다. 자세한 내용은 [실행](advanced-parameters.md#execution)을 참조하세요.

**[!UICONTROL Save / Cancel:]**&#x200B;을(를) 사용하면 워크플로우의 변경 내용을 저장하거나 취소할 수 있습니다.

>[!NOTE]
>
>활동 그룹을 선택하고 이러한 명령 중 하나를 적용할 수 있습니다.

마우스 오른쪽 단추 클릭 메뉴는 이 [섹션](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow)에도 자세히 설명되어 있습니다.
