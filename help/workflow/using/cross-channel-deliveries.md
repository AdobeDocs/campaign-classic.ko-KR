---
product: campaign
title: 크로스 채널 게재
description: 크로스 채널 게재에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Channels Activity
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 8%

---

# 크로스 채널 게재{#cross-channel-deliveries}



크로스 채널 게재는 **[!UICONTROL Deliveries]** campaign 워크플로우 활동의 탭.

사용할 수 있는 다양한 채널은 다음과 같습니다.

* [이메일](../../delivery/using/about-email-channel.md)
* [DM](../../delivery/using/about-direct-mail-channel.md)
* [모바일](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/about-social-marketing.md)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

게재를 기반으로 할 템플릿을 선택하고 해당 콘텐츠를 정의합니다.

다양한 타겟팅 활동을 사용하여 워크플로우의 게재 업스트림에 대한 타겟을 지정할 수 있습니다.

아래 예에서는 푸시 알림 가입자용 이메일 또는 SMS를 전송하는 워크플로우를 만든 다음 1주일 후 푸시 알림을 만듭니다. 방법은 다음과 같습니다.

1. 캠페인 만들기.
1. 에서 **[!UICONTROL Targeting and workflows]** 캠페인의 탭에서 다음을 추가합니다 **[!UICONTROL Query]** 을 워크플로우에 추가합니다.
1. 쿼리를 구성합니다. 예를 들어 여기서는 푸시 알림을 구독하는 수신자를 타겟 차원으로 선택합니다.

   >[!NOTE]
   >
   >푸시 알림의 경우 **가입자 응용 프로그램** 대상 차원.

   ![](assets/cross_channel_delivery_1.png)

1. 쿼리에 필터 조건을 추가합니다. 이 경우 모바일 번호 또는 이메일 주소가 있는 수신자를 선택합니다.

   ![](assets/cross_channel_delivery_2.png)

1. 추가 **[!UICONTROL Split]** 활동을 워크플로우에 추가하여 모바일 번호가 있는 수신자와 이메일 주소가 있는 수신자를 구분할 수 있습니다.
1. 에서 **[!UICONTROL Delivery]** 탭에서 각 타겟에 대한 게재를 선택합니다.

   워크플로우에서 게재 활동을 두 번 클릭하여 클래식 게재 마법사와 동일한 방식으로 게재를 만듭니다. 자세한 정보는 이 [페이지](../../delivery/using/about-email-channel.md)를 참조하십시오.

   ![](assets/cross_channel_delivery_3.png)

1. 추가 및 구성 **[!UICONTROL Wait]** 받는 사람이 한 번에 너무 많은 게재를 받지 않도록 하는 활동.
1. 추가 **[!UICONTROL Split]** 활동을 통해 iOS 또는 Android 모바일 애플리케이션의 구독자를 분할합니다.

   각 운영 체제에 대한 서비스를 선택합니다. 서비스 만들기에 대한 자세한 내용은 다음을 참조하십시오 [페이지](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. 각 운영 체제에 대한 모바일 애플리케이션 전달을 선택하고 구성합니다.

   ![](assets/cross_channel_delivery_5.png)
