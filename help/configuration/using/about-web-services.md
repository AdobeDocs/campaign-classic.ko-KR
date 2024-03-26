---
product: campaign
title: 웹 서비스 정보
description: 웹 서비스 정보
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: API
role: Data Engineer, Developer
exl-id: 7aa2aef1-2eb6-48a6-82fa-4451bed66216
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 4%

---

# 웹 서비스 정보{#about-web-services}

## Adobe Campaign API의 정의 {#definition-of-adobe-campaign-apis}

Adobe Campaign 애플리케이션 서버는 점점 다양해지고 복잡한 회사 정보 시스템과 개방적이고 쉽게 통합되도록 설계되었습니다.

Adobe Campaign API는 애플리케이션 내의 JavaScript와 애플리케이션 외부의 SOAP에서 사용됩니다. 이러한 라이브러리는 보강할 수 있는 일반 함수 라이브러리를 구성합니다. 자세한 내용은 다음을 참조하십시오. [SOAP 메서드 구현](../../configuration/using/implementing-soap-methods.md).

>[!IMPORTANT]
>
>하루에 인증된 엔진 호출 수는 라이선스 계약에 따라 다릅니다. 자세한 정보는 이 [페이지](https://helpx.adobe.com/kr/legal/product-descriptions/adobe-campaign-classic---product-description.html)를 참조하십시오.\
>전체 설명을 포함한 모든 API 목록은 다음에서 사용할 수 있습니다. [이 전용 설명서](https://experienceleague.adobe.com/developer/campaign-api/api/index.html.

## 필수 구성 요소 {#prerequisites}

Adobe Campaign API를 사용하기 전에 다음 항목에 익숙해야 합니다.

* JavaScript
* 프로토콜
* Adobe Campaign 데이터 모델

## Adobe Campaign API 사용 {#using-adobe-campaign-apis}

Adobe Campaign에서는 두 가지 유형의 API를 사용합니다.

* 데이터 모델 데이터 쿼리를 위한 일반 데이터 액세스 API입니다. 을(를) 참조하십시오 [데이터 지향 API](../../configuration/using/data-oriented-apis.md).
* 게재, 워크플로우, 구독 등 각 오브젝트에 대해 작업을 수행할 수 있는 비즈니스별 API. 을(를) 참조하십시오 [비즈니스 지향 API](../../configuration/using/business-oriented-apis.md).

API를 개발하고 Adobe Campaign과 상호 작용하려면 데이터 모델에 익숙해야 합니다. Adobe Campaign을 사용하면 기본 사항에 대한 전체 설명을 생성할 수 있습니다. 을(를) 참조하십시오 [모델에 대한 설명](../../configuration/using/data-oriented-apis.md#description-of-the-model).

## SOAP 호출 {#soap-calls}

SOAP 프로토콜을 사용하면 리치 클라이언트를 통해 API 메서드를 호출하거나 웹 서비스를 사용하는 타사 응용 프로그램을 호출하거나 이러한 메서드를 기본적으로 사용하는 JSP를 호출할 수 있습니다.

![](assets/s_ncs_configuration_architecture.png)

SOAP 메시지의 구조는 다음과 같습니다.

* 메시지 구조를 정의하는 봉투,
* 선택적 헤더,
* 호출 및 응답에 대한 정보가 포함된 본문,
* 오류 조건을 정의하는 오류 관리.

## 리소스 및 교환 {#resources-and-exchanges}

다음 스키마는 Adobe Campaign API 사용과 관련된 다양한 리소스를 보여줍니다.

![](assets/s_ncs_integration_webservices_schema_pres.png)

## &#39;ExecuteQuery&#39; 메서드에 대한 SOAP 메시지의 예 {#example-of-a-soap-message-on-the--executequery--method--}

이 예에서 SOAP 쿼리는 &quot;ExecuteQuery&quot; 메서드를 호출합니다. 이 메서드는 인증을 위한 매개 변수(세션 토큰)로 문자열을 사용하고 실행할 쿼리 설명에 대한 XML 콘텐츠를 사용합니다.

자세한 내용은 다음을 참조하십시오. [ExecuteQuery(xtk:queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-).

>[!NOTE]
>
>이 서비스의 WSDL 설명은 다음 예제에서 완료됩니다. [웹 서비스 설명: WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl).

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

다음 `<soap-env:envelope>` element는 SOAP 봉투를 나타내는 메시지의 첫 번째 요소입니다.

다음 `<soap-env:body>` 요소는 포락선의 첫 번째 자식 요소입니다. 여기에는 메시지에 대한 설명, 즉 쿼리 또는 응답의 콘텐츠가 포함됩니다.

호출할 메서드가 `<executequery>` 요소를 추가합니다.

SOAP에서 매개변수는 표시 순서에 따라 인식됩니다. 첫 번째 매개 변수, `<__sessiontoken>`는 인증 체인을 가져옵니다. 두 번째 매개변수는 쿼리의 XML 설명입니다. `<querydef>` 요소를 생성하지 않습니다.

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

쿼리 결과는에서 입력됩니다. `<pdomoutput>` 요소를 생성하지 않습니다.

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

다음 `<soap-env:fault>` soap 메시지 본문의 요소는 웹 서비스 처리 중에 발생하는 오류 신호를 전달하는 데 사용됩니다. 이는 다음 하위 요소로 구성됩니다.

* `<faultcode>` : 오류 유형을 나타냅니다. 오류 유형은 다음과 같습니다.

   * 사용된 SOAP 버전과 호환되지 않는 경우 &quot;VersionMismatch&quot;
   * 메시지 헤더에 문제가 있는 경우 &quot;MustUnderstand&quot;
   * 클라이언트에서 일부 정보가 누락된 경우 &quot;클라이언트&quot;
   * 서버에서 처리를 실행하는 데 문제가 있는 경우 &quot;서버&quot;

* `<faultstring>` : 오류를 설명하는 메시지
* `<detail>` : 긴 오류 메시지

다음 경우에 서비스 호출의 성공 또는 실패가 식별됩니다. `<faultcode>` 요소가 확인되었습니다.

>[!IMPORTANT]
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

웹 서비스를 제출하려면 해당 서비스 방법을 구현하는 Adobe Campaign 서버에 연결해야 합니다.

서버 URL은 다음과 같습니다.

https://serverName/nl/jsp/soaprouter.jsp

포함 **`<server>`** Adobe Campaign 애플리케이션 서버(**nlserver 웹**).
