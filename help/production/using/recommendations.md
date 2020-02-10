---
title: Recommendations
seo-title: Recommendations
description: Recommendations
seo-description: null
page-status-flag: never-activated
uuid: d898fe6d-7627-405f-b2bc-b17bf1dc9e96
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: a31c5c9f-503f-4b55-8409-34d4addbd581
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# Recommendations{#recommendations}

Adobe Campaign은 트랜잭션 기반의 OLTP 데이터베이스(Transactional System)입니다. 즉, 기본 데이터베이스가 자주 업데이트되어 시간이 지남에 따라 성능이 저하됩니다. 이러한 문제를 방지하려면 정기적으로 데이터베이스를 유지 관리해야 합니다.

>[!CAUTION]
>
>데이터베이스는 정기적으로 유지되는 경우에만 최적으로 수행됩니다. 일부 RDBMS에서 제공하는 자동 유지 관리가 충분하지 않고 관계형 데이터베이스 트랜잭션 관리 시스템에서처럼 심층 유지 관리를 대체하지 않습니다.
>  
>이 문서에 설명된 절차는 권장 사항입니다. 유지 관리 계획은 데이터베이스 관리자의 책임으로서 문제가 발생할 경우 첫 번째 연락처여야 합니다.

