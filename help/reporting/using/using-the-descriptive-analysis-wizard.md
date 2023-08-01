---
product: campaign
title: 기술적 분석 마법사 사용
description: 기술적 분석 마법사 사용
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Reporting, Monitoring
exl-id: 848d67c7-d1dc-4eba-bcb8-672e76d8ce87
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1570'
ht-degree: 1%

---

# 기술적 분석 마법사 사용{#using-the-descriptive-analysis-wizard}



설명 분석 보고서를 만들려면 전용 마법사를 사용하십시오. 구성은 분석할 데이터와 원하는 렌더링에 따라 다릅니다.

## 데이터베이스의 데이터 분석 {#analyzing-data-in-the-database}

설명 분석 마법사는 **[!UICONTROL Tools > Descriptive analysis]** 메뉴: 이 경우, 분석은 기본적으로 수신자와 관련이 있습니다(**nms:recipient**). Adobe Campaign 데이터베이스의 모든 데이터에 적용됩니다.

![](assets/reporting_descriptive_wz_launch.png)

표준 수신자 이외의 테이블을 분석하려면(**nms:recipient**), **[!UICONTROL Advanced settings...]** 마법사의 마지막 단계에서 연결하고 설정과 일치하는 테이블을 선택합니다(이 경우). **cus:individual**:

![](assets/reporting_descriptive_other_schema.png)

데이터의 일부에 대한 통계를 만들려면 필터를 정의할 수 있습니다. 이렇게 하려면 다음을 클릭하십시오. **[!UICONTROL Advanced settings...]** 아래 표시된 대로 필터를 연결하고 정의합니다.

![](assets/reporting_descriptive_wz_filter.png)

이 분석은 16세 이상의 런던에 거주하는 데이터베이스 수신자에게만 해당됩니다.

## 데이터 세트 분석 {#analyzing-a-set-of-data}

목록, 워크플로우 전환, 하나 이상의 게재, 수신자 선택 등 다른 컨텍스트를 통해 설명 분석 마법사를 사용할 수 있습니다.

수신자 테이블을 가리키는 Adobe Campaign 트리의 여러 노드를 통해 액세스할 수 있습니다.

항목을 선택하고 마우스 오른쪽 단추를 클릭하여 설명 분석 마법사를 엽니다. 선택한 데이터만 분석됩니다.

![](assets/reporting_descriptive_from_recipients.png)

* 세트 **수신자**&#x200B;를 클릭하고 분석할 수신자를 선택한 다음 마우스 오른쪽 단추를 클릭하고 을 선택합니다. **[!UICONTROL Actions > Explore...]**, 위에 표시된 대로 필터를 수신자 목록에 적용하면 해당 콘텐츠만 분석됩니다.

  폴더 또는 현재 필터에서 모든 수신자를 선택하려면 Ctrl+A 단축키를 사용합니다. 즉, 표시되지 않은 수신자도 선택됩니다.

  수신자에 대한 설명 분석의 예는 다음을 참조하십시오. [정성적 데이터 분석](../../reporting/using/use-cases.md#qualitative-data-analysis).

* 의 맥락에서 **워크플로우**, 수신자 테이블을 가리키는 전환 위에 커서를 놓고 마우스 오른쪽 단추를 누른 다음 을 선택합니다 **[!UICONTROL Analyze target]**. 자세한 내용은 의 예를 참조하십시오. [워크플로우에서 전환 대상 분석](../../reporting/using/use-cases.md#analyzing-a-transition-target-in-a-workflow).
* 대상 **목록**&#x200B;를 클릭하고, 하나 이상의 목록을 선택한 다음 수신자와 동일한 프로세스를 적용합니다.
* 의 맥락에서 **게재**&#x200B;을(를) 클릭하고 분석할 타겟의 게재를 선택한 다음 마우스 오른쪽 단추를 클릭하고 을(를) 선택합니다 **[!UICONTROL Actions > Explore the target]**, 아래와 같이 표시됩니다.

  ![](assets/reporting_descriptive_from_deliveries.png)

  게재에 대한 설명 분석의 예는 여기에 제공됩니다. [모집단 분석](../../reporting/using/use-cases.md#analyzing-a-population) 그리고 여기: [수신자 추적 로그 분석](../../reporting/using/use-cases.md#analyzing-recipient-tracking-logs).

## 정성 배포 템플릿 구성 {#configuring-the-qualitative-distribution-template}

다음 **[!UICONTROL Qualitative distribution]** 템플릿을 사용하면 모든 유형의 데이터(예: 회사 이름, 이메일 도메인)에 대한 통계를 만들 수 있습니다.

를 통해 작성된 보고서에 사용할 수 있는 구성 옵션 **[!UICONTROL Qualitative distribution]** 템플릿은에 자세히 설명되어 있습니다. [테이블에 데이터 표시](#displaying-data-in-the-table). 전체 예는에 자세히 설명되어 있습니다. [모집단 분석](../../reporting/using/use-cases.md#analyzing-a-population).

설명 분석 마법사를 사용하여 데이터를 분석할 때 사용 가능한 옵션은 선택한 설정에 따라 다릅니다. 이러한 내용은 아래에 자세히 설명되어 있습니다.

### 데이터 빈 {#data-binning}

표시할 변수를 선택할 때 데이터 비닝을 정의할 수 있습니다. 즉, 선택한 데이터에 대한 그룹화 기준을 구성할 수 있습니다.

![](assets/s_ncs_user_report_wizard_031.png)

>[!NOTE]
>
>합계를 사용하여 계산과 관련된 필드를 계산할 때 다음을 확인합니다. **[!UICONTROL The data is already aggregated]** 성능을 개선합니다.

옵션은 필드의 내용에 따라 다릅니다.

* **[!UICONTROL None]** : 이 옵션을 사용하면 빈 없이 변수에 사용할 수 있는 모든 값을 표시할 수 있습니다.

  >[!CAUTION]
  >
  >이 옵션은 보고서 및 시스템 성능에 큰 영향을 줄 수 있으므로 주의해서 사용해야 합니다.

* **[!UICONTROL Auto]** : 이 옵션을 사용하면 가장 자주 표시되는 n개의 값을 표시할 수 있습니다. 이 숫자들은 자동으로 계산되며, 각각은 빈 수와 비교한 변수의 백분율을 나타냅니다. 숫자 값의 경우 Adobe Campaign은 데이터를 정렬할 n 클래스를 자동으로 생성합니다.
* **[!UICONTROL Manual]** : 이 옵션은 다음과 같이 작동합니다 **[!UICONTROL Auto]** 옵션을 선택할 수 있습니다. 단, 이러한 값은 수동으로 설정할 수 있습니다. 이렇게 하려면 **[!UICONTROL Add]** 값 테이블 오른쪽에 있는 단추입니다.

  개인화 전에 Adobe Campaign에서 값을 자동으로 초기화할 수 있습니다. 이렇게 하려면 생성할 빈 수를 입력하고 다음을 클릭하십시오. **[!UICONTROL Initialize with]** 링크(아래 참조):

  ![](assets/reporting_descriptive_initialize.png)

  그런 다음 필요에 따라 콘텐츠를 조정합니다.

  ![](assets/reporting_descriptive_initialize_perso.png)

  원하는 정밀도 수준에 따라 날짜가 포함된 필드를 시간, 일, 월, 연도 등으로 그룹화할 수 있습니다.

  ![](assets/reporting_descriptive_group_by_year.png)

* **[!UICONTROL Modulo]** : 숫자 값의 경우 값 그룹을 생성할 수 있습니다. 예를 들어, 값이 10인 모듈로 를 사용하면 10씩 변경되는 값의 간격을 만들 수 있습니다.

  ![](assets/reporting_descriptive_initialize_modulo.png)

  이 예에서는 연령 그룹별 수신자 분류를 볼 수 있습니다.

  ![](assets/reporting_descriptive_initialize_modulo_result.png)

### 테이블에 데이터 표시 {#displaying-data-in-the-table}

도구 모음을 사용하여 테이블의 변수 표시를 개인화할 수 있습니다. 열 삭제, 열이 아닌 행으로 데이터 표시, 열을 왼쪽 또는 오른쪽으로 이동, 값 계산 보기 또는 변경.

![](assets/s_ncs_user_report_wizard_toolbar.png)

창의 위쪽 섹션에서 디스플레이 설정을 선택할 수 있습니다.

통계의 이름과 소계를 표시하거나 숨기고 통계의 방향을 선택할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [분석 보고서 표시 설정](../../reporting/using/processing-a-report.md#analysis-report-display-settings).

### 차트에 데이터 표시 {#displaying-data-in-the-chart}

설명 분석 마법사의 첫 번째 단계에서는 표 없이 차트 양식으로만 데이터를 표시하도록 선택할 수 있습니다. 이 경우 그래픽을 구성할 때 변수 선택을 수행해야 합니다. 먼저 표시할 변수 수를 선택하고 관련 데이터베이스에서 필드를 선택해야 합니다.

![](assets/s_ncs_user_report_wizard_023.png)

그런 다음 원하는 차트 유형을 선택합니다.

![](assets/s_ncs_user_report_wizard_024.png)

>[!NOTE]
>
>차트와 테이블에 변수를 동시에 표시할 수 있습니다. 이렇게 하려면 **[!UICONTROL Table configuration]** 창. 클릭 **[!UICONTROL Next]** 차트 구성 창에서 차트 유형을 선택합니다. 하위 차원이 표에 정의되어 있으면 차트에 표시되지 않습니다.

다음을 클릭합니다. **[!UICONTROL Variants]** 차트 등록 정보를 수정하려면 링크를 클릭하십시오.

![](assets/reporting_descriptive_graphe_options.png)

제공되는 옵션은 선택한 차트의 유형에 따라 다릅니다. 자세한 정보는 [이 페이지](../../reporting/using/creating-a-chart.md#chart-types-and-variants)를 참조하십시오.

### 통계 계산 {#statistics-calculation}

설명 분석 마법사를 사용하여 데이터에 대한 여러 유형의 통계를 계산할 수 있습니다. 기본적으로 단순 개수는 하나만 구성됩니다.

클릭 **[!UICONTROL Add]** 새 통계를 만듭니다.

![](assets/reporting_descriptive_create_stat.png)

다음과 같은 작업이 가능합니다.

* **[!UICONTROL Count]** (집계 필드의) 중복 값을 포함하여 집계할 필드의 null이 아닌 모든 값을 계산하려면
* **[!UICONTROL Average]** 숫자 필드 값의 평균을 계산하려면
* **[!UICONTROL Minimum]** 숫자 필드의 최소값을 계산하려면
* **[!UICONTROL Maximum]** 숫자 필드의 최대값을 계산하려면
* **[!UICONTROL Sum]** 숫자 필드에 있는 값의 합계를 계산하려면
* **[!UICONTROL Standard deviation]** 반환된 값이 평균을 중심으로 분산되는 방식을 계산하려면
* **[!UICONTROL Row percentage distribution]** 열의 값과 행의 값의 비율을 계산하려면(테이블에만 사용 가능)
* **[!UICONTROL Column percentage distribution]** 행의 값과 열의 값의 비율을 계산하려면(테이블에만 사용 가능)
* **[!UICONTROL Total percentage distribution]** 값에 따라 관련된 수신자의 분포를 계산하려면

  ![](assets/s_ncs_user_report_wizard_026.png)

* **[!UICONTROL Calculated field]** 개인화된 연산자(테이블에만 사용 가능)를 생성합니다. 다음 **[!UICONTROL User function]** 필드에서는 데이터에 적용할 계산을 입력할 수 있습니다.

  예: 국가 및 원산지를 기준으로 고객당 평균 구매 금액 계산

  ![](assets/report_compute_data_sample1.png)

  위의 정보를 테이블에 표시하려면 고객당 평균 구매 금액을 저장하는 계산된 필드를 만들어야 합니다.

  방법은 다음과 같습니다.

   1. 구매 합계를 계산합니다.

      ![](assets/report_compute_data_sample2.png)

   1. 이 통계는 테이블에 표시되지 않습니다. 을(를) 선택 취소해야 합니다. **[!UICONTROL Display in the table]** 옵션 **[!UICONTROL Advanced]** 탭.

      ![](assets/report_compute_data_sample3.png)

   1. 새로 만들기 **[!UICONTROL Calculated field]** statistics를 입력하고 다음 공식을 입력합니다. **[!UICONTROL User function]** 필드: **@purchases/@count**.

      ![](assets/report_compute_data_sample4.png)

### 보고서 표시 {#displaying-the-report}

마법사의 마지막 단계에서는 보고서, 즉 구성된 테이블이나 차트를 표시할 수 있습니다.

보고서에 표가 있으면 계산 결과 셀에 색상이 지정됩니다. 결과가 높을수록 색상이 더 강렬해집니다.

![](assets/report_compute_data_sample1.png)

결과의 레이아웃을 변경할 수 있습니다. 이렇게 하려면 관련 변수를 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 입력을 선택합니다.

![](assets/s_ncs_user_report_wizard_029.png)

보고서에 차트가 포함되어 있으면 범례의 레이블을 사용하여 표시된 정보를 필터링할 수 있습니다. 레이블을 클릭하여 차트에 표시를 활성화/비활성화합니다.

![](assets/report_display_data_in_graph.png)

## 정량적 배포 템플릿 구성 {#configuring-the-quantitative-distribution-template}

설명 분석을 직접 생성하려면 다음을 선택합니다. **템플릿의 새로운 설명 분석** 기본적으로 설정되지 않은 경우 옵션입니다.

다음 **[!UICONTROL Quantitative distribution]** 측정 또는 카운트할 수 있는 데이터에 대한 통계를 생성할 수 있는 템플릿(예: 송장 금액, 수신자 연령).

를 통해 생성된 분석 보고서의 구성 모드 **[!UICONTROL Quantitative distribution]** 템플릿은 구현 예제에 자세히 설명되어 있습니다 [정량적 데이터 분석](../../reporting/using/use-cases.md#quantitative-data-analysis).

설명 분석 마법사를 사용하여 정량 보고서를 만들 때 사용할 수 있는 옵션은 아래에 자세히 설명되어 있습니다.

계산과 관련된 변수를 선택하여 시작합니다.

![](assets/s_ncs_user_report_wizard_017.png)

기본적으로 Adobe Campaign은 선택한 데이터에 대해 계산할 일련의 통계를 제공합니다. 필요에 따라 이 목록을 변경하거나 목록을 추가하거나 통계를 삭제할 수 있습니다.

다음과 같은 작업이 가능합니다.

* **[!UICONTROL Count]** (집계 필드의) 중복 값을 포함하여 집계할 필드의 null이 아닌 모든 값을 계산하려면
* **[!UICONTROL Average]** 숫자 필드 값의 평균을 계산하려면
* **[!UICONTROL Minimum]** 숫자 필드의 최소값을 계산하려면
* **[!UICONTROL Maximum]** 숫자 필드에 있는 값의 최대값을 계산합니다.
* **[!UICONTROL Sum]** 숫자 필드에 있는 값의 합계를 계산하려면
* **[!UICONTROL Standard deviation]** 반환된 값이 평균을 기준으로 분산되는 방식을 계산합니다.
* **[!UICONTROL Number of missing values]** 정의된 값이 없는 숫자 필드 수를 계산합니다.
* **[!UICONTROL Decile distribution]** 숫자 필드 값의 1/10을 나타내도록 반환된 값을 배포합니다.
* **[!UICONTROL Custom distribution]** 사용자 정의 임계값을 기준으로 반환된 값을 분배합니다.

  다음 **[!UICONTROL Detail...]** 버튼을 사용하면 통계를 편집하고, 필요한 경우 해당 계산 또는 표시를 개인화할 수 있습니다.

  ![](assets/s_ncs_user_report_wizard_030.png)

  마법사의 마지막 단계에 정량분석 보고서가 표시됩니다.

  ![](assets/reporting_descriptive_view_report.png)

  보고서를 변경하려면 다음을 참조하십시오 [보고서 처리](../../reporting/using/processing-a-report.md).
