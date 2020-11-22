---
solution: Campaign Classic
product: campaign
title: 캠페인 시뮬레이션
description: 캠페인 시뮬레이션
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1243'
ht-degree: 1%

---


# 캠페인 시뮬레이션{#campaign-simulations}

## 시뮬레이션 정보 {#about-simulations}

캠페인 최적화를 사용하면 시뮬레이션을 사용하여 캠페인 계획의 효율성을 테스트할 수 있습니다. 이렇게 하면 캠페인의 잠재적 성공을 측정할 수 있습니다.생성된 매출, 적용된 유형 규칙 등을 기반으로 대상 볼륨.

시뮬레이션을 사용하면 게재의 효과를 모니터링하고 비교할 수 있습니다.

>[!NOTE]
>
>테스트 모드에서 준비된 배달은 서로 영향을 주지 않습니다. 예를 들어, 분산 마케팅에서 캠페인을 평가할 때 또는 게재가 임시 달력에 예약되지 않은 경우 가능합니다.\
>즉, 압력 및 용량 규칙은 **[!UICONTROL Target estimation and message personalization]** 모드에서 배달에만 적용됩니다. 및 **[!UICONTROL Estimation and approval of the provisional target]** 의 **[!UICONTROL Target evaluation]** 배달은 고려되지 않습니다.\
>배달 속성의 하위 탭에서 배달 모드를 **[!UICONTROL Typology]** 선택합니다.

![](assets/simu_campaign_select_delivery_mode.png)

## 시뮬레이션 설정 {#setting-up-a-simulation}

### 시뮬레이션 만들기 {#creating-a-simulation}

시뮬레이션을 만들려면 다음 단계를 적용합니다.

1. 우주로 **[!UICONTROL Campaigns]** 가서 섹션 내의 **[!UICONTROL More]** 링크를 **[!UICONTROL Create]** 클릭하고 **[!UICONTROL Simulation]** 옵션을 선택합니다.

   ![](assets/simu_campaign_opti_01.png)

1. 템플릿과 시뮬레이션 이름을 입력합니다. 시뮬레이션 **[!UICONTROL Save]** 을 만들려면 을 클릭합니다.

   ![](assets/simu_campaign_opti_02.png)

1. 탭을 클릭하여 **[!UICONTROL Edit]** 구성합니다.

   ![](assets/simu_campaign_opti_edit.png)

1. 이 **[!UICONTROL Scope]** 탭에서 이 시뮬레이션에 대해 고려할 배달을 지정합니다. 이렇게 하려면 **[!UICONTROL Add]** 단추를 클릭하고 사용할 배달 선택 모드를 지정합니다.

   ![](assets/simu_campaign_opti_edit_scope.png)

   각 배달을 하나씩 선택하거나 캠페인, 프로그램 또는 계획별로 정렬할 수 있습니다.

   >[!NOTE]
   >
   >계획, 프로그램 또는 캠페인을 통해 배달을 선택하는 경우 시뮬레이션이 시작될 때마다 고려하도록 배달 목록을 자동으로 새로 고칠 수 있습니다. 이렇게 하려면 옵션을 **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]** 확인하십시오.
   >  
   >이렇게 하지 않으면 시뮬레이션이 생성될 때 계획, 프로그램 또는 캠페인에서 사용할 수 없는 게재 고려가 되지 않습니다.나중에 추가된 배달은 무시됩니다.

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. 시뮬레이션 범위에 포함할 요소를 선택합니다. 필요한 경우 Shift 및 Ctrl 키를 사용하여 여러 요소를 선택합니다.

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   Click **[!UICONTROL Finish]** to approve the selection.

   계획, 프로그램 또는 캠페인에 속하는 선택한 게재와 납품을 수동으로 결합할 수 있습니다.

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   필요한 경우 링크를 통해 동적 조건을 사용할 수 **[!UICONTROL Edit the dynamic condition...]** 있습니다.

   이 구성 **[!UICONTROL Save]** 을 승인하려면 클릭하십시오.

   >[!NOTE]
   >
   >시뮬레이션을 계산할 때 타겟이 계산된 게재만 고려됩니다(상태: **Target 준비** 또는 **전달**&#x200B;준비).

1. 탭에서 수신자 스키마와 같은 분석 차원을 **[!UICONTROL Calculations]** 선택합니다.

   ![](assets/simu_campaign_opti_dimension.png)

1. 그런 다음 표현식을 추가할 수 있습니다.

   ![](assets/simu_campaign_opti_dimension_02.png)

### 실행 설정 {#execution-settings}

시뮬레이션의 **[!UICONTROL General]** 탭에서 실행 설정을 입력할 수 있습니다.

* 이 **[!UICONTROL Schedule execution for down-time]** 옵션은 선택한 우선 순위 수준을 기준으로 시뮬레이션 실행을 덜 바쁜 기간으로 정의합니다. 시뮬레이션은 상당한 데이터베이스 리소스를 사용하므로 긴급한 시뮬레이션이 밤 시간에 실행되도록 예약해야 합니다.
* 시뮬레이션 **[!UICONTROL Priority]** 에 적용된 수준 중 트리거를 지연하는 수준입니다.
* **[!UICONTROL Save SQL queries in the log]**. SQL 로그를 사용하면 시뮬레이션이 오류로 끝나는 경우 진단할 수 있습니다. 또한 시뮬레이션이 너무 느린 이유를 알 수 있습니다. 이러한 메시지는 **[!UICONTROL SQL logs]** **[!UICONTROL Audit]** 탭의 하위 탭에서 시뮬레이션을 수행한 후에 표시됩니다.

## 시뮬레이션 실행 {#executing-a-simulation}

### 시뮬레이션 시작 {#starting-a-simulation}

시뮬레이션 범위가 정의되면 실행할 수 있습니다.

이렇게 하려면 시뮬레이션 대시보드를 열고 을 클릭합니다 **[!UICONTROL Start simulation]**.

![](assets/simu_campaign_opti_start.png)

실행이 완료되면 시뮬레이션을 열고 **[!UICONTROL Results]** 탭을 클릭하여 각 게재에 대해 계산된 대상을 봅니다.

![](assets/simu_campaign_opti_results.png)

1. 하위 **[!UICONTROL Deliveries]** 탭에는 시뮬레이션에서 고려된 모든 배달이 나열됩니다. 두 가지 사항을 보여 줍니다.

   * 배달 **[!UICONTROL Initial count]** 에서 예상 중에 계산된 목표입니다.
   * 시뮬레이션 **[!UICONTROL Final count]** 을 마친 수신자의 수입니다.

      초기 및 최종 카운트의 차이는 시뮬레이션 전에 구성된 다양한 규칙 또는 필터의 적용을 반영합니다.

      이 계산에 대해 자세히 알려면 하위 탭을 **[!UICONTROL Exclusions]** 편집합니다.

1. 하위 **[!UICONTROL Exclusions]** 탭에서는 제외 분류를 볼 수 있습니다.

   ![](assets/simu_campaign_opti_14.png)

1. 하위 **[!UICONTROL Alerts]** 탭은 시뮬레이션 중에 생성된 모든 경고 메시지를 그룹화합니다. 용량 과부하(타깃팅된 받는 사람 수가 설정된 용량을 초과하는 경우) 시 경고 메시지를 보낼 수 있습니다.
1. 하위 **[!UICONTROL Exploration of the exclusions]** 탭에서는 결과 분석 테이블을 만들 수 있습니다. 사용자는 abscissa/ordinate 축에 변수를 표시해야 합니다.

   분석 테이블 만들기의 예를 보려면 탐색 결과 [의 끝을 참조하십시오](#exploring-results).

### 결과 보기 {#viewing-results}

#### 감사 {#audit}

이 **[!UICONTROL Audit]** 탭에서는 시뮬레이션 실행을 모니터링할 수 있습니다. 하위 **[!UICONTROL SQL Logs]** 탭은 전문가 사용자에게 유용합니다. SQL 형식으로 실행 로그를 나열합니다. 이러한 로그는 시뮬레이션 실행 전 탭에서 **[!UICONTROL Save SQL queries in the log]** 옵션을 선택한 경우에만 **[!UICONTROL General]** 표시됩니다.

![](assets/simu_campaign_opti_11.png)

#### 결과 살펴보기 {#exploring-results}

하위 **[!UICONTROL Exploration of the exclusions]** 탭에서는 시뮬레이션에서 발생한 데이터를 분석할 수 있습니다.

설명 분석은 [이 섹션에 자세히 설명되어 있습니다](../../reporting/using/about-adobe-campaign-reporting-tools.md).

## 시뮬레이션 결과 {#results-of-a-simulation}

시뮬레이션 결과에 대한 첫 번째 개요 **[!UICONTROL Log]** 및 **[!UICONTROL Results]** 탭의 표시기를 제공합니다. 보다 자세한 결과 보기를 보려면 **[!UICONTROL Reports]** 탭을 엽니다.

### 보고서 {#reports}

시뮬레이션 결과를 분석하려면 보고서를 편집합니다.그들에게는 제외와 원인이 있다.

기본적으로 다음 보고서가 제공됩니다.

* **[!UICONTROL Detail of simulation exclusions]** :이 보고서는 관련된 모든 게재에 대한 제외 원인 세부 차트를 제공합니다.
* **[!UICONTROL Simulation summary]** :이 보고서는 다양한 게재에서 시뮬레이션에서 제외된 모집단을 보여줍니다.
* **[!UICONTROL Summary of exclusions linked to the simulation]** :이 보고서는 적용된 유형 규칙 및 규칙당 제외 비율을 보여주는 차트와 함께 시뮬레이션으로 인한 예외 차트를 보여줍니다.

>[!NOTE]
>
>새 보고서를 만들고 제공된 보고서에 추가할 수 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../reporting/using/about-adobe-campaign-reporting-tools.md)을 참조하십시오.

보고서에 액세스하려면 대시보드를 통해 타깃팅된 시뮬레이션의 **[!UICONTROL Reports]** 링크를 클릭합니다.

![](assets/campaign_opt_reporting_edit_from_board.png)

시뮬레이션 대시보드에서 액세스할 수 있는 **[!UICONTROL Reports]** 링크를 사용하여 보고서를 편집할 수도 있습니다.

### 시뮬레이션 비교 {#comparing-simulations-}

시뮬레이션이 실행될 때마다 이전 결과가 바뀝니다.한 실행에서 다른 실행으로 결과를 표시하고 비교할 수 없습니다.

결과를 비교하려면 보고서를 사용해야 합니다. 실제로 Adobe Campaign을 사용하면 보고서 내역을 저장하여 나중에 다시 볼 수 있습니다. 이 작업 내역은 시뮬레이션의 라이프 사이클 동안 저장됩니다.

**예제:**

1. 전달 유형에 대한 시뮬레이션을 만들어 A **가** 적용됩니다.
1. 탭 **[!UICONTROL Reports]** 에서 사용 가능한 보고서(예: **[!UICONTROL Detail of simulation exclusions]** 예:
1. 보고서의 오른쪽 상단에서 아이콘을 클릭하여 새 내역을 만듭니다.

   ![](assets/campaign_opt_reporting_create_hist.png)

1. 시뮬레이션을 닫고 유형 분류 구성 **을 변경합니다**.
1. 시뮬레이션을 다시 실행하고 내역이 생성된 보고서에 표시된 시뮬레이션과 결과를 비교합니다.

   ![](assets/campaign_opt_reporting_edit_hist.png)

   필요한 만큼 보고서 내역을 저장할 수 있습니다.

### 보고 축 {#reporting-axes}

이 **[!UICONTROL Calculations]** 탭에서는 타겟에서 보고 축을 정의할 수 있습니다. 결과 분석 중에 이 축이 [사용됩니다(결과 탐색 참조](#exploring-results)).

>[!NOTE]
>
>각 시뮬레이션에 대해 개별적으로 정의하지 않고 시뮬레이션 템플릿에서 계산 축을 정의하는 것이 좋습니다.\
>시뮬레이션 템플릿은 Adobe Campaign 트리의 **[!UICONTROL Resources > Templates > Simulation templates]** 노드에 저장됩니다.

**예제:**

아래 예에서, 수신자의 상태(&quot;고객&quot;, &quot;잠재 고객&quot; 또는 없음)를 기반으로 추가 보고 축을 만들고 싶습니다.

1. 보고 축을 정의하려면 필드에서 처리할 정보가 포함된 테이블을 **[!UICONTROL Analysis dimension]** 선택합니다. 이 정보는 필수 사항입니다.
1. 여기에서 수신자 테이블의 세그먼트 필드를 선택합니다.

   ![](assets/simu_campaign_opti_09.png)

1. 다음 옵션을 사용할 수 있습니다.

   * **[!UICONTROL Generate target overlap statistics]** 시뮬레이션 보고서에서 모든 겹침 통계를 복구할 수 있습니다. 겹치는 하나의 시뮬레이션 내에서 두 개 이상의 게재에서 받는 사람을 대상으로 합니다.

      >[!IMPORTANT]
      >
      >이 옵션을 선택하면 시뮬레이션 실행 시간이 크게 늘어납니다.

   * **[!UICONTROL Keep the simulation work table]** 시뮬레이션 추적을 유지할 수 있습니다.

      >[!IMPORTANT]
      >
      >이러한 테이블을 자동으로 저장하려면 상당한 스토리지 용량이 필요합니다.데이터베이스가 충분히 큰지 확인하십시오.

시뮬레이션 결과가 표시되면 선택한 표현식에 대한 정보가 **[!UICONTROL Overlaps]** 하위 탭에 표시됩니다.

배달 타겟이 겹치는 시뮬레이션의 두 개 이상의 배달에서 대상 받는 사람을 나타냅니다.

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>이 하위 탭은 옵션이 활성화된 경우에만 **[!UICONTROL Generate target recovery statistics]** 표시됩니다.

보고 축에 대한 정보는 하위 탭에서 생성된 제외 분석 보고서에서 처리할 수 **[!UICONTROL Exploring exclusions]** 있습니다. For more on this, refer to [Exploring results](#exploring-results).
