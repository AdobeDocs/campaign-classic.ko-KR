---
product: campaign
title: 캠페인 시뮬레이션
description: Campaign 시뮬레이션 시작
role: User, Data Engineer
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: Campaigns
exl-id: 709c64a8-34bf-43fa-a820-238295fb26b8
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 2%

---

# 캠페인 시뮬레이션{#campaign-simulations}

## 시뮬레이션 정보 {#about-simulations}

캠페인 최적화를 사용하면 시뮬레이션을 사용하여 캠페인 계획의 효율성을 테스트할 수 있습니다. 이를 통해 생성된 매출, 적용된 유형화 규칙을 기반으로 한 타겟 볼륨 등 캠페인의 잠재적 성공을 측정할 수 있습니다.

시뮬레이션을 사용하면 게재의 영향을 모니터링하고 비교할 수 있습니다.

>[!NOTE]
>
>예를 들어 분산 마케팅에서 캠페인을 평가할 때 또는 임시 캘린더에 게재가 예약되지 않는 한 테스트 모드에서 준비된 게재는 서로 영향을 주지 않습니다.\
>즉, 압력 및 용량 규칙은 의 게재에만 적용됩니다. **[!UICONTROL Target estimation and message personalization]** 모드. 게재 위치 **[!UICONTROL Estimation and approval of the provisional target]** 및 **[!UICONTROL Target evaluation]** 모드는 고려되지 않습니다.\
>게재 모드는 다음에서 선택됩니다. **[!UICONTROL Typology]** 게재 속성의 하위 탭입니다.

![](assets/simu_campaign_select_delivery_mode.png)

## 시뮬레이션 설정 {#setting-up-a-simulation}

### 시뮬레이션 만들기 {#creating-a-simulation}

시뮬레이션을 만들려면 다음 단계를 적용합니다.

1. 를 엽니다. **[!UICONTROL Campaigns]** 탭을 클릭하고 **[!UICONTROL More]** 링크 포함 **[!UICONTROL Create]** 섹션을 선택하고 **[!UICONTROL Simulation]** 옵션을 선택합니다.

   ![](assets/simu_campaign_opti_01.png)

1. 템플릿과 시뮬레이션 이름을 입력합니다. 클릭 **[!UICONTROL Save]** 를 클릭하여 시뮬레이션을 만듭니다.

   ![](assets/simu_campaign_opti_02.png)

1. 다음을 클릭합니다. **[!UICONTROL Edit]** 탭 을 클릭하여 구성합니다.

   ![](assets/simu_campaign_opti_edit.png)

1. 다음에서 **[!UICONTROL Scope]** 탭에서 이 시뮬레이션에 고려할 게재를 지정합니다. 이렇게 하려면 **[!UICONTROL Add]** 버튼을 클릭하고 고려할 게재 선택 모드를 지정합니다.

   ![](assets/simu_campaign_opti_edit_scope.png)

   각 게재를 하나씩 선택하거나 캠페인, 프로그램 또는 플랜별로 정렬할 수 있습니다.

   >[!NOTE]
   >
   >플랜, 프로그램 또는 캠페인을 통해 게재를 선택하는 경우, Adobe Campaign은 시뮬레이션이 시작될 때마다 고려할 게재 목록을 자동으로 새로 고칠 수 있습니다. 이렇게 하려면 다음을 확인하십시오. **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]** 옵션을 선택합니다.
   >  
   >이렇게 하지 않으면 시뮬레이션이 생성될 때 계획, 프로그램 또는 캠페인에서 사용할 수 없는 게재는 고려되지 않습니다. 나중에 추가된 게재는 무시됩니다.

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. 시뮬레이션 범위에 포함할 요소를 선택합니다. 필요한 경우 Shift 키와 Ctrl 키를 사용하여 여러 요소를 선택합니다.

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   클릭 **[!UICONTROL Finish]** 을 눌러 선택을 승인합니다.

   선택한 게재 및 계획, 프로그램 또는 캠페인에 속하는 게재를 수동으로 결합할 수 있습니다.

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   필요한 경우 다음을 통해 동적 조건을 사용할 수 있습니다. **[!UICONTROL Edit the dynamic condition...]** 링크를 클릭합니다.

   클릭 **[!UICONTROL Save]** 을(를) 통해 이 구성을 승인할 수 있습니다.

   >[!NOTE]
   >
   >타겟이 계산된 게재만 시뮬레이션을 계산할 때 고려됩니다(상태: **대상 준비** 또는 **게재 준비 완료**).

1. 다음에서 **[!UICONTROL Calculations]** 탭에서 수신자 스키마 등의 분석 차원을 선택합니다.

   ![](assets/simu_campaign_opti_dimension.png)

1. 그런 다음 표현식을 추가할 수 있습니다.

   ![](assets/simu_campaign_opti_dimension_02.png)

### 실행 설정 {#execution-settings}

다음 **[!UICONTROL General]** 시뮬레이션의 탭에서는 실행 설정을 입력할 수 있습니다.

* 다음 **[!UICONTROL Schedule execution for down-time]** 옵션은 선택한 우선 순위 수준에 따라 덜 바쁜 기간으로 시뮬레이션 시작을 지연합니다. 시뮬레이션은 상당한 데이터베이스 리소스를 사용하므로 급하지 않은 시뮬레이션을 야간에 실행하도록 예약해야 합니다.
* 다음 **[!UICONTROL Priority]** 트리거를 지연하기 위해 시뮬레이션에 적용되는 레벨입니다.
* **[!UICONTROL Save SQL queries in the log]**. SQL 로그를 사용하면 시뮬레이션이 오류로 끝나는 경우 진단할 수 있습니다. 또한 시뮬레이션이 너무 느린 이유를 찾는 데 도움이 될 수 있습니다. 이러한 메시지는 의 시뮬레이션 후에 표시됩니다. **[!UICONTROL SQL logs]** 의 하위 탭 **[!UICONTROL Audit]** 탭.

## 시뮬레이션 실행 {#executing-a-simulation}

### 시뮬레이션 시작 {#starting-a-simulation}

시뮬레이션 범위가 정의되면 실행할 수 있습니다.

이렇게 하려면 시뮬레이션 대시보드를 열고 을 클릭합니다. **[!UICONTROL Start simulation]**.

![](assets/simu_campaign_opti_start.png)

실행이 완료되면 시뮬레이션을 열고 를 클릭합니다. **[!UICONTROL Results]** 탭으로 이동하여 각 게재에 대해 계산된 타겟을 봅니다.

![](assets/simu_campaign_opti_results.png)

1. 다음 **[!UICONTROL Deliveries]** 하위 탭에는 시뮬레이션에서 고려한 모든 게재가 나열됩니다. 여기에는 두 개의 카운트가 표시됩니다.

   * 다음 **[!UICONTROL Initial count]** 게재 시 추정 중 계산된 목표입니다.
   * 다음 **[!UICONTROL Final count]** 시뮬레이션 후 카운트된 수신자 수입니다.

     초기 카운트와 최종 카운트 간의 차이는 시뮬레이션 전에 구성된 다양한 규칙 또는 필터의 적용을 반영한다.

     이 계산에 대해 자세히 알아보려면 **[!UICONTROL Exclusions]** 하위 탭.

1. 다음 **[!UICONTROL Exclusions]** 하위 탭에서는 제외 분류를 볼 수 있습니다.

   ![](assets/simu_campaign_opti_14.png)

1. 다음 **[!UICONTROL Alerts]** 하위 탭은 시뮬레이션 중에 생성된 모든 경고 메시지를 그룹화합니다. 용량 과부하 시 경고 메시지를 보낼 수 있습니다(대상 받는 사람 수가 설정된 용량을 초과하는 경우).
1. 다음 **[!UICONTROL Exploration of the exclusions]** 하위 탭에서는 결과 분석 표를 만들 수 있습니다. 사용자는 횡축/누진 축에 변수를 표시해야 합니다.

   분석 테이블 작성의 예는 의 끝을 참조하십시오. [결과 탐색](#exploring-results).

### 결과 보기 {#viewing-results}

#### 감사 {#audit}

다음 **[!UICONTROL Audit]** 탭에서는 시뮬레이션 실행을 모니터링할 수 있습니다. 다음 **[!UICONTROL SQL Logs]** 하위 탭은 전문가 사용자에게 유용합니다. 실행 로그를 SQL 형식으로 나열합니다. 이러한 로그는 **[!UICONTROL Save SQL queries in the log]** 옵션이에서 선택됨 **[!UICONTROL General]** 시뮬레이션 실행 전 탭

![](assets/simu_campaign_opti_11.png)

#### 결과 탐색 {#exploring-results}

다음 **[!UICONTROL Exploration of the exclusions]** 하위 탭에서는 시뮬레이션의 결과를 분석할 수 있습니다.

설명 분석은에 자세히 설명되어 있습니다. [이 섹션](../../reporting/using/about-adobe-campaign-reporting-tools.md).

## 시뮬레이션 결과 {#results-of-a-simulation}

의 지표 **[!UICONTROL Log]** 및 **[!UICONTROL Results]** 탭은 시뮬레이션 결과에 대한 첫 번째 개요를 제공합니다. 결과를 더 자세히 보려면 **[!UICONTROL Reports]** 탭.

### 보고서 {#reports}

시뮬레이션 결과를 분석하려면 보고서를 편집합니다. 보고서에 제외 및 원인이 표시됩니다.

기본적으로 다음 보고서가 제공됩니다.

* **[!UICONTROL Detail of simulation exclusions]** : 이 보고서는 관련된 모든 게재에 대한 제외 원인에 대한 세부 차트를 제공합니다.
* **[!UICONTROL Simulation summary]** : 이 보고서는 다양한 게재 전반에 걸쳐 시뮬레이션에서 제외된 모집단을 보여줍니다.
* **[!UICONTROL Summary of exclusions linked to the simulation]** : 이 보고서는 적용된 유형화 규칙과 함께 시뮬레이션으로 인해 발생한 제외 차트 및 규칙당 제외 비율을 보여 주는 차트를 보여 줍니다.

>[!NOTE]
>
>새 보고서를 만들어 제공된 보고서에 추가할 수 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../reporting/using/about-adobe-campaign-reporting-tools.md)을 참조하십시오.

보고서에 액세스하려면 다음을 클릭합니다. **[!UICONTROL Reports]** 대시보드를 통한 타겟팅된 시뮬레이션의 링크입니다.

![](assets/campaign_opt_reporting_edit_from_board.png)

다음을 사용하여 보고서를 편집할 수도 있습니다. **[!UICONTROL Reports]** 시뮬레이션 대시보드에서 액세스할 수 있는 링크입니다.

### 시뮬레이션 비교 {#comparing-simulations-}

시뮬레이션이 실행될 때마다 결과는 이전 결과를 대체합니다. 한 실행의 결과를 다른 실행과 표시하거나 비교할 수 없습니다.

결과를 비교하려면 보고서를 사용해야 합니다. 실제로 Adobe Campaign을 사용하면 보고서 기록을 저장하여 나중에 다시 볼 수 있습니다. 이 기록은 시뮬레이션의 라이프사이클 동안 저장됩니다.

**예제:**

1. 유형화를 사용하는 게재에 대한 시뮬레이션 만들기 **A** 적용 대상.
1. 다음에서 **[!UICONTROL Reports]** 탭에서 사용 가능한 보고서 중 하나(예: ) 편집 **[!UICONTROL Detail of simulation exclusions]** 예.
1. 보고서의 오른쪽 위에서 아이콘을 클릭하여 새 기록을 만듭니다.

   ![](assets/campaign_opt_reporting_create_hist.png)

1. 시뮬레이션을 닫고 유형화 구성을 변경합니다. **A**.
1. 시뮬레이션을 다시 실행하고 결과를 기록이 생성된 보고서에 표시된 결과와 비교합니다.

   ![](assets/campaign_opt_reporting_edit_hist.png)

   보고서 기록을 필요한 만큼 저장할 수 있습니다.

### 보고 축 {#reporting-axes}

다음 **[!UICONTROL Calculations]** 탭에서는 대상에 대한 보고 축을 정의할 수 있습니다. 이 축은 결과 분석 중에 사용됩니다( 참조). [결과 탐색](#exploring-results)).

>[!NOTE]
>
>각 시뮬레이션에 대해 개별적으로 정의하지 않고 시뮬레이션 템플릿에서 계산 축을 정의하는 것이 좋습니다.\
>시뮬레이션 템플릿은에 저장됩니다 **[!UICONTROL Resources > Templates > Simulation templates]** Adobe Campaign 트리의 노드입니다.

**예제:**

아래 예에서는 수신자의 상태(&quot;고객&quot;, &quot;잠재 고객&quot; 또는 없음)를 기반으로 추가 보고 축을 생성하려고 합니다.

1. 보고 축을 정의하려면 다음에서 처리할 정보가 포함된 테이블을 선택합니다 **[!UICONTROL Analysis dimension]** 필드. 이 정보는 필수입니다.
1. 여기에서는 수신자 테이블의 세그먼트 필드를 선택하려고 합니다.

   ![](assets/simu_campaign_opti_09.png)

1. 다음 옵션을 사용할 수 있습니다.

   * **[!UICONTROL Generate target overlap statistics]** 시뮬레이션 보고서에서 모든 중복 통계를 복구할 수 있습니다. 중복은 하나의 시뮬레이션 내 두 개 이상의 게재에서 타겟팅된 수신자입니다.

     >[!IMPORTANT]
     >
     >이 옵션을 선택하면 시뮬레이션 실행 시간이 상당히 늘어납니다.

   * **[!UICONTROL Keep the simulation work table]** 시뮬레이션 추적을 유지할 수 있습니다.

     >[!IMPORTANT]
     >
     >이러한 테이블을 자동으로 저장하려면 상당한 저장 용량이 필요합니다. 데이터베이스가 충분히 큰지 확인하십시오.

시뮬레이션 결과가 표시되면 선택한 표현식에 대한 정보가 **[!UICONTROL Overlaps]** 하위 탭.

게재 대상 중복은 시뮬레이션의 두 개 이상의 게재에서 타겟팅된 수신자를 나타냅니다.

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>이 하위 탭은 **[!UICONTROL Generate target recovery statistics]** 옵션이 활성화되었습니다.

보고 축에 대한 정보는 다음에서 만든 제외 분석 보고서에서 처리할 수 있습니다. **[!UICONTROL Exploring exclusions]** 하위 탭. 자세한 내용은 다음을 참조하십시오. [결과 탐색](#exploring-results).
