---
product: campaign
title: Apple의 메일 앱에서의 메일 개인 정보 보호
description: 캠페인이 Apple의 메일 개인 정보 보호 기능의 영향을 받는 방식을 알아봅니다
exl-id: e044b35a-b49f-408a-900d-2afe8ff10212
source-git-commit: 1a9e0f8bf374e10af938d15dcebe943819ae327b
workflow-type: tm+mt
source-wordcount: '2100'
ht-degree: 1%

---

# Apple의 메일 앱에서의 메일 개인 정보 보호

![v7 및 v8에 적용됩니다](../../assets/common.svg)

## 변경 사항

2021년에 Apple은 네이티브 메일 앱에 대한 새로운 개인 정보 보호 기능을 도입했습니다. 이제 이 앱에는 Apple의 메일 개인 정보 보호 기능이 포함되어 있습니다. 기본적으로 보낸 사람은 더 이상 추적 픽셀을 사용하여 Apple의 메일 개인 정보 보호 기능을 사용하도록 선택한 수신자에 대한 정보를 수집할 수 없습니다. [자세한 내용](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/apple-mail-privacy-faq.html?lang=ko){target=&quot;_blank&quot;}.

## 캠페인이 어떤 영향을 받습니까?

Adobe Campaign은 전자 메일 열기 수를 추적하기 위해 픽셀 추적 기능을 사용하는 기능을 제공합니다. 이 기능은 타깃팅 및 캠페인뿐만 아니라 지표에도 사용할 수 있습니다. 예를 들어 이메일 오픈율을 사용하여 캠페인 효율성 및 사용자 참여를 측정할 수 있습니다. 즉, 세그먼테이션, 타깃팅 및 지표가 캠페인에서 영향을 받을 수 있습니다. [자세한 내용](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/apple-mail-privacy-faq.html#in-addition-to-measuring-opens%2C-what-else-is-impacted%3F){target=&quot;_blank&quot;}.

## 어떤 작업을 수행해야 합니까?

Apple의 새로운 기능은 이메일 개인 정보 보호 측면에서 업계에서 채택할 여러 가지 기능입니다. Adobe의 권장 사항을 따르는 것이 좋습니다.

### 캠페인 트리거에 미치는 영향 평가

이러한 변경 사항이 현재 캠페인 트리거에 어떤 영향을 미치는지 평가합니다. 이메일 열기 수를 세그멘테이션, 타겟팅 또는 재타겟팅의 기준으로 사용하는 워크플로우를 식별합니다. 다음 문서를 참조하십시오. [팁과 트릭](#find-email-open-tracking).

### 데이터 유지

데이터를 보존하고 현재 지식을 장치에 통합합니다. 사용자 에이전트의 주요 성능 지표(KPI)를 기반으로 할 수 있습니다. 예를 들어 iOS 및 Apple의 메일 앱을 사용하는 사람의 프로필에 대한 KPI를 작성할 수 있습니다. 다음 문서를 참조하십시오. [팁과 트릭](#preserve-tracking-data).

### 추적 로그를 보존 기간 이상으로 보관합니다.

Adobe Campaign의 보존 기간을 초과하여 추적 로그를 보관합니다.

1. 캠페인 인스턴스에서 유지 기간 기간을 확인합니다.
1. 활성 대상 매핑을 다시 확인하십시오. 기본 제공 프로필 테이블(`nmsRecipient`).
1. Adobe Campaign에서 추적 로그를 내보냅니다. 사용자 에이전트 및 운영 체제에 대한 데이터가 포함된 로그를 포함합니다.

### 현재 공개 비율의 추세 평가

iOS 장치에서 Apple의 메일 앱을 사용하는 대상의 비율을 결정합니다.
이 평가를 사용하여, 잠재적인 예외적인 틈새 및 그 원인을 식별할 수 있습니다. 간격이 캠페인 성과 문제로 인한 것인지, Apple의 개인 정보 보호 기능으로 인한 것인지를 결정할 수 있습니다. 다음 문서를 참조하십시오. [팁과 트릭](#measure-ios-footprint).

### 캠페인 전략 및 성능 지표 재평가

무엇보다 캠페인 전략과 캠페인 성과 지표를 미리 재평가하는 것이 좋습니다. 클릭스루, 제품 보기 및 구매와 같이 더 안정적인 지표를 참조할 수 있습니다.

현재 사용 가능한 데이터를 살펴보고 공개 비율과 다른 지표 간의 상관관계를 평가하는 것이 좋습니다. 이러한 지표가 일관되게 상호 관련이 있는 경우 높은 수준의 신뢰도로 트리거를 개선할 수 있습니다.

## 팁과 트릭

### 전체 iOS 사용 공간 측정 {#measure-ios-footprint}

Adobe Campaign 데이터에서 통찰력을 얻으려면 기본 제공 보고서를 사용할 수 있습니다.

* **[!UICONTROL Operating Systems]** 보고서

   운영 체제 및 버전당 방문자 수를 식별하려면 이 보고서를 사용합니다. [자세한 내용](../../reporting/using/global-reports.md#operating-systems).

   총 방문자 수와 관련하여 운영 체제당 방문자 수 분류를 볼 수 있습니다.

   ![](../../reporting/using/assets/s_ncs_user_os_report.png)

   각 운영 체제에 대해 운영 체제 버전당 방문자 분류를 볼 수 있습니다.

   ![](../../reporting/using/assets/s_ncs_user_os_report2.png)

* **[!UICONTROL Breakdown of opens]** 보고서

   운영 체제당 이메일 열기 비율을 식별하려면 이 보고서를 사용합니다. [자세한 내용](../../reporting/using/global-reports.md#breakdown-of-opens).

   ![](../../reporting/using/assets/dlv_useragent_report.png)

### 이메일 열기 추적 사용 방법 확인 {#find-email-open-tracking}

이메일 열기 수를 세그멘테이션, 타겟팅 및 재타겟팅의 기준으로 사용하는 워크플로우를 식별할 수 있습니다.

이렇게 하려면 **[!UICONTROL type]** 추적된 링크 URL(**[!UICONTROL url/@type]**). 전자 메일 오픈의 경우 이 속성은 **[!UICONTROL Open]**. 이 속성은 쿼리 편집기, **[!UICONTROL Query]** 워크플로우 활동 및 사전 정의된 필터. 이 속성을 마케팅 캠페인에 대한 타깃팅 기준으로 사용할 수 있습니다.

![](assets/identify-email-open-tracking-1.png)

이 예에서는 마케터가 최근 7일 이내에 특정 게재 이메일을 열고 지난 달에 구입한 수신자에게 포상 오퍼를 보내려고 합니다. 워크플로우 쿼리에서는 다음과 같은 다양한 방법으로 이메일 열기를 사용할 수 있습니다.

* 쿼리에서 이메일 열기 수를 타겟팅 기준으로 사용할 수 있습니다.

   특정 게재의 추적 로그 URL 유형을 필터링 조건으로 지정할 수 있습니다 **[!UICONTROL Open]**.

   ![](assets/identify-email-open-tracking-2.png)

* 사전 정의된 필터를 사용할 수 있습니다. [자세히 알아보기](../../workflow/using/creating-a-filter.md)

   ![](assets/identify-email-open-tracking-3.png)

   워크플로우의 쿼리 활동에서 이 사전 정의된 필터를 사용할 수 있습니다.

   ![](assets/identify-email-open-tracking-4.png)

   >[!NOTE]
   >
   >워크플로우에서는 사전 정의된 필터의 타깃팅 기준을 볼 수 없습니다.

이메일을 여는 워크플로우가 타겟팅 기준으로 사용되는 목록을 검색하려면 `xtk:workflow` 스키마. 워크플로우의 컨텐츠는 **[!UICONTROL XML memo (data)]** XML 형식의 필드입니다.

![](assets/identify-email-open-tracking-5.png)

워크플로우에 이 컨텐츠가 포함되어야 한다고 지정할 수 있습니다.

`expr="[url/@type] = 2"`

이 타깃팅 기준은 추적된 URL의 유형을 **[!UICONTROL Open]**.

![](assets/identify-email-open-tracking-6.png)

#### 구현 및 샘플 패키지의 예

이 구현 예를 사용하여 이메일 열기 수가 타겟팅 기준으로 사용되는 워크플로우를 식별하고 선택한 캠페인 운영자에게 알림을 보낼 수 있습니다. 이 구현을 다음과 같은 용도로 사용할 수 있습니다.

* 타겟팅 워크플로우에서 이메일 열기 수에서 다른 KPI로 전환하는 잠재적 영향을 측정할 수 있습니다. 이메일 열기를 사용하지 않는 경우 추가 작업이 필요하지 않습니다.
* 구현을 재평가할 때 이 예제를 사용하여 워크플로우를 건너뛸 수 있습니다.

이 예는 단일 기술 워크플로우에 있는 사용자 지정 구현을 보여줍니다.

![](assets/identify-email-open-wkf-1.png)

>[!IMPORTANT]
>
>패키지는 예로만 제공되며 제품 기능으로 Adobe에서 지원하지 않습니다.
>
>샘플 코드를 캠페인 구현에 조정해야 할 수 있습니다.
>
>최종 사용자는 이 샘플 패키지를 설치하고 사용할 유일한 책임이 있습니다.
>
>비프로덕션 환경에서 이 패키지를 테스트하고 유효성을 검사하는 것이 좋습니다.

다운로드 [샘플 패키지](assets/PKG_Search_workflows_using_Opens_in_queries_V1.xml) 설치하고 [자세히 알아보기](../../platform/using/working-with-data-packages.md#importing-packages)

패키지를 설치한 후 인스턴스에 기본 제공 기술 워크플로우가 포함된 폴더에서 워크플로우에 액세스할 수 있습니다.

`/Administration/Production/Technical workflows/nmsTechnicalWorkflow`

사용자 인터페이스에서 을(를) 선택합니다. **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

![](assets/identify-email-open-tracking-8.png)

워크플로우는 다음 주요 단계로 구성됩니다.

1. 이메일을 여는 워크플로우가 타겟팅 기준으로 사용되는 워크플로우를 나열합니다.
1. 이메일이 열리는 사전 정의된 필터를 타깃팅 기준으로 나열합니다.
1. 미리 정의된 이러한 필터가 사용되는 워크플로우를 나열합니다.
1. 두 워크플로우 목록을 하나의 목록으로 병합합니다.
1. 지정된 연산자에게 이메일 알림을 보냅니다.

워크플로우는 다음과 같은 세부 단계로 구성됩니다.

1. 초기 활동은 의 쿼리 활동입니다 `xtk:workflow` 스키마. 이 활동은 인스턴스에 따라 이메일을 포함하는 명시적 워크플로우 쿼리를 타겟팅 기준으로 여는 데 사용됩니다.

   ![](assets/identify-email-open-tracking-9.png)

   ![](assets/identify-email-open-tracking-10.png)

   ![](assets/identify-email-open-tracking-11.png)

   그 결과 워크플로우 목록이 반환됩니다.

   ![](assets/identify-email-open-tracking-12.png)

   이 정보는 재사용되므로 작업 테이블의 이름은 글로벌 워크플로우 인스턴스 변수에 저장됩니다.

   ![](assets/identify-email-open-tracking-13.png)

1. 두 번째 쿼리는 전자 메일 열기를 포함하는 사전 정의된 필터를 찾는 데 사용됩니다.

   ![](assets/identify-email-open-tracking-14.png)

   ![](assets/identify-email-open-tracking-15.png)

   ![](assets/identify-email-open-tracking-16.png)

   사전 정의된 필터 목록이 결과로 반환됩니다.

   ![](assets/identify-email-open-tracking-17.png)

1. 이 사전 정의된 필터 목록은 이러한 필터가 사용되는 워크플로우를 찾는 데 사용됩니다.
1. 두 워크플로우 목록이 하나의 목록으로 병합됩니다.

   이를 위해 JavaScript 코드가 사용됩니다.

   ![](assets/identify-email-open-tracking-18.png)

   ```javascript
   const queryPredFilter = xtk.queryDef.create(
     <queryDef schema={vars.targetSchema} operation="select">
        <select>
          <node alias="@id" expr="@id" />
          <node alias="@name" expr="@name"  />
        </select>
        <where/>
     </queryDef>
       ).ExecuteQuery()
   
   var qDef =
     <queryDef schema="xtk:workflow" operation="select">
       <select>
         <node expr="@id"/>
         <node expr="@internalName"/>
         <node expr="@label"/>
       </select>
       <where>
         <condition boolOperator="OR" expr={"data like '%expr=[url/@type] = 2%'" }/>
       </where>
     </queryDef>
   
   for each (var filter in queryPredFilter) {       
   
      //logInfo (filter.@name);
      var condition;
      condition =<condition boolOperator="OR" expr={"data like '%" + filter.@name + "%'" }/>
      qDef.where.appendChild(condition);   
   
   }
   
   var queryWorkflowList = xtk.queryDef.create(qDef);
   var workflowList = queryWorkflowList.ExecuteQuery();
   
   var sWorkflowList = "";
   var iCount = 0
   for each (var workflow in workflowList) {       
   
      //logInfo ("Workflow ID: " + workflow.@id + " in " + instance.vars.mainTargetSchema);
   
      iWorkflowId = workflow.@id;
      iWorkflowName = workflow.@internaName;
      iWorkflowLabel = workflow.@label;
   
       xtk.session.Write(
             <{instance.vars.mainTargetSchema.split(':')[1]}
               _operation="insertOrUpdate"       
               _key="@id"
               xtkschema={instance.vars.mainTargetSchema}
               id={iWorkflowId}
               internaName={iWorkflowName}
               label={iWorkflowLabel}
             />
       )
   }
   ```

1. 병합된 목록에서 중복 워크플로우가 제거됩니다.

   ![](assets/identify-email-open-tracking-19.png)

1. 목록이 비어 있지 않은지 테스트를 수행합니다.

   ![](assets/identify-email-open-tracking-20.png)

   목록이 비어 있지 않으면 이메일 알림을 위한 HTML 테이블에 삽입됩니다.

   ![](assets/identify-email-open-tracking-21.png)

   ```js
   const queryWorkflow = xtk.queryDef.create(
       <queryDef schema={vars.targetSchema} operation="select">
           <select>
               <node alias="@id" expr="@id" />
               <node alias="@internalName" expr="@internalName"  />
               <node alias="@label" expr="@label"  />
           </select>
           <where/>
       </queryDef>
   ).ExecuteQuery()
   
   var sWorkflowList = '<table border="0" >';
   
   sWorkflowList = sWorkflowList + "<tr><th>Worklow Id</th><th>Name</th><th>Label</th></tr>";
   
   for each (var workflow in queryWorkflow) {       
   
      sWorkflowList = sWorkflowList + "<tr>" +
                       "<td>" + workflow.@id + "</td>" +
                       "<td>" + workflow.@internalName + "</td>" +
                       "<td>" + workflow.@label + "</td>" +
                       "</tr>";
   
   }
   
   sWorkflowList = sWorkflowList + "</table>";
   
   instance.vars.workflowList = sWorkflowList;
   ```

1. HTML 테이블이 알림 템플릿에 추가됩니다.

   ```js
   <%= instance.vars.workflowLIst%>
   ```

   ![](assets/identify-email-open-tracking-22.png)

   이메일 알림에는 쿼리에 타겟팅 기준으로 이메일 열기를 포함하는 워크플로우 목록이 포함되어 있습니다.

   ![](assets/identify-email-open-tracking-23.png)

### 현재 추적 데이터 유지 {#preserve-tracking-data}

#### 영향을 받는 데이터

프로필 데이터는 이메일 열기 및 클릭스루와 같은 작업의 추적 데이터로 보강됩니다. 또한 추적은 이 정보가 사용 가능한 경우 사용자 에이전트를 통해 사용자 장치에 대한 주요 정보를 제공합니다.

간단히 말해 Adobe Campaign 추적 데이터는 다음 정보를 제공합니다.

* 특정 이메일 메시지를 통해 열거나 클릭한 사람과 연결된 프로필입니다
* 개설 날짜
* 사용된 장치(예: iPhone 또는 Mac)
* 운영 체제 및 버전(예: iOS 15, macOS 12 또는 Windows 10)
* 메일 응용 프로그램이나 웹 브라우저와 같은 응용 프로그램과 버전(예: Outlook 2019)

#### 추적 데이터를 유지해야 하는 이유는 무엇입니까?

다음과 같은 여러 가지 이유로 이 데이터를 유지하는 것이 좋습니다.

* 이 데이터는 Adobe Campaign에 의해 제한된 기간 동안 유지됩니다. 보존 기간은 인스턴스의 구성에 따라 다릅니다.

   인스턴스의 설정을 확인합니다. [자세한 내용](../../platform/using/privacy-management.md#data-retention).

* Apple의 최근 변경 사항 외에 추적 데이터를 사용하여 대상의 참여를 유도할 수 있는 엄청난 가치를 추가할 수 있습니다.
* Apple은 자체 이메일 앱 및 메일 개인 정보 보호 기능에 대한 추가 변경 사항을 가져올 수 있습니다.

이러한 모든 이유로 가능한 한 빨리 이 데이터를 내보내는 것이 좋습니다. 그렇지 않으면 대상의 일부에 대한 추적 데이터가 부정적인 영향을 받을 수 있습니다.

#### 추적 데이터를 유지하려면 어떻게 해야 합니까?

추적 데이터를 보존하려면 Adobe Campaign에서 정보 시스템으로 내보내야 합니다. [자세한 내용](../../platform/using/get-started-data-import-export.md).

>[!IMPORTANT]
>
>다음 예제는 기본 제공 `nms:Recipient` 스키마: 기본 프로필 스키마. 사용자 지정 프로필에 첨부된 추가 사용자 지정 대상 매핑을 사용하는 경우 이 내보내기 전략을 모든 사용자 지정 로그 표로 확장하는 것이 좋습니다. [자세한 내용](../../configuration/using/target-mapping.md).

##### 원칙

기본적으로 `nms:Recipient` 스키마는 내보내야 하는 세 개의 스키마에 연결되어 있습니다.

| 스키마 | 컨텐츠 |
| --- | --- |
| nms:trackingLogRcp | 데이터 추적, 즉 사용자, 시간 및 관련 메시지 |
| nms:trackingUrl | 전자 메일 열기 또는 클릭스루 등 링크에 대한 세부 사항 |
| nms:userAgent | 장치에 대한 정보 |

표는 데이터 모델에 연결됩니다.

![](assets/data-schema-for-tracking-data.png)

이러한 관계를 사용하여 단일 내보내기 쿼리를 만듭니다.

![](assets/export-tracking-data-1.png)

연결된 스키마의 유용한 정보를 사용하여 이 데이터를 보강할 수 있습니다.

| 스키마 | 컨텐츠 |
| --- | --- |
| nms:Recipient | 프로필과 관련된 세부 사항입니다 |
| nms:배달 | 사용자가 반응한 메시지에 대한 정보입니다 |

Adobe Campaign에서 지원하는 외부 스토리지 솔루션으로 결과를 내보낼 수 있습니다.

* SFTP
* S3
* Azure Blob

##### 구현

이 예는 Adobe Campaign에서 추적 데이터를 내보내는 방법을 보여줍니다.

1. 쿼리로 시작하는 워크플로우를 만듭니다.

   초기 쿼리는 지난 3개월 동안의 추적 로그를 검색하는 데 사용됩니다.
증분 쿼리를 사용하여 아직 내보내지 않은 레코드만 추출할 수 있습니다.

   에서 필요한 모든 정보를 추가합니다. **[!UICONTROL Additional data]** 노드 아래에 있어야 합니다.

   ![](assets/export-tracking-data-2.png)

1. 추가 **[!UICONTROL Data extraction (file)]** 활동. 쿼리의 모든 데이터를 추출 파일 형식에 매핑합니다.

   ![](assets/export-tracking-data-3.png)

   파일 형식(예: TXT 또는 CSV)을 선택합니다.

   ![](assets/export-tracking-data-4.png)

1. 지원되는 스토리지 솔루션에 파일을 업로드하기 위한 세 번째 및 마지막 활동을 추가합니다.

![](assets/export-tracking-data-5.png)

##### 고급 구현: iOS 장치별 분류

워크플로우를 사용하여 수신자가 Apple의 메일 앱을 사용하는지 여부를 결정할 수 있습니다. 추적 로그를 장치별로 분할할 수 있습니다. 예를 들어 쿼리 필터를 사용하여 iOS 장치별로 레코드를 분류할 수 있습니다.

| 애플리케이션 | 운영 체제 또는 장치  | 쿼리 필터 |
| --- | --- | --- |
| Apple 메일 | iOS 15 | `operating System (Browser) contains 'iOS 15' and browser (Browser) contains 'ApplewebKit'` |
| Apple 메일 | iOS 14 또는 iOS 13 | `browser contains 'AppleWebKit' and operating System of browser contains 'iOS 14' or operating System of browser contains 'iOS 13'` |
| Apple 메일 | iOS 모바일 장치: iPad, iPod 및 iPhone | `device (Browser) contains iPhone or device (Browser) equal to iPod or device (Browser) equal to iPad and browser (Browser) equal to 'AppleWebKit'` |
| Apple 메일 | iPhone , iPad 또는 iPod | `browser (Browser) equal to 'AppleWebKit' and device (Browser) equal to iPhone or device (Browser) equal to iPod or device (Browser) equal to iPad` |
| Apple 메일 | Mac | `browser (Browser) equal to 'AppleWebKit' and operating System (Browser) contains 'Mac'` |
| Safari | macOS | `browser (Browser) equal to 'Safari' and device (Browser) equal to PC and operating System (Browser) contains 'Mac'` |
| Safari | 모바일 장치 | `browser (Browser) equal to 'Safari' and device (Browser) equal to iPad or device (Browser) equal to iPod or device (Browser) equal to iPhone` |

![](assets/export-tracking-data-6.png)

이러한 규칙은 다음과 같이 다양한 용도로 사용할 수 있습니다.

* 외부 스토리지 솔루션으로 데이터 내보내기 및 아카이빙
* 프로필에 첨부할 KPI를 계산합니다
* 제외 목록 만들기
* 보고

다음 예에서는 워크플로우를 사용하여 iOS 장치별로 레코드를 분류하는 방법을 보여줍니다.

* 첫 번째 예제 워크플로우는 다음 활동으로 구성됩니다.

   1. 초기 **[!UICONTROL Query]** 활동은 최근 3개월 동안 열린 모든 이메일을 선택하는 데 사용됩니다.
   1. A **[!UICONTROL Split]** 활동은 이메일 애플리케이션, 브라우저, 운영 체제 및 장치별로 선택 항목을 분할하는 데 사용됩니다.

   1. A **[!UICONTROL Deduplication]** 활동은 각각 **[!UICONTROL Split]** 활동. 다음 **[!UICONTROL Deduplication]** 활동은 중복 이메일 주소를 제거하는 데 사용됩니다.

      다음 **[!UICONTROL Deduplication]** 활동은 뒤에 배치됩니다 **[!UICONTROL Split]** 활동은 다양한 장치를 사용하는 수신자에 대한 정보를 유실하지 않도록 합니다.

   1. An **[!UICONTROL End]** 활동은 각각 **[!UICONTROL Deduplication]** 활동.

   이 유형의 워크플로우는 타겟팅을 위해 기본 제공 수신자 테이블에만 수신자를 저장하는 경우에 유용합니다.

   ![](assets/export-tracking-data-wkf-1.png)

* 두 번째 예제 워크플로우는 다음 활동으로 구성됩니다.

   1. 초기 **[!UICONTROL Query]** 활동은 최근 3개월 동안 열린 모든 이메일을 선택하는 데 사용됩니다.
   1. A **[!UICONTROL Deduplication]** 활동은 중복 이메일 주소를 제거하는 데 사용됩니다.
   1. A **[!UICONTROL Fork]** 활동이 사용됨:

      * 한 전환에서 **[!UICONTROL Change dimension]** 활동은 추적 로그가 참조하는 수신자를 찾는 데 사용됩니다.
      * 다른 전환에서 **[!UICONTROL Split]** 활동은 이메일 애플리케이션, 브라우저, 운영 체제 및 장치별로 선택 항목을 분할하는 데 사용됩니다.
   1. An **[!UICONTROL End]** 활동은 이후 각 전환을 따릅니다 **[!UICONTROL Split]** 활동.

   이 유형의 워크플로우는 기본 제공 수신자 테이블 이외의 표에 수신자를 저장하는 경우에 유용합니다.

   ![](assets/export-tracking-data-wkf-2.png)

## 유용한 링크

[Apple 메일 개인 정보 보호 FAQ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/apple-mail-privacy-faq.html){target=&quot;_blank&quot;}
