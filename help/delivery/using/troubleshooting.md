---
title: 문제 해결
seo-title: 문제 해결
description: 문제 해결
seo-description: null
page-status-flag: never-activated
uuid: 02bd48cf-3928-4817-97b0-1e64cc8ad8ef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: b64c9729-cfe2-4d02-8c59-9e53efd34a96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 문제 해결{#troubleshooting}

모바일 장치가 Wi-Fi에 연결되어 있고 알림을 받지 않는 경우 FCM/APNS 포트가 방화벽으로 차단되지 않는지 확인하십시오.

**Android**:모바일 장치는 포트 5228에서 5230 사이의 FCM 서버에 연결합니다. 따라서 FCM과의 연결을 승인하도록 방화벽을 구성해야 합니다. 열 포트는 다음과 같습니다.5228(가장 자주 사용되는 항목), 5229 및 5230.

**iOS**:

이진 커넥터:알림을 전송하려면 포트 2195에서 인바운드 및 아웃바운드 TCP 트래픽을 인증해야 합니다. 푸시 서비스에 연결된 장치는 포트 5223에서 인바운드 및 아웃바운드 TCP 트래픽을 승인해야 합니다.

HTTP/2 커넥터:다음 서버와의 통신을 허용해야 합니다.

* api.push.apple.com:포트 443
* api.development.push.apple.com:포트 443

>[!NOTE]
>
>두 커넥터에 대한 자세한 내용은 커넥터를 [참조하십시오](../../delivery/using/setting-up-mobile-app-channel.md#connectors).
