---
product: campaign
title: 워크플로우 감독
description: Campaign 워크플로우를 감독하는 방법 알아보기
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: ca6d4bf4-7b3a-4d36-9fc3-0b83531d0132
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 0%

---

# 사용 사례: 워크플로우 관리{#supervising-workflows}

![](../../assets/common.svg)

이 사용 사례에서는 &quot;일시 중지됨&quot;, &quot;중지됨&quot; 또는 &quot;오류 발생&quot;인 워크플로우 집합의 상태를 모니터링할 수 있는 워크플로우 만들기에 대해 자세히 설명합니다.

이것의 목적은 다음과 같습니다.

* 워크플로우를 사용하여 비즈니스 워크플로우 그룹을 모니터링합니다.
* 배달 활동을 통해 감독자에게 메시지를 보냅니다.

워크플로우 세트의 상태를 모니터링하려면 다음 단계를 수행해야 합니다.

1. 모니터링 워크플로우를 만듭니다.
1. 워크플로우의 일시 중지, 중지 또는 오류 여부를 판별하려면 JavaScript를 작성합니다.
1. **[!UICONTROL Test]** 활동을 만듭니다.
1. 게재 템플릿을 준비합니다.

>[!NOTE]
>
>워크플로우 외에도 캠페인 **워크플로우 Heatmap**&#x200B;을 사용하면 현재 실행 중인 워크플로우의 세부 정보에서 분석할 수 있습니다. 자세한 내용은 [전용 섹션](heatmap.md)을 참조하십시오.
>
>**워크플로우의 실행을 모니터링하는 방법에 대한 자세한 내용은 [이 섹션](monitoring-workflow-execution.md)을 참조하십시오.**

## 1단계: 모니터링 워크플로우 만들기 {#step-1--creating-the-monitoring-workflow}

모니터링할 워크플로우 폴더는 **관리 > 프로덕션 > 기술 워크플로우** 노드에 저장된 **&quot;CustomWorkflows&quot;** 폴더입니다. 이 폴더에는 비즈니스 워크플로우가 포함되어 있습니다.

**모니터링 워크플로우**&#x200B;는 기술 워크플로우 폴더의 루트에 저장됩니다. 사용된 레이블은 **&quot;Monitoring&quot;**&#x200B;입니다.

다음 스키마는 활동의 시퀀스를 보여줍니다.

![](assets/uc_monitoring_workflow_overview.png)

이 워크플로우는 다음과 같이 구성됩니다.

* **&quot;시작&quot;** 활동.
* 비즈니스 워크플로우 폴더 분석을 담당하는 **&quot;JavaScript 코드&quot;** 활동.
* **&quot;Test&quot;** 활동을 통해 감리자에게 게재를 보내거나 워크플로우를 다시 시작합니다.
* 메시지 레이아웃을 담당하는 **&quot;배달&quot;** 활동.
* 워크플로우 반복 간의 리드 타임을 제어하는 **&quot;Wait&quot;** 활동.

## 2단계: JavaScript 작성 {#step-2--writing-the-javascript}

JavaScript 코드의 첫 번째 부분은 &quot;pause&quot;(@state = 13), &quot;error&quot;(@failed = 1) 또는 &quot;stoped&quot;(@state = 20) 상태로 워크플로우를 식별할 수 있는 **쿼리(queryDef)**&#x200B;와 일치합니다.

모니터링할 워크플로우 폴더의 **내부 이름**&#x200B;은 다음과 같은 조건에 있습니다.

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

JavaScript 코드의 두 번째 부분에서는 쿼리 중에 복구된 상태에 따라 각 워크플로우&#x200B;**에 대한 메시지를 표시할 수 있습니다.**

>[!NOTE]
>
>만든 문자열은 워크플로우의 이벤트 변수에 로드해야 합니다.

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

## 3단계: 테스트 활동 만들기 {#step-3--creating-the--test--activity}

테스트 활동을 사용하면 게재를 전송해야 하는지 또는 모니터링 워크플로우가 &quot;대기&quot; 활동을 기반으로 다른 주기를 실행해야 하는지 여부를 결정할 수 있습니다.

세 개의 이벤트 변수 &quot;vars.strWorkflowError&quot;, &quot;vars.strWorkflowPaused&quot; 또는 &quot;vars.strWorkflowStop&quot;이 void가 아닌 경우 수퍼바이저 **에 게재를 보냅니다.**

![](assets/uc_monitoring_workflow_test.png)

모니터링 워크플로우를 정기적으로 다시 시작하도록 &quot;대기&quot; 활동을 구성할 수 있습니다. 이 사용 사례에서는 대기 시간이 1시간&#x200B;**으로 설정됩니다.**

![](assets/uc_monitoring_workflow_attente.png)

## 4단계: 게재 준비 {#step-4--preparing-the-delivery}

배달 활동은 **리소스 > 템플릿 > 배달 템플릿** 노드에 저장된 **배달 템플릿**&#x200B;을 기반으로 합니다.

이 템플릿에는 다음이 포함되어야 합니다.

* **관리자의 이메일 주소입니다**.
* **개인화된** 텍스트를 삽입하기 위한 HTML 콘텐츠.

   ![](assets/uc_monitoring_workflow_variables_diffusion.png)

   선언된 세 개의 변수(WF_Stop, WF_Paused, WF_Error)는 세 개의 워크플로우 이벤트 변수와 일치합니다.

   이러한 변수는 게재 템플릿 속성의 **변수** 탭에서 선언해야 합니다.

   워크플로우 이벤트 변수의 **컨텐츠를 복구하려면 JavaScript 코드에서 반환한 값으로 초기화할 게재에 대한 변수를 선언해야 합니다.**

   게재 템플릿에는 다음 컨텐츠가 있습니다.

   ![](assets/uc_monitoring_workflow_model_diffusion.png)

템플릿이 생성되어 승인되면 **배달** 활동을 구성해야 합니다.

* &quot;배달&quot; 활동을 이전에 만든 게재 템플릿에 연결합니다.
* 워크플로우의 이벤트 변수를 게재 템플릿과 관련된 변수에 연결합니다.

**배달** 활동을 두 번 클릭하고 다음 옵션을 선택합니다.

* 배달: **템플릿**&#x200B;에서 생성된 새로 만들기를 선택하고 이전에 만든 게재 템플릿을 선택합니다.
* **수신자 및 콘텐츠** 필드의 경우 **게재**&#x200B;에 지정됨 을 선택합니다.
* 실행할 작업: **준비 및 시작**&#x200B;을 선택합니다.
* **오류 처리** 옵션의 선택을 취소합니다.

   ![](assets/uc_monitoring_workflow_optionmodel.png)

* **배달** 활동의 **스크립트** 탭으로 이동하여 개인화 필드 메뉴를 통해 세 개의 **문자 문자열** 유형 변수를 추가합니다.

   ![](assets/uc_monitoring_workflow_selectlinkvariables.png)

   ![](assets/uc_monitoring_workflow_linkvariables.png)

   선언된 세 가지 변수는 다음과 같습니다.

   ```
   delivery.variables._var[0].stringValue = vars.strWorkflowError;
   delivery.variables._var[1].stringValue = vars.strWorkflowPaused;
   delivery.variables._var[2].stringValue = vars.strWorkflowStop; 
   ```

이 모니터링 워크플로우가 실행되면 수신자에게 다음 요약을 전송합니다.

![](assets/uc_monitoring_workflow_mailfinal.png)
