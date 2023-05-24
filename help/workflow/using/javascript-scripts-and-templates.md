---
product: campaign
title: JavaScript 스크립트 및 템플릿
description: JavaScript 스크립트 및 템플릿
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 4a3647d1-cf8c-4867-871e-472287be7c6a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1242'
ht-degree: 2%

---

# JavaScript 스크립트 및 템플릿{#javascript-scripts-and-templates}



스크립트를 사용하면 값을 계산하고 프로세스의 다른 작업 간에 데이터를 교환하며 SOAP 호출을 사용하여 특정 작업을 실행할 수 있습니다.

스크립트는 워크플로 다이어그램의 어디에나 있습니다.

* 모든 활동에는 초기화 스크립트가 있습니다. 초기화 스크립트는 활동이 활성화될 때 실행되며, 변수를 초기화하고 속성을 수정하는 데 사용할 수 있습니다.
* &#39;JavaScript 코드&#39; 활동은 단순히 스크립트를 실행하는 데 사용됩니다.
* &#39;Test&#39; 활동은 적절한 전환을 활성화하기 위해 JavaScript 표현식을 평가합니다.
* 대부분의 텍스트 필드는 JavaScript 템플릿입니다. JavaScript 표현식은 &lt;%=~%> 사이에 포함될 수 있습니다. 이러한 필드에는 표현식 입력에 도움이 되는 드롭다운 목록을 여는 버튼이 있습니다.

   ![](assets/script-button.png)

## 오브젝트 노출됨 {#objects-exposed}

워크플로우 컨텍스트에서 실행되는 JavaScript는 일련의 추가 전역 오브젝트에 액세스합니다.

* **인스턴스**: 실행 중인 워크플로우를 나타냅니다. 이 개체의 스키마는 입니다. **xtk:workflow**.
* **작업**: 실행 중인 작업을 나타냅니다. 이 개체의 스키마는 입니다. **xtk:workflowTask**.
* **이벤트**: 실행 중인 작업을 활성화한 이벤트를 나타냅니다. 이 개체의 스키마는 입니다. **xtk:workflowEvent**. 이 개체는 다음에 대해 초기화되지 않았습니다. **AND-결합** 여러 전환에서 활성화된 활동을 입력합니다.
* **events**: 현재 작업을 활성화한 이벤트 목록을 나타냅니다. 이 개체의 스키마는 입니다. **xtk:workflowEvent**. 이 표에는 일반적으로 한 개의 요소가 포함되어 있지만 **AND-결합** 여러 전환을 기반으로 활성화된 활동을 입력합니다.
* **활동**: 실행 중인 작업의 모델을 나타냅니다. 이 개체의 스키마는 활동 유형에 따라 다릅니다. 이 객체는 초기화 스크립트로 수정할 수 있으며, 다른 스크립트에서는 을 사용하여 수정하면 알 수 없는 효과가 있습니다.

이러한 객체에 사용할 수 있는 등록 정보는 스크립트 도구 모음의 오른쪽에 있는 버튼을 클릭하여 드롭다운 목록에서 볼 수 있습니다.

>[!CAUTION]
>
>이러한 개체의 속성은 vars 속성의 하위 속성을 제외하고 읽기 전용입니다.
>  
>이러한 속성의 대부분은 기본 작업을 실행한 후 또는 인스턴스가 수동화된 경우에만 업데이트됩니다. 읽은 값은 반드시 현재 상태와 일치하지 않고 이전 상태와 일치합니다.

**예제**

이 예제와 다음 예에서는 **JavaScript 코드** 활동 및 **종료** 다음 다이어그램에 표시된 대로 활동.

![](assets/script-1.png)

를 두 번 클릭합니다. **JavaScript 코드** 활동 을 클릭하고 다음 스크립트를 삽입합니다.

```
logInfo("Label: " + instance.label)
logInfo("Start date: " + task.creationDate)
```

다음 **[!UICONTROL logInfo(message)]** 함수는 로그에 메시지를 삽입합니다.

클릭 **[!UICONTROL OK]** 만들기 마법사를 닫은 다음 워크플로 목록의 오른쪽 상단에 있는 작업 단추를 사용하여 워크플로를 시작합니다. 실행이 끝나면 로그를 참조하십시오. 스크립트에 해당하는 두 개의 메시지가 표시되어야 합니다. 하나는 워크플로우의 레이블을 표시하고 다른 하나는 스크립트가 활성화된 날짜를 표시합니다.

## 변수 {#variables}

변수는 의 자유 속성입니다 **[!UICONTROL instance]**, **[!UICONTROL task]** 및 **[!UICONTROL event]** 개체. 이러한 변수에 대해 승인된 JavaScript 유형은 다음과 같습니다 **[!UICONTROL string]**, **[!UICONTROL number]** 및 **[!UICONTROL Date]**.

### 인스턴스 변수 {#instance-variables}

인스턴스 변수(**[!UICONTROL instance.vars.xxx]**)은 글로벌 변수와 비슷합니다. 모든 활동에서 공유됩니다.

### 작업 변수 {#task-variables}

작업 변수(**[!UICONTROL task.vars.xxx]**)는 로컬 변수와 비슷합니다. 현재 작업에서만 사용됩니다. 이러한 변수는 데이터를 유지하기 위해 영구적인 활동에서 사용되며 경우에 따라 동일한 활동의 여러 스크립트 간에 데이터를 교환하는 데 사용됩니다.

### 이벤트 변수 {#event-variables}

이벤트 변수(**[!UICONTROL vars.xxx]**) 워크플로우 프로세스의 기본 작업 간에 데이터 교환을 활성화합니다. 진행 중인 작업을 활성화한 작업에 의해 이러한 변수가 전달됩니다. 이를 수정하고 새 항목을 정의할 수 있습니다. 그런 다음 다음 다음 활동으로 전달됩니다.

>[!CAUTION]
>
>의 경우에는 [AND-결합](and-join.md) 활동을 입력하면 변수가 병합되지만 동일한 변수가 두 번 정의되면 충돌이 발생하고 값이 확인되지 않습니다.

이벤트는 가장 자주 사용되는 변수이며 인스턴스 변수보다 우선하여 사용해야 합니다.

특정 이벤트 변수는 다양한 활동에서 수정하거나 읽습니다. 이러한 변수는 모두 문자열 유형 변수입니다. 예를 들어 내보내기는 **[!UICONTROL vars.filename]** 방금 내보낸 파일의 전체 이름을 사용하는 변수입니다. 이러한 모든 읽기 또는 수정된 변수는에 설명되어 있습니다 [활동 기본 정보](about-activities.md), 섹션 **입력 매개 변수** 및 **출력 매개 변수** 을 참조하십시오.

### 활용 사례 {#example}

>[!NOTE]
>
>추가적인 워크플로우 사용 사례는에서 사용할 수 있습니다. [이 섹션](about-workflow-use-cases.md).

**예 1**

이 예에서는 인스턴스 변수를 사용하여 모집단에 적용할 분할 비율을 동적으로 계산합니다.

1. 워크플로우를 만들고 시작 활동을 추가합니다.

1. 인스턴스 변수를 정의하도록 JavaScript 코드 활동을 추가하고 구성합니다.

   예제: `instance.vars.segmentpercent = 10;`

   ![](assets/js_ex1.png)

1. 필요에 따라 쿼리 활동을 추가하고 수신자를 타겟팅합니다.

1. Split 활동을 추가하고 들어오는 모집단의 임의 샘플링을 수행하도록 구성합니다. 샘플링 비율은 원하는 대로 선택할 수 있습니다. 이 예제에서는 50%로 설정되어 있습니다.

   이전에 정의된 인스턴스 변수 덕분에 동적으로 업데이트되는 이 백분율입니다.

   ![](assets/js_ex2.png)

1. 분할 활동의 고급 탭에 있는 초기화 스크립트 섹션 내에서 JS 조건을 정의합니다. JS 조건은 분할 활동에서 나오는 첫 번째 전환의 무작위 샘플링 백분율을 선택하고 이전에 만든 인스턴스 변수에 의해 설정된 값으로 업데이트합니다.

   ```
   activity.transitions.extractOutput[0].limiter.percent = instance.vars.segmentpercent;
   ```

   ![](assets/js_ex3.png)

1. 보충 항목이 분할 활동의 개별 전환에서 생성되었는지 확인하고 각 아웃바운드 전환 후 종료 활동을 추가합니다.

1. 워크플로우를 저장하고 실행합니다. 동적 샘플링은 인스턴스 변수에 따라 적용됩니다.

   ![](assets/js_ex4.png)

**예제 2**

1. 이전 예제의 워크플로를 가져와 의 스크립트를 **JavaScript 코드** 다음 스크립트를 사용하는 활동:

   ```
   instance.vars.foo = "bar1"
   vars.foo = "bar2"
   task.vars.foo = "bar3"
   ```

1. 다음 스크립트를 의 초기화 스크립트에 추가합니다. **종료** 활동:

   ```
   logInfo("instance.vars.foo = " + instance.vars.foo)
   logInfo("vars.foo = " + vars.foo)
   logInfo("task.vars.foo = " + task.vars.foo)
   ```

1. 워크플로우를 시작한 다음 로그를 확인합니다.

   ```
   Workflow finished
   task.vars.foo = undefined
   vars.foo = bar2
   instance.vars.foo = bar1
   Starting workflow (operator 'admin')
   ```

이 예는 활동이 다음을 수행하는 것을 보여줍니다. **JavaScript 코드** 인스턴스 변수 및 이벤트 변수에 액세스하지만 작업 변수는 외부에서 액세스할 수 없습니다(&#39;정의되지 않음&#39;).

### 쿼리에서 인스턴스 변수 호출 {#calling-an-instance-variable-in-a-query}

활동에서 인스턴스 변수를 지정했으면 워크플로우 쿼리에서 다시 사용할 수 있습니다.

따라서 변수를 호출합니다 **instance.vars.xxx = &quot;yyy&quot;** 필터에 다음을 입력합니다. **$(instance/vars/xxx)**.

예제:

1. 를 통해 게재의 내부 이름을 정의하는 인스턴스 변수를 만듭니다. **[!UICONTROL JavaScript code]**: **instance.vars.deliveryIN = &quot;DM42&quot;**.

   ![](assets/wkf_js_activity_1.png)

1. 타겟팅 및 필터링 차원이 수신자인 쿼리를 만듭니다. 조건에서 변수에 의해 지정된 게재를 보낸 모든 수신자를 찾도록 지정합니다.

   다시 말해서 이 정보는 게재 로그에 저장됩니다.

   에서 인스턴스 변수를 참조하려면 **[!UICONTROL Value]** 열, 입력 **$(instance/vars/@deliveryIN)**.

   이 워크플로우는 DM42 게재 수신자를 반환합니다.

   ![](assets/wkf_var_in_query.png)

## 고급 함수 {#advanced-functions}

표준 JavaScript 함수 외에도 파일을 조작하거나, 데이터베이스의 데이터를 읽거나 수정하거나, 로그에 메시지를 추가하는 데 특수 함수를 사용할 수 있습니다.

### 저널 {#journal}

**[!UICONTROL logInfo(message)]** 위의 예제에 자세히 설명되어 있습니다. 이 함수는 저널에 정보 메시지를 추가합니다.

**[!UICONTROL logError(message)]** 로그에 오류 메시지를 추가합니다. 스크립트가 실행을 중단하고 워크플로가 오류 상태로 변경됩니다(기본적으로 인스턴스는 일시 중지됩니다).

## 초기화 스크립트 {#initialization-script}

특정 조건에서 실행 시 활동의 속성을 수정할 수 있습니다.

활동의 대부분의 속성은 JavaScript 템플릿을 사용하거나 워크플로우 속성에서 스크립트로 값을 계산할 수 있으므로 동적으로 계산할 수 있습니다.

그러나 다른 속성의 경우 초기화 스크립트를 사용해야 합니다. 이 스크립트는 작업이 실행되기 전에 평가됩니다. 다음 **[!UICONTROL activity]** 변수는 작업에 해당하는 활동을 참조합니다. 이 활동의 속성은 수정할 수 있으며 이 작업에만 영향을 줍니다.

**관련 항목**
[워크플로우의 JavaScript 코드 예](javascript-in-workflows.md)
