---
product: campaign
title: 문제 해결
description: 문제 해결
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 4%

---

# 문제 해결{#troubleshooting}

모바일 장치가 Wi-Fi에 연결되어 있고 알림을 받지 않는 경우 FCM/APNs 포트가 방화벽에 의해 차단되지 않았는지 확인합니다.

**Android**:모바일 장치는 포트 5228에서 5230으로 FCM 서버에 연결합니다. 따라서 FCM과의 연결을 허용하도록 방화벽을 구성해야 합니다. 열 포트는 다음과 같습니다.5228(가장 자주 사용), 5229 및 5230.

**iOS**:

HTTP/2 커넥터:다음 서버와의 통신을 허용해야 합니다.

* api.push.apple.com:포트 443
* api.development.push.apple.com:포트 443

>[!NOTE]
>
>두 커넥터에 대한 자세한 내용은 [Adobe Campaign](configuring-the-mobile-application.md)에서 모바일 애플리케이션 구성 을 참조하십시오.
