---
product: campaign
title: 캠페인 유형 분류 정보
description: 캠페인 유형 분류 정보
audience: campaign
content-type: reference
topic-tags: campaign-optimization
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 17%

---

# 캠페인 유형 분류 정보{#about-campaign-typologies}

![](../../assets/v7-only.svg)

캠페인 최적화는 게재 전송을 제어, 필터링 및 모니터링할 수 있는 Adobe Campaign 모듈입니다. 캠페인 간의 충돌을 방지하기 위해 Adobe Campaign은 특정 제한 조건을 적용하여 다양한 조합을 테스트할 수 있습니다. 따라서 전송되는 메시지는 고객 및 회사 커뮤니케이션 정책의 요구 및 기대를 충족하도록 보장합니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#typologies-video)

>[!NOTE]
>
>오퍼링에 따라 캠페인 최적화를 포함하거나 추가 기능을 추가할 수 있습니다. 사용권 계약을 확인하십시오.

## 유형화 규칙 {#typology-rules}

Adobe Campaign을 사용하여 네 가지 유형의 유형화 규칙을 디자인하고 적용할 수 있습니다.

* **** 기준에 따라 대상의 일부를 제외할 수 있는 필터링 규칙. 자세한 내용은 [필터링 규칙](filtering-rules.md)을 참조하십시오.
* **** 마케팅 피로도 제어할 수 있는 사전 요구 규칙입니다. 자세한 내용은 [압력 규칙](pressure-rules.md)을 참조하십시오.
* **** 최적의 처리 조건을 보장하기 위해 로드를 제한할 수 있는 커패시티 규칙입니다. 자세한 내용은 [용량 제어](consistency-rules.md#controlling-capacity)를 참조하십시오.
* **** 메시지를 보내기 전에 메시지의 유효성을 확인할 수 있는 규칙을 제어합니다. 자세한 내용은 [제어 규칙](control-rules.md)을 참조하십시오.

유형화 규칙을 만들면 게재 시 참조되는 캠페인 유형화로 그룹화됩니다. [유형화 적용](#applying-typologies)을 참조하십시오.

## 유형화 {#typologies}

캠페인 유형화에는 여러 개의 [유형화 규칙](#typology-rules)이 포함될 수 있지만, 게재는 하나의 유형화만 참조할 수 있습니다.

**[!UICONTROL Rules]** 탭에서는 적용할 유형화 규칙을 추가, 삭제 또는 볼 수 있습니다.

![](assets/campaign_opt_rules_tab.png)

## 유형화 적용 {#applying-typologies}

게재에 유형화를 만들고 적용하는 단계는 아래에 나와 있습니다.

1. 유형화 규칙을 만듭니다.

   유형화 규칙이 **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 노드에 있습니다.

   Campaign에서 사용할 수 있는 다양한 규칙은 다음 섹션에서 설명합니다. [영업 압력 규칙](pressure-rules.md), [능력 규칙](consistency-rules.md#controlling-capacity), [제어 규칙](control-rules.md) 및 [필터링 규칙](filtering-rules.md)을 참조하십시오.

1. 유형화를 만들고 유형화로 만든 규칙을 참조합니다.

   유형화는 **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** 노드를 통해 액세스합니다.

1. 생성한 유형화를 사용하도록 게재를 구성합니다. 이 작업에 대한 자세한 정보는 [이 섹션](applying-rules.md#applying-a-typology-to-a-delivery)을 참조하십시오.
1. 캠페인 시뮬레이션을 통해 동작을 테스트 및 제어합니다. 캠페인 시뮬레이션에 대한 자세한 정보는 [이 섹션](campaign-simulations.md)을 참조하십시오.

게재를 준비하는 동안 기준이 충족되면 수신자는 제외됩니다. 로그를 확인하여 제외 사항을 모니터링할 수 있습니다. 압력 유형화 규칙에 대한 샘플 사용 사례는 [이 페이지](pressure-rules.md#use-cases-on-pressure-rules)에서 확인할 수 있습니다.

## 튜토리얼 비디오 {#typologies-video}

### 유형화 규칙을 사용하여 피로도 관리를 설정하는 방법입니다

이 비디오에서는 유형화 규칙을 활용하여 Adobe Campaign에서 피로 관리를 구현하는 방법을 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### 사전 정의된 필터를 사용하여 피로 관리를 설정하는 방법

피로도 관리는 수신자의 과도한 요청을 방지하기 위해 메시지 빈도 및 수량을 제어합니다. 캠페인 인스턴스에 캠페인 최적화 모듈이 없는 경우 사전 정의된 필터를 구성하여 수신한 메시지 수로 대상 모집단을 필터링할 수 있습니다
이 비디오에서는 필터를 사용하여 Adobe Campaign Classic에서 피로도 관리를 구현하는 방법을 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

추가 Campaign 방법 비디오는 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.

**관련 항목**

* [모든 채널의 게재에 자동 비즈니스 규칙 적용](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)

* [유형화 및 피로도 관리 시작](pressure-rules.md)

