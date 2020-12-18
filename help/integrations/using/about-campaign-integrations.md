---
solution: Campaign Classic
product: campaign
title: Campaign 통합 기본 정보
description: 다른 Adobe 솔루션을 사용하여 다양한 기능을 Campaign과 결합할 수 있습니다.
audience: integrations
content-type: reference
topic-tags: campaign-integrations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 9%

---


# Adobe Campaign 통합 시작 {#about-campaign-integrations}

Adobe Experience Cloud은 강력한 핵심 서비스의 공통 세트를 사용하여 공통 데이터 플랫폼을 기반으로 구축된 포괄적인 최고급 통합 솔루션 세트입니다.

Adobe Campaign 및 [Adobe Experience Cloud 솔루션](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) 및 [핵심 서비스](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html) 간에 사용할 수 있는 기능 통합에 대해 알아봅니다. 그런 다음 솔루션 구현을 현대화하고 Experience Cloud을 구현하여 고객 속성 및 대상과 같은 기능을 사용할 수 있습니다.

![](assets/ExCloud-solutions.png)

Adobe Campaign과 통합할 수 있는 Adobe 솔루션 및 핵심 서비스의 전체 목록과 관련 설명서는 [이 섹션](#experience-cloud-integrations)에서 제공됩니다.

>[!CAUTION]
>
>이러한 통합 기능의 대부분은 Adobe ID을 통해 로그인하려면 IMS(Adobe Identity Management System)를 구현해야 합니다. [이 페이지에서 자세히 알아보십시오](../../integrations/using/about-adobe-id.md).


## 솔루션 연결 {#working-with-experience-cloud-solutions}

여러 솔루션을 Adobe Experience Cloud에 연결할 수 있습니다. **조직**&#x200B;은 관리자가 그룹과 사용자를 구성하고 Adobe Experience Cloud에서 SSO(Single Sign-On)를 제어할 수 있도록 하는 고객 엔티티입니다. 조직은 모든 Experience Cloud 제품 및 솔루션을 포괄하는 로그인 회사와 같은 역할을 합니다. 대부분의 경우 조직은 회사의 이름입니다. 하지만 회사는 여러 조직을 가질 수 있습니다.

조직 관리 및 Adobe Experience Cloud 계정 연결은 [Adobe Experience Cloud 도움말 포털](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html)에 자세히 설명되어 있습니다.

## ID 및 쿠키 관리 {#id-and-cookies}

Adobe Campaign을 설치하거나 기존 설치를 Adobe Experience Cloud과 통합할 때 [Adobe Experience Cloud Identity Service](https://docs.adobe.com/content/help/en/id-service/using/home.html)가 활성화됩니다. 이 서비스는 Adobe Campaign이 먼저 사용하는 영구적 쿠키를 추적 기능으로 대체합니다.

Adobe Experience Cloud ID 서비스(ID 서비스)는 Experience Cloud의 모든 솔루션에서 방문자를 식별하는 범용 영구 ID를 제공합니다.

추적 로그를 생성하는 수신자에게 고유 방문자 ID가 할당됩니다. 이 ID는 **[!UICONTROL nms:trackingLogRcp]** 테이블의 **[!UICONTROL Requester UUID (@sourceID)]** 필드에 저장됩니다. **방문자 ID 서비스가 구현되기 전에 존재했던 수신자의 추적 데이터를 더 이상 사용할 수 없습니다**.

그러면 ID가 동일한 [CNAME](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/cname.html)의 다른 Adobe Experience Cloud 솔루션에서 인식됩니다.

## Experience Cloud 통합 {#experience-cloud-integrations}

다음 표에서는 사용 가능한 Experience Cloud 통합 문서에 대한 액세스를 제공합니다.

<table> 
 <thead> 
  <tr> 
   <th> 솔루션 및 핵심 서비스<br /> </th> 
   <th> 사용 사례<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe 실시간 고객 데이터 플랫폼(RTCDP)</strong><br /> </td> 
   <td> Adobe Campaign과 Adobe RTCDP(실시간 고객 데이터 플랫폼) 간의 통합을 통해 세그먼트 데이터를 공유하고 Adobe Campaign으로 대상을 가져올 수 있습니다.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">캠페인 </a> - 실시간 고객 데이터 플랫폼 통합에 대한 자세한 내용을 살펴보십시오.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management 시스템(IMS) - Adobe ID</strong><br /> </td> 
   <td> 다른 Adobe Experience Cloud 솔루션과 동일한 Adobe ID을 사용하여 Adobe Campaign에 연결할 수 있습니다.<br /> Adobe Experience Cloud 통합, 특히 핵심 서비스에 연결된 특정 기능을 사용하려면 로그인하는 데 Adobe ID을 사용해야 합니다.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Adobe Campaign</a> 와 함께 Adobe ID을 구현하는 방법에 대해 자세히 알아보십시오.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> <strong>Adobe Experience Manager</strong>에서 직접 Adobe Campaign 데이터베이스에 매핑된 이메일 내용 또는 양식을 만들 수 있습니다.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Adobe Campaign </a> - Adobe Experience Manager 통합에 대해 자세히 알아보십시오.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Adobe Campaign에서 만들어 보낸 이메일이 열릴 때 <strong>Adobe Target</strong>에 의해 동적으로 계산되는 이미지를 삽입할 수 있습니다.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Adobe Campaign </a> - Adobe Target 통합에 대해 자세히 알아보십시오.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>사람 핵심 </strong><br /> <strong>서비스Adobe Audience Manager</strong><br /> </td> 
   <td> Adobe Experience Cloud 솔루션과 사용하는 코어 간에 대상을 공유할 수 있습니다.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Adobe Campaign - </a> 사용자 핵심 서비스 및 Adobe Audience Manager 통합에 대한 자세한 내용을 살펴보십시오.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>자산 핵심 서비스</strong><br /> </td> 
   <td> Adobe Experience Cloud 라이브러리의 자산을 Adobe Campaign에서 만든 이메일 및 랜딩 페이지에 삽입할 수 있습니다.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Adobe Campaign에 </a> 대한 자세한 내용 - Assets 핵심 서비스 통합</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> <strong>AEM Assets</strong> 라이브러리의 에셋을 Adobe Campaign에서 만든 이메일 및 랜딩 페이지에 삽입할 수 있습니다.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Adobe Campaign </a> - AEM Assets 통합에 대해 자세히 알아보십시오.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud 트리거</strong><br /> </td> 
   <td> <strong>트리거 핵심 서비스</strong>와 Adobe Campaign 간의 통합을 통해 Adobe Analytics이 웹 사이트에서 추적하는 특정 비헤이비어에 대한 반응으로 고객에게 개인화된 이메일을 보낼 수 있습니다.<br /> <p><a href="https://helpx.adobe.com/kr/campaign/kb/triggers-and-campaign.html">Adobe Campaign </a> - Experience Cloud 트리거 통합에 대해 자세히 알아보십시오.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - 데이터 커넥터</strong><br /> </td> 
   <td> <strong>데이터 커넥터</strong> (이전의 Adobe Genesis)을 사용하면 Adobe Campaign 및 Adobe Analytics이 이메일 캠페인 후의 사용자 행동과 관련된 세그먼트를 통해 상호 작용할 수 있습니다. 반대로, Adobe Campaign이 제공하는 이메일 캠페인의 지표와 특성을 Adobe Analytics - 데이터 커넥터로 전송합니다.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">캠페인 </a> - 데이터 커넥터 통합에 대해 자세히 알아보십시오.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

