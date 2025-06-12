---
product: campaign
title: SMS 채널 시작
description: SMS 채널 시작
feature: SMS
role: User
exl-id: 6fc2ab09-8ea7-4865-88ad-bd45eee68958
source-git-commit: d3d731c64cb5a430de6adac3aeb326f74134c436
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# SMS 채널 시작{#sms-channel}

Adobe Campaign을 사용하여 모바일 장치에서 고객에게 문자 메시지를 보낼 수 있습니다. SMS 편집기에서 텍스트 형식의 메시지를 만들고, 개인화하고, 미리 볼 수 있습니다.

SMS는 사용자가 어디에 있든지 사용자에게 연락할 수 있는 직접적이고 매우 효과적인 채널입니다. 높은 공개 비율과 거의 즉각적인 전달을 제공하는 SMS는 시간에 민감한 경고, 트랜잭션 업데이트 및 간결한 프로모션 메시지에 이상적입니다. SMS를 사용하여 크로스 채널 전략을 보완하고 효과적인 실시간 커뮤니케이션을 제공합니다. [Adobe Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=ko){target=_blank}에서 SMS 채널을 효과적으로 구성하고 사용하는 방법을 알아보세요.

Campaign v8 프로모션 이니셔티브의 일부로 Campaign Classic 설명서가 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다.

>[!BEGINTABS]

>[!TAB SMS 채널 설명서]

SMS 채널에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=ko){target=_blank}를 참조하세요.


[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=ko){target=_blank}


>[!TAB SMS 게재 만들기]

Campaign v8 설명서에서 SMS 게재 만들기와 관련된 주요 단계를 알아봅니다.

* [SMS 채널 개요](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=ko){target="_blank"}: 모바일 장치에서 고객에게 문자 메시지를 보내는 방법을 알아봅니다.
* [SMS 게재 만들기](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/create-sms.html?lang=ko){target="_blank"}: 새 SMS 게재를 만드는 데 필요한 여러 단계를 살펴봅니다.
* [콘텐츠 정의](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/sms-content.html?lang=ko){target="_blank"}: SMS 메시지의 콘텐츠를 개인화하는 방법을 알아봅니다.
* [대상 선택](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/sms-audience.html?lang=ko){target="_blank"}: 기본 대상은 Adobe Campaign 데이터베이스에서 추출되거나 외부 파일에도 저장될 수 있습니다.
* [SMS 증명 보내기](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/validate-sms/sms-proofs.html?lang=ko): 게재 유효성 검사 주기를 설정해야 합니다. 대상자에게 콘텐츠를 보내기 전에 콘텐츠가 승인되었는지 확인하십시오.
* [대상자에게 보내기](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/validate-sms/sms-send.html?lang=ko): 이제 SMS의 유효성을 검사하면 대상자에게 보낼 수 있습니다.
* [SMS 모니터링 및 추적](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms-monitor.html?lang=ko): 마케팅 캠페인이 효율적으로 수행되도록 SMS 게재를 모니터링합니다.


>[!TAB SMS 구성]

SMS 구성에 대한 자세한 내용은 다음 페이지를 참조하십시오.

* [독립 실행형 구성](sms-set-up.md): 독립 실행형 인스턴스에서 SMS 채널을 구성하는 방법을 알아봅니다.
* [중간 소싱 구성](sms-set-up-mid.md): 중간 서버를 사용하여 휴대폰으로 보내는 방법을 알아봅니다.
* [SMS 커넥터](sms-protocol.md): SMS 커넥터 프로토콜 및 설정에 대해 알아봅니다.
* [추가 구성](sms-send.md): 고급 매개 변수 및 기타 추가 구성에 대해 알아봅니다.
* [문제 해결](troubleshooting-sms.md): 일련의 잠재적 문제와 해결 방법을 나열했습니다.

>[!ENDTABS]



<!--
Use Adobe Campaign to send personalized SMS messages.

Before starting sending SMS:

* Make sure recipient profiles contain at least a mobile phone in their profile.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).

The key steps to send a SMS are as follows:

* [Configure the SMS channel](sms-set-up.md)
* [Create a SMS delivery](sms-create.md)
* [Define the audience](sms-create.md#selecting-the-target-population)
* [Define the SMS content](sms-create.md#defining-the-sms-content)
* [Send, monitor and track SMS](sms-send.md)
* [Troubleshoot](troubleshooting-sms.md)

In addition, you need to be familiar with SMS protocol and settings. Walk through the connection set up between Adobe Campaign and a SMPP provider in [this document](sms-protocol.md)

For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).

>[!NOTE]
>
>Adobe Campaign also lets you submit notifications on mobile terminals, via its **Adobe Campaign Mobile App Channel (NMAC)** option. 
> 
>For more on this, refer to the [Get started with mobile app channel](about-mobile-app-channel.md) section.
-->