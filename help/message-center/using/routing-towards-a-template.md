---
solution: Campaign Classic
product: campaign
title: 템플릿을 향해 라우팅
description: 템플릿을 향해 라우팅
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 9%

---


# 템플릿을 향해 라우팅{#routing-towards-a-template}

메시지 템플릿이 실행 인스턴스에 게시되면 실시간으로 연결되거나 일괄 처리 이벤트가 자동으로 생성됩니다. 라우팅 단계는 이벤트를 적절한 메시지 템플릿에 연결하는 것으로 구성됩니다. 연결은 이벤트 자체의 속성과 템플릿의 속성에 지정된 이벤트 유형을 기반으로 합니다.

이벤트 속성에 있는 이벤트 유형의 정의:

![](assets/messagecenter_event_type_001.png)

메시지 템플릿 속성의 이벤트 유형 정의:

![](assets/messagecenter_event_type_002.png)

기본적으로 공정순서는 다음 정보를 기반으로 합니다.

* 이벤트 유형
* 사용할 채널(기본적으로:email)
* 게시 날짜를 기반으로 하는 가장 최근 배달 템플릿
