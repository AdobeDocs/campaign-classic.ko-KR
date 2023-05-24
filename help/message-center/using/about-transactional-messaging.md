---
product: campaign
title: 트랜잭션 메시지 시작
description: Adobe Campaign Classic 트랜잭션 메시지 작동 원리 및 주요 단계에 대해 자세히 알아보십시오
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Transactional Messaging
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 7%

---


# 트랜잭션 메시지 시작 {#about-transactional-messaging}



## 개요 {#overview}

**트랜잭션 메시지** (메시지 센터)는 외부 정보 시스템에서 보낸 이벤트에서 생성된 사용자 지정 트리거 알림을 관리하기 위해 설계된 캠페인 모듈입니다.

트랜잭션 메시지는 웹 사이트와 같은 공급자가 실시간으로 전송하는 개별적이고 고유한 통신입니다. 수신자가 확인하거나 확정하려는 중요한 정보가 포함되어 있기 때문에 특히 기대됩니다.

트랜잭션 메시지 기능은 확장성을 지원하고 연중무휴 서비스를 제공하도록 설계되었습니다.

* **기한이 언제까지죠?** 이 메시지에는 중요한 정보가 포함되어 있으므로 사용자는 실시간으로 전송될 것으로 예상합니다. 따라서 트리거되는 이벤트와 메시지 도착 사이의 지연 시간이 매우 짧아야 합니다.

* **중요한 이유** 일반적으로 트랜잭션 메시지는 오픈율이 높습니다. 따라서 고객 관계를 정의하므로 고객의 행동에 강력한 영향을 줄 수 있으므로 신중하게 설계해야 합니다.

* **예제?** 계정 생성 후 환영 메시지, 주문 배송 확인, 청구서, 암호 변경 확인 메시지, 고객이 웹 사이트를 열람한 후 알림, 제품 비가용성 커뮤니케이션, 계정 명세서 등이 될 수 있습니다.

>[!IMPORTANT]
>
>트랜잭션 메시지에는 특정 라이센스가 필요합니다. 사용권 계약을 확인하십시오.

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## 트랜잭션 메시지 작동 원리 {#transactional-messaging-operating-principle}

Adobe Campaign 트랜잭션 메시지 모듈은 변경할 이벤트를 개인화된 트랜잭션 메시지로 반환하는 정보 시스템에 통합됩니다. 이러한 메시지는 이메일, SMS 또는 푸시 알림을 통해 개별적으로 또는 일괄적으로 전송할 수 있습니다.

이 기능은 다음과 같은 특정 아키텍처를 기반으로 합니다 **실행 인스턴스** 이(가) 다음에서 분리됩니다. **컨트롤 인스턴스**. 이러한 배포를 통해 가용성이 높아지고 로드 관리가 향상됩니다. 자세한 내용은 [트랜잭션 메시지 아키텍처](../../message-center/using/transactional-messaging-architecture.md).

>[!NOTE]
>
>Adobe 클라우드에서 호스팅되는 메시지 센터 실행 인스턴스에 대해 새 사용자를 만들려면 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). 메시지 센터 사용자는 전용 액세스 권한이 필요한 특정 운영자입니다 **[!UICONTROL Real time events (nmsRtEvent)]** 개 폴더.

트랜잭션 메시지 전체 프로세스는 다음과 같이 설명할 수 있습니다.

![](assets/transactional-msg-overview.png)

예를 들어 고객이 제품을 구매할 수 있는 웹 사이트를 보유한 회사라고 가정해 보겠습니다.

Adobe Campaign을 사용하면 장바구니에 제품을 추가한 고객에게 알림 이메일을 보낼 수 있습니다. 둘 중 한 명이 구매(캠페인 이벤트를 트리거하는 외부 이벤트)를 수행하지 않고 웹 사이트를 떠나면 장바구니 포기 이메일이 자동으로 전송됩니다(트랜잭션 메시지 게재).

이 작업을 수행하는 주요 단계는 아래에 자세히 설명되어 있습니다. [이 섹션](#key-steps).

>[!NOTE]
>
>Adobe Campaign은 다른 어떤 게재보다 트랜잭션 메시지 처리에 우선 순위를 둡니다.

## 주요 단계 {#key-steps}

Adobe Campaign에서 개인화된 트랜잭션 메시지를 만들고 관리할 때의 주요 단계는 아래에 요약되어 있습니다.

### 컨트롤 인스턴스에서 수행하는 단계

다음에서 **컨트롤 인스턴스**, 다음 작업을 수행해야 합니다.

1. [이벤트 유형 만들기](../../message-center/using/creating-event-types.md).
1. [메시지 템플릿 만들기 및 디자인](../../message-center/using/creating-the-message-template.md). 이 단계에서 메시지에 이벤트를 연결해야 합니다.
1. [메시지 테스트](../../message-center/using/testing-message-templates.md).
1. [메시지 템플릿을 게시합니다](../../message-center/using/publishing-message-templates.md).

>[!NOTE]
>
>위의 모든 단계는 **컨트롤 인스턴스**. 컨트롤 인스턴스에 템플릿을 게시하면 해당 템플릿도 모든 인스턴스에 게시됩니다 **실행 인스턴스**. 트랜잭션 메시지 인스턴스에 대한 자세한 내용은 [트랜잭션 메시지 아키텍처](../../message-center/using/transactional-messaging-architecture.md).

### 실행 인스턴스에서 이벤트 처리

트랜잭션 메시지 템플릿을 디자인하고 게시하면 해당 이벤트가 트리거되는 경우 아래에 있는 주요 단계가 다음에서 수행됩니다. **실행 인스턴스**:

1. 외부 정보 시스템에 의해 이벤트가 생성되면 관련 데이터가 를 통해 Campaign으로 전송됩니다 **푸시 이벤트** 및 **푸시 이벤트** 메서드를 사용합니다. 다음을 참조하십시오 [이벤트 컬렉션](../../message-center/using/about-event-processing.md#event-collection).
1. 이벤트가 적절한 메시지 템플릿에 연결됩니다. 다음을 참조하십시오 [템플릿을 향해 라우팅](../../message-center/using/about-event-processing.md#routing-towards-a-template).
1. 데이터 보강 단계가 완료되면 게재가 전송됩니다. 다음을 참조하십시오 [게재 실행](../../message-center/using/delivery-execution.md). 타겟팅된 각 수신자는 개인화된 메시지를 수신합니다.

## 관련 항목 {#related-topics}

* [소통 채널 시작](../../delivery/using/communication-channels.md)
* [게재 만들기 주요 단계](../../delivery/using/steps-about-delivery-creation-steps.md)
* [트랜잭션 메시지 아키텍처](../../message-center/using/transactional-messaging-architecture.md)
* [트랜잭션 메시지 보고서 액세스](../../message-center/using/about-transactional-messaging-reports.md)
