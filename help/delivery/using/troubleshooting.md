---
product: campaign
title: 푸시 문제 해결
description: 푸시 문제 해결
feature: Push, Troubleshooting
role: User
hide: true
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
TQID: https://experienceleague.adobe.com/3T6eC52Edyai-8Bn-ioDxvB5C04iDqBNmlZzuxVturE
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 109
ht-degree: 0%

---

# 문제 해결{#troubleshooting}

모바일 장치가 Wi-Fi에 연결되어 있고 알림을 받지 못하는 경우, FCM/APNs 포트가 방화벽에 의해 차단되고 있지 않은지 확인하십시오.

**Android**: 모바일 장치가 포트 5228에서 5230까지의 FCM 서버에 연결됩니다. 따라서 FCM과의 연결을 승인하도록 방화벽을 구성해야 합니다. 열려는 포트는 5228(가장 자주 사용됨), 5229 및 5230입니다.

**iOS**:

HTTP/2 커넥터: 다음 서버와의 통신을 허용해야 합니다.

* api.push.apple.com: 포트 443
* api.development.push.apple.com: 포트 443

>[!NOTE]
>
>두 커넥터에 대한 자세한 내용은 [Adobe Campaign에서 모바일 응용 프로그램 구성](configuring-the-mobile-application.md)을 참조하세요.
