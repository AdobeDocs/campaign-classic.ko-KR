---
product: campaign
title: 데이터를 수집하여 분석
description: 데이터를 수집하여 분석
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: cf621374-88f9-4def-8bea-87e0ea69ecd3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 3%

---

# 데이터를 수집하여 분석{#collecting-data-to-analyze}

![](../../assets/common.svg)

보고서 작성에 사용할 데이터는 보고서 페이지에서 직접 선택할 수 있습니다(자세한 내용은 다음을 참조하십시오 [컨텍스트 사용](../../reporting/using/using-the-context.md)) 또는 하나 이상의 쿼리를 통해 수집됩니다.

이 활동은 다음과 같은 세 가지 다른 방법을 제공합니다.

1. 데이터베이스의 데이터를 사용하여 쿼리 작성
1. 목록에 포함된 데이터 처리
1. 기존 큐브에 포함된 데이터 사용

계산 유형, 데이터 볼륨 및 내구성 등에 따라 방법을 선택할 수 있습니다. 이러한 모든 매개 변수를 신중하게 검토하여 Adobe Campaign 데이터베이스가 오버로드되지 않도록 하고 생성된 보고서의 생성 및 조작을 최적화해야 합니다. 자세한 정보는 이 [페이지](../../reporting/using/best-practices.md#optimizing-report-creation)를 참조하십시오.

모든 경우에 데이터는 를 통해 수집됩니다 **[!UICONTROL Query]** 유형 활동.

![](assets/reporting_query_edit.png)

이 데이터 선택 모드는 데이터베이스의 데이터를 사용하여 보고서의 데이터를 수집하거나 빌드해야 하는 경우에 적합합니다. 경우에 따라 보고서에 사용된 요소에서 직접 데이터를 선택할 수도 있습니다. 예를 들어 차트를 삽입할 때 소스 데이터를 직접 선택할 수 있습니다. 자세한 내용은 [컨텍스트 사용](../../reporting/using/using-the-context.md).

## 스키마에서 데이터 사용 {#using-the-data-from-a-schema}

데이터베이스 스키마에 연결된 데이터를 사용하려면 쿼리 편집기에서 적절한 옵션을 선택하고 적용할 쿼리를 구성합니다.

다음 예제에서는 데이터베이스의 프로필 중에서 각 국가에 대한 수신자 수를 수집할 수 있습니다. 그런 다음 보고서 형식으로 표 형태로 표시할 수 있습니다.

![](assets/reporting_query_from_schema.png)

## 가져온 목록 사용 {#using-an-imported-list}

보고서를 만들려면 가져온 데이터 목록의 데이터를 사용할 수 있습니다.

이렇게 하려면 **[!UICONTROL Use an imported list]** 옵션을 선택하고 관련 목록을 선택합니다.

![](assets/reporting_query_from_list.png)

을(를) 클릭합니다. **[!UICONTROL Edit query...]** 링크를 클릭하여 보고서를 작성하기 위한 이 목록의 요소 간에 수집할 데이터를 정의합니다.

## 큐브 사용 {#using-a-cube}

쿼리를 정의할 큐브를 선택할 수 있습니다.

![](assets/reporting_query_from_cube.png)

큐브를 사용하면 최종 사용자가 보고서 및 테이블을 쉽게 구성할 수 있도록 하면서 데이터베이스의 탐색 및 분석 기능을 확장할 수 있습니다. 기존의 완전히 구성된 큐브를 선택하고 계산, 측정 단위 및 통계를 사용하면 됩니다. 큐브 만들기에 대한 자세한 내용은 [이 섹션](../../reporting/using/about-cubes.md).

을(를) 클릭합니다. **[!UICONTROL Edit query...]** 링크하고 보고서에 표시하거나 사용할 지표를 선택합니다.

![](assets/reporting_query_from_cube_edit_query.png)

## 쿼리의 필터링 옵션 {#filtering-options-in-the-queries}

전체 데이터베이스에서 쿼리를 실행하지 않으려면 데이터를 필터링해야 합니다.

### 간소화된 필터 {#simplified-filter}

을(를) 선택할 수 있습니다 **[!UICONTROL Filter automatically with the context]** 목록, 수신자 또는 게재와 같은 트리의 특정 노드를 통해 보고서에 액세스할 수 있도록 하는 옵션입니다.

다음 **[!UICONTROL Filter with the folder]** 옵션을 사용하면 폴더를 지정하고 해당 컨텐츠만 고려할 수 있습니다. 이렇게 하면 다음과 같이 트리에 있는 폴더 중 하나의 데이터만 표시하도록 보고서 데이터를 필터링할 수 있습니다.

![](assets/reporting_control_folder.png)

### 수집된 데이터 양 제한 {#limiting-the-amount-of-data-collected}

결과 제한 옵션을 사용하여 쿼리를 통해 추출할 레코드 수를 구성합니다.

* **[!UICONTROL Limit to first record]** 하나의 결과를 추출하려면
* **[!UICONTROL Size]** 레코드 집합을 추출합니다.
