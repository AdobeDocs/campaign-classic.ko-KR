---
product: campaign
title: Adobe Campaign 에서 모바일 애플리케이션 구성
description: 모바일 애플리케이션 구성을 시작하는 방법을 알아봅니다
feature: Push
role: User, Developer
level: Intermediate, Experienced
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 5%

---

# 앱 구성 시작



이 섹션에서는 온라인 휴가 패키지를 판매하는 회사를 기반으로 하는 구성 샘플을 찾을 수 있습니다. 모바일 애플리케이션(Neotrips)은 Android 용 Neotrips와 iOS 용 Neotrips의 두 가지 버전으로 고객에게 제공됩니다.

Adobe Campaign에서 푸시 알림을 보내려면 다음을 수행해야 합니다.

* **[!UICONTROL Mobile application]** Neotrips 모바일 애플리케이션 용 유형 정보 서비스를 만들기. iOS](configuring-the-mobile-application.md#configuring-ios-service)의 경우 이 섹션을 참조하십시오[. 및 [이 섹션은 Android](configuring-the-mobile-application-android.md#configuring-android-service) 용입니다.
* 이 서비스에 iOS 및 Android 버전의 애플리케이션을 추가합니다.
* iOS](create-notifications-ios.md) 및 [Android](create-notifications-android.md) 용 [게재를 만들기.

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>**[!UICONTROL Subscriptions]** 서비스 탭로 이동하여 서비스 가입자 목록, 즉 모바일에 애플리케이션 설치하고 알림 수신에 동의한 모든 사람을 봅니다.

## 패키지 설치 {#installing-package-ios}

[!BADGE 온프레미스 및 하이브리드]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용됩니다"}

![](assets/do-not-localize/how-to-video.png)[비디오로 모바일 앱 패키지를 설치하는 방법 알아보기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html#sending-messages)

하이브리드/호스팅 고객의 경우 Campaign 푸시 알림 채널에 액세스하려면 Adobe Systems 고객 지원](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 팀 팀에 문의하십시오[.

온-프레미스 고객은 기본 제공 패키지를 설치해야 합니다.

>[!CAUTION]
>
>이 페이지](../../installation/using/installing-campaign-standard-packages.md)에서 Campaign 내장 패키지, 모범 사례 및 권장 사항에 [대해 자세히 알아보십시오.

설치 단계는 다음과 같습니다.

1. Adobe Campaign 클라이언트 콘솔에서 **[!UICONTROL Tools > Advanced > Import package]** 패키지 가져오기 도우미에 액세스합니다.

   ![](assets/package_ios.png)

1. **[!UICONTROL Install a standard package]**&#x200B;을(를) 선택합니다.

1. 목록이 나타나면 을 선택합니다 **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. 을 클릭한 **[!UICONTROL Next]**&#x200B;다음 **[!UICONTROL Start]** , 패키지 설치를 시작합니다.

   패키지가 설치되면 진행률 표시줄에 **100%**&#x200B;이(가) 표시되며, 설치 로그에 **[!UICONTROL Installation of packages successful]** 메시지가 표시됩니다.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** 설치 창.

이 단계가 완료되면 Android 및 iOS 앱을 구성할 수 있습니다.
다음 섹션을 참조하십시오.

* [iOS용 구성 단계](configuring-the-mobile-application.md)

* [Android용 구성 단계](configuring-the-mobile-application-android.md)
