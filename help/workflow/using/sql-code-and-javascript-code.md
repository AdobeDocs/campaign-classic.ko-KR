---
product: campaign
title: SQL 코드 및 JavaScript 코드
description: SQL 및 JavaScript 코드 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 729a2010-c2d8-481b-8c9e-780b9e5f97ef
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 10%

---

# SQL 코드 및 JavaScript 코드{#sql-code-and-javascript-code}



## SQL 코드 {#sql-code}

An **[!UICONTROL SQL code]** 활동은 SQL 스크립트를 실행합니다. 스크립트는 JST 템플릿입니다.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   편집기의 중앙 영역에는 실행할 스크립트가 포함되어 있습니다. 이 스크립트는 JST 템플릿이므로 워크플로우 컨텍스트에 따라 구성할 수 있습니다.

* **[!UICONTROL Processing errors]**

   을(를) 참조하십시오. [처리 오류](monitoring-workflow-execution.md#processing-errors).

## JavaScript 코드 및 고급 JavaScript 코드 {#javascript-code}

**[!UICONTROL JavaScript code]** 및 **[!UICONTROL Advanced JavaScript code]** 활동은 워크플로우의 컨텍스트에서 JavaScript 스크립트를 실행합니다. 스크립팅에 대한 자세한 정보는 다음 섹션을 참조하십시오.

* [JavaScript 스크립트 및 템플릿](javascript-scripts-and-templates.md)
* [워크플로우의 JavaScript 코드 예](javascript-in-workflows.md)

### 실행 지연 {#exec-delay}

20.2 릴리스부터 실행 지연이 **[!UICONTROL JavaScript code]** 및 **[!UICONTROL Advanced JavaScript code]** 활동. 기본적으로 실행 단계는 1시간을 초과할 수 없습니다. 이 지연 후에 오류 메시지와 함께 프로세스가 중단되고 활동 실행이 실패합니다.

에서 이 지연을 변경할 수 있습니다. **[!UICONTROL Stop execution after]** 이러한 활동에서 사용할 수 있는 필드입니다.

이 제한을 무시하려면 값을 로 설정해야 합니다 **0**.

### JavaScript 코드 {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**: 편집기의 중앙 영역에는 실행할 스크립트가 포함되어 있습니다.

* **[!UICONTROL Process errors]**: 을(를) 참조하십시오. [처리 오류](monitoring-workflow-execution.md#processing-errors).

### 고급 JavaScript 코드 {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL First call]**: 편집기의 첫 번째 영역에는 첫 번째 호출 동안 실행할 스크립트가 포함됩니다.
* **[!UICONTROL Next calls]**: 편집기의 두 번째 영역에는 다음 호출 동안 실행할 스크립트가 포함됩니다.
* **[!UICONTROL Transitions]**: 여러 활동 출력 전환을 정의할 수 있습니다.
* **[!UICONTROL Schedule]**: 다음 **[!UICONTROL Schedule]** 탭에서는 활동을 트리거할 시기를 예약할 수 있습니다.

고급 JavaScript는 영구적 작업이며, 완료로 표시되지 않은 경우 주기적으로 호출됩니다. 작업을 종료하고 향후 리콜을 방지하려면 **task.setCompleted()** 메서드에서 사용할 수 있습니다 **[!UICONTROL Next calls]** 섹션:

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```
