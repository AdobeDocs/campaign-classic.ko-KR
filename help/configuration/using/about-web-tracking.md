---
product: campaign
title: 웹 추적 정보
description: 웹 추적 정보
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# 웹 추적 정보{#about-web-tracking}

![](../../assets/v7-only.svg)

Adobe Campaign 플랫폼을 사용하면 전자 메일 메시지에서 링크를 클릭하는 인터넷 사용자의 동작을 표시하는 표준 추적 외에도 인터넷 사용자가 웹 사이트를 검색하는 방법에 대한 정보를 수집할 수 있습니다. 이 데이터 수집은 웹 추적 모듈에 의해 수행됩니다.

인터넷 사용자가 주어진 게재에서 전자 메일에서 추적된 링크를 클릭하면 리디렉션 서버가 브로드로그 식별자(broadlogId) 및 게재 식별자(deliveryId)가 포함된 세션 쿠키를 예약합니다.

그러면 웹 클라이언트는 사용자가 웹 추적 태그가 포함된 페이지를 방문할 때마다 이 쿠키를 서버에 전송합니다. 이 작업은 웹 클라이언트가 닫힐 때까지 세션 전체에서 계속됩니다.

리디렉션 서버는 다음과 같은 방식으로 데이터를 수집합니다.

* 매개 변수로 전송된 식별자를 통해 본 페이지의 URL입니다.
* 세션 쿠키를 통해 웹 페이지를 방문한 게재
* 세션 쿠키를 통해 클릭한 인터넷 사용자의 식별자입니다.
* 생성된 업무 량과 같은 추가 정보.

다음 다이어그램은 클라이언트와 다양한 서버 간의 대화 상자 단계를 보여줍니다.

![](assets/d_ncs_integration_webtracking_structure1.png)
