---
product: campaign
title: 이벤트 구성
description: 사용자 지정 구현을 위한 이벤트를 구성하는 방법 알아보기
audience: integrations
content-type: reference
exl-id: 13717b3b-d34a-40bc-9c9e-dcf578fc516e
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 0%

---

# 사용자 지정 구현을 위한 이벤트 구성 {#events}

이 구성의 일부는 사용자 정의 개발이며, 다음을 필요로 합니다.

* Adobe Campaign의 JSON, XML 및 Javascript 구문 분석에 대한 작업 지식입니다.
* QueryDef 및 작성기 API에 대한 작업 지식.
* 개인 키를 사용한 암호화 및 인증의 작업 개념.

Javascript 코드를 편집하려면 기술 기술이 필요하므로 적절한 이해 없이 시도하지 마십시오.

## JavaScript에서 이벤트 처리 {#events-javascript}

### JavaScript 파일 {#file-js}

파이프라인은 JavaScript 함수를 사용하여 각 메시지를 처리합니다. 이 함수는 사용자가 정의합니다.

JSConnector&quot; 특성 아래의 **[!UICONTROL NmsPipeline_Config]** 옵션에 구성됩니다. 이 javascript는 이벤트가 수신될 때마다 호출됩니다. [!DNL pipelined] 프로세스에 의해 실행됩니다.

샘플 Javascript 파일은 cus:triggers.js입니다.

### JavaScript 함수 {#function-js}

[!DNL pipelined] Javascript는 특정 함수로 시작해야 합니다.

이 함수는 모든 이벤트에 대해 한 번 호출됩니다.

```
function processPipelineMessage(xmlTrigger) {}
```

다음과 같이 반환됩니다

```
<undefined/>
```

Javascript를 편집한 후 [!DNL pipelined]을 다시 시작해야 합니다.

### 데이터 형식 {#trigger-format} 트리거

[!DNL trigger] 데이터는 XML 형식으로 JS 함수에 전달됩니다.

* **[!UICONTROL @triggerId]** 속성에 [!DNL trigger] 이름이 포함되어 있습니다.
* JSON 형식의 **데이터 보강** 요소는 Adobe Analytics에서 생성한 데이터를 포함하며, 트리거에 첨부됩니다.
* **[!UICONTROL @offset]** 은 메시지에 대한 &quot;포인터&quot;입니다. 큐 내의 메시지 순서를 나타냅니다.
* **[!UICONTROL @partition]** 는 큐 내의 메시지 컨테이너입니다. 오프셋은 파티션을 기준으로 합니다. <br>큐에 약 15개의 파티션이 있습니다.

예제:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### 데이터 형식 보강 {#enrichment-format}

>[!NOTE]
>
>가능한 다양한 구현의 특정 예입니다.

콘텐츠는 각 트리거에 대해 Adobe Analytics에서 JSON 형식으로 정의됩니다.
예를 들어 트리거 LogoUpload_upload_Visits:

* **[!UICONTROL eVar01]** 는 Adobe Campaign 수신자와 조정하는 데 사용되는 문자열 형식의 쇼퍼 ID를 포함할 수 있습니다. <br>주요 키인 쇼퍼 ID를 찾기 위해 조정해야 합니다.

* **[!UICONTROL timeGMT]** UTC Epoch 형식(01/01/1970 UTC 이후 초)으로 Adobe Analytics 측에서 트리거되는 시간을 포함할 수 있습니다.

예제:

```
{
 "analyticsHitSummary": {
 "dimensions": {
 "eVar01": {
 "type": "string",
 "data": ["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],
 "name": " eVar01",
 "source": "session summary"
 },
 "timeGMT": {
 "type": "int",
 "data": [1469164186, 1469164195],
 "name": "timeGMT",
 "source": "session summary"
 }
 },
 "products": {}
 }
 }
```

### 이벤트 처리 순서{#order-events}

이벤트는 오프셋 순서대로 한 번에 하나씩 처리됩니다. [!DNL pipelined] 의 각 스레드는 다른 파티션을 처리합니다.

마지막으로 검색한 이벤트의 &#39;offset&#39;은 데이터베이스에 저장됩니다. 따라서 프로세스가 중지되면 마지막 메시지에서 다시 시작됩니다. 이 데이터는 내장 스키마 xtk:pipelineOffset에 저장됩니다.

이 포인터는 각 인스턴스 및 각 소비자에 따라 다릅니다. 따라서 많은 인스턴스가 서로 다른 소비자와 동일한 파이프라인에 액세스하면 각각 모든 메시지와 동일한 순서로 수신됩니다.

파이프라인 옵션의 **소비자** 매개 변수는 호출 인스턴스를 식별합니다.

현재 &#39;스테이징&#39; 또는 &#39;개발&#39;과 같은 별도의 환경에 대해 다른 큐가 있을 수 없습니다.

### 로깅 및 오류 처리 {#logging-error-handling}

logInfo() 와 같은 로그는 [!DNL pipelined] 로그로 전달됩니다. logError() 와 같은 오류가 [!DNL pipelined] 로그에 기록되며, 이로 인해 이벤트가 다시 시도 큐에 배치됩니다. 이 경우 파이프라인 로그를 확인해야 합니다.
오류 메시지가 [!DNL pipelined] 옵션에 설정된 지속 시간에 여러 번 다시 시도됩니다.

디버깅 및 모니터링을 위해 전체 트리거 데이터는 XML 형식의 &quot;data&quot; 필드에 있는 트리거 테이블에 작성됩니다. 또는 트리거 데이터가 포함된 logInfo()도 동일한 용도로 사용됩니다.

### 데이터 구문 분석 {#data-parsing}

이 샘플 Javascript 코드는 데이터 보강 부분의 eVar01을 구문 분석합니다.

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var shopper_id = ""
 if (xmlTrigger.enrichments.length() > 0)
 {
 if (xmlTrigger.enrichments.toString().match(/eVar01/) != undefined)
 {
 var enrichments = JSON.parse(xmlTrigger.enrichments.toString())
 shopper_id = enrichments.analyticsHitSummary.dimensions. eVar01.data[0]
 }
 }
 (…)
 }
```

오류를 방지하려면 구문 분석 시 주의하십시오.
이 코드는 모든 트리거에 사용되므로 대부분의 데이터가 필요하지 않습니다. 따라서 존재하지 않을 때 비워 둘 수 있습니다.

### 트리거 {#storing-triggers-js} 저장

>[!NOTE]
>
>가능한 다양한 구현의 특정 예입니다.

이 샘플 JS 코드는 트리거를 데이터베이스에 저장합니다.

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var event = 
 <pipelineEvent
 xtkschema = "cus:pipelineEvent"
 _operation = "insert"
 created = {timeNow}
 lastModified = {timeNow}
 triggerType = {triggerType}
 timeGMT = {timeGMT}
 shopper_id = {shopper_id}
 data = {xmlTrigger.toXMLString()}
 />
 xtk.session.Write(event)
 return <undef/>;
 }
```

### 제한 {#constraints}

이 코드는 고주파에서 실행되며 다른 마케팅 활동에 대해 잠재적 부정적인 영향을 줄 수 있으므로 이 코드에 대한 성능이 최적이어야 합니다. 특히 마케팅 서버에서 시간당 100만 개 이상의 트리거 이벤트를 처리하거나 제대로 조정되지 않은 경우 발생합니다.

이 Javascript의 컨텍스트는 제한됩니다. API의 일부 함수를 사용할 수 있는 것은 아닙니다. 예를 들어 getOption() 또는 getCurrentdate() 가 작동하지 않습니다.

더 빠른 처리를 위해 이 스크립트의 여러 스레드가 동시에 실행됩니다. 코드가 스레드로부터 안전해야 합니다.

## 이벤트 {#store-events} 저장

>[!NOTE]
>
>가능한 다양한 구현의 특정 예입니다.

### 파이프라인 이벤트 스키마 {#pipeline-event-schema}

이벤트는 데이터베이스 테이블에 저장됩니다. 마케팅 캠페인에서 고객을 타겟팅하고 트리거를 사용하여 이메일을 보강하는 데 사용됩니다.
각 트리거는 개별 데이터 구조를 가질 수 있지만 모든 트리거는 단일 테이블에 있을 수 있습니다.
triggerType 필드는 데이터를 트리거하는 대상을 식별합니다.

다음은 이 테이블의 샘플 스키마 코드입니다.

| 속성 | 유형 | 레이블 | 설명 |
|:-:|:-:|:-:|:-:|
| pipelineEventId | Long | 기본 키 | 트리거의 내부 기본 키입니다. |
| 데이터 | 메모 | 데이터 트리거 | XML 형식의 트리거 데이터의 전체 콘텐츠입니다. 디버깅 및 감사 목적으로 사용됩니다. |
| triggerType | 문자열 50 | TriggerType | 트리거 이름입니다. 웹 사이트에서 고객의 행동을 식별합니다. |
| shopper_id | 문자열 32 | shopper_id | 구매자의 내부 식별자입니다. 조정 워크플로우에 의해 설정됩니다. 0이면 Campaign에서 고객을 알 수 없음을 의미합니다. |
| shopper_key | Long | shopper_key | Analytics에서 캡처한 구매자의 외부 식별자입니다. |
| 생성됨 | Datetime | 생성됨 | Campaign에서 이벤트가 생성된 시간입니다. |
| lastModified | Datetime | 마지막 수정 날짜 | Adobe에서 이벤트가 마지막으로 수정된 시간입니다. |
| timeGMT | Datetime | Timestamp | Analytics에서 이벤트가 생성된 시간입니다. |

### 이벤트 {#display-events} 표시

이벤트 스키마를 기반으로 하여 간단한 양식으로 이벤트를 표시할 수 있습니다.

>[!NOTE]
>
>파이프라인 이벤트 노드는 내장된 것이 아니며, Campaign에서 관련 양식을 만들어야 합니다. 이러한 작업은 전문가 사용자로만 제한됩니다. 자세한 정보는 다음 섹션을 참조하십시오.[탐색 계층](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy). 및 [양식 편집](../../configuration/using/editing-forms.md)

![](assets/triggers_7.png)

## 이벤트 {#processing-the-events} 처리

### 조정 작업 과정 {#reconciliation-workflow}

조정 은 Adobe Analytics의 고객을 Adobe Campaign 데이터베이스에 연결하는 프로세스입니다. 예를 들어 일치하기 위한 기준은 shopper_id일 수 있습니다.

성능상의 이유로 워크플로우에 의해 배치 모드에서 일치를 수행해야 합니다.
작업 로드를 최적화하려면 빈도를 15분으로 설정해야 합니다. 따라서 Adobe Campaign의 이벤트 수신과 마케팅 워크플로우의 처리 사이의 지연 시간은 최대 15분입니다.

### JavaScript에서 단위 조정을 위한 옵션 {#options-unit-reconciliation}

JavaScript에서 각 트리거에 대한 조정 쿼리를 실행할 수 있습니다. 성능에 영향을 주고 더 빠른 결과를 제공합니다. 재활동이 필요한 특정 사용 사례에 필요할 수 있습니다.

shopper_id에 인덱스가 설정되어 있지 않으면 구현하기 어려울 수 있습니다. 마케팅 서버가 아닌 별도의 데이터베이스 서버에 있는 기준의 경우 데이터베이스 링크를 사용하므로 성능이 저하됩니다.

### 워크플로우 삭제 {#purge-workflow}

트리거는 1시간 내에 처리됩니다. 볼륨은 시간당 약 100만 개의 트리거일 수 있습니다. 이렇게 하면 제거 워크플로우가 제자리에 놓여야 하는 이유를 설명합니다. 제거는 하루에 한 번 실행되며 3일 이상 경과한 모든 트리거를 삭제합니다.

### 캠페인 워크플로우 {#campaign-workflow}

트리거 캠페인 워크플로우는 종종 사용된 다른 반복 캠페인과 유사합니다.
예를 들어 마지막 날 동안 특정 이벤트를 찾는 트리거에 대한 쿼리로 시작할 수 있습니다. 해당 타겟은 이메일을 전송하는 데 사용됩니다. 데이터 보강 작업은 트리거에서 가져올 수 있습니다. 구성이 필요 없으므로 마케팅에서 안전하게 사용할 수 있습니다.
