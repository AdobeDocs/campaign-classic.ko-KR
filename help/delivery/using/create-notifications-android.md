---
product: campaign
title: Android 장치에 대한 푸시 알림 만들기
description: Android용 푸시 알림을 만드는 방법 알아보기
feature: Push
role: User, Developer, Data Engineer
hide: true
hidefromtoc: true
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 89e350c727fb9379d28916f79d9749f22fd4974f
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Android에 대한 알림 만들기{#create-notificaations-android}

Adobe Campaign을 사용하여 Android 디바이스에서 푸시 알림을 보냅니다. 게재 만들기에 대한 전체 개념은 [이 섹션](steps-about-delivery-creation-steps.md)에 나와 있습니다.

새 게재를 만드는 것으로 시작합니다.

![](assets/nmac_delivery_1.png)

Firebase Cloud Messaging을 사용하면 두 가지 유형의 메시지 중에서 선택할 수 있습니다.

* **[!UICONTROL Data message]**(클라이언트 앱에서 처리됨).
  <br>android 알림을 생성하여 장치에 표시하는 모바일 응용 프로그램으로 직접 메시지를 보냅니다. 데이터 메시지에는 사용자 정의 애플리케이션 변수만 포함됩니다.

* **[!UICONTROL Notification message]**, FCM SDK에서 자동으로 처리됨.
  <br> FCM은 클라이언트 앱을 대신하여 사용자의 장치에 메시지를 자동으로 표시합니다. 알림 메시지에는 사전 정의된 매개 변수 및 옵션 세트가 포함되어 있지만 사용자 지정 애플리케이션 변수를 사용하여 추가로 개인화할 수 있습니다.

Firebase 클라우드 메시징 메시지 유형에 대한 자세한 내용은 [FCM 설명서](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages){target="_blank"}를 참조하십시오.


## 데이터 메시지 만들기 {#creating-data-message}

1. **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**(으)로 이동합니다.

1. **[!UICONTROL New]**&#x200B;을(를) 클릭합니다.

   ![](assets/nmac_android_3.png)

1. **[!UICONTROL Deliver on Android (android)]** 드롭다운에서 **[!UICONTROL Delivery template]** 선택. 게재에 **[!UICONTROL Label]** 추가

1. 타깃팅할 모집단을 정의하려면 **[!UICONTROL To]**&#x200B;을(를) 클릭하십시오. 기본적으로 **[!UICONTROL Subscriber application]** 대상 매핑이 적용됩니다. 서비스를 선택하려면 **[!UICONTROL Add]**&#x200B;을(를) 클릭하십시오.

   ![](assets/nmac_android_7.png)

1. **[!UICONTROL Target type]** 창에서 **[!UICONTROL Subscribers of an Android mobile application]**&#x200B;을(를) 선택하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL Service]** 드롭다운에서 이전에 만든 서비스를 선택한 다음 응용 프로그램을 선택하고 **[!UICONTROL Finish]**&#x200B;을(를) 클릭합니다.
구성 단계 중에 추가된 내용에 따라 **[!UICONTROL Application variables]**&#x200B;이(가) 자동으로 추가됩니다.

   ![](assets/nmac_android_6.png)

1. **[!UICONTROL data message]**&#x200B;을(를) **[!UICONTROL Message Type]**(으)로 선택합니다.

1. 리치 알림을 편집합니다.

   ![](assets/nmac_android_5.png)

1. 필요한 경우 이전에 구성한 **[!UICONTROL Application variables]**&#x200B;에 정보를 추가할 수 있습니다. **[!UICONTROL Application variables]**&#x200B;은(는) Android 서비스에서 구성해야 하며, 모바일 장치로 전송되는 메시지 페이로드의 일부입니다.

1. **[!UICONTROL Save]**&#x200B;을(를) 클릭하고 게재를 보냅니다.

구독자의 모바일 Android 장치에서 수신할 때 푸시 알림에 이미지와 웹 페이지가 표시되어야 합니다.

![](assets/nmac_android_4.png)

## 알림 메시지 만들기 {#creating-notification-message}

![](assets/do-not-localize/how-to-video.png) [비디오에서 Android 푸시 알림을 만드는 방법을 알아봅니다](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=ko#additional-resources){target="_blank"}.

1. **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**(으)로 이동합니다.

1. **[!UICONTROL New]**&#x200B;을(를) 클릭합니다.

   ![](assets/nmac_android_3.png)

1. **[!UICONTROL Deliver on Android (android)]** 드롭다운에서 **[!UICONTROL Delivery template]** 선택. 게재에 **[!UICONTROL Label]** 추가

1. 타깃팅할 모집단을 정의하려면 **[!UICONTROL To]**&#x200B;을(를) 클릭하십시오. 기본적으로 **[!UICONTROL Subscriber application]** 대상 매핑이 적용됩니다. 서비스를 선택하려면 **[!UICONTROL Add]**&#x200B;을(를) 클릭하십시오.

   ![](assets/nmac_android_7.png)

1. **[!UICONTROL Target type]** 창에서 **[!UICONTROL Subscribers of an Android mobile application]**&#x200B;을(를) 선택하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL Service]** 드롭다운에서 이전에 만든 서비스를 선택한 다음 응용 프로그램을 선택하고 **[!UICONTROL Finish]**&#x200B;을(를) 클릭합니다.

   ![](assets/nmac_android_6.png)

1. **[!UICONTROL notification message]**&#x200B;을(를) **[!UICONTROL Message Type]**(으)로 선택합니다.

1. 제목을 추가하고 메시지를 편집합니다. **[!UICONTROL Notification options]**&#x200B;을(를) 사용하여 푸시 알림 개인화:

   * **[!UICONTROL Channel ID]**: 알림의 채널 ID를 설정합니다. 이 채널 ID의 알림을 수신하려면 먼저 앱에서 이 채널 ID로 채널을 만들어야 합니다.
   * **[!UICONTROL Sound]**: 장치에서 알림을 받을 때 소리를 재생하도록 설정합니다.
   * **[!UICONTROL Color]**: 알림의 아이콘 색상을 설정합니다.
   * **[!UICONTROL Icon]**: 프로필 장치에 표시할 알림 아이콘을 설정합니다.
   * **[!UICONTROL Tag]**: 알림 대화 상자에서 기존 알림을 바꾸는 데 사용되는 식별자를 설정합니다.
   * **[!UICONTROL Click action]**: 알림에서 사용자 클릭과 관련된 작업을 설정합니다.

   **[!UICONTROL Notification options]** 및 이러한 필드를 채우는 방법에 대한 자세한 내용은 [FCM 설명서](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}를 참조하십시오.

   ![](assets/nmac_android_8.png)

1. 애플리케이션이 HTTP v1 API 프로토콜로 구성된 경우 다음 **[!UICONTROL HTTPV1 additional options]**&#x200B;을(를) 사용하여 푸시 알림을 추가로 개인화할 수 있습니다.

   * **[!UICONTROL Ticker]**: 알림의 티커 텍스트를 설정합니다. Android 5.0 Lollipop으로 설정된 장치에만 사용할 수 있습니다.
   * **[!UICONTROL Image]**: 알림에 표시할 이미지의 URL을 설정합니다.
   * **[!UICONTROL Notification Count]**: 응용 프로그램 아이콘에 직접 표시할 읽지 않은 새 정보의 수를 설정하십시오.
   * **[!UICONTROL Sticky]**: true 또는 false로 설정합니다. false로 설정하면 사용자가 클릭할 때 알림이 자동으로 해제됩니다. true로 설정하면 사용자가 알림을 클릭할 때에도 알림이 계속 표시됩니다.
   * **[!UICONTROL Notification Priority]**: 알림의 우선 순위 수준을 기본값, 최소, 낮음 또는 높음으로 설정합니다. 자세한 내용은 [FCM 설명서](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority)를 참조하세요.
   * **[!UICONTROL Visibility]**: 알림의 표시 수준을 공개, 비공개 또는 비밀로 설정합니다. 자세한 내용은 [FCM 설명서](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility)를 참조하세요.

   **[!UICONTROL HTTP v1 additional options]** 및 이러한 필드를 채우는 방법에 대한 자세한 내용은 [FCM 설명서](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}를 참조하십시오.

   ![](assets/nmac_android_9.png)

1. 필요한 경우 이전에 구성한 **[!UICONTROL Application variables]**&#x200B;에 정보를 추가할 수 있습니다. **[!UICONTROL Application variables]**&#x200B;은(는) Android 서비스에서 구성해야 하며, 모바일 장치로 전송되는 메시지 페이로드의 일부입니다.

1. **[!UICONTROL Save]**&#x200B;을(를) 클릭하고 게재를 보냅니다.

구독자의 모바일 Android 장치에서 수신할 때 푸시 알림에 이미지와 웹 페이지가 표시되어야 합니다.
