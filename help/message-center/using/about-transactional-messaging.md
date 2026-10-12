---
product: campaign
title: 트랜잭션 메시지 시작
description: Adobe Campaign Classic 트랜잭션 메시지 작동 원리 및 주요 단계에 대해 자세히 알아보십시오
feature: Transactional Messaging, Message Center
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
TQID: 'https://experienceleague.adobe.com/n4w2hZkuzHlD3Axc1tUCGfBQ13D28j3Xpmdh07tVr4g'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
source-git-commit: 617db6f51887118c965b8938b2b9f14335293875
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 8%
---
# 트랜잭션 메시지 시작 {#about-transactional-messaging}



## 개요 {#overview}

**트랜잭션 메시지**(메시지 센터)는 외부 정보 시스템에서 보낸 이벤트에서 생성된 사용자 지정 트리거 알림을 관리하기 위해 고안된 캠페인 모듈입니다.

Campaign v7에서 v8로 전환하는 과정의 일부로 Campaign Classic 설명서 세트가 간소화 및 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다. 트랜잭션 메시지에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}

이 섹션에서는 온-프레미스 및 하이브리드 배포에 대한 트랜잭션 메시지 아키텍처와 제어 및 실행 인스턴스의 구성을 다룹니다.

>[!IMPORTANT]
>
>트랜잭션 메시지에는 특정 라이센스가 필요합니다. 사용권 계약을 확인하십시오.

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## 트랜잭션 메시지 작동 원리 {#transactional-messaging-operating-principle}

Adobe Campaign 트랜잭션 메시지 모듈은 변경할 이벤트를 개인화된 트랜잭션 메시지로 반환하는 정보 시스템에 통합됩니다. 이러한 메시지는 이메일, SMS 또는 푸시 알림을 통해 개별적으로 또는 일괄적으로 전송할 수 있습니다.

이 기능은 **실행 인스턴스**&#x200B;가 **제어 인스턴스**&#x200B;와 분리되는 특정 아키텍처를 사용합니다. 이러한 배포를 통해 가용성이 높아지고 로드 관리가 향상됩니다. 자세한 내용은 [트랜잭션 메시지 아키텍처](../../message-center/using/transactional-messaging-architecture.md)를 참조하십시오.

>[!NOTE]
>
>Adobe Cloud에서 호스팅되는 메시지 센터 실행 인스턴스에 대해 새 사용자를 만들려면 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의해야 합니다. 메시지 센터 사용자는 **[!UICONTROL Real time events (nmsRtEvent)]**&#x200B;개 폴더에 액세스하는 데 전용 권한이 필요한 특정 운영자입니다.

>[!NOTE]
>
>Adobe Campaign은 다른 어떤 게재보다 트랜잭션 메시지 처리에 우선 순위를 둡니다.

## 주요 단계 {#key-steps}

Adobe Campaign에서 개인화된 트랜잭션 메시지를 만들고 관리할 때의 주요 단계는 아래에 요약되어 있습니다.

### 컨트롤 인스턴스에서 수행하는 단계

**컨트롤 인스턴스**&#x200B;에서 다음 작업을 수행해야 합니다.

1. [이벤트 유형 만들기](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/real-time/transactional){target="_blank"}(Campaign v8 설명서).
1. [메시지 템플릿을 만들고 디자인](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"}(Campaign v8 설명서). 이 단계에서 메시지에 이벤트를 연결해야 합니다.
1. [메시지를 테스트합니다](../../message-center/using/testing-message-templates.md).
1. [메시지 템플릿을 게시](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"}(Campaign v8 설명서).

>[!NOTE]
>
>위의 모든 단계는 **컨트롤 인스턴스**&#x200B;에서 수행됩니다. 컨트롤 인스턴스에 템플릿을 게시하면 모든 **실행 인스턴스**&#x200B;에도 게시됩니다. 트랜잭션 메시지 인스턴스에 대한 자세한 내용은 [트랜잭션 메시지 아키텍처](../../message-center/using/transactional-messaging-architecture.md)를 참조하십시오.

### 실행 인스턴스에서 이벤트 처리

트랜잭션 메시지 템플릿을 디자인하고 게시하면 해당 이벤트가 트리거되는 경우 **실행 인스턴스**&#x200B;에서 아래의 기본 단계가 수행됩니다.

1. 외부 정보 시스템에서 이벤트가 생성되면 관련 데이터가 **PushEvent** 및 **PushEvents** 메서드를 통해 Campaign으로 전송됩니다. [이벤트 컬렉션](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-collection){target="_blank"}(Campaign v8 설명서)을 참조하세요.
1. 이벤트가 적절한 메시지 템플릿에 연결됩니다. [템플릿을 향해 라우팅](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-to-template){target="_blank"}(Campaign v8 설명서)을 참조하십시오.
1. 데이터 보강 단계가 완료되면 게재가 전송됩니다. [게재 실행](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"}(Campaign v8 설명서)을 참조하세요. 타겟팅된 각 수신자는 개인화된 메시지를 수신합니다.

## 관련 항목 {#related-topics}

* [소통 채널 시작](../../delivery/using/communication-channels.md)
* [게재 만들기 주요 단계](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=ko){target="_blank"}
* [트랜잭션 메시지 아키텍처](../../message-center/using/transactional-messaging-architecture.md)
* [트랜잭션 메시지 보고서 액세스](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"}(Campaign v8 설명서)
