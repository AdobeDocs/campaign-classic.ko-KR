---
title: 보고를 위한 모범 사례
seo-title: 보고를 위한 모범 사례
description: 보고를 위한 모범 사례
seo-description: null
page-status-flag: never-activated
uuid: 09de6a17-b3a7-4543-b672-b0a21653aa75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
discoiquuid: 904961e0-7dff-4350-8d5d-e4bdd368b3ff
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c41cf2f35495a1514642e47f0b7146d8dd50946

---


# 보고를 위한 모범 사례{#best-practices-reporting}

## 요구 사항 분석{#analyzing-needs}

보고 도구를 사용하는 것은 조정할 데이터의 볼륨, 복잡도, 설정할 보고 유형에 따라 달라집니다.

보고서의 작성, 사용 및 내구성을 최적화하려면 충족하려는 요구 사항을 자세히 살펴보아야 합니다. 이 첫 번째 분석을 통해 만들 보고서 유형과 최상의 작성 모드를 식별할 수 있습니다. 보고서를 만들려면 다음 단계를 적용합니다.

1. 요구 사항 확인

   첫 번째 단계는 필요성을 명확히 파악하는 것입니다.보고서에 표시할 내용 및 목표(모니터링, 분석, 데이터 내보내기 등)를 참조하십시오.

   Adobe Campaign은 다양한 보고 기능을 제공합니다. 가장 적합한 기능을 식별해야 하는 필요성을 분석하는 것이 중요합니다.

   예를 들어, 다음을 수행할 수 있습니다.

   * 데이터베이스의 데이터를 살펴보고 측정( [이 섹션을](../../reporting/using/about-cubes.md)통해)
   * 기존 보고서에 지표 추가( [이 섹션](../../reporting/using/about-reports-creation-in-campaign.md)참조),
   * 데이터베이스의 데이터 보기( [이 섹션을](../../reporting/using/about-descriptive-analysis.md)통해),
   * 새 배달 보고서 만들기( [이 섹션](../../reporting/using/about-reports-creation-in-campaign.md)참조),
   * Adobe Campaign 데이터베이스에서 데이터 내보내기(워크플로우를 통해 [이 섹션](../../workflow/using/about-workflows.md)참조),
   * 피벗 테이블 만들기( [이 섹션](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)참조),
   * 집계된 데이터 탐색( [이 섹션을](../../reporting/using/about-cubes.md)통해),
   * 마법사를 사용하여 데이터 분석( [이 섹션을](../../reporting/using/about-descriptive-analysis.md)통해),
   * 대량의 데이터 분석( [이 섹션](../../reporting/using/about-reports-creation-in-campaign.md)참조) 등

1. 타겟 모집단 식별

   그런 다음 만들려는 보고서가 어떤 대상을 타깃팅하는지, 어떤 공개 보고서를 볼 것인지, 보고서 표시 모드(브라우저, Adobe Campaign에서, 특정 개체, 전체 플랫폼 등에 대해)를 알아야 합니다.

   다음에 대한 보고서를 만들 수도 있습니다.

   * 모든 Adobe Campaign 운영자,
   * 마케팅 캠페인에만 액세스할 수 있는 권한을 가진 연산자,
   * 임시 사용을 위한 단일 연산자
   * 웹 액세스 등의 모든 연산자
   이러한 고려 사항은 액세스 권한 및 보안과 연결된 문제를 고려해야 합니다.

1. 컨텐츠 정의

   그런 다음 표시할 데이터 유형을 찾아야 합니다.전달 표시기, 데이터베이스 프로필에 대한 보고서 등

   또한 이 데이터의 특성(계산, 중요 사항 등으로 인한 단순, 위치, 타사 시스템의 Adobe Campaign에서), 업데이트 빈도(일별, 주별, 즉석에서)와 볼륨을 정의해야 합니다.

   특히 시간 측면에서 보고서 표시 문제를 방지하기 위해 데이터 볼륨 및 업데이트에 연결된 문제를 신중하게 검토해야 합니다. 따라서 보고서 외부의 일부 데이터를 미리 계산하기 위해 집계를 만드는 것이 좋습니다. 추적 및 배달 로그가 포함된 표에는 수백만 개의 레코드가 포함될 수 있습니다.즉, 보고서에서 사용할 워크플로우를 통해 데이터를 집계해야 합니다.

## 보고서 작성 최적화{#optimizing-report-creation}

### 데이터 볼륨 {#data-volume}

최적의 성과를 보장하려면 조작된 데이터의 양이 너무 크면 안 됩니다.

예:

* 보고서의 계산 시간은 5분을 초과할 수 없습니다.

   마찬가지로, 디자인 단계에서 적은 양의 데이터가 있는 경우, 보고서 계산이 60초를 초과하면 계산 방법을 변경해야 합니다.

* Marketing Analytics를 사용할 때 조작된 데이터는 1천만 개의 줄을 초과할 수 없습니다.

또한 밤에 집계를 계산하고 이 집계된 데이터를 보고서에서 직접 사용하는 것이 좋습니다. 이러한 집계는 전용 데이터 관리 워크플로우(SQL 쿼리)를 통해 만들어야 합니다.

또한 밤에 보고서를 계산하고 데이터베이스를 오버로드하지 않고 언제든지 볼 수 있는 내역을 자동으로 만들 수도 있습니다.

### 쿼리 {#queries}

가능하면 SQL 쿼리를 사용하고 JavaScript 사후 처리를 피하는 것이 좋습니다. 필요한 경우 워크플로우에서 스크립트 활동을 사용하고 계산에 사용되는 데이터를 삭제합니다. 또한 보관된 데이터를 사용하여 처리 시간을 단축할 수 있습니다.

이 경우 다음 구문을 사용해야 합니다.

```
if(string(ctx@_historyId)!==""))
```

보고서에 표시되는 데이터를 수집할 수 있는 쿼리는 너무 복잡하지 않아야 합니다. 특히 데이터베이스의 모든 데이터에 적용되는 경우 더욱 복잡해야 합니다. 성능을 개선하기 위해 다음 쿼리를 실행하기 전에 데이터를 필터링하는 것이 유용할 수 있습니다.즉, 계산은 데이터의 일부에만 영향을 미칩니다.

### 공연 {#performances}

위의 권장 사항을 사용하면 보고서 계산을 최적화할 수 있습니다.

이 외에도 Adobe Campaign에서는 다음 개선 사항을 권장합니다.

* 데이터 모델 연구:인덱싱된 필드는 계산 공식을 개선하기 위해 주로 사용해야 합니다.

   인덱스 필드를 빠르게 찾으려면 Adobe Campaign 인터페이스에서 열 이름을 확인합니다.필드가 인덱스되면 정렬 화살표는 빨간색으로 표시됩니다.

* 보고서가 장기적으로 유효한지 확인합니다.시간이 지남에 따라 데이터 볼륨이 크게 증가할 수 있습니다.

   마찬가지로, 테스트 단계 동안 조작된 데이터의 양은 프로덕션의 실제 데이터 볼륨과 다를 수 있습니다. 이것이 테스트 단계가 중요한 이유입니다.

   마지막으로 데이터 삭제 지연을 알고 수정해야 데이터 조작이 용이합니다.

### 보고서 내보내기 {#exporting-reports}

보고서 내보내기와 관련된 권장 사항은 [이 섹션에](../../reporting/using/actions-on-reports.md#exporting-a-report)자세히 설명되어 있습니다.
