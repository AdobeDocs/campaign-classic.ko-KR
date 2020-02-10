---
title: 웹 추적 정보
seo-title: 웹 추적 정보
description: 웹 추적 정보
seo-description: null
page-status-flag: never-activated
uuid: 59d18ffb-c26e-4571-8364-5e85ec587349
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 38ba9be9-dabc-41d4-878c-d772955301fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 웹 추적 정보{#about-web-tracking}

Adobe Campaign 플랫폼을 사용하면 인터넷 사용자가 이메일 메시지에서 링크를 클릭하는 동작을 보여주는 표준 추적 외에도 인터넷 사용자가 웹 사이트를 검색하는 방법에 대한 정보를 수집할 수 있습니다. 이 데이터 수집은 웹 추적 모듈에서 수행됩니다.

인터넷 사용자가 주어진 배달에서 전자 메일에 있는 추적된 링크를 클릭하면 리디렉션 서버가 브로드로그 식별자(broadlogId) 및 배달 식별자(deliveryId)가 포함된 세션 쿠키를 보관합니다.

그런 다음 웹 클라이언트는 사용자가 웹 추적 태그가 포함된 페이지를 방문할 때마다 이 쿠키를 서버로 보냅니다. 이 작업은 웹 클라이언트가 닫힐 때까지 세션 동안 계속됩니다.

리디렉션 서버는 다음과 같은 방식으로 데이터를 수집합니다.

* 매개 변수로 전송된 식별자를 통해 본 페이지의 URL
* 세션 쿠키를 통해 웹 페이지를 방문한 배달
* 세션 쿠키를 통해 클릭한 인터넷 사용자의 식별자입니다.
* 생성된 비즈니스 볼륨 등의 추가 정보.

다음 다이어그램은 클라이언트와 다양한 서버 사이의 대화 단계를 보여줍니다.

![](assets/d_ncs_integration_webtracking_structure1.png)

