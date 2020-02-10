---
title: 이벤트 처리 정보
seo-title: 이벤트 처리 정보
description: 이벤트 처리 정보
seo-description: null
page-status-flag: never-activated
uuid: 6c3e02b3-0d4d-4661-952a-e4915ca9ef92
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: a78c9986-7c49-47db-99a0-9f0949c4dee7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c2c53041d8a19a491b8ec4da12a8a0ced25cf9a

---


# 이벤트 처리 정보{#about-event-processing}

트랜잭션 메시징 컨텍스트에서 이벤트는 외부 정보 시스템에 의해 생성되며 **[!UICONTROL PushEvent]** 및 **[!UICONTROL PushEvents]** 메서드를 통해 Adobe Campaign으로 전송됩니다(이벤트 설명 [참조](../../message-center/using/event-description.md)). 여기에는 이벤트 유형(예: 웹 사이트에서 주문 확인 또는 계정 생성), 이메일 주소 또는 모바일 번호와 같은 이벤트와 연결된 데이터뿐만 아니라 전달하기 전에 트랜잭션 메시지를 보완하고 개인화할 수 있는 기타 정보가 포함됩니다. 고객 연락처 정보, 메시지 언어 또는 이메일 형식이 될 수 있습니다.

이벤트 데이터의 예:

![](assets/messagecenter_events_request_001.png)

트랜잭션 메시징 이벤트를 처리하려면 다음 단계를 적용해야 합니다.

1. 이벤트 컬렉션,
1. 메시지 템플릿으로 전송되기 전에 이벤트 데이터 수집(Campaign 트랜잭션 메시지 모듈에 사용할 수 있는 데이터 수집 옵션을 취득한 경우),
1. 메시지 템플릿으로 이벤트 전송,
1. 개인화 데이터를 통한 이벤트 향상,
1. 배달 실행,
1. 연결된 배달이 실패한 이벤트 재활용(Adobe Campaign 워크플로우를 통해 수행할 수 있음).

## 이벤트 상태 {#event-statuses}

이벤트 **내역의**> **[!UICONTROL Message Center]** **[!UICONTROL Event history]** 에서 처리된 모든 이벤트를 하나의 보기로 그룹화합니다. 이벤트 유형 또는 **상태별로**&#x200B;분류할 수 있습니다. 이러한 상태는 다음과 같습니다.

* **보류 중**:즉, 이벤트는 다음과 같습니다.

   * 방금 수집되었으며 아직 처리되지 않은 이벤트. 이 **[!UICONTROL Number of errors]** 열에는 값 0이 표시됩니다. 이메일 템플릿이 아직 연결되지 않았습니다.
   * 처리되는 이벤트입니다. 그러나 확인이 잘못된 이벤트입니다. 이 **[!UICONTROL Number of errors]** 열에는 0이 아닌 값이 표시됩니다. 이 이벤트가 다시 처리되는 시기를 알려면 **[!UICONTROL Process requested on]** 열을 참조하십시오.

* **배달**&#x200B;대기 중:이벤트가 처리되고 배달 템플릿이 연결됩니다. 이메일이 배달 보류 중이며 클래식 배달 프로세스가 적용됩니다. 자세한 내용은 배달을 열 수 있습니다. 배달을 [참조하십시오](../../delivery/using/about-message-tracking.md).
* **전송**, **무시** 및 배달 **오류**:이러한 배달 상태는 updateEventsStatus **워크플로우를 통해 복구됩니다** . 자세한 내용은 관련 제공을 열 수 있습니다.
* **이벤트가 포함되지**&#x200B;않음:메시지 센터 라우팅 단계가 실패했습니다. 예를 들어 Adobe Campaign에서 이벤트의 템플릿으로 사용되는 이메일을 찾지 못했습니다.
* **이벤트 만료**:최대 전송 시도 수에 도달했습니다. 이벤트는 null로 간주됩니다.
