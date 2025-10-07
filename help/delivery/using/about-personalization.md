---
product: campaign
title: 개인화 시작하기
description: Campaign에서 메시지를 개인화하고 조건부 콘텐츠를 사용하는 방법을 알아봅니다
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Personalization
role: User
exl-id: 555082a2-1b62-4aa4-b80c-77b1a1ef9491
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 14%

---

# 개인화 시작하기{#about-personalization}

Adobe Campaign이 전달하는 메시지는 콘텐츠 또는 메시지 모양을 고려하여 여러 가지 방법으로 개인화할 수 있습니다. 이러한 방법은 특히 수신자 프로필에서 가져온 기준에 따라 결합할 수 있습니다. 이메일 게재의 경우 메시지의 **[!UICONTROL Source]** 탭에서 직접 JavaScript에서 게재의 요소 및 개인화 조건을 정의할 수 있습니다. 일반적으로 Adobe Campaign을 통해 다음을 수행할 수 있습니다.

* 메시지 형식을 개인화합니다. [메시지 내용](defining-the-email-content.md#message-content)을 참조하세요.
* 동적 개인화 필드를 삽입합니다. [개인화 필드](personalization-fields.md)를 참조하세요.
* 사전 정의된 개인화 블록을 삽입합니다. [개인화 블록](personalization-blocks.md)을 참조하세요.
* 조건부 콘텐츠 만들기 [조건부 콘텐츠](conditional-content.md) 섹션을 참조하십시오.

>[!CAUTION]
>
>다음 변수는 개인화에 사용할 수 있지만 수정할 수 없는 내부 변수입니다. **delivery**, **message**, **dataSource**, **targetData**, **공급자**, **coupon**, **couponValue**, **제안**.


Adobe Campaign을 통해 각 수신자의 프로필과 관심사에 맞는 메시지를 전송할 수 있도록 게재를 개인화할 수 있습니다.

Personalization을 사용하면 보다 관련성이 높고 매력적인 메시지를 만들 수 있습니다. 수신자 데이터를 사용하여 콘텐츠를 조정하거나, 동적 필드를 추가하거나, 조건에 따라 다른 정보를 표시할 수 있습니다. 게재에서 개인화 기능을 설정하고 사용하는 방법은 [Adobe Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=ko){target=_blank}를 참조하세요.

Campaign v8 프로모션 이니셔티브의 일부로 Campaign Classic 설명서가 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다.

>[!BEGINTABS]

>[!TAB 콘텐츠 개인화 설명서]

콘텐츠 개인화에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=ko){target=_blank}를 참조하세요.


[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=ko){target=_blank}


>[!TAB 전자 메일 게재 만들기]

Campaign v8 설명서에서 이메일 게재 만들기와 관련된 주요 단계를 알아봅니다.

* [전자 메일 게재를 만들기](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email.html?lang=ko){target="_blank"}: 전자 메일 게재를 만드는 데 필요한 여러 단계에 대해 알아봅니다.
* [전자 메일 콘텐츠 정의](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=ko){target="_blank"}: 보낸 사람, 제목, 콘텐츠, 이미지 등 전자 메일에 포함될 내용을 정의합니다.
* [대화형 콘텐츠 정의](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-interactive-content.html?lang=ko){target="_blank"}: 대화형 AMP for Email 형식을 사용하여 다이내믹 전자 메일을 보냅니다.
* [일본어 모바일에서 전자 메일 보내기](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/sending-emails-on-japanese-mobiles.html?lang=ko){target="_blank"}: 모바일에서 전자 메일에 세 가지 특정 일본어 형식 중 하나를 사용합니다.
* [전자 메일에 파일 첨부](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html?lang=ko){target="_blank"}: 전자 메일에 하나 이상의 파일을 첨부하는 다양한 방법을 알아봅니다.


>[!TAB 이메일 매개 변수]

Campaign v8 설명서에서 이메일 매개 변수에 대해 알아보려면 다음 페이지를 참조하십시오.

* [미러 페이지에 연결](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/mirror-page.html?lang=ko){target="_blank"}: 클라이언트가 항상 최상의 렌더링 환경을 얻을 수 있도록 미러 페이지를 구성하십시오.
* [BCC 주소 추가](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-bcc.html?lang=ko){target="_blank"}: 플랫폼에서 보낸 전자 메일의 복사본을 유지하도록 Adobe Campaign을 구성합니다.
* [추가 전자 메일 매개 변수 정의](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-parameters.html?lang=ko){target="_blank"}: 게재 속성에서 사용할 수 있는 옵션 및 매개 변수에 대해 자세히 알아보세요.

또한 이 [페이지](sending-with-enhanced-mta.md)를 참조하여 Enhanced MTA에 대해 알아보십시오.

>[!ENDTABS]





<!--
Adobe Campaign lets you mass deliver personalized electronic messages to a target population.

Before starting sending emails:

* Make sure recipient profiles contain at least an email address.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).
* Read out these sections to learn more about Deliverability: [Deliverability management in Campaign](about-deliverability.md) and [Deliverability best practices guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=ko).

The key steps to send an email are as follows:

* [Create an email delivery](creating-an-email-delivery.md)
* [Define the target population](steps-defining-the-target-population.md)
* [Define the email content](defining-the-email-content.md)
* [Send the email](sending-messages.md)
* [Monitor the delivery](about-delivery-monitoring.md)

The sections below provide information that is specific to the email channel. For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).
-->