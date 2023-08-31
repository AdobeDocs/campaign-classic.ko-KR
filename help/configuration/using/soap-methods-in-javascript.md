---
product: campaign
title: JavaScript의 SOAP 메서드
feature: Configuration, Instance Settings
description: JavaScript의 SOAP 메서드
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 13%

---

# JavaScript의 SOAP 메서드{#soap-methods-in-javascript}

Adobe Campaign 서버에서 실행되는 JavaScript입니다.

## 정적 메서드 {#static-methods}

정적 SOAP 메서드는 스키마를 나타내는 개체에 대해 메서드를 호출하여 액세스됩니다. 스키마는 &#39;namespace&#39; 개체의 속성입니다. 이러한 네임스페이스는 전역 변수이므로, 예를 들어 xtk 또는 nms 변수는 해당 네임스페이스를 나타냅니다

다음 예제에서는 xtk:workflow 스키마의 정적 PostEvent 메서드를 호출합니다.

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## 비정적 메서드 {#non-static-methods}

비정적 SOAP 메서드를 사용하려면 먼저 해당 스키마에서 &quot;get&quot; 또는 &quot;create&quot; 메서드를 사용하여 엔터티를 검색해야 합니다.

다음 예제에서는 &quot;xtk:queryDef&quot; 스키마의 ExecuteQuery 메서드를 호출합니다.

```
var query = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
    </select>
  </queryDef>
)

var res = query.ExecuteQuery()

for each (var w in res.workflow) 
  logInfo(w.@internalName)
```

## 예제 {#examples}

* &quot;get&quot; 작업을 사용하여 수신자 테이블을 쿼리합니다.

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="get">    
      <select>      
        <node expr="@firstName"/>      
        <node expr="@lastName"/>      
        <node expr="@email"/>    
      </select>    
      <where>      
        <condition expr="@email = 'peter.martinez@adobe.com'"/>    
      </where>  
    </queryDef>)
  
  var recipient = query.ExecuteQuery()
  
  logInfo(recipient.@firstName)
  logInfo(recipient.@lastName)
  ```

* &quot;select&quot; 작업을 사용하여 수신자 테이블을 쿼리합니다.

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="select">    
      <select>      
        <node expr="@email"/>      
        <node expr="@lastName"/>      
        <node expr="@firstName"/>    
      </select>    
      <where>      
        <condition expr="@age > 25"/>    
      </where>    
    </queryDef>)
  
  var res = query.ExecuteQuery()
  
  for each (var recipient in res.recipient) 
  {  
    logInfo(recipient.@email)  
    logInfo(recipient.@firstName)  
    logInfo(recipient.@lastName)
  }
  ```

* 수신자 테이블에 데이터 쓰기:

  ```
  xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
  ```
