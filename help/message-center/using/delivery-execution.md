---
solution: Campaign Classic
product: campaign
title: 게재 실행
description: 게재 실행
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 1788346f7dfe2c18c490363c90358fcb737f1646
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 4%

---


# 게재 실행{#delivery-execution}

## {#transactional-message-send}을(를) 보내는 트랜잭션 메시지

실행 인스턴스에서, 농축 단계가 완료되고 배달 템플릿이 이벤트에 연결되면 배달이 전송됩니다.

>[!NOTE]
>
>MTA는 다른 배달보다 트랜잭션 메시지 처리를 우선 배치합니다.

모든 배달은 **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** 폴더로 그룹화됩니다.

![](assets/messagecenter_deliveries_execinstances_001.png)

기본적으로 배달 월별로 하위 폴더로 정렬됩니다. 이 정렬은 아래와 같이 메시지 템플릿 속성에서 변경할 수 있습니다.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>호스팅 또는 하이브리드 설치 환경에서 향상된 MTA로 업그레이드한 경우 향상된 전달 능력, 처리량 및 바운스 처리를 위해 모든 트랜잭션 메시지를 Adobe Campaign Enhanced MTA와 함께 보낼 수 있습니다. 모든 영향은 표준 마케팅 메시지와 동일하며 [Adobe Campaign Enhanced MTA](https://helpx.adobe.com/kr/campaign/kb/acc-campaign-enhanced-mta.html) 문서에 자세히 설명되어 있습니다.

## 트랜잭션 메시지 모니터링 {#transactional-message-monitoring}

트랜잭션 메시지를 모니터링하려면 배달 로그를 확인하십시오. 배달 로그에 액세스하는 방법은 [이 섹션](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)에 있습니다.

실행 인스턴스에서 전송된 트랜잭션 배달은 매 시간마다 실행되는 기술 워크플로(**[!UICONTROL Message Center execution instance]**)를 통해 제어 인스턴스로 다시 동기화됩니다.

>[!NOTE]
>
>배달은 이벤트 생성 날짜가 아닌 최신 이벤트 업데이트를 기반으로 하여 이벤트를 주별로 누적합니다. 따라서 제어 인스턴스에서 트랜잭션 메시징 배달 로그를 추출할 때 각 배달 로그 ID와 연결된 배달 ID는 로그가 업데이트되면(예: 이벤트에 대한 인바운드 바운스가 수신될 때) 시간에 따라 변경될 수 있습니다.

<!--The transactional deliveries sent from the execution instance are synchronized back to the control instance as follows.

Let's take a [delivery template](../../message-center/using/introduction.md) labelled *Template_1*.

1. An event corresponding to *Template_1* is received on the execution instance.
1. The **Processing real time events** (rtEventsProcessing) workflow processes the event and searches for an existing delivery for the current month.

    >[!NOTE]
    >
    >If not found, a new delivery is created and the event is assigned to the new delivery.

1. The transactional email is sent and the delivery status changes to **[!UICONTROL Sent]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and updates the delivery logs on the control instance.
1. The control instance searches for an existing delivery for week 40 (2020-09-28_Template_1).

    >[!NOTE]
    >
    >If not found, a new delivery is created.

1. The week after, an inbound bounce is received for the event.
1. The status of the event changes to **[!UICONTROL Delivery failed]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and searches for a delivery for week 41 (2020-10-05_Template_1) to update the delivery logs. The delivery logs are then linked to a new delivery for the current week.

To summarize, the deliveries weekly accumulate the events based on the latest event update, and not on the event creation date.

Therefore, when extracting transactional messaging delivery logs from the control instance, the delivery ID associated with each delivery log ID changes every week.-->