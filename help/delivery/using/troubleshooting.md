---
solution: Campaign Classic
product: campaign
title: 문제 해결
description: 문제 해결
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 3%

---


# 문제 해결{#troubleshooting}

모바일 장치가 Wi-Fi에 연결되어 있고 알림을 받지 않는 경우 FCM/APNs 포트가 방화벽으로 차단되지 않는지 확인합니다.

**Android**:모바일 장치는 포트 5228에서 5230 사이의 FCM 서버에 연결합니다. 그러므로 FCM과의 연결을 승인하도록 방화벽을 구성해야 합니다. 열 포트는 다음과 같습니다.5228(가장 자주 사용하는 항목), 5229 및 5230입니다.

**iOS**:

이진 커넥터:알림을 전송하려면 포트 2195에서 인바운드 및 아웃바운드 TCP 트래픽을 인증해야 합니다. 푸시 서비스에 연결된 장치는 포트 5223에서 인바운드 및 아웃바운드 TCP 트래픽을 승인해야 합니다.

HTTP/2 커넥터:다음 서버와의 통신을 허용해야 합니다.

* api.push.apple.com:포트 443
* api.development.push.apple.com:포트 443

>[!NOTE]
>
>두 커넥터에 대한 자세한 내용은 [Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md)에서 모바일 응용 프로그램 구성을 참조하십시오.
