---
product: campaign
title: 추천
description: 추천
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---

# 추천{#recommendations}

![](../../assets/v7-only.svg)

Adobe Campaign은 트랜잭션 수준이 높은 시스템(OLTP 데이터베이스)입니다. 즉, 기본 데이터베이스가 자주 업데이트되므로 시간이 지남에 따라 성능이 저하됩니다. 이러한 유형의 문제를 방지하려면 일반 데이터베이스 유지 관리가 필요합니다.

>[!IMPORTANT]
>
>데이터베이스는 정기적으로 유지되는 경우에만 최적으로 수행됩니다. 일부 RDBMS에서 제공하는 자동 유지 관리가 충분하지 않으며 관계형 데이터베이스 트랜잭션 관리 시스템처럼 깊이 있는 유지 관리를 대체하지 않습니다.
>  
>이 문서에 설명된 절차는 권장 사항입니다. 유지 관리 계획은 데이터베이스 관리자의 책임이며 문제가 발생할 경우 첫 번째 연락처여야 합니다.
