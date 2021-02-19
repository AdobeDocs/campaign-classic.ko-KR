---
solution: Campaign Classic
product: campaign
title: 설명 분석 마법사 사용
description: 설명 분석 마법사 사용
audience: reporting
content-type: reference
topic-tags: analyzing-populations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1558'
ht-degree: 1%

---


# 설명 분석 마법사 사용{#using-the-descriptive-analysis-wizard}

설명 분석 보고서를 만들려면 전용 마법사를 사용합니다. 구성은 분석할 데이터와 원하는 렌더링에 따라 달라집니다.

## 데이터베이스 {#analyzing-data-in-the-database}의 데이터 분석

설명 분석 마법사는 **[!UICONTROL Tools > Descriptive analysis]** 메뉴를 통해 시작할 수 있습니다.이 경우 분석은 기본적으로 수신자에게 영향을 줍니다(**nms:recipient**). Adobe Campaign 데이터베이스의 모든 데이터에 적용됩니다.

![](assets/reporting_descriptive_wz_launch.png)

표준 받는 사람 이외의 테이블을 하나(**nms:recipient**) 분석하려면 마법사의 마지막 단계에서 **[!UICONTROL Advanced settings...]** 링크를 클릭하고 설정과 일치하는 테이블을 선택합니다(이 경우 **cus:individual**).

![](assets/reporting_descriptive_other_schema.png)

데이터의 일부에 대한 통계를 만들려면 필터를 정의할 수 있습니다.이렇게 하려면 아래와 같이 **[!UICONTROL Advanced settings...]** 링크를 클릭하고 적용할 필터를 정의합니다.

![](assets/reporting_descriptive_wz_filter.png)

이 분석은 런던에서 16세 이상 그리고 살고 있는 데이타베이스 수신자에게만 영향을 줄 것이다.

## 데이터 집합 {#analyzing-a-set-of-data} 분석

다른 컨텍스트를 통해 설명 분석 마법사를 사용할 수 있습니다.목록, 워크플로우 전환, 하나 이상의 전달, 수신자 선택 등

수신자 테이블을 가리키는 Adobe Campaign 트리의 여러 노드를 통해 액세스할 수 있습니다.

항목을 선택하고 마우스 오른쪽 단추를 클릭하여 설명 분석 마법사를 엽니다. 선택한 데이터만 분석됩니다.

![](assets/reporting_descriptive_from_recipients.png)

* **받는 사람** 집합에 대해 분석할 받는 사람을 선택한 다음 마우스 오른쪽 단추를 클릭하고 위에 표시된 대로 **[!UICONTROL Actions > Explore...]**&#x200B;를 선택합니다. 필터를 받는 사람 목록에 적용하면 해당 컨텐츠만 분석됩니다.

   폴더 또는 현재 필터의 모든 받는 사람을 선택하려면 CTRL+A 단축키를 사용합니다. 즉, 표시되지 않은 받는 사람도 선택됩니다.

   받는 사람을 설명하는 분석의 예를 보려면 다음을 참조하십시오.[질적 데이터 분석](../../reporting/using/use-cases.md#qualitative-data-analysis).

* **workflow** 컨텍스트에서 수신자 테이블을 가리키는 전환 위에 커서를 놓고 마우스 오른쪽 단추를 클릭하고 **[!UICONTROL Analyze target]**&#x200B;를 선택합니다. 자세한 내용은 워크플로우](../../reporting/using/use-cases.md#analyzing-a-transition-target-in-a-workflow)에서 전환 대상 분석의 예를 참조하십시오.[
* **lists**&#x200B;에 대해 하나 이상의 목록을 선택하고 수신자와 동일한 프로세스를 적용합니다.
* **배달** 컨텍스트에서 분석할 대상이 있는 배달을 선택하고 마우스 오른쪽 단추를 클릭한 후 **[!UICONTROL Actions > Explore the target]**&#x200B;를 선택합니다(아래 참조).

   ![](assets/reporting_descriptive_from_deliveries.png)

   게재에 대한 설명 분석의 예는 다음과 같습니다.[모집단 분석](../../reporting/using/use-cases.md#analyzing-a-population) 및 다음:[수신자 추적 로그 분석 중](../../reporting/using/use-cases.md#analyzing-recipient-tracking-logs).

## 질적 배포 템플릿 구성 {#configuring-the-qualitative-distribution-template}

**[!UICONTROL Qualitative distribution]** 템플릿을 사용하면 모든 데이터 유형(예: 회사 이름, 이메일 도메인)에 대한 통계를 만들 수 있습니다.

**[!UICONTROL Qualitative distribution]** 템플릿을 통해 만든 보고서에 사용할 수 있는 구성 옵션은 [표](#displaying-data-in-the-table)에 데이터 표시를 참조하십시오. 전체 예는 [모집단 분석](../../reporting/using/use-cases.md#analyzing-a-population)에 자세히 설명되어 있습니다.

설명 분석 마법사를 사용하여 데이터를 분석할 때 사용 가능한 옵션은 선택한 설정에 따라 다릅니다. 아래에 자세히 나와 있습니다.

### 데이터 시작 {#data-binning}

표시할 변수를 선택할 때 데이터 베이닝을 정의할 수 있습니다. 즉, 선택한 데이터에 대한 그룹화 기준을 구성할 수 있습니다.

![](assets/s_ncs_user_report_wizard_031.png)

>[!NOTE]
>
>계산과 관련된 필드가 합계를 사용하여 계산되는 경우 **[!UICONTROL The data is already aggregated]**&#x200B;을 선택하여 성과를 향상시킵니다.

옵션은 필드의 내용에 따라 달라집니다.

* **[!UICONTROL None]** :이 옵션을 사용하면 베이닝 없이 변수에 사용할 수 있는 모든 값을 표시할 수 있습니다.

   >[!CAUTION]
   >
   >이 옵션은 주의해서 사용해야 합니다.보고서 및 시스템 성능에 큰 영향을 줄 수 있습니다.

* **[!UICONTROL Auto]** :이 옵션을 사용하면 가장 자주 표현되는 n개의 값을 표시할 수 있습니다. 이러한 지표는 자동으로 계산되며 각 지표는 저장소 수와 비교하여 변수의 백분율을 나타냅니다. 숫자 값의 경우 Adobe Campaign은 데이터를 정렬할 클래스를 자동으로 n개 생성합니다.
* **[!UICONTROL Manual]** :이 옵션은 이러한 값을 수동으로 설정할 수  **[!UICONTROL Auto]** 있다는 점을 제외하고 옵션과 동일하게 작동합니다. 이렇게 하려면 값 테이블 오른쪽에 있는 **[!UICONTROL Add]** 단추를 클릭합니다.

   개인화를 시작하기 전에 Adobe Campaign에서 값을 자동으로 초기화할 수 있습니다.이렇게 하려면 생성할 저장소 수를 입력하고 아래와 같이 **[!UICONTROL Initialize with]** 링크를 클릭합니다.

   ![](assets/reporting_descriptive_initialize.png)

   필요에 맞게 컨텐츠를 조정할 수 있습니다.

   ![](assets/reporting_descriptive_initialize_perso.png)

   원하는 정밀도 수준에 따라 날짜가 포함된 필드를 시간, 일, 월, 년 등으로 그룹화할 수 있습니다.

   ![](assets/reporting_descriptive_group_by_year.png)

* **[!UICONTROL Modulo]** :숫자 값의 경우 값 그룹을 만들 수 있습니다. 예를 들어 값이 10인 모듈에서는 10을 10으로 변경하는 값의 간격을 만들 수 있습니다.

   ![](assets/reporting_descriptive_initialize_modulo.png)

   이 예에서는 연령 그룹별 수신자 분류를 볼 수 있습니다.

   ![](assets/reporting_descriptive_initialize_modulo_result.png)

### {#displaying-data-in-the-table} 테이블에 데이터 표시

도구 모음을 사용하여 표의 변수 표시를 개인화합니다.열을 삭제하고, 열이 아닌 행으로 데이터를 표시하고, 열을 왼쪽이나 오른쪽으로 이동하거나, 값 계산을 보거나 변경합니다.

![](assets/s_ncs_user_report_wizard_toolbar.png)

창의 위쪽 섹션에서 디스플레이 설정을 선택할 수 있습니다.

통계 이름 및 하위 합계를 표시하거나 숨기고 통계 방향을 선택할 수 있습니다. 자세한 내용은 [분석 보고서 표시 설정](../../reporting/using/processing-a-report.md#analysis-report-display-settings)을 참조하십시오.

### {#displaying-data-in-the-chart} 차트에 데이터 표시

설명 분석 마법사의 첫 번째 단계에서 테이블 없이 차트 양식에만 데이터를 표시하도록 선택할 수 있습니다. 이 경우 그래픽을 구성할 때 변수 선택을 수행해야 합니다. 먼저 표시할 변수 수를 선택하고 관련 데이터베이스에서 필드를 선택해야 합니다.

![](assets/s_ncs_user_report_wizard_023.png)

그런 다음 원하는 차트 유형을 선택합니다.

![](assets/s_ncs_user_report_wizard_024.png)

>[!NOTE]
>
>차트와 표에 변수를 동시에 표시할 수 있습니다. 이렇게 하려면 **[!UICONTROL Table configuration]** 창에 변수를 입력합니다. **[!UICONTROL Next]**&#x200B;을 클릭하고 차트 구성 창에서 차트 유형을 선택합니다. 하위 차원이 테이블에 정의된 경우 차트에 표시되지 않습니다.

차트 속성을 수정하려면 **[!UICONTROL Variants]** 링크를 클릭합니다.

![](assets/reporting_descriptive_graphe_options.png)

제공된 옵션은 선택한 차트 유형에 따라 다릅니다. 자세한 정보는 [이 페이지](../../reporting/using/creating-a-chart.md#chart-types-and-variants)를 참조하십시오.

### 통계 계산 {#statistics-calculation}

설명 분석 마법사를 사용하면 데이터에 대한 여러 유형의 통계를 계산할 수 있습니다. 기본적으로 하나의 간단한 카운트만 구성됩니다.

**[!UICONTROL Add]**&#x200B;을 클릭하여 새 통계를 만듭니다.

![](assets/reporting_descriptive_create_stat.png)

다음 작업을 수행할 수 있습니다.

* **[!UICONTROL Count]** 합계 필드의 중복 값(합계 필드)을 포함하여, 계산할 필드의 null이 아닌 모든 값을 카운트하려면
* **[!UICONTROL Average]** 숫자 필드에서 값의 평균을 계산하려면
* **[!UICONTROL Minimum]** 숫자 필드에서 값의 최소값을 계산하려면
* **[!UICONTROL Maximum]** 숫자 필드에 있는 값의 최대값을 계산하려면
* **[!UICONTROL Sum]** 숫자 필드에 있는 값의 합을 계산하려면
* **[!UICONTROL Standard deviation]** 반환된 값이 평균을 기준으로 어떻게 분산되는지 계산하려면
* **[!UICONTROL Row percentage distribution]** 열의 값 비율과 행의 값 비율을 계산하려면(테이블에만 사용 가능)
* **[!UICONTROL Column percentage distribution]** 행의 값 대 열 값 비율([테이블 전용]에만 사용 가능)
* **[!UICONTROL Total percentage distribution]** 값을 기준으로 받는 사람의 배포를 계산하려면

   ![](assets/s_ncs_user_report_wizard_026.png)

* **[!UICONTROL Calculated field]** 를 클릭하여 개인화된 연산자를 만듭니다(테이블에만 사용 가능). **[!UICONTROL User function]** 필드에서 데이터에 적용할 계산을 입력할 수 있습니다.

   예:국가 및 출처를 기준으로 고객당 평균 구매 금액 계산

   ![](assets/report_compute_data_sample1.png)

   위 정보를 표에 표시하려면 고객당 평균 구매 금액을 저장하기 위한 계산된 필드를 만들어야 합니다.

   방법은 다음과 같습니다.

   1. 구매 합계를 계산합니다.

      ![](assets/report_compute_data_sample2.png)

   1. 이 통계가 테이블에 표시되지 않습니다. **[!UICONTROL Advanced]** 탭의 **[!UICONTROL Display in the table]** 옵션의 선택을 취소해야 합니다.

      ![](assets/report_compute_data_sample3.png)

   1. 새 **[!UICONTROL Calculated field]** 유형 통계를 만들고 **[!UICONTROL User function]** 필드에 다음 공식을 입력합니다.**@purchases/@count**.

      ![](assets/report_compute_data_sample4.png)

### 보고서 {#displaying-the-report} 표시

마법사의 마지막 단계에서는 보고서(예: 구성된 표 또는 차트)를 표시할 수 있습니다.

보고서에 표가 포함되어 있으면 계산 결과 셀에 색상이 지정됩니다. 결과가 높을수록 색상이 더 강렬해집니다.

![](assets/report_compute_data_sample1.png)

결과 레이아웃을 변경할 수 있습니다. 이렇게 하려면 관련 변수를 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 입력을 선택합니다.

![](assets/s_ncs_user_report_wizard_029.png)

보고서에 차트가 포함되어 있는 경우 범례의 레이블을 사용하여 표시된 정보를 필터링할 수 있습니다.차트를 활성화/비활성화하려면 레이블을 클릭합니다.

![](assets/report_display_data_in_graph.png)

## 수량 배포 템플릿 {#configuring-the-quantitative-distribution-template} 구성

설명 분석을 직접 생성하려면 템플릿&#x200B;**옵션이 기본적으로 설정되어 있지 않으면**&#x200B;새 설명 분석 옵션을 선택합니다.

측정하거나 계산할 수 있는 데이터(예: 송장 금액, 수신자의 연령)에 대한 통계를 생성할 수 있는 **[!UICONTROL Quantitative distribution]** 템플릿.

**[!UICONTROL Quantitative distribution]** 템플릿을 통해 만든 분석 보고서의 구성 모드는 구현 예 [수량 데이터 분석](../../reporting/using/use-cases.md#quantitative-data-analysis)에 자세히 설명되어 있습니다.

설명 분석 마법사를 사용하여 수량 보고서를 만들 때 사용할 수 있는 옵션은 아래에 자세히 설명되어 있습니다.

계산에서 중요한 변수를 선택하여 시작합니다.

![](assets/s_ncs_user_report_wizard_017.png)

기본적으로 Adobe Campaign은 선택한 데이터에 대해 계산될 일련의 통계를 제공합니다. 필요에 따라 이 목록을 변경하거나, 목록에 추가하거나, 통계를 삭제할 수 있습니다.

다음 작업을 수행할 수 있습니다.

* **[!UICONTROL Count]** 합계 필드의 중복 값(합계 필드)을 포함하여, 계산할 필드의 null이 아닌 모든 값을 카운트하려면
* **[!UICONTROL Average]** 숫자 필드에서 값의 평균을 계산하려면
* **[!UICONTROL Minimum]** 숫자 필드에서 값의 최소값을 계산하려면
* **[!UICONTROL Maximum]** 숫자 필드에 있는 값의 최대값을 계산하기 위해.
* **[!UICONTROL Sum]** 숫자 필드에 있는 값의 합을 계산하려면
* **[!UICONTROL Standard deviation]** 반환된 값이 평균을 기준으로 어떻게 배포되는지 계산하기 위해.
* **[!UICONTROL Number of missing values]** 을 클릭하여 정의된 값이 없는 숫자 필드 수를 계산합니다.
* **[!UICONTROL Decile distribution]** 반환되는 값을 배포하려면 각 값이 숫자 필드에 있는 값의 1/10을 나타내도록 하십시오.
* **[!UICONTROL Custom distribution]** 사용자 정의 임계값을 기반으로 반환된 값을 배포하려면.

   **[!UICONTROL Detail...]** 단추를 사용하여 통계를 편집하고 필요한 경우 계산 또는 표시를 개인화할 수 있습니다.

   ![](assets/s_ncs_user_report_wizard_030.png)

   마법사의 마지막 단계는 양적 분석 보고서를 보여줍니다.

   ![](assets/reporting_descriptive_view_report.png)

   보고서를 변경하려면 [보고서 처리](../../reporting/using/processing-a-report.md)를 참조하십시오.

