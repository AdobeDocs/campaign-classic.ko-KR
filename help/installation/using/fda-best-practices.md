---
solution: Campaign Classic
product: campaign
title: 캠페인 FDA 모범 사례 및 제한 사항
description: 외부 데이터베이스(FDA) 작업 시 모범 사례 및 제한 사항 학습
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 0a92ebd6c9400f8caf43da8f633c7755a3fb77ce
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 4%

---


# 모범 사례 및 제한 사항

## 임시 스키마 만들기 {#create-temporary-schemas}

FDA를 통해 그린플럼 외부 데이터베이스에 대한 몇 가지 액세스를 관리할 수 있습니다. 전용 옵션을 사용하면 외부 계정을 구성할 때 작업 스키마를 직접 만들 수 있습니다.

![](assets/fda_work_table.png)

>[!NOTE]
>
>이 옵션은 PostgreSQL Greenplum에서만 사용할 수 있습니다.

## 외부 데이터 {#optimizing-email-personalization-with-external-data}로 이메일 개인화 최적화

전용 워크플로우에서 메시지 개인화를 사전 처리할 수 있습니다. 이렇게 하려면 배달 속성의 **[!UICONTROL Analysis]** 탭에서 사용할 수 있는 **[!UICONTROL Prepare the personalization data with a workflow]** 옵션을 사용합니다.

배달 분석 중에 이 옵션은 외부 데이터베이스에 연결된 테이블의 데이터를 포함하여, 대상에 연결된 모든 데이터를 임시 테이블에 저장하는 워크플로우를 자동으로 만들고 실행합니다.

이 옵션은 개인화 단계를 실행할 때 성능을 크게 향상시킵니다.

## 워크플로 {#using-data-from-an-external-database-in-a-workflow}에서 외부 데이터베이스의 데이터 사용

여러 Adobe Campaign 워크플로우 활동에서 외부 데이터베이스에 저장된 데이터를 사용할 수 있습니다.

* **외부 데이터에 대한 필터**  -  [](../../workflow/using/targeting-data.md#selecting-data) QueryActivity를 사용하여 외부 데이터를 추가하고 정의된 필터 구성에서 사용할 수 있습니다. 자세한 정보는 이 [페이지](../../workflow/using/targeting-data.md#selecting-data)를 참조하십시오.

* **하위 세트 만들기**  -  [](../../workflow/using/split.md) 스플린타일을 사용하여 하위 세트를 만들 수 있습니다. 외부 데이터를 사용하여 사용할 필터링 기준을 정의할 수 있습니다. 자세한 정보는 이 [페이지](../../workflow/using/split.md)를 참조하십시오.

* **외부 데이터베이스**  로드 - RDBMS( [데이터 로드](../../workflow/using/data-loading--rdbms-.md) ) 활동에서 외부 데이터를 사용할 수 있습니다. [이 페이지](../../workflow/using/data-loading--rdbms-.md)에서 자세히 알아보십시오.

* **정보 및 링크**  추가  [](../../workflow/using/enrichment.md) - 추가 추가 활동 기능을 사용하면 워크플로우의 작업 테이블에 데이터를 추가하고 외부 테이블에 링크를 추가할 수 있습니다. 이 컨텍스트에서는 외부 데이터베이스의 데이터를 사용할 수 있습니다. [이 페이지](../../workflow/using/enrichment.md)에서 자세히 알아보십시오.

## FDA 제한 사항 {#limitations}

FDA 옵션은 워크플로우에서 일괄 처리 모드에서 외부 데이터베이스의 데이터를 조작하기 위해 수행됩니다. 성능 문제를 방지하기 위해 다음과 같은 일반 운영 상황에서는 FDA 모듈을 사용하지 않는 것이 좋습니다.개인화, 상호 작용, 실시간 메시징 등

Adobe Campaign과 외부 데이터베이스를 모두 최대한 사용해야 하는 작업은 피하십시오. 이렇게 하려면 다음을 수행합니다.

* Adobe Campaign 데이터베이스를 외부 데이터베이스로 내보내고 결과를 Adobe Campaign으로 다시 가져오기 전에 외부 데이터베이스에서만 작업을 실행합니다.

* 외부 Adobe Campaign 데이터베이스에서 데이터를 수집하고 작업을 로컬로 실행합니다.

외부 데이터베이스의 데이터를 사용하여 게재에서 개인화를 수행하려는 경우 워크플로우에서 사용할 데이터를 수집하여 임시 테이블에서 사용할 수 있도록 합니다. 그런 다음 임시 테이블의 데이터를 사용하여 배달을 개인화합니다.

FDA 옵션은 사용하는 외부 데이터베이스 시스템의 제한 사항을 따릅니다.

