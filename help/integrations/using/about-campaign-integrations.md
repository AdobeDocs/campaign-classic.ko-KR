---
title: Campaign 통합 기본 정보
description: 현재 버전의 Adobe Campaign과 [Adobe Experience Cloud 솔루션] 간의 기능 통합에 대해 자세히 알아보기
page-status-flag: never-activated
uuid: 087abdf0-b4b2-45e6-be21-b03bf85ddf83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: campaign-integrations
discoiquuid: 0af1fd96-48ef-43c9-a03b-0f9a6e0e02fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e488e1771fe4d07132844900f41f5f4f09fa9438
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 2%

---


# Campaign 통합 기본 정보 {#about-campaign-integrations}

Adobe Experience Cloud는 강력한 핵심 서비스의 공통 세트를 제공하는 공통 데이터 플랫폼을 기반으로 구축된 포괄적인 최고급 통합 솔루션입니다.

Adobe Campaign과 [Adobe Experience Cloud 솔루션](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) 및 [핵심 서비스 간의 기능 통합에 대해 자세히 알아보십시오](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html). 그런 다음 솔루션 구현을 현대화하고 Experience Cloud를 구현하여 고객 속성 및 대상과 같은 기능을 사용할 수 있습니다.

Adobe Campaign과 통합할 수 있는 Adobe 솔루션 및 핵심 서비스 목록과 관련 설명서는 [이 섹션에서 제공됩니다](#experience-cloud-integrations).

![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>이러한 통합 대부분은 IMS(Adobe ID)를 통해 로그인해야 합니다. For more on this implementation, refer to [this page](../../integrations/using/about-adobe-id.md).
>
>IMS 구현은 매우 복잡한 과정이며 오래 걸릴 수 있습니다. Adobe 기술 관리자에게는 엄격히 지정되어 있습니다.

## 솔루션 연결 {#working-with-experience-cloud-solutions}

환경에 따라 여러 솔루션을 Adobe Experience Cloud에 연결할 수 있습니다. 이 지표는 조직으로 연결됩니다. 조직은 **관리자가 그룹과 사용자를 구성하고 Experience Cloud에서 Single Sign-On을 제어할 수 있도록 해주는 개체입니다** . 조직은 모든 Experience Cloud 제품 및 솔루션을 포괄하는 로그인 회사와 같은 기능을 합니다. 대부분의 경우 조직은 회사 이름입니다. 하지만, 회사는 많은 조직을 가질 수 있습니다.

조직 관리 및 Adobe Experience Cloud 계정 연결은 [Adobe Experience Cloud 도움말 포털에 자세히 설명되어 있습니다](https://marketing.adobe.com/resources/help/ko_KR/mcloud/organizations.html).

>[!CAUTION]
>
>Adobe Campaign을 새로 설치하거나 기존 설치를 Adobe Experience Cloud와 통합할 때 [Experience Cloud ID 서비스가](https://marketing.adobe.com/resources/help/en_US/mcvid/) 활성화됩니다. 이 서비스는 Adobe Campaign에서 가장 먼저 사용되는 영구 쿠키의 추적 기능을 대체합니다.
>
>그러면 추적 로그를 생성하는 수신자에게 고유 방문자 ID가 할당됩니다. 이 ID는 표의 **[!UICONTROL Requester UUID (@sourceID)]** 필드에 **[!UICONTROL nms:trackingLogRcp]** 저장됩니다. 방문자 ID 서비스가 구현되기 전에 존재했던 수신자의 추적 데이터를 더 이상 사용할 수 없습니다.
>
>그러면 ID가 동일한 [CNAME의 다른 Adobe Experience Cloud 솔루션에서 인식됩니다](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_cname.html).

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
   <td> <strong>Adobe 실시간 고객 데이터 플랫폼</strong><br /> </td> 
   <td> Adobe Campaign과 Adobe 실시간 고객 데이터 플랫폼 간의 통합을 통해 세그먼트 데이터를 공유하고 대상을 Adobe Campaign으로 가져올 수 있습니다.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">Campaign에 대한 자세한</a> 내용 - Adobe 실시간 고객 데이터 플랫폼 통합</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS - Adobe ID</strong><br /> </td> 
   <td> 다른 Adobe Experience Cloud 솔루션과 동일한 Adobe ID로 Adobe Campaign에 연결할 수 있습니다.<br /> Adobe Experience Cloud 통합, 특히 핵심 서비스에 연결된 특정 기능을 사용하려면 로그인하는 데 Adobe ID를 사용해야 합니다.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Adobe Campaign을 사용하여 Adobe ID 구현에 대해 자세히</a> 알아보십시오.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Adobe Experience Manager에서 직접 Adobe Campaign 데이터베이스에 매핑된 이메일 콘텐츠 또는 양식을 만들 수 <strong>있습니다</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Adobe Campaign - Adobe Experience Manager 통합에 대해 자세히</a> 알아보십시오.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Adobe Campaign에서 만들고 보낸 이메일을 열 때 <strong>Adobe Target</strong> 에서 동적으로 계산된 이미지를 삽입할 수 있습니다.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Adobe Campaign - Adobe Target 통합에 대해 자세히</a> 알아보십시오.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>사용자 핵심 서비스</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Adobe Experience Cloud 솔루션과 사용하는 코어 간에 대상을 공유할 수 있습니다.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Adobe Campaign - People 코어 서비스 및 Adobe Audience Manager 통합에 대해 자세히</a> 알아보십시오.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>자산 핵심 서비스</strong><br /> </td> 
   <td> Adobe Experience Cloud 라이브러리의 에셋을 Adobe Campaign에서 만든 이메일 및 랜딩 페이지에 삽입할 수 있습니다.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Adobe Campaign에 대한 자세한</a> 내용 - Assets 핵심 서비스 통합</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> AEM 자산 라이브러리의 자산을 <strong>Adobe Campaign에서 만든 이메일 및 랜딩</strong> 페이지에 삽입할 수 있습니다.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Adobe Campaign - AEM Assets 통합에 대해 자세히</a> 알아보십시오.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud 트리거</strong><br /> </td> 
   <td> 트리거 코어 서비스 <strong>와</strong> Adobe Campaign 간의 통합을 통해 Adobe Analytics에서 웹 사이트에서 추적할 수 있는 특정 행동에 대한 반응으로 개인화된 이메일을 고객에게 보낼 수 있습니다.<br /> <p><a href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html">Adobe Campaign - Experience Cloud 트리거 통합에 대해 자세히</a> 알아보십시오.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - 데이터 커넥터</strong><br /> </td> 
   <td> <strong>데이터 커넥터</strong> (이전의 Adobe Genesis)를 사용하면 Adobe Campaign 및 Adobe Analytics가 이메일 캠페인 이후 사용자 동작과 관련된 세그먼트를 통해 상호 작용할 수 있습니다. 반대로, Adobe Campaign에서 제공하는 이메일 캠페인의 지표와 속성을 Adobe Analytics - 데이터 커넥터로 보냅니다.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">캠페인 - 데이터 커넥터 통합에 대해 자세히</a> 알아보십시오.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

