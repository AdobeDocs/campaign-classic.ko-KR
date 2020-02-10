---
title: 데이터 지향 API
seo-title: 데이터 지향 API
description: 데이터 지향 API
seo-description: null
page-status-flag: never-activated
uuid: f81356b3-8eef-4b65-9510-47c9d4b4e871
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: fba46d42-0253-425b-bbc2-6702d4140e05
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f9b3508fee3b441752648258b1bc9d5d2b919791

---


# 데이터 지향 API{#data-oriented-apis}

데이터 지향 API를 사용하면 전체 데이터 모델을 해결할 수 있습니다.

## 데이터 모델 개요 {#overview-of-the-datamodel}

Adobe Campaign은 개체당 전용 읽기 API를 제공하지 않습니다(getRecipient 또는 getDelivery 함수 등 없음). QUERY &amp; WRITER 데이터 읽기 및 수정 방법을 사용하여 모델의 데이터에 액세스합니다.

Adobe Campaign을 사용하여 컬렉션을 관리할 수 있습니다.쿼리를 사용하면 기본 전체에서 수집한 정보 집합을 복구할 수 있습니다. SQL 모드의 액세스와 달리 Adobe Campaign API는 데이터 열 대신 XML 트리를 반환합니다. 따라서 Adobe Campaign은 수집된 모든 데이터가 포함된 합성 문서를 만듭니다.

이 운영 모드는 XML 문서의 특성과 요소 및 데이터베이스의 테이블 열 사이에 일대일 매핑을 제공하지 않습니다.

XML 문서는 데이터베이스의 MEMO 유형 필드에 저장됩니다.

## 모델에 대한 설명 {#description-of-the-model}

스크립트에서 데이터베이스의 필드를 처리할 수 있으려면 Adobe Campaign 데이터 모델에 익숙해야 합니다.

데이터 모델에 대한 프레젠테이션은 Adobe Campaign 데이터 [모델 설명을](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html)참조하십시오.

구조를 생성하려면 다음 문서를 참조하십시오.데이터 [모델 또는 데이터 사전을 생성하는 방법](https://helpx.adobe.com/campaign/kb/generate-data-model.html).

## 쿼리 및 작성기 {#query-and-writer}

다음 소개 스키마 세부 사항은 데이터베이스와 고객(웹 페이지 또는 Adobe Campaign 클라이언트 콘솔) 간의 읽기 및 쓰기(작성자)를 위한 낮은 수준의 교환입니다.

![](assets/s_ncs_integration_webservices_schema_writer.png)

### ExecuteQuery {#executequery}

열 및 조건의 경우 쿼리를 사용할 수 있습니다.

이를 통해 기본 SQL을 격리할 수 있습니다. 쿼리 언어는 기본 엔진에 의존하지 않습니다.일부 함수는 다시 매핑되며, 이 함수는 여러 SELECT SQL 주문을 생성할 수 있습니다.

자세한 내용은 스키마 &#39;xtk:queryDef&#39; [의 &#39;ExecuteQuery&#39; 메서드에 대한 예를 참조하십시오](../../configuration/using/web-service-calls.md#example-on-the--executequery--method-of-schema--xtk-querydef-).

ExecuteQuery **메서드는** ExecuteQuery(xtk:queryDef) [에](#executequery--xtk-querydef-)표시됩니다.

### 쓰기 {#write}

쓰기 명령을 사용하면 하나 이상의 기본 표에 항목이 있는 간단한 문서 또는 복잡한 문서를 작성할 수 있습니다.

거래 API를 사용하면 updateOrInsert **명령을 통해 조정을 관리할 수** 있습니다.한 번의 명령으로 데이터를 만들거나 업데이트할 수 있습니다. 수정 병합(**병합**)을 구성할 수도 있습니다.이 운영 모드에서는 부분 업데이트를 승인할 수 있습니다.

XML 구조는 데이터에 대한 논리적 보기를 제공하며 SQL 테이블의 물리적 구조를 사이드 단계로 이동할 수 있도록 해줍니다.

Write 메서드는 Write [/ WriteCollection(xtk:session)에](#write---writecollection--xtk-session-)제공됩니다.

## ExecuteQuery(xtk:queryDef) {#executequery--xtk-querydef-}

이 방법을 사용하면 스키마와 연결된 데이터에서 쿼리를 수행할 수 있습니다. 이 매개 변수로 제출할 쿼리를 설명하는 XML 문서와 인증 문자열이 필요합니다. 반환 매개 변수는 쿼리 결과가 쿼리가 참조하는 스키마 형식으로 포함된 XML 문서입니다.

&quot;xtk:queryDef&quot; 스키마의 &quot;ExecuteQuery&quot; 메서드 정의:

```
<method name="ExecuteQuery" const="true">
  <parameters>
    <param desc="Output XML document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

>[!NOTE]
>
>&quot;const&quot; 방식입니다. 입력 매개 변수는 XML 문서에 &quot;xtk:queryDef&quot; 스키마 형식으로 포함됩니다.

### 입력 쿼리의 XML 문서 형식 {#format-of-the-xml-document-of-the-input-query}

쿼리의 XML 문서 구조는 &quot;xtk:queryDef&quot; 스키마에 설명되어 있습니다. 이 문서에서는 SQL 쿼리의 절에 대해 설명합니다.&quot;select&quot;, &quot;where&quot;, &quot;order by&quot;, &quot;group by&quot;, &quot;having&quot;

```
<queryDef schema="schema_key" operation="operation_type">
  <select>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </select>
  <where> 
    <condition expr="expression1"/> 
    <condition expr="expression2"/>
    ... 
  </where>
  <orderBy>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </orderBy>
  <groupBy>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </groupBy>
  <having>
    <condition expr="expression1"/> 
    <condition expr="expression2"/>
    ...
  </having>
</queryDef>
```

하위 쿼리( `<subquery>` )를 `<condition> ` 요소에 정의할 수 있습니다. 요소의 구문은 `<subquery> ` a의 구문을 기반으로 합니다 `<querydef>`.

Example of a `<subquery>  : </subquery>`

```
<condition setOperator="NOT IN" expr="@id" enabledIf="$(/ignored/@ownerType)=1">
  <subQuery schema="xtk:operatorGroup">
     <select>
       <node expr="[@operator-id]" />
     </select>
     <where>
       <condition expr="[@group-id]=$long(../@owner-id)"/>
     </where>
   </subQuery>
</condition>  
  
```

쿼리는 **스키마** 속성에서 시작 스키마를 참조해야 합니다.

원하는 작업 유형이 **작업** 속성에 입력되고 다음 값 중 하나를 포함합니다.

* **get**:테이블에서 레코드를 검색하고 데이터가 없는 경우 오류를 반환합니다.
* **getIfExists**:테이블에서 레코드를 검색하고 데이터가 없는 경우 빈 문서를 반환합니다.
* **선택**:여러 레코드를 반환하는 커서를 만들고 데이터가 없는 경우 빈 문서를 반환합니다.
* **카운트**:데이터 개수를 반환합니다.

XPath **구문은** 입력 스키마를 기반으로 데이터를 찾는 데 사용됩니다. XPath에 대한 자세한 내용은 데이터 스키마를 [참조하십시오](../../configuration/using/data-schemas.md).

#### &#39;get&#39; 작업의 예 {#example-with-the--get--operation}

이메일에 필터가 있는 받는 사람의 성 및 이름(&quot;nms:recipient&quot; 스키마)을 검색합니다.

```
<queryDef schema="nms:recipient" operation="get">
  <!-- fields to retrieve -->
  <select>
    <node expr="@firstName"/>
    <node expr="@lastName"/>
  </select> 

  <!-- condition on email -->
  <where>  
    <condition expr="@email= 'john.doe@aol.com'"/>
  </where>
</queryDef>
```

#### &#39;select&#39; 작업 예 {#example-with-the--select--operation}

폴더에서 필터링된 수신자 목록을 반환하고, 생년월일 기준으로 내림차순으로 정렬된 전자 메일 도메인을 반환합니다.

```
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <!-- builds a string with the concatenation of the last name and first name separated by a dash -->      
    <node expr="@lastName+'-'+@firstName"/>
    <!-- get year of birth date -->
    <node expr="Year(@birthDate)"/>
  </select> 

  <where>  
     <condition expr="[@folder-id] = 1234 and @domain like 'Adobe%'"/>
  </where>

  <!-- order by birth date -->
  <orderBy>
    <node expr="@birthDate" sortDesc="true"/> <!-- by default sortDesc="false" -->
  </orderBy>
</queryDef>
```

식은 간단한 필드나 산술 연산이나 문자열 연결과 같은 복잡한 표현식이 될 수 있습니다.

반환할 레코드 수를 제한하려면 **lineCount** 속성을 `<querydef>` 요소에 추가합니다.

쿼리에서 반환한 레코드 수를 100으로 제한하려면 다음을 수행합니다.

```
<queryDef schema="nms:recipient" operation="select" lineCount="100">
...
```

다음 100개의 레코드를 검색하려면 동일한 쿼리를 다시 실행하고 **startLine 속성을** 추가합니다.

```
<queryDef schema="nms:recipient" operation="select" lineCount="100" startLine="100">
...
```

#### &#39;count&#39; 작업의 예 {#example-with-the--count--operation}

쿼리의 레코드 수를 카운트하려면

```
<queryDef schema="nms:recipient" operation="count"">
  <!-- condition on the folder and domain of the e-mail -->
  <where>  
    <condition expr="[@folder-id] = 1234" and @domain like 'Adobe%'"/>
  </where>
</queryDef>
```

>[!NOTE]
>
>다시 이전 예제의 조건을 사용합니다. and `<select>` clauses are not used. </select>&#39;

#### 데이터 그룹화 {#data-grouping}

참조된 전자 메일 주소를 두 번 이상 검색하려면 다음을 수행하십시오.

```
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <node expr="count(@email)"/>
  </select>

  <!-- e-mail grouping clause -->
  <groupby>
    <node expr="@email"/>
  </groupby>

  <!-- grouping condition -->
  <having>
    <condition expr="count(@email) > 1"/>
  </having>

</queryDef>
```

groupBy 속성을 그룹화할 **필드에** 직접 추가하여 쿼리를 단순화할 수 있습니다.

```
<select>
  <node expr="@email" groupBy="true"/>
</select>
```

>[!NOTE]
>
>더 이상 `<groupby>` 요소를 채울 필요가 없습니다.

#### 조건 대괄호 {#bracketing-in-conditions}

다음은 동일한 조건에 대한 대괄호의 두 예입니다.

* 단일 표현식의 간단한 버전:

   ```
   <where>
     <condition expr="(@age > 15 or @age <= 45) and  (@city = 'Newton' or @city = 'Culver City') "/>
   </where>
   ```

* 구조화된 `<condition>` 요소 버전:

   ```
   <where>
     <condition bool-operator="AND">
       <condition expr="@age > 15" bool-operator="OR"/>
       <condition expr="@age <= 45"/>
     </condition>
     <condition>
       <condition expr="@city = 'Newton'" bool-operator="OR"/>
       <condition expr="@city = 'Culver City'"/>
     </condition>
   </where>
   ```

동일한 필드에 여러 조건이 적용될 경우 &#39;OR&#39; 연산자를 &#39;IN&#39; 연산자로 바꿀 수 있습니다.

```
<where>
  <condition>
    <condition expr="@age IN (15, 45)"/>
    <condition expr="@city IN ('Newton', 'Culver City')"/>
  </condition>
</where>
```

이 구문은 조건에 두 개 이상의 데이터를 사용할 때 쿼리를 단순화합니다.

#### 링크의 예 {#examples-on-links}

* 링크 1-1 또는 N1:테이블에 외래 키(테이블에서 링크 시작)가 있으면 연결된 테이블의 필드를 직접 필터링하거나 검색할 수 있습니다.

   폴더 레이블에 대한 필터의 예:

   ```
   <where>
     <condition expr="[folder/@label] like 'Segment%'"/>
   </where>
   ```

   &quot;nms:recipient&quot; 스키마에서 폴더 필드를 검색하려면

   ```
   <select>
     <!-- label of recipient folder -->
     <node expr="[folder/@label]"/>
     <!-- displays the string count of the folder -->
     <node expr="partition"/>
   </select>
   ```

* 컬렉션 링크(1N):컬렉션 테이블의 필드에 대한 필터링은 EXISTS 또는 NOT **EXISTS** **연산자를 통해 수행해야 합니다** .

   &#39;뉴스레터&#39; 정보 서비스에 가입한 수신자를 필터링하려면:

   ```
   <where>
     <condition expr="subscription" setOperator="EXISTS">
       <condition expr="@name = 'Newsletter'"/>
     </condition>
   </where>
   ```

   쿼리에서 기본 제품을 반환하므로 `<select>` 절에서 컬렉션 링크의 필드를 직접 검색하는 것은 권장되지 않습니다. 연결된 테이블에 레코드(예 `<node expr="">`)가 하나만 있을 때만 사용됩니다.

   &quot;구독&quot; 컬렉션 링크의 예:

   ```
   <select>
     <node expr="subscription/@label"/>
   </select>
   ```

   절의 컬렉션 링크 요소를 포함하는 하위 목록을 검색할 수 `<select>` 있습니다. 참조된 필드의 XPath는 컬렉션 요소의 컨텍스트에 해당합니다.

   필터링( `<orderby>` ) 및 제한( `<where>` ) 요소를 컬렉션 요소에 추가할 수 있습니다.

   이 예에서는 각 수신자에 대해 질의가 받는 사람이 가입한 이메일 및 정보 서비스 목록을 반환합니다.

   ```
   <queryDef schema="nms:recipient" operation="select">
     <select>
       <node expr="@email"/>
   
       <!-- collection table (unbound type) -->
       <node expr="subscription">  
         <node expr="[service/@label]"/>    
         <!-- sub-condition on the collection table -->
         <where>  
           <condition expr="@expirationDate >= GetDate()"/>
         </where>
         <orderBy>
           <node expr="@expirationDate"/> 
         </orderBy>
       </node>
     </select> 
   </queryDef>
   ```

#### &#39;where&#39; 및 &#39;select&#39; 절의 매개 변수 바인딩 {#binding-the-parameters-of-the--where--and--select--clause}

매개 변수 바인딩을 사용하면 엔진에서 쿼리에 사용되는 매개 변수의 값을 설정할 수 있습니다. 이 기능은 엔진에서 값 이스케이프 작업을 담당하고 있을 뿐만 아니라 검색할 매개 변수에 대한 캐시를 추가로 제공하므로 매우 유용합니다.

쿼리가 생성되면 &quot;bound&quot; 값이 문자(? in ODBC, `#[index]#` in postgres...) in the SQL query.

```
<select>
  <!--the value will be bound by the engine -->
  <node expr="@startDate = #2002/02/01#"/>                   
  <!-- the value will not be bound by the engine but visible directly in the query -->
  <node expr="@startDate = #2002/02/01#" noSqlBind="true"/> 
</select>
```

매개 변수를 바인딩하지 않으려면 &quot;noSqlBind&quot; 특성을 값 &#39;true&#39;로 채워야 합니다.

>[!CAUTION]
>
>쿼리에 &quot;order-by&quot; 또는 &quot;group-by&quot; 지침이 포함된 경우 데이터베이스 엔진은 값을 &quot;바인딩&quot;할 수 없습니다. 쿼리의 &quot;select&quot; 및/또는 &quot;where&quot; 지침에 @noSqlBind=&quot;true&quot; 속성을 배치해야 합니다.

#### 쿼리 작성 팁: {#query-building-tip-}

쿼리 구문에 도움이 되도록 Adobe Campaign 클라이언트 콘솔( **[!UICONTROL Tools/ Generic query editor...]** 메뉴)에서 일반 쿼리 편집기를 사용하여 쿼리를 작성할 수 있습니다. 이렇게 하려면:

1. 검색할 데이터를 선택합니다.

   ![](assets/s_ncs_integration_webservices_queyr1.png)

1. 필터 조건을 정의합니다.

   ![](assets/s_ncs_integration_webservices_queyr2.png)

1. 쿼리를 실행하고 Ctrl+F4를 눌러 쿼리 소스 코드를 봅니다.

   ![](assets/s_ncs_integration_webservices_queyr3.png)

### 출력 문서 형식 {#output-document-format}

반환 매개 변수는 쿼리와 연결된 스키마 형식의 XML 문서입니다.

&quot;get&quot; 작업의 &quot;nms:recipient&quot; 스키마에서 반환되는 예:

```
<recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
```

&quot;선택&quot; 작업에서 반환된 문서는 다음 요소의 열거형입니다.

```
<!-- the name of the first element does not matter -->
<recipient-collection>   
  <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
  <recipient email="peter.martinez@adobe.com" lastName"Martinez" firstName="Peter"/>
  <recipient...
</recipient-collection>  
```

&quot;count&quot; 유형 작업에 대해 반환되는 문서의 예:

```
<recipient count="3"/>
```

#### 별칭 {#alias}

별칭을 사용하면 출력 문서의 데이터 위치를 수정할 수 있습니다. alias **** 속성은 해당 필드에 XPath를 지정해야 합니다.

```
<queryDef schema="nms:recipient" operation="get">
  <select>
    <node expr="@firstName" alias="@firstName"/>
    <node expr="@lastName"/>
    <node expr="[folder/@label]" alias="@My_folder"/>
  </select> 
</queryDef>
```

반환:

```
<recipient My_folder="Recipients" First name ="John" lastName="Doe"/>
```

대신:

```
<recipient firstName="John" lastName="Doe">
  <folder label="Recipients"/>
</recipient>
```

### SOAP 메시지 예 {#example-of-soap-messages}

* 쿼리:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <ExecuteQuery xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <__sessiontoken xsi:type='xsd:string'/>
         <entity xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <queryDef operation="get" schema="nms:recipient" xtkschema="xtk:queryDef">
             <select>
               <node expr="@email"/>
               <node expr="@lastName"/>
               <node expr="@firstName"/>
             </select>
             <where>
               <condition expr="@id = 3599"/>
             </where>
           </queryDef>
         </entity>
       </ExecuteQuery>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* 응답:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <ExecuteQueryResponse xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <pdomOutput xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
         </pdomOutput>
       </ExecuteQueryResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

## Write / WriteCollection (xtk:session) {#write---writecollection--xtk-session-}

이러한 서비스는 엔티티(&quot;Write&quot; 메서드) 또는 엔티티 컬렉션(&quot;WriteCollection&quot; 메서드)을 삽입하거나 업데이트하거나 삭제하는 데 사용됩니다.

업데이트할 엔티티는 데이터 스키마와 연결됩니다. 입력 매개 변수는 인증 문자열(로그인해야 함)과 업데이트할 데이터가 들어 있는 XML 문서입니다.

이 문서는 쓰기 절차 구성에 대한 지침에 의해 보완됩니다.

오류를 제외하고 호출은 데이터를 반환하지 않습니다.

&quot;xtk:session&quot; 스키마에서 &quot;Write&quot; 및 &quot;WriteCollection&quot; 메서드의 정의:

```
<method name="Write" static="true">
  <parameters>
    <param name="doc" type="DOMDocument" desc="Difference document"/>
  </parameters>
</method>
<method name="WriteCollection" static="true">
  <parameters>
    <param name="doc" type="DOMDocument" desc="Difference collection document"/>
  </parameters>
</method>
```

>[!NOTE]
>
>이것은 &quot;정적&quot; 메서드입니다. 입력 매개 변수는 업데이트할 스키마 형식으로 XML 문서에 포함됩니다.

### 개요 {#overview}

데이터 조정은 연결된 스키마에 입력된 키의 정의에 따라 작동합니다. 쓰기 프로시저는 입력 문서에 입력된 데이터를 기준으로 첫 번째 자격 조건을 갖춘 키를 찾습니다. 엔티티는 데이터베이스에 존재함에 따라 삽입되거나 업데이트됩니다.

업데이트할 엔티티의 스키마의 키는 xtkschema **속성을** 기반으로 완료됩니다.

따라서 키를 구성하는 XPath 목록이 포함된 **_key** 속성을 쉼표로 구분하여 조정 키를 강제로 사용할 수 있습니다.

다음 값으로 **_operation** 속성을 채워 작업 유형을 강제 적용할 수 있습니다.

* **삽입**:레코드를 강제로 삽입합니다(조정 키는 사용되지 않음).
* **insertOrUpdate**:조정 키(기본 모드)에 따라 레코드를 업데이트하거나 삽입합니다.
* **업데이트**:레코드를 업데이트합니다.데이터가 없는 경우 아무 작업도 수행되지 않습니다.
* **삭제**:레코드를 삭제하고
* **없음**:업데이트 또는 삽입 없이 링크 조정에만 사용됩니다.

### &#39;Write&#39; 메서드의 예 {#example-with-the--write--method}

이메일 주소, 생년월일 및 읍과 함께 받는 사람(암시적 &quot;insertOrUpdate&quot; 작업)을 업데이트하거나 삽입하는 경우:

```
<recipient xtkschema="nms:recipient" email="john.doe@adobe.com" birthDate="1956/05/04" folder-id=1203 _key="@email, [@folder-id]">
  <location city="Newton"/>
</recipient>
```

수신자 삭제:

```
<recipient xtkschema="nms:recipient" _operation="delete" email="rene.dupont@adobe.com" folder-id=1203 _key="@email, [@folder-id]"/>
```

>[!NOTE]
>
>삭제 작업의 경우 입력 문서에는 조정 키를 구성하는 필드만 포함되어야 합니다.

### &#39;WriteCollection&#39; 메서드의 예 {#example-with-the--writecollection--method}

여러 수신자를 위한 업데이트 또는 삽입:

```
<recipient-collection xtkschema="nms:recipient">    
  <recipient email="john.doe@adobe.com" firstName="John" lastName="Doe" _key="@email"/>
  <recipient email="peter.martinez@adobe.com" firstName="Peter" lastName="Martinez" _key="@email"/>
  <recipient ...
</recipient-collection>
```

### 링크의 예 {#example-on-links}

#### 예 1 {#example-1}

내부 이름(@name)을 기준으로 받는 사람과 폴더를 연결하는 중입니다.

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <folder name="Folder2" _operation="none"/>
</recipient>
```

연결된 요소에 &quot;_key&quot; 및 &quot;_operation&quot; 속성을 입력할 수 있습니다. 이 요소의 동작은 입력 스키마의 주 요소와 동일합니다.

기본 엔티티의 키 정의(&quot;nms:recipient&quot;)는 연결된 테이블의 필드(요소 `<folder>` 스키마 &quot;xtk:folder&quot;)와 전자 메일로 구성됩니다.

>[!NOTE]
>
>폴더 요소에 입력된 작업 &quot;없음&quot;은 업데이트나 삽입 없이 폴더의 조정을 정의합니다.

#### 예 2 {#example-2}

받는 사람으로부터 회사(&quot;cus:company&quot; 스키마의 연결된 테이블) 업데이트:

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <company name="adobe" code="ERT12T" _key="@name" _operation="update"/>
</recipient>
```

#### 예제 3 {#example-3}

그룹 관계 테이블을 사용하여 그룹에 받는 사람 추가(&quot;nms:rcpGrpRel&quot;):

```
<recipient _key="@email" email="martin.ledger@adobe.net" xtkschema="nms:recipient">
  <rcpGrpRel _key="[rcpGroup/@name]">
    <rcpGroup name="GRP1"/>
  </rcpGrpRel>
</recipient>
```

>[!NOTE]
>
>그룹 이름을 기반으로 하는 암시적 키가 &quot;nms:group&quot; 스키마에 정의되어 있으므로 키의 정의가 `<rcpgroup>` 요소에 입력되지 않습니다.

### XML 컬렉션 요소 {#xml-collection-elements}

기본적으로 XML 컬렉션 요소를 업데이트하려면 모든 컬렉션 요소를 채워야 합니다. 데이터베이스의 데이터는 입력 문서의 데이터로 바뀝니다. 문서에 업데이트할 요소만 포함된 경우 데이터베이스의 XML 데이터로 병합을 적용하려면 업데이트할 모든 컬렉션 요소에 &quot;_operation&quot; 속성을 채워야 합니다.

### SOAP 메시지 예 {#example-of-soap-messages-1}

* 쿼리:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <Write xmlns='urn:xtk:persist' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <__sessiontoken xsi:type='xsd:string'/>
         <domDoc xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <recipient xtkschema="nms:recipient" email="rene.dupont@adobe.com" firstName="René" lastName="Dupont" _key="@email">
         </domDoc>
       </Write>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* 응답:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <WriteResponse xmlns='urn:' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </WriteResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

   오류가 있는 반환:

   ```
   <?xml version='1.0'?>
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <SOAP-ENV:Fault>
         <faultcode>SOAP-ENV:Server</faultcode>
         <faultstring xsi:type="xsd:string">Error while executing the method 'Write' of service 'xtk:persist'.</faultstring>
         <detail xsi:type="xsd:string">PostgreSQL error: ERROR:  duplicate key violates unique constraint &quot;nmsrecipient_id&quot;Impossible to save document of type 'Recipients (nms:recipient)'</detail>
       </SOAP-ENV:Fault>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

