---
title: 건축
description: 워크플로우는 특정 모듈로 처리되며, 이 모듈은 처리 부하를 공유하기 위해 여러 서버에서 시작할 수 있습니다.
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3a932bc440853151704f1ba1e188fa0af9d4c5cb
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# 건축 {#architecture}

워크플로우는 특정 모듈에 의해 처리됩니다. 이 모듈은 처리 부하를 공유하기 위해 여러 서버에서 시작할 수 있습니다.

![](assets/architecture.png)

* &#39;Workflow Instance Runner&#39;(runwf) 프로세스는 지정된 워크플로 인스턴스의 모든 작업을 실행합니다. 당분간 실행할 작업이 없으면 &#39;수동적&#39;이 됩니다. 즉, 데이터베이스의 상태를 저장한 다음 중지합니다.
* &#39;Workflow Server&#39;(wfserver) 모듈은 현재 워크플로 인스턴스를 모니터링합니다. 수행할 작업이 있으면 이 모듈은 해당 인스턴스를 활성화(또는 재활성화)하는 프로세스를 생성합니다.

