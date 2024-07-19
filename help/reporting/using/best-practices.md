---
product: campaign
title: 보고 모범 사례
description: Campaign 보고 모범 사례
feature: Reporting, Monitoring
badge: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
exl-id: 0c7f00f3-b16d-41c5-a7b1-f5a59201bf8c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 5%

---

# 보고 우수 사례{#best-practices-reporting}



## 요구 분석{#analyzing-needs}

보고 도구를 사용하는 것은 조작할 데이터의 양, 복잡성 및 설정할 보고 유형에 따라 다릅니다.

보고서의 생성, 사용 및 내구성을 최적화하려면 충족하려는 요구 사항을 면밀히 살펴야 합니다. 이 첫 번째 분석을 통해 생성할 보고서 유형과 최상의 생성 모드를 식별할 수 있습니다. 보고서를 만들려면 다음 단계를 적용합니다.

1. 요구 사항 파악

   첫 번째 단계는 보고서에 표시하려는 내용과 목표가 무엇인지(모니터링, 분석, 데이터 내보내기 등)의 필요성을 명확하게 식별하는 것입니다.

   Adobe Campaign은 다양한 보고 기능을 제공합니다. 가장 적합한 기능을 식별해야 하는 필요성을 분석하는 것이 중요합니다.

   예를 들어 다음과 같은 작업을 수행할 수 있습니다.

   * 데이터베이스의 데이터를 탐색하고 측정을 정의합니다. [이 섹션에서](../../reporting/using/ac-cubes.md) 자세히 알아보기
   * 기존 보고서에 지표 추가. [이 섹션에서](../../reporting/using/about-reports-creation-in-campaign.md) 자세히 알아보기
   * 데이터베이스에서 데이터를 봅니다. [이 섹션에서](../../reporting/using/about-descriptive-analysis.md) 자세히 알아보기
   * 새 게재 보고서를 만듭니다. 자세히 알아보기 [이 섹션](../../reporting/using/about-reports-creation-in-campaign.md)),
   * 워크플로우를 통해 Adobe Campaign 데이터베이스에서 데이터를 내보냅니다. [이 섹션](../../workflow/using/about-workflows.md) 참조
   * 피벗 테이블을 만듭니다. [이 섹션에서](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table) 자세히 알아보기
   * 집계된 데이터를 탐색합니다. [이 섹션에서](../../reporting/using/ac-cubes.md) 자세히 알아보기
   * 마법사를 사용하여 데이터를 분석합니다. [이 섹션에서](../../reporting/using/about-descriptive-analysis.md) 자세히 알아보기
   * 대량의 데이터를 분석합니다. [이 섹션에서](../../reporting/using/about-reports-creation-in-campaign.md) 자세히 알아보기

1. 대상 모집단 식별

   그런 다음 만들려는 보고서가 대상으로 지정되는지, 이를 볼 공개의 종류와 보고서 표시 모드(브라우저, Adobe Campaign, 특정 개체, 전체 플랫폼 등)를 알아야 합니다.

   다음에 대한 보고서를 만들 수도 있습니다.

   * 모든 Adobe Campaign 연산자,
   * 마케팅 캠페인에만 액세스할 수 있는 권한이 있는 운영자
   * 임시 사용을 위한 단일 연산자,
   * 웹 액세스 등의 모든 연산자

   이러한 고려 사항은 액세스 권한 및 보안과 관련된 문제도 고려해야 합니다.

1. 콘텐츠 정의

   그런 다음 표시할 데이터 유형(게재 지표, 데이터베이스 프로필에 대한 보고서 등)을 확인해야 합니다.

   또한 이 데이터의 특성(단순, 계산 결과, 중요 등), 위치(Adobe Campaign의 경우, 서드파티 시스템), 계산 주기(매일, 매주, 즉석으로)를 정의하는 업데이트 주기 및 볼륨을 알고 있어야 합니다.

   데이터 볼륨 및 업데이트와 관련된 문제는 특히 시간 측면에서 보고서 표시 문제를 방지하기 위해 신중하게 고려해야 합니다. 따라서 보고서 외부의 일부 데이터를 미리 계산할 수 있도록 합계를 만드는 것이 좋습니다. 추적 및 게재 로그가 포함된 테이블에는 수백만 개의 레코드가 포함될 수 있습니다. 즉, 보고서에서 사용할 워크플로우를 통해 데이터를 집계해야 합니다.

## 보고서 디자인 최적화{#optimizing-report-creation}

### 데이터 볼륨 {#data-volume}

최적의 성능을 보장하려면 조작된 데이터의 양이 너무 많으면 안 됩니다.

즉,

* 보고서의 계산 시간은 5분을 초과할 수 없습니다.

  마찬가지로, 설계 단계에서 적은 양의 데이터를 사용할 때 보고서 계산이 60초를 초과하는 경우 계산 방법을 변경해야 합니다.

* Marketing Analytics 모듈을 사용할 때 보고 데이터는 1,000만 줄을 초과할 수 없습니다.

또한 야간에 합계를 계산하고 이 집계된 데이터를 보고서에서 직접 사용하는 것이 좋습니다. 이러한 집계는 전용 데이터 관리 워크플로우(SQL 쿼리)를 통해 생성해야 합니다.

또한 야간에 보고서를 계산하고 데이터베이스를 오버로드하지 않고 언제든지 볼 수 있는 기록을 자동으로 만들 수 있습니다.

### 쿼리 {#queries}

가능하면 SQL 쿼리를 사용하고 JavaScript 후처리를 피하는 것이 좋습니다. 필요한 경우 워크플로우에서 스크립트 활동을 사용하고 계산에 사용된 데이터를 삭제합니다. 보관된 데이터를 사용하여 처리 시간을 단축할 수도 있습니다.

이 경우 다음 구문을 사용해야 합니다.

```
if(string(ctx@_historyId)!==""))
```

보고서에 표시된 데이터를 수집할 수 있는 쿼리는 너무 복잡하지 않아야 합니다. 특히 데이터베이스의 모든 데이터에 적용되는 경우에는 더욱 그렇습니다. 성능을 향상시키려면 이러한 쿼리를 실행하기 전에 데이터를 필터링하는 것이 유용할 수 있습니다. 즉, 계산은 데이터의 일부만 고려합니다.

### 공연 {#performances}

위의 권장 사항을 사용하면 보고서 계산을 최적화할 수 있습니다.

이 외에도 Adobe Campaign은 다음과 같은 개선을 권장합니다.

* 데이터 모델 작업: 주로 계산 공식을 개선하는 데 인덱싱된 필드를 사용해야 합니다.

  색인화된 필드를 빠르게 찾으려면 Adobe Campaign 인터페이스에서 열 이름을 확인하십시오. 필드가 색인화된 경우 정렬 화살표는 빨간색으로 밑줄이 그어집니다.

  인덱스에 대한 자세한 내용은 [이 섹션](../../configuration/using/data-model-best-practices.md#indexes)을 참조하세요.

* 보고서 확장성이 있는지 확인하십시오. 시간이 지남에 따라 데이터 볼륨이 크게 증가할 수 있습니다.

  마찬가지로 테스트 단계 동안 조작되는 데이터의 양이 실제 운영 데이터 양과 다를 수 있습니다. 이것이 테스트 단계가 중요한 이유입니다.

  마지막으로, 데이터 제거 지연은 용이한 데이터 조작을 위해 필요할 때 알려지고 조정될 필요가 있다.

  정리 및 데이터 보존에 대한 자세한 내용은 [이 섹션](../../configuration/using/data-model-best-practices.md#data-retention)을 참조하세요.

### 보고서 내보내기 {#exporting-reports}

보고서 내보내기에 관련된 Recommendations은 [이 섹션](../../reporting/using/actions-on-reports.md#exporting-a-report)에 자세히 설명되어 있습니다.
