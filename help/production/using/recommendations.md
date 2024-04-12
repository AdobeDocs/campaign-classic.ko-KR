---
product: campaign
title: 권장 사항
description: 권장 사항
feature: Monitoring
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 3%

---

# 권장 사항{#recommendations}



Adobe Campaign은 트랜잭션이 많은 시스템(OLTP 데이터베이스)입니다. 즉, 기본 데이터베이스가 자주 업데이트되어 시간이 지남에 따라 성능이 저하됩니다. 이러한 유형의 문제를 방지하려면 정기적인 데이터베이스 유지 관리가 필요합니다.

>[!IMPORTANT]
>
>데이터베이스는 정기적으로 유지 관리되는 경우에만 최적으로 수행됩니다. 일부 RDBMS에서 제공하는 자동 유지 보수는 모든 관계형 데이터베이스 트랜잭션 관리 시스템에서처럼 충분하지 않으며 심층 유지 관리를 대체하지 않습니다.
>  
>이 문서에 설명된 절차는 권장 사항입니다. 유지 관리 계획은 데이터베이스 관리자가 담당하며, 데이터베이스 관리자는 문제가 발생할 경우 첫 번째 담당자여야 합니다.
