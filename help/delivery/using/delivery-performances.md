---
product: campaign
title: 게재 성능 모범 사례
description: 게재 성능 및 모범 사례에 대해 자세히 알아보기
feature: Deliverability
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 3%

---

# 게재 성능 모범 사례 {#delivery-performances}

>[!NOTE]
>
>게재 성능 및 모범 사례에 대한 포괄적인 지침은 [Campaign v8 게재 모범 사례](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices) 페이지에 설명되어 있습니다. 이 콘텐츠는 Campaign Classic v7 및 Campaign v8 사용자 모두에게 적용됩니다.
>
>이 페이지는 하이브리드 및 온-프레미스 배포를 위한 **Campaign Classic v7 전용 성능 구성**&#x200B;을 설명합니다.

게재 성능, 플랫폼 최적화, 격리 관리, 데이터베이스 유지 관리 및 예약 권장 사항에 대한 포괄적인 모범 사례는 [Campaign v8 게재 모범 사례 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}를 참조하세요.

## 성능 조정 {#best-practices-performance}

**Campaign Classic v7 하이브리드/온-프레미스 배포**&#x200B;의 경우 다음 데이터베이스 및 인프라 최적화를 통해 게재 성능을 향상시킬 수 있습니다.

### 데이터베이스 최적화

응용 프로그램에서 사용되는 SQL 쿼리의 성능을 최적화하려면 **주소를 인덱싱하십시오**. 인덱스는 데이터 스키마의 기본 요소에서 선언할 수 있습니다. 이 최적화를 사용하려면 온-프레미스 배포에서 사용할 수 있는 직접 데이터베이스 액세스 및 스키마 사용자 지정이 필요합니다.

### 인프라 조정

**대규모 게재 구성**: 백만 명 이상의 수신자에게 게재하려면 전송 큐에 공간이 있어야 합니다. 온-프레미스 설치의 경우 MTA 하위 항목을 사용자 지정 배치 크기를 처리하도록 구성할 수 있습니다. 인프라 용량에 따라 이러한 설정을 조정하려면 시스템 관리자에게 문의하십시오.

>[!NOTE]
>
>Campaign v8 Managed Cloud Services 사용자의 경우 인프라 최적화 및 MTA 구성은 Adobe에서 관리합니다. 배포에 적용할 수 있는 성능 권장 사항은 [Campaign v8 게재 모범 사례](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}를 참조하세요.

## 데이터베이스 유지 관리 {#performance-issues}

**Campaign Classic v7 하이브리드/온-프레미스 배포**&#x200B;의 경우 플랫폼 및 데이터베이스 유지 관리가 게재 전송 성능에 직접적인 영향을 줍니다.

정기적인 유지 관리 작업은 다음과 같습니다.

**데이터베이스 정리**: 데이터베이스 정리 워크플로우를 사용하여 이전 게재 로그, 추적 데이터 및 임시 테이블을 제거합니다. 데이터베이스 유지 관리가 잘못되면 게재 준비 및 전송 속도가 느려질 수 있습니다.

**데이터베이스 성능 모니터링**: 쿼리 성능, 인덱스 단편화 및 테이블 통계를 모니터링합니다. 자세한 지침은 [이 페이지](../../production/using/database-performances.md)를 참조하세요.

**기술 워크플로우 모니터링**: 모든 기술 워크플로우(특히 정리, 추적 및 게재 기능 업데이트 워크플로우)가 오류 없이 올바르게 실행되고 있는지 확인하십시오.

>[!NOTE]
>
>Campaign v8 Managed Cloud Services 사용자의 경우 데이터베이스 유지 관리 및 기술 워크플로우는 Adobe에서 모니터링 및 관리됩니다. [Campaign v8 모니터 게재 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}에 설명된 대로 게재별 모니터링에 집중합니다.

## 관련 항목

* [게재 모범 사례](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}(Campaign v8 설명서)
* [게재 기능 모니터링](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}(Campaign v8 설명서)
* [게재 문제 해결](delivery-troubleshooting.md)
* [데이터베이스 성능](../../production/using/database-performances.md)(v7 하이브리드/온-프레미스)
