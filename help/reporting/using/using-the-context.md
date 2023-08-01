---
product: campaign
title: 보고서의 컨텍스트 사용
description: 보고서에서 컨텍스트를 사용하는 방법을 알아봅니다
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Reporting, Monitoring
exl-id: a19e2843-d3f9-48c3-af72-cc1bc54f6360
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# 보고서의 컨텍스트 사용{#using-the-context}



다음과 같은 형식으로 데이터를 표시하려는 경우 **[!UICONTROL tables]** 또는 **[!UICONTROL charts]**, 새 쿼리 (참조)의 두 소스에서 가져올 수 있습니다. [데이터에 대한 직접 필터 정의](#defining-a-direct-filter-on-data)) 또는 보고서 컨텍스트( 참조: [컨텍스트 데이터 사용](#using-context-data)).

## 데이터에 대한 직접 필터 정의 {#defining-a-direct-filter-on-data}

### 데이터 필터링 {#filtering-data}

사용 **[!UICONTROL Query]** 보고서를 작성할 때 유형 활동은 필수가 아닙니다. 데이터는 보고서를 구성하는 표 및 차트에서 직접 필터링할 수 있습니다.

이렇게 하면 를 통해 보고서에 직접 표시할 데이터를 선택할 수 있습니다. **[!UICONTROL Page]** 보고서 활동.

이렇게 하려면 **[!UICONTROL Filter data...]** 링크 **[!UICONTROL Data]** 탭: 이 링크를 사용하면 표현식 편집기에 액세스하여 분석할 데이터에 대한 쿼리를 정의할 수 있습니다.

![](assets/reporting_filter_data_from_page.png)

### 예: 차트에서 필터 사용 {#example--use-a-filter-in-a-chart}

다음 예제에서는 프랑스에 거주하고 해당 연도 동안 구매한 수신자 프로필만 차트에 표시하도록 하려고 합니다.

이 필터를 정의하려면 차트에 페이지를 배치한 다음 편집합니다. 다음을 클릭합니다. **[!UICONTROL Filter data]** 표시할 데이터와 일치하는 필터를 연결하여 만듭니다. Adobe Campaign에서 쿼리 빌드에 대한 자세한 내용은 [이 섹션](../../platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

여기에서는 선택한 수신자의 도시별 분류를 표시하려고 합니다.

![](assets/reporting_graph_with_2vars.png)

렌더링은 다음과 같이 표시됩니다.

![](assets/reporting_graph_with_2vars_preview.png)

### 예: 피벗 테이블에서 필터 사용 {#example--use-a-filter-in-a-pivot-table}

이 예에서 필터를 사용하면 다른 쿼리를 미리 사용하지 않고 피벗 테이블에 파리가 아닌 고객만 표시할 수 있습니다.

다음 단계를 적용합니다.

1. 차트에 페이지를 배치한 다음 편집합니다.
1. 피벗 테이블을 만듭니다.
1. 로 이동 **[!UICONTROL Data]** 을(를) 탭하고 사용할 큐브를 선택합니다.
1. 다음을 클릭합니다. **[!UICONTROL Filter data...]** 회사 목록에서 Adobe을 제거하려면 다음 쿼리를 연결하고 정의합니다.

   ![](assets/s_ncs_advuser_report_display_03.png)

필터링 기준을 충족하는 수신자만 보고서에 표시됩니다.

![](assets/s_ncs_advuser_report_display_04.png)

## 컨텍스트 데이터 사용 {#using-context-data}

데이터를 다음과 같은 형식으로 표시 **[!UICONTROL table]** 또는 **[!UICONTROL chart]**, 데이터는 보고서 컨텍스트에서 가져올 수 있습니다.

테이블이나 차트가 포함된 페이지에서 **[!UICONTROL Data]** 탭에서는 데이터 소스를 선택할 수 있습니다.

![](assets/s_ncs_advuser_report_datasource_3.png)

* 다음 **[!UICONTROL New query]** 옵션을 사용하면 쿼리를 작성하여 데이터를 수집할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [데이터에 대한 직접 필터 정의](#defining-a-direct-filter-on-data).
* 다음 **[!UICONTROL Context data]** 옵션을 사용하면 입력 데이터를 사용할 수 있습니다. 보고서의 컨텍스트는 차트 또는 표를 포함하는 페이지의 인바운드 전환에 포함된 정보와 일치합니다. 이 컨텍스트는 예를 들어 다음을 통해 수집된 데이터를 포함할 수 있습니다. **[!UICONTROL Query]** 활동 위치: **[!UICONTROL Page]** 활동 및 보고서에서 고려해야 하는 테이블 및 필드를 지정해야 합니다.

예를 들어 쿼리 상자에서 수신자에 대해 다음 쿼리를 작성합니다.

![](assets/s_ncs_advuser_report_datasource_2.png)

그런 다음 보고서의 데이터 소스를 지정하십시오(이 경우). **[!UICONTROL Data from the context]**.

데이터 위치는 자동으로 추론됩니다. 필요한 경우 데이터 경로를 강제 적용할 수 있습니다.

![](assets/s_ncs_advuser_report_datasource_4.png)

통계가 관련된 데이터를 선택하면 사용 가능한 필드가 쿼리에 지정된 데이터와 일치합니다.

![](assets/s_ncs_advuser_report_datasource_1.png)
