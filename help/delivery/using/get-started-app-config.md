---
solution: Campaign Classic
product: campaign
title: 'Adobe Campaign에서 모바일 애플리케이션 구성 '
description: 모바일 애플리케이션 구성으로 시작하는 방법 살펴보기
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 1d7d48f52f69e4902eafa6806c2cd9170c21fe5a
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 9%

---


# 앱 구성 시작

이 섹션에서는 온라인 휴일 패키지를 판매하는 회사를 기반으로 한 구성 샘플을 확인할 수 있습니다. 이 모바일 애플리케이션(네오트피)은 두 가지 버전으로 고객에게 제공됩니다.Android 및 iOS용 네오트립

Adobe Campaign에서 푸시 알림을 전송하려면 다음을 수행해야 합니다.

* Neotrips 모바일 응용 프로그램에 대한 **[!UICONTROL Mobile application]** 유형 정보 서비스를 만듭니다. iOS에 대한 [이 섹션을 참조하십시오](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service). Android용 [이 섹션](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service).
* 이 서비스에 애플리케이션의 iOS 및 Android 버전을 추가합니다.
* iOS 및 Android 모두에 대한 배달을 만듭니다. [이 페이지](../../delivery/using/creating-notifications.md)를 참조하십시오.

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>서비스의 **[!UICONTROL Subscriptions]** 탭으로 이동하여 해당 서비스의 가입자 목록을 봅니다. 즉, 해당 애플리케이션을 모바일에 설치했고 알림을 수신하기로 동의한 모든 사람이 해당됩니다.

## 패키지 설치 {#installing-package-ios}

![](assets/do-not-localize/how-to-video.png) [비디오에 모바일 앱 패키지 설치 방법 살펴보기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=en#sending-messages)

하이브리드/호스팅 고객인 경우 Adobe 고객 지원 센터에 연락하여 Campaign의 푸시 알림 채널에 액세스합니다.

온-프레미스 고객은 다음 설치 단계를 수행해야 합니다.

1. Adobe Campaign 클라이언트 콘솔에서 패키지 가져오기 마법사 **[!UICONTROL Tools > Advanced > Package import...]** 에 액세스합니다.

   ![](assets/package_ios.png)

1. **[!UICONTROL Install a standard package]**&#x200B;을(를) 선택합니다.

1. 목록이 표시되면 선택합니다 **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. 을 **[!UICONTROL Next]**&#x200B;클릭한 다음 패키지 설치를 **[!UICONTROL Start]** 시작합니다.

   패키지가 설치되면 진행률 표시줄이 **100%** 표시되고 설치 로그에 다음 메시지가 표시됩니다. **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** 설치 창

이 단계가 완료되면 Android 및 iOS 앱을 구성할 수 있습니다.
다음 섹션을 참조하십시오.

* [iOS용 구성 단계](../../delivery/using/configuring-the-mobile-application.md)

* [Android용 구성 단계](../../delivery/using/configuring-the-mobile-application-android.md)
