---
title: Campaign Classic 표준 패키지 설치
seo-title: Campaign Classic 표준 패키지 설치
description: Campaign Classic 표준 패키지 설치
seo-description: null
page-status-flag: never-activated
uuid: 1cba9487-52fc-442f-ae99-f8a2c157f25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: dd8f9adf-208c-42d9-b1a7-bfc8a690687e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f5062117b5cefbdd2570018f6803f114c14a3fae

---


# Campaign Classic 표준 패키지 설치{#installing-campaign-standard-packages}

## 표준 패키지 정보 {#campaign-standard-packages}

패키지는 사용자의 요구 사항에 따라 설치할 수 있는 기능 세트입니다. 이 옵션을 사용하면 인스턴스에 옵션을 더 추가할 수 있습니다.

>[!CAUTION]
>
>라이센스 계약에 명시된 옵션에 해당하는 패키지만 설치할 수 있습니다.
>
>패키지가 설치되면 제거할 수 없습니다. 새 패키지를 설치하면 모든 플랫폼에 영향을 줄 수 있습니다.최종 배포 전에 테스트 및 유효성 검사를 수행해야 합니다.

표준 패키지를 설치하려면:

1. Adobe Campaign 클라이언트 콘솔에서 패키지 가져오기 마법사에 **[!UICONTROL Tools > Advanced > Package import...]** 액세스합니다.
1. 을 **[!UICONTROL Install a standard package]**&#x200B;선택합니다.
1. 표시되는 목록에서 설치할 패키지를 확인합니다.
   >[!NOTE]
   >
   >패키지가 회색으로 표시되면 설치할 수 없습니다. 즉, 이미 설치되어 있거나 인스턴스와 호환되지 않습니다. 예를 들어, 마케팅 인스턴스에는 **Mid-sourcing 플랫폼** 패키지를 설치할 수 없습니다. 아래 표에 이 정보가 나와 있습니다.
1. 을 **[!UICONTROL Next]**&#x200B;클릭한 다음 패키지 설치를 **[!UICONTROL Start]** 시작합니다.

   패키지가 설치되면 진행률 표시줄이 **100%** 로 표시되며 설치 로그에 다음 메시지가 표시됩니다. **[!UICONTROL Installation of packages successful]** Adobe

1. **[!UICONTROL Close]** 설치 창

패키지가 설치되었습니다.

### 기본 패키지 목록 {#list-of-standard-packages}

다음 표에는 설명이 포함된 모든 표준 패키지, 설치할 수 있는 인스턴스 유형(마케팅, 중간 등)이 나와 있습니다. 및 추가 정보를 참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 패키지 </th> 
   <th> 설명 </th> 
   <th> 인스턴스 유형 </th> 
   <th> 추가 정보 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 게재<br /> </td> 
   <td> 메시지가 전송될 때 발생하는 전달 및 최종 문제를 모니터링합니다.<br /> </td> 
   <td> 모두</td> 
   <td> <a href="../../delivery/using/monitoring-a-delivery.md">자세한 내용</a></td> 
  </tr> 
  <tr> 
   <td> 마케팅 캠페인(캠페인)<br /> </td> 
   <td> 커뮤니케이션 및 마케팅 캠페인을 정의, 최적화, 실행 및 분석합니다.<br /> </td> 
   <td> 마케팅</td> 
   <td> <a href="../../campaign/using/designing-marketing-campaigns.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 마케팅 리소스(MRM)<br /> </td> 
   <td> 작업, 예산 및 마케팅 리소스의 관리 및 추적을 제공하여 협업 모드에서 마케팅 작업을 제어합니다.<br /> </td> 
   <td> 마케팅</td> 
   <td> <a href="../../campaign/using/about-marketing-resource-management.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 오퍼 엔진(상호 작용)<br /> </td> 
   <td> 해당 연락처(고객 또는 타겟)와 상호 작용하는 동안 단일 또는 여러 개의 수정된 오퍼로 만들어 실시간으로 응답합니다. <br /> </td> 
   <td> 모두<br /> </td> 
   <td> 선택 사항, <a href="../../interaction/using/interaction-and-offer-management.md">자세한 내용</a></td> 
  </tr> 
  <tr> 
   <td> 실행 인스턴스가 있는 오퍼 엔진 제어<br /> </td> 
   <td> </td> 
   <td> 마케팅<br /> </td> 
   <td> 선택 사항입니다</td> 
  </tr> 
  <tr> 
   <td> 실행 인스턴스를 위한 오퍼 엔진<br /> </td> 
   <td> </td> 
   <td> 중간, 실행 <br /> </td> 
   <td> 선택 사항입니다</td> 
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> 소셜 네트워크(소셜 마케팅) <br /> </td> 
   <td> Adobe Campaign을 Twitter 및 Facebook과 동기화합니다.<br /> </td> 
   <td> 모두</td> 
   <td> <a href="../../social/using/starting-workflows.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션 메시지 제어(메시지 센터 - 제어)<br /> </td> 
   <td> 정보 시스템에서 트리거된 이벤트에서 생성된 트리거 메시지를 관리합니다.<br /> </td> 
   <td> 마케팅<br /> </td> 
   <td> 선택 사항, <a href="../../message-center/using/about-transactional-messaging.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션 메시지 실행(메시지 센터 - 실행) <br /> </td> 
   <td> 가용성을 높이고 로드 관리를 향상시킵니다.<br /> </td> 
   <td> 실행<br /> </td> 
   <td> 선택 사항, <a href="../../message-center/using/about-transactional-messaging.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> LINE 채널<br /> </td> 
   <td> Adobe Campaign과 함께 LINE 채널을 사용하여 배달을 보냅니다.<br /> </td> 
   <td> 모두<br /> </td> 
   <td> 옵션, 메시지 센터 필수</td> 
  </tr> 
  <tr> 
   <td> DM 채널<br /> </td> 
   <td> Adobe Campaign과 함께 DM 채널을 사용하여 배달을 보냅니다.<br /> </td> 
   <td> 모두<br /> </td> 
   <td> 선택 사항, <a href="../../delivery/using/about-direct-mail-channel.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 모바일 채널(SMS) <br /> </td> 
   <td> Adobe Campaign과 함께 모바일/SMS 채널을 사용하여 배달을 보냅니다.<br /> </td> 
   <td> 모두<br /> </td> 
   <td> 선택 사항, <a href="../../delivery/using/sms-channel.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 전화 채널<br /> </td> 
   <td> Adobe Campaign과 전화 채널을 사용하여 배달을 전송합니다.<br /> </td> 
   <td> 모두<br /> </td> 
   <td> 선택 사항입니다</td> 
  </tr> 
  <tr> 
   <td> 팩스 채널<br /> </td> 
   <td> Adobe Campaign과 함께 팩스 채널을 사용하여 배달을 전송합니다.<br /> </td> 
   <td> 모두<br /> </td> 
   <td> 선택 사항입니다</td> 
  </tr> 
  <tr> 
   <td> 모바일 앱 채널<br /> </td> 
   <td> Adobe Campaign 플랫폼을 사용하여 앱을 통해 개인화된 알림을 iOS 및 Android 터미널로 보냅니다. <br /> </td> 
   <td> 모두<br /> </td> 
   <td> 선택 사항, <a href="../../delivery/using/about-mobile-app-channel.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 콘텐츠 관리자<br /> </td> 
   <td> 반복적인 뉴스레터 또는 웹 사이트를 만든 다음 메시지를 확인하고 게시합니다.<br /> </td> 
   <td> </td> 
   <td> <a href="../../delivery/using/about-content-management.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 온라인 설문 조사(설문 조사 관리자)<br /> </td> 
   <td> 온라인 양식을 만들어 관리하여 프로필 정보를 추가하거나 수정하고 구독을 취소하거나 경쟁 등록 양식을 구독 취소할 수 있습니다.<br /> </td> 
   <td> 마케팅<br /> </td> 
   <td> 선택 사항, <a href="../../web/using/about-surveys.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 마케팅 분석<br /> </td> 
   <td> 데이터를 분석 및 측정하고, 통계를 계산하며, 보고서 작성 및 계산을 단순화 및 최적화할 수 있습니다. 또한 보고서를 만들고 타겟 모집단을 만들 수도 있습니다. <br /> </td> 
   <td> 마케팅<br /> </td> 
   <td> 선택 사항, <a href="../../reporting/using/about-cubes.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 응답 관리자<br /> </td> 
   <td> 마케팅 캠페인의 성공 및 수익성을 측정하거나 모든 커뮤니케이션 채널에 대한 제안을 제공합니다.<br /> </td> 
   <td> 마케팅<br /> </td> 
   <td> 선택 사항, <a href="../../campaign/using/about-response-manager.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 외부 데이터 액세스(통합 데이터 액세스)<br /> </td> 
   <td> 하나 이상의 외부 데이터베이스에 저장된 정보를 처리하기 위해 Adobe Campaign 데이터 구조를 변경하지 않고 외부 데이터에 액세스할 수 있도록 통합 데이터 액세스(FDA) 옵션을 제공합니다.<br /> </td> 
   <td> 모두<br /> </td> 
   <td> 선택 사항, <a href="../../workflow/using/accessing-an-external-database--fda-.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 캠페인 최적화<br /> </td> 
   <td> 회사 커뮤니케이션 정책에 따라 전송되는 메시지가 고객의 요구와 기대에 가장 잘 맞도록 전달 전송을 제어, 필터 및 모니터링합니다. <br /> </td> 
   <td> 마케팅<br /> </td> 
   <td> 선택 사항, <a href="../../campaign/using/about-campaign-typologies.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 배달 가능성 모니터링(이메일 배달 기능)<br /> </td> 
   <td> 바운싱 또는 스팸으로 표시되지 않고 수신자의 받은 편지함에 도달하는 캠페인의 성공을 측정합니다.<br /> </td> 
   <td> 모두 </td> 
   <td> 선택 사항, <a href="https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 쿠폰 관리<br /> </td> 
   <td> 예정된 마케팅 오퍼에 추가할 쿠폰 세트를 만듭니다.<br /> </td> 
   <td> 마케팅<br /> </td> 
   <td> 선택 사항, <a href="../../delivery/using/personalized-coupons.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 받은 편지함 렌더링(IR)<br /> </td> 
   <td> 수신될 수 있는 다양한 컨텍스트에서 메시지를 미리 보고 주요 데스크톱 및 응용 프로그램의 호환성을 확인할 수 있습니다. 리트머스 계정이 필요합니다.<br /> </td> 
   <td> 마케팅<br /> </td> 
   <td> 선택 사항, <a href="../../delivery/using/about-deliverability.md#inbox-rendering">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 중앙/로컬 마케팅(분산 마케팅)<br /> </td> 
   <td> 중앙 개체(본사, 마케팅 부서 등) 간의 협업 캠페인 구현 및 해당 지역 업체(판매 지점, 지역 기관 등)와<br /> </td> 
   <td> 마케팅 </td> 
   <td> 선택 사항, <a href="../../campaign/using/about-distributed-marketing.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> CRM 커넥터<br /> </td> 
   <td> Adobe Campaign 플랫폼을 타사 시스템에 연결하는 다양한 CRM 커넥터를 제공합니다.<br /> </td> 
   <td> 마케팅</td> 
   <td> <a href="../../platform/using/crm-connectors.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 웹 분석 커넥터<br /> </td> 
   <td> Adobe Campaign 및 Adobe Analytics가 웹 분석 커넥터 패키지를 통해 상호 작용할 수 있도록 합니다.<br /> </td> 
   <td> 마케팅 </td> 
   <td> 트랜잭션 메시지와 호환되지 않음 <a href="../../platform/using/adobe-analytics-data-connector.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> AEM 통합<br /> </td> 
   <td> AEM의 컨텐츠 편집 기능과 Adobe Campaign의 전달 기능을 활용할 수 있도록 이메일 게재의 컨텐츠 및 양식을 Adobe Experience Manager에서 직접 관리할 수 있습니다.<br /> </td> 
   <td> 마케팅</td> 
   <td> <a href="../../integrations/using/about-adobe-experience-manager.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> Adobe Marketing Cloud 공유 대상 통합<br /> </td> 
   <td> Adobe Experience Cloud 솔루션 및 핵심 서비스와 고객/세그먼트를 교환하고 공유할 수 있습니다.<br /> </td> 
   <td> 마케팅<br /> </td> 
   <td> IMS 필요, <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> Adobe Marketing Cloud와 통합<br /> </td> 
   <td> 다른 Adobe Marketing Cloud 솔루션의 대상/세그먼트를 Adobe Campaign으로 가져오고 내보낼 수 있습니다. </td> 
   <td> 마케팅</td> 
   <td> 선택 사항, <a href="../../integrations/using/configuring-ims.md#installing-the-package">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 개인 정보 보호 규정<br /> </td> 
   <td> Campaign Classic에서 프로젝트가 GDPR을 준수하는 데 도움이 되는 추가 기능을 포함합니다.<br /> </td> 
   <td> 모두</td> 
   <td> <a href="https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 중간 출처로 이전 <br /> </td> 
   <td> 중간 소싱 서버의 설치 및 구성뿐만 아니라 제3자가 중간 소싱 모드로 메시지를 전송할 수 있는 인스턴스의 배포에 대한 세부 사항입니다.<br /> </td> 
   <td> 마케팅 </td> 
   <td> 선택 사항, <a href="../../installation/using/mid-sourcing-server.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> 중간 소싱 플랫폼<br /> </td> 
   <td> 이 구성은 호스팅된(ASP) 구성과 내부화 간의 최적의 중간 솔루션입니다. 외향적 실행 구성 요소는 Adobe Campaign에서 호스팅되는 "미드소싱" 서버에서 수행됩니다.<br /> </td> 
   <td> 중간 소싱 </td> 
   <td> 선택 사항, <a href="../../installation/using/mid-sourcing-server.md">자세한 내용</a> </td> 
  </tr> 
  <tr> 
   <td> ACS 커넥터<br /> </td> 
   <td> Adobe Campaign v7 및 Adobe Campaign Standard를 연결합니다. 이 기능은 Campaign Standard에 자동으로 데이터를 복제하여 두 애플리케이션 중 최상의 결과를 통합하는 Campaign v7의 통합 기능입니다. <br /> </td> 
   <td> 마케팅 </td> 
   <td> 선택 사항, <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">자세한 내용</a> </td> 
  </tr> 
 </tbody> 
</table>

### 메시지 센터 패키지 {#message-center-package}

배달 채널(모바일 채널, 모바일 앱 채널 등)을 추가하려면 메시지 센터 패키지를 설치하기 전에 이 작업을 수행해야 합니다. 이메일 채널에서 메시지 센터 프로젝트를 시작한 다음 프로젝트 중간에 새 채널을 추가하기로 결정한 경우 다음 단계를 따라야 합니다.

1. 패키지 가져오기 마법사()를 사용하여 원하는 채널(예: **모바일 채널**)을 설치합니다 **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**.
1. 파일( **[!UICONTROL Tools > Advanced > Import package > File]**)을 가져오고 다음을 선택합니다.

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. 에서 **[!UICONTROL XML data content to import]**&#x200B;연결된 채널에 해당하는 메시지 센터 배달 템플릿만 유지합니다. 예를 들어 모바일 채널을 **추가한**&#x200B;경우 **(smsTriggerMessage) 템플릿에 해당하는** 엔티티 **[!UICONTROL Mobile transactional message]** 요소만유지하십시오. 모바일 앱 채널을 추가한 **경우** iOS 트랜잭션 메시지 **템플릿(iosTriggerMessage) 및** Android 트랜잭션 메시지 **** (androidTriggerMessage)만 보관하십시오.

   ![](assets/messagecenter_install_channel.png)

### LINE 패키지 {#line-package}

Adobe Campaign과 함께 LINE 채널을 사용하여 배달을 보내려면 LINE 패키지를 설치해야 합니다.

LINE 패키지 설치는 패키지 가져오기 섹션에 자세히 설명된 표준 [설치입니다](../../platform/using/working-with-data-packages.md#importing-packages) .

![](assets/line_config_1.png)

>[!CAUTION]
>
>LINE 이전에 메시지 센터 패키지를 설치한 경우 LINE용 메시지 센터 배달 템플릿을 사용할 수 없습니다.
