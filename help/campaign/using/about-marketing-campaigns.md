---
product: campaign
title: 마케팅 캠페인 기본 정보
description: 마케팅 캠페인을 정의, 최적화, 실행 및 분석할 수 있습니다.
role: User
feature: Campaigns
exl-id: 07cfa2b3-4e70-437a-ad5f-15fbfe717d5c
source-git-commit: dd6bcb16fe41b6a3f1e3f5aaf2f753b29ad4bc1d
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 33%

---

# 마케팅 캠페인 오케스트레이션{#designing-marketing-campaigns}

Adobe Campaign은 온라인과 오프라인의 모든 채널에서 캠페인을 개인화하고 게재할 수 있는 다양한 솔루션을 제공합니다. 마케팅 캠페인을 생성, 구성, 실행 및 분석할 수 있습니다. 모든 마케팅 캠페인은 통합 제어 센터에서 관리할 수 있습니다.

캠페인에는 작업(게재) 및 프로세스(파일 가져오기 또는 추출)와 리소스(마케팅 문서, 게재 아웃라인)가 포함됩니다. 마케팅 캠페인에서 사용됩니다. 캠페인은 프로그램의 일부이며 프로그램은 캠페인 플랜에 포함됩니다.

캠페인 관리에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html?lang=ko){target=_blank}를 참조하세요.

![](assets/do-not-localize/campaign.jpg){width="40%"}

캠페인 관리와 관련된 주요 단계를 알아봅니다.

* [시작](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=ko){target=_blank}: Adobe Campaign에서 마케팅 캠페인을 만들고 실행하는 방법을 단계별로 살펴봅니다.

* [첫 번째 캠페인을 만듭니다](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-create.html?lang=ko){target=_blank}: 캠페인을 조정하고 논리를 설정하는 방법에 대해 알아봅니다. 캠페인은 게재, 타겟팅 규칙, 비용, 파일 내보내기, 관련 문서 등 마케팅 캠페인과 관련된 모든 요소를 중앙에서 관리합니다.

* [캠페인에서 메시지 보내기](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-deliveries.html?lang=ko){target=_blank}: 캠페인에서 크로스 채널 게재 오케스트레이션: 개인화된 이메일, SMS, 푸시 알림 및 인앱 메시지를 통해 Adobe Campaign과의 커뮤니케이션을 간소화합니다.

![](assets/do-not-localize/add-on.jpg){width="40%"}

캠페인 관리에 사용할 수 있는 세 가지 추가 기능:

* [캠페인 최적화](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=ko){target=_blank}: 이 모듈을 사용하면 게재 전송을 제어, 필터링 및 모니터링할 수 있습니다. 이를 통해 회사 커뮤니케이션 정책을 준수하면서 고객의 요구 사항과 기대치에 가장 적합한 메시지를 보내도록 보장합니다.

* [마케팅 리소스 관리](https://experienceleague.adobe.com/docs/campaign/automation/mrm/about-marketing-resource-management.html?lang=ko){target=_blank}: 이 모듈을 사용하면 관련된 작업, 예산 및 마케팅 리소스에 대한 완전한 관리 및 실시간 추적을 제공하여 공동 작업 모드에서 마케팅 작업을 제어할 수 있습니다.

* [분산 마케팅](https://experienceleague.adobe.com/docs/campaign/automation/distributed-marketing/about-distributed-marketing.html?lang=ko){target=_blank}: 이 모듈을 사용하면 관련된 작업, 예산 및 마케팅 리소스에 대한 완전한 관리 및 실시간 추적을 제공하여 공동 작업 모드에서 마케팅 작업을 제어할 수 있습니다.

<!--

Adobe Campaign lets you define, optimize, execute and analyze communications and marketing campaigns. Adobe Campaign acts like a unified order and execution center for marketing strategies. For more on this, refer to [Access campaigns](../../distributed/using/accessing-campaigns.md) and [Create marketing campaigns](../../campaign/using/setting-up-marketing-campaigns.md).

In addition, the **Marketing Resource Management (MRM)** module lets you control marketing actions in a collaborative mode by providing complete management and real-time tracking of the tasks, budgets and marketing resources involved. The Marketing Resource Management lets you optimize and regulate the management of internal and external processes, resources and marketing campaigns, as well as third party relations (agencies, printers, etc.). For more on this, refer to [this section](../../mrm/using/about-marketing-resource-management.md).

>[!NOTE]
>
>For more on the Adobe Campaign core functionalities, refer t [this section](../../platform/using/about-adobe-campaign-classic.md) section.  
>Capabilities related to population targeting, message personalization and message delivery on the various channels are detailed in [this section](../../delivery/using/steps-about-delivery-creation-steps.md).

![](assets/do-not-localize/how-to-video.png) [Discover marketing campaigns keys concepts in video](#video)

## Core concepts {#core-concepts}

The following concepts need to be known in the context of Campaign:

* **Campaign**

  A campaign centralizes all the elements related to a marketing campaign: deliveries, targeting rules, costs, export files, related documents, etc. Each campaign is attached to a program.

  For more on this, refer to [Adding a campaign](../../campaign/using/setting-up-marketing-campaigns.md#adding-a-campaign).

* **Program**

  A program lets you define marketing actions for a calendar period: launch, canvassing, loyalty, etc. Each program contains campaigns linked to a calendar, which provides an overall view.

* **Plan**

  The marketing plan can contain multiple programs. It is linked to a calendar period, has an allocated budget and can also be linked up to documents and objectives.

  For more on this, refer to [Campaign calendar](../../campaign/using/accessing-marketing-campaigns.md#campaign-calendar).

* **Workflow**

  A campaign workflow contains the same activities as for all workflows but is specific to the campaign. It enables you to create and configure deliveries for all available channels.

  For more on this, refer to [this section](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

* **Objectives**

  Within the campaign, program or plan, you can state a list of objectives. These are quantified values to be reached. At the end of the campaign, program or plan, the MRM module lets you compare the objectives and results in dedicated reports.

* **Delivery outline**

  A delivery outline is a structured description of a delivery. Every delivery can refer to a delivery outline which contains, for example, the related offers, documents to be attached, or a link to stores. An offer can be referenced in the delivery according to the delivery outline selected.

  For more on this, refer to [this section](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

## Tutorial {#video}

This video presents the key concepts of marketing campaigns.

>[!VIDEO](https://video.tv.adobe.com/v/35131?quality=12)

Additional Campaign Classic how-to videos are available [here](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko).

-->