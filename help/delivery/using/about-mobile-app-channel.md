---
product: campaign
title: 모바일 앱 채널 시작
description: Adobe Campaign에서 모바일 앱 채널 시작
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
TQID: 'https://experienceleague.adobe.com/hNwtWC-TnFXsSv7CqqzKqr29sk67h2rwMBOTcBTToDs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: a4657621-810c-498b-8a27-7ced9c176dda
    internal-label: Push notifications
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: cce1f22c34cbd13d063850a7ca636a3b0dfc62f6
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 6%
---
# 모바일 앱 채널 시작{#about-mobile-app-channel}

Adobe Campaign을 사용하여 푸시 알림 게재를 만들어 개인화된 메시지를 모바일 앱 사용자에게 보냅니다.

Campaign v7에서 v8로 전환하는 과정의 일부로 Campaign Classic 설명서 세트가 간소화 및 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다. 푸시 알림 채널에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/push/push){target=_blank}를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/push/push){target=_blank}

다음 정보는 Campaign Classic에만 해당됩니다.

+++ **패키지 설치**

![](assets/do-not-localize/how-to-video.png) [비디오에서 모바일 앱 패키지를 설치하는 방법을 알아봅니다](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html#sending-messages)

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

이 단계를 완료하면 Android 및 iOS 앱을 구성할 수 있습니다. Campaign v8 [설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target="_blank"}를 참조하세요.

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
>두 커넥터에 대한 자세한 내용은 Campaign v8 [설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html){target="_blank"}를 참조하세요.

+++
