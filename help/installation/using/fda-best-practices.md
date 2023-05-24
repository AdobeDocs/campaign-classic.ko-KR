---
product: campaign
title: Campaign FDA 모범 사례 및 제한 사항
description: 외부 데이터베이스(FDA) 작업 시 모범 사례 및 제한 사항에 대해 알아봅니다
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 7%

---

# 모범 사례 및 제한 사항



## 외부 데이터로 이메일 개인화 최적화 {#optimizing-email-personalization-with-external-data}

전용 워크플로우에서 메시지 개인화를 사전 처리할 수 있습니다. 이 작업을 수행하려면 다음을 사용하십시오. **[!UICONTROL Prepare the personalization data with a workflow]** 옵션이에서 사용할 수 있습니다. **[!UICONTROL Analysis]** 게재 속성 탭.

게재 분석 시 이 옵션은 외부 데이터베이스에 연결된 테이블의 데이터를 포함하여 대상에 연결된 모든 데이터를 임시 테이블에 저장하는 워크플로우를 자동으로 만들고 실행합니다.

이 옵션은 개인화 단계를 실행할 때 성능을 크게 향상시킵니다.

## 워크플로우에서 외부 데이터베이스의 데이터 사용 {#using-data-from-an-external-database-in-a-workflow}

여러 Adobe Campaign 워크플로우 활동에서 외부 데이터베이스에 저장된 데이터를 사용할 수 있습니다.

* **외부 데이터 필터링** - [쿼리](../../workflow/using/targeting-data.md#selecting-data) 활동을 사용하면 외부 데이터를 추가하고 정의된 필터 구성에서 사용할 수 있습니다. 자세한 정보는 이 [페이지](../../workflow/using/targeting-data.md#selecting-data)를 참조하십시오.

* **하위 집합 만들기** - [분할](../../workflow/using/split.md) 활동을 사용하면 하위 세트를 만들 수 있습니다. 외부 데이터를 사용하여 사용할 필터링 기준을 정의할 수 있습니다. 자세한 정보는 이 [페이지](../../workflow/using/split.md)를 참조하십시오.

* **외부 데이터베이스 로드** - 다음에서 외부 데이터를 사용할 수 있습니다. [데이터 로드 중](../../workflow/using/data-loading--rdbms-.md) (RDBMS) 활동. [이 페이지](../../workflow/using/data-loading--rdbms-.md)에서 자세히 알아보십시오.

* **정보 및 링크 추가** - [데이터 보강](../../workflow/using/enrichment.md) 활동을 사용하면 워크플로우의 작업 테이블에 데이터를 추가하고 외부 테이블에 대한 링크를 추가할 수 있습니다. 이 컨텍스트에서는 외부 데이터베이스의 데이터를 사용할 수 있습니다. [이 페이지](../../workflow/using/enrichment.md)에서 자세히 알아보십시오.

## FDA 제한 사항 {#limitations}

FDA 옵션은 워크플로우에서 배치 모드로 외부 데이터베이스의 데이터를 조작하기 위해 만들어집니다. 성능 문제를 방지하기 위해 개인화, 상호 작용, 실시간 메시징 등과 같은 단일 작업의 컨텍스트에서는 FDA 모듈을 사용하지 않는 것이 좋습니다.

Adobe Campaign과 외부 데이터베이스를 모두 사용해야 하는 작업을 가능한 한 피하십시오. 이렇게 하려면 다음 작업을 수행할 수 있습니다.

* Adobe Campaign 데이터베이스를 외부 데이터베이스로 내보내고 결과를 Adobe Campaign으로 다시 가져오기 전에 외부 데이터베이스에서만 작업을 실행합니다.

* 외부 Adobe Campaign 데이터베이스에서 데이터를 수집하고 작업을 로컬로 실행합니다.

외부 데이터베이스의 데이터를 사용하여 게재에서 개인화를 수행하려면 워크플로우에서 사용할 데이터를 수집하여 임시 테이블에서 사용할 수 있도록 하십시오. 그런 다음 임시 테이블의 데이터를 사용하여 게재를 개인화합니다.

FDA 옵션은 사용하는 외부 데이터베이스 시스템의 제한을 따릅니다.
