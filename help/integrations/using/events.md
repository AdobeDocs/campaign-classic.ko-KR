---
title: 통합 구성
seo-title: 통합 구성
description: 통합 구성
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 0%

---


# 트리거 이벤트 {#events}

## JavaScript에서 이벤트 처리 {#events-javascript}

### JavaScript 파일 {#file-js}

파이프라인은 JavaScript 함수를 사용하여 각 메시지를 처리합니다. 이 함수는 사용자가 정의합니다.

&quot;JSConnector&quot; 속성 아래의 **[!UICONTROL NmsPipeline_Config]** 옵션에서 구성됩니다. 이 javascript는 이벤트를 받을 때마다 호출됩니다. 그 [!DNL pipelined] 과정에 의해 운영된다.

샘플 JS 파일은 cus:triggers.js입니다.

### JavaScript 함수 {#function-js}

Javascript [!DNL pipelined] 는 특정 함수로 시작해야 합니다.

이 함수는 모든 이벤트에 대해 한 번 호출됩니다.

```
function processPipelineMessage(xmlTrigger) {}
```

원래 상태로 돌아와야 합니다

```
<undefined/>
```

JS를 편집한 [!DNL pipelined] 후 다시 시작합니다.

### 데이터 형식 트리거 {#trigger-format}

이 [!DNL trigger] 데이터는 JS 함수로 전달됩니다. XML 포맷으로 되어 있습니다.

* 속성에는 **[!UICONTROL @triggerId]** 해당 속성의 이름이 포함되어 [!DNL trigger]있습니다.
* JSON **형식의** 농축은 Analytics에서 생성된 데이터를 포함하며 트리거에 첨부됩니다.
* **[!UICONTROL @offset]** 은 메시지에 대한 &quot;포인터&quot;입니다. 큐 내의 메시지 순서를 나타냅니다.
* **[!UICONTROL @partitio]**n은 큐 내의 메시지 컨테이너입니다. 오프셋이 파티션에 비례합니다. <br>큐에는 약 15개의 파티션이 있습니다.

예:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### 데이터 형식 강화 {#enrichment-format}

>[!NOTE]
>
>가능한 다양한 구현의 특정 예입니다.

컨텐츠는 각 트리거에 대해 Analytics에 정의됩니다. JSON 포맷으로 되어 있습니다.
예를 들어 LogoUpload_uploading_Visits 트리거

* **[!UICONTROL eVar01]** 에는 캠페인 수신자와 대사하는 데 사용되는 구매자 ID가 포함될 수 있습니다. 문자열 형식입니다. <br>주요 열쇠인 구매자 ID를 찾기 위해 조정해야 한다.

* **[!UICONTROL timeGMT]** 는 Analytics 쪽에서 트리거 시간을 포함할 수 있습니다. UTC Epoch 형식(01/01/1970 UTC 이후 초)입니다.

예:

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

### 이벤트 처리 순서 {#order-events}

이벤트는 오프셋 순서로 한 번에 하나씩 처리됩니다. Each thread of the [!DNL pipelined] processes a different partition.

마지막으로 검색된 이벤트의 &#39;오프셋&#39;이 데이터베이스에 저장됩니다. 따라서 프로세스가 중지되면 마지막 메시지에서 다시 시작됩니다. 이 데이터는 내장 스키마 xtk:pipelineOffset에 저장됩니다.

이 포인터는 각 인스턴스와 각 소비자에 따라 다릅니다. 따라서 많은 인스턴스가 서로 다른 소비자와 동일한 파이프라인에 액세스하면 각각 모든 메시지를 동일한 순서로 받게 됩니다.

파이프라인 옵션의 &quot;consumer&quot; 매개 변수는 호출 인스턴스를 식별합니다.

현재, &#39;staging&#39; 또는 &#39;dev&#39;와 같은 별도의 환경에 대해 다른 대기열이 있을 수 있는 방법은 없습니다.

### 로깅 및 오류 처리 {#logging-error-handling}

logInfo()와 같은 로그는 [!DNL pipelined] 로그에 전달됩니다. logError()와 같은 오류는 [!DNL pipelined] 로그에 기록되므로 이벤트가 다시 시도 대기열에 추가됩니다. 파이프라인 로그를 확인합니다.
오류 메시지가 옵션에 설정된 지속 시간에 여러 번 [!DNL pipelined] 다시 시도됩니다.

디버깅 및 모니터링을 위해 전체 트리거 데이터는 트리거 테이블에 기록됩니다. XML 형식의 &quot;데이터&quot; 필드에 있습니다. 또는 트리거 데이터를 포함하는 logInfo()는 동일한 용도로 사용됩니다.

### 데이터 구문 분석 {#data-parsing}

이 샘플 JS 코드는 추가에서 eVar01을 구문 분석합니다.

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
이 코드는 모든 트리거에 사용되므로 대부분의 데이터는 필요하지 않습니다. 따라서 존재하지 않을 때는 비워 둘 수 있습니다.

### 트리거 저장 {#storing-triggers-js}

>[!NOTE]
>
>가능한 다양한 구현의 특정 예입니다.

이 샘플 JS 코드는 트리거를 데이터베이스에 저장합니다.

```
function processPipelineMessage(xmlTrigger)
 {```
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

이 코드는 높은 주파수에서 실행되므로 성능이 최적화되어야 합니다. 다른 마케팅 활동에는 부정적인 효과가 있을 수 있습니다. 특히 Marketing Server에서 시간당 100만 개 이상의 트리거 이벤트를 처리하는 경우. 또는 제대로 조정되지 않은 경우

이 Javascript의 컨텍스트는 제한됩니다. API의 일부 기능을 사용할 수 있는 것은 아닙니다. 예를 들어 getOption() 또는 getCurrentdate()는 작동하지 않습니다.

빠른 처리를 위해 이 스크립트의 여러 스레드가 동시에 실행됩니다. 코드는 스레드 안전이어야 합니다.

## 이벤트 저장 {#store-events}

>[!NOTE]
>
>가능한 다양한 구현의 특정 예입니다.

### 파이프라인 이벤트 스키마 {#pipeline-event-schema}

이벤트는 데이터베이스 테이블에 저장됩니다. 마케팅 캠페인에서 고객을 타깃팅하고 트리거를 사용하여 이메일을 보완합니다.
각 트리거는 별도의 데이터 구조를 가질 수 있지만 모든 트리거는 단일 테이블에 유지될 수 있습니다.
triggerType 필드는 데이터가 발생하는 트리거로부터 식별합니다.

이 테이블에 대한 샘플 스키마 코드는 다음과 같습니다.

| 속성 | 유형 | 레이블 | 설명 |
|:-:|:-:|:-:|:-:|
| pipelineEventId | Long | 기본 키 | 트리거의 내부 기본 키입니다. |
| 데이터 | 메모 | 트리거 데이터 | 트리거 데이터의 전체 내용을 XML 형식으로 표시합니다. 디버깅 및 감사 목적 |
| triggerType | 문자열 50 | TriggerType | 트리거 이름입니다. 웹 사이트에서 고객의 행동을 식별합니다. |
| shopper_id | 문자열 32 | shopper_id | 구매자의 내부 식별자입니다. 조정 워크플로우에 의해 설정됩니다. 0이면, Campaign에서 고객을 알 수 없음을 의미합니다. |
| shopper_key | Long | shopper_key | Analytics에 의해 캡처된 구매자의 외부 식별자입니다. |
| created | 날짜/시간 | 작성일 | 캠페인에서 이벤트가 생성된 시간입니다. |
| lastModified | 날짜/시간 | 마지막 수정일 | Adobe에서 마지막으로 이벤트가 수정된 시간입니다. |
| timeGMT | 날짜/시간 | 타임스탬프 | Analytics에서 이벤트가 생성된 시간입니다. |

### 이벤트 표시 {#display-events}

이벤트 스키마를 기반으로 하는 간단한 양식으로 이벤트를 표시할 수 있습니다.

>[!NOTE]
>
>파이프라인 이벤트 노드는 내장되어 있지 않으므로 Campaign에서 관련 양식과 함께 추가해야 합니다. 이러한 작업은 전문가 사용자로만 제한됩니다. 자세한 내용은 다음 섹션을 참조하십시오. [탐색 계층](../../configuration/using/about-navigation-hierarchy.md) 및 [양식](../../configuration/using/editing-forms.md)편집

![](assets/triggers_7.png)

## 이벤트 처리 {#processing-the-events}

### 조정 워크플로우 {#reconciliation-workflow}

화해란 Analytics의 고객을 Campaign 데이터베이스에 연결하는 프로세스입니다. 예를 들어 일치에 대한 기준은 shopper_id일 수 있습니다.

성능상의 이유로 워크플로우에서 일치를 일괄 처리 모드로 수행해야 합니다.
작업 로드를 최적화하려면 빈도를 15분으로 설정해야 합니다. 따라서 Adobe Campaign의 이벤트 수신과 마케팅 워크플로우에 의한 처리 사이의 지연 시간은 최대 15분입니다.

### JavaScript의 단위 조정 옵션 {#options-unit-reconciliation}

이론적으로는 JavaScript의 각 트리거에 대해 조정 쿼리를 실행할 수 있습니다. 성능도 향상되어 보다 빠른 결과를 얻을 수 있습니다. 재활동이 필요할 때 특정 사용 사례에 필요할 수 있습니다.

shopper_id에 인덱스가 설정되어 있지 않으면 하기가 어려울 수 있습니다. 기준이 마케팅 서버가 아닌 별도의 데이터베이스 서버에 있는 경우 데이터베이스 링크를 사용하므로 성능이 저하됩니다.

### 제거 워크플로우 {#purge-workflow}

트리거는 1시간 이내에 처리되므로 오랫동안 보관할 이유가 없습니다. 볼륨은 시간당 약 100만 개의 트리거일 수 있습니다. 삭제 워크플로우가 필요한 이유를 설명합니다. 제거는 3일 이상 오래된 모든 트리거를 삭제하고 하루에 한 번 실행됩니다.

### 캠페인 워크플로우 {#campaign-workflow}

트리거 캠페인 워크플로우는 종종 사용된 다른 되풀이되는 캠페인과 비슷합니다.
예를 들어 마지막 날 동안 특정 이벤트를 찾는 트리거에 대한 쿼리부터 시작할 수 있습니다. 해당 타겟은 이메일을 보내는 데 사용됩니다. 농축이나 데이터는 방아쇠를 당길 수 있다. 구성이 필요 없으므로 Marketing에서 안전하게 사용할 수 있습니다.
