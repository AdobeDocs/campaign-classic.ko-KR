---
product: campaign
title: 캠페인 옵션 구성
description: Campaign 옵션 구성 방법 알아보기
feature: Installation, Application Settings
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '4012'
ht-degree: 6%

---

# Campaign Classic 옵션 목록{#configuring-campaign-options}

다음 **[!UICONTROL Administration / Platform / Options]** 노드를 사용하면 Adobe Campaign 옵션을 구성할 수 있습니다. 일부는 Campaign 설치 시 기본 제공되며, 일부는 필요한 경우 수동으로 추가할 수 있습니다. 사용 가능한 옵션은 인스턴스와 함께 설치된 패키지에 따라 다릅니다.


>[!CAUTION]
>
>* 이 페이지에 나열되지 않은 옵션은 내부용이며 **은(는) 수정할 수 없습니다.**.
>
>* Adobe Campaign 옵션 수정 또는 업데이트는 전문가 사용자만 수행할 수 있습니다.

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
   <td> 게재 가능성 인스턴스로 전송된 마지막 broadLogMsg의 날짜.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> 게재 보고서 식별자. 식별자를 얻으려면 지원 센터에 문의하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> 받은 편지함 렌더링에 테스트 주소를 사용할 스키마 목록입니다. (요소 이름은 쉼표로 구분됨) 예: custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> Enhanced MTA가 보낸 이메일의 원시 사본을 보낼 BCC 이메일 주소입니다. <br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> 게재 속성에서 게재를 시작하도록 특정 연산자 또는 연산자 그룹이 지정된 경우 게재를 담당하는 운영자가 전송을 확인하도록 할 수 있습니다.</p><p> 이렇게 하려면 "1"을 값으로 입력하여 옵션을 활성화합니다. 이 옵션을 비활성화하려면 "0"을 입력합니다.</p><p> 그러면 전송 확인 프로세스가 기본값으로 작동합니다. 게재 속성에서 전송을 위해 지정된 운영자 또는 운영자 그룹(또는 관리자)만 전송을 확인하고 수행할 수 있습니다. <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">이 섹션</a>을 참조하십시오.</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign은 "Nms_DefaultRcpSchema" 전역 변수를 사용하여 기본 수신자 데이터베이스(nms:recipient)와 대화를 나눕니다.<br /> 옵션 값은 외부 수신자 테이블과 일치하는 스키마 이름과 일치해야 합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> 게재를 청구 보고서의 기본 게재로 간주하기 위한 최소 수신자 수.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> 새 템플릿에 대한 기본 라우팅 서비스 공급자입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> 게재를 준비하는 동안 broadLogs 삽입을 위한 최소 배치 크기(행 수)입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> broadLogs 삽입을 위한 배치 크기가 게재 준비 중 두 배가 되는 배치 기간 임계값(밀리초 수)입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> 중간 소싱 게재 분석 시 게재 부분 그룹화.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> 게재에 대한 기본 게재 기간(초).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> 게재 메시지 표준화를 위한 정규 표현식.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> 값으로 "1"을 입력하면 더 이상 연락을 하지 않으려는 수신자를 제외할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> 값으로 "1"을 입력하면 double을 자동으로 무시할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span> <br /> </td> 
   <td> 메시지에 회신할 때 사용되는 오류 주소의 구문을 정의할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span> <br /> </td> 
   <td> 메시지를 보낼 때 사용되는 보낸 사람 주소의 구문을 정의할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> 개인화된 URL에서 다운로드하고 이메일에 첨부된 이미지를 검색할 때 서버에서 응답을 가져오는 데 필요한 시간 제한(초)을 정의할 수 있습니다. 이 값을 초과하면 메시지를 보낼 수 없습니다. 기본값은 60초입니다.<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> 개인화된 URL에서 다운로드되고 이메일에 첨부된 이미지에 허용되는 최대 크기(바이트)를 정의할 수 있습니다. 기본값은 100,000바이트(100KB)입니다. 증명을 보내고 이메일을 처리하기 위해 이미지를 다운로드할 때 이미지 크기가 이 값을 초과하거나 다운로드 문제가 있는 경우 게재 로그에 오류가 표시되고 증명 전달이 실패합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> 전자 메일 또는 트랜잭션 전자 메일 템플릿의 최대 첨부 파일 수를 설정할 수 있습니다. 이 값을 초과하면 게재 분석 로그 또는 트랜잭션 이메일 템플릿을 게시할 때 경고가 표시됩니다. 기본값은 첨부 파일 1개입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> 분석 시 최대 재시도 수.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> 게시 스크립트.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> 푸시 메시지에 대한 broadLogMsg 수를 비활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> 게재 마법사에서 메시지 가중치를 표시합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> 사용자가 비워 두면 이메일 게재에 사용되는 인스턴스 수준의 기본 '오류' 이메일 주소입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> 사용자가 비워 두면 이메일 게재에 사용되는 인스턴스 수준의 기본 '보낸 사람' 이메일 주소입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> 사용자가 이메일 게재를 위해 비워 둔 경우 인스턴스 수준에서 사용되는 기본 '회신' 이메일 주소입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> 고객의 일반 이름. 수신자에게 표시되는 일부 경고 메시지에 사용됩니다.<br /> "귀하가 '조직' 또는 제휴 회사에 연락하여 이 메시지를 받았습니다. 더 이상 '조직'에서 메시지를 받지 않음<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> 사용자가 비워 둔 경우 이메일 게재에 사용되는 인스턴스 수준의 기본 '보낸 사람' 이메일 레이블입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> 사용자가 비워 둔 경우 이메일 게재에 사용되는 인스턴스 수준의 기본 '회신' 이메일 레이블입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> 이메일 메시지 두 번 다시 시도 사이의 기간(초).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> 이메일 메시지 재시도 기간.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> 임시 게재에 대한 메시지 가중치를 계산하는 데 사용되는 공식입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> 승인된 전달 이메일 주소 목록(인바운드 메일 처리 모듈에서). 주소는 쉼표로 구분해야 합니다(모두 허용하려면 *). 예: xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> URL(LINE 채널)을 인코딩하기 위해 'lineImage' 서블릿에 사용되는 AES 키입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> 채널 "이메일"(기본값으로 사용) : 수신자를 격리하기 전에 보내는 동안 발생하는 SOFT 오류에 대해 허용되는 최대 오류 수.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> 채널 "이메일"(기본값으로 사용) : 새로운 SOFT 오류를 고려하기 전에 이전에 참조된 SOFT 오류 이후 소요된 최소 기간입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> 채널 "모바일"에서 : 수신자를 격리하기 전에 전송하는 동안 발생한 SOFT 오류에 대해 허용되는 최대 오류 수.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> 채널 "모바일"에서 : 새로운 SOFT 오류를 고려하기 전에 이전에 참조된 SOFT 오류 이후 소요된 최소 기간.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> 동기화 워크플로우를 실행할 때마다 복구되는 브로드로그 수를 제한하도록 최대 기간(시간 단위로 표시)을 지정할 수 있습니다.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> MidSourcing 세션의 최대 호출 수로, 동시에 실행할 수 있습니다(기본적으로 3개).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> 사용자 지정 지연(분). 이후 게재는 '지연됨'으로 간주되며 기본값은 30분입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>이 옵션은 <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationManager</a></span> 실행 중인 게재 수를 계산할 때의 기술 워크플로우입니다.</p>상태가 일관되지 않은 게재가 실행 중인 게재 수에서 제외되는 일 수를 정의할 수 있습니다.</p><p>기본적으로 값은 "7"로 설정되어 있습니다. 즉, 7일이 지난 일관되지 않은 게재는 제외됩니다.</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> 보낸 사람 주소의 1행입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span> <br /> </td> 
   <td> 발신자 주소 3행입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span> <br /> </td> 
   <td> 발신자 주소 4행입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span> <br /> </td> 
   <td> 발신자 주소 6행입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span> <br /> </td> 
   <td> 발신자 주소 7행입니다.<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span> <br /> </td> 
   <td> 미러 페이지 서버의 URL(기본적으로 NmsTracking_ServerUrl과 동일해야 함).<br /> 라우팅 정의에 URL이 지정되지 않은 경우 이메일 게재의 기본값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> 보낸 SMS 메시지의 매개 변수: 메시지 우선 순위를 표시하기 위해 SMS 게이트웨이에 전송된 정보.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> SMS 메시지 전송 시 다시 시도 횟수.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> SMS 메시지 재시도가 수행되는 기간.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> 에 대한 마지막 통합 일자 <span class="uicontrol">NmsUserAgent</span> 통계입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> 웹 세그먼트 및 해당 상태가 포함된 옵션의 이름.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Code128의 특수 문자에 대한 지원을 활성화/비활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> 이메일 주소에 유효한 문자입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> 게재의 XML 코드 편집을 비활성화하려면 이 옵션을 "0" 값과 함께 추가합니다(마우스 오른쪽 단추 클릭 / <span class="uicontrol">XML 소스 편집</span> 또는 <span class="uicontrol">CTRL + F4</span> 바로 가기).<br /> </td> 
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
   <td> <span class="uicontrol">NcmResourcesDir</span> <br /> </td> 
   <td> Adobe Campaign 클라이언트 콘솔에 게시할 리소스 위치입니다. <a href="../../delivery/using/formatting.md#image-referencing">이 섹션</a>을 참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmResourcesDirPreview</span> <br /> </td> 
   <td> Adobe Campaign 클라이언트 콘솔에서 미리 볼 수 있는 리소스의 위치입니다. <a href="../../delivery/using/formatting.md#image-referencing">이 섹션</a>을 참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> 업로드 도중 건너뛴 이미지의 URL 마스크 목록.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> 업로드 중인 이미지 구성. 값은 none / tracking / script / list 가 될 수 있습니다 (연산자의 선택 설정에 의해 재정의될 수 있음). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> 서버의 이미지가 저장될 폴더.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> 로고를 표시할 공간입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> 발행물의 루트 폴더입니다.<br /> HTML 및 텍스트 컨텐츠 생성에 대한 자세한 내용은 <a href="../../delivery/using/using-a-content-template.md">이 섹션</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> 게재에서 사용되는 이미지가 저장되는 서버를 정의하여 브라우저가 해당 이미지를 가져올 수 있도록 할 수 있습니다.<br /> 빌드 버전 &lt;= 5098의 경우 인스턴스에 업로드된 이미지의 URL을 사용합니다.<br /> 빌드 버전 &gt; 5098의 경우 대신 게재의 공개 URL 또는 을 사용합니다. <span class="uicontrol">XtkFileRes_Public_URL</span> 옵션 URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> 이미지 업로드를 위한 인스턴스 이름을 구성할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> 이미지 업로드에 대한 암호를 구성할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> 이미지를 업로드하도록 미디어 URL을 구성할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> 게재의 온라인 리소스에 대한 기본 유효 기간(초)입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> 공개 리소스 파일의 새 URL.<br /> </td> 
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
   <td> 이 개월 수에 대해 마케팅 기록이 표시됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> 캠페인의 기본 유효 기간(초)입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> operationMgt 워크플로에서 시작하여 한 번에 처리할 수 있는 게재/워크플로/가설/시뮬레이션 작업의 최대 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> 다음을 모니터링할 수 있습니다. <a href="../../workflow/using/about-technical-workflows.md">operationManager</a> 기술 워크플로우 실행. 활성화되면(값 "1") 실행 정보가 워크플로우 감사 로그에 기록됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> 예약 모드에서 타겟팅 및 추출 조건에 대한 기간.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> 테이블 통계가 자동으로 다시 계산되는 영향을 받는 레코드 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> 내보낸 보고서의 오른쪽 위 모서리에 표시될 로고입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> 일시 중지된 워크플로 확인 사이의 대기 일수.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> 값으로 "1"을 입력하여 작업 소유자별 게재 유효성 검사를 활성화합니다. 이 옵션을 비활성화하려면 "0"을 입력합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> 워크플로우의 활동 "마케팅 리소스 알림"에 로드할 추가 JS 라이브러리입니다.<br /> </td> 
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
   <td> <span class="uicontrol">RestrictEditingOOTBSschema</span> <br /> </td> 
   <td> (21.1.3 릴리스부터) 1을 선택하면(기본값) 이 옵션은 빌트인 스키마 편집을 비활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOOTBJavascript</span> <br /> </td> 
   <td> (21.1.3 릴리스부터) 1을 선택하면(기본값) 이 옵션은 빌트인 JavaScript 코드 에디션을 비활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPassword</span> <br /> </td> 
   <td> (설치 호환성 모드: build&gt;6000) 활성화되면 (값 "1") 이 옵션을 사용하면 데이터베이스에 저장된 이전 암호를 사용하여 외부 계정 또는 인스턴스에 연결할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> 이 키는 데이터베이스에서 대부분의 암호를 암호화하는 데 사용됩니다. (외부 계정, LDAP 암호...)<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> 1을 선택한 경우 이 옵션은 JavaScript에서 privilegeEscalation을 허용합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> 1을 선택한 경우 이 옵션은 파일 다운로드 중(fileDownload.jsp를 통해) ACL 컨트롤을 비활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> 1을 선택하면 이 옵션은 Javascript 내에서 파일 sandboxing을 비활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> 'true'로 설정하면 관리자가 아닌 운영자가 배포 마법사를 통해 xtkOption 값을 업데이트할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> 1을 선택한 경우 이 옵션을 사용하면 decryptString을 사용하여 일부 암호를 해독할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> 레코드를 삭제하기 전에 "수정자" 필드를 수정하여 mData에 감사 추적 정보가 있는 요소의 삭제를 추적하려면 "1" 값을 입력합니다.<br /> </td> 
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
   <td> <span class="uicontrol">MC_EnrichmentCustomJs</span> <br /> </td> 
   <td> 이벤트 강화를 위해 개인화할 JavaScript 라이브러리. 에는 다음 두 함수의 구현이 포함되어야 합니다.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : 데이터베이스의 이벤트를 풍부하게 만들고 저장합니다(여기서 <span class="uicontrol">aiEventId</span> 은 처리된 실시간 이벤트 테이블에 해당합니다.</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : 데이터베이스의 이벤트를 풍부하게 만들고 저장합니다(여기서 <span class="uicontrol">aiEventId</span> 는 처리된 일괄 처리 이벤트의 ID 테이블에 해당합니다.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> 게재 로그를 통한 마지막 이벤트 상태 업데이트 날짜.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> 라우팅 이벤트에 대해 개인화할 JavaScript 라이브러리입니다. 에는 다음 두 함수의 구현이 포함되어야 합니다.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatchRtEvent(iEventId);</span> : 실시간 이벤트를 처리하기 위해 선택한 트랜잭션 메시지의 내부 이름을 반환합니다(여기서 <span class="uicontrol">iEventId</span> 은 처리된 실시간 이벤트의 ID에 해당합니다.</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId);</span> : 일괄 처리 이벤트를 처리하기 위해 선택한 트랜잭션 메시지의 내부 이름을 반환합니다(여기서 <span class="uicontrol">iEventId</span> 은 처리된 일괄 처리 이벤트의 ID에 해당합니다.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> 실시간 이벤트의 평균 전송 시간에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> 실시간 이벤트의 평균 전송 시간에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> 실시간 이벤트의 평균 처리 시간에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> 실시간 이벤트의 평균 처리 시간에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> 대기열에 추가된 평균 실시간 이벤트 수에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> 실시간 이벤트의 평균 대기 시간에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> 실시간 이벤트의 평균 대기 시간에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> 대기열에 추가된 평균 실시간 이벤트 수에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> 실시간 이벤트의 처리 오류에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> 실시간 이벤트의 처리 오류에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> 대기열에 추가된 최대 실시간 이벤트 수에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> 대기열에 추가된 최대 실시간 이벤트 수에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> 대기열에 추가된 최소 실시간 이벤트 수에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> 대기열에 추가된 최소 실시간 이벤트 수에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> 보류 중인 실시간 이벤트 대기열의 중요 상태 전 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> 보류 중인 실시간 이벤트 대기열의 경고 전 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> 실시간 이벤트 처리량에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> 실시간 이벤트 처리량에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> 이벤트 라우팅에 대한 다시 그룹화 크기입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> RtEvent 상태의 포인터를 업데이트합니다(데이터를 검색할 때까지의 마지막 날짜).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> 환영 메시지(LINE 채널)를 보내는 데 사용되는 메시지 센터 서버 URL.<br /> </td> 
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
   <td> <p>브로드로그가 데이터베이스에서 지워지는 지연 시간을 정의할 수 있습니다.</p><p>이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> 이벤트 기록이 데이터베이스에서 지워지는 지연 시간을 정의할 수 있습니다.</p><p>
   이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> 데이터베이스에서 이벤트가 지워지는 지연 시간을 정의할 수 있습니다.</p><p>이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> 이벤트 통계가 데이터베이스에서 지워지는 지연 시간을 정의할 수 있습니다.</p><p>이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> 데이터베이스에서 제안이 지워지는 지연 시간을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>격리가 데이터베이스에서 지워지는 지연 시간을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycedDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>데이터베이스에서 재활용된 게재가 지워지는 지연 시간을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectPurgeDelay</span> <br /> </td> 
   <td> <p>거부가 데이터베이스에서 지워지는 지연 시간을 정의할 수 있습니다.</p><p>이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>추적 로그가 데이터베이스에서 지워지는 지연 시간을 정의할 수 있습니다.</p><p>이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> 추적 통계가 데이터베이스에서 지워지는 지연 시간을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>데이터베이스에서 방문자가 지워지는 지연 시간을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>데이터베이스에서 워크플로우 결과가 지워지는 지연 시간을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 만들어집니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Azure SQL Datawarehouse 커넥터 옵션.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>다음과 같은 잠재적 값에 따라 모든 워크플로우 및 PostgreSQL 데이터베이스 쿼리의 무조건적 정지 동작에 영향을 줄 수 있습니다.<ul>
    <li><p>0 - 기본값: 워크플로우 프로세스를 중지하며 데이터베이스에 영향을 주지 않음<p></li>
    <li><p>1 - pg_cancel_backend: 워크플로 프로세스를 중단하고 데이터베이스의 쿼리를 취소합니다.<p></li>
    <li><p>2 - pg_terminate_backend: 워크플로우 프로세스를 중지하고 데이터베이스의 쿼리를 종료합니다.<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Adobe Campaign ootb 테이블의 데이터를 포함하기 위한 테이블스페이스의 이름입니다.<br />다음을 참조하십시오 <a href="../../installation/using/creating-and-configuring-the-database.md">데이터베이스 만들기 및 구성</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Adobe Campaign ootb 테이블의 인덱스를 포함할 테이블스페이스의 이름입니다.<br />다음을 참조하십시오 <a href="../../installation/using/creating-and-configuring-the-database.md">데이터베이스 만들기 및 구성</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Adobe Campaign 작업 테이블의 데이터를 포함하려는 테이블스페이스의 이름입니다.<br />다음을 참조하십시오 <a href="../../installation/using/creating-and-configuring-the-database.md">데이터베이스 만들기 및 구성</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Adobe Campaign 작업 테이블의 인덱스를 포함할 테이블스페이스의 이름입니다.<br />다음을 참조하십시오 <a href="../../installation/using/creating-and-configuring-the-database.md">데이터베이스 만들기 및 구성</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> 백업 및 복제를 최적화하기 위해 Microsoft SQL Server의 작업 테이블에 대해 별도의 데이터베이스를 구성할 수 있습니다. 이 옵션은 임시 데이터베이스의 이름에 해당합니다. 작업 테이블을 지정하면 이 데이터베이스에 작성됩니다. 예: 'tempdb.dbo.' (이름은 점으로 끝나야 합니다.) <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">자세히 보기</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Adobe Campaign 인스턴스의 시간대 다음을 참조하십시오 <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">구성</a>.<br /> </td> 
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
   <td> 데이터베이스의 ID입니다. 유니코드 DataBase의 경우 'u'로 시작합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> 자동으로 생성된 내부 이름에 추가된 접두사.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> xtk:schema 및 xtk:srcSchema에서 쿼리가 반환한 최대 결과 수<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> 이 시간 이후에 생성된, autopk="true"이고 "pkSequence" 특성이 없는 모든 사용자 지정된 스키마는 자동 생성된 시퀀스 "auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemaname&gt;
       시퀀스(_s) 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> 마이그레이션 중에 트리 구조는 새 버전 표준을 기반으로 자동으로 재구성됩니다.<br /> 이 옵션을 사용하면 탐색 트리의 자동 마이그레이션을 비활성화할 수 있습니다. 이를 사용하는 경우 마이그레이션 후 오래된 폴더를 삭제하고 새 폴더를 추가하고 필요한 모든 검사를 실행해야 합니다.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">데이터 유형:</span> 정수</p> </li> 
     <li> <p> <span class="uicontrol">값(텍스트)</span> : 1 </p> </li> 
    </ul> 기본 제공 탐색 트리가 너무 많이 변경된 경우에만 이 옵션을 사용해야 합니다.<br /> 이 작업에 대한 자세한 정보는 <a href="../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11">이 섹션</a>을 참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> 의 마지막 처리 날짜 <span class="uicontrol">NmsEmailErrorStat</span> 테이블 정리.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">업그레이드 후 오류</span> <br /> </td> 
   <td> 아래 구문에 따라 업그레이드 후 발생한 오류에 대한 정보입니다.<br /> <strong>{Build number}:{mode: pre/post/...}:{오류가 발생한 'lessThan'/'greaterOrEquelThan' 위치 + 하위 단계}</strong> </td> 
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
   <td> <span class="uicontrol">AEMResourceTypeFilter</span> <br /> </td> 
   <td> Adobe Campaign에서 사용할 수 있는 AEM 리소스 유형입니다. 값은 쉼표로 구분해야 합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> Experience Cloud 트리거를 구성할 수 있습니다. 데이터 유형은 "긴 텍스트"이며 JSON 형식이어야 합니다. 다음을 참조하십시오 <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Adobe Campaign Classic에서 Experience Cloud 트리거 를 사용하는 방법</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> 이 옵션은 CRM 커넥터를 통해 서드파티 시스템에서 데이터를 가져올 때 사용됩니다. 옵션을 활성화하면 마지막 가져오기 이후 수정된 개체만 수집할 수 있습니다. 이 옵션은 아래와 같이 수동으로 만들고 채워야 합니다. 
    <ul> 
     <li> <p> <span class="uicontrol">내부 이름</span> : LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">값(필드)</span> : 마지막 가져오기 날짜(yyyy/MM/dd hh 포함):mm:ss 형식입니다. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> 통합에 사용되는 Adobe Target 서버입니다. 이 옵션은 기본적으로 이미 선택되어 있습니다. 이 값은 Adobe Target 도메인 서버 다음에 /m2 값이 옵니다. 예: tt.omtrdc.net/m2.<br /><a href="../../integrations/using/configuring-the-integration-with-adobe-target.md"> 이 섹션</a>을 참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Adobe Target 조직 이름. 이 값은 Adobe Target 클라이언트의 이름에 해당합니다.<br /><a href="../../integrations/using/configuring-the-integration-with-adobe-target.md"> 이 섹션</a>을 참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span> <br /> </td> 
   <td> Adobe Audience Manager 통합에 사용되는 옵션입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span> <br /> </td> 
   <td> Adobe Audience Manager 통합에 사용되는 옵션입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> Teradata 커넥터 옵션.<br /> </td> 
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
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchControl_</span> <br /> </td> 
   <td> '+ [proposition의 스키마] + "_" + extAccountSource.@executionInstanceId + [명제의 스키마] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> '+ [ 제안 스키마] + "_" + extAccountSource.@executionInstanceId + "_" + extAccountTarget.@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> 동기화 워크플로우 추적입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> 비동기 제안 쓰기를 활성화/비활성화합니다("0"은 비활성화하고, "1"은 활성화하십시오).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
   <td> 쿠폰을 활성화할 수 있습니다.<br /> </td> 
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
   <td> 실행 인스턴스 식별자.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> 과금 보고서 전송 시 사용되는 고객 식별자.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> 애플리케이션 서버에 액세스하기 위한 내부 기본 URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> 마지막 업그레이드 전 AC 인스턴스의 빌드 번호입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> 공개 웹 애플리케이션 서버의 기본 URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunactionsToRDBMS</span> <br /> </td> 
   <td> 마이그레이션 후 선언되지 않은 이전 SQL 함수를 계속 사용할 수 있습니다. 이 옵션을 사용하면 보안 위험이 따르므로 사용하지 않는 것이 좋습니다.<br /> </td> 
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
   <td> 추적 URL 계산 스크립트.<br /> </td> 
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
   <td> <span class="uicontrol">NmsTracking_마지막 통합</span> <br /> </td> 
   <td> 마지막으로 추적 정보가 새 데이터로 통합되었습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> URL 계산 스크립트 열기.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> 추적 서버 암호<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> 포인터는 ID 및 날짜를 통해 처리된 마지막 메시지 이벤트를 추적합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> 전면 추적 서버의 보안 URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> 전면 추적 서버의 URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> 추적 서버에 연결하는 데 사용되는 URL 목록입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> 브라우저 식별 규칙 세트.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> 웹 추적 태그를 계산하는 데 사용되는 스크립트.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> 웹 추적 관리를 위해 설계된 가상 게재의 이름입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> 웹 추적 모드를 정의할 수 있습니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 개인 정보 보호 {#privacy}

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
   <td> 옵션 1을 선택한 경우 두 번째 단계에서 인터페이스에서 삭제를 수동으로 확인해야 합니다. 그렇지 않으면 데이터가 확인 없이 삭제됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> 요청 사이의 지연은 삭제 확인을 대기하고 요청이 취소됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllow</span> <br /> </td> 
   <td> 개인 정보 보호 요청을 처리/삭제할 때 허용되는 최대 오류 수.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_RemoveDelay</span> <br /> </td> 
   <td> 요청 사이의 지연이 대기열에 만들어지고 요청 데이터가 삭제됩니다.<br /> </td> 
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
   <td> 사용자를 인증하고 사용자에게 권한을 제공하는 데 LDAP 서버를 사용할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> 응용 프로그램 로그인으로 서버에 접속하여 다양한 검색을 수행할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> 응용 프로그램 로그인에 대한 암호화된 암호입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> Adobe Campaign에서 연산자 및 권한을 자동으로 만들 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> 로그인을 기반으로 한 LDAP DN의 계산 공식입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> 디렉토리에서 DN 검색을 활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span> <br /> </td> 
   <td> 검색 기준입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchFilter</span> <br /> </td> 
   <td> DN 검색 필터.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchScope</span> <br /> </td> 
   <td> 검색 범위.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Mechanism</span> <br /> </td> 
   <td> LDAP 서버에 접속하는 데 사용되는 인증 유형(일반, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span> <br /> </td> 
   <td> LDAP 디렉토리에서 Adobe Campaign의 명명된 권한으로 권한 및 그룹을 동기화할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> 인증 이름이 포함된 LDAP 속성입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> 검색 기준입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> 사용자 승인을 위한 검색 필터.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> LDAP 승인에서 Adobe Campaign 권한 이름을 추출하는 표현식.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span> <br /> </td> 
   <td> 검색 범위.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Server</span> <br /> </td> 
   <td> LDAP 서버 주소(구분 기호로 ':'를 지정하여 포트를 지정할 수 있음).<br /> </td> 
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
   <td> 값을 1로 설정하면 스크롤 막대를 세부 양식에 추가할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> '기타 서버' 모드에서 웹 폼 무효화에 사용할 인스턴스입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> '기타 서버' 모드에서 웹 폼 무효화에 사용할 인스턴스의 암호입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> 웹 폼의 무효화 모드를 지정할 수 있는 옵션: 기본적으로 로컬, 옵션이 '추적'인 경우 추적 서버를 사용하고 '기타 서버' 옵션과 함께 개인화된 목록을 사용합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURLs</span> <br /> </td> 
   <td> 웹 폼 무효화를 위해 연락할 서버의 개인화된 주소 목록('기타 서버' 모드).<br /> </td> 
  </tr> 
 </tbody> 
</table>
