---
solution: Campaign Classic
product: campaign
title: 외부 데이터베이스 액세스
description: 외부 데이터베이스의 데이터에 액세스하고 처리하는 방법 살펴보기
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 3%

---


# 통합 데이터 액세스 시작하기 {#about-federated-data-access}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

## 사전 요구 사항 {#operating-principle}

FDA 옵션을 사용하면 데이터 모델을 서드파티 데이터베이스로 확장할 수 있습니다. 타깃팅된 테이블의 구조를 자동으로 감지하고 SQL 소스의 데이터를 사용합니다.

이 기능을 사용하려면 사전 요구 사항이 아래에 나열되어 있습니다.

* **구성**:snowflake을 제외하고 통합 데이터 액세스를 설정하려면 **온-프레미스** 또는 **하이브리드** 호스팅 모델이 필요합니다. [자세히 알아보기](../../installation/using/hosting-models.md)
* **외부 데이터베이스 버전**:adobe campaign FDA 모듈과 호환되는 외부 데이터베이스가 필요합니다. 데이터베이스 시스템 및 호환 버전 목록은 캠페인 [호환성 매트릭스에 자세히 설명되어 있습니다](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
* **권한**:또한 사용자는 Adobe Campaign 및 외부 데이터베이스에 [필요한 권한을](../../installation/using/remote-database-access-rights.md) 가지고 있어야 합니다.

## 제한 사항 {#limitations}

FDA 옵션은 워크플로우의 일괄 처리 모드에서 외부 데이터베이스의 데이터를 조작하기 위해 수행됩니다. 성능 문제를 방지하려면 다음과 같은 비군사적인 작업 환경에서 FDA 모듈을 사용하지 않는 것이 좋습니다.개인화, 상호 작용, 실시간 메시징 등

Adobe Campaign과 외부 데이터베이스를 모두 최대한 사용해야 하는 작업은 피하십시오. 이렇게 하려면 다음을 수행할 수 있습니다.

* 결과를 Adobe Campaign으로 다시 가져오기 전에 Adobe Campaign 데이터베이스를 외부 데이터베이스로 내보내고 외부 데이터베이스에서만 작업을 실행합니다.

* 외부 Adobe Campaign 데이터베이스에서 데이터를 수집하고 작업을 로컬로 실행합니다.

외부 데이터베이스의 데이터를 사용하여 게재에서 개인화를 수행하려는 경우 워크플로우에서 사용할 데이터를 수집하여 임시 테이블에서 사용할 수 있도록 합니다. 그런 다음 임시 테이블의 데이터를 사용하여 배달을 개인화합니다.

FDA 옵션은 사용하는 외부 데이터베이스 시스템의 제한 사항을 따릅니다.

## 추천 {#recommendations}

### 임시 스키마 만들기 {#create-temporary-schemas}

FDA를 통해 Greenplum 외부 데이터베이스에 대한 몇 가지 액세스를 관리할 수 있습니다. 전용 옵션을 사용하면 외부 계정을 구성할 때 작업 스키마를 직접 만들 수 있습니다.

![](assets/fda_work_table.png)

>[!NOTE]
>
>이 옵션은 PostgreSQL Greenplum에서만 사용할 수 있습니다.

### 외부 데이터로 이메일 개인화 최적화 {#optimizing-email-personalization-with-external-data}

전용 워크플로우에서 메시지 개인화를 사전에 처리할 수 있습니다. 이렇게 하려면 배달 속성의 탭 **[!UICONTROL Prepare the personalization data with a workflow]** 에서 사용할 수 있는 **[!UICONTROL Analysis]** 옵션을 사용합니다.

배달 분석 중에 이 옵션은 대상에 연결된 모든 데이터를 외부 데이터베이스에 연결된 테이블의 데이터를 포함하여 임시 테이블에 저장하는 워크플로우를 자동으로 만들고 실행합니다.

이 옵션은 개인화 단계를 실행할 때 성능을 크게 향상시킵니다.

### Use data from an external database in a workflow {#using-data-from-an-external-database-in-a-workflow}

여러 Adobe Campaign 워크플로우 활동에서 외부 데이터베이스에 저장된 데이터를 사용할 수 있습니다.

* **외부 데이터** 필터 - [쿼리](../../workflow/using/targeting-data.md#selecting-data) 활동을 사용하면 외부 데이터를 추가하고 정의된 필터 구성에서 사용할 수 있습니다. 자세한 정보는 이 [페이지](../../workflow/using/targeting-data.md#selecting-data)를 참조하십시오.

* **하위 세트 만들기** - [분할](../../workflow/using/split.md) 활동을 통해 하위 세트를 만들 수 있습니다. 외부 데이터를 사용하여 사용할 필터링 기준을 정의할 수 있습니다. 자세한 정보는 이 [페이지](../../workflow/using/split.md)를 참조하십시오.

* **외부 데이터베이스** 로드 - RDBMS( [데이터 로드](../../workflow/using/data-loading--rdbms-.md) ) 활동에서 외부 데이터를 사용할 수 있습니다. 자세한 내용은 [이 페이지를 참조하십시오](../../workflow/using/data-loading--rdbms-.md).

* **정보 및 링크** 추가 - [데이터](../../workflow/using/enrichment.md) 농축활동기능을 사용하면 워크플로우의 작업 테이블에 데이터를 추가하고 외부 테이블에 링크를 추가할 수 있습니다. 이 컨텍스트에서는 외부 데이터베이스의 데이터를 사용할 수 있습니다. 자세한 내용은 [이 페이지를 참조하십시오](../../workflow/using/enrichment.md).
