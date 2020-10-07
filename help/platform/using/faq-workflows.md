---
title: 워크플로우 FAQ
seo-title: 워크플로우를 통해 프로세스 자동화 및 데이터 관리
description: Campaign Classic FAQ
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 100%

---


# 워크플로우 FAQ {#workflows-faq}

Adobe Campaign 워크플로우를 통해 프로세스와 작업을 오케스트레이션하는 방법을 배웁니다.

## 워크플로우를 만드는 주요 단계는 무엇입니까? {#what-are-the-key-steps-to-create-a-workflow-}

[첫 번째 워크플로우를 만드는 방법을 배우려면 여기를 클릭하십시오](../../workflow/using/building-a-workflow.md). Campaign에서 워크플로우를 빌드하기 위한 개념과 모범 사례를 배웁니다.

## Campaign에서 데이터를 가져오려면 어떻게 해야 합니까? {#how-can-i-import-data-in-campaign-}

[이 섹션의](../../workflow/using/importing-data.md) Campaign 워크플로우를 통해 데이터를 가져오는 모범 사례에 대해 배웁니다.

## 워크플로우 실행을 모니터링할 수 있습니까? {#can-i-monitor-workflow-execution-}

[이 페이지](../../workflow/using/starting-a-workflow.md)에서 Campaign 워크플로우 실행을 모니터링하는 방법을 이해합니다.

## 워크플로우로 Campaign 데이터를 어떻게 업데이트할 수 있습니까? {#how-can-i-update-campaign-data-with-a-workflow-}

데이터베이스의 데이터에 대해 대규모 업데이트, 병합 및 삽입 작업을 수행할 수 있습니다.

[자세한 내용을 보려면 여기를 클릭하십시오](../../workflow/using/update-data.md).

## 데이터 관리 기능을 활용하려면 어떻게 해야 합니까? {#how-can-i-leverage-data-management-capabilities-}

Adobe Campaign에서는 보다 효율적이고 유연한 도구를 제공하여 복잡한 타겟팅 문제를 해결하는 활동 집합을 활용할 수 있습니다. 데이터 관리 활동을 사용하면 계약, 구독, 게재 반응성 등과 관련된 정보를 사용하여 연락처와 모든 커뮤니케이션을 일관성 있게 관리할 수 있습니다. 데이터 관리를 사용하면 세분화 작업 중 특히 다음의 데이터 라이프 사이클을 추적할 수 있습니다.

* 데이터 마트에서 모델링되지 않은 데이터를 포함하여 타겟팅 프로세스를 단순화 및 최적화(새 테이블 만들기: 구성에 따라 각 타겟팅 워크플로우에 대한 로컬 확장).
* 특히 타겟 구성 단계 또는 데이터베이스 관리 동안 버퍼 계산 보관 및 전달
* 외부 베이스 액세스(선택 사항): 타겟팅 프로세스 중에 고려된 다른 유형의 데이터베이스

[여기를 클릭하여 자세히 알아보고](../../workflow/using/targeting-data.md#data-management) 복합 타겟을 디자인하며 데이터 관리 워크플로우 활동을 결합한 데이터 작업을 수행합니다.

## 개인화된 메시지 전송을 자동화할 수 있습니까? {#can-i-automate-personalized-messages-sending-}

[이 활용 사례](../../workflow/using/enriching-data.md)를 읽어 참가자의 가장 높은 점수를 기준으로 개인화된 메시지를 고객에게 보냅니다.

## 워크플로우로 하위 집합에서 대상을 분할하려면 어떻게 해야 합니까? {#how-can-i-split-an-audience-in-subsets-with-a-workflow-}

[이 섹션에서](../../workflow/using/split.md) 대상을 여러 하위 집합으로 분할하는 방법을 알아봅니다.

## 외부 파일에서 수신자 데이터를 업데이트하려면 어떻게 해야 합니까? {#how-can-i-update-recipient-data-from-an-external-file-}

캠페인 테이블의 특정 필드를 외부 텍스트 파일의 값으로 수정할 수 있습니다.

[방법을 알아보려면 여기를 클릭하세요](../../platform/using/importing-data.md#example--enrich-the-values-with-those-of-an-external-file).

## 신규 수신자를 식별하고 타겟팅하려면 어떻게 해야 합니까? {#how-can-i-identify-and-target-new-recipients-}

[이 사용 사례](../../workflow/using/using-aggregates.md)에서는 집계를 사용하여 데이터베이스에 추가된 마지막 수신자를 자동으로 식별하고 환영 메시지를 보내는 방법을 알아봅니다.
