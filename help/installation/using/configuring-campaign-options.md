---
solution: Campaign Classic
product: campaign
title: Campaign 옵션 구성
description: Campaign 옵션을 구성하는 방법 알아보기
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: 3413a54b1f45d23dcec9bf363bcf714a94642245
workflow-type: tm+mt
source-wordcount: '3941'
ht-degree: 1%

---

# Campaign Classic 옵션 목록{#configuring-campaign-options}

**[!UICONTROL Administration / Platform / Options]** 노드를 사용하여 Adobe Campaign 옵션을 구성할 수 있습니다. 일부는 Campaign을 설치할 때 기본적으로 제공되며, 필요한 경우 수동으로 추가할 수 있습니다. 사용 가능한 옵션은 인스턴스에 설치된 패키지에 따라 다릅니다.

>[!CAUTION]
>
>* 이 페이지에 나열되지 않은 옵션은 내부 전용이며 **은(는) 수정할 수 없습니다**.
   >
   >
* Adobe Campaign 옵션 수정 또는 업데이트는 전문가 사용자만 수행할 수 있습니다.


## 게재 {#delivery}

<table> 
 <thead> 
  <tr> 
   <th> 옵션 이름 </th> 
   <th> 설명 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgDate</span> <br /> </td> 
   <td> 게재 가능성 인스턴스에서 검색한 마지막 broadLogMsg 날짜입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> 게재 가능성 인스턴스로 보낸 마지막 broadLogMsg 날짜입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> 게재 보고서 식별자. 식별자를 얻으려면 지원 센터에 문의하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> 받은 편지함 렌더링에 테스트 주소를 사용할 스키마 목록입니다. (요소 이름은 쉼표로 구분됨) 예:custom_nms_recipient<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> 특정 연산자 또는 운영자 그룹이 게재 속성에서 게재를 시작하도록 지정된 경우 게재를 담당하는 연산자가 전송을 확인하도록 허용할 수 있습니다.</p><p> 이렇게 하려면 값으로 "1"을 입력하여 옵션을 활성화합니다. 이 옵션을 비활성화하려면 "0"을 입력합니다.</p><p> 전송 확인 프로세스는 기본값으로 작동합니다.게재 속성에서 전송을 위해 지정된 운영자 또는 그룹(또는 관리자)만 전송을 확인하고 수행할 수 있습니다. <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">이 섹션</a>을 참조하십시오.</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign은 "Nms_DefaultRcpSchema" 전역 변수를 사용하여 기본 수신자 데이터베이스(nms:recipient)와의 대화 상자를 사용합니다.<br /> 옵션 값은 외부 수신자 테이블과 일치하는 스키마 이름과 일치해야 합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> 게재를 청구 보고서에서 주 수신자로 간주하기 위한 최소 수신자 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> 새 템플릿에 대한 기본 라우팅 서비스 공급자입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> 한 번에 전송을 위해 만들어진 BroadLogs 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> 트랜잭션당 로그(broadLogs)를 표에 삽입:일괄 처리당 처리할 행 수<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> 중간 소싱 게재를 분석할 때 게재 부분의 그룹화 크기입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> 게재에 대한 기본 배달 기간(초)입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> 배달 메시지를 정규화하기 위한 정규 표현식입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> 값으로 "1"을 입력하면 더 이상 연락하지 않으려는 수신자를 제외할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicationsRecipients</span> <br /> </td> 
   <td> 값으로 "1"을 입력하면 double을 자동으로 무시할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span> <br /> </td> 
   <td> 메시지에 응답할 때 사용되는 오류 주소의 구문을 정의할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span> <br /> </td> 
   <td> 메시지를 보낼 때 사용되는 보낸 사람 주소의 구문을 정의할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> 개인화된 URL에서 다운로드한 및 이메일에 첨부된 이미지를 검색할 때 서버에서 응답을 받을 때 시간 제한(초)을 정의할 수 있습니다. 이 값을 초과하면 메시지를 보낼 수 없습니다. 기본값은 60초입니다.<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> 개인화된 URL에서 다운로드되고 이메일에 첨부된 이미지에 허용되는 최대 크기(바이트)를 정의할 수 있습니다. 기본값은 100,000바이트입니다. 증명을 보내고 이메일을 처리하기 위해 이미지를 다운로드할 때 이미지 크기가 이 값을 초과하거나 다운로드 문제가 있는 경우 게재 로그에 오류가 표시되고 증명 게재는 실패합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> 전자 메일 또는 트랜잭션 전자 메일 템플릿에 최대 첨부 파일 수를 설정할 수 있습니다. 이 값을 초과하면 게재 분석 로그에 또는 트랜잭션 이메일 템플릿을 게시할 때 경고가 표시됩니다. 기본값은 1개의 첨부 파일입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> 분석 중 최대 다시 시도 횟수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> 게시 스크립트.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> 푸시 메시지에 대해 broadLogMsg 수를 사용하지 않도록 설정합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> 게재 마법사에서 메시지 가중치를 표시합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> 사용자가 비어 있는 경우 전자 메일 게재에 사용되는 인스턴스 수준의 기본 'error' 전자 메일 주소입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> 사용자가 비워 둘 경우 인스턴스 수준에서 전자 메일 배달에 사용되는 기본 '보낸 사람' 전자 메일 주소입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> 사용자가 비어 있는 경우 전자 메일 게재에 사용되는 인스턴스 수준의 기본 '회신' 전자 메일 주소입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> 고객의 일반 이름입니다. 수신자에게 표시되는 일부 경고 메시지에 사용됩니다.<br /> "***** 또는 제휴 회사와 연락하여 이 메시지를 받고 있습니다. 더 이상 *****".<br />에서 메시지를 받지 않으려면 </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> 사용자가 비어 있는 경우 전자 메일 게재에 사용되는 인스턴스 수준의 기본 'from' 전자 메일 레이블입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> 사용자가 비어 있는 경우 전자 메일 게재에 사용되는 인스턴스 수준의 기본 '회신' 전자 메일 레이블입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> 전자 메일 메시지의 두 다시 시도 사이의 기간(초).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> 전자 메일 메시지에 대한 다시 시도 기간입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> 임시 배달용 메시지의 가중치를 계산하는 데 사용되는 공식입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> 승인된 전달 이메일 주소 목록(인바운드 메일 처리 모듈에서). 주소는 쉼표로(또는 모두 허용하려면 *)구분해야 합니다. 예: xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> URL(LINE 채널)을 인코딩하기 위해 'lineImage' 서블릿에 사용되는 AES 키.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNAPI_EmailMaxError</span> <br /> </td> 
   <td> 채널 "이메일"(기본값으로 사용)에서:수신자를 격리하기 전에 보내는 동안 SOFT 오류에 대해 허용되는 최대 오류 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNAPI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> 채널 "이메일"(기본값으로 사용)에서:새 SOFT 오류를 고려하기 전에 이전에 참조된 SOFT 오류 이후 최소 체류 기간<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNAPI_MobileMaxError</span> <br /> </td> 
   <td> 채널 "모바일"에서:수신자를 격리하기 전에 보내는 동안 SOFT 오류에 대해 허용되는 최대 오류 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNAPI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> 채널 "모바일"에서:새 SOFT 오류를 고려하기 전에 이전에 참조된 SOFT 오류 이후 최소 체류 기간<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> 동기화 워크플로우를 실행할 때마다 복구된 브로드로그 수를 제한하는 것으로 최대 기간(시간 단위)을 지정할 수 있습니다.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> MidSourcing 세션의 최대 호출 수(기본적으로 3개)로 동시에 실행할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> 게재를 '지연'으로 간주한 후 사용자 지정 지연(분)으로, 기본값은 30분입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>이 옵션은 실행 중인 게재 수를 계산할 때 <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span> 기술 워크플로우에서 사용됩니다.</p>이를 통해 불일치 상태의 게재가 실행 중인 게재 수에서 제외되는 위의 일 수를 정의할 수 있습니다.</p><p>기본적으로 이 값은 "7"으로 설정되어 있습니다. 즉, 7일 이상 오래된 일관되지 않은 게재는 제외됩니다.</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> 보낸 사람 주소의 줄 1입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span> <br /> </td> 
   <td> 보낸 사람 주소의 줄 3입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span> <br /> </td> 
   <td> 보낸 사람 주소의 줄 4입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span> <br /> </td> 
   <td> 보낸 사람 주소의 6행입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span> <br /> </td> 
   <td> 보낸 사람 주소의 줄 7입니다.<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span> <br /> </td> 
   <td> 미러 페이지 서버의 URL(기본적으로 NmsTracking_ServerUrl과 동일해야 함)입니다.<br /> 라우팅 정의에 URL을 지정하지 않은 경우 게재 기본 값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> 보낸 SMS 메시지의 매개 변수:메시지 우선 순위를 나타내기 위해 SMS 게이트웨이로 전송되는 정보입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> SMS 메시지를 보낼 때 다시 시도 횟수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> SMS 메시지의 다시 시도를 수행하는 기간입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> <span class="uicontrol">NmsUserAgent</span> 통계에 대한 마지막 통합 날짜입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> 웹 세그먼트 및 해당 상태를 포함하는 옵션의 이름입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Code128에 대한 특수 문자 지원을 활성화/비활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> 전자 메일 주소의 올바른 문자입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> "0" 값과 함께 이 옵션을 추가하여 게재 XML 코드 버전을 사용하지 않도록 설정합니다(마우스 오른쪽 단추 클릭 / <span class="uicontrol">XML 소스 편집</span> 또는 <span class="uicontrol">CTRL + F4</span> 바로 가기).<br /> </td> 
  </tr>  
 </tbody> 
</table>

<!--<tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC email address for Momentum to send a raw copy of the sent emails. <br /> </td> 
  </tr>
-->

## 리소스 {#resources}

<table> 
 <thead> 
  <tr> 
   <th> 옵션 이름 </th> 
   <th> 설명 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDir</span> <br /> </td> 
   <td> Adobe Campaign 클라이언트 콘솔에서 게시할 리소스 위치입니다. <a href="../../delivery/using/formatting.md#image-referencing">이 섹션</a>을 참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmResourceDirPreview</span> <br /> </td> 
   <td> Adobe Campaign 클라이언트 콘솔에서 미리 볼 리소스 위치입니다. <a href="../../delivery/using/formatting.md#image-referencing">이 섹션</a>을 참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> 업로드 중에 건너뛴 이미지의 URL 마스크 목록입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> 이미지 업로드 구성. 값은 none / tracking / script / list일 수 있습니다(연산자의 선택적 설정으로 재정의할 수 있음). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> 서버의 이미지를 저장할 폴더입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> 로고를 표시할 스페이스입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> 게시물의 루트 폴더입니다.<br /> HTML 및 텍스트 콘텐츠 생성에 대한 자세한 정보는  <a href="../../delivery/using/using-a-content-template.md">이 섹션</a>을 참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> 브라우저에서 게재에 사용된 이미지가 저장되는 서버를 정의할 수 있도록 해줍니다.<br /> 빌드 버전  &lt;&gt;<br /> 빌드 버전 5098보다 큰 경우 게재 공개 URL 또는 XtkFileRes_ <span class="uicontrol">Public_</span> URL 옵션의 URL을 대신 사용합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> 이미지 업로드를 위한 인스턴스 이름을 구성할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> 이미지 업로드를 위한 암호를 구성할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> 이미지 업로드를 위한 미디어 URL을 구성할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> 게재의 온라인 리소스에 대한 기본 유효 기간(초)입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> 공용 리소스 파일의 새 URL입니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 캠페인 및 워크플로우 관리 {#campaign-e-workflow-management}

<table> 
 <thead> 
  <tr> 
   <th> 옵션 이름 </th> 
   <th> 설명 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">CrmMarketingActivityWindow</span> <br /> </td> 
   <td> 마케팅 기록은 이 개월 수에 표시됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> 캠페인의 기본 유효 기간(초)입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> operationMgt 워크플로우에서 시작하여 한 번에 처리할 수 있는 최대 배달/워크플로우/가설/시뮬레이션 작업 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> <a href="../../workflow/using/about-technical-workflows.md">operationMgt</a> 기술 워크플로우 실행을 모니터링할 수 있습니다. 활성화되면(값 "1") 실행 정보가 워크플로우 감사 로그에 기록됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> 예약된 모드의 타깃팅 및 추출 조건에 대한 기간입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> 테이블 통계가 자동으로 다시 계산되는 영향을 받는 레코드 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> 내보낸 보고서의 오른쪽 상단 모서리에 표시되는 로고입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> 일시 중지된 워크플로에 대한 검사 사이에 대기할 일 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> 값으로 "1"을 입력하여 작업 소유자가 게재 검증을 활성화합니다. 이 옵션을 비활성화하려면 "0".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> 워크플로우의 활동 "마케팅 리소스 알림"에서 로드할 추가 JS 라이브러리.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 보안 {#security}

<table> 
 <thead> 
  <tr> 
   <th> 옵션 이름 </th> 
   <th> 설명 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPassword</span> <br /> </td> 
   <td> (설치 호환성 모드:build&gt;6000) 활성화되면(값 "1") 이 옵션을 사용하면 데이터베이스에 저장된 이전 암호를 외부 계정 또는 인스턴스에 연결할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> 이 키는 데이터베이스의 대부분의 암호를 암호화하는 데 사용됩니다. (외부 계정, LDAP 암호..).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> 1을 선택한 경우 이 옵션은 javascript에서 privilegeEscalation을 허용합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> 1을 선택한 경우 이 옵션은 파일 다운로드 중(fileDownload.jsp 사용)에 ACL 컨트롤을 비활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> 1을 선택한 경우 이 옵션은 Javascript 내에서 파일 샌드박스를 비활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> 'true'로 설정하면 관리자가 아닌 연산자가 배포 마법사를 통해 xtkOption 값을 업데이트하도록 승인됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> 1을 선택한 경우 이 옵션을 사용하면 decryptString을 사용하여 일부 암호를 해독할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> 레코드를 삭제하기 전에 "수정한 사람" 필드를 수정하여 mData에서 감사 추적 정보로 요소의 삭제를 추적할 "1" 값을 입력합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 메시지 센터 {#message-center}

<table> 
 <thead> 
  <tr> 
   <th> 옵션 이름 </th> 
   <th> 설명 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">MC_EnforcedCustomJs</span> <br /> </td> 
   <td> 이벤트를 보강하기 위해 개인화된 JavaScript 라이브러리입니다. 다음 두 함수의 구현을 포함해야 합니다.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enifyRtEvents(aiEventId); </span> :데이터베이스의 이벤트를 강화하고 저장합니다(여기서  <span class="uicontrol"></span> aiEventIdid는 처리된 실시간 이벤트 테이블에 해당됨).</p> </li> 
     <li> <p> <span class="uicontrol">aemBatchEvents(aiEventId); </span> :데이터베이스의 이벤트를 강화하고 저장합니다(여기서  <span class="uicontrol"></span> aiEventIdid는 처리된 배치 이벤트의 ID 테이블에 해당됨).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> 게재 로그를 통해 마지막 이벤트 상태를 업데이트하는 날짜입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> 라우팅 이벤트를 위해 개인화할 JavaScript 라이브러리입니다. 다음 두 함수의 구현을 포함해야 합니다.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatchRtEvent(iEventId); </span> :실시간 이벤트를 처리하기 위해 선택한 트랜잭션 메시지의 내부 이름을 반환합니다(여기서  <span class="uicontrol"></span> iEventIdid는 처리된 실시간 이벤트의 ID에 해당합니다).</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId); </span> :일괄 처리 이벤트를 처리하기 위해 선택한 트랜잭션 메시지의 내부 이름을 반환합니다(여기서  <span class="uicontrol"></span> iEventIdid는 처리된 일괄 처리 이벤트의 ID에 해당합니다).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> 실시간 이벤트의 평균 전송 시간에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> 실시간 이벤트의 평균 전송 시간에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> 실시간 이벤트의 평균 처리 시간에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> 실시간 이벤트의 평균 처리 시간에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> 큐에 있는 평균 실시간 이벤트 수에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> 실시간 이벤트의 평균 큐 시간에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> 실시간 이벤트의 평균 큐 시간에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> 큐에 있는 평균 실시간 이벤트 수에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> 실시간 이벤트의 처리 오류를 위한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> 실시간 이벤트의 처리 오류에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> 큐에 있는 최대 실시간 이벤트 수에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> 큐에 있는 최대 실시간 이벤트 수에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> 대기 중인 최소 실시간 이벤트 수에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> 큐에 있는 최소 실시간 이벤트 수에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> 대기 중인 실시간 이벤트 큐에 대한 위기 조건 이전의 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> 대기 중인 실시간 이벤트 큐에 대한 경고 전 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> 실시간 이벤트 처리량에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> 실시간 이벤트 처리량에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> 이벤트 라우팅에 대한 다시 그룹화 크기입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> RtEvent 상태 포인터 업데이트(데이터가 검색될 때까지 마지막 날짜).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> 환영 메시지를 보내는 데 사용되는 메시지 센터 서버 URL(LINE 채널)입니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 데이터베이스 {#database}

<table> 
 <thead> 
  <tr> 
   <th> 옵션 이름 </th> 
   <th> 설명 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_LastCleanup</span> <br /> </td> 
   <td> 정리 프로세스가 마지막으로 실행된 시간을 정의합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>데이터베이스에서 브로드로그가 지워지는 지연을 정의할 수 있습니다.</p><p>이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표시되어야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> 데이터베이스에서 이벤트 기록이 지워지는 지연을 정의할 수 있습니다.</p><p>
   이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표시되어야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> 데이터베이스에서 이벤트가 지워진 후 지연을 정의할 수 있습니다.</p><p>이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표시되어야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> 데이터베이스에서 이벤트 통계가 지워지는 지연을 정의할 수 있습니다.</p><p>이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표시되어야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_ProvisionPurgeDelay</span> <br /> </td> 
   <td><p> 데이터베이스에서 proposition을 지운 후 지연을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표시되어야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>격리를 데이터베이스에서 지운 후 지연을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표시되어야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RepeedDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>데이터베이스에서 재생 게재가 지워지는 지연을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표시되어야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>데이터베이스에서 거부가 지워진 후 지연을 정의할 수 있습니다.</p><p>이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표시되어야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>추적 로그가 데이터베이스에서 지워지는 지연을 정의할 수 있습니다.</p><p>이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표시되어야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> 추적 통계가 데이터베이스에서 지워지는 시간을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표시되어야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>방문자가 데이터베이스에서 지워지는 지연을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표시되어야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>데이터베이스에서 워크플로우 결과가 지워지는 지연을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표시되어야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Azure SQL Datawarehouse 커넥터 옵션.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>다음 잠재적 값에 따라 모든 워크플로우 및 PostgreSQL 데이터베이스 쿼리의 무조건적 정지 동작에 영향을 줄 수 있습니다.<ul>
    <li><p>0 - 기본값:워크플로 프로세스를 중지하며 데이터베이스에 영향을 주지 않습니다.<p></li>
    <li><p>1 - pg_cancel_backend:워크플로 프로세스를 중지하고 데이터베이스의 쿼리를 취소합니다<p></li>
    <li><p>2 - pg_terminate_end:워크플로 프로세스를 중지하고 데이터베이스에서 쿼리를 종료합니다.<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Adobe Campaign ootb 테이블의 데이터를 포함할 테이블스페이스의 이름입니다.<br />데이터베이스  <a href="../../installation/using/creating-and-configuring-the-database.md">만들기 및 구성</a>을 참조하십시오.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Adobe Campaign ootb 테이블의 인덱스를 포함하려는 테이블스페이스의 이름입니다.<br />데이터베이스  <a href="../../installation/using/creating-and-configuring-the-database.md">만들기 및 구성</a>을 참조하십시오.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Adobe Campaign 작업 테이블의 데이터를 포함할 테이블스페이스의 이름입니다.<br />데이터베이스  <a href="../../installation/using/creating-and-configuring-the-database.md">만들기 및 구성</a>을 참조하십시오.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Adobe Campaign 작업 테이블의 인덱스를 포함할 테이블스페이스의 이름입니다.<br />데이터베이스  <a href="../../installation/using/creating-and-configuring-the-database.md">만들기 및 구성</a>을 참조하십시오.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> 백업 및 복제를 최적화하기 위해 Microsoft SQL Server에서 작업 테이블에 대해 별도의 데이터베이스를 구성할 수 있습니다. 옵션은 임시 데이터베이스의 이름에 해당합니다.지정한 경우 작업 테이블이 이 데이터베이스에 작성됩니다. 예:'tempdb.dbo' (이름은 점으로 끝나야 합니다.) <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">자세히 알아보기</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Adobe Campaign 인스턴스의 시간대입니다. <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">구성</a>.<br /> 참조 </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> 데이터베이스의 문자열 필드가 NChar로 정의됩니까?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> 데이터베이스의 'datetime' 필드에 시간대 정보가 저장됩니까?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> 데이터베이스의 ID입니다. 유니코드 DataBase에 대해 'u'로 시작합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> 자동으로 생성된 내부 이름에 접두사가 추가되었습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> xtk:schema 및 xtk:srcSchema.<br />에 대한 쿼리에서 반환되는 최대 결과 수 </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> 이 시간 이후에 자동 k="true"를 사용하고 "pkSequence" 속성이 없는 모든 사용자 지정된 스키마는 자동으로 생성된 시퀀스 "auto_"를 가져옵니다 
    &lt;schemanamespace&gt; 
     &lt;스키마 이름&gt;
       _seq 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> 마이그레이션 중에 트리 구조가 새 버전 표준에 따라 자동으로 재구성됩니다.<br /> 이 옵션을 사용하면 탐색 트리의 자동 마이그레이션을 비활성화할 수 있습니다. 이 기능을 사용하는 경우 마이그레이션 후 오래된 폴더를 삭제해야 하며 새 폴더를 추가하고 필요한 모든 검사를 실행해야 합니다.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">데이터 유형: </span> 정수</p> </li> 
     <li> <p> <span class="uicontrol">값(텍스트)</span> :3 </p> </li> 
    </ul> 이 옵션은 기본 제공 탐색 트리가 너무 많은 변경 사항을 거친 경우에만 사용해야 합니다.<br /> 이 작업에 대한 자세한 정보는 <a href="../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure">이 섹션</a>을 참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> <span class="uicontrol">NmsEmailErrorStat</span> 테이블 정리를 위한 마지막 처리 날짜입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> 아래 구문 다음에 따라 업그레이드 후 발생한 오류에 대한 정보가 표시됩니다.<br /> <strong>{Build number}:{mode:pre/post/..}:{오류가 발생한 'lessThan'/'greaterOrEquelThan' + sub-step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> 정리 워크플로우를 통해 통계 업데이트가 수행되지 않도록 "1" 값을 입력합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 통합 {#integration}

<table> 
 <thead> 
  <tr> 
   <th> 옵션 이름 </th> 
   <th> 설명 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">AEMRessourceTypeFilter</span> <br /> </td> 
   <td> Adobe Campaign에서 사용할 수 있는 AEM 리소스 유형입니다. 값은 쉼표로 구분해야 합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> Experience Cloud 트리거를 구성할 수 있습니다. 데이터 유형은 "long text"이며 JSON 형식이어야 합니다. <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Adobe Campaign Classic</a>에서 Experience Cloud 트리거를 사용하는 방법<br />을 참조하십시오. </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;&gt;_&lt;&gt;</span> <br /> </td> 
   <td> 이 옵션은 CRM 커넥터를 통해 서드파티 시스템에서 데이터를 가져올 때 사용됩니다. 옵션을 활성화하면 마지막 가져오기 이후 수정된 객체만 수집할 수 있습니다. 이 옵션은 다음과 같이 수동으로 만들고 채워야 합니다. 
    <ul> 
     <li> <p> <span class="uicontrol">내부 이름</span> :LASTIMPORT_&lt;&gt;_&lt;&gt;</p> </li> 
     <li> <p> <span class="uicontrol">값(필드)</span> :yyyy/MM/dd hh:mm:ss 형식을 사용하는 마지막 가져오기의 날짜입니다. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> 통합에 사용되는 Adobe Target 서버입니다. 이 옵션은 기본적으로 이미 선택되어 있습니다. 이 값은 Adobe Target 도메인 서버에 해당하며 다음에 /m2 값이 옵니다. 예:tt.omtrdc.net/m2<br /><a href="../../integrations/using/configuring-the-integration-with-adobe-target.md"> 이 섹션</a>을 참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Adobe Target 조직 이름. 이 값은 Adobe Target 클라이언트의 이름에 해당합니다.<br /><a href="../../integrations/using/configuring-the-integration-with-adobe-target.md"> 이 섹션</a>을 참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span> <br /> </td> 
   <td> Adobe Audience Manager과의 통합에 사용되는 옵션입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span> <br /> </td> 
   <td> Adobe Audience Manager과의 통합에 사용되는 옵션입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> Teradata 커넥터 옵션<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
   <td> 하이브 커넥터 옵션.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 오퍼 {#offers}

<table> 
 <thead> 
  <tr> 
   <th> 옵션 이름 </th> 
   <th> 설명 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCoupons_MaxPerTransac</span> <br /> </td> 
   <td> SQL 트랜잭션당 업데이트된 쿠폰 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastProvisionSynchControl_</span> <br /> </td> 
   <td> '+ [제안 스키마] + "_" + extAccountSource.@executionInstanceId + [제안 스키마] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastProvisionSynchExec_</span> <br /> </td> 
   <td> '+ [ 제안 스키마] + "_" + extAccountSource.@executionInstanceId + "_" + extAccountTarget.@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> 동기화 워크플로우 추적.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> 비동기 제안 쓰기 사용/사용 안 함("0"은 사용 안 함, "1"은 사용 안 함).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
   <td> 쿠폰 사용<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 서버 {#server}

<table> 
 <thead> 
  <tr> 
   <th> 옵션 이름 </th> 
   <th> 설명 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsExecutionInstanceId</span> <br /> </td> 
   <td> 실행 인스턴스 식별자입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> 청구 보고서를 보낼 때 사용되는 고객 식별자입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> 응용 프로그램 서버에 액세스할 내부 기본 URL입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> 마지막 업그레이드 전 AC 인스턴스의 빌드 번호입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> 공용 웹 응용 프로그램 서버의 기본 URL입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFfunctionsToRDBMS</span> <br /> </td> 
   <td> 마이그레이션 후 선언되지 않은 이전 SQL 함수를 계속 사용할 수 있습니다. 보안 위험으로 인해 이 옵션을 사용하지 않는 것이 좋습니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 추적 {#tracking}

<table> 
 <thead> 
  <tr> 
   <th> 옵션 이름 </th> 
   <th> 설명 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Available</span> <br /> </td> 
   <td> 추적을 활성화할 수 있는 옵션입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span> <br /> </td> 
   <td> 추적된-URL 계산 스크립트입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> 추적 서버의 외부 계정을 정의할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> 추적 서버에서 인스턴스 이름을 정의할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> 마지막으로 추적 정보가 새 데이터로 통합되었습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> URL 계산 스크립트를 엽니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> 추적 서버의 암호<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> 포인터가 ID 및 날짜를 통해 처리된 마지막 메시지 이벤트를 추적합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> 전두추적 서버의 보안 URL입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> 전두추적 서버의 URL입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> 추적 서버에 연결하는 데 사용되는 URL 목록입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> 브라우저 식별 규칙 집합입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> 웹 추적 태그를 계산하는 데 사용되는 스크립트입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> 웹 추적 관리를 위해 설계된 가상 배달의 이름입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> 웹 추적 모드를 정의할 수 있습니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 개인 정보 {#privacy}

<table> 
 <thead> 
  <tr> 
   <th> 옵션 이름 </th> 
   <th> 설명 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePending</span> <br /> </td> 
   <td> 옵션 1 을 선택한 경우 두 번째 단계에서 인터페이스에서 삭제를 수동으로 확인해야 합니다. 그렇지 않으면 데이터가 확인 없이 삭제됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> 요청 간의 지연이 확인을 삭제할 때까지 기다리며 요청이 취소되었습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> 개인 정보 요청을 처리/삭제할 때 허용되는 최대 오류 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> 요청 간의 지연이 큐에 만들어지고 요청 데이터가 삭제됩니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## LDAP {#ldap}

<table> 
 <thead> 
  <tr> 
   <th> 옵션 이름 </th> 
   <th> 설명 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Active</span> <br /> </td> 
   <td> 사용자를 인증하고 사용자에게 권한을 제공하는 데 사용할 LDAP 서버를 사용하도록 설정합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> 응용 프로그램 로그인하여 서버에 문의하여 다양한 검색을 확인하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> 응용 프로그램 로그인에 대해 암호화된 암호입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> Adobe Campaign에서 연산자 및 권한을 자동으로 만들 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> 로그인 기반 LDAP DN에 대한 계산 공식입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> 디렉터리에서 DN 검색을 사용하도록 설정합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span> <br /> </td> 
   <td> 기본 검색.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchFilter</span> <br /> </td> 
   <td> DN 검색 필터입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchScope</span> <br /> </td> 
   <td> 검색 범위입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Mechanism</span> <br /> </td> 
   <td> LDAP 서버에 연결하는 데 사용되는 인증 유형(일반, md5, lds, ntlm, dpa)입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span> <br /> </td> 
   <td> LDAP 디렉토리에서 권한 및 그룹을 Adobe Campaign의 명명된 권한에 동기화할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> 인증 이름이 포함된 LDAP 속성입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> 기본 검색.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> 사용자 권한을 검색합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> LDAP 권한에서 Adobe Campaign 권한 이름을 추출하는 식입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span> <br /> </td> 
   <td> 검색 범위입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Server</span> <br /> </td> 
   <td> LDAP 서버 주소(구분 기호로 ':'을 지정하여 포트를 지정할 수 있음).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 웹 양식 {#web-forms}

<table> 
 <thead> 
  <tr> 
   <th> 옵션 이름 </th> 
   <th> 설명 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkUseScrollBar</span> <br /> </td> 
   <td> 값을 1로 설정하면 스크롤 막대가 세부 양식에 추가할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> '기타 서버' 모드에서 웹 양식 무효화에 사용할 인스턴스입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> '기타 서버' 모드에서 웹 양식 무효화에 사용할 인스턴스의 암호입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> 웹 양식의 무효화 모드를 지정할 수 있는 옵션입니다.기본적으로 로컬에서는 옵션이 'tracking'이면 추적 서버를 사용하고 'other server(s)' 옵션이 있는 개인화된 목록을 사용합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURL</span> <br /> </td> 
   <td> 웹 양식 무효화를 위해 연결할 서버의 개인화된 주소 목록입니다('기타 서버' 모드).<br /> </td> 
  </tr> 
 </tbody> 
</table>
