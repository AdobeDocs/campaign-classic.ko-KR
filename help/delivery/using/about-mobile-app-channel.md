---
product: campaign
title: 모바일 앱 채널 시작
description: Adobe Campaign에서 모바일 앱 채널 시작
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 2%

---

# 모바일 앱 채널 시작{#about-mobile-app-channel}

Adobe Campaign을 사용하여 푸시 알림 게재를 만들어 개인화된 메시지를 모바일 앱 사용자에게 보냅니다.

푸시 알림을 사용하면 iOS 및 Android에서 사용자를 실시간으로 참여시킬 수 있습니다. 업데이트, 공지 또는 프로모션 등을 전송할 때 콘텐츠, 시간 및 타겟팅을 제어할 수 있습니다. [Adobe Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/emails/email){target=_blank}에서 푸시 채널 설정 및 사용, 구독 관리, APNs 및 FCM과의 통합, 메시지 개인화 방법을 알아봅니다.

Campaign v8 프로모션 이니셔티브의 일부로 Campaign Classic 설명서가 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다.

>[!BEGINTABS]

>[!TAB 푸시 채널 설명서]

푸시 알림 채널에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=ko){target=_blank}를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=ko){target=_blank}


>[!TAB 푸시 게재 만들기]

Campaign v8 설명서에서 푸시 게재 만들기와 관련된 주요 단계를 알아봅니다.

* [푸시 알림 만들기](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=ko#push-create){target="_blank"}: 푸시 게재를 만드는 데 필요한 여러 단계에 대해 알아봅니다.
* [푸시 알림 전송 및 모니터링](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=ko#push-test){target="_blank"}: 게재의 유효성 검사, 전송 및 추적 방법을 알아봅니다.
* [Android 리치 푸시 게재 디자인](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-android.html?lang=ko){target="_blank"}: Android 장치에 대한 리치 푸시 알림을 만들고 구성하는 방법에 대해 알아봅니다.
* [iOS 리치 푸시 알림 디자인](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-ios.html?lang=ko){target="_blank"}: Adobe Campaign v8에서 iOS 장치에 대한 리치 푸시 알림을 디자인하고 구성하는 방법에 대해 알아봅니다.


>[!TAB 푸시 매개 변수]

푸시 매개 변수에 대한 자세한 내용은 Campaign v8 설명서를 다음 페이지를 참조하십시오.

* [구성 필수 구성 요소](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=ko#before-starting){target="_blank"}: 권한을 설정하고 앱을 구성하는 방법에 대해 알아봅니다.
* [Launch 속성 구성](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=ko#launch-property){target="_blank"}: 푸시 알림을 사용하도록 설정하는 Adobe Experience Platform 데이터 수집에서 모바일 태그 속성을 설정하는 방법에 대해 알아봅니다.
* [푸시 서비스 모바일 서비스 구성](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=ko#push-service){target="_blank"}: 모바일 앱 사용자를 위해 타깃팅된 푸시 알림을 사용하도록 설정하려면 Adobe에서 iOS 및 Android 푸시 서비스를 설정하십시오.
* [모바일 속성에서 확장을 구성](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=ko#configure-extension){target="_blank"}: 푸시 알림을 활성화하고 사용자 상호 작용을 효과적으로 관리하려면 Campaign 확장을 모바일 속성에 통합합니다.

>[!ENDTABS]


다음 정보는 Campaign Classic에만 해당됩니다.

+++ **패키지 설치**

![](assets/do-not-localize/how-to-video.png) [비디오에서 모바일 앱 패키지를 설치하는 방법을 알아봅니다](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=ko#sending-messages)

하이브리드/호스팅 고객은 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 팀에 문의하여 Campaign의 푸시 알림 채널에 액세스하십시오.

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

이 단계를 완료하면 Android 및 iOS 앱을 구성할 수 있습니다. Campaign v8 [설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=ko){target="_blank"}를 참조하세요.

+++

+++ **문제 해결**

모바일 장치가 Wi-Fi에 연결되어 있고 알림을 받지 못하는 경우, FCM/APNs 포트가 방화벽에 의해 차단되고 있지 않은지 확인하십시오.

**Android**: 모바일 장치가 포트 5228에서 5230까지의 FCM 서버에 연결됩니다. 따라서 FCM과의 연결을 승인하도록 방화벽을 구성해야 합니다. 열려는 포트는 5228(가장 자주 사용됨), 5229 및 5230입니다.

**iOS**:

HTTP/2 커넥터: 다음 서버와의 통신을 허용해야 합니다.

* api.push.apple.com: 포트 443
* api.development.push.apple.com: 포트 443

>[!NOTE]
>
>두 커넥터에 대한 자세한 내용은 Campaign v8 [설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=ko){target="_blank"}를 참조하세요.

+++
