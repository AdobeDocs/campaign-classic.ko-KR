---
product: campaign
title: 마케팅 캠페인 만들기
description: 마케팅 캠페인을 만들고 실행하는 방법 알아보기
role: User
feature: Campaigns, Cross Channel Orchestration, Programs
hide: true
hidefromtoc: true
exl-id: a8fce21f-ffe3-4819-87ca-ac0ad9f21e41
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 5%

---

# 마케팅 캠페인 시작{#setting-up-marketing-campaigns}

캠페인에는 작업(게재) 및 프로세스(파일 가져오기 또는 추출)와 리소스(마케팅 문서, 게재 아웃라인)가 포함됩니다. 마케팅 캠페인에서 사용됩니다. 캠페인은 프로그램의 일부이며 프로그램은 캠페인 플랜에 포함됩니다.

![](assets/do-not-localize/how-to-video.png) 마케팅 계획, 프로그램 및 캠페인을 만드는 방법을 알아봅니다. [비디오에서](#video)

마케팅 캠페인을 만들려면 다음 작업을 수행하십시오.

1. 캠페인 만들기: 캠페인 및 레이블, 유형, 시작 및 종료 날짜, 예산, 관련 리소스, 관리자 및 참여자와 같은 특성을 살펴봅니다. [자세히 알아보기](#creating-a-campaign).

1. 대상 모집단 정의: 타깃팅 쿼리가 있는 워크플로우를 만듭니다. [자세히 알아보기](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population).

1. 게재 만들기: 채널을 선택하고 전송할 콘텐츠를 정의합니다. [자세히 알아보기](../../campaign/using/marketing-campaign-deliveries.md#creating-deliveries).

1. 게재를 승인합니다. [자세히 알아보기](../../campaign/using/marketing-campaign-approval.md).

1. 게재 모니터링. [자세히 알아보기](../../campaign/using/marketing-campaign-monitoring.md).

1. 캠페인 및 관련 비용 계획 [자세히 알아보기](../../campaign/using/providers-stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

이 단계를 완료하면 게재를 시작하고([이 섹션](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery) 참조) 게재와 관련된 데이터, 프로세스 및 정보를 확인하고 필요한 경우 관련 문서를 관리할 수 있습니다([이 섹션](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents) 참조). 캠페인 및 게재의 처리 단계 실행을 추적할 수도 있습니다([이 섹션](../../campaign/using/marketing-campaign-monitoring.md) 참조).

## 계획 및 프로그램 계층 만들기 {#creating-plan-and-program-hierarchy}

마케팅 계획 및 프로그램에 대한 폴더 계층을 구성하려면 다음을 수행합니다.

1. 홈 페이지에서 **탐색기** 아이콘을 클릭합니다.
1. 계획을 생성할 폴더를 마우스 오른쪽 단추로 누릅니다.
1. **새 폴더 추가 > 캠페인 관리 > 플랜**&#x200B;을 선택합니다.

   ![](assets/create_plan_1.png)

1. 플랜 이름을 변경합니다.
1. 새로 만든 계획을 마우스 오른쪽 단추로 클릭하고 **속성...**&#x200B;을 선택합니다.

   ![](assets/create_plan_2.png)

1. **일반** 탭에서 **내부 이름**&#x200B;을(를) 수정하여 패키지를 내보내는 동안 중복되지 않도록 합니다.
1. **저장**&#x200B;을 클릭합니다.
1. 새로 만든 계획을 마우스 오른쪽 단추로 클릭하고 **새 &#39;프로그램&#39; 폴더 만들기**&#x200B;를 선택합니다.
1. 위의 단계를 반복하여 새 프로그램 폴더와 해당 내부 이름의 이름을 변경합니다.

## 캠페인 만들기 {#creating-a-campaign}

### 캠페인 추가 {#adding-a-campaign}

캠페인 목록을 통해 캠페인을 만들 수 있습니다. 이 보기를 표시하려면 **[!UICONTROL Campaigns]** 대시보드에서 **[!UICONTROL Campaigns]** 메뉴를 선택하십시오.

![](assets/s_ncs_user_add_an_op_from_list.png)

**[!UICONTROL Program]** 필드를 사용하면 캠페인을 연결할 프로그램을 선택할 수 있습니다. 이 정보는 필수입니다.

![](assets/s_ncs_user_new_op_wz_a.png)

프로그램을 통해 캠페인을 만들 수도 있습니다. 이렇게 하려면 관련 프로그램의 **[!UICONTROL Schedule]** 탭에서 **[!UICONTROL Add]** 단추를 클릭하십시오.

![](assets/s_ncs_user_add_an_op.png)

프로그램의 **[!UICONTROL Schedule]** 탭을 통해 캠페인을 만들면 해당 캠페인이 관련 프로그램에 자동으로 연결됩니다. 이 경우 **[!UICONTROL Program]** 필드가 숨겨집니다.

캠페인 생성 창에서 캠페인 템플릿을 선택하고 캠페인에 대한 이름 및 설명을 추가합니다. 캠페인 시작 및 종료 날짜를 지정할 수도 있습니다.

캠페인을 만들려면 **[!UICONTROL OK]**&#x200B;을(를) 클릭하십시오. 프로그램 일정에 추가됩니다.

![](assets/s_ncs_user_program_planning_with_op.png)

>[!NOTE]
>
>표시할 캠페인을 필터링하려면 **[!UICONTROL Filter]** 링크를 클릭하고 표시할 캠페인의 상태를 선택하십시오.

![](assets/s_ncs_user_program_planning_filter.png)

### 캠페인 편집 및 구성 {#editing-and-configuring-a-campaign}

그런 다음 방금 만든 캠페인을 편집하고 해당 매개 변수를 정의할 수 있습니다.

캠페인을 열고 구성하려면 일정에서 선택한 다음 **[!UICONTROL Open]**&#x200B;을(를) 클릭합니다.

![](assets/s_ncs_user_new_op_edit.png)

이렇게 하면 캠페인 대시보드로 이동합니다.

## 반복 및 정기 캠페인 {#recurring-and-periodic-campaigns}

반복 캠페인은 연결된 일정에 따라 워크플로우를 실행하도록 구성된 특정 템플릿을 기반으로 하는 캠페인입니다. 따라서 워크플로우는 캠페인 내에서 반복됩니다. 타겟팅은 각 실행에 대해 복제되며, 다양한 프로세스 및 타겟 모집단을 추적합니다. 또한 대상 예상 값을 사용하여 시뮬레이션을 시작할 수 있도록 자동 워크플로우 만들기 동안 적용 범위를 통해 향후 타깃팅을 미리 실행할 수 있습니다.

정기 캠페인은 템플릿의 실행 일정에 따라 자동으로 생성되는 캠페인입니다.

### 반복 캠페인 만들기 {#creating-a-recurring-campaign}

반복 캠페인은 실행할 워크플로우 템플릿 및 실행 일정을 정의하는 특정 템플릿에서 만들어집니다.

#### 반복 캠페인용 템플릿 만들기 {#creating-the-campaign-template}

1. **[!UICONTROL Recurring]** 캠페인 템플릿을 만듭니다.

   >[!NOTE]
   >
   >빈 템플릿을 만드는 대신 기본 템플릿을 복제하는 것이 좋습니다.

   ![](assets/s_ncs_user_op_template_recur_tab.png)

1. 템플릿 이름과 캠페인 기간을 입력합니다.

   ![](assets/s_ncs_user_op_template_recur_duplicate.png)

1. 이 유형의 캠페인에는 템플릿 실행 일정을 만들기 위해 **[!UICONTROL Schedule]** 탭이 추가됩니다.

이 탭에서 이 템플릿을 기반으로 캠페인의 계획된 실행 날짜를 지정합니다.

![](assets/s_ncs_user_op_template_recur_planning.png)

실행 예약의 구성 모드가 워크플로의 **[!UICONTROL Scheduler]** 개체와 일치합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/architecture.md)을 참조하십시오.

>[!IMPORTANT]
>
>데이터베이스를 오버로드할 수 없도록 실행 일정 구성을 신중하게 수행해야 합니다. 반복 캠페인은 지정된 일정에 따라 템플릿의 워크플로우를 복제합니다. 지나치게 빈번한 워크플로우 생성을 구현하면 데이터베이스 작업이 방해될 수 있습니다.

1. 표시된 기간 동안 해당 워크플로우를 만들려면 **[!UICONTROL Create in advance for]** 필드에 값을 지정하십시오.
1. 타겟팅 매개 변수 및 하나 이상의 일반 게재와 함께 이 템플릿을 기반으로 캠페인에 사용할 워크플로우 템플릿을 만듭니다.

   >[!NOTE]
   >
   >이 워크플로는 반복 워크플로 템플릿으로 저장해야 합니다. 이렇게 하려면 워크플로 속성을 편집하고 **[!UICONTROL Execution]** 탭에서 **[!UICONTROL Recurring workflow template]** 옵션을 선택합니다.

   ![](assets/s_ncs_user_op_template_recur_wf_option.png)

#### 반복 캠페인 만들기 {#create-the-recurring-campaign}

반복 캠페인을 만들고 템플릿에 정의된 일정에 따라 워크플로우를 실행하려면 다음 절차를 적용합니다.

1. 반복 캠페인 템플릿을 기반으로 새 캠페인을 만듭니다.
1. 워크플로우 실행 일정을 입력합니다.

   ![](assets/s_ncs_user_op_recur_planning.png)

1. 캠페인 일정을 사용하면 각 라인에 대해 자동 워크플로우 생성 또는 실행 시작 날짜를 입력할 수 있습니다.

   각 행에 대해 다음과 같은 추가 옵션을 추가할 수 있습니다.

   * **[!UICONTROL To be approved]** : 워크플로우에서 게재 승인 요청을 강제 적용할 수 있습니다.
   * **[!UICONTROL To be started]** : 시작 날짜에 도달하면 워크플로를 시작할 수 있도록 해줍니다.

   **[!UICONTROL Create in advance for]** 필드를 사용하면 입력한 기간을 다루는 모든 워크플로를 만들 수 있습니다.

   **[!UICONTROL Jobs on campaigns]** 워크플로우를 실행하면 캠페인 일정에 정의된 발생 횟수를 기반으로 전용 워크플로우가 만들어집니다. 따라서 워크플로우는 각 실행 날짜에 대해 생성됩니다.

1. 반복 워크플로우는 캠페인에 있는 워크플로 템플릿에서 자동으로 만들어집니다. 캠페인의 **[!UICONTROL Targeting and workflows]** 탭에 표시됩니다.

   ![](assets/s_ncs_user_op_recur_planning_wfs.png)

   반복 워크플로우 인스턴스의 레이블은 템플릿 레이블과 워크플로우 번호로 구성되며 # 문자는 그 사이에 있습니다.

   일정에서 만든 워크플로는 **[!UICONTROL Schedule]** 탭의 **[!UICONTROL Workflow]** 열에서 워크플로와 자동으로 연결됩니다.

   ![](assets/s_ncs_user_op_recur_planning_wfs_1.png)

   이 탭에서 각 워크플로우를 편집할 수 있습니다.

   ![](assets/s_ncs_user_op_recur_planning_wf_edit.png)

   >[!NOTE]
   >
   >워크플로우와 연관된 일정 라인의 시작 일자는 다음 구문과 함께 워크플로우의 변수에서 사용할 수 있습니다.\
   >`$date(instance/vars/@startPlanningDate)`

### 정기 캠페인 만들기 {#creating-a-periodic-campaign}

정기 캠페인은 실행 일정에 따라 캠페인 인스턴스를 만들 수 있는 특정 템플릿을 기반으로 하는 캠페인입니다. 캠페인 인스턴스는 템플릿 일정에 정의된 빈도에 따라 정기 캠페인 템플릿을 기반으로 자동으로 생성됩니다.

#### 캠페인 템플릿 만들기 {#creating-the-campaign-template-1}

1. 기존 캠페인 템플릿을 복제하여 **[!UICONTROL Periodic]** 캠페인 템플릿을 만듭니다.

   ![](assets/s_ncs_user_op_template_period_create.png)

1. 템플릿의 속성을 입력합니다.

   >[!NOTE]
   >
   >템플릿이 할당된 운영자는 선택한 프로그램에서 캠페인을 만들 수 있는 적절한 권한이 있어야 합니다.

1. 이 템플릿과 연결된 워크플로우를 만듭니다. 템플릿에서 만든 모든 정기 캠페인에서 복제됩니다.

   ![](assets/s_ncs_user_op_template_period_wf.png)

   >[!NOTE]
   >
   >이 워크플로는 워크플로 템플릿입니다. 캠페인 템플릿에서 실행할 수 없습니다.

1. 반복 캠페인 템플릿에 대한 실행 일정을 완료합니다. **[!UICONTROL Add]** 단추를 클릭하고 시작 및 종료 날짜를 정의하거나 링크를 통해 실행 일정을 채웁니다.

   ![](assets/s_ncs_user_op_template_period_planning_add.png)

   >[!IMPORTANT]
   >
   >정기 캠페인 템플릿은 위에 정의된 일정에 따라 새 캠페인을 만듭니다. 따라서 Adobe Campaign 데이터베이스를 오버로드할 수 없도록 신중하게 완료해야 합니다.

1. 실행 시작 날짜에 도달하면 일치하는 캠페인이 자동으로 만들어집니다. 템플릿의 모든 특성을 사용합니다.

   각 캠페인은 템플릿 일정을 통해 편집할 수 있습니다.

   ![](assets/s_ncs_user_op_template_period_planning.png)

각 정기 캠페인에는 동일한 요소가 포함되어 있습니다. 생성되면 표준 캠페인으로 관리됩니다.

## 튜토리얼 비디오 {#video}

이 비디오에서는 마케팅 계획, 프로그램 및 캠페인을 만드는 방법을 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/35132?quality=12)

추가 캠페인 사용 방법 비디오를 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.
