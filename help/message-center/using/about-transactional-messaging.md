---
product: campaign
title: 트랜잭션 메시지 시작
description: Adobe Campaign Classic 트랜잭션 메시지 작동 원리 및 주요 단계에 대해 자세히 알아보십시오
feature: Transactional Messaging, Message Center
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 4%

---


# 트랜잭션 메시지 시작 {#about-transactional-messaging}



## 개요 {#overview}

**트랜잭션 메시지**(메시지 센터)는 외부 정보 시스템에서 보낸 이벤트에서 생성된 사용자 지정 트리거 알림을 관리하기 위해 고안된 캠페인 모듈입니다.

트랜잭션 메시지는 웹 사이트와 같은 공급자가 실시간으로 전송하는 개별적이고 고유한 통신입니다. 수신자가 확인하거나 확정하려는 중요한 정보가 포함되어 있기 때문에 특히 기대됩니다.

트랜잭션 메시지 기능은 확장성을 지원하고 연중무휴 서비스를 제공하도록 설계되었습니다.

* **기한이 언제입니까?** 이 메시지에는 중요한 정보가 포함되어 있으므로 사용자는 이 메시지가 실시간으로 전송될 것으로 예상합니다. 따라서 트리거되는 이벤트와 메시지 도착 사이의 지연 시간이 매우 짧아야 합니다.

* **중요한 이유** 일반적으로 트랜잭션 메시지의 열기 비율이 높습니다. 따라서 고객 관계를 정의하므로 고객의 행동에 강력한 영향을 줄 수 있으므로 신중하게 설계해야 합니다.

* **예?** 계정 만들기, 주문 배송 확인, 청구서, 암호 변경 확인 메시지, 고객이 웹 사이트를 열람한 후 알림, 제품 비가용성 커뮤니케이션, 계정 명세서 등을 만든 후 환영 메시지가 될 수 있습니다.

>[!IMPORTANT]
>
>트랜잭션 메시지에는 특정 라이센스가 필요합니다. 사용권 계약을 확인하십시오.

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## 트랜잭션 메시지 작동 원리 {#transactional-messaging-operating-principle}

Adobe Campaign 트랜잭션 메시지 모듈은 변경할 이벤트를 개인화된 트랜잭션 메시지로 반환하는 정보 시스템에 통합됩니다. 이러한 메시지는 이메일, SMS 또는 푸시 알림을 통해 개별적으로 또는 일괄적으로 전송할 수 있습니다.

이 기능은 **실행 인스턴스**&#x200B;가 **제어 인스턴스**&#x200B;와 분리되는 특정 아키텍처를 사용합니다. 이러한 배포를 통해 가용성이 높아지고 로드 관리가 향상됩니다. 자세한 내용은 [트랜잭션 메시지 아키텍처](../../message-center/using/transactional-messaging-architecture.md)를 참조하십시오.

>[!NOTE]
>
>Adobe 클라우드에서 호스팅되는 메시지 센터 실행 인스턴스에 대해 새 사용자를 만들려면 [고객 지원 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의해야 합니다. 메시지 센터 사용자는 **[!UICONTROL Real time events (nmsRtEvent)]**&#x200B;개 폴더에 액세스하는 데 전용 권한이 필요한 특정 운영자입니다.

트랜잭션 메시지 전체 프로세스는 다음과 같이 설명할 수 있습니다.

![](assets/transactional-msg-overview.png)

예를 들어 고객이 제품을 구매할 수 있는 웹 사이트를 보유한 회사라고 가정해 보겠습니다.

Adobe Campaign을 사용하면 장바구니에 제품을 추가한 고객에게 알림 이메일을 보낼 수 있습니다. 둘 중 한 명이 구매(캠페인 이벤트를 트리거하는 외부 이벤트)를 수행하지 않고 웹 사이트를 떠나면 장바구니 포기 이메일이 자동으로 전송됩니다(트랜잭션 메시지 게재).

이 작업을 수행하는 주요 단계는 [이 섹션](#key-steps)에 자세히 설명되어 있습니다.

>[!NOTE]
>
>Adobe Campaign은 다른 어떤 게재보다 트랜잭션 메시지 처리에 우선 순위를 둡니다.

## 주요 단계 {#key-steps}

Adobe Campaign에서 개인화된 트랜잭션 메시지를 만들고 관리할 때의 주요 단계는 아래에 요약되어 있습니다.

### 컨트롤 인스턴스에서 수행하는 단계

**컨트롤 인스턴스**&#x200B;에서 다음 작업을 수행해야 합니다.

1. [이벤트 형식을 만듭니다](../../message-center/using/creating-event-types.md).
1. [메시지 템플릿을 만들고 디자인합니다](../../message-center/using/creating-the-message-template.md). 이 단계에서 메시지에 이벤트를 연결해야 합니다.
1. [메시지를 테스트합니다](../../message-center/using/testing-message-templates.md).
1. [메시지 템플릿을 Publish](../../message-center/using/publishing-message-templates.md).

>[!NOTE]
>
>위의 모든 단계는 **컨트롤 인스턴스**&#x200B;에서 수행됩니다. 컨트롤 인스턴스에 템플릿을 게시하면 모든 **실행 인스턴스**&#x200B;에도 게시됩니다. 트랜잭션 메시지 인스턴스에 대한 자세한 내용은 [트랜잭션 메시지 아키텍처](../../message-center/using/transactional-messaging-architecture.md)를 참조하십시오.

### 실행 인스턴스에서 이벤트 처리

트랜잭션 메시지 템플릿을 디자인하고 게시하면 해당 이벤트가 트리거되는 경우 **실행 인스턴스**&#x200B;에서 아래의 기본 단계가 수행됩니다.

1. 외부 정보 시스템에서 이벤트가 생성되면 관련 데이터가 **PushEvent** 및 **PushEvents** 메서드를 통해 Campaign으로 전송됩니다. [이벤트 컬렉션](../../message-center/using/about-event-processing.md#event-collection)을 참조하세요.
1. 이벤트가 적절한 메시지 템플릿에 연결됩니다. [템플릿을 향해 라우팅](../../message-center/using/about-event-processing.md#routing-towards-a-template)을 참조하세요.
1. 데이터 보강 단계가 완료되면 게재가 전송됩니다. [게재 실행](../../message-center/using/delivery-execution.md)을 참조하세요. 타겟팅된 각 수신자는 개인화된 메시지를 수신합니다.

## 관련 항목 {#related-topics}

* [소통 채널 시작](../../delivery/using/communication-channels.md)
* [게재 만들기 주요 단계](../../delivery/using/steps-about-delivery-creation-steps.md)
* [트랜잭션 메시지 아키텍처](../../message-center/using/transactional-messaging-architecture.md)
* [트랜잭션 메시지 보고서 액세스](../../message-center/using/about-transactional-messaging-reports.md)
