---
product: campaign
title: 푸시 문제 해결
description: 푸시 문제 해결
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Push
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 2%

---

# 문제 해결{#troubleshooting}



모바일 장치가 Wi-Fi에 연결되어 있고 알림을 받지 못하는 경우, FCM/APNs 포트가 방화벽에 의해 차단되고 있지 않은지 확인하십시오.

**Android**: 모바일 장치가 포트 5228 ~ 5230의 FCM 서버에 연결됩니다. 따라서 FCM과의 연결을 승인하도록 방화벽을 구성해야 합니다. 열려는 포트는 5228(가장 자주 사용됨), 5229 및 5230입니다.

**iOS**:

HTTP/2 커넥터: 다음 서버와의 통신을 허용해야 합니다.

* api.push.apple.com: 포트 443
* api.development.push.apple.com: 포트 443

>[!NOTE]
>
>두 커넥터에 대한 자세한 내용은 다음을 참조하십시오. [Adobe Campaign에서 모바일 애플리케이션 구성](configuring-the-mobile-application.md).
