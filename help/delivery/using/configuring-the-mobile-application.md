---
product: campaign
title: Adobe Campaign에서 iOS 모바일 애플리케이션 구성
description: iOS용 모바일 애플리케이션을 설정하는 방법 알아보기
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 4%

---

# iOS용 구성 단계 {#configuring-the-mobile-application-in-adobe-campaign-ios}

패키지가 설치되면 Adobe Campaign Classic에서 iOS 앱 설정을 정의할 수 있습니다.

>[!NOTE]
>
>Android용 앱을 구성하는 방법 및 Android용 게재를 만드는 방법에 대해 알아보려면 이 [섹션](../../delivery/using/configuring-the-mobile-application-android.md)을 참조하십시오.

## iOS 외부 계정 구성 {#configuring-external-account-ios}

iOS의 경우 iOS HTTP/2 커넥터가 HTTP/2 APNs에 알림을 보냅니다.

이 커넥터를 구성하려면 다음 단계를 수행하십시오.

1. **[!UICONTROL Administration > Platform > External accounts]**(으)로 이동합니다.
1. **[!UICONTROL iOS routing]** 외부 계정을 선택합니다.
1. **[!UICONTROL Connector]** 탭에서 **[!UICONTROL Access URL of the connector]** 필드를 다음 URL로 입력합니다.```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

이제 iOS 커넥터가 구성되었습니다. 서비스 만들기를 시작할 수 있습니다.

## iOS 서비스 구성 {#configuring-ios-service}

>[!CAUTION]
>
>Adobe Campaign SDK에 통합하기 전에 푸시 작업 ID에 대해 애플리케이션이 구성되었어야 합니다.
>
>이 경우가 아니면 [이 페이지](https://developer.apple.com/documentation/usernotifications)를 참조하십시오.

1. **[!UICONTROL Profiles and Targets > Services and subscriptions]** 노드로 이동하고 **[!UICONTROL New]** 를 클릭합니다.

   ![](assets/nmac_service_1.png)

1. **[!UICONTROL Label]** 및 **[!UICONTROL Internal name]**&#x200B;을(를) 정의합니다.
1. **[!UICONTROL Type]** 필드로 이동하고 **[!UICONTROL Mobile application]** 을 선택합니다.

   >[!NOTE]
   >
   >기본 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 대상 매핑이 수신자 테이블에 연결되어 있습니다. 다른 대상 매핑을 사용하려면 새 대상 매핑을 만들어 서비스의 **[!UICONTROL Target mapping]** 필드에 입력해야 합니다. 대상 매핑 만들기에 대한 자세한 내용은 [구성 안내서](../../configuration/using/about-custom-recipient-table.md)를 참조하십시오.

   ![](assets/nmac_ios.png)

1. 그런 다음 **[!UICONTROL Add]** 단추를 클릭하여 응용 프로그램 유형을 선택합니다.

   ![](assets/nmac_service_2.png)

1. iOS 개발 및 프로덕션 애플리케이션을 만듭니다. 자세한 정보는 이 [섹션](../../delivery/using/configuring-the-mobile-application.md#creating-ios-app)을 참조하십시오.

## iOS 모바일 애플리케이션 만들기 {#creating-ios-app}

이제 서비스를 만든 후 iOS 애플리케이션을 만들어야 합니다.

1. 새로 만든 서비스에서 **[!UICONTROL Add]** 버튼을 클릭하여 애플리케이션 유형을 선택합니다.

   ![](assets/nmac_service_2.png)

1. 다음 창이 나타납니다. **[!UICONTROL Create an iOS application]** 을 선택하고 **[!UICONTROL Label]** 을 입력하여 시작합니다.

   ![](assets/nmac_ios_2.png)

1. 필요한 경우 일부 **[!UICONTROL Application variables]**으로 푸시 메시지 콘텐츠를 보강할 수 있습니다. 사용자 지정할 수 있으며 모바일 장치로 전송되는 메시지 페이로드의 일부입니다.
다음 예제에서는 **mediaURL** 및 **mediaExt**&#x200B;를 추가하여 리치 푸시 알림을 만든 다음 알림 내에 표시할 이미지를 애플리케이션에 제공합니다.

   ![](assets/nmac_ios_3.png)

1. **[!UICONTROL Subscription parameters]** 탭에서는 **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** 스키마의 확장을 사용하여 매핑을 정의할 수 있습니다.

   >[!NOTE]
   >
   >개발 버전(샌드박스) 및 응용 프로그램의 프로덕션 버전에 대해 동일한 인증서를 사용하지 않도록 하십시오.

1. **[!UICONTROL Sounds]** 탭에서는 재생할 사운드를 지정할 수 있습니다. **[!UICONTROL Add]** 을 클릭하고 응용 프로그램에 포함된 파일의 이름 또는 시스템 사운드의 이름을 포함해야 하는 **[!UICONTROL Internal name]** 필드를 채웁니다.

1. **[!UICONTROL Next]** 을 클릭하여 개발 응용 프로그램 구성을 시작합니다.

1. 동일한 **[!UICONTROL Integration key]**&#x200B;이 Adobe Campaign과 SDK를 통해 애플리케이션 코드에 정의되어 있는지 확인합니다. 자세한 내용은 다음을 참조하십시오.[모바일 애플리케이션에 Campaign SDK 통합](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md). 각 애플리케이션에만 해당하는 이 통합 키를 사용하면 모바일 애플리케이션을 Adobe Campaign 플랫폼에 연결할 수 있습니다.

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]**&#x200B;은 문자열 값으로 완전히 사용자 지정할 수 있지만 SDK에 지정된 값과 동일해야 합니다.

1. **[!UICONTROL Application icon]** 필드에서 기본 아이콘 중 하나를 선택하여 서비스에서 모바일 애플리케이션을 개인화합니다.

1. **[!UICONTROL Authentication mode]**&#x200B;을(를) 선택합니다. 모바일 애플리케이션의 **[!UICONTROL Certificate]** 탭에서 언제든지 인증 모드를 변경할 수 있습니다.
   * **[!UICONTROL Certificate-based authentication]**:을( **[!UICONTROL Enter the certificate...]**  를) 클릭한 다음 p12 키를 선택하고 모바일 애플리케이션 개발자가 제공한 암호를 입력합니다.
   * **[!UICONTROL Token-based authentication]**:연결 설정을  **[!UICONTROL Key ID]**&#x200B;입력한  **[!UICONTROL Team ID]** 다음  **[!UICONTROL Bundle ID]** 을 클릭하여 p8 인증서를 선택합니다  **[!UICONTROL Enter the private key]**. **[!UICONTROL Token-based authentication]**&#x200B;에 대한 자세한 내용은 [Apple 설명서](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns)를 참조하십시오.

   >[!NOTE]
   >
   > 이 인증 모드는 더 안전하며 인증서 만료에 바인딩되지 않으므로 iOS 구성에 **[!UICONTROL Token-based authentication]** 을 사용하는 것이 좋습니다.

   ![](assets/nmac_ios_4.png)

1. **[!UICONTROL Test the connection]** 을 클릭하여 성공했는지 확인할 수 있습니다.

1. **[!UICONTROL Next]** 을 클릭하여 프로덕션 애플리케이션 구성을 시작하고 위에 설명된 것과 동일한 단계를 수행합니다.

   ![](assets/nmac_ios_5.png)

1. **[!UICONTROL Finish]**&#x200B;을(를) 클릭합니다.

이제 iOS 애플리케이션을 Campaign Classic에서 사용할 준비가 되었습니다.

## iOS 리치 알림 만들기 {#creating-ios-delivery}

iOS 10 이상을 사용하면 풍부한 알림을 생성할 수 있습니다. Adobe Campaign은 장치가 리치 알림을 표시할 수 있는 변수를 사용하여 알림을 전송할 수 있습니다.

이제 새 게재를 만들고 만든 모바일 애플리케이션에 연결해야 합니다.

1. **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**(으)로 이동합니다.

1. **[!UICONTROL New]**&#x200B;을(를) 클릭합니다.

   ![](assets/nmac_android_3.png)

1. **[!UICONTROL Delivery template]** 드롭다운에서 **[!UICONTROL Deliver on iOS (ios)]** 을 선택합니다. 게재에 **[!UICONTROL Label]**&#x200B;을(를) 추가합니다.

1. **[!UICONTROL To]** 을 클릭하여 타겟팅할 모집단을 정의합니다. 기본적으로 **[!UICONTROL Subscriber application]** 대상 매핑이 적용됩니다. **[!UICONTROL Add]** 을 클릭하여 이전에 만든 서비스를 선택합니다.

   ![](assets/nmac_ios_9.png)

1. **[!UICONTROL Target type]** 창에서 **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** 을 선택하고 **[!UICONTROL Next]** 를 클릭합니다.

1. **[!UICONTROL Service]** 드롭다운에서 앞에서 만든 서비스를 선택한 다음 타깃팅할 애플리케이션을 선택하고 **[!UICONTROL Finish]** 을 클릭합니다.
**[!UICONTROL Application variables]**&#x200B;은 구성 단계 중에 추가된 내용에 따라 자동으로 추가됩니다.

   ![](assets/nmac_ios_6.png)

1. 리치 알림을 편집합니다.

   ![](assets/nmac_ios_7.png)

1. 모바일 애플리케이션에서 미디어 콘텐츠를 다운로드할 수 있도록 하려면 알림 편집 창에서 **[!UICONTROL Mutable content]** 상자를 선택합니다.

1. **[!UICONTROL Save]** 을 클릭하고 게재를 전송합니다.

구독자의 모바일 iOS 장치에서 수신한 경우 푸시 알림에 이미지 및 웹 페이지가 표시되어야 합니다.

![](assets/nmac_ios_8.png)
