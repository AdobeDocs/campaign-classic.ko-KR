---
product: campaign
title: 웹 서비스 호출
description: 웹 서비스 호출
feature: API
role: Data Engineer, Developer
exl-id: ce94e7e7-b8f8-4c82-937f-e87d15e50c34
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 1%

---

# 웹 서비스 호출{#web-service-calls}

## 일반 정보 {#general-information}

모든 API 메서드는 웹 서비스 형식으로 표시됩니다. 이렇게 하면 Adobe Campaign 애플리케이션 서버의 기본 진입점인 SOAP 호출을 통해 모든 Adobe Campaign 기능을 관리할 수 있습니다. Adobe Campaign 콘솔 자체는 SOAP 호출만 사용합니다.

웹 서비스를 사용하면 서드파티 시스템에서 많은 애플리케이션을 만들 수 있습니다.

* 백오피스 또는 트랜잭션 시스템에서 동기식 경고, 알림 및 실시간 게재 템플릿 실행
* 단순화된 기능(웹 인터페이스 등)을 갖춘 특수 인터페이스 개발
* 거래 규칙을 관찰하고 기본 물리적 모델과 분리된 상태로 데이터베이스에 있는 데이터의 공급 및 조회.

## 웹 서비스의 정의 {#definition-of-web-services}

Adobe Campaign 애플리케이션 서버에 구현된 웹 서비스의 정의는 데이터 스키마에서 사용할 수 있습니다.

웹 서비스는 데이터 스키마의 문법에 설명되어 있으며 **`<methods>`** 요소에서 사용할 수 있습니다.

```
<methods>
  <method name="GenerateForm" static="true">
    <help>Generates the form in Mail or Web mode</help>
    <parameters>
      <param name="formName" type="string" desc="Name of form"/>
      <param name="mailMode" type="boolean" desc="Generate a form of type Mail"/>
      <param name="result" type="string" inout="out" desc="Result "/>
    </parameters>
  </method>
</methods>
```

다음은 **GenerateForm** 메서드의 정의에 대한 예입니다.

서비스 설명은 `<method>` 요소로 시작합니다. `<parameters>` 요소에서 메서드의 매개 변수 목록이 완료되었습니다. 각 매개 변수는 이름, 유형(부울, 문자열, DOMElement 등)으로 지정됩니다. 설명. &quot;out&quot; 값이 있는 &quot;inout&quot; 속성을 사용하면 &quot;result&quot; 매개 변수가 SOAP 호출 출력에 있다고 지정할 수 있습니다.

&quot;static&quot; 속성(값 &quot;true&quot;가 있음)은 이 메서드를 static으로 설명하므로 메서드의 모든 매개 변수를 선언해야 합니다.

&quot;const&quot; 메서드는 암시적으로 연결된 스키마 형식의 XML 문서를 해당 입력으로 가지고 있습니다.

Adobe Campaign 스키마의 `<method>` 요소에 대한 전체 설명은 [메서드](../../configuration/using/schema/method.md)의 &quot;스키마 참조&quot; 장에서 확인할 수 있습니다.

&quot;xtk:queryDef&quot; 스키마의 &quot;const&quot; 유형 &quot;ExecuteQuery&quot; 메소드의 예:

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

이 메서드의 입력 매개 변수는 &quot;xtk:queryDef&quot; 스키마 형식의 XML 문서입니다.

## 웹 서비스 설명: WSDL {#web-service-description--wsdl}

WSDL(웹 서비스 설명 라이브러리) 파일은 각 서비스에 사용할 수 있습니다. 이 XML 파일은 금속어를 사용하여 서비스를 설명하고 서비스 실행을 위해 연락할 사용 가능한 메서드, 매개 변수 및 서버를 지정합니다.

### WSDL 파일 생성 {#wsdl-file-generation}

WSDL 파일을 생성하려면 웹 브라우저에서 다음 URL을 입력해야 합니다.

https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

포함:

* **`<server>`**: Adobe Campaign 응용 프로그램 서버(nlserver 웹)
* **`<schema>`**: 스키마 식별 키(namespace:schema_name)

### 스키마 &quot;xtk:queryDef&quot;의 &quot;ExecuteQuery&quot; 메서드에 대한 예 {#example-on-the--executequery--method-of-schema--xtk-querydef-}

WSDL 파일은 URL에서 생성됩니다.

`https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef`

WSDL 설명은 웹 서비스를 구성하는 &quot;바인딩&quot;에 의해 프로토콜에 연결된 &quot;포트&quot;에 연결된 메시지를 구성하는 데 사용되는 형식을 정의함으로써 시작합니다.

#### 유형 {#types}

유형 정의는 XML 스키마를 기반으로 합니다. 이 예제에서 &quot;ExecuteQuery&quot; 메서드는 &quot;s:string&quot; 문자열과 XML 문서(`<s:complextype>`)를 매개 변수로 사용합니다. 메서드(&quot;ExecuteQueryResponse&quot;)의 반환 값이 XML 문서(`<s:complextype>`)입니다.

```
<types>
<s:schema elementFormDefault="qualified" targetNamespace="urn:xtk:queryDef">
  <s:element name="ExecuteQuery">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="sessiontoken" type="s:string"/>
        <s:element maxOccurs="1" minOccurs="1" name="entity">
          <s:complexType>
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="ExecuteQueryResponse">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="pdomOutput">
          <s:complexType mixed="true">
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
```

#### 메시지 {#messages}

`<message>`은(는) 보낼 필드 집합의 이름과 형식을 설명합니다. 메서드는 두 개의 메시지를 사용하여 매개 변수(&quot;ExecuteQueryIn&quot;)와 반환 값(&quot;ExecuteQueryOut&quot;)으로 전달합니다.

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### PortType {#porttype}

`<porttype>`은(는) 응답(&quot;output&quot;)을 생성하는 쿼리(&quot;input&quot;)에 의해 트리거된 &quot;ExecuteQuery&quot; 작업의 메시지를 연결합니다.

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### 바인딩 {#binding}

`<binding>` 부분은 SOAP 통신 프로토콜( `<soap:binding>` ), HTTP의 데이터 전송(&quot;전송&quot; 특성 값) 및 &quot;ExecuteQuery&quot; 작업의 데이터 형식을 지정합니다. SOAP Envelope의 본문에는 변형 없이 메시지 세그먼트가 직접 포함됩니다.

```
<binding name="queryDefMethodsSoap" type="tns:queryDefMethodsSoap">
  <soap:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
  <operation name="ExecuteQuery">
    <soap:operation soapAction="xtk:queryDef#ExecuteQuery" style="document"/>
    <input>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </input>
    <output>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </output>
  </operation>
</binding>
```

#### 서비스 {#service}

`<service>` 부분은 Adobe Campaign 응용 프로그램 서버의 URL에서 해당 URI를 사용하여 &quot;XtkQueryDef&quot; 서비스를 설명합니다.

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## 연결 {#connectivity}

Adobe Campaign은 [보안 영역](../../installation/using/security-zones.md) 및 세션 관리 설정을 도입하여 인증 메커니즘에 대한 보안을 강화했습니다.

두 가지 인증 모드를 사용할 수 있습니다.

* **logon 메서드()** 호출을 통해. 이 모드는 세션 토큰과 보안 토큰을 생성합니다. 가장 안전한 모드이므로 가장 권장됩니다.

또는

* 세션 토큰을 만드는 **Adobe Campaign 로그인 + 암호를 통해**. 세션 토큰은 설정된 기간 후에 자동으로 만료됩니다. 이 모드는 권장되지 않으며 일부 영역 설정(allowUserPassword=&quot;true&quot; 및 sessionTokenOnly=&quot;true&quot;)에 대한 응용 프로그램 보안 설정을 줄여야 합니다.

### 세션 토큰 특성 {#session-token-characteristics}

세션 토큰에는 다음과 같은 특성이 있습니다.

* X시간 라이프 사이클(라이프 사이클은 &#39;serverConf.xml&#39; 파일에서 구성할 수 있으며 기본 기간은 24시간입니다.)
* 임의 구성(더 이상 사용자 로그인 및 암호가 포함되지 않음)
* 웹을 통해 액세스할 경우:

   * 세션 토큰은 영구 토큰이 되며 브라우저가 닫히면 삭제되지 않습니다
   * HTTP 전용 쿠키에 배치됩니다(운영자에 대해 쿠키가 활성화되어야 함)

### 보안 토큰 특성 {#security-token-characteristics}

보안 토큰에는 다음과 같은 특성이 있습니다.

* 세션 토큰에서 생성됩니다.
* 이 파일에는 24시간 수명 주기가 있습니다(&#39;serverConf.xml&#39; 파일에서 구성 가능, 기본 기간은 24시간).
* Adobe Campaign 콘솔에 저장됩니다
* 웹을 통해 액세스할 경우:

   * 문서에 저장됩니다.__securityToken 속성
   * 보안 토큰을 업데이트하기 위해 페이지 URL이 업데이트됩니다
   * 토큰이 포함된 숨겨진 필드를 통해 양식도 업데이트됩니다

#### 보안 토큰 이동 {#security-token-movement}

콘솔을 통해 액세스할 경우 다음과 같은 이점이 있습니다.

* 로그온 응답(HTTP 헤더)에서 전송됨
* 각 쿼리(HTTP 헤더)에 사용됨

POST 및 GET HTTP에서:

* 서버가 토큰으로 링크를 완료합니다.
* 서버가 양식에 숨겨진 필드를 추가합니다.

SOAP 호출에서:

* 호출 헤더에 추가됩니다.

### 호출 예 {#call-examples}

* **HttpSoapConnection/SoapService** 사용:

```
  
    var cnx = new HttpSoapConnection("https://serverURL/nl/jsp/soaprouter.jsp");
  var session = new SoapService(cnx, 'urn:xtk:session');
  session.addMethod("Logon", "xtk:session#Logon",
                      ["sessiontoken", "string", "Login", "string", "Password", "string", "Parameters", "NLElement"],
                      ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
  
  var res = session.Logon("", "admin", "pwd", <param/>);
  var sessionToken = res[0];
  var securityToken = res[2];
  
  cnx.addTokens(sessionToken, securityToken);
  var query = new SoapService(cnx, 'urn:xtk:queryDef');
  query.addMethod("ExecuteQuery", "xtk:queryDef#ExecuteQuery",
                      ["sessiontoken", "string", "entity", "NLElement"],
                      ["res", "NLElement"]);
  
  var queryRes = query.ExecuteQuery("", <queryDef operation="select" schema="nms:recipient">
            <select>
              <node expr="@email"/>
              <node expr="@lastName"/>
              <node expr="@firstName"/>
            </select>
            <where>
              <condition expr="@email = 'joe.doe@aol.com'"/>
            </where>
          </queryDef>);
  logInfo(queryRes[0].toXMLString())
```

* **HttpServletRequest** 사용:

>[!NOTE]
>
>다음 **HttpServletRequest** 호출에 사용되는 URL은 **serverConf.xml** 파일의 url 권한 섹션에서 허용 목록 상태여야 합니다. 서버 자체의 URL에도 적용됩니다.

로그온 실행():

```
var req = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req.header["Content-Type"] = "text/xml; charset=utf-8";
req.header["SOAPAction"] =   "xtk:session#Logon";
req.method = "POST";
req.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:session">' +
    '<soapenv:Header/>' +
    '<soapenv:Body>' +
        '<urn:Logon>' +
            '<urn:sessiontoken></urn:sessiontoken>' +
            '<urn:strLogin>LOGIN_HERE</urn:strLogin>' +
            '<urn:strPassword>PASSWORD_HERE</urn:strPassword>' +
            '<urn:elemParameters></urn:elemParameters>' +
        '</urn:Logon>' +
    '</soapenv:Body>' +
'</soapenv:Envelope>';
req.execute();
           
var resp = req.response;
var xmlRes = new XML(String(resp.body).replace("<?xml version='1.0'?>",""));
var sessionToken = String(xmlRes..*::pstrSessionToken);;
var securityToken = String(xmlRes..*::pstrSecurityToken);
```

쿼리 실행:

```
var req2 = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req2.header["Content-Type"] = "text/xml; charset=utf-8";
req2.header["SOAPAction"] =   "xtk:queryDef#ExecuteQuery";req2.header["X-Security-Token"] = securityToken;
req2.header["cookie"]           = "__sessiontoken="+sessionToken;
req2.method = "POST";
req2.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:queryDef">' +
             '<soapenv:Header/><soapenv:Body><urn:ExecuteQuery><urn:sessiontoken/><urn:entity>' +
                '<queryDef operation="select" schema="nms:recipient">' +
                  '<select><node expr="@email"/><node expr="@lastName"/><node expr="@firstName"/></select>' +
                  '<where><condition expr="@email = \'john.doe@aol.com\'"/></where>' +
                '</queryDef>' +
           '</urn:entity></urn:ExecuteQuery></soapenv:Body></soapenv:Envelope>';
req2.execute();
var resp2 = req2.response;
logInfo(resp2.body)
```
