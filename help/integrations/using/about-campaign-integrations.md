---
title: Campaign 통합 기본 정보
description: 다른 Adobe 솔루션을 사용하여 다양한 기능을 Campaign과 결합할 수 있습니다.
page-status-flag: never-activated
uuid: 087abdf0-b4b2-45e6-be21-b03bf85ddf83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: campaign-integrations
discoiquuid: 0af1fd96-48ef-43c9-a03b-0f9a6e0e02fe
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 10%

---


# Campaign 통합 기본 정보 {#about-campaign-integrations}

Adobe Experience Cloud은 강력한 핵심 서비스의 공통 세트를 갖춘 공통 데이터 플랫폼을 기반으로 구축된 포괄적인 동급 최강의 통합 솔루션 세트입니다.

Adobe Campaign 솔루션과 [Adobe Experience Cloud 솔루션](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) 및 [핵심 서비스](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html)간의 기능 통합에 대해 자세히 알아보십시오. 그런 다음 솔루션 구현을 현대화하고 Experience Cloud을 구현하여 고객 속성 및 대상과 같은 기능을 사용할 수 있습니다.

Adobe Campaign과 통합할 수 있는 Adobe 솔루션 및 핵심 서비스 및 관련 설명서는 [이 섹션에서 제공됩니다](#experience-cloud-integrations).

![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>이러한 통합 대부분은 Adobe ID(IMS)를 통해 로그인해야 합니다. For more on this implementation, refer to [this page](../../integrations/using/about-adobe-id.md).
>
>IMS 구현은 매우 복잡한 과정이며 오래 걸릴 수 있습니다. 이는 Adobe 기술 관리자들에게 엄격히 지정되어 있습니다.

## 솔루션 연결 {#working-with-experience-cloud-solutions}

환경에 따라 여러 솔루션을 Adobe Experience Cloud에 연결할 수 있습니다. 이 지표는 조직으로 연결됩니다. An **organization** is the entity that enables an administrator to configure groups and users, and to control single sign-on in the Experience Cloud. 조직은 모든 Experience Cloud 제품 및 솔루션을 포괄하는 로그인 회사와 같은 기능을 합니다. 대부분의 경우 조직은 회사의 이름입니다. 하지만 회사는 여러 조직을 가질 수 있습니다.

조직 관리 및 Adobe Experience Cloud 계정 연결은 [Adobe Experience Cloud 도움말 포털에 자세히 설명되어 있습니다](https://docs.adobe.com/content/help/ko-KR/core-services/interface/manage-users-and-products/organizations.html).

>[!CAUTION]
>
>Adobe Campaign을 새로 설치하거나 기존 설치를 Adobe Experience Cloud과 통합하면 [Experience Cloud ID 서비스가](https://docs.adobe.com/content/help/en/id-service/using/home.html) 활성화됩니다. 이 서비스는 Adobe Campaign이 먼저 사용하는 영구 쿠키를 추적 기능으로 대체합니다.
>
>그러면 추적 로그를 생성하는 수신자에게 고유 방문자 ID가 할당됩니다. 이 ID는 표의 **[!UICONTROL Requester UUID (@sourceID)]** 필드에 **[!UICONTROL nms:trackingLogRcp]** 저장됩니다. 방문자 ID 서비스가 구현되기 전에 존재했던 수신자의 추적 데이터를 더 이상 사용할 수 없습니다.
>
>그러면 ID가 동일한 [CNAME의 다른 Adobe Experience Cloud 솔루션에서 인식됩니다](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/cname.html).

## Experience Cloud 통합 {#experience-cloud-integrations}

다음 표는 사용 가능한 Experience Cloud 통합 문서에 대한 액세스를 제공합니다.

<table> 
 <thead> 
  <tr> 
   <th> 솔루션 및 핵심 서비스<br /> </th> 
   <th> 사용 사례<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe 실시간 고객 데이터 플랫폼</strong><br /> </td> 
   <td> Adobe Campaign 및 Adobe 실시간 고객 데이터 플랫폼 간의 통합을 통해 세그먼트 데이터를 공유하고 대상을 Adobe Campaign으로 가져올 수 있습니다.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">캠페인 - Adobe 실시간 고객 데이터 플랫폼 통합에 대해 자세히</a> 알아보십시오.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS - Adobe ID</strong><br /> </td> 
   <td> 다른 Adobe Experience Cloud 솔루션과 동일한 Adobe ID을 사용하여 Adobe Campaign에 연결할 수 있습니다.<br /> Adobe Experience Cloud 통합, 특히 핵심 서비스와 연결된 특정 기능을 사용하려면 로그인하는 데 Adobe ID을 사용해야 합니다.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Adobe Campaign과 함께 Adobe ID을 구현하는 방법에 대해 자세히</a> 알아보십시오.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Allows you to create email contents or forms mapped to the Adobe Campaign database directly in <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Adobe Campaign에 대한 자세한</a> 내용 - Adobe Experience Manager 통합</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Allows you to insert images that are dynamically computed by <strong>Adobe Target</strong> when the email created and sent by Adobe Campaign is opened.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Adobe Campaign에 대한 자세한</a> 내용 - Adobe Target 통합</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>People 코어 서비스</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> 사용자가 사용하는 Adobe Experience Cloud 솔루션과 코어 간에 대상을 공유할 수 있습니다.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Adobe Campaign에 대한 자세한</a> 내용 - 사람 코어 서비스 및 Adobe Audience Manager 통합</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>자산 핵심 서비스</strong><br /> </td> 
   <td> Adobe Experience Cloud 라이브러리의 자산을 Adobe Campaign에서 만든 이메일 및 랜딩 페이지에 삽입할 수 있습니다.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Adobe Campaign에 대한 자세한</a> 내용 - 자산 핵심 서비스 통합</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Allows you to insert assets from your <strong>AEM Assets</strong> library into emails and landing pages created in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Adobe Campaign에 대한 자세한</a> 내용 - AEM Assets 통합</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud 트리거</strong><br /> </td> 
   <td> Integration between <strong>Triggers core service</strong> and Adobe Campaign allows you to send personalized emails to your customers as a reaction to specific behaviors that are tracked on your website by Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/kr/campaign/kb/triggers-and-campaign.html">Adobe Campaign에 대한 자세한</a> 내용 - Experience Cloud 트리거 통합</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - 데이터 커넥터</strong><br /> </td> 
   <td> <strong>데이터 커넥터</strong> (이전의 Adobe Genesis)을 사용하면 Adobe Campaign 및 Adobe Analytics이 이메일 캠페인 이후 사용자 동작과 관련된 세그먼트를 통해 상호 작용할 수 있습니다. 반대로, 이 엔진은 Adobe Campaign이 Adobe Analytics - 데이터 커넥터로 제공하는 이메일 캠페인의 지표와 속성을 전송합니다.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">캠페인 - 데이터 커넥터 통합에 대해 자세히</a> 알아보십시오.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

