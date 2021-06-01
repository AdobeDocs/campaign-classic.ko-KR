---
product: campaign
title: 비즈니스 지향 API
description: 비즈니스 지향 API
audience: configuration
content-type: reference
topic-tags: api
exl-id: e6638870-3141-4f12-b904-db436127c0d1
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 3%

---

# 비즈니스 지향 API{#business-oriented-apis}

비즈니스 API는 각 개체 유형별로 다릅니다. 이 변수는 다음과 같은 효과를 갖습니다.

* 게재:

   * 게재 작업을 만들려면 [SubmitDelivery(nms:delivery)](#submitdelivery--nms-delivery-),
   * 캠페인 보내기(시작, 일시 중지, 중지, 증명 보내기),
   * 게재 로그를 복구하는 중입니다.

* 워크플로우:

   * 워크플로우 시작,
   * 프로세스 확인 등

      JavaScript](../../configuration/using/soap-methods-in-javascript.md)에서 [SOAP 메서드를 참조하십시오.

* 콘텐츠 관리
* 구독 관리에서 [구독 (nms:subscription)](#subscribe--nms-subscription-) 및 [구독 취소(nms:subscription)](#unsubscribe--nms-subscription-)를 참조하십시오.
* 데이터 프로세스:가져오기, 내보내기.

이 섹션에서는 &quot;구독&quot;, &quot;구독 취소&quot; 및 &quot;SubmitDelivery&quot; 서비스의 사용에 대해 자세히 설명합니다.

>[!IMPORTANT]
>
>[Campaign JSAPI ](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) 설명서에는 Adobe Campaign에서 SOAP 호출 및 Javascript 사용에 대한 추가 정보와 애플리케이션에서 사용되는 모든 메서드 및 함수에 대한 전체 참조가 포함되어 있습니다.

## 구독 (nms:subscription) {#subscribe--nms-subscription-}

이 서비스를 사용하면 수신자를 정보 서비스에 구독하고 수신자 프로필을 업데이트할 수 있습니다.

서비스를 호출하려면 다음 매개 변수가 필요합니다.

* 인증,
* 구독 서비스의 내부 이름,
* 받는 사람 정보(&quot;nms:recipient&quot; 스키마에서)가 포함된 XML 문서
* 수신자가 없는 경우 수신자를 만들 부울입니다.

&quot;nms:subscription&quot; 스키마의 &quot;subscribe&quot; 메서드에 대한 설명:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

조정 키의 정의는 XML 문서의 `<recipient>` 요소에 있는 _**키** 속성을 통해 입력해야 합니다. 이 특성의 내용은 쉼표로 구분된 XPath 목록입니다.

이 호출은 오류를 제외하고 데이터를 반환하지 않습니다.

### 예제 {#examples}

전자 메일 주소에서 수신자 조정 키를 사용한 구독:입력 XML 문서는 이 필드에 있는 전자 메일 주소와 키의 정의를 참조해야 합니다.

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

구독과 수신자를 업데이트합니다.

```
<recipient _key="email, [folder-id]" email= "john.doe@adobe.com" folder-id="1305" firstName="John" lastName="Doe"/>
```

### SOAP 메시지 예 {#example-of-soap-messages}

* 쿼리:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:Subscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <sessiontoken xsi:type='xsd:string'/>
         <service xsi:type='xsd:string'>SVC1</service>
         <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <recipient _key="@email" email= "john.doe@adobe.com/>
         </content>
         <create xsi:type='xsd:boolean'>true</create>
       </m:Subscribe>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* 응답:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:SubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </m:SubscribeResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

## 구독 취소(nms:subscription) {#unsubscribe--nms-subscription-}

이 서비스를 사용하면 정보 서비스에서 수신자의 구독을 취소하고 수신자 프로필을 업데이트할 수 있습니다.

서비스를 호출하려면 다음 매개 변수가 필요합니다.

* 인증,
* 구독을 취소할 서비스의 내부 이름입니다.
* 받는 사람 정보(&quot;nms:recipient&quot; 스키마에서)가 포함된 XML 문서

nms:subscription 스키마의 &quot;Subscription&quot; 메서드에 대한 설명:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

조정 키의 정의는 XML 문서의 `<recipient>` 요소에 있는 _key 특성을 통해 입력해야 합니다. 이 특성의 내용은 쉼표로 구분된 XPath 목록입니다.

수신자가 데이터베이스에 없거나 관련 정보 서비스를 구독하지 않은 경우 서비스는 작업을 수행하지 않고 오류를 생성하지 않습니다.

>[!NOTE]
>
>서비스 이름이 매개 변수로 지정되지 않은 경우 수신자가 자동으로(@blackList=&quot;1&quot;)차단 목록에 있게 됩니다.

이 호출은 오류를 제외하고 데이터를 반환하지 않습니다.

### SOAP 메시지 예 {#example-of-soap-messages-1}

쿼리:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:Unsubscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    <sessiontoken xsi:type='xsd:string'/>
    <service xsi:type='xsd:string'>SVC1</service>
    <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
      <recipient _key="@email" email= "john.doe@adobe.com/>
    </content>
  </m:Unsubscribe>
</SOAP-ENV:Body>
```

응답:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:UnsubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    </m:UnsubscribeResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## SubmitDelivery (nms:delivery) {#submitdelivery--nms-delivery-}

이 서비스를 통해 게재 작업을 만들고 제출할 수 있습니다.

서비스를 호출하려면 다음 매개 변수가 필요합니다.

* 인증,
* 게재 템플릿의 내부 이름,
* 추가 배달 데이터가 포함된 선택적 XML 문서입니다.

성능 문제가 발생할 수 있으므로 이 API를 볼륨에서 호출하면 안 됩니다.

스키마에 있는 메서드에 대한 설명:

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

게재 템플릿은 Adobe Campaign 클라이언트 콘솔에서 만들어야 합니다. 모든 게재에 공통되는 매개 변수(보낸 사람 주소 또는 메시지의 유효 기간)가 포함되어 있습니다.

입력 XML 문서는 &quot;nms:delivery&quot; 스키마의 구조를 따르는 게재 템플릿 조각입니다. 게재 템플릿에서 정적으로 정의할 수 없는 모든 추가 데이터(예: 타겟으로 수신자 목록)가 포함됩니다.

이 호출은 오류를 제외하고 데이터를 반환하지 않습니다.

### XML 문서 예 {#xml-document-example}

이 예는 외부 데이터 소스(이 경우 파일)의 사용자 지정 게재 템플릿을 기반으로 합니다. 구성은 게재 템플릿에서 완전히 설명되므로, 호출이 발생할 때 계속 전송되는 모든 것은 `<externalsource>` 요소의 파일 컨텐츠입니다.

```
<delivery>
  <targets fromExternalSource="true">
    <externalSource>
      MsgId|ClientId|Title|Name|FirstName| Mobile|Email| Market_segment|Product_affinity1 |Product_affinity2|Product_affinity3| Product_affinity4| Support_Number|Amount|Threshold1|000001234|M.| Doe|John|0650201020| john.doe@adobe.com
|1| A1|A2|A3|A4|E12|120000|100000
    </externalSource>
  </target>
</delivery>
```

게재 템플릿이 없는 경우 다음 샘플을 사용할 수 있습니다.

```
<delivery>
<targets fromExternalSource="true" targetMode="1" noReconciliation="true" addressField="Email" >  
    <fileFormat active="true">  
      <source format="text" type="text">  
        <dataSourceConfig >  
          <dataSourceColumn label="Email" name="Email" type="string"/>  
        </dataSourceConfig>  
      </source>  
      <destination type="xtkDataStore"/>  
    </fileFormat>  
    <externalSource><![CDATA[not-a-repicipient@domain.com]]></externalSource>  
  </targets> 
</delivery> 
```
