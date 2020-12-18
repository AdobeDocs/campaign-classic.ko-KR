---
solution: Campaign Classic
product: campaign
title: 이벤트 처리 기본 정보
description: 이벤트 처리 기본 정보
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 3%

---


# 이벤트 처리 기본 정보{#about-event-processing}

트랜잭션 메시지 컨텍스트에서 이벤트는 외부 정보 시스템에 의해 생성되며 **[!UICONTROL PushEvent]** 및 **[!UICONTROL PushEvents]** 메서드를 통해 Adobe Campaign으로 전송됩니다( [이벤트 설명](../../message-center/using/event-description.md) 참조). 여기에는 이벤트 유형(예: 웹 사이트에서 주문 확인 또는 계정 만들기), 이메일 주소 또는 모바일 번호와 같이 이벤트에 연결된 데이터와 배달 전에 트랜잭션 메시지를 채우고 개인화할 수 있는 기타 정보가 포함되어 있습니다. 고객 연락처 정보, 메시지 언어 또는 이메일 형식이 될 수 있습니다.

이벤트 데이터의 예:

![](assets/messagecenter_events_request_001.png)

트랜잭션 메시징 이벤트를 처리하려면 다음 단계를 적용해야 합니다.

1. 이벤트 컬렉션,
1. 메시지 템플릿으로 이벤트 전송,
1. 개인화 데이터를 통한 이벤트 향상,
1. 게재 실행,
1. 연결된 배달이 실패한 이벤트 재활용(Adobe Campaign 작업 과정을 통해 이 단계를 수행할 수 있음).

## 이벤트 상태 {#event-statuses}

**이벤트 내역**&#x200B;은 **[!UICONTROL Message Center]** > **[!UICONTROL Event history]**&#x200B;에서 처리된 모든 이벤트를 하나의 보기로 그룹화합니다. 이벤트 유형별로 또는 **status**&#x200B;로 분류할 수 있습니다. 이러한 상태는 다음과 같습니다.

* **보류 중**:즉, 이벤트는 다음과 같습니다.

   * 수집되고 아직 처리되지 않은 이벤트. **[!UICONTROL Number of errors]** 열에는 값 0이 표시됩니다. 이메일 템플릿이 아직 연결되지 않았습니다.
   * 처리되는 이벤트입니다. 그러나 확인은 잘못된 것입니다. **[!UICONTROL Number of errors]** 열에는 0이 아닌 값이 표시됩니다. 이 이벤트가 다시 처리되는 시기를 알려면 **[!UICONTROL Process requested on]** 열을 참조하십시오.

* **배달 보류**:이벤트가 처리되고 배달 템플릿이 연결됩니다. 이메일이 배달 보류 중이며 클래식 배달 프로세스가 적용됩니다. 자세한 내용은 배달을 열 수 있습니다. [배달](../../delivery/using/about-message-tracking.md)을 참조하십시오.
* **전송**,  **** 무시 및  **배달 오류**:이러한 배달 상태는 updateEventsStatusworkflow를 통해  **** 복구됩니다. 자세한 내용은 관련 제공을 열 수 있습니다.
* **다루지 않은 이벤트**:메시지 센터 라우팅 단계가 실패했습니다. 예를 들어 Adobe Campaign은 이벤트의 템플릿으로 사용되는 이메일을 찾지 못했습니다.
* **이벤트 만료**:최대 전송 시도 수에 도달했습니다. 이벤트는 null로 간주됩니다.
