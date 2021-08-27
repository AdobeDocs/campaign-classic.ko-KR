---
product: campaign
title: 크로스 채널 게재
description: 크로스 채널 게재에 대해 자세히 알아보기
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 8%

---

# 크로스 채널 게재{#cross-channel-deliveries}

![](../../assets/common.svg)

크로스 채널 게재는 캠페인 워크플로우 활동의 **[!UICONTROL Deliveries]** 탭에서 사용할 수 있습니다.

사용할 수 있는 다양한 채널은 다음과 같습니다.

* [이메일](../../delivery/using/about-email-channel.md)
* [DM](../../delivery/using/about-direct-mail-channel.md)
* [모바일](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md) (Campaign Classic v7만 해당)
* [Facebook](../../social/using/publishing-on-facebook.md) (Campaign Classic v7만 해당)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

게재를 기반으로 할 템플릿을 선택하고 해당 콘텐츠를 정의합니다.

다른 타겟팅 활동을 사용하여 워크플로우의 게재 업스트림에 대한 타겟을 지정할 수 있습니다.

아래 예에서는 푸시 알림 가입자용 이메일 또는 SMS를 전송하는 워크플로우를 만든 다음 1주일 후 푸시 알림을 만듭니다. 방법은 다음과 같습니다.

1. 캠페인 만들기.
1. 캠페인의 **[!UICONTROL Targeting and workflows]** 탭에서 워크플로우에 **[!UICONTROL Query]** 를 추가합니다.
1. 쿼리를 구성합니다. 예를 들어 여기서는 푸시 알림을 구독하는 수신자를 타겟 차원으로 선택합니다.

   >[!NOTE]
   >
   >푸시 알림의 경우 **가입자 응용 프로그램** 대상 차원을 사용합니다.

   ![](assets/cross_channel_delivery_1.png)

1. 쿼리에 필터 조건을 추가합니다. 이 경우 모바일 번호 또는 이메일 주소가 있는 수신자를 선택합니다.

   ![](assets/cross_channel_delivery_2.png)

1. 워크플로우에 **[!UICONTROL Split]** 활동을 추가하여 모바일 번호가 있는 수신자와 이메일 주소가 있는 수신자를 나눕니다.
1. **[!UICONTROL Delivery]** 탭에서 각 대상에 대한 게재를 선택합니다.

   워크플로우에서 게재 활동을 두 번 클릭하여 클래식 게재 마법사와 동일한 방식으로 게재를 만듭니다. 자세한 정보는 이 [페이지](../../delivery/using/about-email-channel.md)를 참조하십시오.

   ![](assets/cross_channel_delivery_3.png)

1. 수신자가 한 번에 너무 많은 게재를 받지 않도록 **[!UICONTROL Wait]** 활동을 추가하고 구성합니다.
1. **[!UICONTROL Split]** 활동을 추가하여 iOS 또는 Android 모바일 애플리케이션의 구독자를 분할합니다.

   각 운영 체제에 대한 서비스를 선택합니다. 서비스 만들기에 대한 자세한 내용은 이 [페이지](../../delivery/using/configuring-the-mobile-application.md)를 참조하십시오.

   ![](assets/cross_channel_delivery_4.png)

1. 각 운영 체제에 대한 모바일 애플리케이션 전달을 선택하고 구성합니다.

   ![](assets/cross_channel_delivery_5.png)
