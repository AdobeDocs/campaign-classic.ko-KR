---
product: campaign
title: 자동 개인 정보 보호 요청 프로세스
description: 자동 개인 정보 보호 요청 프로세스를 설정하는 방법 알아보기
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: a8044037e889f59d4288a0746001e84d319f6bcf
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 98%

---

# 자동 개인 정보 보호 요청 프로세스 {#automatic-privacy-request-api}

![](../../assets/v7-only.svg)

Adobe Campaign은 자동 개인 정보 보호 요청 프로세스를 설정할 수 있는 **API**&#x200B;를 제공합니다.

API를 사용하면 일반 개인 정보 보호 프로세스는 인터페이스](privacy-requests-ui.md)를 사용하는 [과 동일합니다. 유일한 차이점은 개인 정보 보호 요청을 생성하는 것입니다. Adobe Campaign에서 요청을 생성하는 대신 요청 정보가 포함된 POST가 Campaign으로 전송됩니다. 모든 요청에 대해 새 항목이 **[!UICONTROL Privacy Requests]** 화면에 추가됩니다. 그런 다음 개인 정보 기술 워크플로우에서는 인터페이스를 사용하여 추가된 요청과 동일한 방법으로 요청을 처리합니다.

API를 사용하여 개인 정보 보호 요청을 제출하는 경우 반환된 데이터를 테스트하려면 첫 번째 DELETE 요청에 대해 **2단계 프로세스**&#x200B;가 활성화된 상태로 두는 것이 좋습니다. 테스트가 완료되면 DELETE 요청 프로세스가 자동으로 실행되도록 2단계 프로세스를 비활성화할 수 있습니다.

**[!UICONTROL CreateRequestByName]** JS API는 다음과 같이 정의됩니다.

>[!NOTE]
>
>**gdprRequest** API를 사용하는 경우에도 계속 사용할 수 있지만 새로운 **privacyRequest** API를 사용하는 것이 좋습니다.

>[!IMPORTANT]
>
>API를 사용하려면 **[!UICONTROL Privacy Data Right]** 명명된 권한이 필요합니다.

```
<method library="nms:gdpr.js" name="CreateRequestByName" static="true">
 <help>Create a new GDPR Request using namespace internal name</help>
 <parameters>
  <param name="namespaceName" type="string" desc="Namespace internal name"/>
  <param name="reconciliationValue" type="string" desc="Reconciliation value"/>
  <param name="type" type="long" desc="Reconciliation value"/>
  <param name="confirmDeletePending" type="boolean" desc="Request confirm before deleting data"/>
  <param name="regulation" type="long" desc="regulation of newly created request"/>
  <param name="id" type="long" inout="out" desc="ID of newly created request"/>
 </parameters>
</method>
```

>[!NOTE]
>
>&#39;규정&#39; 필드는 Campaign Classic 20.2(빌드 9178+)를 사용하는 경우에만 사용할 수 있습니다.
>
>20.2로 마이그레이션하는 경우 이미 API를 사용 중이라면 위와 같이 &#39;규정&#39; 필드를 추가해야 합니다. 이전 빌드를 사용하는 경우 &#39;규정&#39; 필드 없이 API를 계속 사용할 수 있습니다.

## 외부에서 API 호출 {#invoking-api-externally}

다음은 외부에서 API를 호출하는 방법(API를 통한 인증 및 개인 정보 API에 대한 세부 정보)의 예입니다. 개인 정보 API에 대한 자세한 내용은 [API 설명서](https://experienceleague.adobe.com/developer/campaign-api/api/s-nms-privacyRequest.html?lang=ko)를 참조하십시오. 또한 [웹 서비스 호출 설명서](../../configuration/using/web-service-calls.md)를 참조하십시오.

우선 API를 통해 인증을 수행해야 합니다.

1. 다음 URL을 통해 **xtk:session** WSDL을 다운로드합니다. **`<server url>`/nl/jsp/schemawsdl.jsp?schema=xtk:session**.

1. &quot;Logon&quot; 메서드를 사용하고 사용자 이름 및 암호를 요청의 매개 변수로 전달합니다. 세션 토큰이 포함된 응답을 가져옵니다. 다음은 SoapUI를 사용하는 예제입니다.

   ![](assets/do-not-localize/privacy-api.png)

1. 반환된 세션 토큰을 모든 하위 시퀀스 API 호출에 대한 인증으로 사용합니다. 24시간 후에 만료됩니다.

그런 다음 개인 정보 API를 호출합니다.

1. 다음 URL에서 WSDL을 다운로드합니다. **`<server url>`/nl/jsp/schemawsdl.jsp?schema=nms:privacyRequest**.

1. 특정 개인 정보 보호 요청을 만들려면 **[!UICONTROL CreateRequestByName]**&#x200B;을(를) 사용합니다.

   다음은 **[!UICONTROL CreateRequestByName]**&#x200B;을(를) 사용하는 예제입니다. 위에서 제공한 세션 토큰을 인증으로 사용하는 방법을 참고하십시오. 응답은 생성된 요청의 ID입니다.

   ![](assets/do-not-localize/privacy-api-2.png)

   위의 단계를 수행하는 데 도움이 되도록 다음 사항을 고려하십시오.

   * **nms:gdprRequest** 스키마에서 **queryDef**&#x200B;을 사용하여 Access 요청의 상태를 확인할 수 있습니다.
   * **nms:gdprRequestData** 스키마에서 **queryDef**&#x200B;을 사용하여 Access 요청의 결과를 가져올 수 있습니다.
   * **&quot;$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id&quot;**&#x200B;에서 XML 파일을 다운로드하려면 허용 목록에 있는 IP에서 로그인하고 액세스해야 합니다. 이렇게 하려면 JSSP에서 생성한 파일에 액세스할 수 있는 웹 애플리케이션을 만듭니다.

## JS에서 API 호출 {#invoking-api-from-js}

다음은 Campaign Classic 내의 JS에서 API를 호출하는 방법의 예입니다.

>[!NOTE]
>
>&#39;규정&#39; 필드는 Campaign Classic 20.2(빌드 9178+)를 사용하는 경우에만 사용할 수 있습니다.
>
>20.2로 마이그레이션하는 경우 이미 API를 사용 중이라면 &#39;규정&#39; 필드를 추가해야 합니다. 이전 빌드를 사용하는 경우 &#39;규정&#39; 필드 없이 API를 계속 사용할 수 있습니다.

* **이전 빌드(GDPR 패키지 포함)를 사용**&#x200B;하는 경우 아래와 같이 &#39;규정&#39; 필드 없이 API를 계속 사용할 수 있습니다.

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
   It requires 4 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // GDPR_REQUEST_TYPE_ACCESS = 1;
   // GDPR_REQUEST_TYPE_DELETE = 2;
   var requestType = GDPR_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* **20.2로 마이그레이션**&#x200B;하고 있고 API를 이미 사용하고 있는 경우 아래와 같이 &#39;규정&#39; 필드를 추가해야 합니다.

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is mandatory parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* **Campaign Classic 20.2(빌드 9178+) 또는 상위 빌드를 사용**&#x200B;하는 경우 다음과 같이 &#39;규정&#39; 필드는 선택 사항입니다.

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values 
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is optional parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```
