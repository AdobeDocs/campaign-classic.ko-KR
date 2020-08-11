---
title: 캠페인 유형 정보
seo-title: 캠페인 유형 정보
description: 캠페인 유형 정보
seo-description: null
page-status-flag: never-activated
uuid: ec89fb14-7e2f-4e9f-b7ab-3c2caf93a697
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 72c5151c-ce1e-425a-9aee-beefe9f21a67
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3566f42b92cc1b7280bf9b6e9e0b4da7a54f61db
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 5%

---


# 캠페인 유형 정보{#about-campaign-typologies}

캠페인 최적화는 게재 전송을 제어, 필터링 및 모니터링할 수 있는 Adobe Campaign 모듈입니다. 캠페인 간의 충돌을 피하기 위해, Adobe Campaign은 특정 제한 규칙을 적용하여 다양한 조합을 테스트할 수 있습니다. 따라서 전송된 메시지는 고객과 회사 커뮤니케이션 정책의 요구 및 기대를 충족시킵니다.

>[!NOTE]
>
>오퍼에 따라 캠페인 최적화를 포함하거나 추가 기능을 추가할 수 있습니다. 사용권 계약을 확인하십시오.

## 유형화 규칙 {#typology-rules}

Adobe Campaign을 사용하면 4가지 유형의 분류 규칙을 디자인하고 적용할 수 있습니다.

* **기준을 기준으로 대상의 일부를 제외할 수 있는 필터링** 규칙. For more on this, refer to [Filtering rules](../../campaign/using/filtering-rules.md).
* **마케팅 피로도를 제어할 수 있는 압력** 규칙입니다. For more on this, refer to [Pressure rules](../../campaign/using/pressure-rules.md).
* **최적의 처리 조건을 보장하도록 로드를 제한하는 용량** 규칙 For more on this, refer to [Controlling capacity](../../campaign/using/consistency-rules.md#controlling-capacity).
* **메시지가 전송되기 전에 메시지의 유효성을 확인할 수 있는 규칙을** 제어합니다. For more on this, refer to [Control rules](../../campaign/using/control-rules.md).

이러한 유형이 만들어지면 분류 규칙이 게재에서 참조되는 캠페인 유형 유형에서 그룹화됩니다. 유형 [적용 을 참조하십시오](#applying-typologies).

## 유형화 {#typologies}

캠페인 유형에는 몇 가지 유형 [규칙이](#typology-rules)포함될 수 있지만 배달은 하나의 유형만 참조할 수 있습니다.

이 **[!UICONTROL Rules]** 탭에서는 적용할 분류 규칙을 추가, 삭제 또는 볼 수 있습니다.

![](assets/campaign_opt_rules_tab.png)

## 유형 적용 {#applying-typologies}

게재에 유형을 생성하고 적용하는 단계는 다음과 같습니다.

1. 유형 규칙을 만듭니다.

   Typical 규칙이 **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 노드에서 발견되었습니다.

   Campaign에서 사용할 수 있는 다양한 규칙은 다음 섹션에 설명되어 있습니다. [판매 압력 규칙](../../campaign/using/pressure-rules.md), [용량 규칙](../../campaign/using/consistency-rules.md#controlling-capacity), [제어 규칙](../../campaign/using/control-rules.md) 및 [필터링 규칙](../../campaign/using/filtering-rules.md).

1. 유형을 만들고 여기에 만든 규칙을 참조합니다.

   유형 분류는 **[!UICONTROL Administration > Campaign Management > Typology management]** > 노드를 통해 **[!UICONTROL Typologies]** 액세스합니다.

1. 만든 유형을 사용하도록 배달을 구성합니다. 자세한 정보는 [이 섹션](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery)을 참조하십시오.
1. 캠페인 시뮬레이션을 통해 동작을 테스트하고 제어할 수 있습니다. For more on campaign simulations, refer to [this section](../../campaign/using/campaign-simulations.md).

배달 준비 중, 수신자는 기준이 충족될 때 제외됩니다. 로그를 확인하여 제외 사항을 모니터링할 수 있습니다. 압력 유형 규칙에 대한 샘플 사용 사례는 [이 페이지에서 확인할 수 있습니다](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules).

## 분류 규칙을 사용하여 피로 관리를 설정하는 방법

이 비디오에서는 유형 규칙을 활용하여 Adobe Campaign Classic에서 피로 관리를 구현하는 방법을 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

## 사전 정의된 필터를 사용하여 피로 관리를 설정하는 방법

피로 관리는 수신자의 과도한 호객행위를 방지하기 위해 메시지 빈도와 양을 제어합니다. 캠페인 인스턴스에 캠페인 최적화 모듈이 없는 경우 수신한 메시지 수별로 타겟 모집단을 필터링하는 사전 정의된 필터를 구성할 수 있습니다. 이 비디오에서는 필터를 사용하여 Adobe Campaign Classic에서 피로 관리를 구현하는 방법을 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

**관련 항목**

* [모든 채널의 게재에 자동 비즈니스 규칙 적용](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)

* [캠페인 유형 정보](../../campaign/using/pressure-rules.md)

* [압력 규칙으로 마케팅 피로도 관리](https://docs.adobe.com/content/help/en/campaign-classic/using/orchestrating-campaigns/campaign-optimization/pressure-rules.html)