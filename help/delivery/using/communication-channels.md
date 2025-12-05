---
product: campaign
title: 커뮤니케이션 채널
description: 여러 채널에서 개인화된 메시지를 보낼 수 있는 게재 정보를 만듭니다.
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
role: User
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 2e3a14c97706a873f0791ef83708d704d2eed6c3
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 14%

---

# 커뮤니케이션 채널{#communication-channels}

Adobe Campaign에서는 이메일, SMS, 푸시 알림 및 DM 등 크로스 채널 캠페인을 보내고, 다양한 전용 보고서를 사용하여 캠페인의 효과를 측정할 수 있습니다. 이러한 메시지는 게재를 통해 디자인되고 전송되며 각 수신자에 대해 개인화할 수 있습니다.

핵심 기능에는 타기팅, 정의 및 메시지 개인화, 커뮤니케이션 실행 및 관련 운영 보고서가 포함됩니다.

Campaign v7에서 v8로 전환하는 과정의 일부로 Campaign Classic 설명서 세트가 간소화 및 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다.

>[!BEGINTABS]

>[!TAB 통신 채널 설명서]

통신 채널에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html?lang=ko){target=_blank}를 참조하세요.


[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html?lang=ko){target=_blank}


>[!TAB 게재 콘텐츠 및 대상자]

Campaign v8 설명서&#x200B;**에서 게재 만들기, 콘텐츠 및 대상**&#x200B;과(와) 관련된 주요 단계를 알아보세요.

* [게재 만들기](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=ko#create-the-delivery){target="_blank"}: 일회성 단일 게재를 만드는 방법을 알아봅니다.
* [콘텐츠 정의](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=ko#content-of-the-delivery){target="_blank"}: 각 채널별로 게재 콘텐츠를 구성합니다.
* [대상 지정](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=ko#target-population){target="_blank"}: 주 대상, 증명 대상, 시드 주소 및 컨트롤 그룹 등 여러 유형의 대상을 정의합니다.
* [게재 템플릿 작업](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html?lang=ko){target="_blank"}: 게재를 쉽게 만들 수 있도록 템플릿을 정의하는 방법을 알아봅니다.





>[!TAB 게재 확인 및 보내기]

다음 페이지를 참조하여 게재 유효성 검사, 전송 및 모범 사례 **Campaign v8 설명서**&#x200B;에 대해 알아보십시오.

* [게재 유효성 검사](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=ko#validate-the-delivery){target="_blank"}: 기본 대상으로 보내기 전에 게재의 유효성을 검사하는 방법을 알아봅니다.
* [게재 보내기](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=ko#configuring-and-sending-the-delivery){target="_blank"}: 게재 설정을 구성하고 메시지를 보내는 방법을 정의합니다.
* [게재 모범 사례](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html?lang=ko){target="_blank"}: Campaign 게재 기능 관련 모범 사례를 참조하세요.

>[!ENDTABS]

다음 설정은 Campaign Classic에만 적용됩니다. 다른 게재 설정은 [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html?lang=ko){target="_blank"}를 참조하세요.

+++ **게재 분석**

**게재 분석 성능 개선**

게재 준비 속도를 높이려면 분석을 시작하기 전에 **[!UICONTROL Prepare the delivery parts in the database]** 옵션을 확인할 수 있습니다.

이 옵션을 활성화하면 게재 준비가 데이터베이스 내에서 직접 수행되므로 분석을 상당히 가속화할 수 있습니다.

현재 이 옵션은 다음 조건이 충족될 때만 사용할 수 있습니다.

* 게재는 이메일이어야 합니다. 다른 채널은 현재 지원되지 않습니다.
* 중간 소싱 또는 외부 공정순서를 사용하지 말고 일괄 게재 공정순서 유형만 사용해야 합니다. **[!UICONTROL General]**&#x200B;의 **[!UICONTROL Delivery properties]** 탭에서 사용되는 라우팅을 확인할 수 있습니다.
* 외부 파일에서 가져온 모집단을 타깃팅할 수 없습니다. 단일 게재의 경우 **[!UICONTROL To]**&#x200B;에서 **[!UICONTROL Email parameters]** 링크를 클릭하고 **[!UICONTROL Defined in the database]** 옵션이 선택되어 있는지 확인하십시오. 워크플로우에서 사용되는 게재의 경우 **[!UICONTROL Specified by the inbound event(s)]** 탭에서 받는 사람이 **[!UICONTROL Delivery]**&#x200B;인지 확인하십시오.
* PostgreSQL 데이터베이스를 사용하고 있어야 합니다.

**분석 우선 순위 구성**

게재가 캠페인의 일부인 경우 **[!UICONTROL Advanced]** 탭에서 추가 옵션을 제공합니다. 이렇게 하면 동일한 캠페인의 게재에 대한 처리 순서를 구성할 수 있습니다.

보내기 전에 각 게재를 분석합니다. 분석 기간은 게재 추출 파일에 따라 다릅니다. 파일 크기가 클수록 분석에 더 오래 걸려서 다음 게재가 대기하게 됩니다.

**[!UICONTROL Message preparation by the scheduler]**&#x200B;에 대한 옵션을 사용하면 캠페인 워크플로우에서 게재 분석의 우선 순위를 지정할 수 있습니다.

![](assets/delivery_analysis_priority.png)

게재가 너무 큰 경우 다른 워크플로우 게재 분석이 느려지지 않도록 우선 순위를 낮게 할당하는 것이 좋습니다.

>[!NOTE]
>
>더 큰 게재 분석으로 워크플로우의 진행 속도가 느려지지 않도록 **[!UICONTROL Schedule execution for a time of low activity]**&#x200B;을(를) 클릭하여 실행을 예약할 수 있습니다.

+++

+++ **전송 중**

**다시 시도 구성**

**소프트** 또는 **무시됨** 오류로 인해 일시적으로 게재되지 않은 메시지는 자동 다시 시도될 수 있습니다. 게재 실패 유형 및 이유는 이 [섹션](delivery-failures-quarantine.md#delivery-failure-types-and-reasons)에 나와 있습니다.

>[!IMPORTANT]
>
>호스팅 또는 하이브리드 설치의 경우 [향상된 MTA](sending-with-enhanced-mta.md)(으)로 업그레이드한 경우 게재의 다시 시도 설정은 Campaign에서 더 이상 사용되지 않습니다. 소프트 바운스 재시도 및 재시도 간 시간은 메시지 이메일 도메인에서 돌아오는 바운스 응답의 유형 및 심각도에 따라 고급 MTA에 의해 결정됩니다.

이전 Campaign MTA를 사용하는 온-프레미스 설치 및 호스팅/하이브리드 설치의 경우 게재 매개 변수에 대한 **[!UICONTROL Delivery]** 탭의 중앙 섹션은 게재 다음 날에 수행해야 하는 다시 시도 횟수와 다시 시도 사이의 최소 지연을 나타냅니다.

![](assets/s_ncs_user_wizard_retry_param.png)

기본적으로 5번의 다시 시도가 배달 첫 날에 예약되며 하루 중 24시간 동안 최소 1시간 간격으로 분산됩니다. **[!UICONTROL Validity]** 탭에 정의된 배달 기한까지 하루에 한 번 다시 시도됩니다. 아래 섹션을 참조하십시오.

**유효 기간 정의**

게재가 실행되면 게재 기한까지 메시지(및 다시 시도)를 보낼 수 있습니다. 게재 속성에는 **[!UICONTROL Validity]** 탭을 통해 표시됩니다.

![](assets/s_ncs_user_email_del_valid_period.png)

* **[!UICONTROL Delivery duration]** 필드를 사용하면 전역 게재 다시 시도에 대한 제한을 입력할 수 있습니다. 즉, Adobe Campaign은 시작 날짜부터 메시지를 전송하고 나서 메시지가 오류만 반환하는 경우 유효성 검사 제한에 도달할 때까지 구성 가능한 일반 재시도를 수행합니다.

  날짜를 지정할 수도 있습니다. 이렇게 하려면 **[!UICONTROL Explicitly set validity dates]**&#x200B;을(를) 선택합니다. 이 경우 게재 및 유효성 검사 제한 날짜를 통해 시간을 지정할 수도 있습니다. 기본적으로 현재 시간이 사용되지만 입력 필드에서 직접 수정할 수 있습니다.

  >[!IMPORTANT]
  >
  >호스팅 또는 하이브리드 설치의 경우 [향상된 MTA](sending-with-enhanced-mta.md)(으)로 업그레이드한 경우 Campaign 이메일 게재의 **[!UICONTROL Delivery duration]** 설정은 **3.5일 이하**(으)로 설정된 경우에만 사용됩니다. 3.5일 이상의 값을 정의하면 고려되지 않습니다.

* **리소스의 유효성 제한**: **[!UICONTROL Validity limit]** 필드는 주로 미러 페이지와 이미지에 대해 업로드된 리소스에 사용됩니다. 이 페이지의 리소스는 제한된 시간 동안 유효합니다(디스크 공간을 절약하기 위함).

  이 필드의 값은 다음 단위로 표현할 수 있습니다. **s**(초), **m**(분), **h**(시간), **d**(일)(기본값), **y**(년).

+++

<!--

   Learn how to create a one-shot single delivery. You can create other types of deliveries to build your use cases. 

For more information about the different types of deliveries and how to create them, refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=ko){target="_blank"}. 

>[!NOTE]
>
>Adobe Campaign offers a set of tools to monitor your deliverability and optimize email sending. Learn more in [this section](about-deliverability.md).

Delivery sending can be automated by preparing a delivery and/or sending it in the process of a workflow. For more on delivery-type activities in workflows, refer to [this section](../../workflow/using/about-action-activities.md).

Adobe Campaign offers the following delivery channels:

1. **Email channel**: email deliveries let you send personalized emails to the target population. Refer to [About email channel](about-email-channel.md).
1. **Direct mail channel**: direct mail deliveries let you generate an extraction file which contains data on the target population. Refer to [About direct mail channel](about-direct-mail-channel.md).
1. **Mobile channel**: deliveries on mobile channels let you send personalized SMS or LINE messages to the target population. Refer to [SMS channel](sms-channel.md).
1. **Mobile application channel**: mobile app deliveries let you send notifications to iOS and Android systems. Refer to the [Mobile app channel](about-mobile-app-channel.md) chapter.

   Other channels are described on [this section](#other-channels).

   >[!NOTE]
   >
   >The number of available channels depends on your contract. Please check your license agreement.

Deliveries can be carried out **online** (via email, one of the mobile channels and push notifications), and **offline** (direct mail channel).

Depending on the channel, delivery modes can be:

* Direct mass delivery via Adobe Campaign (default mode for email channel).
* External delivery via a specialist operator who is given the output file generated by the delivery assistant (default mode for direct mail channel).

External accounts are configured via the **[!UICONTROL Administration > Platform > External accounts]** node. This configuration should be performed by expert users only.

## Email deliveries {#email-deliveries}

The [Email channel](about-email-channel.md) is one of the core channels in Adobe Campaign, allowing you to schedule and send personalized emails to specific targets.

You can send different types of emails:

* Single-send emails: emails that you can send once to a defined target. They are usually used to promote a specific content that would be prepared and sent only once (newsletter, promotional email, etc.).
* Recurring emails: in a campaign, send the same email regularly and aggregate each send and its reports on a periodic basis. The same email is sent, but usually to a different target, based on the eligible target for the day of the send. A common example is a birthday email. For more on this, refer to [Recurring deliveries](../../workflow/using/recurring-delivery.md).
* Transactional emails: unitary emails that are triggered based on your customers' behavior. Refer to [Transactional messaging](../../message-center/using/about-transactional-messaging.md).

To learn about delivery usage and recommendations, consult Campaign [Delivery best practices](delivery-best-practices.md).

For more on the different types of deliveries, refer to [this section](#types-of-deliveries).

## Mobile deliveries {#mobile-deliveries}

Adobe Campaign allows you to deliver [SMS](sms-channel.md) and [LINE](line-channel.md) messages on mobiles.

For SMS messages, you can create, modify, and personalize messages in text format only. You can also preview your SMS messages before they are sent.

For LINE messages, you can send text or images and links.

To deliver SMS or LINE messages to a mobile phone you need:

* An external account configured on the **[!UICONTROL Mobile (SMS)]** channel or on the **[!UICONTROL LINE]** channel. 
* An SMS or LINE delivery template that is correctly linked to this external account.

## Push notifications {#push-notifications}

Adobe Campaign allows you to send personalized and segmented [push notifications](about-mobile-app-channel.md) on iOS and Android mobile devices, through dedicated apps. Once configuration and integration steps have been performed, iOS and Android deliveries can be created and sent. You can also design rich notifications with images or videos.

## Direct mail {#direct-mail}

[Direct mail](about-direct-mail-channel.md) is an offline channel that allows you to personalize and generate the file required by direct mail providers. It gives you the possibility to mix online and offline channels in your customer journeys.

Online channels allow you to create your messages (email, SMS, mobile app delivery, etc.) and send them to your audience directly from Adobe Campaign. With offline channels, it is different. When you prepare a direct mail delivery, Adobe Campaign generates a file including all the targeted profiles and the chosen contact information (postal address for example). You will then be able to send this file to your direct mail provider who will take care of the actual sending.

## Other channels {#other-channels}

Adobe Campaign offers Telephone delivery template, which is used to create external deliveries. Using this channel implies you set up dedicated methodologies to process output files. Configuration steps are the same as for [Direct mail channel](about-direct-mail-channel.md).

>[!NOTE]
>
>The Telephone channel is not available out-of-the-box. Its implementation requires Adobe Consulting or an Adobe Partner to be engaged. Please reach out to your Adobe representative for more information.

In addition, 'Other' type deliveries use a specific technical template which does not execute a process: this lets them manage marketing actions executed outside of the Adobe Campaign platform.

This channel has no specific mechanism. It is a generic channel that has its own external account routing option, delivery template type and campaign workflow activity, just like any other communication channel available in Adobe Campaign.

This channel is designed for descriptive purposes only, for example to define deliveries for which you want to keep a trace of the target of a campaign performed in a tool other than Adobe Campaign.

## Types of deliveries{#types-of-deliveries}

There are three types of delivery objects in Campaign:

### Single delivery {#single-delivery}

A **delivery** is a standalone delivery object that is executed once. It can be duplicated, prepared again, but as long as it is in its final state (canceled, stopped, finished), it cannot be reused.

Deliveries can be created either from the list of deliveries, or within a workflow via a [Delivery](../../workflow/using/delivery.md) activity.

Workflows also provide specific delivery activities according to the type of channel you want to use. For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

### Recurring delivery {#recurring-delivery}

A **recurring delivery** lets you create a new delivery each time the activity is executed. This avoids you having to create a new delivery for recurring tasks.

As an example, if you run this type of activity once a month, you will end up with 12 deliveries after a year.

Recurring deliveries are created within workflows via the [Recurring delivery activity](../../workflow/using/recurring-delivery.md). An example of this activity being used is presented in this section: [Creating a recurring delivery in a targeting workflow](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Continuous delivery {#continuous-delivery}

A **continuous delivery** lets you add new recipients to an existing delivery, which avoids having to create a new delivery each time it is executed.

If an information in the delivery changes (content, name, etc.), a new delivery object is created at the delivery execution. If no information was changed, the same delivery object is reused and the delivery and tracking logs are added in the same object.

As an example, if you run this type of activity once a month, you will end up with a single delivery after a year (provided you did not make any change to the delivery).

Continuous deliveries are created within workflows via the [Continuous delivery activity](../../workflow/using/continuous-delivery.md).-->
