---
solution: Campaign Classic
product: campaign
title: Adobe Campaign에서 iOS 모바일 애플리케이션 구성
description: iOS용 모바일 애플리케이션 설정 방법 살펴보기
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 7%

---


# iOS용 구성 단계 {#configuring-the-mobile-application-in-adobe-campaign-ios}

패키지가 설치되면 Adobe Campaign Classic에서 iOS 앱 설정을 정의할 수 있습니다.

>[!NOTE]
>
>Android용 앱을 구성하는 방법과 Android용 배달을 만드는 방법에 대해 알아보려면 이 [섹션을 참조하십시오](../../delivery/using/configuring-the-mobile-application-android.md).

## iOS 외부 계정 구성 {#configuring-external-account-ios}

iOS의 경우 iOS HTTP/2 커넥터는 HTTP/2 APN에 알림을 보냅니다.

이 커넥터를 구성하려면 다음 단계를 따르십시오.

1. 로 **[!UICONTROL Administration > Platform > External accounts]**&#x200B;이동합니다.
1. Select the **[!UICONTROL iOS routing]** external account.
1. 탭에서 **[!UICONTROL Connector]** 다음 URL로 **[!UICONTROL Access URL of the connector]** 필드를 채웁니다. ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   >[!NOTE]
   >
   > Campaign 20.3 릴리스부터 iOS 레거시 바이너리 커넥터는 사용되지 않습니다. 이 커넥터를 사용하는 경우 그에 따라 구현을 조정해야 합니다. [자세히 알아보기](https://helpx.adobe.com/kr/campaign/kb/migrate-to-apns-http2.html)

   ![](assets/nmac_connectors.png)

1. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

이제 iOS 커넥터가 구성되었습니다. 서비스 만들기를 시작할 수 있습니다.

## iOS 서비스 구성 {#configuring-ios-service}

>[!CAUTION]
>
>Adobe SDK와 통합하기 전에 푸시 작업에 대해 응용 프로그램이 구성되어야 합니다.
>
>그렇지 않은 경우 [이 페이지를 참조하십시오](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/).

1. 노드로 **[!UICONTROL Profiles and Targets > Services and subscriptions]** 이동하고 을 클릭합니다 **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Define a **[!UICONTROL Label]** and an **[!UICONTROL Internal name]**.
1. 필드로 이동하여 **[!UICONTROL Type]** 선택합니다 **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >기본 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 대상 매핑이 수신자 테이블에 연결됩니다. 다른 대상 매핑을 사용하려면 새 대상 매핑을 만들고 서비스 **[!UICONTROL Target mapping]** 필드에 입력해야 합니다. 대상 매핑 만들기에 대한 자세한 내용은 구성 [안내서를 참조하십시오](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. 그런 다음 **[!UICONTROL Add]** 단추를 클릭하여 응용 프로그램 유형을 선택합니다.

   ![](assets/nmac_service_2.png)

1. iOS 개발 및 프로덕션 애플리케이션을 제작할 수 있습니다. 자세한 정보는 이 [섹션](../../delivery/using/configuring-the-mobile-application.md#creating-ios-app)을 참조하십시오.

## iOS 모바일 애플리케이션 제작 {#creating-ios-app}

이제 서비스를 만든 후 iOS 응용 프로그램을 만들어야 합니다.

1. 새로 만든 서비스에서 **[!UICONTROL Add]** 단추를 클릭하여 응용 프로그램 유형을 선택합니다.

   ![](assets/nmac_service_2.png)

1. 다음 창이 나타납니다. 를 **[!UICONTROL Create an iOS application]** 입력하여 시작합니다 **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. 필요에 따라 푸시 메시지 컨텐츠와 필요한 내용을 추가할 수 **[!UICONTROL Application variables]** 있습니다. 이러한 구성 요소는 사용자 지정이 가능하고 모바일 장치로 전송된 메시지 페이로드의 일부입니다.
다음 예제에서는 **mediaURLl** 및 **mediaExt를** 추가하여 리치 푸시 알림을 만든 다음 응용 프로그램에 알림 내에 표시할 이미지를 제공합니다.

   ![](assets/nmac_ios_3.png)

1. 이 **[!UICONTROL Subscription parameters]** 탭에서는 스키마 확장으로 매핑을 정의할 수 **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** 있습니다.

   >[!NOTE]
   >
   >응용 프로그램의 개발 버전(샌드박스)과 프로덕션 버전에 동일한 인증서를 사용하지 않도록 하십시오.

1. 이 **[!UICONTROL Sounds]** 탭에서는 재생할 사운드를 지정할 수 있습니다. 응용 프로그램에 포함된 파일 이름 또는 시스템 사운드 이름을 포함해야 하는 필드 **[!UICONTROL Add]** 를 클릭하고 채우기 **[!UICONTROL Internal name]** 필드를 클릭합니다.

1. 을 **[!UICONTROL Next]** 클릭하여 개발 응용 프로그램 구성을 시작합니다.

1. SDK를 통해 Adobe Campaign **[!UICONTROL Integration key]** 와 애플리케이션 코드에서 동일한지 확인합니다. 자세한 내용은 다음을 참조하십시오. [Campaign SDK를 모바일 애플리케이션에 통합합니다](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md). 각 응용 프로그램에만 해당하는 이 통합 키를 사용하면 모바일 응용 프로그램을 Adobe Campaign 플랫폼에 연결할 수 있습니다.

   >[!NOTE]
   >
   > 문자열 값 **[!UICONTROL Integration key]** 으로 사용자 지정이 가능하지만 SDK에 지정된 값과 동일해야 합니다.

1. 필드에서 바로 사용 가능한 아이콘 중 하나를 선택하여 **[!UICONTROL Application icon]** 서비스에서 모바일 애플리케이션을 개인화합니다.

1. **[!UICONTROL Authentication mode]**&#x200B;을(를) 선택합니다. 나중에 모바일 애플리케이션의 **[!UICONTROL Certificate]** 탭에서 인증 모드를 변경할 수 있습니다.
   * **[!UICONTROL Certificate-based authentication]**:그런 다음 p12 키를 선택하고 모바일 애플리케이션 개발자가 제공한 암호를 입력합니다 **[!UICONTROL Enter the certificate...]** .
   * **[!UICONTROL Token-based authentication]**:연결 설정을 채운 **[!UICONTROL Key ID]****[!UICONTROL Team ID]** 다음 을 클릭하여 p8 인증서를 선택합니다 **[!UICONTROL Bundle ID]** **[!UICONTROL Enter the private key]**. For more on **[!UICONTROL Token-based authentication]**, refer to [Apple documentation](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns).

   >[!NOTE]
   >
   > 이 인증 모드는 보안이 강화되어 인증서 만료 **[!UICONTROL Token-based authentication]** 에 바인딩되지 않으므로 iOS 구성에 사용하는 것이 좋습니다.

   ![](assets/nmac_ios_4.png)

1. 클릭해서 성공 여부를 확인할 수 **[!UICONTROL Test the connection]** 있습니다.

1. 프로덕션 애플리케이션 구성 **[!UICONTROL Next]** 을 시작하려면 을 클릭하고 위에 설명된 것과 동일한 단계를 수행합니다.

   ![](assets/nmac_ios_5.png)

1. **[!UICONTROL Finish]**&#x200B;을(를) 클릭합니다.

이제 Campaign Classic에서 iOS 응용 프로그램을 사용할 준비가 되었습니다.

## iOS 리치 알림 만들기 {#creating-ios-delivery}

iOS 10 이상에서는 풍부한 알림을 생성할 수 있습니다. Adobe Campaign은 장치가 리치 알림을 표시할 수 있도록 해주는 변수를 사용하여 알림을 보낼 수 있습니다.

이제 새 배달을 만들고 만든 모바일 애플리케이션에 연결해야 합니다.

1. > **[!UICONTROL Campaign management]** 로 **[!UICONTROL Deliveries]**&#x200B;이동합니다.

1. **[!UICONTROL New]**&#x200B;을(를) 클릭합니다.

   ![](assets/nmac_android_3.png)

1. 드롭다운 **[!UICONTROL Deliver on iOS (ios)]** 에서 **[!UICONTROL Delivery template]** 선택합니다. 전달 **[!UICONTROL Label]** 에 추가

1. 타깃팅할 모집단 **[!UICONTROL To]** 을 정의하려면 클릭합니다. 기본적으로 **[!UICONTROL Subscriber application]** 대상 매핑이 적용됩니다. 이전에 만든 서비스 **[!UICONTROL Add]** 를 클릭하여 선택합니다.

   ![](assets/nmac_ios_9.png)

1. 창에서 **[!UICONTROL Target type]** 을 선택하고 **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** 클릭합니다 **[!UICONTROL Next]**.

1. 드롭다운에서 이전에 만든 서비스를 선택한 다음 타깃팅할 애플리케이션을 선택하고 을 클릭합니다 **[!UICONTROL Service]** **[!UICONTROL Finish]**.
구성 단계 **[!UICONTROL Application variables]** 에서 추가된 내용에 따라 자동으로 추가됩니다.

   ![](assets/nmac_ios_6.png)

1. 리치 알림 편집

   ![](assets/nmac_ios_7.png)

1. 모바일 애플리케이션에서 미디어 컨텐츠를 다운로드할 수 있도록 하려면 알림 편집 **[!UICONTROL Mutable content]** 창의 상자를 선택합니다.

1. 배달 **[!UICONTROL Save]** 을 클릭하고 보냅니다.

구독자의 모바일 iOS 장치에서 수신할 때 푸시 알림에 이미지 및 웹 페이지가 표시되어야 합니다.

![](assets/nmac_ios_8.png)
