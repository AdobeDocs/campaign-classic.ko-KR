---
product: campaign
title: Campaign Classic 기본 제공 패키지 설치
description: Campaign 기본 제공 패키지를 설치하는 방법 알아보기
feature: Installation, Application Settings
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: 0507e0372a81351adc145dafdd3cbe5d5422dc00
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 3%

---

# Campaign Classic 기본 제공 패키지 설치{#installing-campaign-standard-packages}



## 기본 제공 패키지 정보 {#campaign-standard-packages}

기본 제공 패키지에는 사용자의 요구 사항과 계약에 따라 설치할 수 있는 기능 세트가 포함되어 있습니다. Campaign 기본 제공 패키지의 전체 목록은 아래에서 확인할 수 있습니다.

>[!CAUTION]
>
>사용권 계약에 언급된 옵션에 해당하는 패키지만 설치할 수 있습니다.
>
>새 패키지를 설치하면 모든 플랫폼에 영향을 미칠 수 있습니다. 최종 배포 전에 테스트하고 유효성을 검사해야 합니다.
>
>패키지를 설치한 후에는 제거할 수 없습니다.
>
>호스팅 또는 하이브리드 고객은 Adobe에 문의하여 새 기본 제공 패키지를 배포하십시오.

기본 제공 패키지를 설치하려면

1. Adobe Campaign 클라이언트 콘솔의 **[!UICONTROL Tools > Advanced > Import package]**&#x200B;에서 패키지 가져오기 도우미에 액세스합니다.
1. **[!UICONTROL Install a standard package]**&#x200B;을(를) 선택합니다.
1. 패키지 목록에서 설치할 패키지를 선택합니다.
   >[!NOTE]
   >
   >패키지가 회색으로 표시되면 이미 설치되어 있거나 인스턴스와 호환되지 않음을 의미합니다. 호환성은 아래 표에 자세히 설명되어 있습니다.
1. 패키지 설치를 시작하려면 **[!UICONTROL Next]**&#x200B;을(를) 클릭한 다음 **[!UICONTROL Start]**&#x200B;을(를) 클릭합니다.

   패키지가 설치되면 진행률 표시줄에 **100%**&#x200B;이(가) 표시되며, 설치 로그에 **[!UICONTROL Installation of packages successful]** 메시지가 표시됩니다.

1. **[!UICONTROL Close]** 설치 창을 엽니다.

이제 패키지가 설치되었습니다.

### 기본 제공 패키지 목록 {#list-of-standard-packages}

다음 표에는 모든 Campaign 기본 제공 패키지가 나열되어 있습니다.

<table> 
 <thead> 
  <tr> 
   <th> 패키지 </th> 
   <th> 설명 </th> 
   <th> 인스턴스 유형 </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 배달<br /> </td> 
   <td> 메시지를 보낼 때 발생하는 게재 및 최종 문제를 모니터링합니다. <a href="../../delivery/using/about-delivery-monitoring.md">자세히 알아보기</a><br /> </td> 
   <td> 모두</td> 
  </tr> 
  <tr> 
   <td> 마케팅 캠페인(캠페인)<br /> </td> 
   <td> 커뮤니케이션 및 마케팅 캠페인을 정의, 최적화, 실행 및 분석합니다. <a href="https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html" target="_blank">자세히 알아보기</a><br /> </td> 
   <td> 마케팅</td>
  </tr> 
  <tr> 
   <td> 마케팅 리소스(MRM)<br /> </td> 
   <td> 작업, 예산 및 마케팅 리소스에 대한 관리 및 추적을 제공하여 공동 작업 모드에서 마케팅 작업을 제어합니다. <a href="https://experienceleague.adobe.com/docs/campaign/automation/mrm/about-marketing-resource-management.html?lang=ko" target="_blank">자세히 알아보기</a> <br /> </td> 
   <td> 마케팅</td> 
  </tr> 
  <tr> 
   <td> 오퍼 엔진(상호 작용)<br /> </td> 
   <td> 지정된 연락처(고객 또는 타겟)와의 상호 작용 중에 단일 또는 여러 개의 조정된 오퍼로 만들어 실시간으로 응답합니다.  선택 사항입니다. <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">자세히 알아보기</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
  <tr> 
   <td> 실행 인스턴스가 있는 오퍼 엔진 제어. 선택 사항입니다.<br /> </td> 
   <td> 오퍼 엔진(상호 작용)의 제어 인스턴스에 설치할 패키지입니다. <a href="../../interaction/using/distributed-architectures.md#packages-configuration">자세히 알아보기</a> </td> 
   <td> 마케팅<br /> </td>  
  </tr> 
  <tr> 
   <td> 실행 인스턴스용 오퍼 엔진. 선택 사항입니다.<br /> </td> 
   <td> 오퍼 엔진(상호 작용)의 실행 인스턴스에 설치할 패키지입니다. <a href="../../interaction/using/distributed-architectures.md">자세히 알아보기</a> </td> 
   <td> Mid, 실행 <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> 소셜 네트워크(소셜 마케팅) <br /> </td> 
   <td> Adobe Campaign을 X(이전의 Twitter) 및 Facebook과 동기화합니다. <a href="../../social/using/about-social-marketing.md">자세히 알아보기</a> <br /> </td> 
   <td> 모두</td> 
  </tr> 
  <tr> 
   <td> 트랜잭션 메시지 컨트롤(메시지 센터 - 컨트롤)<br /> </td> 
   <td> 정보 시스템에서 트리거된 이벤트에서 생성된 트리거 메시지를 관리합니다. 선택 사항입니다. <a href="../../message-center/using/about-transactional-messaging.md">자세히 알아보기</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션 메시지 실행(메시지 센터 - 실행) <br /> </td> 
   <td> 가용성 향상 및 로드 관리 향상 선택 사항입니다. <a href="../../message-center/using/about-transactional-messaging.md">자세히 알아보기</a><br /> </td> 
   <td> 실행<br /> </td>
  </tr> 
  <tr> 
   <td> LINE 채널<br /> </td> 
   <td> Adobe Campaign에서 LINE 채널을 사용하여 게재를 전송합니다. 선택 사항입니다. 트랜잭션 메시지(메시지 센터 패키지)는 필수입니다. <a href="../../delivery/using/line-channel.md">자세히 알아보기</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
  <tr> 
   <td> DM 채널<br /> </td> 
   <td> Adobe Campaign의 DM 채널을 사용하여 게재를 보냅니다. 선택 사항입니다. <a href="../../delivery/using/about-direct-mail-channel.md">자세히 알아보기</a><br /> </td> 
   <td> 모두<br /> </td>
  </tr> 
  <tr> 
   <td> 모바일 채널(SMS) <br /> </td> 
   <td> Adobe Campaign과 모바일/SMS 채널을 사용하여 게재를 전송합니다. 선택 사항입니다. <a href="../../delivery/using/sms-channel.md">자세히 알아보기</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
   <tr> 
   <td> 전화 채널<br /> </td> 
   <td> Adobe Campaign의 전화 채널을 사용하여 게재를 전송합니다. 콜센터에 사용됩니다. 선택 사항입니다. <a href="../../delivery/using/communication-channels.md">자세히 알아보기</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
  <tr> 
   <td> 모바일 앱 채널<br /> </td> 
   <td> Adobe Campaign 플랫폼을 사용하여 앱을 통해 iOS 및 Android 터미널에 개인화된 알림을 보냅니다. 선택 사항입니다. <a href="../../delivery/using/about-mobile-app-channel.md">자세히 알아보기</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
  <tr> 
   <td> 콘텐츠 관리자<br /> </td> 
   <td> 반복 뉴스레터 또는 웹 사이트를 만든 다음 메시지의 유효성을 검사하고 게시합니다. <a href="../../delivery/using/about-content-management.md">자세히 알아보기</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> 온라인 설문 조사(설문 조사 관리자)<br /> </td> 
   <td> 프로필 정보 추가 또는 수정, 가입, 가입 해지 또는 대회 참가 양식을 위한 온라인 양식을 만들고 관리합니다. 선택 사항입니다. <a href="../../surveys/using/about-surveys.md">자세히 알아보기</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> 데이터를 분석 및 측정하고, 통계를 계산하며, 보고서 작성 및 계산을 간소화 및 최적화할 수 있습니다. 또한 보고서를 만들고 대상 모집단을 빌드할 수 있습니다. 선택 사항입니다. <a href="../../reporting/using/ac-cubes.md">자세히 알아보기</a><br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 응답 관리자<br /> </td> 
   <td> 마케팅 캠페인의 성공 및 수익성을 측정하거나 모든 커뮤니케이션 채널에 대한 제안을 제공합니다.  선택 사항입니다. <a href="../../response/using/about-response-manager.md">자세히 알아보기</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 외부 데이터에 액세스(페더레이션 데이터 액세스)<br /> </td> 
   <td> Adobe Campaign 데이터의 구조를 변경하지 않고 외부 데이터에 액세스할 수 있도록 하나 이상의 외부 데이터베이스에 저장된 정보를 처리하기 위한 FDA(Federated Data Access) 옵션을 제공합니다.  선택 사항입니다. <a href="https://experienceleague.adobe.com/docs/campaign/automation/workflows/advanced-management/accessing-an-external-database-fda.html" target="_blank">자세히 알아보기</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
  <tr> 
   <td> 캠페인 최적화<br /> </td> 
   <td> 회사 커뮤니케이션 정책을 준수하면서 고객의 요구 사항과 기대치에 가장 적합한 메시지를 보낼 수 있도록 게재 전송을 제어, 필터링 및 모니터링합니다. 선택 사항입니다. <a href="https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=ko" target="_blank">자세히 알아보기</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 게재 가능성 모니터링(전자 메일 게재 가능성)<br /> </td> 
   <td> 캠페인이 바운스 없이 또는 스팸으로 표시되지 않고 수신자의 받은 편지함에 도달했는지 측정합니다. 선택 사항입니다. <a href="../../delivery/using/about-deliverability.md">자세히 알아보기</a> <br /> </td> 
   <td> 모두 </td> 
  </tr> 
  <tr> 
   <td> 쿠폰 관리<br /> </td> 
   <td> 예정된 마케팅 오퍼에 추가할 쿠폰 세트를 만듭니다. 선택 사항입니다. <a href="https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalized-coupons.html" target="_blank">자세히 알아보기</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 받은 편지함 렌더링(IR)<br /> </td> 
   <td> 메시지를 받을 수 있는 다른 컨텍스트에서 전송된 메시지를 미리 보고 주요 데스크탑 및 응용 프로그램의 호환성을 확인할 수 있습니다. 선택 사항입니다. <a href="../../delivery/using/inbox-rendering.md">자세히 알아보기</a><br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 중앙/로컬 마케팅(분산 마케팅)<br /> </td> 
   <td> 중앙 엔터티(본사, 마케팅 부서 등)와 지역 엔터티(영업 지점, 지역 에이전시 등) 간의 협력 캠페인을 구현합니다. 선택 사항입니다. <a href="https://experienceleague.adobe.com/docs/campaign/automation/distributed-marketing/about-distributed-marketing.html?lang=ko" target="_blank">자세히 알아보기</a><br /> </td> 
   <td> 마케팅 </td> 
  </tr> 
  <tr> 
   <td> CRM 커넥터<br /> </td> 
   <td> Adobe Campaign 플랫폼을 타사 시스템에 연결하는 다양한 CRM 커넥터를 제공합니다.  <a href="../../platform/using/crm-connectors.md">자세히 알아보기</a> <br /> </td> 
   <td> 마케팅</td> 
  </tr> 
  <tr> 
   <td> 웹 분석 커넥터<br /> </td> 
   <td> Adobe Campaign 및 Adobe Analytics이 Web Analytics 커넥터 패키지를 통해 상호 작용할 수 있습니다. 트랜잭션 메시지(메시지 센터 패키지)와 호환되지 않습니다. <a href="../../integrations/using/gs-aa.md">자세히 알아보기</a><br /> </td> 
   <td> 마케팅 </td> 
  </tr> 
  <tr> 
   <td> AEM 통합<br /> </td> 
   <td> Adobe Experience Manager에서 이메일 게재 콘텐츠와 양식을 직접 관리할 수 있으므로 AEM의 콘텐츠 편집 기능과 Adobe Campaign의 게재 기능을 활용할 수 있습니다. <a href="../../integrations/using/about-adobe-experience-manager.md">자세히 알아보기</a> <br /> </td> 
   <td> 마케팅</td> 
  </tr> 
  <tr> 
   <td> Adobe Experience Cloud 공유 대상 통합<br /> </td> 
   <td> Adobe Experience Cloud 솔루션 및 앱과 대상/세그먼트를 교환하고 공유할 수 있습니다. IMS가 필요합니다. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">자세히 알아보기</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> Adobe Experience Cloud<br />과(와) 통합 </td> 
   <td> 다양한 Adobe Experience Cloud 솔루션의 대상/세그먼트를 Adobe Campaign으로 가져오고 내보낼 수 있습니다. 선택 사항입니다. <a href="../../integrations/using/configuring-ims.md#installing-the-package">자세히 알아보기</a> </td> 
   <td> 마케팅</td> 
  </tr> 
  <tr> 
   <td> 개인 정보 보호 규정<br /> </td> 
   <td> Campaign Classic에서 개인 정보 보호 규정을 준수하는 데 도움이 되는 추가 기능이 포함되어 있습니다. <a href="https://helpx.adobe.com/kr/campaign/kb/acc-privacy.html">자세히 알아보기</a> <br /> </td> 
   <td> 모두</td> 
  </tr> 
  <tr> 
   <td> 중간 소싱 <br />(으)로 전송 </td> 
   <td> 중간 소싱 서버의 설치 및 구성과 서드파티가 중간 소싱 모드에서 메시지를 보낼 수 있는 인스턴스의 배포에 대해 자세히 설명합니다. 선택 사항입니다. <a href="../../installation/using/mid-sourcing-server.md">자세히 알아보기</a> <br /> </td> 
   <td> 마케팅 </td> 
  </tr> 
  <tr> 
   <td> 중간 소싱 플랫폼<br /> </td> 
   <td> 이 구성은 호스팅된(ASP) 구성과 내재화 간의 최적의 중간 솔루션입니다. 외향 실행 구성 요소는 Adobe Campaign에서 호스팅되는 "중간 소싱" 서버에서 수행됩니다. 선택 사항입니다. <a href="../../installation/using/mid-sourcing-server.md">자세히 알아보기</a> <br /> </td> 
   <td> 중간 소싱 </td> 
  </tr> 
  <tr> 
   <td> AMP 지원<br /> </td> 
   <td> 이메일 형식에 새로운 대화형 AMP를 사용하고 다이내믹 이메일을 보낼 수 있습니다. 선택 사항입니다. <a href="https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-interactive-content.html" target="_blank">자세히 알아보기</a> <br /> </td> 
   <td> 모두 </td> 
  </tr> 
  <tr> 
   <td> ACS 커넥터(더 이상 사용되지 않음)<br /> </td> 
   <td> Adobe Campaign v7 및 Adobe Campaign Standard의 브리지입니다. 이 기능은 Campaign Standard에 데이터를 자동으로 복제하여 두 애플리케이션의 최고를 결합하는 Campaign v7의 통합 기능입니다. 선택 사항입니다.<br /> </td> 
   <td> 마케팅 </td> 
  </tr> 
 </tbody> 
</table>

### 메시지 센터 패키지 {#message-center-package}

트랜잭션 메시지(메시지 센터 패키지)를 설치하기 전에 게재 채널(이메일, 모바일 채널, 모바일 앱 채널, LINE 등)을 설치해야 합니다. 이메일 전용 메시지 센터 프로젝트를 시작했으며 나중에 새 채널을 추가해야 하는 경우 다음 단계를 따라야 합니다.

1. 패키지 가져오기 도우미(**)를 사용하여 새 채널(예:**&#x200B;모바일 채널&#x200B;**[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**)을 설치합니다.
1. 파일(**[!UICONTROL Tools > Advanced > Import package > File]**)을 가져온 다음 다음을 선택합니다.

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. **[!UICONTROL XML data content to import]**&#x200B;에서 관련 채널에 해당하는 메시지 센터 게재 템플릿만 유지합니다. 예를 들어 **Mobile 채널**&#x200B;을 추가한 경우 **(smsTriggerMessage) 템플릿에 해당하는** entities **[!UICONTROL Mobile transactional message]** 요소만 유지합니다. **모바일 앱 채널**&#x200B;을 추가한 경우 **iOS 트랜잭션 메시지** 템플릿(iosTriggerMessage) 및 **Android 트랜잭션 메시지**(androidTriggerMessage)만 유지합니다.

   ![](assets/messagecenter_install_channel.png)


### [!DNL LINE] 채널 설정{#line-package}

[!DNL LINE] 채널을 설정하려면 먼저 [!DNL LINE] 패키지를 설치해야 합니다.

중간 소싱 구성의 컨텍스트에서 다음을 수행해야 합니다.

* Marketing 및 MID 인스턴스에 모두 [!DNL LINE] 패키지 설치

* 게재 모드를 변경하여 mid 인스턴스를 가리키도록 mkt 인스턴스에서 [!DNL LINE] 외부 계정을 설정합니다. [자세히 알아보기](../../delivery/using/line-channel.md#configure-line-external)

* MID 인스턴스의 외부 계정에 [!DNL LINE] 자격 증명을 설정합니다.

>[!CAUTION]
>
>[!DNL LINE] 전에 메시지 센터 패키지를 설치하면 [!DNL LINE] 채널의 메시지 센터 게재 템플릿을 사용할 수 없습니다.