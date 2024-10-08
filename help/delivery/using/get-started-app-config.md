---
product: campaign
title: Adobe Campaign에서 모바일 애플리케이션 구성
description: 모바일 애플리케이션 구성으로 시작하는 방법 알아보기
feature: Push
role: User, Developer
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 5%

---

# 앱 구성 시작



이 섹션에서는 온라인 휴일 패키지를 판매하는 회사를 기반으로 하는 구성 샘플을 찾을 수 있습니다. 모바일 애플리케이션(Neotrips)은 Android의 Neotrips 및 iOS의 Neotrips의 두 가지 버전으로 고객이 사용할 수 있습니다.

Adobe Campaign에서 푸시 알림을 전송하려면 다음을 수행해야 합니다.

* Neotrips 모바일 응용 프로그램에 대한 **[!UICONTROL Mobile application]** 형식 정보 서비스를 만듭니다. [iOS에 대한 이 섹션](configuring-the-mobile-application.md#configuring-ios-service)을 참조하세요. 및 [Android에 대한 이 섹션](configuring-the-mobile-application-android.md#configuring-android-service)입니다.
* 애플리케이션의 iOS 및 Android 버전을 이 서비스에 추가합니다.
* [iOS](create-notifications-ios.md) 및 [Android](create-notifications-android.md)에 대한 게재를 만듭니다.

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>서비스의 **[!UICONTROL Subscriptions]** 탭으로 이동하여 서비스 구독자(예: 모바일에 애플리케이션을 설치하고 알림을 받는 데 동의한 모든 사람)의 목록을 봅니다.

## 패키지 설치 {#installing-package-ios}

[!BADGE 온-프레미스 및 하이브리드]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"}

![](assets/do-not-localize/how-to-video.png) [비디오에서 모바일 앱 패키지를 설치하는 방법을 알아봅니다](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html#sending-messages)

하이브리드/호스팅 고객은 [고객 지원 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 팀에 문의하여 Campaign의 푸시 알림 채널에 액세스하십시오.

온-프레미스 고객은 기본 제공 패키지를 설치해야 합니다.

>[!CAUTION]
>
>[이 페이지](../../installation/using/installing-campaign-standard-packages.md)에서 Campaign 기본 제공 패키지, 모범 사례 및 권장 사항에 대해 자세히 알아보세요.

설치 단계는 다음과 같습니다.

1. Adobe Campaign 클라이언트 콘솔의 **[!UICONTROL Tools > Advanced > Import package]**&#x200B;에서 패키지 가져오기 도우미에 액세스합니다.

   ![](assets/package_ios.png)

1. **[!UICONTROL Install a standard package]**&#x200B;을(를) 선택합니다.

1. 표시되는 목록에서 **[!UICONTROL Mobile App Channel]**&#x200B;을(를) 선택합니다.

   ![](assets/package_ios_2.png)

1. 패키지 설치를 시작하려면 **[!UICONTROL Next]**&#x200B;을(를) 클릭한 다음 **[!UICONTROL Start]**&#x200B;을(를) 클릭합니다.

   패키지가 설치되면 진행률 표시줄에 **100%**&#x200B;이(가) 표시되며, 설치 로그에 **[!UICONTROL Installation of packages successful]** 메시지가 표시됩니다.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** 설치 창을 엽니다.

이 단계를 완료하면 Android 및 iOS 앱을 구성할 수 있습니다.
다음 섹션을 참조하십시오.

* [iOS용 구성 단계](configuring-the-mobile-application.md)

* [Android용 구성 단계](configuring-the-mobile-application-android.md)
