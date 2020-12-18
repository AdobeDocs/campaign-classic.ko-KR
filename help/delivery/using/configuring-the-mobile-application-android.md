---
solution: Campaign Classic
product: campaign
title: Adobe Campaign에서 Android 모바일 응용 프로그램 구성
description: Android용 모바일 애플리케이션 설정 방법 살펴보기
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1d7d48f52f69e4902eafa6806c2cd9170c21fe5a
workflow-type: tm+mt
source-wordcount: '1648'
ht-degree: 2%

---


# Android용 구성 단계

패키지가 설치되면 Adobe Campaign Classic에서 Android 앱 설정을 정의할 수 있습니다.

>[!NOTE]
>
>iOS용 앱을 구성하는 방법과 iOS용 배달을 만드는 방법에 대해 알아보려면 이 [섹션](../../delivery/using/configuring-the-mobile-application.md)을 참조하십시오.

주요 단계는 다음과 같습니다.

1. [Android 외부 계정 구성](#configuring-external-account-android)
1. [Android 서비스 구성](#configuring-android-service)
1. [Campaign에서 모바일 앱 만들기](#creating-android-app)
1. [추가 데이터로 앱 스키마 확장](#extend-subscription-schema)

그러면 [Android 리치 알림](#creating-android-delivery)을 만들 수 있습니다.

## Android 외부 계정 {#configuring-external-account-android} 구성

Android의 경우 다음 두 개의 커넥터를 사용할 수 있습니다.

* MTA 자식당 한 개의 연결을 허용하는 V1 커넥터입니다.
* FCM 서버에 동시에 연결하여 처리량을 높일 수 있는 V2 커넥터입니다.

사용할 커넥터를 선택하려면 다음 단계를 따르십시오.

1. **[!UICONTROL Administration > Platform > External accounts]**&#x200B;으로 이동합니다.
1. **[!UICONTROL Android routing]** 외부 계정을 선택합니다.
1. **[!UICONTROL Connector]** 탭에서 **[!UICONTROL JavaScript used in the connector]** 필드를 채웁니다.

   Android V2의 경우:https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > https://localhost:8080/nms/jsp/androidPushConnector.js에 따라 구성할 수도 있지만 커넥터 버전 2를 사용하는 것이 좋습니다.

   ![](assets/nmac_connectors3.png)

1. Android V2의 경우 Adobe 서버 구성 파일(serverConf.xml)에서 하나의 추가 매개 변수를 사용할 수 있습니다.

   * **maxGCMConnectPerChild**:각 하위 서버에서 시작한 FCM에 대한 병렬 HTTP 요청의 최대 제한(기본적으로 8개).

## Android 서비스 {#configuring-android-service} 구성

![](assets/do-not-localize/how-to-video.png) [비디오에서 Android 서비스를 구성하는 방법 학습](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=en#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign)

1. **[!UICONTROL Profiles and Targets > Services and subscriptions]** 노드로 이동하고 **[!UICONTROL New]**&#x200B;을 클릭합니다.

   ![](assets/nmac_service_1.png)

1. **[!UICONTROL Label]** 및 **[!UICONTROL Internal name]**&#x200B;을 정의합니다.
1. **[!UICONTROL Type]** 필드로 이동하여 **[!UICONTROL Mobile application]**&#x200B;을 선택합니다.

   >[!NOTE]
   >
   >기본 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 대상 매핑이 받는 사람 테이블에 연결되어 있습니다. 다른 대상 매핑을 사용하려면 새 대상 매핑을 만들고 서비스의 **[!UICONTROL Target mapping]** 필드에 입력해야 합니다. 대상 매핑 만들기에 대한 자세한 내용은 [구성 안내서](../../configuration/using/about-custom-recipient-table.md)를 참조하십시오.

   ![](assets/nmac_ios.png)

1. 그런 다음 **[!UICONTROL Add]** 단추를 클릭하여 응용 프로그램 유형을 선택합니다.

   ![](assets/nmac_service_2.png)

1. Android 응용 프로그램을 만듭니다. 자세한 정보는 이 [섹션](../../delivery/using/configuring-the-mobile-application-android.md#creating-android-app)을 참조하십시오.

## Android 모바일 응용 프로그램 {#creating-android-app} 만들기

서비스를 만든 후 이제 Android 응용 프로그램을 만들어야 합니다.

1. 새로 만든 서비스에서 **[!UICONTROL Add]** 단추를 클릭하여 응용 프로그램 유형을 선택합니다.

   ![](assets/nmac_service_2.png)

1. **[!UICONTROL Create an Android application]**&#x200B;을 선택하고 **[!UICONTROL Label]**&#x200B;을 입력합니다.

   ![](assets/nmac_android.png)

1. SDK를 통해 Adobe Campaign 및 응용 프로그램 코드에서 동일한 **[!UICONTROL Integration key]**&#x200B;이(가) 정의되어 있는지 확인합니다. 자세한 내용은 다음을 참조하십시오.[모바일 응용 프로그램](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)에 캠페인 SDK를 통합합니다.

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]**&#x200B;은 문자열 값으로 완전히 사용자 지정이 가능하지만 SDK에 지정된 값과 정확히 같아야 합니다.

1. **[!UICONTROL API version]** 선택:HTTP v1 또는 HTTP(레거시). 이러한 구성은 [이 섹션](#select-api-version)에 자세히 설명되어 있습니다.

1. **[!UICONTROL Firebase Cloud Messaging the Android connection settings]** 필드를 채웁니다.

1. **[!UICONTROL Finish]**&#x200B;을(를) 클릭한 뒤 **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다. 이제 Android 응용 프로그램을 Campaign Classic에서 사용할 준비가 되었습니다.

기본적으로 Adobe Campaign은 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 테이블의 **[!UICONTROL User identifier]** (@userKey) 필드에 키를 저장합니다. 이 키를 사용하면 구독을 수신자에게 연결할 수 있습니다. 추가 데이터(예: 복잡한 조정 키)를 수집하려면 다음 구성을 적용해야 합니다.

### API 버전{#select-api-version} 선택

서비스 및 새 모바일 애플리케이션을 만든 후 선택한 API 버전에 따라 모바일 애플리케이션을 구성해야 합니다.

* **HTTP v1** 구성은 이 섹션에  [자세히 설명되어 있습니다](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1).
* **HTTP(기존)** 구성은 이 섹션에  [자세히 설명되어 있습니다](../../delivery/using/configuring-the-mobile-application-android.md#android-service-http).

#### HTTP v1 API{#android-service-httpv1} 구성

HTTP v1 API 버전을 구성하려면 아래 단계를 따르십시오.

1. **[!UICONTROL Mobile application creation wizard]** 창의 **[!UICONTROL API version]** 드롭다운에서 **[!UICONTROL HTTPV1]**&#x200B;을 선택합니다.

1. **[!UICONTROL Load project json file to extract projet details...]**&#x200B;을 클릭하여 JSON 키 파일을 직접 로드합니다. JSON 파일을 추출하는 방법에 대한 자세한 내용은 이 [페이지](https://firebase.google.com/docs/admin/setup#initialize-sdk)를 참조하십시오.

   다음 세부 정보를 수동으로 입력할 수도 있습니다.
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. **[!UICONTROL Test the connection]**&#x200B;을(를) 클릭하여 구성이 올바르고 마케팅 서버에서 FCM에 액세스할 수 있는지 확인합니다.

   >[!CAUTION]
   >
   >중간 소싱 배포의 경우 MID 서버가 FCM 서버에 액세스할 수 있는지 여부를 **[!UICONTROL Test connection]** 버튼이 확인하지 않습니다.

   ![](assets/nmac_android_11.png)

1. 필요한 경우 일부 **[!UICONTROL Application variables]**&#x200B;로 푸시 메시지 내용을 보강할 수 있습니다. 이러한 구성 요소는 사용자 지정이 가능하고 모바일 장치에 전송된 메시지 페이로드의 일부입니다.

1. **[!UICONTROL Finish]**&#x200B;을(를) 클릭한 뒤 **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다. 이제 Android 응용 프로그램을 Campaign Classic에서 사용할 준비가 되었습니다.

다음은 푸시 알림을 보다 개인화하기 위한 FCM 페이로드 이름입니다.

| 메시지 유형 | 구성 가능한 메시지 요소(FCM 페이로드 이름) | 구성 가능한 옵션(FCM 페이로드 이름) |
|:-:|:-:|:-:|
| 데이터 메시지 | N/A | valid_only |
| 알림 메시지 | 제목, body, android_channel_id, 아이콘, 사운드, 태그, 색상, click_action, 이미지, 티커, 고정, 가시성, 알림_우선 순위, 알림_count <br> | valid_only |

<br>
<br>

#### HTTP(레거시) API{#android-service-http} 구성

HTTP(기존) API 버전을 구성하려면 아래 단계를 따르십시오.

1. **[!UICONTROL Mobile application creation wizard]** 창의 **[!UICONTROL API version]** 드롭다운에서 **[!UICONTROL HTTP (legacy)]**&#x200B;을 선택합니다.

1. 모바일 응용 프로그램 개발자가 제공한 **[!UICONTROL Project key]**&#x200B;을 입력합니다.

1. 필요한 경우 일부 **[!UICONTROL Application variables]**&#x200B;로 푸시 메시지 내용을 보강할 수 있습니다. 이러한 구성 요소는 사용자 지정이 가능하고 모바일 장치에 전송된 메시지 페이로드의 일부입니다.

   다음 예제에서는 **title**, **imageURL** 및 **iconURL**&#x200B;을 추가하여 리치 푸시 알림을 만든 다음 응용 프로그램에 알림 내에 표시할 이미지, 제목 및 아이콘을 제공합니다.

   ![](assets/nmac_android_2.png)

1. **[!UICONTROL Finish]**&#x200B;을(를) 클릭한 뒤 **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다. 이제 Android 응용 프로그램을 Campaign Classic에서 사용할 준비가 되었습니다.

다음은 푸시 알림을 보다 개인화하기 위한 FCM 페이로드 이름입니다.

| 메시지 유형 | 구성 가능한 메시지 요소(FCM 페이로드 이름) | 구성 가능한 옵션(FCM 페이로드 이름) |
|:-:|:-:|:-:|
| 데이터 메시지 | 해당 없음 | dryRun |
| 알림 메시지 | 제목, 본문, android_channel_id, 아이콘, 사운드, 태그, 색상, click_action <br> | dryRun |

<br>

## appsubscriptionRcp 스키마 확장 {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [비디오에서 appsubscriptionRcp 스키마를 확장하는 방법 알아보기](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=en#extending-the-app-subscription-schema-to-personalize-push-notifications)

Campaign 데이터베이스의 앱에서 매개 변수를 저장할 새 추가 필드를 정의하려면 **appsubscriptionRcp**&#x200B;을 확장해야 합니다. 이러한 필드는 개인화에 사용됩니다. 방법은 다음과 같습니다.

1. **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** 스키마의 확장을 만들고 새 필드를 정의합니다. [이 페이지](../../configuration/using/about-schema-edition.md)의 스키마 확장에 대해 자세히 알아보기

1. **[!UICONTROL Subscription parameters]** 탭에서 매핑을 정의합니다.

   >[!CAUTION]
   >
   >**[!UICONTROL Subscription parameters]** 탭의 구성 이름이 모바일 응용 프로그램 코드의 구성 이름과 동일한지 확인합니다. [모바일 응용 프로그램](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md) 섹션에 캠페인 SDK 통합을 참조하십시오.

## Android 리치 알림 만들기 {#creating-android-delivery}

Firebase Cloud Messaging을 사용하면 다음과 같은 두 가지 메시지 유형을 선택할 수 있습니다.

* **[!UICONTROL Data message]**, 클라이언트 앱에서 처리됨.
   <br>메시지는 Android 알림을 생성하여 장치에 표시하는 모바일 응용 프로그램으로 바로 전송됩니다. 데이터 메시지에는 사용자 지정 응용 프로그램 변수만 포함됩니다.

* **[!UICONTROL Notification message]**, FCM SDK에 의해 자동으로 처리됩니다.
   <br> FCM은 클라이언트 앱을 대신하여 사용자의 장치에 메시지를 자동으로 표시합니다. 알림 메시지에는 사전 정의된 매개 변수 및 옵션 세트가 포함되어 있지만 사용자 지정 애플리케이션 변수를 사용하여 추가로 개인화할 수 있습니다.

Firebase 클라우드 메시지 유형에 대한 자세한 내용은 [FCM 설명서](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages)를 참조하십시오.

### 데이터 메시지 {#creating-data-message} 만들기

1. **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**&#x200B;로 이동합니다.

1. **[!UICONTROL New]**&#x200B;을(를) 클릭합니다.

   ![](assets/nmac_android_3.png)

1. **[!UICONTROL Delivery template]** 드롭다운에서 **[!UICONTROL Deliver on Android (android)]**&#x200B;을 선택합니다. 배달에 **[!UICONTROL Label]**&#x200B;을(를) 추가합니다.

1. 타게팅할 모집단을 정의하려면 **[!UICONTROL To]**&#x200B;을 클릭합니다. 기본적으로 **[!UICONTROL Subscriber application]** 대상 매핑이 적용됩니다. **[!UICONTROL Add]**&#x200B;을 클릭하여 서비스를 선택합니다.

   ![](assets/nmac_android_7.png)

1. **[!UICONTROL Target type]** 창에서 **[!UICONTROL Subscribers of an Android mobile application]**&#x200B;을 선택하고 **[!UICONTROL Next]**&#x200B;를 클릭합니다.

1. **[!UICONTROL Service]** 드롭다운에서 이전에 만든 서비스를 선택한 다음 애플리케이션을 선택하고 **[!UICONTROL Finish]** 을 클릭합니다.
구성 단계 동안 추가된 내용에 따라 **[!UICONTROL Application variables]**&#x200B;이 자동으로 추가됩니다.

   ![](assets/nmac_android_6.png)

1. **[!UICONTROL data message]**&#x200B;을 **[!UICONTROL Message Type]**(으)로 선택합니다.

1. 리치 알림을 편집합니다.

   ![](assets/nmac_android_5.png)

1. 필요한 경우 이전에 구성한 **[!UICONTROL Application variables]**&#x200B;에 정보를 추가할 수 있습니다. **[!UICONTROL Application variables]** Android 서비스에서 구성해야 하며 모바일 장치에 전송된 메시지 페이로드의 일부입니다.

1. **[!UICONTROL Save]**&#x200B;을 클릭하고 배달을 보냅니다.

구독자의 모바일 Android 장치에서 수신할 때 푸시 알림에 이미지 및 웹 페이지가 표시되어야 합니다.

![](assets/nmac_android_4.png)

### 알림 메시지 {#creating-notification-message} 만들기

>[!NOTE]
>
>알림 메시지에 대한 추가 옵션은 HTTP v1 API 구성에서만 사용할 수 있습니다. 자세한 정보는 이 [섹션](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1)을 참조하십시오.

![](assets/do-not-localize/how-to-video.png) [비디오에서 Android 푸시 알림을 만드는 방법 학습](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=en#additional-resources)

1. **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**&#x200B;로 이동합니다.

1. **[!UICONTROL New]**&#x200B;을(를) 클릭합니다.

   ![](assets/nmac_android_3.png)

1. **[!UICONTROL Delivery template]** 드롭다운에서 **[!UICONTROL Deliver on Android (android)]**&#x200B;을 선택합니다. 배달에 **[!UICONTROL Label]**&#x200B;을(를) 추가합니다.

1. 타게팅할 모집단을 정의하려면 **[!UICONTROL To]**&#x200B;을 클릭합니다. 기본적으로 **[!UICONTROL Subscriber application]** 대상 매핑이 적용됩니다. **[!UICONTROL Add]**&#x200B;을 클릭하여 서비스를 선택합니다.

   ![](assets/nmac_android_7.png)

1. **[!UICONTROL Target type]** 창에서 **[!UICONTROL Subscribers of an Android mobile application]**&#x200B;을 선택하고 **[!UICONTROL Next]**&#x200B;를 클릭합니다.

1. **[!UICONTROL Service]** 드롭다운에서 이전에 만든 서비스를 선택한 다음 애플리케이션을 선택하고 **[!UICONTROL Finish]** 을 클릭합니다.

   ![](assets/nmac_android_6.png)

1. **[!UICONTROL notification message]**&#x200B;을 **[!UICONTROL Message Type]**(으)로 선택합니다.

1. 제목을 추가하고 메시지를 편집합니다. 푸시 알림을 **[!UICONTROL Notification options]**&#x200B;으로 개인화합니다.

   * **[!UICONTROL Channel ID]**:알림의 채널 ID를 설정합니다. 이 채널 ID의 알림을 수신하려면 먼저 앱이 이 채널 ID로 채널을 만들어야 합니다.
   * **[!UICONTROL Sound]**:장치가 알림을 받을 때 사운드가 재생되도록 설정합니다.
   * **[!UICONTROL Color]**:알림의 아이콘 색상을 설정합니다.
   * **[!UICONTROL Icon]**:알림의 아이콘을 설정하여 프로필의 장치에 표시합니다.
   * **[!UICONTROL Tag]**:알림 드로어의 기존 알림을 대체하는 데 사용되는 식별자를 설정합니다.
   * **[!UICONTROL Click action]**:알림에 대한 사용자 클릭과 관련된 작업을 설정합니다.

   **[!UICONTROL Notification options]** 및 이러한 필드를 채우는 방법에 대한 자세한 내용은 [FCM 설명서](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification)를 참조하십시오.

   ![](assets/nmac_android_8.png)

1. 응용 프로그램이 HTTP v1 API 프로토콜로 구성된 경우 다음 **[!UICONTROL HTTPV1 additional options]**&#x200B;으로 푸시 알림을 추가로 개인화할 수 있습니다.

   * **[!UICONTROL Ticker]**:알림의 티커 텍스트를 설정합니다. Android 5.0 Lollipop로 설정된 장치에만 사용할 수 있습니다.
   * **[!UICONTROL Image]**:알림에 표시할 이미지의 URL을 설정합니다.
   * **[!UICONTROL Notification Count]**:새 읽지 않은 정보의 수를 애플리케이션 아이콘에 직접 표시하도록 설정합니다.
   * **[!UICONTROL Sticky]**:true 또는 false로 설정합니다. false로 설정하면 사용자가 해당 알림을 클릭하면 알림이 자동으로 사라집니다. true로 설정된 경우 사용자가 알림을 클릭해도 알림이 계속 표시됩니다.
   * **[!UICONTROL Notification Priority]**:알림의 우선 순위 수준을 기본값, 최소, 낮음 또는 높음으로 설정합니다. 자세한 내용은 [FCM 설명서](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority)를 참조하십시오.
   * **[!UICONTROL Visibility]**:알림의 가시성 수준을 공개, 비공개 또는 기밀로 설정합니다. 자세한 내용은 [FCM 설명서](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility)를 참조하십시오.

   **[!UICONTROL HTTP v1 additional options]** 및 이러한 필드를 채우는 방법에 대한 자세한 내용은 [FCM 설명서](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification)를 참조하십시오.

   ![](assets/nmac_android_9.png)

1. 필요한 경우 이전에 구성한 **[!UICONTROL Application variables]**&#x200B;에 정보를 추가할 수 있습니다. **[!UICONTROL Application variables]** Android 서비스에서 구성해야 하며 모바일 장치에 전송된 메시지 페이로드의 일부입니다.

1. **[!UICONTROL Save]**&#x200B;을 클릭하고 배달을 보냅니다.

구독자의 모바일 Android 장치에서 수신할 때 푸시 알림에 이미지 및 웹 페이지가 표시되어야 합니다.
