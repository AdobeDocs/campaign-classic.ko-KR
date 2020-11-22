---
solution: Campaign Classic
product: campaign
title: 고급 매개 변수
description: 고급 매개 변수
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 2%

---


# 고급 매개 변수{#advanced-parameters}

활동의 속성 화면에는 오류 발생 시 동작, 활동의 실행 기간을 정의할 수 있는 **[!UICONTROL Advanced]** 탭이 있습니다.초기화 스크립트를 입력할 수 있습니다. 이 탭에는 두 가지 버전이 있습니다.

* 간소화된 버전(인스턴스용 **[!UICONTROL Start]** 및 **[!UICONTROL End]** 활동)

   ![](assets/wf-advanced-basic.png)

* 보다 자세한 버전(예: **[!UICONTROL Query]** 활동)

   ![](assets/wf-advanced-full.png)

탭에 입력할 필드는 **[!UICONTROL Advanced]** 다음 섹션에 자세히 설명되어 있습니다.

## 이름 {#name}

이 필드는 활동의 내부 이름을 포함합니다.

## 이미지 {#image}

이 필드를 사용하면 활동에 연결된 이미지를 변경할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [활동 이미지](../../workflow/using/managing-activity-images.md)관리

## 실행 {#execution}

이 필드에서는 작업이 트리거될 때 수행할 작업을 정의할 수 있습니다. 세 가지 가능한 옵션이 있습니다.

이러한 옵션은 일반적으로 활동을 마우스 오른쪽 단추로 클릭하여 장바구니에서 선택됩니다.

* **[!UICONTROL Normal]**:활동은 평소대로 실행됩니다.
* **[!UICONTROL Do not activate]**:이 작업 및 다음 작업(동일한 분기에 포함)이 모두 실행되지 않습니다.
* **[!UICONTROL Activate but do not execute]**:이 작업과 다음 작업(동일한 분기)이 자동으로 중지됩니다. 이 기능은 작업이 시작될 때 여기에 있기를 원하는 경우에 유용합니다. 작업을 수동으로 실행하려면 활동을 마우스 오른쪽 단추로 클릭하고 선택합니다 **[!UICONTROL Normal execution]**.

## 친화성 {#affinity}

이 필드를 사용하면 특정 컴퓨터에서 작업을 강제로 실행할 수 있습니다. For more on this, refer to: [Managing propensity](../../workflow/using/managing-propensity.md).

## 맥스 실행 기간 {#max--execution-period}

이 필드를 사용하면 작업이 너무 오래 걸리는 경우 경고를 설정할 수 있습니다. 워크플로우 작업에는 영향을 주지 않습니다. 작업이 종료될 때까지 완료되지 않으면 **[!UICONTROL Max. execution period]** 이 워크플로우에 대한 경고가 **[!UICONTROL Instance monitoring]** 페이지에 표시됩니다. 이 페이지는 홈 페이지의 **[!UICONTROL Monitoring]** 탭을 통해 액세스합니다.

## 동작 {#behavior}

이 필드에서는 비동기 작업을 사용하기 위해 적용할 동작을 정의할 수 있습니다. 다음 두 가지 옵션을 사용할 수 있습니다.

* **[!UICONTROL Several tasks authorized]**:첫 번째 작업이 완료되지 않았더라도 한 번에 여러 작업을 실행할 수 있습니다.
* **[!UICONTROL The current task has priority]**:진행 중인 작업의 우선 순위가 높습니다. 작업이 진행되는 동안에는 다른 작업이 실행되지 않습니다.

## 시간대 {#time-zone}

이 필드에서는 활동의 시간대를 선택할 수 있습니다. 자세한 내용: [시간대](../../workflow/using/managing-time-zones.md)관리

## 오류 발생 시 {#in-case-of-errors}

이 필드에서는 활동에 오류가 있을 때 수행할 작업을 정의할 수 있습니다. 다음 두 가지 옵션을 사용할 수 있습니다.

* **[!UICONTROL Stop the process]**:워크플로우가 자동으로 중지됩니다. 상태는 로 변경됩니다 **[!UICONTROL Failed]**. 문제가 해결되면 워크플로우를 다시 시작합니다.
* **[!UICONTROL Ignore]**:이 작업 및 다음 작업(동일한 분기에 있음)이 실행되지 않습니다. 이 기능은 반복되는 작업에 유용합니다. 분기에 업스트림 배치 스케줄러가 있는 경우 다음 실행 날짜에 평소처럼 시작됩니다.

## 초기화 스크립트 {#initialization-script}

이 필드에서는 변수를 초기화하거나 활동 속성을 수정할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [JavaScript 스크립트 및 템플릿을 참조하십시오](../../workflow/using/javascript-scripts-and-templates.md).

## 주석 {#comment}

필드 **[!UICONTROL Comment]** 는 설명을 추가할 수 있는 무료 필드입니다.
