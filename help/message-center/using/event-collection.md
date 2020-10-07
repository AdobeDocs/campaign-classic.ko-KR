---
title: 이벤트 컬렉션
seo-title: 이벤트 컬렉션
description: 이벤트 컬렉션
seo-description: null
page-status-flag: never-activated
uuid: 8c373962-40d4-4982-9bd1-ce1cf8261dd5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: cfff302a-6ac0-461a-a1e4-8e4b617fe134
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 7%

---


# 이벤트 컬렉션{#event-collection}

정보 시스템에서 생성된 이벤트는 다음 두 가지 모드를 사용하여 수집할 수 있습니다.

* SOAP 메서드 호출 기능을 사용하면 Adobe Campaign에서 이벤트를 푸시할 수 있습니다.PushEvent 메서드를 사용하면 한 번에 하나의 이벤트를 전송할 수 있으며, PushEvents 메서드를 사용하면 여러 이벤트를 한 번에 전송할 수 있습니다. 이벤트 [설명을 참조하십시오](../../message-center/using/event-description.md).
* 워크플로우를 만들면 파일을 가져오거나 SQL 게이트웨이를 통해 이벤트를 복구할 수 있습니다( **통합 데이터 액세스** 옵션 사용).

이벤트가 수집되면 메시지 템플릿에 연결되기를 기다리는 동안, 기술 워크플로우별로 실행 인스턴스의 실시간 대기열과 일괄 큐 간에 이벤트가 분류됩니다.

![](assets/messagecenter_events_queues_001.png)

