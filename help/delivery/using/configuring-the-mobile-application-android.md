---
product: campaign
title: Adobe Campaign에서 Android 모바일 애플리케이션 구성
description: Android용 모바일 애플리케이션을 설정하는 방법을 알아봅니다
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 3%

---

# Android용 구성 단계

패키지가 설치되면 Adobe Campaign Classic에서 Android 앱 설정을 정의할 수 있습니다.

>[!NOTE]
>
>iOS용 앱을 구성하는 방법 및 iOS용 게재를 만드는 방법에 대해 알아보려면 이 항목을 참조하십시오 [섹션](configuring-the-mobile-application.md).

주요 단계는 다음과 같습니다.

1. [Android 외부 계정 구성](#configuring-external-account-android)
1. [Android 서비스 구성](#configuring-android-service)
1. [Campaign에서 모바일 앱 만들기](#creating-android-app)
1. [추가 데이터로 앱 스키마 확장](#extend-subscription-schema)

그러면 다음을 수행할 수 있습니다 [android 리치 알림 만들기](create-notifications-android.md).

## Android 외부 계정 구성 {#configuring-external-account-android}

Android의 경우 다음 두 개의 커넥터를 사용할 수 있습니다.

* MTA 1차 하위 구성요소당 하나의 연결을 허용하는 V1 커넥터입니다.
* FCM 서버에 대한 동시 연결을 통해 처리량을 향상시킬 수 있는 V2 커넥터입니다.

사용할 커넥터를 선택하려면 다음 단계를 수행하십시오.

1. 이동 **[!UICONTROL Administration > Platform > External accounts]**.
1. 을(를) 선택합니다 **[!UICONTROL Android routing]** 외부 계정.
1. 에서 **[!UICONTROL Connector]** 탭에서 을 입력합니다 **[!UICONTROL JavaScript used in the connector]** 필드:

   Android V2의 경우: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > https://localhost:8080/nms/jsp/androidPushConnector.js에 따라 구성할 수도 있지만 커넥터 버전 2를 사용하는 것이 좋습니다.

   ![](assets/nmac_connectors3.png)

1. Android V2의 경우 Adobe 서버 구성 파일(serverConf.xml)에서 한 개의 추가 매개 변수를 사용할 수 있습니다.

   * **maxGCMConnectPerChild**: 각 하위 서버에서 시작한 FCM에 대한 병렬 HTTP 요청의 최대 제한(기본적으로 8개).

## Android 서비스 구성 {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [비디오에서 Android 서비스를 구성하는 방법을 알아봅니다](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=en#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign)

1. 로 이동합니다. **[!UICONTROL Profiles and Targets > Services and subscriptions]** 노드 및 **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. 정의 **[!UICONTROL Label]** 그리고 **[!UICONTROL Internal name]**.
1. 로 이동합니다. **[!UICONTROL Type]** 필드 및 선택 **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >기본값 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 대상 매핑은 수신자 테이블에 연결됩니다. 다른 대상 매핑을 사용하려면 새 대상 매핑을 생성하고 여기에 입력해야 합니다 **[!UICONTROL Target mapping]** 서비스의 필드입니다. 대상 매핑 만들기에 대한 자세한 내용은 [이 섹션](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. 그런 다음 **[!UICONTROL Add]** 단추를 클릭하여 애플리케이션 유형을 선택합니다.

   ![](assets/nmac_service_2.png)

1. Android 애플리케이션을 만듭니다. 이 작업에 대한 자세한 정보는 [이 섹션](configuring-the-mobile-application-android.md#creating-android-app)을 참조하십시오.

## Android 모바일 애플리케이션 만들기 {#creating-android-app}

이제 서비스를 만든 후 Android 애플리케이션을 만들어야 합니다.

1. 새로 만든 서비스에서 **[!UICONTROL Add]** 단추를 클릭하여 애플리케이션 유형을 선택합니다.

   ![](assets/nmac_service_2.png)

1. 선택 **[!UICONTROL Create an Android application]** 을 입력하고 **[!UICONTROL Label]**.

   ![](assets/nmac_android.png)

1. 똑같이 **[!UICONTROL Integration key]** 는 Adobe Campaign에 정의되며, SDK를 통해 애플리케이션 코드에 정의됩니다. 이 작업에 대한 자세한 정보는 [이 섹션](integrating-campaign-sdk-into-the-mobile-application.md)을 참조하십시오.

   >[!NOTE]
   >
   > 다음 **[!UICONTROL Integration key]** 는 문자열 값으로 완전히 사용자 지정할 수 있지만 SDK에 지정된 값과 동일해야 합니다.

1. 을(를) 선택합니다 **[!UICONTROL API version]**: HTTP v1 또는 HTTP(기존). 이러한 구성은 다음에 자세히 설명되어 있습니다. [이 섹션](#select-api-version)

1. 을 입력합니다. **[!UICONTROL Firebase Cloud Messaging the Android connection settings]** 필드.

1. **[!UICONTROL Finish]**&#x200B;을(를) 클릭한 뒤 **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다. 이제 Android 애플리케이션을 Campaign Classic에서 사용할 준비가 되었습니다.

기본적으로 Adobe Campaign은 **[!UICONTROL User identifier]** (@userKey) 필드 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 테이블. 이 키를 사용하면 구독을 수신자에게 연결할 수 있습니다. 추가 데이터(예: 복잡한 조정 키)를 수집하려면 다음 구성을 적용해야 합니다.

### API 버전을 선택합니다{#select-api-version}

서비스 및 새 모바일 애플리케이션을 만든 후 선택한 API 버전에 따라 모바일 애플리케이션을 구성해야 합니다.

* **HTTP v1** 구성에 대해서는 [이 섹션](configuring-the-mobile-application-android.md#android-service-httpv1).
* **HTTP(기존)** 구성에 대해서는 [이 섹션](configuring-the-mobile-application-android.md#android-service-http).

#### HTTP v1 API 구성{#android-service-httpv1}

HTTP v1 API 버전을 구성하려면 아래 단계를 수행하십시오.

1. 사용자 **[!UICONTROL Mobile application creation wizard]** 창, 선택 **[!UICONTROL HTTPV1]** 에서 **[!UICONTROL API version]** 드롭다운.

1. 클릭 **[!UICONTROL Load project json file to extract project details...]** JSON 키 파일을 직접 로드하기 위해 를 참조하십시오. JSON 파일을 추출하는 방법에 대한 자세한 내용은 [이 페이지](https://firebase.google.com/docs/admin/setup#initialize-sdk).

   다음 세부 정보를 수동으로 입력할 수도 있습니다.
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. 클릭 **[!UICONTROL Test the connection]** 구성이 올바른지, 마케팅 서버가 FCM에 액세스할 수 있는지 확인하십시오.

   >[!CAUTION]
   >
   >중간 소싱 배포의 경우 **[!UICONTROL Test connection]** MID 서버가 FCM 서버에 액세스할 수 있는지 확인하려면 단추를 누릅니다.

   ![](assets/nmac_android_11.png)

1. 옵션은 일부 항목을 사용하여 푸시 메시지 콘텐츠를 보강할 수 있습니다 **[!UICONTROL Application variables]** 필요한 경우 사용자 지정할 수 있으며 모바일 장치로 전송되는 메시지 페이로드의 일부입니다.

1. **[!UICONTROL Finish]**&#x200B;을(를) 클릭한 뒤 **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다. 이제 Android 애플리케이션을 Campaign Classic에서 사용할 준비가 되었습니다.

푸시 알림을 추가로 개인화하기 위한 FCM 페이로드 이름은 다음과 같습니다.

| 메시지 유형 | 구성 가능한 메시지 요소(FCM 페이로드 이름) | 구성 가능한 옵션(FCM 페이로드 이름) |
|:-:|:-:|:-:|
| 데이터 메시지 | N/A | valid_only |
| 알림 메시지 | 제목, body, android_channel_id, 아이콘, 사운드, 태그, 색상, click_action, 이미지, 티커, 가시성, notification_priority, notification_count <br> | valid_only |

<br>
<br>

#### HTTP(기존) API 구성{#android-service-http}

HTTP(기존) API 버전을 구성하려면 아래 단계를 수행하십시오.

1. 사용자 **[!UICONTROL Mobile application creation wizard]** 창, 선택 **[!UICONTROL HTTP (legacy)]** 에서 **[!UICONTROL API version]** 드롭다운.

1. 을(를) 입력합니다. **[!UICONTROL Project key]** 모바일 애플리케이션 개발자가 제공했습니다.

1. 옵션은 일부 항목을 사용하여 푸시 메시지 콘텐츠를 보강할 수 있습니다 **[!UICONTROL Application variables]** 필요한 경우 사용자 지정할 수 있으며 모바일 장치로 전송되는 메시지 페이로드의 일부입니다.

   다음 예에서는 **제목**, **imageURL** 및 **iconURL** 리치 푸시 알림을 만든 다음, 알림 내에 표시할 이미지, 제목 및 아이콘을 애플리케이션에 제공합니다.

   ![](assets/nmac_android_2.png)

1. **[!UICONTROL Finish]**&#x200B;을(를) 클릭한 뒤 **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다. 이제 Android 애플리케이션을 Campaign Classic에서 사용할 준비가 되었습니다.

푸시 알림을 추가로 개인화하기 위한 FCM 페이로드 이름은 다음과 같습니다.

| 메시지 유형 | 구성 가능한 메시지 요소(FCM 페이로드 이름) | 구성 가능한 옵션(FCM 페이로드 이름) |
|:-:|:-:|:-:|
| 데이터 메시지 | 해당 없음 | dryRun |
| 알림 메시지 | 제목, 본문, android_channel_id, 아이콘, 사운드, 태그, 색상, click_action <br> | dryRun |

<br>

## appsubscriptionRcp 스키마 확장 {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [비디오에서 appsubscriptionRcp 스키마를 확장하는 방법을 알아보십시오.](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=en#extending-the-app-subscription-schema-to-personalize-push-notifications)

을(를) 확장해야 합니다 **appsubscriptionRcp** 앱의 매개 변수를 Campaign 데이터베이스에 저장할 새 추가 필드를 정의하려면 이러한 필드는 예를 들어 개인화에 사용됩니다. 방법은 다음과 같습니다.

1. 확장 만들기 **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** 스키마로 지정하고 새 필드를 정의합니다. 의 스키마 확장에 대해 자세히 알아보기 [이 페이지](../../configuration/using/about-schema-edition.md)

1. 에서 매핑을 정의합니다 **[!UICONTROL Subscription parameters]** 탭.

   >[!CAUTION]
   >
   >에서 구성 이름을 확인합니다. **[!UICONTROL Subscription parameters]** 탭은 모바일 애플리케이션 코드의 탭과 동일합니다. [이 섹션](integrating-campaign-sdk-into-the-mobile-application.md)을 참조하십시오.
