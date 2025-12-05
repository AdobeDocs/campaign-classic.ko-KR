---
product: campaign
title: Adobe Campaign Classic 정보
description: 주요 기능, 사용자 인터페이스 및 글로벌 지침을 살펴보십시오.
feature: Overview
role: User
level: Beginner
exl-id: 8febceb0-9694-4045-a630-a7ff2fd18943
source-git-commit: 354fc8fd5d030ed88e2b279ba1dd3eaf2f314d53
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 54%

---

# Campaign Classic 시작{#about-adobe-campaign-classic}

높은 수준의 고객 참여도와 훌륭한 경험을 제공하려면 브랜드는 모든 접점에서 일관된 고객 여정을 만들어야 합니다. 마케터는 이제 마케팅 투자에 대한 높은 수익을 제공하고 충성도를 높일 수 있는 크로스 채널 마케팅 캠페인을 효율적으로 디자인, 계획, 실행, 관리 및 최적화할 수 있습니다.

Adobe Campaign을 사용하면 대화형 마케팅 캠페인 만들기를 조정할 수 있습니다. Adobe Campaign에는 마케팅 및 고객 커뮤니케이션 프로세스를 모델, 간소화 및 자동화하는 혁신적인 기능이 있습니다.


>[!BEGINTABS]

>[!TAB Campaign으로 시작]

Adobe Campaign 기능 및 시작 방법에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/new/get-started){target=_blank}를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/new/get-started){target=_blank}

>[!TAB 캠페인 시작]

* [호환성 매트릭스](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)에서 Adobe Campaign 클라이언트 콘솔과의 시스템 및 도구 호환성을 확인합니다.

* 이 페이지에서 [Adobe Campaign을 설치하고 로그온하는 방법에 대해 알아보려면](launching-adobe-campaign.md).

>[!TAB Campaign UI 찾아보기]

* 이 페이지에서 Adobe Campaign 사용자 인터페이스 [을(를) 살펴보세요](adobe-campaign-workspace.md).

* [캠페인 탐색기](adobe-campaign-workspace.md#using-adobe-campaign-explorer)를 사용하여 작업하는 방법을 알아봅니다.

>[!ENDTABS]

<!--

## Key capabilities {#key-capabilities}

Adobe Campaign provides a platform for designing cross-channel customer experiences and provides an environment for visual campaign orchestration, real time interaction management and cross channel execution.

The marketing campaign cycle in Adobe Campaign illustrates the main areas of functionality of the product:

![](assets/d_ncs_user_emarketing.png)

### Integrated customer profile {#integrated-customer-profile}

Profiles (customers, prospects, newsletter subscribers, etc.) are centralized in the Adobe Campaign database. There are many possible mechanisms for acquiring profiles and building up this database: on-line collection via web forms, manual or automatic import of text files, replication with company databases or other information systems. With Adobe Campaign, you can incorporate marketing history, purchase information, preferences, CRM data, and any relevant PII data in a consolidated view to analyze and take action.

In Adobe Campaign, recipients are the default profiles targeted for sending deliveries (emails, SMS, etc.). Thanks to the recipient data that are stored in the database, you will be able to filter the target that will receive any given delivery and to add personalization data in your delivery contents. Other types of profiles exist in the database. They are designed for different uses. For example, seed profiles are made to test your deliveries before they are sent to the final target.

Profile management basics are explained in [About profiles](../../platform/using/about-profiles.md).

### Targeted segmentation {#targeted-segmentation}

Adobe Campaign has powerful, user-friendly segmentation and targeting features that let you create highly targeted, differentiated offers. The descriptive analysis functionality lets you analyze information upstream and downstream of your marketing campaigns, and the filter management and [graphical query editor](../../platform/using/adobe-campaign-workspace.md#about-queries-in-campaign) functionality lets you filter your subscriber population and sample or create target groups based on an unlimited number of criteria. The analysis and targeting features are described in [this page](../../reporting/using/about-descriptive-analysis.md) and in the [Creating filters](../../platform/using/creating-filters.md) section.

The advanced Data Management functionality extends the data processing capabilities. It simplifies and optimizes the targeting process by including data not modeled in the datamart. This functionality is detailed in [this page](../../workflow/using/targeting-data.md#data-management).

### Cross-channel campaign orchestration {#cross-channel-campaign-orchestration}

Adobe Campaign lets you design and orchestrate targeted and personalized campaigns on multiple channels: email, direct mail, SMS, push notification. A single interface provides you with all the functions required to schedule, orchestrate, configure, personalize, automate, execute, and measure all your campaigns and communications. For more on scheduling and executing campaigns, refer to [this page](../../campaign/using/setting-up-marketing-campaigns.md).

### Personalization and real-time interaction {#personalization-and-real-time-interaction}

Attract your customers' attention and improve response rates thanks to the advanced personalization of message content and headers based on customer profiles and preferences. For more on message content management and personalization, refer to [this page](../../delivery/using/about-personalization.md). Collaborative management of content, notification and approval circuits are detailed in [this section](../../mrm/using/about-marketing-resource-management.md).

### Analysis and reporting {#analysis-and-reporting}

Adobe Campaign lets you monitor and interpret the behavior of your customers by gradually enriching their data and profiles. The reporting and analysis tools let you capitalize on each new campaign, target your marketing initiatives better, and optimize their impact and return on investment. Refer to [this page](../../reporting/using/delivery-reports.md) for more information.

### Adobe Experience Cloud integrations {#adobe-experience-cloud-integrations}

You can combine the delivery functionalities and advanced campaign management functionalities of Adobe Campaign with a set of solutions created to help you personalize your users' experience: Adobe Experience Manager, Adobe Analytics, Adobe Target or Adobe Experience Cloud triggers for example. You can also integrate to Adobe IMS and login to Campaign with your Adobe ID. For more on cross-solution and authentication integrations, refer to [this section](../../integrations/using/about-adobe-id.md).

## Core capabilities and add-ons {#core-capabilities-and-add-ons}

Adobe Campaign offers a set of capabilities to help you implementing and optimizing the conversational marketing functionalities depending on your needs and your architecture. Some of them are core capabilities and some depend on the installation of a package and on your configuration. A detailed product description is available here: [Adobe Campaign product description](https://helpx.adobe.com/kr/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

The following capabilities are available. Depending on your license agreement, some of these capabilities can be available or not in your instance.

* [Channels](../../delivery/using/steps-about-delivery-creation-steps.md) - design and send deliveries on various channels: email, SMS, Line, mobile app, direct mail,
* [Campaign](../../campaign/using/designing-marketing-campaigns.md) - orchestrate cross-channel campaigns,
* [MRM](../../mrm/using/about-marketing-resource-management.md) - manage marketing resources and budgets,
* [Interaction](../../interaction/using/interaction-and-offer-management.md) - managing offers with Campaign,
* [Message Center](../../message-center/using/about-transactional-messaging.md) - send transactional messages by email, SMS or on mobile app,
* [Social Marketing](../../social/using/about-social-marketing.md) - communicate on social media: Facebook, X (formerly known as Twitter),
* [Workflow](../../workflow/using/about-workflows.md) / Data Management - automate processes and manage data with workflows,
* [Web applications](../../web/using/about-web-applications.md) - create web pages and forms,
* [Survey Manager](../../surveys/using/about-surveys.md) - create online surveys and polls,
* [Content Manager](../../delivery/using/about-content-management.md) - manage email content,
* [Distributed Marketing](../../distributed/using/about-distributed-marketing.md) - coordinate campaigns for central/local agencies,
* [Response Manager](../../response/using/about-response-manager.md) - manage customer response,
* [Connectors](../../platform/using/about-connectors.md) - use connectors to communicate with external solutions and database engines,
* [Web Services](../../configuration/using/about-web-services.md) - use Campaign through APIs/Web Services,
* [Reporting](../../reporting/using/about-adobe-campaign-reporting-tools.md) - access built-in reports, analyze data and design your own reports.

-->

## 튜토리얼 비디오 {#video}

이 비디오에서는 Campaign Classic의 주요 기능 및 성능을 소개합니다.

>[!VIDEO](https://video.tv.adobe.com/v/39520?captions=kor&quality=12)

추가 Campaign Classic 방법 비디오는 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 시청할 수 있습니다.
