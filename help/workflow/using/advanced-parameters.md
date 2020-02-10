---
title: 고급 매개 변수
seo-title: 고급 매개 변수
description: 고급 매개 변수
seo-description: null
page-status-flag: never-activated
uuid: 9453d291-921b-4a03-80d1-2c8295f9a986
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: f66f1ff5-3601-4eb8-b05d-6f99164890ae
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 고급 매개 변수{#advanced-parameters}

활동의 속성 화면에는 **[!UICONTROL Advanced]** 활동 실행 기간, 오류 등의 동작을 정의할 수 있는 탭이 있습니다.초기화 스크립트를 입력할 수 있습니다. 이 탭에는 두 가지 버전이 있습니다.

* 간소화된 버전(인스턴스용 **[!UICONTROL Start]** 및 **[!UICONTROL End]** 활동)

   ![](assets/wf-advanced-basic.png)

* 보다 자세한 버전(예: **[!UICONTROL Query]** 활동)

   ![](assets/wf-advanced-full.png)

탭에 입력할 필드는 다음 섹션에 자세히 설명되어 있습니다. **[!UICONTROL Advanced]**

## 이름 {#name}

이 필드에는 활동의 내부 이름이 포함되어 있습니다.

## Image {#image}

이 필드를 사용하면 활동에 연결된 이미지를 변경할 수 있습니다. 자세한 내용은 다음을 참조하십시오.활동 [이미지](../../workflow/using/managing-activity-images.md)관리

## 실행 {#execution}

이 필드를 사용하면 작업이 트리거될 때 수행할 작업을 정의할 수 있습니다. 다음과 같은 세 가지 옵션이 있습니다.

이러한 옵션은 일반적으로 활동을 마우스 오른쪽 단추로 클릭하여 장바구니에서 선택됩니다.

* **[!UICONTROL Normal]**:활동은 평소대로 실행됩니다.
* **[!UICONTROL Do not activate]**:이 작업과 다음 작업(동일한 분기의 경우)은 모두 실행되지 않습니다.
* **[!UICONTROL Activate but do not execute]**:이 작업과 다음 작업(동일한 분기의 경우)이 자동으로 중지됩니다. 이 기능은 작업이 시작될 때 여기에 있기를 원하는 경우에 유용합니다. 작업을 수동으로 실행하려면 활동을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Normal execution]**&#x200B;선택합니다.

## 친화성 {#affinity}

이 필드를 사용하면 특정 컴퓨터에서 작업을 강제로 실행할 수 있습니다. 자세한 내용은 다음을 참조하십시오.성향 [관리](../../workflow/using/managing-propensity.md).

## Max. 실행 기간 {#max--execution-period}

이 필드를 사용하면 작업이 너무 오래 걸리는 경우 경고를 설정할 수 있습니다. 워크플로우 작업에는 영향을 주지 않습니다. 작업이 끝날 때까지 완료되지 않으면 **[!UICONTROL Max. execution period]** 이 워크플로우에 대한 경고가 **[!UICONTROL Instance monitoring]** 페이지에 표시됩니다. 이 페이지는 홈 페이지의 **[!UICONTROL Monitoring]** 탭을 통해 액세스합니다.

## 동작 {#behavior}

이 필드를 사용하면 비동기 작업 사용에 적용할 동작을 정의할 수 있습니다. 다음 두 가지 옵션을 사용할 수 있습니다.

* **[!UICONTROL Several tasks authorized]**:첫 번째 작업이 완료되지 않았더라도 한 번에 여러 작업을 실행할 수 있습니다.
* **[!UICONTROL The current task has priority]**:진행 중인 작업이 우선합니다. 작업이 진행되는 동안에는 다른 작업이 실행되지 않습니다.

## 시간대 {#time-zone}

이 필드를 사용하면 활동의 시간대를 선택할 수 있습니다. 자세한 내용:시간대 [관리](../../workflow/using/managing-time-zones.md).

## 오류 발생 시 {#in-case-of-errors}

이 필드를 사용하면 활동에 오류가 있을 때 수행할 작업을 정의할 수 있습니다. 다음 두 가지 옵션을 사용할 수 있습니다.

* **[!UICONTROL Stop the process]**:워크플로우가 자동으로 중지됩니다. 상태가 로 변경됩니다 **[!UICONTROL Failed]**. 문제가 해결되면 워크플로우를 다시 시작합니다.
* **[!UICONTROL Ignore]**:이 작업 및 다음 작업(동일한 분기)이 모두 실행되지 않습니다. 이 기능은 반복되는 작업에 유용할 수 있습니다. 분기에 업스트림에 스케줄러가 배치되면 다음 실행 날짜에 평소대로 시작됩니다.

## 초기화 스크립트 {#initialization-script}

이 필드를 사용하면 변수를 초기화하거나 활동 속성을 수정할 수 있습니다. 자세한 내용은 다음을 참조하십시오.JavaScript [스크립트 및 템플릿](../../workflow/using/javascript-scripts-and-templates.md).

## 주석 {#comment}

이 **[!UICONTROL Comment]** 필드는 설명을 추가할 수 있는 무료 필드입니다.
