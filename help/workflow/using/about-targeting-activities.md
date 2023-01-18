---
product: campaign
title: 타겟팅 활동 기본 정보
description: 타겟팅 활동 기본 정보
feature: Workflows, Audiences, Targeting Activity
exl-id: 5028ad4c-e427-4e78-962d-c5ea54390db5
source-git-commit: 743baa49e5d62ed1c2f7f635f6bf120a67646e63
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 3%

---

# 워크플로우에서 활동 타겟팅{#about-targeting-activities}

![](../../assets/v7-only.svg)

이러한 활동을 사용하면 세트를 정의하고 교차, 결합 또는 제외 작업을 사용하여 이러한 세트를 분할하거나 결합하여 하나 이상의 대상을 작성할 수 있습니다.

* **쿼리**: 쿼리를 실행할 수 있습니다. 을(를) 참조하십시오. [쿼리 만들기](query.md#creating-a-query).
* **증분 쿼리**: 쿼리를 수행하고 실행을 계획할 수 있습니다. 자세한 내용은 [증분 쿼리](incremental-query.md) 섹션을 참조하십시오.
* **목록 읽기**: 목록에 포함된 데이터를 사용할 수 있습니다. 자세한 내용은 [목록의 데이터 사용: 목록 읽기](../../platform/using/import-export-workflows.md#using-data-from-a-list--read-list) 섹션을 참조하십시오.
* **결합**: 여러 활동의 결과를 하나의 타겟으로 그룹화할 수 있습니다. 자세한 내용은 [결합](union.md) 섹션을 참조하십시오.
* **교차**: 동일한 인바운드 활동 결과를 사용하는 모집단만 추출할 수 있습니다. 자세한 내용은 [교차](intersection.md) 섹션을 참조하십시오.
* **제외**: 하나 이상의 다른 대상이 추출되는 기본 대상을 기반으로 대상을 만들 수 있습니다. 자세한 내용은 [제외](exclusion.md) 섹션을 참조하십시오.
* **분할**: 대상을 여러 하위 집합으로 분할할 수 있습니다. 자세한 내용은 [분할](split.md) 섹션을 참조하십시오.
* **셀**: 에서는 데이터 열 형태로 다양한 하위 세트를 볼 수 있으며, 하위 세트가 많을 경우 이러한 하위 집합을 쉽게 조작할 수 있습니다. 자세한 내용은 [셀](cells.md) 섹션을 참조하십시오.
* **셀별 오퍼**: 다른 오퍼를 모집단의 각 하위 세트에 연결할 수 있습니다. 자세한 내용은 [셀별 오퍼](offers-by-cell.md) 섹션을 참조하십시오.
* **설문 조사 답변**: 설문 조사 중에 수집된 정보를 복구할 수 있습니다. 자세한 정보는 이 [섹션](../../surveys/using/getting-started-with-surveys.md)을 참조하십시오.
* **게재 개요**: 게재 개요를 추가할 수 있습니다. 자세한 내용은 [게재 개요](../../workflow/using/delivery-outline.md) 섹션을 참조하십시오.
* **데이터 보강**: 작업 테이블 또는 워크플로우에 열을 추가할 수 있습니다. 자세한 내용은 [데이터 보강](../../workflow/using/enrichment.md) 섹션을 참조하십시오.
* **스키마 편집**: 변환, 표준화 및 필요한 경우 데이터를 보강할 수 있습니다. 자세한 내용은 [스키마 편집](../../workflow/using/edit-schema.md) 섹션을 참조하십시오.
* **오퍼 엔진**: 워크플로우에서 상호 작용 오퍼 엔진을 호출할 수 있습니다. 자세한 내용은 [오퍼 엔진](../../workflow/using/offer-engine.md) 섹션을 참조하십시오.
* **중복 제거**: 인바운드 활동에서 중복을 제거할 수 있습니다. 자세한 내용은 [중복 제거](../../workflow/using/deduplication.md) 섹션을 참조하십시오.
* **차원 변경**: 워크플로우 구성 주기 동안 타겟팅 차원을 변경할 수 있습니다. 자세한 내용은 [차원 변경](../../workflow/using/change-dimension.md) 섹션을 참조하십시오.
* **구독 서비스**: 을 사용하면 정보 서비스에 대한 target 구독 및 구독 취소를 관리할 수 있습니다. 자세한 내용은 [구독 서비스](../../workflow/using/subscription-services.md) 섹션을 참조하십시오.
* **목록 업데이트**: 목록에 인바운드 활동의 결과를 기록합니다. 자세한 내용은 [목록 업데이트](../../workflow/using/list-update.md) 섹션을 참조하십시오.
* **데이터 업데이트**: 데이터베이스의 데이터를 대량으로 업데이트할 수 있습니다. 자세한 내용은 [데이터 업데이트](../../workflow/using/update-data.md) 섹션을 참조하십시오.
* **CRM 커넥터**: Adobe Campaign과 CRM 간의 동기화를 구성할 수 있습니다. 자세한 내용은 [CRM 커넥터](../../workflow/using/crm-connector.md) 섹션을 참조하십시오.
* **[!UICONTROL Change data source]**: 워크플로우의 데이터 소스를 변경할 수 있습니다 **[!UICONTROL Working table]**. 이렇게 하면 FDA, FFDA 및 로컬 데이터베이스와 같은 다양한 데이터 소스에서 데이터를 관리할 수 있는 유연성이 높아집니다. 자세한 내용은 [CRM 커넥터](../../workflow/using/change-data-source.md) 섹션을 참조하십시오.
