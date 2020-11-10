---
title: 워크플로우 모범 사례
description: 캠페인 워크플로우 모범 사례 학습
page-status-flag: never-activated
uuid: 56b04004-5d96-4169-9494-3d04284d5a3d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 3da951ef-5775-4593-8301-f143c71edc19
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '1609'
ht-degree: 5%

---


# 워크플로우 모범 사례{#workflow-best-practices}

## 실행 및 성능 {#execution-and-performance}

다음은 워크플로우에 적용되는 모범 사례를 비롯하여 캠페인 성과를 최적화하는 일반적인 가이드라인입니다.

워크플로우 실행과 관련된 문제 해결 지침도 [이 섹션에서 사용할 수 있습니다](../../production/using/workflow-execution.md).

### 로그 {#logs}

JavaScript 메서드 **[!UICONTROL logInfo()]** 는 워크플로우 디버깅을 위한 좋은 솔루션입니다. 이 기능은 유용하지만, 특히 자주 실행되는 활동에 대해서는 신중하게 사용해야 합니다.로그를 오버로드하고 로그 테이블의 크기를 크게 늘릴 수 있습니다. 하지만 더 많은 기능이 필요할 수도 있습니다 **[!UICONTROL logInfo()]**.

다음과 같은 두 가지 추가 솔루션을 사용할 수 있습니다.

* **두 처형 사이에 중간 모집단의 결과 유지**

   이 옵션은 워크플로우의 두 실행 사이에 임시 테이블을 유지합니다. 워크플로우 속성 **[!UICONTROL General]** 탭에서 사용할 수 있으며 개발 및 테스트 목적으로 데이터를 모니터링하고 결과를 확인하는 데 사용할 수 있습니다. 개발 환경에서는 이 옵션을 사용할 수 있지만 프로덕션 환경에서는 사용할 수 없습니다. 임시 테이블을 유지하면 데이터베이스 크기가 크게 증가하고 결국 크기 제한에 도달할 수 있습니다. 게다가, 백업 속도가 느려질 것이다.

   워크플로우의 마지막 실행 테이블만 유지됩니다. 이전 실행의 작업 테이블은 일별로 실행되는 워크플로우에 의해 **[!UICONTROL cleanup]** 삭제됩니다.

   >[!CAUTION]
   >
   >프로덕션 워크플로우에서는 이 옵션을 체크 인할 수 없습니다. 이 옵션은 결과를 분석하는 데 사용되며 테스트 목적으로만 설계되므로 개발 또는 스테이징 환경에서만 사용해야 합니다.

* **저널에 SQL 쿼리 기록**

   워크플로우 속성 **[!UICONTROL Execution]** 탭에서 사용할 수 있는 이 옵션은 다양한 작업의 도구에서 생성된 모든 SQL 쿼리를 기록합니다. 플랫폼에 의해 실제로 실행되는 요소를 확인할 수 있습니다. 그러나 이 옵션은 개발 중에만 사용해야 하며 프로덕션 단계에서 활성화해서는 안됩니다.

더 이상 필요하지 않은 로그를 제거합니다. 워크플로우 내역은 자동으로 삭제되지 않습니다.모든 메시지는 기본적으로 유지됩니다. 작업 내역은 메뉴 **[!UICONTROL File > Actions]** 를 통해 또는 목록 위의 도구 모음에 있는 작업 단추를 클릭하여 삭제할 수 있습니다. 삭제 내역을 선택합니다.
로그를 제거하는 방법을 알아보려면 이 [설명서를 참조하십시오](../../workflow/using/starting-a-workflow.md).

### 워크플로우 계획 {#workflow-planning}

* 하루 동안 안정된 수준의 활동을 유지하고 인스턴스가 과부하를 방지하기 위해 최고점을 피하도록 하세요. 이렇게 하려면 하루 종일 전체 워크플로우 시작 시간을 균등하게 배포합니다.
* 리소스 경합을 줄이기 위해 데이터 로드를 하루 사이에 예약합니다.
* 긴 워크플로우는 서버 및 데이터베이스 리소스에 영향을 줄 수 있습니다. 가장 긴 워크플로우를 분할하여 처리 시간을 줄일 수 있습니다.
* 전반적인 실행 시간을 줄이려면 시간이 많이 소요되는 활동을 간소화되고 빠른 활동으로 대체하십시오.
* 20개 이상의 워크플로우를 동시에 실행하지 마십시오. 동시에 너무 많은 워크플로우가 실행되면 시스템이 리소스가 부족해지고 불안해질 수 있습니다. 워크플로가 시작되지 않을 수 있는 이유에 대한 자세한 내용은 이 [문서를 참조하십시오](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html).

### 워크플로우 실행 {#workflow-execution}

전체 시스템 성능이 저하되고 데이터베이스에 블록을 만들 수 있으므로 15분마다 이상 워크플로우를 실행하지 않는 것이 좋습니다.

워크플로우를 일시 중지 상태로 두지 마십시오. 임시 워크플로우를 만드는 경우, 작업이 제대로 완료되고 **[!UICONTROL paused]** 상태가 되지 않아야 합니다. 일시 중지된 경우 임시 테이블을 보관해야 하므로 데이터베이스 크기가 증가됩니다. 워크플로우 속성 아래에 있는 워크플로우 감독자를 지정하여 워크플로우에 실패하거나 시스템에서 일시 중지된 경우 경고를 전송합니다.

워크플로가 일시 중지된 상태로 유지되지 않도록 하려면

* 예기치 않은 오류가 발생하지 않도록 정기적으로 워크플로우를 확인하십시오.
* 다양한 워크플로우에서 대규모 워크플로우를 분할하는 등 워크플로우를 최대한 간단하게 유지할 수 있습니다. 다른 워크플로우의 실행에 따라 활동을 트리거할 수 **[!UICONTROL External signal]** 있습니다.
* 워크플로우에서 흐름을 사용하는 비활성화된 활동이 스레드를 열게 하고 많은 공간을 사용할 수 있는 많은 임시 테이블로 연결되는 것을 방지할 수 있습니다. 워크플로우에서 활동 **[!UICONTROL Do not enable]** 을 유지하거나 상태를 유지하지 **[!UICONTROL Enable but do not execute]** 마십시오.

또한 사용하지 않는 워크플로우를 중지합니다. 계속 실행되는 워크플로우는 데이터베이스에 대한 연결을 유지합니다.

예외적인 경우에만 무조건적인 중지를 사용하십시오. 이 작업은 정기적으로 사용하지 마십시오. 워크플로우에 의해 생성된 데이터베이스에 대한 연결을 완전히 닫지 않으면 성능이 저하됩니다.

### 엔진 옵션에서 실행 {#execute-in-the-engine-option}

창에서는 **[!UICONTROL Workflow properties]** 옵션을 확인하지 **[!UICONTROL Execute in the engine]** 마십시오. 이 옵션을 활성화하면 워크플로가 우선권을 가지며 다른 모든 워크플로우는 이 작업이 완료될 때까지 워크플로우 엔진에서 중지됩니다.

![](assets/wf-execute-in-engine.png)

## 워크플로우 속성 {#workflow-properties}

### 워크플로우 폴더 {#workflow-folders}

Adobe은 전용 폴더에 워크플로우를 만드는 것을 권장합니다.

워크플로우가 전체 플랫폼(예: 정리 프로세스)에 영향을 주는 경우 기본 제공 **[!UICONTROL Technical Workflows]** 폴더에 하위 폴더를 추가하는 것이 좋습니다.

### 워크플로우 이름 지정 {#workflow-naming}

예상과 다르게 수행될 경우 쉽게 찾고 문제를 해결하기 위해 워크플로우에 적절한 이름과 레이블을 지정하는 것을 권장합니다. 워크플로우의 설명 필드를 작성하여 운영자가 쉽게 이해할 수 있도록 수행할 프로세스를 요약합니다.

워크플로우가 여러 워크플로우를 포함하는 프로세스의 일부인 경우 레이블을 입력할 때 명시적일 수 있습니다.숫자를 사용하는 것은 워크플로우(레이블별)를 정렬하는 좋은 방법입니다.

예제:

* 001 - 가져오기 - 수신자 가져오기
* 002 - 가져오기 - 판매 가져오기
* 003 - 가져오기 - 판매 세부 정보 가져오기
* 010 - 내보내기 - 배달 로그 내보내기
* 011 - 내보내기 - 추적 로그 내보내기

### 워크플로우 심각도 {#workflow-severity}

워크플로우 속성의 **[!UICONTROL Execution]** 탭에서 워크플로우의 심각도를 구성할 수 있습니다.

* 보통
* 프로덕션
* 중요

워크플로우를 만들 때 이 정보를 제공하면 구성된 프로세스의 심각도를 이해하는 데 도움이 됩니다.

이 옵션은 캠페인 워크플로우 이외의 워크플로우에 영향을 주지 않습니다.

캠페인이 동시에 실행해야 하는 많은 프로세스가 있는 경우 심각도가 높은 캠페인 워크플로우(캠페인/작업의 일부로 생성된 워크플로우)가 우선 순위가 높습니다. 기본적으로 NmsOperation_LimitConcurrency 옵션에 따라 캠페인에서 동시에 10개의 프로세스만 실행할 수 있습니다. 예를 들어 캠페인에 25개의 워크플로우가 있는 경우 심각도가 높은 워크플로우는 10개의 프로세스의 첫 번째 풀에서 실행됩니다.

### 워크플로우 모니터링 {#workflow-monitoring}

오류가 있는 경우 경고가 표시되려면 프로덕션 환경에서 실행되는 모든 예약된 워크플로우를 모니터링해야 합니다.

워크플로우 속성에서 기본 그룹 또는 사용자 지정 그룹 중 하나를 **[!UICONTROL Workflow supervisors]** 선택합니다. 이메일 설정이 설정된 상태에서 하나 이상의 연산자가 이 그룹에 속하는지 확인합니다.

워크플로우 구축을 시작하기 전에 워크플로우 감독자를 정의해야 합니다. 오류 발생 시 이메일로 통보를 받게 됩니다. For more on this, refer to [Managing errors](../../workflow/using/monitoring-workflow-execution.md#managing-errors).

정기적으로 **[!UICONTROL Monitoring]** 우주를 확인하여 활성 워크플로우의 전체 상태를 확인합니다. For more on this, refer to [Instance supervision](../../workflow/using/monitoring-workflow-execution.md#instance-supervision).

Workflow HeatMap을 사용하면 Adobe Campaign 플랫폼 관리자가 인스턴스의 로드를 모니터링하고 그에 따라 워크플로우를 계획할 수 있습니다. For more on this, refer to [Workflow monitoring](../../workflow/using/heatmap.md).

## 활동 사용 {#using-activities}

>[!CAUTION]
>
>동일한 워크플로우 내에서 활동을 복사하고 붙여넣을 수 있습니다. 그러나 여러 워크플로우에서 붙여넣기 활동을 복사하는 것은 권장되지 않습니다. 게재 및 스케줄러와 같은 활동에 연결된 일부 설정은 대상 워크플로우를 실행하는 동안 충돌과 오류를 초래할 수 있습니다. 대신 워크플로우 **중복을** 권장합니다. 자세한 내용은 워크플로우 [중복을 참조하십시오](../../workflow/using/building-a-workflow.md#duplicating-workflows).

### 활동 이름 {#name-of-the-activity}

워크플로우를 개발하는 동안 모든 활동에는 이름이 지정되고 모든 Adobe Campaign 개체도 이름이 지정됩니다. 도구에 의해 이름이 생성되는 동안 구성할 때 명시적인 이름으로 이름을 바꾸는 것이 좋습니다. 나중에 이 작업을 수행하면 다른 이전 활동의 이름을 사용하는 활동과 함께 워크플로가 중단될 수 있습니다. 그래서 나중에 이름을 갱신하는 것은 어려운 일이 될 것이다.

활동 이름은 **[!UICONTROL Advanced]** 탭에서 찾을 수 있습니다. 이름 **[!UICONTROL query]**&#x200B;을 **[!UICONTROL query1]**&#x200B;붙이지 말고 **[!UICONTROL query11]**, 예를 들어 명시적인 이름을 **[!UICONTROL querySubscribedRecipients]**&#x200B;주세요. 이 이름은 저널에 표시되고 SQL 로그에 해당되는 경우 SQL 로그에 표시되며 구성 시 워크플로우를 디버깅하는 데 도움이 됩니다.

### 첫 번째 및 마지막 활동 {#first-and-last-activities}

* 항상 **[!UICONTROL Start]** 활동 또는 활동으로 워크플로우를 **[!UICONTROL Scheduler]** 시작합니다. 관련 있는 경우 활동을 사용할 수도 **[!UICONTROL External signal]** 있습니다.
* When building your workflow, only use one **[!UICONTROL Scheduler]** activity per branch. 워크플로우의 동일한 분기에 여러 개의 스케줄러(서로 연결됨)가 있는 경우 실행할 작업 수가 기하급수적으로 증가하여 데이터베이스가 상당히 과부하 됩니다. 이 규칙은 **[!UICONTROL Scheduling & History]** 탭이 있는 모든 활동에도 적용됩니다. 예약에 대한 자세한 [내용을 살펴보십시오](../../workflow/using/scheduler.md).

   ![](assets/wf-scheduler.png)

* 모든 워크플로우에 **[!UICONTROL End]** 활동 사용 이를 통해 Adobe Campaign은 워크플로우 내의 계산에 사용되는 임시 공간을 확보할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [시작 및 종료](../../workflow/using/start-and-end.md).

### 활동 내 Javascript {#javascript-within-an-activity}

워크플로우 활동을 초기화할 때 JavaScript를 추가할 수 있습니다. 이 작업은 활동의 활동 **[!UICONTROL Advanced]** 탭에서 수행할 수 있습니다.

워크플로우를 보다 쉽게 찾기 위해 활동 레이블의 시작과 끝에 이중 대시를 사용하는 것이 좋습니다.— My label —.

### 신호 {#signal}

대부분의 경우, 여러분은 신호가 어디에서 호출되는지 알지 못할 것입니다. 이 문제를 방지하려면 신호 활동의 **[!UICONTROL Comment]** 탭 내에 있는 **[!UICONTROL Advanced]** 필드를 사용하여 이 활동에 대한 신호의 예상 출처를 문서화합니다.

![](assets/workflow-signal-bp.png)

## 워크플로우 업데이트 {#workflow-update}

프로덕션 워크플로우를 직접 업데이트해서는 안 됩니다. 이 프로세스가 템플릿 워크플로로 캠페인을 만드는 것으로 구성되어 있지 않는 한, 먼저 개발 환경에서 프로세스를 테스트해야 합니다. 이 확인 후에는 워크플로우를 배포하고 프로덕션에서 시작할 수 있습니다.

프로덕션 환경이 아닌 개발 또는 스테이징 환경에서 모든 테스트를 수행할 수 있습니다. 이러한 경우에는 성능을 보장할 수 없습니다.

보관된 워크플로우는 개발 또는 테스트 플랫폼에 보관될 수 있지만 프로덕션 환경은 가능한 한 깨끗해야 합니다. 오래된 워크플로우는 비활성 상태인 경우 프로덕션 환경에서 제거해야 합니다.
