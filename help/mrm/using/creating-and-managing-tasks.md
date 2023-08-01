---
product: campaign
title: 작업 만들기 및 관리
description: 작업 만들기 및 관리
feature: Resource Management
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
exl-id: cc1200fa-f6d8-4f41-aed1-d1a7f229447a
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '3736'
ht-degree: 0%

---

# 작업 만들기 및 관리{#creating-and-managing-tasks}



Adobe Campaign을 사용하면 작업을 만들고 애플리케이션에서 작업의 전체 주기를 직접 관리할 수 있습니다. 프로그램 및 캠페인 구현은 Adobe Campaign 운영자 또는 외부 서비스 공급자에게 할당된 작업으로 분류할 수 있습니다. 이 작업 모드를 사용하면 모든 프로그램 참여자와 외부 참여자를 포함하는 개방형 공동 작업 환경을 만들 수 있습니다.

작업 목록 또는 캠페인 대시보드에서 작업을 만들고, 보고, 모니터링할 수 있습니다. 마케팅 계획, 프로그램 및 캠페인의 일정에서 보고 추적할 수도 있습니다.

작업은 캠페인에 첨부되며 종속성, 즉 연결된 작업을 가질 수 있습니다. 각 작업에는 상태, 우선 순위, 예상 로드 및 관련 비용이 있습니다.

모든 작업은 목록을 통해 액세스할 수 있는 목록으로 그룹화됩니다. **캠페인** 탭. 자세한 내용은 다음을 참조하십시오. [작업 액세스](#accessing-tasks).

이들은 자신이 속한 프로그램의 일정에 표시될 수 있다.

![](assets/d_ncs_user_tasks_in_planning.png)

## 작업 액세스 {#accessing-tasks}

### 작업 표시 {#displaying-tasks}

작업은 를 통해 액세스할 수 있는 작업 목록에 표시됩니다. **[!UICONTROL Campaigns]** 탭.

![](assets/s_ncs_user_task_edit_view.png)

연결된 연산자의 모든 작업을 볼 수 있습니다.

자세한 내용은 다음을 참조하십시오. [작업 실행 상태](#execution-status-of-a-task) 및 [작업 진행 상태](#progress-status-of-a-task).

### 작업 필터링 {#filtering-tasks}

이 보기를 표시하면 이 보기만 표시되도록 자동으로 필터링됩니다 **[!UICONTROL operator tasks]**. 창의 위쪽 섹션에 있는 필드를 사용하여 작업을 필터링할 수도 있습니다.

![](assets/s_ncs_user_task_filter_from_view.png)

### 작업 편집 {#editing-tasks}

편집할 작업을 클릭합니다.

![](assets/s_ncs_user_task_edit_from_view.png)

## 새 작업 만들기 {#creating-a-new-task}

작업을 만들려면 **[!UICONTROL Tasks]** 링크 **[!UICONTROL Campaigns]** 탭하고 선택 **[!UICONTROL Create]**.

![](assets/s_ncs_user_task_create_new.png)

최소한 작업 이름을 입력하고 연결된 캠페인을 선택하십시오. 시작 및 종료 날짜도 지정해야 합니다. 이 세 가지 정보는 필수입니다.

클릭 **[!UICONTROL Save]** 을 눌러 작업을 생성합니다.

![](assets/s_ncs_user_task_create_simple.png)

캠페인의 대시보드를 통해 작업을 생성할 수도 있습니다. 이 경우 작업이 생성된 캠페인에 자동으로 연결됩니다.

![](assets/s_ncs_user_task_create_new_from_op.png)

작업이 생성되면 캠페인 일정 및 작업 목록에 추가됩니다. 작업을 편집하려면 일정에서 해당 작업을 선택하거나 작업 개요에서 해당 이름을 클릭하고 **[!UICONTROL Open]** 링크를 클릭합니다.

![](assets/s_ncs_user_task_edit_simple.png)

이를 구성하려면 다음을 표시해야 합니다.

* 관리자 및 참여자: 을 참조하십시오. [관리자 및 참가자](#manager-and-participants).
* 생성 일정: 다음을 참조하십시오. [실행 일정](#execution-schedule).
* 약정된 비용: 다음을 참조하십시오. [경비 및 수익](#expenses-and-revenues).

검토자를 추가할 수도 있습니다(참조). [검토자](#reviewers)) 및 참조된 문서(참조: [참조된 문서](#documents-referenced)).

작업 수명 주기는에 나와 있습니다. [라이프 사이클](#life-cycle).

### 관리자 및 참가자 {#manager-and-participants}

업무를 담당하는 운영자에게만 이를 종결할 수 있는 권한이 부여된다.

기본적으로 Adobe Campaign 연산자가 작업을 만들면 이 작업이 자동으로 할당됩니다. 다른 연산자를 선택하려면 **[!UICONTROL Assigned to]** 필드.

![](assets/s_ncs_user_task_edit_simple_general_tab.png)

>[!NOTE]
>
>운영자 관리 는에 표시됩니다. [이 섹션](../../platform/using/access-management.md).

작업을 수행하는 데 관련된 연산자를 지정할 수 있습니다. 이 운영자는 작업을 닫을 수 있는 권한이 없습니다. 자신에게 할당된 작업만 승인할 수 있습니다.

다음을 사용하여 선택됩니다. **[!UICONTROL Resources]** 아이콘을 클릭합니다. 클릭 **[!UICONTROL Add]** 관련 연산자를 선택합니다.

![](assets/s_ncs_user_task_add_resources.png)

클릭 **[!UICONTROL Ok]** 사용률을 입력합니다. 작업 실행 기간 동안 운영자에게 할당된 부하를 나타냅니다. 이 비율은 표시 전용이며 백분율로 표시됩니다.

예를 들어 실행 일정이 10일로 설정된 작업의 경우 사용률이 50%인 운영자는 10일 동안 작업 시간의 절반 동안 이 작업에 동원됩니다.

각 연산자에 대해 스케줄링된 작업 로드 및 실제 작업 로드를 입력할 수 있습니다. 이 기간은 또한 정보 용도로만 사용됩니다.

종료 날짜 이전에 작업에 관련된 모든 운영자에게 자동으로 전송되는 미리 알림을 구성할 수 있습니다.

다음을 통해 Adobe Campaign 운영자 프로필을 볼 수 있습니다. **[!UICONTROL Edit link]** 아이콘.

![](assets/s_ncs_user_task_edit_resource_profile.png)

연산자 대시보드를 사용하면 작업 로드(진행 중인 다른 작업)를 확인할 수 있습니다.

![](assets/s_ncs_user_task_edit_resource_planning.png)

### 검토자 {#reviewers}

참여자 외에 담당자에 의해 작업이 종료된 후 해당 작업을 검토할 운영자를 정의할 수 있습니다. 이렇게 하려면 **[!UICONTROL Enable task approval]** 왼쪽 아래 섹션에 있는 옵션 **[!UICONTROL Resources]** 창. 개별 연산자, 연산자 그룹 또는 연산자 목록일 수 있습니다.

![](assets/s_ncs_user_task_edit_resource_validation.png)

연산자 목록을 지정하려면 **[!UICONTROL Edit...]** 첫 번째 검토자의 오른쪽에 있는 링크로 이동하여 아래와 같이 필요한 만큼 연산자를 추가합니다.

![](assets/s_ncs_user_task_edit_resource_operators.png)

검토자 구성 창의 아래 섹션에서 작업에 대한 승인 일정을 정의할 수 있습니다. 기본적으로 검토자는 작업을 승인하기 위해 제출 날짜로부터 3일을 받습니다. 관련 운영자에게 승인 기한 전에 자동으로 전송되는 미리 알림을 구성할 수 있습니다.

![](assets/s_ncs_user_edit_op_valid_calendar.png)

이미 다른 사업자에게 이를 수행하도록 할당한 경우에도 업무 담당자는 자신에게 이를 승인하는 업무를 할당할 수 있다. 정의된 검토자가 없는 경우 알림이 작업 담당자에게 전송됩니다. 이 있는 기타 모든 Adobe Campaign 연산자 **[!UICONTROL Administrator]** 권한은 작업을 승인할 수도 있습니다. 하지만 알림은 수신되지 않습니다.

### 참조된 문서 {#documents-referenced}

작업에 문서 및 마케팅 리소스를 추가할 수 있습니다(자세한 내용은 다음을 참조하십시오.) [마케팅 리소스 관리](../../mrm/using/managing-marketing-resources.md)). 이렇게 하려면 작업을 열고 다음을 클릭합니다. **[!UICONTROL Documents]** 아이콘을 클릭합니다.

클릭 **[!UICONTROL Add]** 작업에 추가할 문서를 선택합니다. 마케팅 리소스에 동일한 프로세스를 적용합니다.

![](assets/s_ncs_user_task_edit_documents.png)

참조된 문서는 작업 대시보드뿐만 아니라 작업과 관련된 운영자에게 전송되는 알림에도 표시됩니다.

![](assets/s_ncs_user_task_notification_documents.png)

### 실행 일정 {#execution-schedule}

작업의 유효 기간은 다음에 표시됩니다. **[!UICONTROL Start]** 및 **[!UICONTROL End]** 필드. 스케줄된 부하는 해당 기간 동안 수행될 작업량을 표현한다. 일 또는 시간 단위로 표시됩니다.

>[!NOTE]
>
>임무의 라이프 사이클은에 나와 있습니다. [라이프 사이클](#life-cycle).

다음 **[!UICONTROL Workload performed]** 또한 일 및 시간 단위로 표시되는 필드를 사용하면 예약된 작업 로드와 관련하여 작업의 진행 상황을 수동으로 업데이트할 수 있습니다.

![](assets/s_ncs_user_task_percentage_done_enter.png)

다음 **[!UICONTROL Progress status]** 작업 중 백분율로 표시된 작업은 관련 운영자가 수행한 작업에 따라 자동으로 업데이트됩니다. 수동으로 입력할 수 있습니다.

이 정보는 작업 대시보드에서 볼 수 있습니다.

![](assets/s_ncs_user_task_percentage_done_from_dashboard.png)

캠페인 탭에도 표시됩니다.

![](assets/s_ncs_user_task_percentage_done_from_op.png)

작업 실행 일정 종료 날짜에 도달했지만 작업이 완료되지 않은 경우 작업이 다음과 같이 수행됩니다. **[!UICONTROL Late]**. 경고 운영자에게 경고 메시지도 표시됩니다.

자세한 내용은 다음을 참조하십시오. [작업 진행 상태](#progress-status-of-a-task).

### 경비 및 수익 {#expenses-and-revenues}

각 태스크에 대해 관련 비용을 정의하고 수익을 예측할 수 있습니다. 작업이 첨부된 캠페인에 대해 계산된 다음 통합됩니다.

이 정보를 지정하려면 **[!UICONTROL Expenses and revenue]** 아이콘을 클릭합니다.

![](assets/s_ncs_user_task_edit_costs.png)

기본적으로 부과된 예산은 작업이 첨부된 캠페인의 예산입니다. 작업 세부 정보에 표시됩니다.

>[!NOTE]
>
>비용 및 예산에 대한 자세한 내용은 [비용 약정, 계산 및 과금](../../mrm/using/controlling-costs.md#cost-commitment--calculation-and-charging).

이 창에서는 도달할 목표를 정의할 수도 있습니다. 목표는 해당 작업의 예측 매출로 표시됩니다.

### 서비스 공급자 {#service-providers}

외부 서비스 공급자는 작업 관리에 관여할 수 있습니다.

이렇게 하려면 작업 속성을 편집하고 관련 서비스 공급자를 선택합니다. 서비스 제공자와 연관된 비용 범주가 창의 중앙 섹션에 자동으로 나열됩니다.

자세한 내용은 다음을 참조하십시오. [서비스 공급자 및 해당 비용 범주 만들기](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories).

작업 실행과 관련된 비용 범주를 선택합니다. 이를 위해 비용 유형을 선택하고 필요한 경우 추가 비용에 금액을 추가합니다.

![](assets/s_ncs_user_task_edit_simple_costs_tab.png)

>[!NOTE]
>
>예산 및 비용 관리 방법은에 나와 있습니다. [비용 제어](../../mrm/using/controlling-costs.md).

서비스 공급자를 선택하면 작업 대시보드에 표시됩니다.

![](assets/s_ncs_user_task_supplier_view.png)

### 지연된 작업 {#late-tasks}

상태가 변경되지 않은 상태로 작업이 종료 날짜에 도달하면 늦습니다. **[!UICONTROL Finished]**. 작업이 지연되면 기본적으로 어떤 연산자도 경고되지 않습니다. 알림 이메일의 전달을 구성할 수 있습니다. 모든 운영자는 작업에 참여하지 않더라도 알림을 받을 수 있습니다.

로 이동 **[!UICONTROL Resources]** 상자를 선택하고 연산자를 **[!UICONTROL Assignation]** 필드. 여러 사람에게 알리려면 연산자 그룹을 선택합니다.

![](assets/mrm_task_alert_if_late.png)

### 초기 알림 {#initial-notifications}

시작일이 미래인 작업을 만들거나 수정할 때, Adobe Campaign에서는 작업 담당자에게 이메일을 보내어 시작일을 알려 준다고 제안합니다.

![](assets/mrm_task_first_notif.png)

그러나 만들고 있는 작업이 오래 걸리는 경우에는 작업이 시작되기 전에 알림을 보내도록 예약하는 것이 좋습니다. 예를 들어 한 달 후에 작업이 시작되면 작업이 시작되기 1주일 전에 담당자에게 알릴 수 있습니다.

알림을 예약하려면 **[!UICONTROL Resources]** 상자 및 사용 **[!UICONTROL Initial notification]** 필드.

![](assets/mrm_task_alert_before.png)

* 캠페인 내의 작업에 대해 특정 날짜 및 시간을 선택합니다.
* 캠페인 템플릿 내의 작업의 경우, 알림 시간은 작업이 시작되기 전까지 남은 시간으로 표시됩니다(예:에 2d를 입력하는 경우) **[!UICONTROL Initial notification]** 이 필드에서는 작업 시작 2일 전에 이메일을 전송합니다.

알림을 예약한 경우 작업을 저장하면 Adobe Campaign에서 알림을 즉시 전송할 오퍼를 중지합니다. 전송하기로 결정할 수 있으며, 이렇게 하면 예약된 알림이 대체되지 않습니다.

### 프로그램에 연결된 작업 {#task-linked-to-a-program}

특정 캠페인(예: 프로그램 내에서 예정된 캠페인의 테마를 논의하는 회의)이 아닌 전체 조직과 관련된 작업을 관리하기 위해 프로그램에서 직접 작업을 만들 수 있습니다. 작업이 프로그램 일정에 나타납니다.

프로그램에 직접 연결된 작업을 만들려면 다음 작업을 수행하십시오.

1. 프로그램 일정을 엽니다. 홈페이지에서 **[!UICONTROL Campaigns > Browse > Other choices > Programs]**. 창의 오른쪽 섹션에 전체 프로그램 일정이 열립니다.
1. 일정에서 원하는 프로그램을 클릭합니다. 창에 프로그램이 표시됩니다.
1. 이 창에서 다음을 클릭합니다. **[!UICONTROL Open]**. 프로그램 일정이 열립니다.
1. 다음을 클릭합니다. **[!UICONTROL Add]** 오른쪽의 일정 위에 있는 단추를 클릭한 다음 **[!UICONTROL Add a task]**.

![](assets/mrm_task_create_from_prg.png)

### 운영자 가용성 {#operator-availability}

작업 대시보드에서 운영자 이름 옆에 있는 아이콘은 작업이 적용되는 기간 동안 다른 작업 또는 이벤트에서 이미 작업 중임을 나타냅니다. 운영자가 담당하거나 참여하는 작업이 **[!UICONTROL Assigned to]** 필드 또는 작업 **[!UICONTROL Resources]** 상자.

![](assets/mrm_task_alert_operator_busy.png)

### 워크플로우의 작업 {#task-in-a-workflow}

사용 **[!UICONTROL Task]** campaign 워크플로우의 요소를 사용하면 작업 승인 여부에 따라 두 가지 시나리오를 정의할 수 있습니다.

![](assets/mrm_task_in_workflow.png)

캠페인 워크플로우에서 **[!UICONTROL Task]** 활동은 다음에서 찾을 수 있습니다. **[!UICONTROL Flow control]** 탭.

## 작업 유형 {#types-of-task}

캠페인을 통해 작업을 만들 때 특정 작업을 만들 수 있습니다. 선택한 템플릿에 작업 유형이 정의되어 있습니다.

![](assets/s_ncs_user_task_select_template.png)

다음 작업을 예약할 수 있습니다.

* [작업 제어](#control-tasks),
* [그룹화 작업](#grouping-task),
* [그룹화 작업](#grouping-task),
* [알림 작업](#notification-task).

>[!NOTE]
>
>**[!UICONTROL Control task]** 및 **[!UICONTROL Grouping]** 작업을 만들 수 있습니다. **전용** campaign 대시보드를 통해\
>지정된 연산자의 작업 맵에 표시됩니다. 다음을 참조하십시오 [작업 액세스](#accessing-tasks).

### 작업 제어 {#control-tasks}

A **[!UICONTROL Control task]** 게재 승인(타기팅, 콘텐츠, 추출 파일, 예산 또는 증명 승인)에 연결됩니다.

![](assets/s_ncs_user_task_new_control.png)

작업이 생성되면 캠페인 대시보드에 작업이 추가됩니다.

![](assets/s_ncs_user_task_edit_from_board.png)

그런 다음 편집하고 매개 변수를 지정할 수 있습니다.

### 마케팅 리소스 만들기 작업 {#marketing-resource-creation-task}

마케팅 리소스 만들기 작업은 마케팅 리소스의 만들기 및 게시를 관리하는 데 사용할 수 있습니다. 리소스 자체가 아니라 작업을 통해 리소스를 관리하는 경우 다음을 수행할 수 있습니다.

* 캠페인을 통해 리소스 만들기 프로세스를 제어합니다.
* 일정에서 리소스 만들기 프로세스를 봅니다.
* 리소스 만들기 프로세스(미리 알림, 알림)를 관리합니다.
* 리소스 만들기에 연결된 비용을 계산하고 제어합니다.
* 작업을 통해 리소스를 승인하고 게시합니다(관련 옵션이 활성화된 경우).

#### 작업과 연결된 리소스 간의 상호 작용 {#interaction-between-the-task-and-its-linked-resource}

마케팅 리소스 만들기 작업은 연결된 리소스와 상호 작용합니다. 이것은 다음을 의미합니다.

* 리소스 만들기 일정 및 연결된 비용은 작업을 통해 관리됩니다.
* 운영자는 일반(다운로드 또는 업로드, 잠금 및 잠금 해제)과 같은 리소스 작업을 할 수 있습니다. 이는 작업에 영향을 주지 않습니다.
* 다음 작업을 통해 리소스 승인 및 게시를 수행할 수 있습니다. **[!UICONTROL Publish the marketing resource]** 옵션이 활성화되어 있으면 리소스가 승인되고 작업이 완료되면 자동으로 게시됩니다. 옵션이 활성화되지 않은 경우 작업과 리소스는 상호 작용하지 않습니다. 한 작업에 대해 동작해도 다른 작업에 영향을 주지 않습니다.

  일련의 연결된 작업을 사용하여 전체 승인 주기를 정의할 수 있습니다. 다음 확인: **[!UICONTROL Publish the marketing resource]** 마지막 작업에 대한 옵션만: 리소스를 게시하려면 모든 작업을 완료해야 합니다. 또한 하위 마케팅 리소스 작업을 만들면 하위 작업에서 리소스가 자동으로 선택됩니다.

   * **리소스를 통해**: 승인을 위해 리소스를 제출하거나 승인하는 경우 이러한 작업은 작업에 영향을 주지 않습니다.
   * **작업을 통해**: 다음 경우 **[!UICONTROL Publish the marketing resource]** 작업에서 옵션이 선택되어 있으면 리소스가 승인되고 작업이 완료되면 자동으로 게시됩니다(위 참조). 이 옵션을 선택하지 않으면 작업과 리소스가 상호 작용하지 않습니다. 한 작업에 대해 작업을 수행해도 다른 작업에는 영향을 주지 않습니다.

#### 마케팅 리소스 만들기 작업 구성 {#configuring-a-marketing-resource-creation-task}

작업을 검토하는 사람은 리소스에 정의된 콘텐츠를 검토하는 사람과 같지 않습니다. 그러나 **[!UICONTROL Publish the marketing resource]** 옵션이 선택되어 있으면(아래 참조) 작업을 완료하면 자동으로 리소스가 승인되므로(또는 검토자가 정의되지 않은 경우 작업 관리자) 작업 검토자는 리소스 콘텐츠를 승인할 권한이 있습니다.

![](assets/mrm_task_asset_creation.png)

다음에서 **[!UICONTROL Marketing resource]** 필드에서 이 작업을 통해 관리할 리소스를 정의합니다. 다음을 수행할 수 있습니다.

* 기존 리소스를 선택합니다. 드롭다운 목록에는 상태의 모든 리소스가 표시됩니다. **[!UICONTROL Being edited]**.
* 리소스 만들기: **[!UICONTROL Select the link]** 아이콘을 클릭한 다음 **[!UICONTROL Create]** 아이콘.

다음 **[!UICONTROL Publish the marketing resource]** 옵션을 사용하면 리소스 게시를 자동화할 수 있습니다. 작업이 완료되면 **[!UICONTROL Finished]**, 리소스의 상태가 자동으로 다음으로 전환됨 **[!UICONTROL Published]**, 승인을 위해 제출되지 않았거나 승인되지 않았더라도, 작업을 완료하는 검토자가 리소스에 정의된 콘텐츠 검토자가 아닌 경우 등이 포함됩니다.

다음 **[!UICONTROL Publish the resource]** 단추를 사용할 수 있고 리소스 게시 검토자는 게시 준비가 되었음을 알리는 알림 이메일을 수신합니다. 다음에서 **[!UICONTROL Edit > Tracking]** 탭, 검토 및 작업 검토자에 의한 게시가 표시됩니다. 리소스 사후 처리 워크플로우가 정의된 경우 이제 실행됩니다.

![](assets/mrm_resource_audit_tab.png)

### 그룹 작업 {#grouping-task}

다음 **[!UICONTROL Grouping task]** 작업 유형을 사용하면 여러 작업을 그룹화하고 진행 상황 관리 및 승인을 동기화할 수 있습니다.

그룹화 작업에 연결된 경비 또는 리소스가 없습니다.

그룹화 작업으로 그룹화된 모든 작업은 자체 대시보드에서 볼 수 있습니다. 원하는 작업 목록만 표시하도록 작업 목록을 필터링할 수 있습니다.

그룹화 작업에는 그룹화된 작업을 쉽게 만들 수 있는 링크가 있습니다.

그룹화 작업을 기반으로 그룹화된 작업을 만들려면 캠페인 대시보드로 이동하여 그룹화 작업의 이름을 클릭하여 해당 설명을 표시한 다음 을 클릭합니다 **[!UICONTROL Add a task]**.

![](assets/mrm_task_grouped_create.png)

하지만 그룹화 작업에 연결할 작업을 이미 만든 경우에는 **[!UICONTROL Linked to]** 필드 **[!UICONTROL Properties]** 상자.

![](assets/s_ncs_user_task_group_with.png)

### 알림 작업 {#notification-task}

알림 작업을 사용하면 (운영자, 운영자 그룹, 서비스 공급자 등) 이메일 게재를 예약할 수 있습니다. 이를 통해 캠페인이 곧 완료됨을 누군가에게 알리거나, 운영자가 준비할 수 있도록 캠페인이 시작되기 전에 문서를 보내기 위한 미리 알림을 예약할 수 있습니다. 즉, 캠페인이나 프로그램 내의 커뮤니케이션을 추적하고 수행된 작업을 자세히 볼 수 있습니다.

#### 라이프 사이클 {#life-cycle}

알림 작업은 승인이 필요하지 않습니다. 즉, 라이프 사이클이 표준 작업보다 간단합니다.

![](assets/mrm_task_notif_lifecycle.png)

알림 작업에는 다음과 같은 상태가 있을 수 있습니다.

* **[!UICONTROL Scheduled]** 이메일이 전송될 때까지
* **[!UICONTROL In progress]** 이메일을 보낸 후 종료 날짜에 도달할 때까지
* **[!UICONTROL Finished]** 종료 날짜에 도달하면.

#### 구성 {#configuration}

![](assets/mrm_task_notif_dashboard.png)

만드는 동안 작업에 다음 요소를 입력해야 합니다.

* **[!UICONTROL Assigned to]** : 이메일을 받을 운영자 또는 운영자 그룹. 이메일을 보낸 후 작업을 다시 할당하면 새 운영자에게 이메일이 전송되지 않습니다(이렇게 하려면 작업을 다시 초기화하고 시작 날짜를 변경해야 함).
* **작업 시작일**: 알림 이메일을 전송할 날짜입니다. 이 날짜는 작업 기록 시 미래여야 합니다.
* **작업 종료일**: 작업 상태가 변경되는 날짜 **[!UICONTROL Finished]**. 기본적으로 종료 날짜는 시작 날짜와 동일합니다. 그러나 작업에 기간을 할당하면 필요한 경우 운영자가 일정에서 수행해야 하는 시간을 상징할 수 있습니다.
* **[!UICONTROL Description]** : 여기에 입력한 텍스트가 알림 이메일의 본문에 표시됩니다.

  ![](assets/mrm_task_notif_dashboard_msg.png)

작업 및 알림 이메일에 첨부 파일을 추가할 수 있습니다. 이렇게 하려면 **[!UICONTROL Documents]** 아이콘 을 클릭하여 오른쪽 상단의 도구 모음에 액세스합니다.

## 라이프 사이클 {#life-cycle-1}

### 작업 간 링크 {#links-between-tasks}

다음 **[!UICONTROL Properties]** 각 작업의 버튼을 사용하면 캠페인에서 작업 간의 링크를 정의할 수 있습니다. 그룹화 작업을 사용하여 작업을 하위 작업으로 분할할 수 있습니다( 참조) [연결된 작업](#linked-tasks)) 또는 작업 간의 종속성을 정의합니다( 참조). [그룹화 작업](#grouping-tasks)).

#### 연결된 작업 {#linked-tasks}

사용 **[!UICONTROL Linked task]** 그룹화 작업과 작업을 연결하는 필드입니다. 다음을 참조하십시오 [작업 유형](#types-of-task).

다음 예에서는 타겟팅 승인이 네 개의 하위 작업으로 분류됩니다.

![](assets/s_ncs_user_task_linked_tasks.png)

각 하위 과제는 주 과제와 연계되는 표준 과제이다.

![](assets/s_ncs_user_task_depends_on.png)

#### 작업 그룹화 {#grouping-tasks}

사용 **[!UICONTROL Grouped to]** 작업 실행을 다른 작업 실행에 따라 달라지도록 하는 필드입니다.

![](assets/s_ncs_user_task_group_with.png)

작업 간의 종속성은 캠페인 대시보드의 화살표로 표시됩니다.

![](assets/s_ncs_user_task_dependencies_from_board.png)

그룹화된 작업의 경우 Adobe Campaign은 상위 작업의 종료 날짜를 하위 작업에 시작 날짜로 자동 할당합니다. 예를 들어 **초대 만들기** 작업은 10월 15일 오후 3시 30분에 종료됩니다. **초대 이메일 보내기** 하위 작업은 10월 15일 오후 3시 30분에 시작됩니다.

또한 상위 작업의 종료를 연기하면 일부 하위 작업이 영향을 받을 수 있습니다. 이러한 작업은 상태가 인 하위 작업입니다. **[!UICONTROL Scheduled]** 시작 일자가 상위 작업의 새 종료 일자보다 이전인 경우 작업 기간은 동일하게 유지됩니다. 하위 작업의 시작 날짜가 상위 작업의 새 종료 날짜보다 이후인 경우 하위 작업은 영향을 받지 않습니다.

**예제**

10월 9일 오후 5시에 종료될 예정인 상위 작업에는 작업 A와 작업 B라는 두 개의 하위 작업이 있습니다. 작업 A는 10월 10일 오후 2시에 시작될 예정이며 작업 B는 10월 12일 오전 8시에 시작될 예정입니다.

상위 작업을 연기하겠습니다. 이제 10월 11일 오후 1시에 종료됩니다. A 작업만 연기되어 10월 11일 오후 1시에 시작됩니다.

![](assets/mrm_task_parent_postpones_child.png)

### 작업 실행 상태 {#execution-status-of-a-task}

작업 맵에서 작업 상태를 볼 수 있습니다. 작업 실행 상태는 운영자 작업에 따라 자동으로 업데이트됩니다.

작업은 다음과 같을 수 있습니다. **[!UICONTROL Scheduled]**, **[!UICONTROL In progress]**, **[!UICONTROL Finished]**, **[!UICONTROL Canceled]**, **[!UICONTROL Pending approval]** 또는 **[!UICONTROL Rejected]**.

* 작업이 생성되면 다음과 같이 됩니다. **[!UICONTROL Scheduled]** 시작 날짜가 미래인 경우. 시작 날짜에 도달할 때까지 이 상태를 유지합니다.
* 일단 시작되면 작업은 다음과 같습니다. **[!UICONTROL In progress]**. 작업 담당자가 작업을 닫으면 다음으로 변경됩니다. **[!UICONTROL Finished]**.
* 검토자가 정의된 경우 작업은 다음과 같습니다. **[!UICONTROL Pending approval]** 일단 담당자가 마감하고 검토자가 승인할 때까지 마감한다. 검토자가 거부하면 작업은 다음과 같이 됩니다. **[!UICONTROL Rejected]**.
* 작업은 책임자가 대시보드 또는 를 통해 취소할 수 있습니다. **[!UICONTROL Task map]** 을(를) 클릭하여 **[!UICONTROL Cancel]** 단추를 클릭합니다.
* 작업을 예약하려면 미래의 시작 날짜를 입력합니다. 그런 다음 작업 수행과 관련된 Adobe Campaign 운영자에게 첫 번째 알림을 보낼 수 있습니다. 다음을 참조하십시오 [작업 수명 주기 완료](#complete-task-life-cycle).

>[!NOTE]
>
>* 작업 상태가 자동으로 업데이트됩니다.
>* 유효기간이 종료되었더라도 종결되지 않은 업무는 계속 진행 중인 업무 목록에 나타난다. 경고는 작업이 지연되었음을 운영자에게 알립니다.
>

### 작업 진행 상태 {#progress-status-of-a-task}

실행 상태 외에도 작업을 진행 상태와 연결할 수 있습니다. **[!UICONTROL Late]**, **[!UICONTROL To approve]**, **[!UICONTROL To do today]** 또는 **[!UICONTROL To do this week]**. 이 정보는 작업 일정에 따라 자동으로 입력됩니다.

프로세스 또는 진행 상태별로 작업 목록을 필터링할 수 있습니다.

자세한 내용은 다음을 참조하십시오. [작업 액세스](#accessing-tasks).

### 작업 수명 주기 완료 {#complete-task-life-cycle}

다음은 담당자가 참여자 및 검토자를 정의한 전체 작업 수명 주기 단계입니다.

1. 담당자가 업무를 만들고 다양한 분야로 진출한다. 자세한 내용은 다음을 참조하십시오. [새 작업 만들기](#creating-a-new-task).

   작업을 만들고 편집할 때 **미래 시간으로 예약됨** (작업 시작 날짜에 도달하지 않는 한) 참여자 및 관리자에게 새 작업이 예약되었음을 알리는 알림을 보낼 수 있습니다.

   ![](assets/s_ncs_user_task_planed_send_message.png)

   이 첫 번째 알림을 보내려면 **[!UICONTROL Yes]**. 이 알림은 다음 작업에 대해 알려주며 콘텐츠에 대한 세부 정보와 마감까지 남은 일 수를 포함합니다.

   작업이 생성되고 미래를 위해 예약되면 상태는 다음과 같습니다 **[!UICONTROL Scheduled]**.

1. 작업 시작일에 책임자 및 참여자는 작업이 시작되었음을 알리는 알림을 받습니다. 상태가 다음으로 변경됨: **[!UICONTROL In progress]**.
1. 참가자에게 할당된 섹션을 완료한 후 참가자는 다음 중 한 가지 방법으로 작업을 승인할 수 있습니다.

   * 알림 이메일을 통해
   * 콘솔 또는 웹 인터페이스를 통해 작업 대시보드를 만듭니다.

     ![](assets/s_ncs_user_task_start_rea.png)

1. 참가자가 작업을 승인할 때마다 작업의 진행 상태가 업데이트됩니다.

   ![](assets/s_ncs_user_task_percentage_done_op.png)

1. 검토자는 운영자가 자신에게 할당된 섹션을 완료했다는 알림 이메일을 수신합니다.

   작업 대시보드의 진행률을 따를 수 있습니다.

   ![](assets/s_ncs_user_task_follow_from_dashboard.png)

1. 작업 책임자가 작업이 완료되었다고 결정하면 작업을 시작할 때 전송된 알림 이메일의 링크, 콘솔 또는 인터페이스를 사용하여 작업을 닫을 수 있습니다.

   ![](assets/s_ncs_user_task_console_ressource_validation.png)

   >[!NOTE]
   >
   >업무 담당자는 결재가 없더라도 언제든지 마감할 수 있다. 진행 상태는 자동으로 100%로 변경됩니다.

1. 작업 상태가 (으)로 변경됨 **[!UICONTROL To approve]**, 검토자에게 알림이 전송됩니다.

   알림 이메일, 콘솔 또는 웹 인터페이스를 통해 작업을 승인합니다.

   캠페인 대시보드를 통해 다음 작업을 수행할 수 있습니다.

   ![](assets/s_ncs_user_task_console_validation.png)

   또한 작업 승인 버튼을 사용할 수도 있습니다.

   ![](assets/s_ncs_user_task__validation.png)

   >[!NOTE]
   >
   >작업 상태가 (으)로만 변경됩니다. **[!UICONTROL To approve]** 을 활성화한 경우 **[!UICONTROL Enable task validation]** 의 옵션 **[!UICONTROL Resources]** 작업 창.\
   >검토자가 작업을 거부하면 상태가 (으)로 변경됩니다. **[!UICONTROL Rejected]**, 작업 라이프 사이클이 자동으로 다시 시작됩니다.

1. 작업 상태가 (으)로 변경됨 **[!UICONTROL Finished]**. 관련된 모든 사람에게 알림이 전송됩니다.

   >[!NOTE]
   >
   >작업이 완료되면 담당자는 해당 작업의 수명 주기를 다시 초기화할 수 있습니다. 이렇게 하려면 작업을 열고 다음을 클릭합니다. **[!UICONTROL Reset task to execute it again...]** 대시보드 하단에 있는 링크입니다.
