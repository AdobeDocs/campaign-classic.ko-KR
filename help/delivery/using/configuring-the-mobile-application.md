---
product: campaign
title: Adobe Campaign에서 iOS 모바일 애플리케이션 구성
description: iOS용 모바일 애플리케이션을 설정하는 방법을 알아봅니다
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: 3b8d685642fc74d918a0e312c66d5e4f7b424192
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 6%

---

# iOS용 구성 단계 {#configuring-the-mobile-application-in-adobe-campaign-ios}

![](../../assets/common.svg)

패키지가 설치되면 Adobe Campaign Classic에서 iOS 앱 설정을 정의할 수 있습니다.

>[!NOTE]
>
>Android용 앱을 구성하는 방법 및 Android용 게재를 만드는 방법에 대해 알아보려면 다음 문서를 참조하십시오 [섹션](configuring-the-mobile-application-android.md).

주요 단계는 다음과 같습니다.

1. [iOS 외부 계정 구성](#configuring-external-account-ios)
1. [iOS 서비스 구성](#configuring-ios-service)
1. [Campaign에서 iOS 모바일 앱 통합](#creating-ios-app)

그러면 다음을 수행할 수 있습니다 [iOS 장치에 대한 푸시 알림 만들기](create-notifications-ios.md).


## iOS 외부 계정 구성 {#configuring-external-account-ios}

iOS의 경우 iOS HTTP/2 커넥터는 HTTP/2 APNs에 알림을 보냅니다.

이 커넥터를 구성하려면 다음 단계를 수행하십시오.

1. 이동 **[!UICONTROL Administration > Platform > External accounts]**.
1. 을(를) 선택합니다 **[!UICONTROL iOS routing]** 외부 계정.
1. 에서 **[!UICONTROL Connector]** 탭에서 을 입력합니다 **[!UICONTROL Access URL of the connector]** 다음 URL이 있는 필드: ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. **[!UICONTROL Save]**&#x200B;를 클릭합니다.

이제 iOS 커넥터가 구성되었습니다. 서비스 만들기를 시작할 수 있습니다.

## iOS 서비스 구성 {#configuring-ios-service}

>[!CAUTION]
>
>Adobe Campaign SDK에 통합하기 전에 푸시 작업 ID에 대해 애플리케이션이 구성되었어야 합니다.
>
>이 경우가 아니면 다음을 참조하십시오. [이 페이지](https://developer.apple.com/documentation/usernotifications).

1. 로 이동합니다. **[!UICONTROL Profiles and Targets > Services and subscriptions]** 노드 및 **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. 정의 **[!UICONTROL Label]** 그리고 **[!UICONTROL Internal name]**.
1. 로 이동합니다. **[!UICONTROL Type]** 필드 및 선택 **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >기본값 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 대상 매핑은 수신자 테이블에 연결됩니다. 다른 대상 매핑을 사용하려면 새 대상 매핑을 생성하고 여기에 입력해야 합니다 **[!UICONTROL Target mapping]** 서비스의 필드입니다. 대상 매핑 만들기에 대한 자세한 내용은 [구성 안내서](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. 그런 다음 **[!UICONTROL Add]** 단추를 클릭하여 애플리케이션 유형을 선택합니다.

   ![](assets/nmac_service_2.png)

1. iOS 개발 및 프로덕션 애플리케이션을 만듭니다. 자세한 정보는 이 [섹션](configuring-the-mobile-application.md#creating-ios-app)을 참조하십시오.

## iOS 모바일 앱 만들기 {#creating-ios-app}

서비스를 만든 후 Campaign에서 iOS 애플리케이션을 만듭니다. 아래의 단계를 수행하십시오.

1. 새로 만든 서비스에서 **[!UICONTROL Add]** 단추를 클릭하여 애플리케이션 유형을 선택합니다.

   ![](assets/nmac_service_2.png)

1. 다음 창이 나타납니다. 선택 **[!UICONTROL Create an iOS application]** 다음을 입력하여 시작합니다. **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. 옵션은 일부 항목을 사용하여 푸시 메시지 콘텐츠를 보강할 수 있습니다 **[!UICONTROL Application variables]** 필요한 경우 사용자 지정할 수 있으며 모바일 장치로 전송되는 메시지 페이로드의 일부입니다.
다음 예에서는 **mediaURL** 및 **mediaExt** 리치 푸시 알림을 만든 다음, 알림 내에 표시할 이미지를 애플리케이션에 제공합니다.

   ![](assets/nmac_ios_3.png)

1. 다음 **[!UICONTROL Subscription parameters]** 탭에서는 확장 기능을 사용하여 매핑을 정의할 수 있습니다 **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** 스키마.

   >[!NOTE]
   >
   >개발 버전(샌드박스) 및 응용 프로그램의 프로덕션 버전에 대해 동일한 인증서를 사용하지 않도록 하십시오.

1. 다음 **[!UICONTROL Sounds]** 탭에서는 재생할 사운드를 지정할 수 있습니다. 클릭 **[!UICONTROL Add]** 및 채우기 **[!UICONTROL Internal name]** 응용 프로그램에 포함된 파일의 이름 또는 시스템 사운드의 이름을 포함해야 하는 필드입니다.

1. 클릭 **[!UICONTROL Next]** 개발 애플리케이션 구성을 시작하려면 다음을 수행하십시오.

1. 똑같이 **[!UICONTROL Integration key]** 는 Adobe Campaign에 정의되며, SDK를 통해 애플리케이션 코드에 정의됩니다. 자세한 정보는 이 [페이지](integrating-campaign-sdk-into-the-mobile-application.md)를 참조하십시오. 각 애플리케이션에만 해당하는 이 통합 키를 사용하면 모바일 애플리케이션을 Adobe Campaign 플랫폼에 연결할 수 있습니다.

   >[!NOTE]
   >
   > 다음 **[!UICONTROL Integration key]** 는 문자열 값으로 완전히 사용자 지정할 수 있지만 SDK에 지정된 값과 동일해야 합니다.

1. 에서 기본 아이콘 중 하나를 선택합니다 **[!UICONTROL Application icon]** 필드에서 모바일 애플리케이션을 개인화할 수 있습니다.

1. **[!UICONTROL Authentication mode]**&#x200B;을(를) 선택합니다. 에서는 항상 나중에 인증 모드를 변경할 수 있습니다 **[!UICONTROL Certificate]** 모바일 애플리케이션의 탭입니다.
   * **[!UICONTROL Certificate-based authentication]**: 클릭 **[!UICONTROL Enter the certificate...]**  그런 다음 p12 키를 선택하고 모바일 애플리케이션 개발자가 제공한 암호를 입력합니다.
   * **[!UICONTROL Token-based authentication]**: 연결 설정을 입력합니다 **[!UICONTROL Key ID]**, **[!UICONTROL Team ID]** 및 **[!UICONTROL Bundle ID]** 그런 다음 를 클릭하여 p8 인증서를 선택합니다. **[!UICONTROL Enter the private key]**. 자세한 내용 **[!UICONTROL Token-based authentication]**&#x200B;를 참조하려면 [Apple 설명서](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns).

   >[!NOTE]
   >
   > Adobe은 **[!UICONTROL Token-based authentication]** 이 인증 모드가 더 안전하며 인증서 만료에 바인딩되지 않으므로 iOS 구성에 사용됩니다.

   ![](assets/nmac_ios_4.png)

1. 을(를) 클릭합니다 **[!UICONTROL Test the connection]** 성공했는지 확인

1. 클릭 **[!UICONTROL Next]** 프로덕션 애플리케이션 구성을 시작하고 위의 설명과 동일한 단계를 수행하십시오.

   ![](assets/nmac_ios_5.png)

1. **[!UICONTROL Finish]**&#x200B;를 클릭합니다.

이제 iOS 애플리케이션을 Campaign Classic에서 사용할 준비가 되었습니다.
