---
title: 템플릿 라우팅
seo-title: 템플릿 라우팅
description: 템플릿 라우팅
seo-description: null
page-status-flag: never-activated
uuid: 1f8252c4-7f96-4759-9544-39b8f854961f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 8fa464e6-3c88-441c-8179-0c54960469a7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 템플릿 라우팅{#routing-towards-a-template}

메시지 템플릿이 실행 인스턴스에 게시되면 실시간으로 연결되거나 배치 이벤트가 자동으로 생성됩니다. 라우팅 단계는 이벤트를 적절한 메시지 템플릿에 연결하는 것으로 구성됩니다. 연결은 이벤트 자체 및 템플릿의 속성에 지정된 이벤트 유형을 기반으로 합니다.

이벤트 속성의 이벤트 유형 정의:

![](assets/messagecenter_event_type_001.png)

메시지 템플릿 속성의 이벤트 유형 정의:

![](assets/messagecenter_event_type_002.png)

기본적으로 라우팅은 다음 정보를 기반으로 합니다.

* 이벤트 유형,
* 사용할 채널(기본적으로:이메일),
* 게시 날짜를 기준으로 한 최신 배달 템플릿입니다.

