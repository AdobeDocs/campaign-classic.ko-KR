---
title: 배달 유형
seo-title: 배달 유형
description: 배달 유형
seo-description: null
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 707352334144df86ae82aa51d595ae6bc751d1f2

---


# 배달 유형{#types-of-deliveries}

Campaign에는 다음 세 가지 유형의 배달 개체가 있습니다.

## 단일 전달 {#single-delivery}

배달은 **** 한 번 실행되는 독립 실행형 배달 개체입니다. 다시 복제하거나 준비할 수 있지만 최종 상태(취소, 중지, 완료)에 있는 한 다시 사용할 수 없습니다.

배달 목록 또는 배달 활동을 통해 워크플로우 내에서 배달 기능을 만들 [수](../../workflow/using/delivery.md) 있습니다.

또한 워크플로우는 사용할 채널의 유형에 따라 특정 배달 활동을 제공합니다. For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

## 반복 전달 {#recurring-delivery}

반복 **배달을** 사용하면 활동이 실행될 때마다 새 배달을 만들 수 있습니다. 따라서 반복되는 작업에 대해 새 배달을 만들지 않아도 됩니다.

예를 들어, 이 유형의 활동을 한 달에 한 번 실행하는 경우 1년 후에 12개의 게재로 끝납니다.

반복 배달은 반복 배달 활동을 통해 워크플로우 내에서 [생성됩니다](../../workflow/using/recurring-delivery.md). 사용 중인 이 활동의 예는 다음 섹션에 나와 있습니다.타깃팅 [워크플로우에서](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)반복 게재 만들기.

## 지속적인 전달 {#continuous-delivery}

연속 **배달을** 사용하면 기존 배달에 새 수신자를 추가할 수 있으므로 매번 새 배달을 만들 필요가 없습니다.

게재 정보(컨텐츠, 이름 등)가 변경되면 게재 실행 시 새 배달 개체가 생성됩니다. 정보를 변경하지 않은 경우 동일한 배달 개체를 다시 사용하고 동일한 개체에 배달 및 추적 로그가 추가됩니다.

예를 들어, 이 유형의 활동을 한 달에 한 번 실행하는 경우 1년 후 단일 배달로 끝납니다(전달을 변경하지 않은 경우).

연속 배달은 지속적인 배달 활동을 통해 워크플로우 내에서 [생성됩니다](../../workflow/using/continuous-delivery.md).
