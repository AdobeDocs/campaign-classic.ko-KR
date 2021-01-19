---
solution: Campaign Classic
product: campaign
title: Campaign Classic 내장 패키지 설치
description: Campaign 내장 패키지를 설치하는 방법 알아보기
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 44f2aed49a12d51bb3b38f304e6b922f0faf68cc
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 5%

---


# Campaign Classic 내장 패키지 설치{#installing-campaign-standard-packages}

## 내장 패키지 {#campaign-standard-packages} 정보

내장된 패키지에는 사용자의 요구 사항과 계약에 따라 설치할 수 있는 일련의 기능이 포함되어 있습니다. Campaign 내장 패키지의 전체 목록은 아래에서 확인할 수 있습니다.

>[!CAUTION]
>
>라이센스 계약에 명시된 옵션에 해당하는 패키지만 설치할 수 있습니다.
>
>새 패키지를 설치하면 모든 플랫폼에 영향을 줄 수 있습니다.최종 배포 전에 테스트 및 검증을 수행해야 합니다.
>
>패키지가 설치되면 제거할 수 없습니다.

내장 패키지를 설치하려면:

1. Adobe Campaign 클라이언트 콘솔의 **[!UICONTROL Tools > Advanced > Package import...]**&#x200B;에서 패키지 가져오기 마법사에 액세스합니다.
1. **[!UICONTROL Install a standard package]**&#x200B;을(를) 선택합니다.
1. 패키지 목록에서 설치할 패키지를 확인합니다.
   >[!NOTE]
   >
   >패키지가 회색으로 표시되면 이미 설치되어 있거나 인스턴스와 호환되지 않음을 의미합니다. 호환성은 아래 표에 자세히 나와 있습니다.
1. **[!UICONTROL Next]**&#x200B;을 클릭한 다음 **[!UICONTROL Start]**&#x200B;을 클릭하여 패키지 설치를 시작합니다.

   패키지가 설치되면 진행률 표시줄에 **100%**&#x200B;이 표시되고 설치 로그에 다음 메시지가 표시됩니다.**[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** 설치 창을 엽니다.

패키지가 설치되었습니다.

### 기본 패키지 목록 {#list-of-standard-packages}

다음 표는 모든 Campaign 내장 패키지를 나열합니다.

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
   <td> 게재<br /> </td> 
   <td> 메시지가 전송될 때 발생하는 전달 및 최종 문제를 모니터링합니다. <a href="../../delivery/using/about-delivery-monitoring.md">자세히 알아보기</a><br /> </td> 
   <td> 모두</td> 
  </tr> 
  <tr> 
   <td> 마케팅 캠페인(캠페인)<br /> </td> 
   <td> 커뮤니케이션 및 마케팅 캠페인을 정의, 최적화, 실행 및 분석합니다. <a href="../../campaign/using/designing-marketing-campaigns.md">자세한 내용</a><br /> </td> 
   <td> 마케팅</td>
  </tr> 
  <tr> 
   <td> 마케팅 리소스(MRM)<br /> </td> 
   <td> 작업, 예산 및 마케팅 리소스에 대한 관리 및 추적을 제공하여 협업 모드에서 마케팅 작업을 제어합니다. <a href="../../campaign/using/about-marketing-resource-management.md">자세한 내용</a> <br /> </td> 
   <td> 마케팅</td> 
  </tr> 
  <tr> 
   <td> 오퍼 엔진(상호 작용)<br /> </td> 
   <td> 단일 또는 여러 개의 수정된 오퍼로 만들어 지정된 연락처(고객 또는 타겟)와 상호 작용하는 동안 실시간으로 응답합니다.  선택 사항입니다. <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">자세한 내용</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
  <tr> 
   <td> 실행 인스턴스에서 오퍼 엔진 제어 선택 사항입니다.<br /> </td> 
   <td> 오퍼 엔진(상호 작용)의 제어 인스턴스에 설치할 패키지입니다. <a href="../../interaction/using/distributed-architectures.md#packages-configuration">자세한 내용</a> </td> 
   <td> 마케팅<br /> </td>  
  </tr> 
  <tr> 
   <td> 실행 인스턴스용 오퍼 엔진. 선택 사항입니다.<br /> </td> 
   <td> 오퍼 엔진의 실행 인스턴스(상호 작용)에 설치할 패키지입니다. <a href="../../interaction/using/distributed-architectures.md">자세한 내용</a> </td> 
   <td> 중간, 실행 <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> 소셜 네트워크(소셜 마케팅) <br /> </td> 
   <td> Adobe Campaign을 Twitter 및 Facebook과 동기화합니다. <a href="../../social/using/about-social-marketing.md">자세한 내용</a> <br /> </td> 
   <td> 모두</td> 
  </tr> 
  <tr> 
   <td> 트랜잭션 메시지 제어(메시지 센터 - 제어)<br /> </td> 
   <td> 정보 시스템에서 트리거된 이벤트에서 생성된 트리거 메시지를 관리합니다. 선택 사항입니다. <a href="../../message-center/using/about-transactional-messaging.md">자세한 내용</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션 메시지 실행(메시지 센터 - 실행) <br /> </td> 
   <td> 가용성을 높이고 로드 관리를 향상시킵니다. 선택 사항입니다. <a href="../../message-center/using/about-transactional-messaging.md">자세한 내용</a><br /> </td> 
   <td> 실행<br /> </td>
  </tr> 
  <tr> 
   <td> LINE 채널<br /> </td> 
   <td> Adobe Campaign에서 LINE 채널을 사용하여 배달을 전송합니다. 선택 사항입니다. 트랜잭션 메시지(메시지 센터 패키지)는 필수입니다. <a href="../../delivery/using/line-channel.md">자세한 내용</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
  <tr> 
   <td> 다이렉트 메일 채널<br /> </td> 
   <td> Adobe Campaign에서 DM 채널을 사용하여 배달을 보냅니다. 선택 사항입니다. <a href="../../delivery/using/about-direct-mail-channel.md">자세한 내용</a><br /> </td> 
   <td> 모두<br /> </td>
  </tr> 
  <tr> 
   <td> 모바일 채널(SMS) <br /> </td> 
   <td> Adobe Campaign에서 모바일/SMS 채널을 사용하여 배달을 전송합니다. 선택 사항입니다. <a href="../../delivery/using/sms-channel.md">자세한 내용</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
   <tr> 
   <td> 전화 채널<br /> </td> 
   <td> Adobe Campaign에서 전화 채널을 사용하여 배달물을 전송합니다. 콜 센터에 사용됩니다. 선택 사항입니다. <a href="../../delivery/using/communication-channels.md">자세한 내용</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
  <tr> 
   <td> 모바일 앱 채널<br /> </td> 
   <td> Adobe Campaign 플랫폼을 사용하여 앱을 통해 iOS 및 Android 터미널에 개인화된 알림을 보냅니다. 선택 사항입니다. <a href="../../delivery/using/about-mobile-app-channel.md">자세한 내용</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
  <tr> 
   <td> 콘텐츠 관리자<br /> </td> 
   <td> 반복적인 뉴스레터 또는 웹 사이트를 만든 다음 메시지를 확인하고 게시합니다. <a href="../../delivery/using/about-content-management.md">자세한 내용</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> 온라인 설문 조사(설문 조사 관리자)<br /> </td> 
   <td> 온라인 양식을 만들고 관리하여 프로필 정보를 추가하거나 수정하고 구독, 구독 취소 또는 대회 참가 양식을 만듭니다. 선택 사항입니다. <a href="../../web/using/about-surveys.md">자세한 내용</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 마케팅 분석<br /> </td> 
   <td> 데이터를 분석 및 측정하고, 통계를 계산하며, 보고서 생성 및 계산을 단순화 및 최적화할 수 있습니다. 또한 보고서를 만들고 타겟 모집단을 만들 수도 있습니다. 선택 사항입니다. <a href="../../reporting/using/about-cubes.md">자세한 내용</a><br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 반응 관리자<br /> </td> 
   <td> 마케팅 캠페인의 성공 및 수익성을 측정하거나 모든 커뮤니케이션 채널에 대한 제안을 제공합니다.  선택 사항입니다. <a href="../../campaign/using/about-response-manager.md">자세한 내용</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 외부 데이터에 대한 액세스(Federated Data Access)<br /> </td> 
   <td> 하나 이상의 외부 데이터베이스에 저장된 정보를 처리할 수 있도록 Federated Data Access(FDA) 옵션을 제공하여 Adobe Campaign 데이터 구조를 변경하지 않고도 외부 데이터에 액세스할 수 있습니다.  선택 사항입니다. <a href="../../workflow/using/accessing-an-external-database--fda-.md">자세한 내용</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
  <tr> 
   <td> 캠페인 최적화<br /> </td> 
   <td> 회사 커뮤니케이션 정책을 준수하면서 전송 전송을 제어, 필터 및 모니터링하여 보낸 메시지가 고객의 요구 사항과 기대를 가장 잘 충족하도록 합니다. 선택 사항입니다. <a href="../../campaign/using/about-campaign-typologies.md">자세한 내용</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달 가능성 모니터링(이메일 배달 가능)<br /> </td> 
   <td> 바운싱 또는 스팸으로 표시되지 않고 수신자의 받은 편지함에 도달하는 캠페인의 성공을 측정합니다. 선택 사항입니다. <a href="../../delivery/using/about-deliverability.md">자세한 내용</a> <br /> </td> 
   <td> 모두 </td> 
  </tr> 
  <tr> 
   <td> 쿠폰 관리<br /> </td> 
   <td> 예정된 마케팅 오퍼에 추가할 쿠폰 세트를 만듭니다. 선택 사항입니다. <a href="../../delivery/using/personalized-coupons.md">자세한 내용</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 받은 편지함 렌더링(IR)<br /> </td> 
   <td> 수신될 수 있는 여러 컨텍스트로 전송된 메시지를 미리 보고 주요 데스크톱 및 응용 프로그램의 호환성을 확인할 수 있습니다. 선택 사항입니다. <a href="../../delivery/using/inbox-rendering.md">자세한 내용</a><br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 중앙/로컬 마케팅(분산 마케팅)<br /> </td> 
   <td> 중앙 개체(본사, 마케팅 부서 등) 간 협력 캠페인을 구현합니다. 및 지역 개체(판매 지점, 지역 기관 등)를 포괄적으로 포함합니다. 선택 사항입니다. <a href="../../campaign/using/about-distributed-marketing.md">자세한 내용</a><br /> </td> 
   <td> 마케팅 </td> 
  </tr> 
  <tr> 
   <td> CRM 커넥터<br /> </td> 
   <td> Adobe Campaign 플랫폼을 타사 시스템에 연결하는 다양한 CRM 커넥터를 제공합니다.  <a href="../../platform/using/crm-connectors.md">자세한 내용</a> <br /> </td> 
   <td> 마케팅</td> 
  </tr> 
  <tr> 
   <td> 웹 분석 커넥터<br /> </td> 
   <td> Adobe Campaign 및 Adobe Analytics이 웹 분석 커넥터 패키지를 통해 상호 작용할 수 있습니다. 트랜잭션 메시지(메시지 센터 패키지)와 호환되지 않습니다. <a href="../../platform/using/adobe-analytics-data-connector.md">자세한 내용</a><br /> </td> 
   <td> 마케팅 </td> 
  </tr> 
  <tr> 
   <td> AEM 통합<br /> </td> 
   <td> AEM 컨텐츠 편집 기능 및 Adobe Campaign의 전달 기능을 활용할 수 있도록 이메일 전달 컨텐츠와 양식을 Adobe Experience Manager에서 직접 관리할 수 있습니다. <a href="../../integrations/using/about-adobe-experience-manager.md">자세한 내용</a> <br /> </td> 
   <td> 마케팅</td> 
  </tr> 
  <tr> 
   <td> Adobe Experience Cloud 공유 대상 통합<br /> </td> 
   <td> Adobe Experience Cloud 솔루션 및 핵심 서비스와 대상/세그먼트를 교환하고 공유할 수 있습니다. IMS가 필요합니다. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">자세한 내용</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> Adobe Experience Cloud<br />과 통합 </td> 
   <td> 다양한 Adobe Experience Cloud 솔루션의 대상/세그먼트를 Adobe Campaign으로 가져오고 내보낼 수 있습니다. 선택 사항입니다. <a href="../../integrations/using/configuring-ims.md#installing-the-package">자세한 내용</a> </td> 
   <td> 마케팅</td> 
  </tr> 
  <tr> 
   <td> 개인 정보 보호 규정<br /> </td> 
   <td> Campaign Classic에서 개인 정보 보호를 준수하는 추가 기능을 포함합니다. <a href="https://helpx.adobe.com/kr/campaign/kb/acc-privacy.html">자세한 내용</a> <br /> </td> 
   <td> 모두</td> 
  </tr> 
  <tr> 
   <td> 중간 소싱 <br />으로 이전 </td> 
   <td> 중간 소싱 서버의 설치 및 구성과 제3자가 중간 소싱 모드로 메시지를 전송할 수 있는 인스턴스 배포에 대해 자세히 설명합니다. 선택 사항입니다. <a href="../../installation/using/mid-sourcing-server.md">자세한 내용</a> <br /> </td> 
   <td> 마케팅 </td> 
  </tr> 
  <tr> 
   <td> 중간 소싱 플랫폼<br /> </td> 
   <td> 이 구성은 호스팅된(ASP) 구성과 내부화 간에 최적의 중간 솔루션입니다. 외부 실행 구성 요소는 Adobe Campaign에서 호스팅되는 "중간 소싱" 서버에서 수행됩니다. 선택 사항입니다. <a href="../../installation/using/mid-sourcing-server.md">자세한 내용</a> <br /> </td> 
   <td> 중간 소싱 </td> 
  </tr> 
  <tr> 
   <td> AMP 지원<br /> </td> 
   <td> 새로운 대화형 AMP를 이메일 형식으로 사용하고 동적 이메일을 보낼 수 있습니다. 선택 사항입니다. <a href="../../delivery/using/defining-interactive-content.md">자세한 내용</a> <br /> </td> 
   <td> 모두 </td> 
  </tr> 
  <tr> 
   <td> ACS 커넥터<br /> </td> 
   <td> Adobe Campaign v7과 Adobe Campaign Standard의 다리 역할을 합니다. 데이터를 Campaign Standard에 자동으로 복제하여 두 애플리케이션 중 최상의 결과를 통합하는 Campaign v7의 통합 기능입니다. 선택 사항입니다. <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">자세한 내용</a> <br /> </td> 
   <td> 마케팅 </td> 
  </tr> 
 </tbody> 
</table>

### 메시지 센터 패키지 {#message-center-package}

배달 채널(이메일, 모바일 채널, 모바일 앱 채널 등)을 설치해야 합니다. 트랜잭션 메시지를 설치하기 전에(메시지 센터 패키지). 이메일 전용 메시지 센터 프로젝트를 시작하고 이후에 새 채널을 추가해야 하는 경우 다음 단계를 수행해야 합니다.

1. 패키지 가져오기 마법사( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**)를 사용하여 **모바일 채널**&#x200B;과 같은 새 채널을 설치합니다.
1. 파일( **[!UICONTROL Tools > Advanced > Import package > File]**)을 가져오고 다음을 선택합니다.

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. **[!UICONTROL XML data content to import]**&#x200B;에서 관련 채널에 해당하는 메시지 센터 배달 템플릿만 유지합니다. 예를 들어 **모바일 채널**&#x200B;을 추가한 경우 **[!UICONTROL Mobile transactional message]**(smsTriggerMessage) 템플릿에 해당하는 **entities** 요소만 유지하십시오. **모바일 앱 채널**&#x200B;을 추가한 경우 **iOS 트랜잭션 메시지** 템플릿(iosTriggerMessage) 및 **Android 트랜잭션 메시지**(androidTriggerMessage)만 유지합니다.

   ![](assets/messagecenter_install_channel.png)

>[!CAUTION]
>
>LINE 이전에 메시지 센터 패키지를 설치한 경우 LINE용 메시지 센터 배달 템플릿을 사용할 수 없습니다.

