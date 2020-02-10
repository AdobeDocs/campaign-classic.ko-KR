---
title: JavaScript의 SOAP 메서드
seo-title: JavaScript의 SOAP 메서드
description: JavaScript의 SOAP 메서드
seo-description: null
page-status-flag: never-activated
uuid: 8fd1aabc-e51a-433d-835f-6b5a717c7aeb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 815d3eb9-ac45-441f-9a5f-0cd505fcf88a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# JavaScript의 SOAP 메서드{#soap-methods-in-javascript}

Adobe Campaign 서버에서 실행되는 JavaScript입니다.

## 정적 메서드 {#static-methods}

정적 SOAP 메서드는 스키마를 나타내는 개체에서 메서드를 호출하여 액세스합니다. 스키마는 &#39;namespace&#39; 개체의 속성입니다. 이러한 네임스페이스는 전역 변수이므로 xtk 또는 nms 변수는 해당 네임스페이스를 나타냅니다

다음 예제에서는 xtk:workflow 스키마의 정적 PostEvent 메서드를 호출합니다.

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## 비정적 메서드 {#non-static-methods}

비정적 SOAP 메서드를 사용하려면 먼저 해당 스키마에서 &quot;get&quot; 또는 &quot;create&quot; 메서드를 사용하여 엔티티를 검색해야 합니다.

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

## 예 {#examples}

* 받는 사람 테이블에 대해 &quot;get&quot; 작업을 쿼리합니다.

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

* &quot;선택&quot; 작업으로 수신자 테이블에서 쿼리:

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

