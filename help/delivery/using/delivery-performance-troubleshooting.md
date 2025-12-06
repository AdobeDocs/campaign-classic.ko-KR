---
product: campaign
title: 게재 성능 및 문제 해결
description: Campaign Classic v7에서 게재 성능을 최적화하고 문제를 해결하는 방법 알아보기
feature: Monitoring, Deliverability, Troubleshooting
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# 게재 성능 및 문제 해결 {#delivery-performance-troubleshooting}

>[!NOTE]
>
>게재 성능 및 모범 사례에 대한 포괄적인 지침은 [Campaign v8 게재 모범 사례](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices) 페이지에 설명되어 있습니다. 이 콘텐츠는 Campaign Classic v7 및 Campaign v8 사용자 모두에게 적용됩니다.
>
>이 페이지에서는 하이브리드 및 온-프레미스 배포의 성능 최적화 및 문제 해결을 위한 **Campaign Classic v7 관련 구성**&#x200B;에 대해 설명합니다.

게재 성능, 플랫폼 최적화, 격리 관리, 데이터베이스 유지 관리 및 예약 권장 사항에 대한 포괄적인 모범 사례는 [Campaign v8 게재 모범 사례 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}를 참조하세요.

## 성능 최적화 {#performance-optimization}

**Campaign Classic v7 하이브리드/온-프레미스 배포**&#x200B;의 경우 다음 데이터베이스 및 인프라 최적화를 통해 게재 성능을 향상시킬 수 있습니다.

### 데이터베이스 최적화

응용 프로그램에서 사용되는 SQL 쿼리의 성능을 최적화하려면 **주소를 인덱싱하십시오**. 인덱스는 데이터 스키마의 기본 요소에서 선언할 수 있습니다. 이 최적화를 사용하려면 온-프레미스 배포에서 사용할 수 있는 직접 데이터베이스 액세스 및 스키마 사용자 지정이 필요합니다.

### 인프라 조정

**대규모 게재 구성**: 백만 명 이상의 수신자에게 게재하려면 전송 큐에 공간이 있어야 합니다. 온-프레미스 설치의 경우 MTA 하위 항목을 사용자 지정 배치 크기를 처리하도록 구성할 수 있습니다. 인프라 용량에 따라 이러한 설정을 조정하려면 시스템 관리자에게 문의하십시오.

>[!NOTE]
>
>Campaign v8 Managed Cloud Services 사용자의 경우 인프라 최적화 및 MTA 구성은 Adobe에서 관리합니다. 배포에 적용할 수 있는 성능 권장 사항은 [Campaign v8 게재 모범 사례](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}를 참조하세요.

### 데이터베이스 유지 관리 {#database-maintenance}

**Campaign Classic v7 하이브리드/온-프레미스 배포**&#x200B;의 경우 플랫폼 및 데이터베이스 유지 관리가 게재 전송 성능에 직접적인 영향을 줍니다.

정기적인 유지 관리 작업은 다음과 같습니다.

**데이터베이스 정리**: 데이터베이스 정리 워크플로우를 사용하여 이전 게재 로그, 추적 데이터 및 임시 테이블을 제거합니다. 데이터베이스 유지 관리가 잘못되면 게재 준비 및 전송 속도가 느려질 수 있습니다.

**데이터베이스 성능 모니터링**: 쿼리 성능, 인덱스 단편화 및 테이블 통계를 모니터링합니다. 자세한 지침은 [이 페이지](../../production/using/database-performances.md)를 참조하세요.

**기술 워크플로우 모니터링**: 모든 기술 워크플로우(특히 정리, 추적 및 게재 기능 업데이트 워크플로우)가 오류 없이 올바르게 실행되고 있는지 확인하십시오.

>[!NOTE]
>
>Campaign v8 Managed Cloud Services 사용자의 경우 데이터베이스 유지 관리 및 기술 워크플로우는 Adobe에서 모니터링 및 관리됩니다. [Campaign v8 모니터 게재 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}에 설명된 대로 게재별 모니터링에 집중합니다.

## 게재 문제 해결 {#troubleshooting}

>[!NOTE]
>
>게재 문제 해결에 대한 포괄적인 지침은 Campaign Classic v7 및 Campaign v8 사용자 모두에게 해당되는 Campaign v8 설명서에 기재되어 있습니다.
>
>* 일반적인 배달 오류 및 솔루션: [배달 오류 이해](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* 느린 게재 진단: [Campaign UI에서 게재 모니터링](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* 게재 모범 사례: [게재 모범 사례](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>이 섹션에서는 하이브리드 및 온-프레미스 배포에 대한 **Campaign Classic v7 관련 문제 해결**&#x200B;에 대해 설명합니다.

**Campaign Classic v7 하이브리드/온-프레미스 배포**&#x200B;의 경우 다음 문제 해결 단계는 관리하는 인프라에만 해당됩니다.

### MX 규칙 구성

특정 ISP에서 전송률 조절 문제가 발생하는 경우 MX 규칙 구성을 검토하고 조정해야 할 수 있습니다. MX 규칙 및 할당량에 대한 자세한 내용은 [이 섹션](../../installation/using/email-deliverability.md#about-mx-rules)을 참조하세요.

### 게재 성능을 위한 데이터베이스 유지 관리

중간 소싱 배포에서 다음 오류가 발생하는 경우:

```
Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
```

그 원인은 마케팅 인스턴스가 데이터를 중간 소싱 서버에 보내기 전에 데이터를 작성하는 데 너무 많은 시간을 소비하는 성능 문제와 관련되어 있습니다.

**온-프레미스 설치의 경우**&#x200B;데이터베이스에 대해 진공을 수행하고 다시 인덱싱합니다. 데이터베이스 유지 관리에 대한 자세한 내용은 [이 섹션](../../production/using/recommendations.md)을 참조하세요.

또한 예약된 활동이 있는 모든 워크플로우와 실패 상태에 있는 모든 워크플로우를 다시 시작해야 합니다. [이 섹션](../../workflow/using/scheduler.md)을 참조하십시오.

### 기술 워크플로우 모니터링

온-프레미스 설치의 경우 게재 가능성과 관련된 모든 기술 워크플로우가 오류 없이 실행되고 있는지 확인합니다.

**게재 기능 업데이트 워크플로**: 바운스 메일 자격 규칙 및 게재 기능 지표를 업데이트합니다.

**추적 워크플로**: 보낸 게재에 대한 추적 데이터를 처리합니다.

**데이터베이스 정리 워크플로우**: 성능을 유지하기 위해 이전 게재 로그와 임시 테이블을 정기적으로 제거합니다.

**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**&#x200B;에서 워크플로 상태를 확인하십시오.

>[!NOTE]
>
>Campaign v8 Managed Cloud Services 사용자의 경우 기술 워크플로우 및 인프라 모니터링은 Adobe에서 관리합니다. [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}에 설명된 대로 게재 콘텐츠 및 타깃팅에 집중하십시오.

## 관련 항목

* [게재 실패 이해](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}(Campaign v8 설명서)
* [게재 모범 사례](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}(Campaign v8 설명서)
* [Campaign UI에서 게재 모니터링](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}(Campaign v8 설명서)
* [데이터베이스 유지 관리](../../production/using/recommendations.md)(v7 하이브리드/온-프레미스)
* [이메일 전달성](../../installation/using/email-deliverability.md)(v7 하이브리드/온-프레미스)
* [데이터베이스 성능](../../production/using/database-performances.md)(v7 하이브리드/온-프레미스)

