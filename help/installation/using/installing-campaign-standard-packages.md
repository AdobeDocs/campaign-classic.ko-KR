---
product: campaign
title: Campaign Classic 기본 제공 패키지 설치
description: Campaign 기본 제공 패키지를 설치하는 방법 알아보기
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: 035297523c25061f28751c28df86d562f40f45ea
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 6%

---

# Campaign Classic 기본 제공 패키지 설치{#installing-campaign-standard-packages}

![](../../assets/v7-only.svg)

## 기본 제공 패키지 기본 정보 {#campaign-standard-packages}

기본 제공 패키지에는 사용자의 요구 사항과 계약에 따라 설치할 수 있는 기능 세트가 들어 있습니다. Campaign 기본 제공 패키지의 전체 목록은 아래에서 확인할 수 있습니다.

>[!CAUTION]
>
>라이선스 계약에 언급된 옵션에 해당하는 패키지만 설치할 수 있습니다.
>
>새 패키지를 설치하면 모든 플랫폼에 영향을 줄 수 있습니다. 최종 배포 전에 테스트 및 유효성 검사를 수행해야 합니다.
>
>패키지가 설치되면 제거할 수 없습니다.
>
>호스팅 또는 하이브리드 고객은 Adobe에 연락하여 새 기본 제공 패키지를 배포합니다.

기본 제공 패키지를 설치하려면 다음을 수행하십시오.

1. 에서 패키지 가져오기 마법사에 액세스 **[!UICONTROL Tools > Advanced > Import package]** ( Adobe Campaign 클라이언트 콘솔) 아래에 그룹화됩니다.
1. **[!UICONTROL Install a standard package]**&#x200B;을(를) 선택합니다.
1. 패키지 목록에서 설치할 패키지를 확인합니다.
   >[!NOTE]
   >
   >패키지가 회색으로 표시되면 이미 설치되어 있거나 해당 인스턴스와 호환되지 않음을 의미합니다. 호환성은 아래 표에 자세히 설명되어 있습니다.
1. 클릭 **[!UICONTROL Next]**, 그런 다음 **[!UICONTROL Start]** 패키지 설치를 시작하려면 다음을 수행하십시오.

   패키지가 설치되면 진행률 표시줄이 표시됩니다 **100%** 설치 로그에 다음 메시지가 표시됩니다. **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** 설치 창

이제 패키지가 설치되었습니다.

### 기본 패키지 목록 {#list-of-standard-packages}

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
   <td> 게재<br /> </td> 
   <td> 메시지를 보낼 때 발생하는 게재 및 최종 문제를 모니터링합니다. <a href="../../delivery/using/about-delivery-monitoring.md">자세히 알아보기</a><br /> </td> 
   <td> 모두</td> 
  </tr> 
  <tr> 
   <td> 마케팅 캠페인(캠페인)<br /> </td> 
   <td> 커뮤니케이션 및 마케팅 캠페인을 정의, 최적화, 실행 및 분석할 수 있습니다. <a href="../../campaign/using/designing-marketing-campaigns.md">추가 정보</a><br /> </td> 
   <td> 마케팅</td>
  </tr> 
  <tr> 
   <td> 마케팅 리소스(MRM)<br /> </td> 
   <td> 작업, 예산 및 마케팅 리소스에 대한 관리 및 추적을 제공하여 협업 모드에서 마케팅 작업을 제어합니다. <a href="../../mrm/using/about-marketing-resource-management.md">추가 정보</a> <br /> </td> 
   <td> 마케팅</td> 
  </tr> 
  <tr> 
   <td> 오퍼 엔진(상호 작용)<br /> </td> 
   <td> 단일 또는 여러 개의 수정된 오퍼로 설정하여 지정된 연락처(고객 또는 타겟)와의 상호 작용 중에 실시간으로 응답합니다.  선택 사항입니다. <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">추가 정보</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
  <tr> 
   <td> 실행 인스턴스를 사용하여 오퍼 엔진 제어. 선택 사항입니다.<br /> </td> 
   <td> 오퍼 엔진의 제어 인스턴스에 설치할 패키지(상호 작용) <a href="../../interaction/using/distributed-architectures.md#packages-configuration">추가 정보</a> </td> 
   <td> 마케팅<br /> </td>  
  </tr> 
  <tr> 
   <td> 실행 인스턴스에 대한 오퍼 엔진입니다. 선택 사항입니다.<br /> </td> 
   <td> 오퍼 엔진의 실행 인스턴스에 설치할 패키지(상호 작용) <a href="../../interaction/using/distributed-architectures.md">추가 정보</a> </td> 
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
   <td> Adobe Campaign을 Twitter 및 Facebook과 동기화합니다. <a href="../../social/using/about-social-marketing.md">추가 정보</a> <br /> </td> 
   <td> 모두</td> 
  </tr> 
  <tr> 
   <td> 트랜잭션 메시지 제어(메시지 센터 - 제어)<br /> </td> 
   <td> 정보 시스템에서 트리거된 이벤트에서 생성된 트리거 메시지를 관리합니다. 선택 사항입니다. <a href="../../message-center/using/about-transactional-messaging.md">추가 정보</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션 메시지 실행(메시지 센터 - 실행) <br /> </td> 
   <td> 가용성을 높이고 로드 관리를 강화합니다. 선택 사항입니다. <a href="../../message-center/using/about-transactional-messaging.md">추가 정보</a><br /> </td> 
   <td> 실행<br /> </td>
  </tr> 
  <tr> 
   <td> LINE 채널<br /> </td> 
   <td> Adobe Campaign과 함께 LINE 채널을 사용하여 게재를 보냅니다. 선택 사항입니다. 트랜잭션 메시지(메시지 센터 패키지)는 필수입니다. <a href="../../delivery/using/line-channel.md">추가 정보</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
  <tr> 
   <td> DM 채널<br /> </td> 
   <td> Adobe Campaign에서 DM 채널을 사용하여 게재를 보냅니다. 선택 사항입니다. <a href="../../delivery/using/about-direct-mail-channel.md">추가 정보</a><br /> </td> 
   <td> 모두<br /> </td>
  </tr> 
  <tr> 
   <td> 모바일 채널(SMS) <br /> </td> 
   <td> Adobe Campaign에서 모바일/SMS 채널을 사용하여 게재를 보냅니다. 선택 사항입니다. <a href="../../delivery/using/sms-channel.md">추가 정보</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
   <tr> 
   <td> 전화 채널<br /> </td> 
   <td> Adobe Campaign에서 전화 채널을 사용하여 게재를 보냅니다. 콜 센터에 사용됩니다. 선택 사항입니다. <a href="../../delivery/using/communication-channels.md">추가 정보</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
  <tr> 
   <td> 모바일 앱 채널<br /> </td> 
   <td> Adobe Campaign 플랫폼을 사용하여 앱을 통해 iOS 및 Android 단말기로 개인화된 알림을 보냅니다. 선택 사항입니다. <a href="../../delivery/using/about-mobile-app-channel.md">추가 정보</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
  <tr> 
   <td> 컨텐츠 관리자<br /> </td> 
   <td> 반복 뉴스레터 또는 웹 사이트를 만든 다음 메시지를 확인하고 게시합니다. <a href="../../delivery/using/about-content-management.md">추가 정보</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> 온라인 설문 조사(설문 조사 관리자)<br /> </td> 
   <td> 온라인 양식을 만들고 관리하여 프로필 정보를 추가 또는 수정하고 구독하거나 구독 취소하거나 대회 시작 양식을 만들 수 있습니다. 선택 사항입니다. <a href="../../surveys/using/about-surveys.md">추가 정보</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> 데이터를 분석 및 측정하고, 통계를 계산하며, 보고서 작성 및 계산을 간소화 및 최적화할 수 있습니다. 또한 보고서를 만들고 대상 모집단을 만들 수도 있습니다. 선택 사항입니다. <a href="../../reporting/using/about-cubes.md">추가 정보</a><br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 반응 관리자<br /> </td> 
   <td> 마케팅 캠페인의 성공 및 수익성을 측정하거나 모든 커뮤니케이션 채널에 대한 제안 위치를 제공합니다.  선택 사항입니다. <a href="../../response/using/about-response-manager.md">추가 정보</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 외부 데이터에 액세스(페더레이션 데이터 액세스)<br /> </td> 
   <td> 하나 이상의 외부 데이터베이스에 저장된 정보를 처리하기 위해 Adobe Campaign 데이터 구조를 변경하지 않고 외부 데이터에 액세스할 수 있는 FDA(Federated Data Access) 옵션을 제공합니다.  선택 사항입니다. <a href="../../workflow/using/accessing-an-external-database--fda-.md">추가 정보</a> <br /> </td> 
   <td> 모두<br /> </td> 
  </tr> 
  <tr> 
   <td> 캠페인 최적화<br /> </td> 
   <td> 게재 전송을 제어, 필터링 및 모니터링하여 회사 커뮤니케이션 정책과 함께 전송된 메시지가 고객의 요구 사항과 기대를 가장 잘 충족하도록 합니다. 선택 사항입니다. <a href="../../campaign-opt/using/about-campaign-typologies.md">추가 정보</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 게재 기능 모니터링(전자 메일 게재 기능)<br /> </td> 
   <td> 바운스 방지 또는 스팸으로 표시되지 않고 수신자의 받은 편지함에 도달하는 캠페인의 성공을 측정합니다. 선택 사항입니다. <a href="../../delivery/using/about-deliverability.md">추가 정보</a> <br /> </td> 
   <td> 모두 </td> 
  </tr> 
  <tr> 
   <td> 쿠폰 관리<br /> </td> 
   <td> 예정된 마케팅 오퍼에 추가할 쿠폰 세트를 만듭니다. 선택 사항입니다. <a href="../../delivery/using/personalized-coupons.md">추가 정보</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 받은 편지함 렌더링(IR)<br /> </td> 
   <td> 수신될 수 있는 다른 컨텍스트에서 전송된 메시지를 미리 보고 주요 데스크톱 및 응용 프로그램의 호환성을 확인할 수 있습니다. 선택 사항입니다. <a href="../../delivery/using/inbox-rendering.md">추가 정보</a><br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> 중앙/로컬 마케팅(분산 마케팅)<br /> </td> 
   <td> 중앙 엔터티(본사, 마케팅 부서 등) 간의 협력 캠페인을 구현합니다. 및 지역 개체(영업 지점, 지역 기관 등)를 참조하십시오. 선택 사항입니다. <a href="../../distributed/using/about-distributed-marketing.md">추가 정보</a><br /> </td> 
   <td> 마케팅 </td> 
  </tr> 
  <tr> 
   <td> CRM 커넥터<br /> </td> 
   <td> Adobe Campaign 플랫폼을 타사 시스템에 연결하는 다양한 CRM 커넥터를 제공합니다.  <a href="../../platform/using/crm-connectors.md">추가 정보</a> <br /> </td> 
   <td> 마케팅</td> 
  </tr> 
  <tr> 
   <td> 웹 Analytics 커넥터<br /> </td> 
   <td> Adobe Campaign 및 Adobe Analytics이 Web Analytics 커넥터 패키지를 통해 상호 작용할 수 있습니다. 트랜잭션 메시지(메시지 센터 패키지)와 호환되지 않습니다. <a href="../../platform/using/adobe-analytics-connector.md">추가 정보</a><br /> </td> 
   <td> 마케팅 </td> 
  </tr> 
  <tr> 
   <td> AEM 통합<br /> </td> 
   <td> AEM 콘텐츠 편집 기능 및 Adobe Campaign 게재 기능을 활용할 수 있도록 이메일 게재 콘텐츠 및 양식을 Adobe Experience Manager에서 직접 관리할 수 있습니다. <a href="../../integrations/using/about-adobe-experience-manager.md">추가 정보</a> <br /> </td> 
   <td> 마케팅</td> 
  </tr> 
  <tr> 
   <td> Adobe Experience Cloud 공유 대상 통합<br /> </td> 
   <td> Adobe Experience Cloud 솔루션 및 핵심 서비스와 대상자/세그먼트를 교환하고 공유할 수 있습니다. IMS 필요 <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">추가 정보</a> <br /> </td> 
   <td> 마케팅<br /> </td> 
  </tr> 
  <tr> 
   <td> Adobe Experience Cloud과 통합<br /> </td> 
   <td> 다양한 Adobe Experience Cloud 솔루션의 대상/세그먼트를 Adobe Campaign으로 가져오고 내보낼 수 있습니다. 선택 사항입니다. <a href="../../integrations/using/configuring-ims.md#installing-the-package">추가 정보</a> </td> 
   <td> 마케팅</td> 
  </tr> 
  <tr> 
   <td> 개인 정보 보호 규정<br /> </td> 
   <td> Campaign Classic의 개인 정보 보호 규정을 준수하는 데 도움이 되는 추가 기능을 포함합니다. <a href="https://helpx.adobe.com/kr/campaign/kb/acc-privacy.html">추가 정보</a> <br /> </td> 
   <td> 모두</td> 
  </tr> 
  <tr> 
   <td> 중간 소싱으로 전송 <br /> </td> 
   <td> 중간 소싱 서버의 설치 및 구성과 타사에서 중간 소싱 모드로 메시지를 보낼 수 있는 인스턴스의 배포에 대해 자세히 설명합니다. 선택 사항입니다. <a href="../../installation/using/mid-sourcing-server.md">추가 정보</a> <br /> </td> 
   <td> 마케팅 </td> 
  </tr> 
  <tr> 
   <td> 중간 소싱 플랫폼<br /> </td> 
   <td> 이 구성은 호스팅(ASP) 구성과 내부 구성 간의 최적 중간 솔루션입니다. 외향 실행 구성 요소는 Adobe Campaign에서 호스팅되는 "중간 소싱" 서버에서 수행됩니다. 선택 사항입니다. <a href="../../installation/using/mid-sourcing-server.md">추가 정보</a> <br /> </td> 
   <td> 중간 소싱 </td> 
  </tr> 
  <tr> 
   <td> AMP 지원<br /> </td> 
   <td> 새로운 대화형 AMP를 이메일 형식에 사용하고 다이내믹 이메일을 보낼 수 있습니다. 선택 사항입니다. <a href="../../delivery/using/defining-interactive-content.md">추가 정보</a> <br /> </td> 
   <td> 모두 </td> 
  </tr> 
  <tr> 
   <td> ACS Connector<br /> </td> 
   <td> Adobe Campaign v7와 Adobe Campaign Standard을 브리짓합니다. Campaign v7의 통합 기능으로 데이터를 Campaign Standard에 자동으로 복제하여 두 애플리케이션 중 최고의 성능을 제공합니다. 선택 사항입니다. <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">추가 정보</a> <br /> </td> 
   <td> 마케팅 </td> 
  </tr> 
 </tbody> 
</table>

### 메시지 센터 패키지 {#message-center-package}

게재 채널(이메일, 모바일 채널, 모바일 앱 채널, LINE 등)을 설치해야 합니다. 트랜잭션 메시지(메시지 센터 패키지)를 설치하기 전에 이메일 전용 메시지 센터 프로젝트를 시작하고 나중에 새 채널을 추가해야 하는 경우 다음 단계를 수행해야 합니다.

1. 새 채널을 설치합니다(예: **모바일 채널**&#x200B;패키지 가져오기 마법사 사용( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. 파일 가져오기( **[!UICONTROL Tools > Advanced > Import package > File]**).

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. 에서 **[!UICONTROL XML data content to import]**&#x200B;를 설정하는 경우 관련 채널에 해당하는 메시지 센터 게재 템플릿만 유지합니다. 예를 들어, **모바일 채널**&#x200B;만 유지합니다 **개체** 에 해당하는 요소 **[!UICONTROL Mobile transactional message]** (smsTriggerMessage) 템플릿을 참조하십시오. 를 추가한 경우 **모바일 앱 채널**&#x200B;만 유지합니다 **iOS 트랜잭션 메시지** 템플릿(iosTriggerMessage) 및 **Android 트랜잭션 메시지** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)


### [!DNL LINE] 채널 설정{#line-package}

을(를) 설정하려면 다음을 수행하십시오 [!DNL LINE] channel을 먼저 설치해야 합니다. [!DNL LINE] 패키지.

중간 소싱 구성 컨텍스트에서 다음을 수행해야 합니다.

* 설치 [!DNL LINE] 마케팅 및 MID 인스턴스 둘 다에 패키지

* 설정 [!DNL LINE] 게재 모드를 변경하여 mid 인스턴스를 가리키도록 mkt 인스턴스의 외부 계정입니다. [자세히 알아보기](../../delivery/using/line-channel.md#configure-line-external)

* 설정 [!DNL LINE] MID 인스턴스에 있는 외부 계정의 자격 증명입니다.

>[!CAUTION]
>
>에 대한 메시지 센터 게재 템플릿 [!DNL LINE] 이전에 메시지 센터 패키지를 설치한 경우에는 채널을 사용할 수 없습니다 [!DNL LINE].