---
title: 애플리케이션 객체
seo-title: 애플리케이션 객체
description: 애플리케이션 객체
seo-description: null
page-status-flag: never-activated
uuid: 84fbad0f-872d-4aca-8ea9-007577be076d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 24d4875b-81fa-4bf3-8cf0-e6998bec4949
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1937c1ddcbde092a22f4fe8c50d3d72b02cfeed

---


# 애플리케이션 객체{#application-objects}

내장된 개체를 모니터링하고 너무 많이 자라지 않도록 하는 것이 중요합니다.

## ID 시퀀스 {#sequence-of-ids}

Adobe Campaign은 이에 따라 소비해야 하는 ID 시퀀스를 사용합니다.xtk **NewId**. 시퀀스가 매우 빨리 소비되는 경우(즉, 하루에 10만 개의 이메일을 전송하는 경우) 비즈니스 요구 사항과 일치하는지 확인해야 합니다. 특정 테이블에 대한 전용 시퀀스를 정의할 수 있습니다. ID 사용을 모니터링하는 워크플로우를 설정할 수 있습니다.

시퀀스가 20억(214748만3648건)이 넘으면 다시 0으로 돌아갑니다. 이 시퀀스를 피하고 문제를 발생시켜야 하므로 이 시퀀스를 모니터링해야 합니다.

큰 표가 있는 경우를 방지하려면 특정 시퀀스를 사용하는 것이 좋습니다. 스키마의 pkSequence **특성을 사용하여** 수행할 수 있습니다.

많은 로그를 만드는 빈도가 높은 워크플로우에서는 많은 ID를 사용합니다. 따라서 워크플로우에서 너무 많은 로그와 높은 주파수를 사용하지 않는 것이 좋습니다.

시퀀스가 이미 순환한 경우, 가장 좋은 방법은 -2,147,483,648부터 시작하여 네거티브 ID로 전환하는 것입니다.

## 폴더 {#folders}

모든 인스턴스에는 1,000개 미만의 폴더가 있어야 합니다. 폴더보다 폴더가 많으면 캠페인 클라이언트에 성능 문제가 발생할 수 있습니다. 모니터링 작업을 설정하여 폴더, 워크플로우 등의 수를 계산하고 주기적으로 다시 보고할 수 있습니다.

또한 개체를 너무 많이 만드는 사용자를 강조 표시합니다.

## 배달 {#deliveries}

인스턴스에는 언제든지 1,000개 미만의 배달이 있어야 합니다. 배달이 많으면 데이터베이스 공간이 많이 소모되고 문제가 발생합니다. 하루에 10개 이상의 게재를 생성하는 인스턴스는 비즈니스 요구 사항에 따라 확인되어야 합니다. 연속 배달을 사용하여 적은 배달을 만드는 것을 고려해 보십시오. For more on this, refer to [this section](../../workflow/using/continuous-delivery.md).

2년 이전의 배달은 인스턴스에서 제거해야 합니다.

## 파일 {#files}

응용 프로그램 서버 디스크의 파일 수는 무한히 증가해서는 안 됩니다.

가져오기 워크플로우에서 파일을 만들어 디스크 확장을 발생시킵니다. 표준 파일 수집 [](../../workflow/using/file-collector.md) 활동을 사용하면 이러한 작업을 수행할 수 없습니다. 파일 컬렉터가 파일을 임시 폴더로 이동하여 자동으로 제거합니다.

워크플로우가 파일을 가져오고 표준 기능을 사용하지 않는 경우 디스크 공간을 최소한으로 유지하기 위해 해당 기능을 제거해야 합니다.

## 트랜잭션 데이터 및 로그 {#transactional-data-and-logs}

데이터를 Adobe Campaign으로 가져오는 모든 [워크플로우는](../../workflow/using/executing-a-workflow.md#work-table) 데이터베이스 크기가 커지게 합니다.

정리 또는 제거 워크플로우가 실행 중이고 기록을 효과적으로 제거하고 있는지 확인합니다. 모든 트랜잭션 데이터 및 로그를 제거해야 합니다. 정리 작업은 표준 테이블만 삭제합니다.추적 및 광범위한 로그 특정 테이블은 특정 워크플로우로 제거해야 합니다. 이 [섹션을](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs)참조하십시오.

기록의 가장 오래된 작성 날짜를 확인하여 거래 데이터의 에이징을 감시합니다.
