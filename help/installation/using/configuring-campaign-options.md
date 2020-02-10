---
title: 캠페인 옵션 구성
seo-title: 캠페인 옵션 구성
description: 캠페인 옵션 구성
seo-description: null
page-status-flag: never-activated
uuid: 32e85e41-6898-4fb3-90c8-2201ceea2e91
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 9c1884f6-1dd8-41ab-b8dc-604c8cc2dc89
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 93a19c765e8d3de0fcbc29e27202fcbd2da6d32f

---


# Campaign Classic 옵션 목록{#configuring-campaign-options}

이 **[!UICONTROL Administration / Platform / Options]** 노드를 사용하면 Adobe Campaign 옵션을 구성할 수 있습니다.

>[!NOTE]
>
>Adobe Campaign 옵션 수정 또는 업데이트는 전문가만 수행할 수 있습니다.

이러한 항목 중 일부는 Campaign을 설치할 때 기본으로 제공되며, 필요에 따라 수동으로 추가할 수도 있습니다. 사용 가능한 옵션은 인스턴스와 함께 설치된 패키지에 따라 다릅니다.

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
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgDate</span><br /> </td> 
   <td> 배달 가능성 인스턴스에서 검색된 마지막 broadLogMsg 날짜.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Delivery_LastBroadLogMsgSent</span><br /> </td> 
   <td> 배달 가능성 인스턴스로 보낸 마지막 broadLogMsg 날짜.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span><br /> </td> 
   <td> 배달 보고서 식별자입니다. 지원 센터에 문의하여 식별자를 얻으십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span><br /> </td> 
   <td> 받은 편지함 렌더링에 테스트 주소를 사용할 스키마 목록입니다. (요소 이름은 쉼표로 구분됨) 예:custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span><br /> </td> 
   <td> 납품이 청구 보고서에서 주 수신자로 간주되기 위한 최소 수신자 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span><br /> </td> 
   <td> 새 템플릿의 기본 라우팅 서비스 공급자입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span><br /> </td> 
   <td> 한 번에 배달할 목적으로 만들어진 BroadLogs 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span><br /> </td> 
   <td> 트랜잭션당 로그(broadLogs) 삽입:일괄 처리당 처리할 행 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span><br /> </td> 
   <td> 중간 소싱 납품 분석 시 납품 부품의 그룹핑 크기<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span><br /> </td> 
   <td> 배달을 위한 기본 배달 기간(초)<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span><br /> </td> 
   <td> 배달 메시지 표준화를 위한 정규 표현식.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span><br /> </td> 
   <td> 값으로 "1"을 입력하면 더 이상 연락하지 않을 수신자를 제외할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span><br /> </td> 
   <td> 값으로 "1"을 입력하면 두 개의 단어를 자동으로 무시할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span><br /> </td> 
   <td> Adobe Campaign은 "Nms_DefaultRcpSchema" 전역 변수를 사용하여 기본 수신자 데이터베이스(nms:recipient)와 대화 상자를 엽니다.<br /> 옵션 값은 외부 수신자 테이블과 일치하는 스키마 이름과 일치해야 합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span><br /> </td> 
   <td> 메시지에 댓글을 달 때 사용되는 오류 주소의 구문을 정의할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span><br /> </td> 
   <td> 메시지를 보낼 때 사용되는 보낸 사람 주소의 구문을 정의할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span><br /> </td> 
   <td> 분석 중 최대 재시도 횟수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span><br /> </td> 
   <td> 게시 스크립트.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span><br /> </td> 
   <td> 푸시 메시지에 대한 broadLogMsg 개수를 비활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span><br /> </td> 
   <td> 배달 마법사에서 메시지 가중치를 표시합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span><br /> </td> 
   <td> 사용자가 비어 있는 경우 인스턴스 수준에서 이메일 배달에 사용되는 기본 '오류' 이메일 주소입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span><br /> </td> 
   <td> 사용자가 비어 있는 경우 인스턴스 수준에서 이메일 배달에 사용되는 기본 '보낸 사람' 이메일 주소입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span><br /> </td> 
   <td> 사용자가 비어 있는 경우 이메일 배달에 사용되는 인스턴스 수준의 기본 '회신' 이메일 주소입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span><br /> </td> 
   <td> 고객의 일반 이름입니다. 수신자에게 표시되는 일부 경고 메시지에 사용됩니다.<br /> "귀사는 ******* 또는 제휴 회사와 연락하여 이 메시지를 수신하게 되었습니다. 더 이상 ******로부터 메시지를 받지 않습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span><br /> </td> 
   <td> 사용자가 비어 있는 경우 인스턴스 수준에서 이메일 배달에 사용되는 기본 '보낸 사람' 이메일 레이블입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span><br /> </td> 
   <td> 사용자가 비어 있는 경우 인스턴스 수준에서 이메일 배달에 사용되는 기본 '회신' 이메일 레이블입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span><br /> </td> 
   <td> 이메일 메시지의 두 재시도 간격(초)<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span><br /> </td> 
   <td> 이메일 메시지에 대한 재시도 기간입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span><br /> </td> 
   <td> 임시 배달에 대한 메시지 가중치를 계산하는 데 사용되는 공식.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_WhitelistEmail</span><br /> </td> 
   <td> 인증된 전달 이메일 주소 목록(인바운드 메일 처리 모듈에서). 주소는 쉼표로 구분해야 합니다(또는 모두를 허용하려면 *). 예: xyz@abc.com, pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span><br /> </td> 
   <td> 채널 "이메일"(기본값으로 사용):받는 사람을 격리하기 전에 보내는 동안 SOFT 오류에 대해 허용되는 최대 오류 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span><br /> </td> 
   <td> 채널 "이메일"(기본값으로 사용):새로운 SOFT 오류를 고려하기 전에 이전에 참조된 SOFT 오류 이후 최소한의 체류 기간이 발생했습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span><br /> </td> 
   <td> 채널 "모바일"에서:받는 사람을 격리하기 전에 보내는 동안 SOFT 오류에 대해 허용되는 최대 오류 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span><br /> </td> 
   <td> 채널 "모바일"에서:새로운 SOFT 오류를 고려하기 전에 이전에 참조된 SOFT 오류 이후 최소한의 체류 기간이 발생했습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span><br /> </td> 
   <td> 미러 페이지 서버의 URL(기본적으로 NmsTracking_ServerUrl과 동일해야 함).<br /> 라우팅 정의에 URL이 지정되지 않은 경우 이메일 배달의 기본값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span><br /> </td> 
   <td> 보낸 사람 주소의 1줄입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span><br /> </td> 
   <td> 보낸 사람 주소의 3줄입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span><br /> </td> 
   <td> 보낸 사람 주소의 4줄입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span><br /> </td> 
   <td> 보낸 사람 주소의 6줄입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span><br /> </td> 
   <td> 보낸 사람 주소의 7줄입니다.<br /> </td> 
  </tr>
    <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span><br /> </td> 
   <td><p>이 옵션은 실행 중인 배달 수를 계산할 <span class="uicontrol"><a href="../../workflow/using/campaign.md">때</a></span> operationMgt 기술 워크플로우에서 사용됩니다.</p>일관성 없는 상태의 배달이 실행 중인 배달 수에서 제외되는 위의 일 수를 정의할 수 있습니다.</p><p>기본적으로 이 값은 "7"로 설정되며, 즉, 7일 이전의 일관성 없는 배달이 제외됩니다.</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span><br /> </td> 
   <td> 전송된 SMS 메시지의 매개 변수:메시지 우선 순위를 나타내기 위해 SMS 게이트웨이로 전송된 정보입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span><br /> </td> 
   <td> SMS 메시지를 보낼 때의 재시도 횟수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span><br /> </td> 
   <td> SMS 메시지 재시도가 수행되는 기간입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span><br /> </td> 
   <td> 이메일 주소의 유효한 문자<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span><br /> </td> 
   <td> 동기화 워크플로가 실행될 때마다 복구된 브로드캐스트 수를 제한하도록 최대 기간(시간 단위)을 지정할 수 있습니다. 이 <a href="../../platform/using/accessing-an-external-database.md#cloud-messaging---fda-synchronization">섹션을</a>참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span><br /> </td> 
   <td> MidSourcing 세션의 최대 호출 수입니다. 이 호출은 병렬로(기본적으로 3회) 실행할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span><br /> </td> 
   <td><p> 전달 속성에서 배달을 시작하기 위해 특정 연산자 또는 연산자 그룹이 지정된 경우 배달을 담당하는 연산자가 전송을 확인하도록 허용할 수 있습니다.</p><p> 이렇게 하려면 "1"을 값으로 입력하여 옵션을 활성화합니다. 이 옵션을 비활성화하려면 "0"을 입력합니다.</p><p> 그러면 전송 확인 프로세스가 기본값으로 작동합니다.전송 속성에서 전송을 위해 지정된 연산자 또는 그룹(또는 관리자)만 전송을 확인하고 수행할 수 있습니다. 이 <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">섹션을</a>참조하십시오.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span><br /> </td> 
   <td> 배달을 '지연'으로 간주하는 사용자 지정 지연(분)은 기본값인 30분입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span><br /> </td> 
   <td> Code128에 대한 특수 문자 지원을 활성화/비활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span><br /> </td> 
   <td> URL(LINE 채널)을 인코딩하기 위해 'lineImage' 서블릿에 사용된 AES 키<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span><br /> </td> 
   <td> 웹 세그먼트와 상태를 포함하는 옵션의 이름입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span><br /> </td> 
   <td> NmsUserAgent 통계에 대한 <span class="uicontrol">마지막 통합</span> 날짜<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> "0" 값과 함께 이 옵션을 추가하면 배달 버전의 XML 코드를 사용할 수 없습니다(마우스 오른쪽 단추 클릭/XML 소스 <span class="uicontrol">편집</span> 또는 <span class="uicontrol">CTRL + F4</span> 단축키).<br /> </td> 
  </tr> 
  <!--<tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC email address for Momentum to send a raw copy of the sent emails. <br /> </td> 
  </tr> 
 </tbody> 
</table>-->

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
   <td> <span class="uicontrol">NcmRessourcesDir</span><br /> </td> 
   <td> Adobe Campaign 클라이언트 콘솔에서 게시할 리소스의 위치입니다. 이 <a href="../../delivery/using/formatting.md#image-referencing">섹션을</a>참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDir미리 보기</span><br /> </td> 
   <td> Adobe Campaign 클라이언트 콘솔에서 미리 보기를 위한 리소스의 위치입니다. 이 <a href="../../delivery/using/formatting.md#image-referencing">섹션을</a>참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span><br /> </td> 
   <td> 업로드하는 동안 건너뛴 이미지에 대한 URL 마스크 목록입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> 이미지 업로드 구성. 이 값은 none / tracking / script / list일 수 있습니다(연산자의 선택적 설정으로 재정의할 수 있음). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span><br /> </td> 
   <td> 서버의 이미지를 저장할 폴더.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span><br /> </td> 
   <td> 로고를 표시할 공간입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span><br /> </td> 
   <td> 발행물의 루트 폴더.<br /> HTML 및 텍스트 내용 생성에 대한 자세한 내용은 <a href="../../delivery/using/using-a-content-template.md">이 섹션을</a>참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span><br /> </td> 
   <td> 전달에 사용된 이미지가 저장되는 서버를 정의하여 브라우저에서 이미지를 가져올 수 있도록 합니다.<br /> 빌드 버전 &lt;= 5098의 경우 인스턴스에 업로드된 이미지의 URL을 사용합니다.<br /> 빌드 버전 &gt; 5098의 경우 게시의 공개 URL 또는 XtkFileRes_ <span class="uicontrol">Public_URL</span> 옵션의 URL을 대신 사용합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span><br /> </td> 
   <td> 이미지 업로드를 위한 인스턴스 이름을 구성할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span><br /> </td> 
   <td> 이미지 업로드를 위한 암호를 구성할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span><br /> </td> 
   <td> 이미지 업로드를 위한 미디어 URL을 구성할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span><br /> </td> 
   <td> 전달의 온라인 리소스에 대한 기본 유효 기간(초)입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span><br /> </td> 
   <td> 공개 리소스 파일에 대한 새 URL입니다.<br /> </td> 
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
   <td> <span class="uicontrol">CrmMarketingActivityWindow</span><br /> </td> 
   <td> 이 개월 수에 대한 마케팅 내역이 표시됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span><br /> </td> 
   <td> 캠페인의 기본 유효 기간(초)입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span><br /> </td> 
   <td> 작업 관리 워크플로우에서 시작하여 한 번에 처리할 수 있는 전달/워크플로우/가설/시뮬레이션 작업의 최대 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span><br /> </td> 
   <td> 작업 관리 <a href="../../workflow/using/campaign.md">기술 워크플로우 실행을 모니터링할</a> 수 있습니다. 활성화되면(값 "1") 실행 정보가 워크플로우 감사 로그에 기록됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span><br /> </td> 
   <td> 예약된 모드에서 타깃팅 및 추출 조건에 대한 기간입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span><br /> </td> 
   <td> 테이블 통계가 자동으로 다시 계산되는 영향을 받는 레코드 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span><br /> </td> 
   <td> 내보낸 보고서의 오른쪽 위 모서리에 표시되는 로고.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span><br /> </td> 
   <td> 일시 중지된 워크플로우에 대한 검사 간 대기할 일 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span><br /> </td> 
   <td> "1"을 값으로 입력하여 작업 소유자가 수행하는 배달 유효성 검사를 활성화합니다. 이 옵션을 비활성화하려면 "0"을 입력합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span><br /> </td> 
   <td> 워크플로우의 활동 "마케팅 리소스 알림"에서 로드할 추가 JS 라이브러리<br /> </td> 
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
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span><br /> </td> 
   <td> (설치 호환성 모드:build&gt;6000) "1"을 입력하면 이 옵션이 저장된 암호에 대한 호환성 모드를 활성화합니다. 이 옵션을 변경하면 데이터베이스에 저장된 이전 암호가 사용되지 않습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span><br /> </td> 
   <td> 이 키는 데이터베이스의 대부분의 암호를 암호화하는 데 사용됩니다. (외부 계정, LDAP 암호...).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span><br /> </td> 
   <td> 1을 선택한 경우 이 옵션을 사용하여 javascript에서 privileescalation을 허용합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span><br /> </td> 
   <td> 1을 선택한 경우 이 옵션은 fileDownload.jsp를 통해 파일 다운로드 동안 ACL 컨트롤을 비활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span><br /> </td> 
   <td> 1을 선택한 경우 이 옵션은 Javascript 내에서 파일 샌드박스를 비활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span><br /> </td> 
   <td> 'true'로 설정된 경우, 권한 있는 비관리 연산자가 배포 마법사를 통해 xtkOption 값을 업데이트할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span><br /> </td> 
   <td> 1을 선택한 경우 이 옵션을 사용하면 암호 해독을 위해 암호 해독을 사용할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span><br /> </td> 
   <td> "1" 값을 입력하여 레코드를 삭제하기 전에 "수정한 사람" 필드를 수정하여 감사 추적 정보가 있는 요소의 삭제를 추적할 수 있습니다.<br /> </td> 
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
   <td> <span class="uicontrol">MC_EncompliantCustomJs</span><br /> </td> 
   <td> 이벤트 강화를 위해 개인화된 JavaScript 라이브러리 다음 두 함수의 구현을 포함해야 합니다.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol"></span> dealliesRtEvents(aiEventId);:데이터베이스의 이벤트를 강화하고 저장합니다(여기서 aiEventId <span class="uicontrol">는</span> 처리된 실시간 이벤트 테이블에 해당합니다).</p> </li> 
     <li> <p> <span class="uicontrol"></span> ellightroomBatchEvents(aiEventId);:데이터베이스의 이벤트를 강화하고 저장합니다. 여기서 aiEventId <span class="uicontrol">는</span> 처리된 배치 이벤트의 ID 테이블에 해당합니다.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span><br /> </td> 
   <td> 배달 로그를 통해 마지막 이벤트 상태 업데이트 날짜<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span><br /> </td> 
   <td> 라우팅 이벤트에 맞게 개인화된 JavaScript 라이브러리 다음 두 함수의 구현을 포함해야 합니다.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol"></span> dispatchRtEvent(iEventId);:실시간 이벤트를 처리하기 위해 선택한 트랜잭션 메시지의 내부 이름을 반환합니다(여기서 iEventId <span class="uicontrol">는</span> 처리된 실시간 이벤트의 ID에 해당합니다).</p> </li> 
     <li> <p> <span class="uicontrol"></span> dispatchBatchEvent(iEventId);:배치 이벤트를 처리하기 위해 선택한 트랜잭션 메시지의 내부 이름을 반환합니다(여기서 iEventId <span class="uicontrol">는</span> 처리된 배치 이벤트의 ID에 해당합니다).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span><br /> </td> 
   <td> 실시간 이벤트의 평균 전송 시간에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span><br /> </td> 
   <td> 실시간 이벤트의 평균 전송 시간에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span><br /> </td> 
   <td> 실시간 이벤트의 평균 처리 시간에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span><br /> </td> 
   <td> 실시간 이벤트의 평균 처리 시간에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span><br /> </td> 
   <td> 대기 중인 실시간 이벤트의 평균 수에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span><br /> </td> 
   <td> 실시간 이벤트의 평균 큐 시간에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span><br /> </td> 
   <td> 실시간 이벤트의 평균 대기열 시간에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span><br /> </td> 
   <td> 큐에 있는 실시간 이벤트의 평균 수에 대한 경고 임계값입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span><br /> </td> 
   <td> 실시간 이벤트의 처리 오류에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span><br /> </td> 
   <td> 실시간 이벤트의 처리 오류에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span><br /> </td> 
   <td> 대기 중인 실시간 이벤트의 최대 수에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span><br /> </td> 
   <td> 큐에 있는 실시간 이벤트의 최대 수에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span><br /> </td> 
   <td> 대기 중인 실시간 이벤트의 최소 수에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span><br /> </td> 
   <td> 큐에 있는 실시간 이벤트의 최소 수에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span><br /> </td> 
   <td> 대기 중인 실시간 이벤트 대기열에 대한 위험 조건 이전의 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span><br /> </td> 
   <td> 대기 중인 실시간 이벤트 대기열에 대한 경고 전 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span><br /> </td> 
   <td> 실시간 이벤트 처리량에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span><br /> </td> 
   <td> 실시간 이벤트 처리량에 대한 경고 임계값.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span><br /> </td> 
   <td> 이벤트 라우팅에 대한 재그룹화의 크기입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span><br /> </td> 
   <td> RtEvent 상태(데이터가 검색될 때까지 마지막 날짜)의 포인터를 업데이트합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span><br /> </td> 
   <td> 환영 메시지를 보내는 데 사용되는 메시지 센터 서버 URL(LINE 채널).<br /> </td> 
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
   <td> <span class="uicontrol">NmsCleanup_LastCleanup</span><br /> </td> 
   <td> 정리 프로세스가 마지막으로 실행된 시간을 정의합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span><br /> </td> 
   <td> <p>데이터베이스에서 브로드로그가 지워지는 시기를 정의할 수 있습니다.</p><p>이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 생성됩니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHasePurgeDelay</span><br /> </td> 
   <td><p> 이벤트 내역이 데이터베이스에서 지워지는 지연을 정의할 수 있습니다.</p><p>
   이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 생성됩니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span><br /> </td> 
   <td><p> 데이터베이스에서 이벤트가 지워지는 지연을 정의할 수 있습니다.</p><p>이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 생성됩니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span><br /> </td> 
   <td><p> 데이터베이스에서 이벤트 통계가 지워지는 시간을 정의할 수 있습니다.</p><p>이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 생성됩니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_ProvisionPurgeDelay</span><br /> </td> 
   <td><p> 데이터베이스에서 제안이 지워지는 시간을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 생성됩니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span><br /> </td> 
   <td> <p>데이터베이스에서 격리된 시간을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 생성됩니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RevernedDeliveryPurgeDelay</span><br /> </td> 
   <td> <p>데이터베이스에서 재활용 배달을 지운 후의 지연을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 생성됩니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span><br /> </td> 
   <td> <p>데이터베이스에서 거부되는 지연을 정의할 수 있습니다.</p><p>이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 생성됩니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span><br /> </td> 
   <td> <p>데이터베이스에서 추적 로그가 지워지는 시기를 정의할 수 있습니다.</p><p>이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 생성됩니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span><br /> </td> 
   <td><p> 데이터베이스에서 추적 통계가 지워지는 지연을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 생성됩니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span><br /> </td> 
   <td> <p>데이터베이스에서 방문자가 지워지는 시간을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 생성됩니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span><br /> </td> 
   <td> <p>데이터베이스에서 워크플로우 결과가 지워지는 지연을 정의할 수 있습니다.</p><p> 이 옵션은 인터페이스 내에서 지연이 수정되면 자동으로 생성됩니다. 옵션 목록에서 값을 수정하는 경우 초 단위로 표현해야 합니다.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span><br /> </td> 
   <td> Azure SQL Datawarehouse 커넥터 옵션.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span><br /> </td> 
   <td>다음 잠재적 값에 따라 모든 워크플로 및 PostgreSQL 데이터베이스 쿼리의 무조건부 중지 동작에 영향을 줄 수 있습니다.<ul>
    <li><p>0 - 기본값:데이터베이스에 영향을 주지 않고 워크플로우 프로세스 중지<p></li>
    <li><p>1 - pg_cancel_backend:데이터베이스의 워크플로우 프로세스 중지 및 쿼리 취소<p></li>
    <li><p>2 - pg_terminate_backend:워크플로우 프로세스를 중지하고 데이터베이스의 쿼리를 종료합니다.<p></li></ul></td> 
  </tr>  
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span><br /> </td> 
   <td> Adobe Campaign 표준 테이블의 인덱스를 포함할 테이블스페이스의 이름입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span><br /> </td> 
   <td> 표준 Adobe Campaign 테이블의 데이터를 포함할 테이블스페이스의 이름입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span><br /> </td> 
   <td> Adobe Campaign 작업 테이블의 데이터를 포함할 테이블스페이스의 이름입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span><br /> </td> 
   <td> Adobe Campaign 작업 테이블의 인덱스를 포함할 테이블스페이스의 이름입니다.<br /> </td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span><br /> </td> 
   <td> Microsoft SQL Server에서 작업 테이블에 대해 별도의 데이터베이스를 구성할 수 있습니다. 백업 및 복제를 최적화합니다. <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)">자세한 내용</a> 보기 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span><br /> </td> 
   <td> Adobe Campaign 인스턴스의 표준 시간대 구성을 <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">참조하십시오</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span><br /> </td> 
   <td> 데이터베이스의 문자열 필드가 NChar로 정의됩니까?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span><br /> </td> 
   <td> 데이터베이스의 'datetime' 필드는 시간대 정보를 저장합니까?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span><br /> </td> 
   <td> 데이터베이스의 ID입니다. 유니코드 DataBase의 경우 'u'로 시작합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span><br /> </td> 
   <td> 자동으로 생성된 내부 이름에 접두사가 추가되었습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span><br /> </td> 
   <td> xtk:schema 및 xtk:srcSchema에 대한 쿼리에서 반환되는 최대 결과 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span><br /> </td> 
   <td> 이 시간 이후에 자동 k="true"로 만들어지며 "pkSequence" 특성이 없는 모든 사용자 지정된 스키마는 자동 생성된 시퀀스 "auto__&lt;schemanespace&gt; &lt;schemaname&gt; _seq를 가져옵니다. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span><br /> </td> 
   <td> 마이그레이션 중에는 트리 구조가 새 버전 표준에 따라 자동으로 재구성됩니다.<br /> 이 옵션을 사용하면 탐색 트리의 자동 마이그레이션을 비활성화할 수 있습니다. 이 기능을 사용하는 경우 마이그레이션 후 오래된 폴더를 삭제하고 새 폴더를 추가하고 필요한 모든 검사를 실행해야 합니다.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol"></span> 데이터 유형:정수</p> </li> 
     <li> <p> <span class="uicontrol">값(텍스트)</span> :1 </p> </li> 
    </ul> 이 옵션은 기본 탐색 트리가 너무 많은 변경을 거친 경우에만 사용해야 합니다.<br /> 자세한 내용은 <a href="../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure">이 섹션을</a>참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span><br /> </td> 
   <td> NmsEmailErrorStat <span class="uicontrol">테이블 정리의 마지막</span> 처리 날짜입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span><br /> </td> 
   <td> <br /> 아래 구문에 따라 Postupgrade에서 발생한 오류에 대한 정보:{ <strong>{빌드 번호}:{mode:pre/post/...}:{The 'lessThan'/'greaterOrEquelThan' where error occurred + sub-step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span><br /> </td> 
   <td> 정리 워크플로우를 통해 통계 업데이트가 수행되지 않도록 "1" 값을 입력합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integration {#integration}

<table> 
 <thead> 
  <tr> 
   <th> 옵션 이름 </th> 
   <th> 설명 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">AEMResourceTypeFilter</span><br /> </td> 
   <td> Adobe Campaign에서 사용할 수 있는 AEM 리소스 유형. 값은 쉼표로 구분해야 합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span><br /> </td> 
   <td> Experience Cloud 트리거를 구성할 수 있습니다. 데이터 형식은 "긴 텍스트"이며 JSON 형식이어야 합니다. Adobe <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Campaign Classic에서 Experience Cloud 트리거 사용 방법을 참조하십시오</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span><br /> </td> 
   <td> 이 옵션은 CRM 커넥터를 통해 타사 시스템에서 데이터를 가져올 때 사용됩니다. 이 옵션을 활성화하면 마지막 가져오기 이후 수정된 개체만 수집할 수 있습니다. 이 옵션은 다음과 같이 수동으로 만들고 채워야 합니다. 
    <ul> 
     <li> <p> <span class="uicontrol">내부 이름</span> :LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">값(필드)</span> :yyyy/MM/dd hh:mm:ss 형식으로 마지막 가져오기의 날짜입니다. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span><br /> </td> 
   <td> 통합에 사용되는 Adobe Target 서버. 이 옵션은 기본적으로 이미 선택되어 있습니다. 이 값은 Adobe Target 도메인 서버에 해당하며 그 다음에 /m2 값이 나옵니다. 예:tt.omtrdc.net/m2.<br /> 이 <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">섹션을</a>참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span><br /> </td> 
   <td> Adobe Target 조직 이름. 이 값은 Adobe Target 클라이언트의 이름에 해당합니다.<br /> 이 <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">섹션을</a>참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span><br /> </td> 
   <td> Adobe Audience Manager와의 통합에 사용되는 옵션입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span><br /> </td> 
   <td> Adobe Audience Manager와의 통합에 사용되는 옵션입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span><br /> </td> 
   <td> Teradata 커넥터 옵션.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span><br /> </td> 
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
   <td> <span class="uicontrol">NmsCoupons_MaxPerTransac</span><br /> </td> 
   <td> SQL 트랜잭션당 업데이트된 쿠폰 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastProvisionSynchControl_</span><br /> </td> 
   <td> '+ [provision's schema] + "_" + extAccountSource.@executionInstanceId + [제안 스키마] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastProvisionSynchExec_</span><br /> </td> 
   <td> '+ [ 제안 스키마] + "_" + extAccountSource.@executionInstanceId + "_" + extAccountTarget@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span><br /> </td> 
   <td> 동기화 워크플로우 추적<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span><br /> </td> 
   <td> 비동기 제안 쓰기를 활성화/비활성화합니다("0"을 비활성화하려면, "1"을 활성화하면).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span><br /> </td> 
   <td> 쿠폰을 사용할 수 있도록 해줍니다.<br /> </td> 
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
   <td> <span class="uicontrol">NmsExecutionInstanceId</span><br /> </td> 
   <td> 실행 인스턴스 식별자입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span><br /> </td> 
   <td> 청구 보고서를 전송할 때 사용되는 고객 식별자입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span><br /> </td> 
   <td> 응용 프로그램 서버에 액세스하는 내부 기본 URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span><br /> </td> 
   <td> 마지막 업그레이드 전에 AC 인스턴스의 빌드 번호입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span><br /> </td> 
   <td> 공용 웹 응용 프로그램 서버의 기본 URL입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS.</span><br /> </td> 
   <td> 마이그레이션한 후 선언되지 않은 이전 SQL 함수를 계속 사용할 수 있습니다. 보안 위험 때문에 이 옵션을 사용하지 않는 것이 좋습니다.<br /> </td> 
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
   <td> <span class="uicontrol">NmsTracking_Available</span><br /> </td> 
   <td> 추적을 활성화할 수 있는 옵션입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span><br /> </td> 
   <td> 추적된 URL 계산 스크립트.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span><br /> </td> 
   <td> 추적 서버의 외부 계정을 정의할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span><br /> </td> 
   <td> 추적 서버에서 인스턴스 이름을 정의할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span><br /> </td> 
   <td> 마지막으로 추적 정보가 새 데이터와 통합되었습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span><br /> </td> 
   <td> URL 계산 스크립트를 엽니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span><br /> </td> 
   <td> 추적 서버 암호<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span><br /> </td> 
   <td> 포인터는 ID 및 날짜를 통해 처리된 마지막 메시지 이벤트를 추적합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span><br /> </td> 
   <td> 정면 추적 서버의 보안 URL입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span><br /> </td> 
   <td> 전두엽 추적 서버의 URL입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span><br /> </td> 
   <td> 추적 서버에 연결하는 데 사용되는 URL 목록입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span><br /> </td> 
   <td> 브라우저 식별 규칙 세트.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span><br /> </td> 
   <td> 웹 추적 태그를 계산하는 데 사용되는 스크립트입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span><br /> </td> 
   <td> 웹 추적 관리를 위해 설계된 가상 배달 이름입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span><br /> </td> 
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
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePending</span><br /> </td> 
   <td> 옵션 1을 선택한 경우 두 번째 단계에서 인터페이스에서 수동으로 삭제를 확인해야 합니다. 그렇지 않으면 확인 없이 데이터가 삭제됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span><br /> </td> 
   <td> 요청 간 지연이 확인 삭제 대기 및 요청이 취소되었습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span><br /> </td> 
   <td> 개인 정보 요청을 처리/삭제할 때 허용되는 최대 오류 수입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span><br /> </td> 
   <td> 요청 간 지연이 큐에 만들어지고 요청 데이터가 삭제됩니다.<br /> </td> 
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
   <td> <span class="uicontrol">XtkLdap_Active</span><br /> </td> 
   <td> 사용자를 인증하고 사용자에게 권한을 제공하는 데 사용할 LDAP 서버를 활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span><br /> </td> 
   <td> 응용 프로그램 로그인하여 다양한 검색을 위해 서버에 문의하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span><br /> </td> 
   <td> 응용 프로그램 로그인에 대한 암호화된 암호입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span><br /> </td> 
   <td> Adobe Campaign에서 연산자 및 권한을 자동으로 만들 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span><br /> </td> 
   <td> 로그인을 기반으로 한 LDAP DN에 대한 계산 공식.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span><br /> </td> 
   <td> 디렉토리에서 DN 검색을 활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span><br /> </td> 
   <td> 검색 기반<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchFilter</span><br /> </td> 
   <td> DN 검색 필터.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchScope</span><br /> </td> 
   <td> 검색 범위.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Mechanism</span><br /> </td> 
   <td> LDAP 서버에 연결하는 데 사용되는 인증 유형(일반, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span><br /> </td> 
   <td> LDAP 디렉토리에서 Adobe Campaign의 명명된 권한에 대한 권한 및 그룹 동기화를 활성화합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span><br /> </td> 
   <td> 인증 이름을 포함하는 LDAP 속성입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span><br /> </td> 
   <td> 검색 기반<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span><br /> </td> 
   <td> 사용자 인증에 대한 검색 필터입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span><br /> </td> 
   <td> LDAP 인증에서 Adobe Campaign 권한 이름을 추출하는 표현식<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span><br /> </td> 
   <td> 검색 범위.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Server</span><br /> </td> 
   <td> LDAP 서버 주소(구분 문자로 ':'를 지정하여 포트를 지정할 수 있음).<br /> </td> 
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
   <td> <span class="uicontrol">XtkUseScrollBar</span><br /> </td> 
   <td> 값을 1로 설정하면 스크롤 막대가 세부 양식에 추가될 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span><br /> </td> 
   <td> '기타 서버' 모드에서 웹 양식 무효화에 사용할 인스턴스입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span><br /> </td> 
   <td> '기타 서버' 모드에서 웹 양식 무효화에 사용할 인스턴스의 암호입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span><br /> </td> 
   <td> 웹 양식의 무효화 모드를 지정할 수 있는 옵션:local by default, uses tracking servers if the option is 'tracking' and uses a personalized list with the 'other server(s)' option.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURL</span><br /> </td> 
   <td> 웹 양식 무효화를 위해 연결할 서버 주소 목록('기타 서버' 모드).<br /> </td> 
  </tr> 
 </tbody> 
</table>

