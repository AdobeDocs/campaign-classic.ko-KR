---
product: campaign
title: Campaign 통합 정보
description: 다른 Adobe 솔루션을 사용하여 다양한 기능을 Campaign과 결합할 수 있습니다
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 12%

---

# Adobe Campaign 통합 시작 {#about-campaign-integrations}



Adobe Experience Cloud은 강력한 핵심 서비스의 공통 세트를 사용하여 공통 데이터 플랫폼에 구축된 포괄적인 최고급 통합 솔루션 세트입니다.

Adobe Campaign과 [Adobe Experience Cloud 솔루션](https://experienceleague.adobe.com/docs/core-services/interface/marketing-cloud-integrations.html) 및 [핵심 서비스](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html). 그런 다음 솔루션 구현을 현대화하고 Experience Cloud을 구현하여 고객 특성 및 대상과 같은 기능을 사용할 수 있습니다.

![](assets/ExCloud-solutions.png)

Adobe Campaign과 통합할 수 있는 Adobe 솔루션 및 핵심 서비스의 전체 목록은 관련 설명서뿐만 아니라 [이 섹션](#experience-cloud-integrations).

>[!CAUTION]
>
>이러한 통합의 대부분은 Adobe ID을 통해 로그인하려면 IMS(Adobe Identity Management System)를 구현해야 합니다. [이 페이지에서 자세히 알아보십시오](../../integrations/using/about-adobe-id.md).

## 솔루션 연결 {#working-with-experience-cloud-solutions}

여러 솔루션을 Adobe Experience Cloud에 연결할 수 있습니다. 다음 **조직** 관리자가 그룹과 사용자를 구성하고, Adobe Experience Cloud에서 SSO(Single Sign-On)를 제어할 수 있도록 해주는 고객 엔티티입니다. 조직은 모든 Experience Cloud 제품 및 솔루션을 포괄하는 로그인 회사와 같은 역할을 합니다. 대부분의 경우 조직은 회사의 이름입니다. 하지만 회사는 여러 조직을 가질 수 있습니다.

조직 관리 및 Adobe Experience Cloud 계정 연결은 [Adobe Experience Cloud 도움말 포털](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html).

## ID 및 쿠키 관리 {#id-and-cookies}

Adobe Campaign을 설치하거나 기존 설치를 Adobe Experience Cloud과 통합할 때 [Adobe Experience Cloud Identity 서비스](https://experienceleague.adobe.com/docs/id-service/using/home.html) 이 활성화되어 있습니다. 이 서비스는 추적 기능에 대해 Adobe Campaign에서 먼저 그리고 가장 먼저 사용하는 영구 쿠키를 대체합니다.

Adobe Experience Cloud Identity 서비스는 Experience Cloud의 모든 솔루션에서 방문자를 식별하는 범용 영구 ID를 제공합니다.

추적 로그를 생성하는 수신자에게 고유 방문자 ID가 지정됩니다. 이 ID는 **[!UICONTROL Requester UUID (@sourceID)]** 필드 **[!UICONTROL nms:trackingLogRcp]** 테이블. **방문자 ID 서비스가 구현되기 전에 존재했던 수신자의 추적 데이터는 더 이상 사용할 수 없습니다**.

그러면 ID가 동일한 CNAME의 다른 Adobe Experience Cloud 솔루션에서 인식됩니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/cname.html)

## Experience Cloud 통합 {#experience-cloud-integrations}

다음 표에서는 사용 가능한 Experience Cloud 통합 문서에 대한 액세스 권한을 제공합니다.

<table> 
 <thead> 
  <tr> 
   <th> 솔루션 및 핵심 서비스<br /> </th> 
   <th> 사용 사례<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Real-time Customer Data Platform(RTCDP)</strong><br /> </td> 
   <td> Adobe Campaign과 Adobe Real-time Customer Data Platform(RTCDP) 간의 통합을 통해 세그먼트 데이터를 공유하고 Adobe Campaign에 대상을 가져올 수 있습니다.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">추가 정보</a> 캠페인 기본 정보 - Adobe Real-time Customer Data Platform 통합.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS(Identity Management 시스템) Adobe - Adobe ID</strong><br /> </td> 
   <td> 다른 Adobe Experience Cloud 솔루션과 동일한 Adobe ID으로 Adobe Campaign에 연결할 수 있습니다.<br /> Adobe Experience Cloud 통합, 특히 핵심 서비스에 연결된 특정 기능(예: Core Services)을 사용하려면 로그인하는 데 Adobe ID을 사용해야 합니다.<br /> <p><a href="../../integrations/using/about-adobe-id.md">추가 정보</a> Adobe Campaign을 사용한 Adobe ID 구현 기본 정보.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> 에서 직접 Adobe Campaign 데이터베이스에 매핑된 이메일 콘텐츠 또는 양식을 만들 수 있습니다 <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">추가 정보</a> Adobe Campaign 정보 - Adobe Experience Manager 통합.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> 동적으로 계산된 이미지를 삽입할 수 있습니다 <strong>Adobe Target</strong> Adobe Campaign에서 만들고 보낸 이메일이 열려 있을 때.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">추가 정보</a> Adobe Campaign 정보 - Adobe Target 통합.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>사용자 핵심 서비스</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> 사용하는 Adobe Experience Cloud 솔루션과 코어 간에 대상을 공유할 수 있습니다.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">추가 정보</a> Adobe Campaign 정보 - 사용자 핵심 서비스 및 Adobe Audience Manager 통합</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>자산 핵심 서비스</strong><br /> </td> 
   <td> Adobe Experience Cloud 라이브러리의 자산을 Adobe Campaign에서 만든 이메일 및 랜딩 페이지에 삽입할 수 있습니다.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">추가 정보</a> Adobe Campaign 기본 정보 - Assets 핵심 서비스 통합</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> 에서 자산을 삽입할 수 있습니다 <strong>AEM Assets</strong> 라이브러리는 Adobe Campaign에서 만든 이메일 및 랜딩 페이지에 연결됩니다.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">추가 정보</a> Adobe Campaign 정보 - AEM Assets 통합.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud 트리거</strong><br /> </td> 
   <td> 통합 <strong>코어 서비스 트리거</strong> 및 Adobe Campaign을 사용하면 Adobe Analytics이 웹 사이트에서 특정 행동을 추적하면 이에 대한 응답으로 고객에게 개인화된 이메일을 보낼 수 있습니다.<br /> <p><a href="https://helpx.adobe.com/kr/campaign/kb/triggers-and-campaign.html">추가 정보</a> Adobe Campaign 정보 - Experience Cloud 트리거 통합.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics 커넥터</strong><br /> </td> 
   <td> <strong>Adobe Analytics 커넥터</strong> Adobe Campaign 및 Adobe Analytics이 이메일 캠페인 이후의 사용자 동작과 관련된 세그먼트를 상호 작용할 수 있습니다. 반대로 Adobe Campaign에서 게재하는 이메일 캠페인의 지표와 특성은 Adobe Analytics로 보냅니다. <br /> <p><a href="../../platform/using/adobe-analytics-connector.md">추가 정보</a> campaign 정보 - Analytics 커넥터 통합.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
