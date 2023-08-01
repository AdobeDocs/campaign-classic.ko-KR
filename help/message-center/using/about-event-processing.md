---
product: campaign
title: 이벤트 처리
description: Adobe Campaign Classic에서 트랜잭션 메시지 이벤트를 처리하는 방법 알아보기
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 3d85866a-6339-458c-807a-b267cce772b8
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 2%

---

# 이벤트 처리 {#about-event-processing}



트랜잭션 메시지의 컨텍스트에서 이벤트는 외부 정보 시스템에 의해 생성되고 를 통해 Adobe Campaign으로 전송됩니다. **[!UICONTROL PushEvent]** 및 **[!UICONTROL PushEvents]** 메서드(참조) [이벤트 설명](../../message-center/using/event-description.md)).

이 이벤트는 다음과 같이 이벤트에 연결된 데이터를 포함합니다. [유형](../../message-center/using/creating-event-types.md) (주문 확인, 웹 사이트에서의 계정 생성 등), 이메일 주소 또는 모바일 번호와 게재 전에 트랜잭션 메시지를 보강하고 개인화할 수 있는 기타 정보(고객 연락처 정보, 메시지 언어, 이메일 형식 등).

이벤트 데이터의 예:

![](assets/messagecenter_events_request_001.png)

## 이벤트 처리 단계 {#event-processing}

트랜잭션 메시지 이벤트를 처리하기 위해 실행 인스턴스에 다음 단계가 적용됩니다.

1. [이벤트 컬렉션](#event-collection)
1. [메시지 템플릿으로 이벤트 전송](#routing-towards-a-template)
1. 개인화 데이터를 통한 이벤트 보강
1. [게재 실행](../../message-center/using/delivery-execution.md)
1. [이벤트 재활용](#event-recycling) (Adobe Campaign 워크플로우를 통해) 연결된 게재가 실패한 사용자

위의 모든 단계가 실행 인스턴스를 통해 수행되면 타겟팅된 각 수신자는 개인화된 메시지를 받게 됩니다.

>[!NOTE]
>
>트랜잭션 메시지 인스턴스에 대한 자세한 내용은 [트랜잭션 메시지 아키텍처](../../message-center/using/transactional-messaging-architecture.md).


## 이벤트 컬렉션 {#event-collection}

정보 시스템에 의해 생성된 이벤트는 다음 두 가지 모드를 사용하여 수집할 수 있습니다.

* SOAP 메서드를 호출하면 Adobe Campaign에서 이벤트를 푸시할 수 있습니다. PushEvent 메서드를 사용하면 한 번에 하나의 이벤트를 보낼 수 있고 PushEvents 메서드를 사용하면 여러 이벤트를 한 번에 보낼 수 있습니다. 자세한 내용은 [이벤트 설명](../../message-center/using/event-description.md).

* 워크플로우를 만들면 파일을 가져오거나 SQL 게이트웨이를 통해 이벤트를 복구할 수 있습니다( [페더레이션 데이터 액세스](../../installation/using/about-fda.md) 선택 사항).

이벤트가 수집되면 메시지 템플릿에 연결되기를 기다리는 동안 실행 인스턴스의 실시간 큐와 배치 큐 사이에 기술 워크플로우로 이벤트가 분류됩니다.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>실행 인스턴스에서 **[!UICONTROL Real time events]** 또는 **[!UICONTROL Batch events]** 액세스 권한 문제가 발생할 수 있으므로 폴더를 보기로 설정하지 말아야 합니다. 폴더를 보기로 설정하는 방법에 대한 자세한 내용은 [이 섹션](../../platform/using/access-management-folders.md).

## 템플릿을 향해 라우팅 {#routing-towards-a-template}

메시지 템플릿이 실행 인스턴스에 게시되면 두 개의 템플릿이 자동으로 생성됩니다. 하나는 실시간 이벤트에 연결되고 다른 하나는 일괄 처리 이벤트에 연결됩니다.

라우팅 단계는 다음 기준에 따라 이벤트를 적절한 메시지 템플릿에 연결하는 단계로 구성됩니다.

* 이벤트 자체의 속성에 지정된 이벤트 유형:

  ![](assets/messagecenter_event_type_001.png)

* 메시지 템플릿 속성에 지정된 이벤트 유형:

  ![](assets/messagecenter_event_type_002.png)

기본적으로 라우팅은 다음 정보를 사용합니다.

* 이벤트 유형
* 사용할 채널(기본값: 이메일)
* 게시 날짜를 기반으로 한 가장 최근 게재 템플릿

## 이벤트 상태 {#event-statuses}

다음 **이벤트 내역**, 아래 **[!UICONTROL Message Center]** > **[!UICONTROL Event history]** , 처리된 모든 이벤트를 하나의 보기로 그룹화합니다. 이벤트 유형별로 또는 다음을 기준으로 분류할 수 있습니다. **상태**. 이러한 상태는 다음과 같습니다.

* **보류 중**: 이벤트는 다음과 같을 수 있습니다.

   * 방금 수집되었으며 아직 처리되지 않은 이벤트입니다. 다음 **[!UICONTROL Number of errors]** 열에 값 0이 표시됩니다. 이메일 템플릿이 아직 연결되지 않았습니다.
   * 처리되었지만 확인이 잘못된 이벤트. 다음 **[!UICONTROL Number of errors]** 열에 0이 아닌 값이 표시됩니다. 이 이벤트가 다시 처리되는 시기를 확인하려면 **[!UICONTROL Process requested on]** 열.

* **게재 보류 중**: 이벤트가 처리되고 게재 템플릿이 연결됩니다. 이메일이 게재 보류 중이며 클래식 게재 프로세스가 적용됩니다. 자세한 내용은 게재를 열 수 있습니다.
* **전송됨**, **무시됨** 및 **게재 오류**: 이러한 게재 상태는 를 통해 복구됩니다. **updateEventsStatus** 워크플로입니다. 자세한 내용은 관련 게재를 열 수 있습니다.
* **이벤트가 다루지 않음**: 트랜잭션 메시지 라우팅 단계 실패. 예를 들어 Adobe Campaign에서 이벤트의 템플릿 역할을 하는 이메일을 찾지 못했습니다.
* **이벤트 만료됨**: 최대 전송 시도 횟수에 도달했습니다. 이 이벤트는 null로 간주됩니다.

## 이벤트 재활용 {#event-recycling}

특정 채널에서 메시지를 배달하지 못하는 경우 Adobe Campaign에서 다른 채널을 사용하여 메시지를 다시 보낼 수 있습니다. 예를 들어 SMS 채널에서의 게재가 실패할 경우 이메일 채널을 사용하여 메시지가 다시 전송됩니다.

이렇게 하려면 를 사용하여 모든 이벤트를 다시 만드는 워크플로우를 구성해야 합니다. **게재 오류** 상태를 확인하고 다른 채널을 할당합니다.

>[!CAUTION]
>
>이 단계는 워크플로우를 통해서만 수행할 수 있으므로 전문가 사용자용으로 예약되어 있습니다. 자세한 내용은 Adobe 계정 담당자에게 문의하십시오.