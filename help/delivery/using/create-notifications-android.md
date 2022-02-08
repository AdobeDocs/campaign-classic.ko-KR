---
product: campaign
title: Android 장치용 푸시 알림 만들기
description: Android용 푸시 알림을 만드는 방법을 알아봅니다
feature: Push
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 1%

---

# Android용 알림 만들기{#create-notificaations-android}

![](../../assets/common.svg)

Adobe Campaign을 사용하여 Android 장치에서 푸시 알림을 보냅니다. 게재 만들기에 대한 글로벌 개념은 [이 섹션](steps-about-delivery-creation-steps.md).

먼저 새 게재를 만듭니다.

![](assets/nmac_delivery_1.png)

Firebase Cloud Messaging을 사용하면 두 가지 유형의 메시지 중 하나를 선택할 수 있습니다.

* **[!UICONTROL Data message]**: 클라이언트 앱에 의해 처리됩니다.
   <br>메시지는 모바일 애플리케이션으로 직접 전송되어 Android 알림을 생성하여 장치에 표시합니다. 데이터 메시지에는 사용자 지정 애플리케이션 변수만 포함됩니다.

* **[!UICONTROL Notification message]**: FCM SDK에서 자동으로 처리합니다.
   <br> FCM은 클라이언트 앱을 대신하여 사용자의 장치에 메시지를 자동으로 표시합니다. 알림 메시지에는 사전 정의된 매개 변수 및 옵션 세트가 포함되어 있지만 사용자 지정 애플리케이션 변수를 사용하여 추가로 개인화할 수 있습니다.

Firebase Cloud 메시지 유형에 대한 자세한 내용은 [FCM 설명서](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages).

## 데이터 메시지 만들기 {#creating-data-message}

1. 이동 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

   ![](assets/nmac_android_3.png)

1. 선택 **[!UICONTROL Deliver on Android (android)]** 에서 **[!UICONTROL Delivery template]** 드롭다운. 추가 **[!UICONTROL Label]** 게재할 수도 있습니다.

1. 클릭 **[!UICONTROL To]** 타겟팅할 모집단을 정의하려면 기본적으로 **[!UICONTROL Subscriber application]** 대상 매핑이 적용됩니다. 클릭 **[!UICONTROL Add]** 을 클릭하여 서비스를 선택합니다.

   ![](assets/nmac_android_7.png)

1. 에서 **[!UICONTROL Target type]** 창, 선택 **[!UICONTROL Subscribers of an Android mobile application]** 을(를) 클릭합니다. **[!UICONTROL Next]**.

1. 에서 **[!UICONTROL Service]** 드롭다운에서 앞에서 만든 서비스를 선택하고 애플리케이션을 클릭한 다음 **[!UICONTROL Finish]**.
다음 **[!UICONTROL Application variables]** 은 구성 단계 동안 추가된 내용에 따라 자동으로 추가됩니다.

   ![](assets/nmac_android_6.png)

1. 선택 **[!UICONTROL data message]** 로서의 **[!UICONTROL Message Type]**.

1. 리치 알림을 편집합니다.

   ![](assets/nmac_android_5.png)

1. 이전에 구성한 내용에 정보를 추가할 수 있습니다 **[!UICONTROL Application variables]** 필요한 경우 **[!UICONTROL Application variables]** 는 Android 서비스에서 구성해야 하며, 모바일 장치로 전송되는 메시지 페이로드의 일부입니다.

1. 클릭 **[!UICONTROL Save]** 게재를 보낼 수 있습니다.

구독자의 모바일 Android 장치에서 수신한 경우 푸시 알림에 이미지 및 웹 페이지가 표시되어야 합니다.

![](assets/nmac_android_4.png)

## 알림 메시지 만들기 {#creating-notification-message}

>[!NOTE]
>
>알림 메시지에 대한 추가 옵션은 HTTP v1 API 구성에서만 사용할 수 있습니다. 자세한 정보는 이 [섹션](configuring-the-mobile-application-android.md#android-service-httpv1)을 참조하십시오.

![](assets/do-not-localize/how-to-video.png) [비디오에서 Android 푸시 알림을 만드는 방법을 알아봅니다](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=en#additional-resources)

1. 이동 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

   ![](assets/nmac_android_3.png)

1. 선택 **[!UICONTROL Deliver on Android (android)]** 에서 **[!UICONTROL Delivery template]** 드롭다운. 추가 **[!UICONTROL Label]** 게재할 수도 있습니다.

1. 클릭 **[!UICONTROL To]** 타겟팅할 모집단을 정의하려면 기본적으로 **[!UICONTROL Subscriber application]** 대상 매핑이 적용됩니다. 클릭 **[!UICONTROL Add]** 을 클릭하여 서비스를 선택합니다.

   ![](assets/nmac_android_7.png)

1. 에서 **[!UICONTROL Target type]** 창, 선택 **[!UICONTROL Subscribers of an Android mobile application]** 을(를) 클릭합니다. **[!UICONTROL Next]**.

1. 에서 **[!UICONTROL Service]** 드롭다운에서 앞에서 만든 서비스를 선택하고 애플리케이션을 클릭한 다음 **[!UICONTROL Finish]**.

   ![](assets/nmac_android_6.png)

1. 선택 **[!UICONTROL notification message]** 로서의 **[!UICONTROL Message Type]**.

1. 제목을 추가하고 메시지를 편집합니다. 를 사용하여 푸시 알림 개인화 **[!UICONTROL Notification options]**:

   * **[!UICONTROL Channel ID]**: 알림의 채널 ID를 설정합니다. 이 채널 ID의 알림을 수신하려면 먼저 앱이 이 채널 ID로 채널을 만들어야 합니다.
   * **[!UICONTROL Sound]**: 장치가 알림을 받을 때 재생할 사운드를 설정합니다.
   * **[!UICONTROL Color]**: 알림의 아이콘 색상을 설정합니다.
   * **[!UICONTROL Icon]**: 프로필의 장치에 표시할 알림의 아이콘을 설정합니다.
   * **[!UICONTROL Tag]**: 알림 서랍에서 기존 알림을 바꾸는 데 사용되는 식별자를 설정합니다.
   * **[!UICONTROL Click action]**: 알림에서 사용자 클릭과 연관된 작업을 설정합니다.

   자세한 내용은 **[!UICONTROL Notification options]** 이러한 필드를 채우는 방법은 [FCM 설명서](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_8.png)

1. 애플리케이션이 HTTP v1 API 프로토콜을 사용하여 구성된 경우 다음을 사용하여 푸시 알림을 추가로 개인화할 수 있습니다 **[!UICONTROL HTTPV1 additional options]**:

   * **[!UICONTROL Ticker]**: 알림의 티커 텍스트를 설정합니다. Android 5.0 Lollipop으로 설정된 장치에만 사용할 수 있습니다.
   * **[!UICONTROL Image]**: 알림에 표시할 이미지의 URL을 설정합니다.
   * **[!UICONTROL Notification Count]**: 애플리케이션 아이콘에 직접 표시하려면 읽지 않은 새로운 정보의 수를 설정합니다.
   * **[!UICONTROL Sticky]**: 를 true 또는 false로 설정합니다. false로 설정하면 사용자가 클릭하면 알림이 자동으로 해제됩니다. true로 설정하면 사용자가 클릭해도 알림이 계속 표시됩니다.
   * **[!UICONTROL Notification Priority]**: 알림의 우선 순위 수준을 기본값, 최소, 낮음 또는 높음으로 설정합니다. 자세한 내용은 [FCM 설명서](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**: 알림의 가시성 수준을 공개, 비공개 또는 비밀로 설정합니다. 자세한 내용은 [FCM 설명서](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   자세한 내용은 **[!UICONTROL HTTP v1 additional options]** 이러한 필드를 채우는 방법은 [FCM 설명서](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_9.png)

1. 이전에 구성한 내용에 정보를 추가할 수 있습니다 **[!UICONTROL Application variables]** 필요한 경우 **[!UICONTROL Application variables]** 는 Android 서비스에서 구성해야 하며, 모바일 장치로 전송되는 메시지 페이로드의 일부입니다.

1. 클릭 **[!UICONTROL Save]** 게재를 보낼 수 있습니다.

구독자의 모바일 Android 장치에서 수신한 경우 푸시 알림에 이미지 및 웹 페이지가 표시되어야 합니다.
