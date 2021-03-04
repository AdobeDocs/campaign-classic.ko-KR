---
solution: Campaign Classic
product: campaign
title: 워크플로우 감독
description: 캠페인 워크플로우를 관리하는 방법 학습
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 11ff62238a8fb73658f2263c25dbeb27d2e0fb23
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 0%

---


# 사용 사례:워크플로우 관리{#supervising-workflows}

이 사용 사례에서는 &quot;일시 중지됨&quot;, &quot;중지됨&quot; 또는 &quot;오류가 있는 워크플로우 집합 상태를 모니터링할 수 있는 워크플로우 만들기에 대해 자세히 설명합니다.

이것의 목적은 다음과 같다.

* 워크플로우를 사용하여 비즈니스 워크플로우 그룹을 모니터링할 수 있습니다.
* &quot;전달&quot; 활동을 통해 관리자에게 메시지를 보냅니다.

워크플로우 세트의 상태를 모니터링하려면 다음 단계를 따라야 합니다.

1. 모니터링 워크플로우를 만듭니다.
1. JavaScript를 작성하여 워크플로우가 일시 중지되었는지, 중지되었는지 또는 오류인지 확인합니다.
1. **[!UICONTROL Test]** 활동을 만듭니다.
1. 배달 템플릿을 준비합니다.

>[!NOTE]
>
>워크플로우 외에도 캠페인 **워크플로우 히트맵**&#x200B;을 사용하면 현재 실행 중인 워크플로우의 세부 정보를 분석할 수 있습니다. 자세한 내용은 [전용 섹션](../../workflow/using/heatmap.md)을 참조하십시오.
>
>**워크플로우의 실행**&#x200B;을 모니터링하는 방법에 대한 자세한 내용은 [이 섹션](../../workflow/using/monitoring-workflow-execution.md)을 참조하십시오.

## 1단계:모니터링 워크플로우 만들기 {#step-1--creating-the-monitoring-workflow}

모니터링하려는 워크플로 폴더는 **관리 > 프로덕션 > 기술 워크플로** 노드에 저장된 **&quot;CustomWorkflows&quot;** 폴더입니다. 이 폴더에는 일련의 비즈니스 워크플로우가 포함되어 있습니다.

**모니터링 워크플로**&#x200B;는 기술 워크플로 폴더의 루트에 저장됩니다. 사용된 레이블은 **&quot;모니터링&quot;**&#x200B;입니다.

다음 스키마는 활동 시퀀스를 보여줍니다.

![](assets/uc_monitoring_workflow_overview.png)

이 워크플로우는 다음과 같이 구성됩니다.

* **&quot;시작&quot;** 활동.
* 비즈니스 워크플로우 폴더 분석을 담당하는 **&quot;JavaScript code&quot;** 활동.
* **&quot;Test&quot;** 활동 - 배달을 감독자에게 보내거나 워크플로우를 다시 시작합니다.
* 메시지 레이아웃을 담당하는 **&quot;배달&quot;** 활동.
* 워크플로우 반복 간의 리드 시간을 제어하는 **&quot;Wait&quot;** 활동

## 2단계:JavaScript {#step-2--writing-the-javascript} 작성

JavaScript 코드의 첫 번째 부분은 &quot;일시 중지&quot;(@state 13), &quot;오류&quot;(@failed 1) 또는 &quot;중지됨&quot;(@state 20) 상태로 워크플로우를 식별할 수 있는 **쿼리(queryDef)**&#x200B;과 일치합니다.

모니터링할 워크플로 폴더의 **내부 이름**&#x200B;이 다음과 같은 조건에 제공됩니다.

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

JavaScript 코드의 두 번째 부분에서는 쿼리 중에 복구된 상태를 기준으로 **각 작업 과정에 대한 메시지를 표시할 수 있습니다**.

>[!NOTE]
>
>만들어진 문자열은 워크플로우의 이벤트 변수에 로드되어야 합니다.

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

## 3단계:&#39;테스트&#39; 작업 {#step-3--creating-the--test--activity} 만들기

&quot;테스트&quot; 활동을 사용하면 배달을 전송해야 하는지 또는 모니터링 워크플로우가 &quot;대기&quot; 활동을 기반으로 다른 주기를 실행해야 하는지 여부를 결정할 수 있습니다.

3개의 이벤트 변수 &quot;vars.strWorkflowError&quot;, &quot;vars.strWorkflowPaused&quot; 또는 &quot;vars.strWorkflowStop&quot; 중 적어도 하나가 void가 아니면 **감독자에게 배달이 전송됩니다.**

![](assets/uc_monitoring_workflow_test.png)

&quot;대기&quot; 활동은 정기적으로 모니터링 워크플로우를 다시 시작하도록 구성할 수 있습니다. 이 사용 사례의 경우 **대기 시간이 1시간**&#x200B;으로 설정됩니다.

![](assets/uc_monitoring_workflow_attente.png)

## 4단계:배달 준비 중 {#step-4--preparing-the-delivery}

&quot;배달&quot; 활동은 **리소스 > 템플릿 > 배달 템플릿** 노드에 저장된 **배달 템플릿**&#x200B;을 기반으로 합니다.

이 템플릿에는 다음이 포함되어야 합니다.

* **관리자의 이메일 주소입니다**.
* **개인화된** 텍스트를 삽입할 수 있는 HTML 컨텐츠

   ![](assets/uc_monitoring_workflow_variables_diffusion.png)

   선언된 3개의 변수(WF_Stop, WF_Paused, WF_Error)는 3개의 워크플로우 이벤트 변수와 일치합니다.

   이러한 변수는 배달 템플릿 속성의 **변수** 탭에서 선언해야 합니다.

   워크플로 이벤트 변수&#x200B;**의 내용을 복구하려면 JavaScript 코드에서 반환되는 값으로 초기화될 전달에 관련된 변수를 선언해야 합니다.**

   배달 템플릿에는 다음 컨텐츠가 있습니다.

   ![](assets/uc_monitoring_workflow_model_diffusion.png)

템플릿이 만들어지고 승인되면 **배달** 활동을 다음과 같이 구성해야 합니다.

* &quot;배달&quot; 활동을 이전에 만든 배달 템플릿에 연결합니다.
* 워크플로우의 이벤트 변수를 배달 템플릿과 관련된 변수에 연결합니다.

**배달** 활동을 두 번 클릭하고 다음 옵션을 선택합니다.

* 배달:**템플릿**&#x200B;에서 새로 만들기를 선택하고 이전에 만든 배달 템플릿을 선택합니다.
* **받는 사람 및 콘텐트** 필드에 **배달**&#x200B;에 지정된 항목을 선택합니다.
* 실행할 작업:**준비 및 시작**&#x200B;을 선택합니다.
* **프로세스 오류** 옵션의 선택을 취소합니다.

   ![](assets/uc_monitoring_workflow_optionmodel.png)

* **배달** 활동의 **스크립트** 탭으로 이동하여 개인화 필드 메뉴를 통해 3개의 **문자 문자열** 유형 변수를 추가합니다.

   ![](assets/uc_monitoring_workflow_selectlinkvariables.png)

   ![](assets/uc_monitoring_workflow_linkvariables.png)

   선언된 3가지 변수는 다음과 같습니다.

   ```
   delivery.variables._var[0].stringValue = vars.strWorkflowError;
   delivery.variables._var[1].stringValue = vars.strWorkflowPaused;
   delivery.variables._var[2].stringValue = vars.strWorkflowStop; 
   ```

이 모니터링 워크플로우가 실행되면 수신자에게 다음 요약을 전송합니다.

![](assets/uc_monitoring_workflow_mailfinal.png)

