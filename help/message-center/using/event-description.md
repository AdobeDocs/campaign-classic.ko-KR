---
title: 이벤트 설명
seo-title: 이벤트 설명
description: 이벤트 설명
seo-description: null
page-status-flag: never-activated
uuid: 7b174ffd-28b2-4147-b992-e17b0b2cf733
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 3c8388d8-1a91-4d16-a8ac-016f643c6009
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# 이벤트 설명{#event-description}

## 트랜잭션 메시징 데이터 모델 정보 {#about-transactional-messaging-datamodel}

트랜잭션 메시지는 캠페인 데이터 모델을 사용하며 두 개의 별도 테이블을 사용합니다. 이러한 표, **NmsRtEvent** 및 **NmsBatchEvent**&#x200B;에는 동일한 필드가 포함되어 있으므로 한 번에 실시간 이벤트를 관리하고 다른 한 손에서는 이벤트를 일괄 처리할 수 있습니다.

## SOAP 메서드 {#soap-methods}

이 섹션에서는 트랜잭션 메시지 모듈 스키마와 연관된 SOAP 방법에 대해 자세히 설명합니다.

두 **가지 PushEvent** 또는 **PushEvents** SOAP 메서드는 **두** nms:rtEvent **및 nms:** BatchEventdataschemas에연결됩니다. 이벤트가 &quot;일괄 처리&quot; 또는 &quot;실시간&quot; 유형인지를 판별하는 정보 시스템입니다.

* **PushEvent** 를 사용하면 메시지에 단일 이벤트를 삽입할 수 있습니다.
* **PushEvents** 를 사용하면 메시지에 일련의 이벤트를 삽입할 수 있습니다.

두 메서드에 액세스하기 위한 WSDL 경로는 다음과 같습니다.

* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:rtEvent실시간** 유형 스키마에 액세스하기 위해 필요합니다.
* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:batchEvent** 배치 유형 스키마에 액세스하는 방법

두 메서드 모두 트랜잭션 메시징 모듈에 로그온하기 위한 **`<urn:sessiontoken>`** 요소를 포함합니다. 신뢰할 수 있는 IP 주소를 통해 식별 방법을 사용하는 것이 좋습니다. 세션 토큰을 검색하려면 로그온 SOAP 호출을 수행한 다음 get token 다음에 로그오프를 수행합니다. 여러 RT 호출에 동일한 토큰을 사용합니다. 이 섹션에 포함된 예는 권장되는 세션 토큰 방법을 사용하는 것입니다.

부하 균형 있는 서버를 사용하는 경우 RT 메시지 수준에서 사용자/암호 인증을 사용할 수 있습니다. 예:

```
<PushEvent xmlns="urn:nms:rtEvent">
<sessiontoken>mc/PASSWORD</sessiontoken>
<domEvent>
<rtEvent wishedChannel="41" type="rt_MobileJourney_iOS_Push" registrationToken="c3ddc8aaecc24822df25d0f49865cca61ea3f86c61bfa53ae4d37294e37f4a1c" hashlpId="27EE7571EC14DBA23B9B5CC0EF79BB782DAECF4C03C88E5D92CC9B9DAC4E5DDA" correlationId="415b7593-4f6f-e911-811f-00505691247c" xmlns="">
<mobileApp uuid="236B24DC-C073-412F-8BCB-AC7207096258" _operation="none"/>
<ctx>...</ctx>
</rtEvent>
</domEvent>
</PushEvent>
```

PushEvent **메서드는** 이벤트를 포함하는 **`<urn:domevent>`** 매개 변수로 구성됩니다.

PushEvents **메서드는** 이벤트를 포함하는 **`<urn:domeventcollection>`** 매개 변수로 구성됩니다.

PushEvent 사용 예:

```
<urn:PushEvent>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEvent>
 
   <rtEvent>
   
   ...
   
   </rtEvent>
 
 </urn:domEvent>

</urn:PushEvent>
```

>[!NOTE]
>
>PushEvents 메서드를 호출하는 **경우** 표준 XML을 준수하도록 부모 XML 요소를 추가해야 합니다. 이 XML 요소는 이벤트에 포함된 다양한 **`<rtevent>`** 요소의 프레임을 만듭니다.

PushEvents 사용 예:

```
<urn:PushEvents>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEventCollection>
 
   <Events>
   
     <rtEvent>... </rtEvent>
     
     <rtEvent>... </rtEvent>
     
     ...
   
   </Events>
 
 </urn:domEventCollection>

</urn:PushEvents>
```

및 **`<rtevent>`** **`<batchevent>`** 요소에는 필수 하위 요소뿐만 아니라 속성 집합도 있습니다.메시지 데이터를 **`<ctx>`** 통합합니다.

>[!NOTE]
>
>이 **`<batchevent>`** 요소를 사용하면 이벤트를 &quot;배치&quot; 대기열에 추가할 수 있습니다. 그러면 **`<rtevent>`** 이벤트가 &quot;실시간&quot; 큐에 추가됩니다.

필수 요소 **`<rtevent>`** 및 **`<batchevent>`** 요소의 특성은 @type 및 @email입니다. @type의 값은 실행 인스턴스를 구성할 때 정의된 항목별 목록 값과 같아야 합니다. 이 값을 사용하면 배달 중에 이벤트 컨텐츠에 연결할 템플릿을 정의할 수 있습니다.

`<rtevent>  configuration example: </rtevent>`

```
<rtEvent type="order_confirmation" email="john.doe@domain.com" origin="eCommerce" wishedChannel="0" externalId="1242" mobilePhone="+33620202020"> 
```

이 예에서는 두 개의 채널이 제공됩니다.이메일 주소와 휴대폰 번호. 원하는 **채널을** 사용하면 이벤트를 메시지로 변환할 때 사용할 채널을 선택할 수 있습니다. &quot;0&quot; 값은 이메일 채널, 모바일 채널에 대한 &quot;1&quot; 값에 해당합니다.

이벤트 배달을 연기하려면 원하는 날짜 뒤에 **[!UICONTROL scheduled]** 필드를 추가합니다. 이 날짜에 이벤트가 메시지로 변환됩니다.

@hospentChannel 및 @emailFormat 속성을 숫자 값으로 채우는 것이 좋습니다. 데이터 스키마 설명에 숫자 값과 레이블을 연결하는 함수 테이블이 있습니다.

>[!NOTE]
>
>허가된 모든 속성에 대한 자세한 설명과 해당 값은 **nms:rtEvent** 및 **nms:BatchEvent 데이터** 스키마에서 확인할 수 있습니다.

이 **`<ctx>`** 요소에는 메시지 데이터가 포함됩니다. XML 컨텐츠가 열려 있으므로 전달할 컨텐츠에 따라 구성할 수 있습니다.

>[!NOTE]
>
>전달 중에 서버가 오버로드되지 않도록 메시지에 포함된 XML 노드의 수와 크기를 최적화하는 것이 중요합니다.

데이터 예:

```
   <ctx>
               <client>
                        <firstname>John</firstname>
                        <lastname>Doe</lastname>
               </client>
               <action>
                         <type>Order confirmation</type>
                          <number>CN23453</number>
               </action>
               <orderdetails>
                          <article num="1">
                                   <name>Generic USB key</name>
                                   <price>20</price>
                           </article>
               </orderdetails>
    </ctx>
   
```

## SOAP 호출에서 반환된 정보 {#information-returned-by-the-soap-call}

이벤트가 수신되면 Adobe Campaign은 고유한 반환 ID를 생성합니다. 보관된 이벤트 버전의 ID입니다.

>[!CAUTION]
>
>SOAP 호출을 수신할 때 Adobe Campaign은 이메일 주소 형식을 확인합니다. 이메일 주소 형식이 잘못되면 오류가 반환됩니다.

* 이벤트 처리가 성공한 경우 메서드에서 반환되는 식별자의 예:

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">72057594037935966</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

반환 식별자 값이 0보다 엄격하게 크면 이벤트가 Adobe Campaign에 성공적으로 보관되었음을 의미합니다.

그러나 이벤트가 처리되지 않으면 오류 메시지 또는 0과 같은 값이 반환됩니다.

* 쿼리에 로그인이 없거나 지정한 연산자에 필요한 권한이 없을 때 실패한 이벤트의 처리 예:

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <SOAP-ENV:Fault>
            <faultcode>SOAP-ENV:Client</faultcode>
            <faultstring xsi:type="xsd:string">Error while reading parameters of method 'PushEvent' of service 'nms:rtEvent'.</faultstring>
            <detail xsi:type="xsd:string">Invalid login or password. Connection denied.</detail>
         </SOAP-ENV:Fault>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* 쿼리의 오류로 인해 실패한 이벤트의 예(XML 분류가 준수하지 않음):

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <SOAP-ENV:Fault>
            <faultcode>SOAP-ENV:Client</faultcode>
            <faultstring xsi:type="xsd:string">The XML SOAP message is invalid (service 'PushEvent', method 'nms:rtEvent').</faultstring>
            <detail xsi:type="xsd:string"><![CDATA[(16:8) : Expected end of tag 'rtevent'
   Error while parsing XML string '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
      <soapenv:Header/>
      <soapenv:Body>
         <urn:PushEvent>
            <urn:sessiontoken>mc/</urn:sessiontoken>
            <urn:domEvent>
   <rtevent type="create_account" email="esther.hall@adobe.com" origin="eCommerce" wishedChannel="email" 
         externalId="1596" language="english" country="EN" emailFormat="2"
         mobilePhone="+447700123123">
     <ctx>
      <website name="eCommerce" url="http://www.eCo']]></detail>
         </SOAP-ENV:Fault>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* 0의 식별자(잘못된 메서드 이름)를 반환하고 실패한 이벤트의 예:

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">0</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

