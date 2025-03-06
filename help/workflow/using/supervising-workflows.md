---
product: campaign
title: 워크플로우 감독
description: Campaign 워크플로우를 관리하는 방법 알아보기
feature: Workflows
hide: true
hidefromtoc: true
exl-id: ca6d4bf4-7b3a-4d36-9fc3-0b83531d0132
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 0%

---

# 사용 사례: 워크플로우 관리{#supervising-workflows}



이 사용 사례에서는 &quot;일시 중지됨&quot;, &quot;중지됨&quot; 또는 &quot;오류 있음&quot;인 워크플로 세트의 상태를 모니터링할 수 있는 워크플로 만들기에 대해 자세히 설명합니다.

목적은 다음과 같습니다.

* 워크플로우를 사용하여 비즈니스 워크플로우 그룹을 모니터링합니다.
* &quot;게재&quot; 활동을 통해 감독자에게 메시지를 보냅니다.

워크플로 세트의 상태를 모니터링하려면 다음 단계를 수행해야 합니다.

1. 모니터링 워크플로우를 만듭니다.
1. JavaScript을 작성하여 워크플로우가 일시 중지, 중지 또는 오류 발생 여부를 확인합니다.
1. **[!UICONTROL Test]** 활동을 만듭니다.
1. 게재 템플릿을 준비합니다.

>[!NOTE]
>
>워크플로우 외에도 Campaign **워크플로우 Heatmap**&#x200B;을(를) 사용하면 현재 실행 중인 워크플로우를 자세히 분석할 수 있습니다. 자세한 내용은 [전용 섹션](heatmap.md)을 참조하세요.
>
>**워크플로우의 실행을 모니터링하는 방법**&#x200B;에 대한 자세한 내용은 [이 섹션](monitoring-workflow-execution.md)을 참조하세요.

## 1단계: 모니터링 워크플로우 만들기 {#step-1--creating-the-monitoring-workflow}

모니터링할 워크플로 폴더는 **관리 > 프로덕션 > 기술 워크플로** 노드에 저장된 **&quot;CustomWorkflows&quot;** 폴더입니다. 이 폴더에는 일련의 비즈니스 워크플로우가 포함되어 있습니다.

**모니터링 워크플로**&#x200B;가 기술 워크플로 폴더의 루트에 저장됩니다. 사용된 레이블은 **&quot;모니터링&quot;**&#x200B;입니다.

다음 스키마는 활동의 순서를 보여 줍니다.

![](assets/uc_monitoring_workflow_overview.png)

이 워크플로우는 다음과 같이 구성됩니다.

* **&quot;시작&quot;** 활동.
* 비즈니스 워크플로 폴더를 분석하는 **&quot;JavaScript 코드&quot;** 활동.
* 감독자에게 게재를 보내거나 워크플로우를 다시 시작하는 **&quot;테스트&quot;** 활동.
* 메시지 레이아웃을 담당하는 **&quot;게재&quot;** 활동.
* 워크플로우 반복 사이의 리드 타임을 제어하는 **&quot;Wait&quot;** 활동.

## 2단계: JavaScript 작성 {#step-2--writing-the-javascript}

JavaScript 코드의 첫 번째 부분은 &quot;일시 중지&quot;(@state == 13), &quot;오류&quot;(@failed == 1) 또는 &quot;중지됨&quot;(@state == 20) 상태의 워크플로우를 식별할 수 있는 **쿼리(queryDef)**&#x200B;과(와) 일치합니다.

모니터링할 워크플로 폴더의 **내부 이름**&#x200B;은(는) 다음 조건에서 제공됩니다.

```
<condition boolOperator="AND" expr="[folder/@name] = 'Folder20'" internalId="1"/>
```

```
var strError = "";
var strPaused = "";
var strStop = "";

var queryWkfError = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
      <node expr="@state"/>
      <node expr="@label"/>
      <node expr="@failed"/>
      <node expr="@state"/>   
    </select>
    <where id="12837805386">
      <condition boolOperator="AND" expr="[folder/@name] = 'Folder20'" internalId="1"/>
        <condition boolOperator="AND" internalId="2">
          <condition boolOperator="OR" expr="@state = 20" internalId="3"/>
          <condition expr="@state = 13" internalId="4"/>
        </condition>  
    </where>
  </queryDef>
);
var ndWkfError = queryWkfError.ExecuteQuery(); 
```

JavaScript 코드의 두 번째 부분을 사용하면 쿼리 중에 복구된 상태에 따라 **각 워크플로우에 대한 메시지를 표시할 수 있습니다**.

>[!NOTE]
>
>생성된 문자열은 워크플로우의 이벤트 변수에 로드되어야 합니다.

```
for each ( var wkf in ndWkfError.workflow ) 
{
  if ( wkf.@state == 13 )  // Status 13 = paused
  {
    if ( wkf.@failed == 1 )
      strError += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
    else
      strPaused += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
  }
  
  if ( wkf.@state == 20 )  // Status 20 = stop
    strStop += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
}

vars.strWorkflowError = strError;
vars.strWorkflowPaused = strPaused;
vars.strWorkflowStop = strStop;
```

## 3단계: &#39;테스트&#39; 활동 만들기 {#step-3--creating-the--test--activity}

테스트 활동을 통해 게재를 전송해야 하는지 또는 모니터링 워크플로우가 &quot;대기&quot; 활동을 기반으로 다른 주기를 실행해야 하는지 여부를 결정할 수 있습니다.

세 개의 이벤트 변수 &quot;vars.strWorkflowError&quot;, &quot;vars.strWorkflowPaused&quot; 또는 &quot;vars.strWorkflowStop&quot; 중 하나 이상이 비어 있지 않은 경우, 감독자 **에게 게재가 전송됩니다.**

![](assets/uc_monitoring_workflow_test.png)

정기적인 간격으로 모니터링 워크플로우를 다시 시작하도록 &quot;대기&quot; 활동을 구성할 수 있습니다. 이 사용 사례의 경우 **대기 시간이 1시간으로 설정되어 있습니다**.

![](assets/uc_monitoring_workflow_attente.png)

## 4단계: 게재 준비 {#step-4--preparing-the-delivery}

&quot;게재&quot; 활동은 **리소스 > 템플릿 > 게재 템플릿** 노드에 저장된 **게재 템플릿**&#x200B;을 기반으로 합니다.

이 템플릿에는 다음이 포함되어야 합니다.

* **감독자의 전자 메일 주소**.
* 개인화된 텍스트를 삽입하기 위한 **HTML 콘텐츠**

  ![](assets/uc_monitoring_workflow_variables_diffusion.png)

  선언된 세 변수(WF_Stop, WF_Paused, WF_Error)는 세 워크플로우 이벤트 변수와 일치합니다.

  이러한 변수는 게재 템플릿 속성의 **변수** 탭에서 선언해야 합니다.

  **워크플로 이벤트 변수의 콘텐츠**&#x200B;를 복구하려면 JavaScript 코드에서 반환된 값으로 초기화될 게재와 관련된 변수를 선언해야 합니다.

  게재 템플릿에는 다음 콘텐츠가 있습니다.

  ![](assets/uc_monitoring_workflow_model_diffusion.png)

템플릿을 만들고 승인했으면 **게재** 활동을 다음과 같이 구성해야 합니다.

* 이전에 만든 게재 템플릿에 &quot;게재&quot; 활동을 연결합니다.
* 워크플로우의 이벤트 변수를 게재 템플릿과 관련된 변수에 연결합니다.

**배달** 활동을 두 번 클릭하고 다음 옵션을 선택합니다.

* 게재: **새로 만들기, 템플릿에서 만들기**&#x200B;를 선택하고 이전에 만든 게재 템플릿을 선택합니다.
* **수신자 및 콘텐츠** 필드에 대해 **게재에 지정됨**&#x200B;을(를) 선택합니다.
* 실행할 작업: **준비 및 시작**&#x200B;을(를) 선택합니다.
* **오류 처리** 옵션을 선택 취소합니다.

  ![](assets/uc_monitoring_workflow_optionmodel.png)

* **배달** 활동의 **스크립트** 탭으로 이동하여 개인화 필드 메뉴를 통해 세 개의 **문자열** 형식 변수를 추가하십시오.

  ![](assets/uc_monitoring_workflow_selectlinkvariables.png)

  ![](assets/uc_monitoring_workflow_linkvariables.png)

  선언된 세 가지 변수는 다음과 같습니다.

  ```
  delivery.variables._var[0].stringValue = vars.strWorkflowError;
  delivery.variables._var[1].stringValue = vars.strWorkflowPaused;
  delivery.variables._var[2].stringValue = vars.strWorkflowStop; 
  ```

이 모니터링 워크플로우가 시작되면 수신자에게 다음 요약을 보냅니다.

![](assets/uc_monitoring_workflow_mailfinal.png)
