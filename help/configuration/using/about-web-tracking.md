---
product: campaign
title: 웹 추적 정보
feature: Configuration, Instance Settings
description: 웹 추적 정보
role: User, Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 8%

---

# 웹 추적 정보{#about-web-tracking}

Adobe Campaign 플랫폼을 사용하면 인터넷 사용자가 이메일 메시지에서 링크를 클릭하는 동작을 표시하는 표준 추적 외에도 인터넷 사용자가 웹 사이트를 검색하는 방법에 대한 정보를 수집할 수 있습니다. 이 데이터 수집은 웹 추적 모듈에 의해 수행됩니다.

인터넷 사용자가 지정된 게재에서 이메일의 추적된 링크를 클릭하면 연결된 리디렉션 서버가 브로드로그 식별자(broadlogId)와 게재 식별자(deliveryId)가 포함된 세션 쿠키를 저장합니다.

그런 다음 웹 클라이언트는 사용자가 웹 추적 태그가 포함된 페이지를 방문할 때마다 이 쿠키를 서버에 보냅니다. 이는 세션 내내, 즉 웹 클라이언트가 닫힐 때까지 계속됩니다.

리디렉션 서버는 이러한 방식으로 다음 데이터를 수집합니다.

* 매개 변수로 전송된 식별자를 통해 본 페이지의 URL
* 세션 쿠키를 통해 웹 페이지를 방문한 게재
* 세션 쿠키를 통해 클릭한 인터넷 사용자의 식별자
* 생성된 거래량과 같은 추가 정보.

다음 다이어그램은 클라이언트와 다양한 서버 간의 대화 단계를 보여 줍니다.

![](assets/d_ncs_integration_webtracking_structure1.png)
