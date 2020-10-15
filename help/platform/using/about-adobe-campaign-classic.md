---
title: Adobe Campaign Classic 정보
seo-title: Adobe Campaign Classic 정보
description: 주요 기능, 사용자 인터페이스 및 글로벌 지침을 살펴보십시오.
seo-description: null
page-status-flag: never-activated
uuid: 2d0160fa-8328-4ff9-ab91-56e4058f8a99
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: a2b43311-737c-4a3b-a6af-1788879f9414
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 99%

---


# Get Started with Campaign Classic{#about-adobe-campaign-classic}

높은 수준의 고객 참여도와 훌륭한 경험을 제공하려면 브랜드는 모든 접점에서 일관된 고객 여정을 만들어야 합니다. 마케터는 이제 마케팅 투자에 대한 높은 수익을 제공하고 충성도를 높일 수 있는 크로스 채널 마케팅 캠페인을 효율적으로 디자인, 계획, 실행, 관리 및 최적화할 수 있습니다.

Adobe Campaign을 사용하면 대화형 마케팅 캠페인 만들기를 조정할 수 있습니다. Adobe Campaign에는 마케팅 및 고객 커뮤니케이션 프로세스를 모델, 간소화 및 자동화하는 혁신적인 기능이 있습니다.

>[!NOTE]
>
>Adobe Campaign Classic은 v6.11 및 v7에서 사용할 수 있습니다. 언급된 경우를 제외하고 도움말 자료는 최신 빌드의 두 버전 모두에 적용됩니다. 스크린샷은 Campaign Classic v7 사용자 인터페이스를 반영합니다.

## 주요 기능 {#key-capabilities}

Adobe Campaign은 크로스 채널 고객 경험을 디자인할 수 있는 플랫폼을 제공하며 시각적인 캠페인 오케스트레이션, 실시간 상호 작용 관리 및 크로스 채널 실행 환경을 제공합니다.

Adobe Campaign의 마케팅 캠페인 주기는 제품의 주요 기능을 보여줍니다.

![](assets/d_ncs_user_emarketing.png)

### Integrated customer profile {#integrated-customer-profile}

프로필(고객, 잠재 고객, 뉴스레터 구독자 등) 은 Adobe Campaign 데이터베이스에 중앙 집중화됩니다. 프로필을 가져오고 이 데이터베이스를 빌드하는 데 사용할 수 있는 메커니즘은 웹 양식을 통한 온라인 수집, 텍스트 파일 수동 또는 자동 가져오기, 회사 데이터베이스 또는 기타 정보 시스템을 사용한 복제와 같이 다양합니다. Adobe Campaign을 사용하면 마케팅 기록, 구매 정보, 환경 설정, CRM 데이터 및 관련 PII 데이터를 통합 뷰에 통합하여 분석하고 조치를 취할 수 있습니다.

Adobe Campaign에서 수신자는 게재(전자 메일, SMS 등)를 보낼 타겟팅된 기본 프로필입니다. 데이터베이스에 저장된 수신자 데이터 덕분에 주어진 게재를 받을 대상을 필터링하고 게재 콘텐츠에 개인화 데이터를 추가할 수 있습니다. 데이터베이스에 다른 유형의 프로필이 있습니다. 다양한 용도로 디자인되어 있습니다. 예를 들어 최종 대상으로 전송되기 전에 시드 프로필을 테스트하여 게재를 테스트합니다.

프로필 관리 기본 사항은 [프로필 정보](../../platform/using/about-profiles.md)에서 설명합니다.

### 타겟팅된 세분화 {#targeted-segmentation}

Adobe Campaign은 고도로 타겟팅되고 차별화된 오퍼를 만들 수 있는 강력하고 사용자 친화적인 세분화 및 타겟팅 기능을 제공합니다. 설명 분석 기능을 사용하면 마케팅 캠페인의 업스트림 및 다운스트림에 대한 정보를 분석할 수 있으며 필터 관리 및 [그래픽 쿼리 편집기](../../platform/using/about-queries-in-campaign.md) 기능을 사용하면 구독자 모집단을 필터링하고 기준을 제한 없이 대상 그룹을 샘플링하거나 만들 수 있습니다. 분석 및 타겟팅 기능은 [이 페이지](../../reporting/using/about-descriptive-analysis.md) 및 [필터 만들기](../../platform/using/creating-filters.md) 섹션에 설명되어 있습니다.

고급 데이터 관리 기능은 데이터 처리 기능을 확장합니다. 데이터 마트에서 모델링되지 않은 데이터를 포함하여 타겟팅 프로세스를 단순화하고 최적화합니다. 이 기능은 [이 페이지에](../../workflow/using/targeting-data.md#data-management) 자세히 설명되어 있습니다.

### 크로스 채널 캠페인 오케스트레이션 {#cross-channel-campaign-orchestration}

Adobe Campaign을 사용하면 타겟팅되고 개인화된 캠페인을 전자 메일, DM, SMS, 푸시 알림과 같은 다양한 채널에 디자인 및 오케스트레이션 할 수 있습니다. 단일 인터페이스는 모든 캠페인 및 커뮤니케이션을 일정 계획, 오케스트레이션, 구성, 개인화, 자동화, 실행 및 측정하는 데 필요한 모든 기능을 제공합니다. 캠페인 일정 예약 및 실행에 대한 자세한 내용은 [이 페이지](../../campaign/using/setting-up-marketing-campaigns.md)를 참조하십시오.

### 개인화 및 실시간 상호 작용 {#personalization-and-real-time-interaction}

고객 프로필과 기본 설정을 기반으로 한 메시지 콘텐츠와 헤더의 고급 개인화 덕분에 고객의 관심을 유도하고 응답률을 향상시킬 수 있습니다. 메시지 콘텐츠 관리 및 개인화에 대한 자세한 내용은 [이 페이지](../../delivery/using/about-personalization.md)를 참조하십시오. 콘텐츠, 알림 및 승인 회로의 공동 관리 기능은 [이 섹션](../../campaign/using/about-marketing-resource-management.md)에 자세히 설명되어 있습니다.

### 분석 및 보고 {#analysis-and-reporting}

Adobe Campaign을 사용하면 데이터와 프로필을 단계적으로 강화하여 고객의 동작을 모니터링하고 해석할 수 있습니다. 보고 및 분석 도구를 사용하면 각각의 새로운 캠페인을 활용할 수 있고, 마케팅 이니셔티브를 더 잘 타겟팅할 수 있으며, 마케팅 활동의 영향과 투자 수익률을 최적화할 수 있습니다. 자세한 내용은 [이 페이지를](../../reporting/using/delivery-reports.md) 참조하십시오.

### Adobe Experience Cloud 통합 {#adobe-experience-cloud-integrations}

Adobe Campaign의 게재 기능 및 고급 캠페인 관리 기능과 사용자 경험을 개인화할 수 있도록 만들어진 솔루션 세트를 결합할 수 있습니다. 예를 들어 Adobe Experience Manager, Adobe Analytics, Adobe Target 또는 Adobe Experience Cloud 트리거를 사용할 수 있습니다. 또한 Adobe IMS에 통합하고 Adobe ID로 Campaign에 로그인할 수 있습니다. 솔루션 간 및 인증 통합에 대한 자세한 내용은 [이 섹션](../../integrations/using/about-adobe-id.md)을 참조하십시오.

## 핵심 기능 및 추가 기능 {#core-capabilities-and-add-ons}

Adobe Campaign은 요구 사항과 아키텍처에 따라 대화형 마케팅 기능을 구현하고 최적화하는 데 도움이 되는 기능의 집합을 제공합니다. 일부는 핵심 기능이며 일부는 패키지 설치 및 구성에 따라 다릅니다. 자세한 제품 설명은 [Adobe Campaign Classic 제품 설명](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-classic—product-description.html)에 나와 있습니다.

다음 기능을 사용할 수 있습니다. 사용권 계약에 따라 이러한 기능 중 일부를 사용자 인스턴스에 사용하거나 사용하지 않을 수 있습니다.

* [채널](../../delivery/using/steps-about-delivery-creation-steps.md) - 다양한 채널에서 게재를 디자인 및 전송합니다. 전자 메일, SMS, Line, 모바일 앱, DM,
* [캠페인](../../campaign/using/designing-marketing-campaigns.md) - 크로스 채널 캠페인 오케스트레이션,
* [MRM](../../campaign/using/about-marketing-resource-management.md) - 마케팅 리소스 및 예산 관리,
* [상호 작용](../../interaction/using/interaction-and-offer-management.md) - 캠페인으로 오퍼 관리,
* [메시지 센터](../../message-center/using/about-transactional-messaging.md) - 전자 메일, SMS 또는 모바일 앱으로 트랜잭션 메시지를 보낼 수 있습니다.
* [소셜 마케팅](../../social/using/about-social-marketing.md) - Facebook, Twitter와 같은 소셜 미디어에서 커뮤니케이션,
* [워크플로우](../../workflow/using/about-workflows.md) /데이터 관리 - 워크플로우를 통해 프로세스 자동화 및 데이터 관리
* [웹 애플리케이션](../../web/using/about-web-applications.md) - 웹 페이지 및 양식 만들기,
* [설문 조사 관리자](../../web/using/about-surveys.md) - 온라인 설문 조사 및 투표 만들기,
* [Content Manager](../../delivery/using/about-content-management.md) - 전자 메일 콘텐츠 관리,
* [분산 마케팅](../../campaign/using/about-distributed-marketing.md) - 중앙/지방 에이전시의 캠페인 조정
* [응답 관리자](../../campaign/using/about-response-manager.md) - 고객 응답 관리,
* [커넥터](../../platform/using/about-connectors.md) - 커넥터를 사용하여 외부 솔루션 및 데이터베이스 엔진과 커뮤니케이션합니다.
* [웹 서비스](../../configuration/using/about-web-services.md) - API/웹 서비스를 통해 캠페인 사용,
* [보고](../../reporting/using/about-adobe-campaign-reporting-tools.md) - 기본 제공 보고서에 액세스하고 데이터를 분석하며 보고서를 디자인할 수 있습니다.

