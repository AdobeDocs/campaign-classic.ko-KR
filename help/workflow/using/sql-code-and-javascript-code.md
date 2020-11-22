---
solution: Campaign Classic
product: campaign
title: SQL 코드 및 JavaScript 코드
description: SQL 및 JavaScript 코드 워크플로우 활동에 대한 자세한 내용
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 5%

---


# SQL 코드 및 JavaScript 코드{#sql-code-and-javascript-code}

## SQL 코드 {#sql-code}

활동은 **[!UICONTROL SQL code]** SQL 스크립트를 실행합니다. 스크립트는 JST 템플릿입니다.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   편집기의 중앙 영역에는 실행할 스크립트가 포함되어 있습니다. 이 스크립트는 JST 템플릿이므로 워크플로우 컨텍스트에 따라 구성할 수 있습니다.

* **[!UICONTROL Processing errors]**

   처리 [오류를 참조하십시오](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## JavaScript 코드 및 고급 JavaScript 코드 {#javascript-code}

**[!UICONTROL JavaScript code]** 및 **[!UICONTROL Advanced JavaScript code]** 활동은 워크플로우의 컨텍스트에서 JavaScript 스크립트를 실행합니다. 스크립팅에 대한 자세한 내용은 [JavaScript 스크립트 및 템플릿](../../workflow/using/javascript-scripts-and-templates.md) 섹션을 참조하십시오.

>[!NOTE]
>
>기본적으로 실행 단계 **[!UICONTROL JavaScript code]** 및 **[!UICONTROL Advanced JavaScript code]** 활동은 1시간을 초과할 수 없습니다. 이 지연 후에 오류 메시지와 함께 프로세스가 중단되고 활동 실행이 실패합니다.
>
>활동 속성에서 사용할 수 있는 **[!UICONTROL Stop execution after]** 필드에서 이러한 지연을 변경할 수 있습니다.

* **[!UICONTROL JavaScript code]**

   ![](assets/javascript_code.png)

   * **[!UICONTROL Script]**:편집기의 중앙 영역에는 실행할 스크립트가 포함되어 있습니다.
   * **[!UICONTROL Processing errors]**:처리 [오류를 참조하십시오](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

* **[!UICONTROL Advanced JavaScript code]**

   ![](assets/advanced_javascript_code.png)

   * **[!UICONTROL First call]**:편집기의 첫 번째 영역에는 첫 번째 호출 동안 실행되는 스크립트가 포함됩니다.
   * **[!UICONTROL Next calls]**:편집기의 두 번째 영역에는 다음 호출 동안 실행되는 스크립트가 포함됩니다.
   * **[!UICONTROL Transitions]**:여러 가지 활동 출력 전환을 정의할 수 있습니다.
   * **[!UICONTROL Schedule]**:이 **[!UICONTROL Schedule]** 탭에서는 활동을 트리거할 시기를 예약할 수 있습니다.
