---
product: campaign
title: Campaign 통합 정보
description: 다른 Adobe 솔루션을 사용하여 다양한 기능을 Campaign과 결합할 수 있습니다
feature: Overview
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: integrations
content-type: reference
level: Intermediate, Experienced
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 4%

---

# Adobe Campaign 통합 시작 {#about-campaign-integrations}

Adobe Experience Cloud은 강력한 솔루션 및 앱의 공통 세트를 사용하여 공통 데이터 플랫폼에 구축된 포괄적인 최고급 통합 솔루션 세트입니다.

[이 페이지](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/integrations){_blank}에서 Adobe Campaign과 Adobe Experience Cloud 솔루션 간에 사용할 수 있는 기능 통합에 대해 자세히 알아보세요.

Adobe Campaign과 통합할 수 있는 Adobe 솔루션 및 앱 서비스와 관련 문서의 전체 목록은 [이 섹션](#experience-cloud-integrations)에서 확인할 수 있습니다.

>[!CAUTION]
>
>이러한 통합을 사용하려면 Adobe IMS(Identity Management System)를 구현하고 Adobe ID을 통해 로그인해야 합니다. [이 페이지에서 자세히 알아보십시오](../../integrations/using/about-adobe-id.md).
>

## 솔루션 연결 {#working-with-experience-cloud-solutions}

여러 솔루션을 Adobe Experience Cloud에 연결할 수 있습니다. **조직**&#x200B;은(는) 관리자가 그룹과 사용자를 구성하고, Adobe Experience Cloud에서 SSO(Single Sign-On)를 제어할 수 있도록 하는 고객 엔터티입니다. 조직은 모든 Experience Cloud 제품 및 솔루션을 포괄하는 로그인 회사와 같은 역할을 합니다. 대부분의 경우 조직은 회사의 이름입니다. 그러나 회사는 여러 조직을 가질 수 있습니다.

조직 관리 및 Adobe Experience Cloud 계정 연결에 대한 자세한 내용은 [Adobe Experience Cloud 도움말 포털](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations){_blank}을 참조하세요.

## ID 및 쿠키 관리 {#id-and-cookies}

Adobe Campaign을 설치하거나 기존 설치를 Adobe Experience Cloud과 통합할 때 [Adobe Experience Cloud ID 서비스](https://experienceleague.adobe.com/en/docs/id-service/using/home){_blank}가 활성화됩니다. 이 서비스는 추적 기능으로 Adobe Campaign이 가장 먼저 사용하는 영구 쿠키를 대체합니다.

Adobe Experience Cloud ID 서비스(ID 서비스)는 Experience Cloud의 모든 솔루션에서 방문자를 식별하는 범용 영구 ID를 제공합니다.

추적 로그를 생성하는 수신자에게 고유 방문자 ID가 할당됩니다. 이 ID는 **[!UICONTROL nms:trackingLogRcp]** 테이블의 **[!UICONTROL Requester UUID (@sourceID)]** 필드에 저장됩니다. **방문자 ID 서비스가 구현되기 전에 있었던 수신자의 추적 데이터를 더 이상 사용할 수 없습니다**.

그러면 이 ID는 동일한 CNAME을 사용하는 다른 Adobe Experience Cloud 솔루션에서 인식됩니다. [자세히 알아보기](https://experienceleague.adobe.com/en/docs/id-service/using/reference/analytics-reference/cname){_blank}.

## Experience Cloud 통합 {#experience-cloud-integrations}

다음 표는 사용 가능한 Experience Cloud 통합 설명서에 대한 액세스를 제공합니다.

<table> 
 <thead> 
  <tr> 
   <th> 솔루션 및 앱<br /> </th> 
   <th> 사용 사례<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe 실시간 고객 데이터 플랫폼(RTCDP)</strong><br /> </td> 
   <td> Adobe Campaign과 Adobe Real-time Customer Data Platform(RTCDP) 간의 통합을 구성하여 세그먼트 데이터를 공유하고 대상을 Adobe Campaign으로 가져옵니다.<br /> <p>Campaign - Adobe 실시간 고객 데이터 플랫폼 통합에 대해 <a href="../../integrations/using/get-started-sources-destinations.md">자세히 알아보기</a>.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe IMS(Identity Management System) - Adobe ID</strong><br /> </td> 
   <td> 다른 Adobe Experience Cloud 솔루션과 동일한 Adobe ID을 사용하여 Adobe Campaign에 연결하도록 Adobe IMS를 구성합니다.<br /> Adobe Experience Cloud 통합에 연결된 특정 기능을 사용하려면 Adobe ID을 사용하여 로그인해야 합니다.<br /> <p>Adobe Campaign을 사용한 Adobe ID 구현에 대해 <a href="../../integrations/using/about-adobe-id.md">자세히 알아보세요</a>.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> <strong>Adobe Experience Manager</strong>에서 직접 Adobe Campaign 데이터베이스에 매핑된 전자 메일 콘텐츠 또는 양식을 만들려면 이 통합을 구성하십시오.<br /> <p>Adobe Campaign - Adobe Experience Manager 통합에 대해 <a href="../../integrations/using/about-adobe-experience-manager.md">자세히 알아보기</a>.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Adobe Campaign에서 만들고 보낸 전자 메일을 열 때 <strong>Adobe Target</strong>에서 동적으로 계산된 이미지를 삽입하도록 이 통합을 구성하십시오.<br /> <p>Adobe Campaign - Adobe Target 통합에 대해 <a href="../../integrations/using/integrating-with-adobe-target.md">자세히 알아보기</a>.</p><br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> 사용하는 Adobe Experience Cloud 솔루션과 앱 간에 대상자를 공유하도록 이 통합을 구성하십시오.<br /> <p>Adobe Campaign - Adobe Audience Manager 통합에 대해 <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">자세히 알아보기</a>.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Assets</strong><br /> </td> 
   <td> Adobe Experience Cloud 라이브러리의 자산을 Adobe Campaign에서 만든 전자 메일 및 랜딩 페이지에 삽입하도록 이 통합을 구성합니다.<br /> <p>Adobe Campaign - Assets 통합에 대해 <a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">자세히 알아보기</a></p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> <strong>AEM Assets</strong> 라이브러리의 자산을 Adobe Campaign에서 만든 전자 메일 및 랜딩 페이지에 삽입하도록 이 통합을 구성하십시오.<br /> <p>Adobe Campaign - AEM Assets 통합에 대해 <a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">자세히 알아보기</a>.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud 트리거</strong><br /> </td> 
   <td> <strong>Adobe Experience Cloud 트리거</strong>와(과) Adobe Campaign 간의 통합을 구성하여 Adobe Analytics이 웹 사이트에서 추적한 특정 행동에 반응하여 고객에게 개인화된 이메일을 보냅니다.<br /> <p>Adobe Campaign - Experience Cloud 트리거 통합에 대해 <a href="about-triggers.md">자세히 알아보기</a>.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics 커넥터</strong><br /> </td> 
   <td> Adobe Campaign 및 Adobe Analytics이 이메일 캠페인 후 사용자 행동에 대한 세그먼트를 통해 상호 작용할 수 있도록 이 통합을 구성합니다. 반대로 Adobe Campaign에서 게재한 이메일 캠페인의 지표와 특성을 Adobe Analytics으로 보냅니다.<br /> <p>Campaign - Analytics 커넥터 통합에 대해 <a href="../../integrations/using/gs-aa.md">자세히 알아보기</a>.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
