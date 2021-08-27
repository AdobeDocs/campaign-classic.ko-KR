---
product: campaign
title: 프로덕션 문제 해결
description: Adobe Campaign 구성, 모니터링, 업그레이드 프로세스, 데이터 처리 및 데이터베이스 유지 관리 절차와 관련된 프로덕션 문제 해결 절차를 살펴봅니다.
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 78c65b31-e3d9-4a46-a101-26f35d00a4ee
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 18%

---

# 프로덕션 문제 해결{#troubleshooting}

![](../../assets/v7-only.svg)

이 섹션에서는 게재 및 워크플로우 실행, 모니터링, 데이터베이스 유지 관리, 연결 등과 같은 Adobe Campaign 일반 프로덕션 문제와 관련된 문제 해결 절차를 설명합니다.

## 공통 및 일반적인 문제 {#common-and-general-issues}

* 이 [page](../../production/using/modules-and-frequent-issues.md)에서는 나열된 모듈에 대해 발생하는 가장 빈번한 문제를 나타냅니다.
* 이 [페이지](../../production/using/workflow-execution.md)에는 워크플로우 실행 시 문제가 발생할 때 따라야 하는 일반적인 문제 해결 절차가 나와 있습니다.
* 이 [페이지](../../production/using/lost-password.md)에서는 손실된 암호를 변경하거나 복구하는 방법을 자세히 설명합니다.
* 이 [페이지](../../production/using/console-update.md)에서는 해당 옵션을 비활성화한 경우 콘솔 업데이트 요청을 다시 활성화하는 방법을 자세히 설명합니다.

## 게재 문제 해결 {#delivery-troubleshooting}

게재에 문제가 있을 경우 특정 작업을 수행할 수 있습니다.
* [게재 가능성 문제](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [이미지 표시 문제](../../production/using/image-display-issues.md)
* [이미지 누락](../../production/using/images-missing.md)
* [임시 파일 문제](../../production/using/temporary-files.md) (*온-프레미스 호스팅 모델만*)

**관련 항목**:

[게재 성능 문제](../../delivery/using/delivery-performances.md)

## 로그 작업 {#working-with-logs}

로그를 사용하여 경험을 개선하는 데 도움이 되는 몇 가지 팁은 다음과 같습니다.

* [로그 정밀도](../../production/using/log-precision.md)
* [추적 로그 문제](../../production/using/tracking-logs-issues.md)

## 데이터베이스 문제 {#database-issues}

다음 섹션을 참조하여 성능 문제를 해결하는 방법을 알아보십시오.

* [데이터베이스 성능](../../production/using/database-performances.md)
* [Oracle 데이터베이스의 인코딩](../../production/using/encoding-of-the-oracle-database.md)

## 연결 개선 사항 {#connection-improvements}

연결 문제가 발생하는 경우 몇 가지 방법으로 문제를 해결할 수 있습니다.

* [연결 실패](../../production/using/failure-to-connect.md)
* [연결 임계값](../../production/using/connection-thresholds.md)

## 기술 문제 해결 {#technical-troubleshooting}

자세한 내용은 아래 섹션으로 이동하십시오.

* [Linux의 스택 추적](../../production/using/stack-trace-in-linux.md)
* [JSP 동작](../../production/using/jsp-behavior.md)
* [Tomcat 버전 찾기](../../production/using/locate-tomcat-version.md)
