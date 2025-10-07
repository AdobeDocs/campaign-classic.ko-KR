---
product: campaign
title: Adobe Campaign에서 iOS 모바일 애플리케이션 구성
description: iOS용 모바일 애플리케이션을 설정하는 방법 알아보기
feature: Push
role: User, Developer
level: Intermediate, Experienced
hide: true
hidefromtoc: true
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: 89e350c727fb9379d28916f79d9749f22fd4974f
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 3%

---

# iOS용 구성 단계 {#configuring-the-mobile-application-in-adobe-campaign-ios}

패키지가 설치되면 Adobe Campaign Classic에서 iOS 앱 설정을 정의할 수 있습니다.

주요 단계:

1. [iOS 외부 계정 구성](#configuring-external-account-ios)
1. [iOS 서비스 구성](#configuring-ios-service)
1. [Campaign에서 iOS 모바일 앱 통합](#creating-ios-app)

그러면 [iOS 장치에 대한 푸시 알림을 만들 수 있습니다](create-notifications-ios.md).

## iOS 외부 계정 구성 {#configuring-external-account-ios}

iOS의 경우 iOS HTTP/2 커넥터가 HTTP/2 APNs에 알림을 보냅니다.

이 커넥터를 구성하려면 다음 단계를 수행하십시오.

1. **[!UICONTROL Administration > Platform > External accounts]**(으)로 이동합니다.
1. **[!UICONTROL iOS routing]** 외부 계정을 선택하십시오.
1. **[!UICONTROL Connector]** 탭에서 **[!UICONTROL Access URL of the connector]** 필드를 다음 URL로 채웁니다. ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

이제 iOS 커넥터가 구성되었습니다. 서비스 만들기를 시작할 수 있습니다.

## iOS 서비스 구성 {#configuring-ios-service}

>[!CAUTION]
>
>Adobe SDK에 통합하기 전에 푸시 작업에 대해 애플리케이션을 구성해야 합니다.
>
>그렇지 않은 경우 [이 페이지](https://developer.apple.com/documentation/usernotifications)를 참조하세요.

1. **[!UICONTROL Profiles and Targets > Services and subscriptions]** 노드로 이동하여 **[!UICONTROL New]**&#x200B;을(를) 클릭합니다.

   ![](assets/nmac_service_1.png)

1. **[!UICONTROL Label]** 및 **[!UICONTROL Internal name]**&#x200B;을(를) 정의합니다.
1. **[!UICONTROL Type]** 필드로 이동하여 **[!UICONTROL Mobile application]**&#x200B;을(를) 선택합니다.

   >[!NOTE]
   >
   >기본 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 대상 매핑이 받는 사람 테이블에 연결되어 있습니다. 다른 대상 매핑을 사용하려면 새 대상 매핑을 만들고 서비스의 **[!UICONTROL Target mapping]** 필드에 입력해야 합니다. 대상 매핑 만들기에 대한 자세한 내용은 [구성 안내서](../../configuration/using/about-custom-recipient-table.md)를 참조하세요.

   ![](assets/nmac_ios.png)

1. 그런 다음 **[!UICONTROL Add]** 단추를 클릭하여 응용 프로그램 유형을 선택합니다.

   ![](assets/nmac_service_2.png)

1. iOS 개발 및 프로덕션 애플리케이션을 만듭니다. 자세한 정보는 이 [섹션](configuring-the-mobile-application.md#creating-ios-app)을 참조하십시오.

## iOS 모바일 앱 만들기 {#creating-ios-app}

서비스를 만든 후 Campaign에서 iOS 애플리케이션을 만듭니다. 아래의 단계를 수행하십시오.

1. 새로 만든 서비스에서 **[!UICONTROL Add]** 단추를 클릭하여 응용 프로그램 유형을 선택합니다.

   ![](assets/nmac_service_2.png)

1. 다음 창이 나타납니다. **[!UICONTROL Create an iOS application]**&#x200B;을(를) 선택하고 **[!UICONTROL Label]**&#x200B;을(를) 입력하여 시작하십시오.

   ![](assets/nmac_ios_2.png)

1. 필요한 경우 **[!UICONTROL Application variables]**을(를) 사용하여 푸시 메시지 콘텐츠를 보강할 수 있습니다. 이는 완전히 맞춤화가 가능하며 모바일 디바이스로 전송되는 메시지 페이로드의 일부입니다.
다음 예제에서는 **mediaURl** 및 **mediaExt**&#x200B;을 추가하여 리치 푸시 알림을 만든 다음 응용 프로그램에 알림 내에 표시할 이미지를 제공합니다.

   ![](assets/nmac_ios_3.png)

1. **[!UICONTROL Subscription parameters]** 탭에서 **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** 스키마의 확장으로 매핑을 정의할 수 있습니다.

   >[!NOTE]
   >
   >애플리케이션의 개발 버전(샌드박스)과 프로덕션 버전에 동일한 인증서를 사용하지 않도록 하십시오.

1. **[!UICONTROL Sounds]** 탭에서 재생할 소리를 지정할 수 있습니다. **[!UICONTROL Add]**&#x200B;을(를) 클릭하고 응용 프로그램에 포함된 파일 이름 또는 시스템 사운드 이름을 포함해야 하는 **[!UICONTROL Internal name]** 필드를 채웁니다.

1. 개발 응용 프로그램 구성을 시작하려면 **[!UICONTROL Next]**&#x200B;을(를) 클릭하십시오.

1. Adobe Campaign 및 SDK을 통해 응용 프로그램 코드에 동일한 **[!UICONTROL Integration key]**&#x200B;이(가) 정의되어 있는지 확인하십시오. <!--For more on this, refer to [this page](integrating-campaign-sdk-into-the-mobile-application.md).--> 각 애플리케이션에 해당하는 이 통합 키를 사용하면 모바일 애플리케이션을 Adobe Campaign 플랫폼에 연결할 수 있습니다.

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]**&#x200B;은(는) 문자열 값으로 완전히 사용자 지정할 수 있지만 SDK에 지정된 값과 정확히 동일해야 합니다.

1. **[!UICONTROL Application icon]** 필드에서 기본 제공 아이콘 중 하나를 선택하여 서비스의 모바일 애플리케이션을 개인화합니다.

1. **[!UICONTROL Authentication mode]**&#x200B;을(를) 선택합니다.

   ![](assets/nmac_ios_5.png)

   두 가지 모드를 사용할 수 있습니다.

   * (권장) **[!UICONTROL Token-based authentication]**: APNs 연결 설정 **[!UICONTROL Key Id]**, **[!UICONTROL Team Id]** 및 **[!UICONTROL Bundle Id]**&#x200B;을(를) 입력한 다음 **[!UICONTROL Enter the private key...]**&#x200B;을(를) 클릭하여 p8 인증서를 선택합니다. **[!UICONTROL Token-based authentication]**&#x200B;에 대한 자세한 내용은 [Apple 설명서](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns){target="_blank"}를 참조하세요.

   * **[!UICONTROL Certificate-based authentication]**: **[!UICONTROL Enter the certificate...]**&#x200B;을(를) 클릭한 다음 p12 키를 선택하고 모바일 애플리케이션 개발자가 제공한 암호를 입력하십시오.

   >[!NOTE]
   >
   > P8 인증 키가 보다 새롭고 안전하므로 Adobe에서는 iOS 구성에 **[!UICONTROL Token-based authentication]**&#x200B;을(를) 사용하는 것이 좋습니다.

1. **[!UICONTROL Test the connection]** 단추를 사용하여 구성의 유효성을 검사하십시오.

1. **[!UICONTROL Next]**&#x200B;을(를) 클릭하여 프로덕션 응용 프로그램 구성을 시작하고 위에 설명된 것과 동일한 단계를 수행합니다.


1. **[!UICONTROL Finish]**&#x200B;을(를) 클릭합니다.

이제 iOS 애플리케이션을 Campaign Classic에서 사용할 준비가 되었습니다.
