---
title: 웹 서비스 정보
seo-title: 웹 서비스 정보
description: 웹 서비스 정보
seo-description: null
page-status-flag: never-activated
uuid: f0b21cb3-aa75-4f54-a9f5-64e880f93e53
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 65919173-3ce0-4d98-936b-f4581df536ae
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# 웹 서비스 정보{#about-web-services}

## Adobe Campaign API 정의 {#definition-of-adobe-campaign-apis}

Adobe Campaign 애플리케이션 서버는 점차 다양해지고 복잡해지는 회사 정보 시스템과의 개방성과 간편한 통합을 위해 설계되었습니다.

Adobe Campaign API는 애플리케이션 내의 JavaScript와 애플리케이션 외부의 SOAP에서 사용됩니다. 이들은 농축될 수 있는 일반 함수의 라이브러리를 구성합니다. 자세한 내용은 SOAP [메서드](../../configuration/using/implementing-soap-methods.md)구현을 참조하십시오.

>[!CAUTION]
>
>공인 엔진 호출 수는 라이선스 계약에 따라 다릅니다. For more on this, refer to [this page](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-classic---product-description.html).\
>전체 설명을 포함한 모든 API 목록은 [이 전용 설명서에서](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html)확인할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

Adobe Campaign API를 사용하기 전에 다음 주제를 알고 있어야 합니다.

* Javascript
* SOAP 프로토콜
* Adobe Campaign 데이터 모델

## Adobe Campaign API 사용 {#using-adobe-campaign-apis}

Adobe Campaign에서는 두 가지 유형의 API를 사용합니다.

* 일반 데이터는 데이터 모델 데이터를 쿼리하기 위해 API에 액세스합니다. 데이터 [지향 API를 참조하십시오](../../configuration/using/data-oriented-apis.md).
* 각 개체에 대해 작업을 수행할 수 있는 비즈니스 특정 API:전달, 워크플로우, 구독 등 비즈니스 [지향 API를 참조하십시오](../../configuration/using/business-oriented-apis.md).

API를 개발하고 Adobe Campaign과 상호 작용하려면 데이터 모델에 익숙해야 합니다. Adobe Campaign을 사용하면 베이스에 대한 전체 설명을 생성할 수 있습니다. 모델의 [설명을 참조하십시오](../../configuration/using/data-oriented-apis.md#description-of-the-model).

## SOAP 호출 {#soap-calls}

SOAP 프로토콜을 사용하면 리치 클라이언트, 웹 서비스를 사용하는 타사 애플리케이션 또는 JSP를 통해 기본적으로 API 메서드를 호출할 수 있습니다.

![](assets/s_ncs_configuration_architecture.png)

SOAP 메시지의 구조는 다음과 같습니다.

* 메시지의 구조를 정의하는 봉투,
* 선택적 헤더,
* 호출과 응답에 대한 정보가 들어 있는 본문입니다
* 오류 조건을 정의하는 오류 관리입니다.

## 리소스 및 교환 {#resources-and-exchanges}

다음 스키마는 Adobe Campaign API 사용과 관련된 다양한 리소스를 보여줍니다.

![](assets/s_ncs_integration_webservices_schema_pres.png)

## &#39;ExecuteQuery&#39; 메서드의 SOAP 메시지 예 {#example-of-a-soap-message-on-the--executequery--method--}

이 예제에서 SOAP 쿼리는 문자열을 인증(세션 토큰)의 매개 변수로 사용하는 &quot;ExecuteQuery&quot; 메서드와 실행할 쿼리의 설명에 대한 XML 내용을 호출합니다.

자세한 내용은 ExecuteQuery(xtk:queryDef) [를 참조하십시오](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-).

>[!NOTE]
>
>이 서비스에 대한 WSDL 설명은 다음 예제에서 완료됩니다.웹 [서비스 설명:WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl).

### SOAP 쿼리 {#soap-query}

```
<?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQuery xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <__sessiontoken xsi:type='xsd:string'/>
        <entity xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <queryDef firstRows="true" lineCount="200" operation="select" schema="nms:rcpGrpRel" startLine="0" startPath="/" xtkschema="xtk:queryDef">
          ...
          </queryDef>
        </entity>
      </ExecuteQuery>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

요소는 `<soap-env:envelope>` SOAP 편지 봉투를 나타내는 메시지의 첫 번째 요소입니다.

요소는 `<soap-env:body>` 둘러싸기의 첫 번째 하위 요소입니다. 여기에는 메시지 설명(예: 쿼리 또는 응답 내용)이 포함됩니다.

호출할 메서드는 SOAP 메시지의 본문으로부터 `<executequery>` 요소에 입력됩니다.

SOAP에서 매개 변수는 모양에 따라 인식됩니다. 첫 번째 매개 변수인 인증 `<__sessiontoken>`체인을 사용하는 두 번째 매개 변수는 `<querydef>` 요소의 쿼리에 대한 XML 설명입니다.

### SOAP 응답 {#soap-response}

```
<?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQueryResponse xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <pdomOutput xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <rcpGrpRel-collection><rcpGrpRel group-id="1872" recipient-id="1362"></rcpGrpRel></rcpGrpRel-collection>
        </pdomOutput>
      </ExecuteQueryResponse>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

쿼리 결과는 `<pdomoutput>` 요소에서 입력됩니다.

## 오류 관리 {#error-management}

SOAP 오류 응답 예:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <SOAP-ENV:Fault>
      <faultcode>SOAP-ENV:Server</faultcode>
      <faultstring>Error while executing 'Write' of the 'xtk:persist'.</faultstring> service
      <detail>ODBC error: [Microsoft][ODBC SQL Server Driver][SQL Server]Cannot insert duplicate key row in object 'XtkOption' with unique index 'XtkOption_name'. SQLSTate: 23000
ODBC error: [Microsoft][ODBC SQL Server Driver][SQL Server]The statement has been terminated. SQLSTate: 01000 Cannot save the 'Options (xtk:option)' document </detail>
    </SOAP-ENV:Fault>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

SOAP 메시지 본문에 있는 `<soap-env:fault>` 요소는 웹 서비스를 처리하는 동안 발생하는 오류 신호를 전달하는 데 사용됩니다. 이것은 다음 하위 요소로 구성됩니다.

* `<faultcode>` :오류 유형을 나타냅니다. 오류 유형은 다음과 같습니다.

   * 사용된 SOAP 버전과 호환되지 않는 경우 &quot;버전 불일치&quot;
   * 메시지 헤더에 문제가 있는 경우 &quot;MustUnderstand&quot;를 참조하십시오.
   * &quot;클라이언트&quot;가 고객에게 정보가 없는 경우
   * 서버에서 처리를 실행하는 데 문제가 있는 경우 &quot;서버&quot;입니다.

* `<faultstring>` :오류를 설명하는 메시지
* `<detail>` :긴 오류 메시지

요소가 확인되면 서비스 호출의 성공 또는 실패가 `<faultcode>` 식별됩니다.

>[!CAUTION]
>
>모든 Adobe Campaign 웹 서비스가 오류를 처리합니다. 따라서 반환된 오류를 처리하기 위해 각 호출을 테스트하는 것이 좋습니다.

C#의 오류 처리 예:

```
try 
{
  // Invocation of method
  ...
}
catch (SoapException e)
{
  System.Console.WriteLine("Soap exception: " + e.Message);        
  if (e.Detail != null)
    System.Console.WriteLine(e.Detail.InnerText);
}
```

## 웹 서비스 서버(또는 EndPoint)의 URL {#url-of-web-service-server--or-endpoint-}

웹 서비스를 제출하려면 해당 서비스 메서드를 구현하는 Adobe Campaign 서버에 연결해야 합니다.

서버 URL은 다음과 같습니다.

[https://`<server>`/nl/jsp/soaprouter.jsp&#39;](https://XXXX//nl/jsp/soaprouter.jsp)

Adobe **`<server>`** Campaign 애플리케이션 서버(**nlserver 웹**)와 함께
