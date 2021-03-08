---
solution: Campaign Classic
product: campaign
title: 이벤트 컬렉션
description: 이벤트 컬렉션
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---


# 이벤트 컬렉션{#event-collection}

정보 시스템에서 생성된 이벤트는 다음 두 가지 모드를 사용하여 수집할 수 있습니다.

* SOAP 메서드를 호출하면 Adobe Campaign에서 이벤트를 푸시할 수 있습니다.PushEvent 메서드를 사용하면 한 번에 하나의 이벤트를 전송할 수 있으며, PushEvents 메서드를 사용하면 여러 이벤트를 한 번에 전송할 수 있습니다. [이벤트 설명](../../message-center/using/event-description.md)을 참조하십시오.
* 워크플로우를 만들면 파일을 가져오거나 SQL 게이트웨이(**통합 데이터 액세스** 옵션 사용)를 통해 이벤트를 복구할 수 있습니다.

수집된 이벤트는 메시지 템플릿에 연결되기를 기다리는 동안, 기술 워크플로우별로 실행 인스턴스의 실시간 큐와 일괄 대기열 간에 분류됩니다.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>실행 인스턴스에서 올바른 문제에 액세스할 수 있으므로 **[!UICONTROL Real time events]** 또는 **[!UICONTROL Batch events]** 폴더를 보기로 설정하지 않아야 합니다. 폴더를 보기로 설정하는 방법에 대한 자세한 내용은 [이 섹션](../../platform/using/access-management-folders.md)을 참조하십시오.
