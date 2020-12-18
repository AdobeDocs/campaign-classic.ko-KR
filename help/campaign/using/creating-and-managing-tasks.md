---
solution: Campaign Classic
product: campaign
title: 작업 만들기 및 관리
description: 작업 만들기 및 관리
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '3733'
ht-degree: 0%

---


# 작업 만들기 및 관리{#creating-and-managing-tasks}

## 작업 {#about-tasks} 정보

Adobe Campaign을 사용하면 작업을 만들고 전체 라이프 사이클을 애플리케이션 내에서 직접 관리할 수 있습니다. 프로그램 및 캠페인 구현은 Adobe Campaign 운영자나 외부 서비스 제공업체에 할당된 작업으로 분류할 수 있습니다. 이 작업 모드를 사용하면 모든 프로그램 참가자 및 외부 참가자를 포함하는 열린 공동 작업 환경을 만들 수 있습니다.

작업 목록 또는 캠페인 대시보드에서 작업을 만들고, 보고, 모니터링할 수 있습니다. 또한 마케팅 계획, 프로그램 및 캠페인의 일정에 따라 보고 추적할 수 있습니다.

작업은 캠페인에 연결되어 있고, 관련된 작업과 같은 종속성을 가질 수 있습니다. 각 작업의 상태, 우선 순위, 예상 로드 및 관련 비용이 있습니다.

모든 작업은 **캠페인** 우주를 통해 액세스할 수 있는 목록으로 그룹화됩니다. 자세한 내용은 [작업 액세스](#accessing-tasks)를 참조하십시오.

프로그램 일정에 표시할 수 있습니다.

![](assets/d_ncs_user_tasks_in_planning.png)

## 작업 액세스 {#accessing-tasks}

### 작업 표시 {#displaying-tasks}

작업은 **[!UICONTROL Campaigns]** 우주를 통해 액세스할 수 있는 작업 목록에 표시됩니다.

![](assets/s_ncs_user_task_edit_view.png)

연결된 연산자의 모든 작업을 볼 수 있습니다.

자세한 내용은 작업[ 및 ](#execution-status-of-a-task)작업의 진행 상태[를 참조하십시오.](#progress-status-of-a-task)

### 작업 필터링 {#filtering-tasks}

이 보기를 표시하면 **[!UICONTROL operator tasks]**&#x200B;만 표시하도록 자동으로 필터링됩니다. 창의 위쪽 섹션에 있는 필드를 사용하여 작업을 필터링할 수도 있습니다.

![](assets/s_ncs_user_task_filter_from_view.png)

### 작업 편집 {#editing-tasks}

작업을 클릭하여 편집합니다.

![](assets/s_ncs_user_task_edit_from_view.png)

## 새 작업 {#creating-a-new-task} 만들기

작업을 만들려면 캠페인 우주의 **[!UICONTROL Tasks]** 링크를 클릭하고 **[!UICONTROL Create]**&#x200B;을 선택합니다.

![](assets/s_ncs_user_task_create_new.png)

작업의 이름 이상을 입력하고 연결된 캠페인을 선택합니다. 시작 및 종료 날짜도 지정해야 합니다. 이 세 가지 정보는 의무적이다.

**[!UICONTROL Save]**&#x200B;을 클릭하여 작업을 만듭니다.

![](assets/s_ncs_user_task_create_simple.png)

캠페인의 대시보드를 통해 작업을 만들 수도 있습니다.이 경우 만든 캠페인에 자동으로 연결됩니다.

![](assets/s_ncs_user_task_create_new_from_op.png)

작업이 만들어지면 캠페인 일정과 작업 목록에 추가됩니다. 작업을 편집하려면 일정에서 작업을 선택하거나 작업 개요에서 해당 이름을 클릭하고 **[!UICONTROL Open]** 링크를 클릭합니다.

![](assets/s_ncs_user_task_edit_simple.png)

이를 구성하려면 다음을 지정해야 합니다.

* 관리자 및 참가자:[관리자 및 참가자](#manager-and-participants)를 참조하십시오.
* 작성 일정:[실행 일정](#execution-schedule)을 참조하십시오.
* 커밋된 비용:[비용 및 매출](#expenses-and-revenues)을 참조하십시오.

또한 광고 검토자([검토자](#reviewers) 참조)와 참조된 문서([참조된 문서](#documents-referenced) 참조)도 사용할 수 있습니다.

작업 라이프 사이클은 [라이프 사이클](#life-cycle)에 표시됩니다.

### 관리자 및 참가자 {#manager-and-participants}

작업을 담당하는 작업자만 작업을 닫을 수 있습니다.

기본적으로 Adobe Campaign 연산자가 작업을 만들면 작업에 자동으로 할당됩니다. 다른 연산자를 선택하려면 **[!UICONTROL Assigned to]** 필드를 사용합니다.

![](assets/s_ncs_user_task_edit_simple_general_tab.png)

>[!NOTE]
>
>연산자 관리는 [이 섹션](../../platform/using/access-management.md)에 있습니다.

작업을 수행하는 데 관련된 연산자를 지정할 수 있습니다. 이러한 연산자는 작업을 닫을 권한이 없습니다. 사용자는 자신에게 할당된 작업만 승인할 수 있습니다.

작업 도구 모음의 **[!UICONTROL Resources]** 아이콘을 사용하여 선택됩니다. **[!UICONTROL Add]**&#x200B;을 클릭하고 관련 연산자를 선택합니다.

![](assets/s_ncs_user_task_add_resources.png)

**[!UICONTROL Ok]**&#x200B;을 클릭한 다음 사용 비율을 입력합니다.이것은 작업 실행 기간 동안 연산자에 할당된 로드를 나타냅니다. 이 비율은 표시 전용이며 백분율로 표시됩니다.

예를 들어 실행 일정이 10일에 설정된 작업의 경우 사용률이 50%인 작업자는 10일 동안 작업 시간의 절반을 이 작업에 사용합니다.

각 연산자에 대해 예약된 작업 로드와 실제 작업 로드를 입력할 수 있습니다. 이러한 기간은 정보 목적으로만 제공됩니다.

종료 날짜 전에 작업에 관련된 모든 연산자에게 자동으로 전송되는 미리 알림을 구성할 수 있습니다.

**[!UICONTROL Edit link]** 아이콘을 통해 Adobe Campaign 연산자 프로파일을 볼 수 있습니다.

![](assets/s_ncs_user_task_edit_resource_profile.png)

연산자 대시보드를 사용하여 작업(진행 중인 다른 작업)을 확인할 수 있습니다.

![](assets/s_ncs_user_task_edit_resource_planning.png)

### 검토자 {#reviewers}

참가자 외에도, 담당자에 의해 작업이 닫힌 후 작업을 검토할 연산자를 정의할 수 있습니다. 이렇게 하려면 **[!UICONTROL Resources]** 창의 왼쪽 아래에 있는 **[!UICONTROL Enable task approval]** 옵션을 클릭합니다. 이것은 개별 연산자, 연산자 그룹 또는 연산자 목록일 수 있습니다.

![](assets/s_ncs_user_task_edit_resource_validation.png)

연산자 목록을 지정하려면 아래 표시된 대로 첫 번째 검토자 오른쪽에 있는 **[!UICONTROL Edit...]** 링크를 클릭하고 필요한 만큼 연산자를 추가합니다.

![](assets/s_ncs_user_task_edit_resource_operators.png)

검토자 구성 창의 하단 섹션에서 작업에 대한 승인 일정을 정의할 수 있습니다. 기본적으로 검토자는 제출 날짜로부터 3일 이내에 작업을 승인해야 합니다. 미리 알림을 구성할 수 있으며, 이 미리 알림은 승인 기한 전에 관련 운영자에게 자동으로 전송됩니다.

![](assets/s_ncs_user_edit_op_valid_calendar.png)

다른 연산자가 이미 이 작업을 수행하도록 지정되어 있더라도 작업을 담당하는 사람이 승인을 하는 작업을 자신에게 할당할 수 있습니다. 정의된 검토자가 없는 경우, 알림을 작업 담당자에게 보냅니다. **[!UICONTROL Administrator]** 권한을 가진 다른 모든 Adobe Campaign 연산자도 작업을 승인할 수 있습니다. 그러나 알림 메시지를 받지 않습니다.

### 문서 참조 {#documents-referenced}

작업에 문서와 마케팅 리소스를 추가할 수 있습니다(자세한 내용은 [마케팅 리소스 관리](../../campaign/using/managing-marketing-resources.md) 참조). 이렇게 하려면 작업을 열고 작업 도구 모음에서 **[!UICONTROL Documents]** 아이콘을 클릭합니다.

**[!UICONTROL Add]**&#x200B;을 클릭하고 작업에 추가할 문서를 선택합니다. 마케팅 리소스에 동일한 프로세스 적용

![](assets/s_ncs_user_task_edit_documents.png)

참조된 문서는 작업 대시보드뿐만 아니라 작업에 관련된 운영자에게 보낸 알림에 나타납니다.

![](assets/s_ncs_user_task_notification_documents.png)

### 실행 일정 {#execution-schedule}

작업의 유효 기간은 **[!UICONTROL Start]** 및 **[!UICONTROL End]** 필드에 표시됩니다. 예약된 부드는 기간 동안 수행할 작업 로드를 나타냅니다. 일 또는 시간 단위로 표시됩니다.

>[!NOTE]
>
>작업의 라이프 사이클은 [라이프 사이클](#life-cycle)에 표시됩니다.

또한 **[!UICONTROL Workload performed]** 필드는 일 및 시간 단위로 표시되므로 예약된 작업 로드와 관련하여 작업의 진행 상황을 수동으로 업데이트할 수 있습니다.

![](assets/s_ncs_user_task_percentage_done_enter.png)

백분율로 표현되는 작업의 **[!UICONTROL Progress status]**&#x200B;은 관련 연산자가 수행한 작업에 따라 자동으로 업데이트됩니다. 수동으로 입력할 수 있습니다.

이 정보는 작업 대시보드에서 볼 수 있습니다.

![](assets/s_ncs_user_task_percentage_done_from_dashboard.png)

캠페인 탭에도 표시됩니다.

![](assets/s_ncs_user_task_percentage_done_from_op.png)

작업 실행 일정 종료 날짜에 도달했지만 작업이 완료되지 않으면 작업은 **[!UICONTROL Late]**&#x200B;이 됩니다. 경고 연산자에도 경고 메시지가 표시됩니다.

자세한 내용은 [작업 진행 상태](#progress-status-of-a-task)를 참조하십시오.

### 비용 및 매출 {#expenses-and-revenues}

각 태스크에 대한 관련 비용을 정의하고 매출을 예측할 수 있습니다. 이러한 값을 계산한 다음 작업이 첨부된 캠페인에 대해 통합됩니다.

이 정보를 지정하려면 작업 도구 모음에서 **[!UICONTROL Expenses and revenue]** 아이콘을 클릭합니다.

![](assets/s_ncs_user_task_edit_costs.png)

기본적으로 청구된 예산은 작업이 첨부된 캠페인의 예산입니다. 작업 세부 정보에 표시됩니다.

>[!NOTE]
>
>비용 및 예산에 대한 자세한 내용은 [비용 약정, 계산 및 비용 청구](../../campaign/using/controlling-costs.md#cost-commitment--calculation-and-charging)를 참조하십시오.

이 창에서 도달할 목표를 정의할 수도 있습니다. 목표에 대한 예측 수익 관점에서 목표가 표시됩니다.

### 서비스 공급자 {#service-providers}

외부 서비스 공급자는 작업 관리에 관여할 수 있습니다.

이렇게 하려면 작업 속성을 편집하고 관련 서비스 공급자를 선택합니다. 서비스 제공자와 연관된 비용 범주는 창의 중앙 섹션에 자동으로 나열됩니다.

자세한 내용은 [서비스 공급자 만들기 및 해당 비용 범주](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)를 참조하십시오.

작업 실행과 관련된 비용 범주를 선택합니다. 이렇게 하려면 비용 유형을 선택하고 필요한 경우 추가 비용을 추가합니다.

![](assets/s_ncs_user_task_edit_simple_costs_tab.png)

>[!NOTE]
>
>예산 및 비용 관리 방법은 [비용 제어](../../campaign/using/controlling-costs.md)에 있습니다.

서비스 공급자를 선택하면 작업 대시보드에 표시됩니다.

![](assets/s_ncs_user_task_supplier_view.png)

### 지연 작업 {#late-tasks}

상태가 **[!UICONTROL Finished]**&#x200B;으로 변경되지 않고 종료 날짜에 도달하면 작업이 늦습니다. 기본적으로 작업이 늦으면 연산자는 경고가 표시되지 않습니다. 알림 이메일의 배달을 구성할 수 있습니다.작업에 참여하지 않더라도 모든 연산자에게 알림을 보낼 수 있습니다.

**[!UICONTROL Resources]** 상자로 이동하여 **[!UICONTROL Assignation]** 필드에 연산자를 추가합니다. 여러 사람에게 알리려면 연산자 그룹을 선택합니다.

![](assets/mrm_task_alert_if_late.png)

### 초기 알림 {#initial-notifications}

나중에 시작 날짜가 있는 작업을 만들거나 수정할 때 Adobe Campaign은 작업 담당자에게 이메일을 보내 작업 시작 시기를 알려줄 수 있도록 합니다.

![](assets/mrm_task_first_notif.png)

그러나, 만들고 있는 작업이 훨씬 길면 작업이 시작되기 전에 알림을 전송하도록 예약하는 것이 더 좋을 수 있습니다. 예를 들어, 작업이 1개월 후에 시작되는 경우 작업이 시작되기 1주일 전에 담당 담당자에게 통지할 수 있습니다.

알림을 예약하려면 **[!UICONTROL Resources]** 상자로 이동하여 **[!UICONTROL Initial notification]** 필드를 사용합니다.

![](assets/mrm_task_alert_before.png)

* 캠페인 내 작업의 경우 특정 날짜 및 시간을 선택합니다.
* 캠페인 템플릿 내의 작업의 경우 알림 시간은 작업이 시작되기 전 남은 시간으로 표시됩니다(예를 들어 **[!UICONTROL Initial notification]** 필드에 2d를 입력하면 작업 시작 날짜 2일 전에 이메일이 전송됩니다).

알림을 예약한 경우 작업을 저장할 때 Adobe Campaign에서는 알림을 즉시 전송하라는 메시지가 계속 표시됩니다. 전송하기로 결정해도 예약된 알림을 대체하지 않습니다.

### {#task-linked-to-a-program} 프로그램에 연결된 작업

특정 캠페인이 아닌 전체 조직과 관련된 작업을 관리하는 프로그램을 통해 직접 작업을 만들 수 있습니다(예를 들어, 프로그램 내에서 예정된 캠페인의 테마에 대해 논의하는 회의). 작업이 프로그램 일정에 나타납니다.

프로그램에 직접 연결된 작업을 만들려면:

1. 프로그램 일정을 엽니다.홈 페이지에서 **[!UICONTROL Campaigns > Browse > Other choices > Programs]**&#x200B;으로 이동합니다. 전체 프로그램 일정이 창의 오른쪽 섹션에 열립니다.
1. 일정에서 원하는 프로그램을 클릭합니다.그 안에 프로그램이 들어 있다.
1. 이 창에서 **[!UICONTROL Open]**&#x200B;을 클릭합니다. 프로그램 일정이 열립니다.
1. 오른쪽의 일정 위에 있는 **[!UICONTROL Add]** 단추를 클릭한 다음 **[!UICONTROL Add a task]**&#x200B;을 클릭합니다.

![](assets/mrm_task_create_from_prg.png)

### 연산자 가용성 {#operator-availability}

작업 대시보드에서 연산자 이름 옆에 있는 아이콘은 작업이 다루는 기간 동안 다른 작업 또는 이벤트에서 작업 중임을 나타냅니다. (운영자가 담당하거나 관련된 작업:**[!UICONTROL Assigned to]** 필드 또는 작업 **[!UICONTROL Resources]** 상자에 나타납니다.

![](assets/mrm_task_alert_operator_busy.png)

### 작업 과정 {#task-in-a-workflow}

캠페인 워크플로우에서 **[!UICONTROL Task]** 요소를 사용하면 작업이 승인되었는지 여부에 따라 두 가지 시나리오를 정의할 수 있습니다.

![](assets/mrm_task_in_workflow.png)

캠페인 워크플로우에서 **[!UICONTROL Task]** 활동은 **[!UICONTROL Flow control]** 탭에 있습니다.

## 작업 유형 {#types-of-task}

캠페인을 통해 작업을 만들 때 특정 작업을 만들 수 있습니다. 작업 유형은 선택한 템플릿에 정의됩니다.

![](assets/s_ncs_user_task_select_template.png)

다음 작업을 예약할 수 있습니다.

* [작업 제어](#control-tasks),
* [그룹화 작업](#grouping-task),
* [그룹화 작업](#grouping-task),
* [알림 작업](#notification-task).

>[!NOTE]
>
>**[!UICONTROL Control task]** 및  **[!UICONTROL Grouping]** 작업은 캠페인 대시보드 **** 를 통해서만 만들 수 있습니다.\
>연산자가 할당된 연산자의 작업 맵에 표시됩니다. [작업 액세스](#accessing-tasks)를 참조하십시오.

### 제어 작업 {#control-tasks}

**[!UICONTROL Control task]**&#x200B;이(가) 배달 승인에 연결되어 있습니다.타깃팅 승인, 컨텐츠, 추출 파일, 예산 또는 증명.

![](assets/s_ncs_user_task_new_control.png)

만들어진 작업은 캠페인 대시보드에 추가됩니다.

![](assets/s_ncs_user_task_edit_from_board.png)

그런 다음 편집하고 매개 변수를 지정할 수 있습니다.

### 마케팅 리소스 만들기 작업 {#marketing-resource-creation-task}

마케팅 리소스 만들기 작업을 사용하여 마케팅 리소스의 작성 및 게시를 관리할 수 있습니다. 자원 자체를 통해서가 아니라 작업을 통해 자원을 관리하는 경우 다음을 수행할 수 있습니다.

* 캠페인을 통해 리소스 만들기 프로세스를 제어합니다.
* 스케줄에서 리소스 생성 프로세스를 봅니다.
* 리소스 만들기 프로세스(미리 알림, 알림)를 관리합니다.
* 자원 생성에 연결된 비용을 계산하고 제어합니다.
* 작업을 통해 리소스를 승인하고 게시합니다(관련 옵션이 활성화된 경우).

#### 작업과 연결된 리소스 {#interaction-between-the-task-and-its-linked-resource} 간의 상호 작용

마케팅 리소스 만들기 작업은 연결된 리소스와 상호 작용합니다. 이것은 다음을 의미합니다.

* 자원 생성 일정 및 여기에 연결된 비용은 작업을 통해 관리됩니다.
* 연산자는 일반(다운로드 또는 업로드, 잠금 및 잠금 해제)과 같은 리소스에서 작업할 수 있습니다.작업에 영향을 주지 않습니다.
* 자원 승인 및 게시는 작업을 통해 수행할 수 있습니다.**[!UICONTROL Publish the marketing resource]** 옵션이 활성화되어 있으면 작업이 완료되면 리소스가 승인되고 자동으로 게시됩니다. 이 옵션이 활성화되지 않으면 작업과 리소스가 상호 작용하지 않습니다.한 사람만을 연기해도 다른 사람은 영향을 받지 않는다.

   일련의 연결된 작업을 사용하여 전체 승인 주기를 정의할 수 있습니다. 마지막 작업에 대해서만 **[!UICONTROL Publish the marketing resource]** 옵션을 선택합니다.리소스를 게시하려면 모든 작업을 완료해야 합니다. 또한 하위 마케팅 리소스 작업을 만들면 하위 작업에서 리소스가 자동으로 선택됩니다.

   * **리소스를 통해**:승인을 위해 리소스를 제출하거나 승인하면 이러한 작업이 작업에 영향을 주지 않습니다.
   * **작업을 통해**:작업 **[!UICONTROL Publish the marketing resource]** 에서 옵션이 선택되어 있으면 작업이 완료되면 리소스가 승인되고 자동으로 게시됩니다(위 참조). 옵션을 선택하지 않으면 작업과 리소스가 상호 작용하지 않습니다.한 사람만을 연기해도 다른 사람은 영향을 받지 않는다.

#### 마케팅 리소스 만들기 작업 {#configuring-a-marketing-resource-creation-task} 구성

작업을 검토하는 사람은 리소스에 정의된 컨텐츠를 검토하는 사람과 동일인이 필요하지 않습니다. 그러나 **[!UICONTROL Publish the marketing resource]** 옵션이 선택되어 있으면(아래 참조) 작업이 자동으로 리소스를 승인하므로 작업 검토자가 리소스 내용을 승인할 수 있습니다(또는 검토자가 정의되지 않은 경우 작업 관리자).

![](assets/mrm_task_asset_creation.png)

**[!UICONTROL Marketing resource]** 필드에서 이 작업을 통해 관리할 리소스를 정의합니다. 다음을 수행할 수 있습니다.

* 기존 리소스를 선택합니다.드롭다운 목록은 **[!UICONTROL Being edited]** 상태의 모든 리소스를 제공합니다.
* 리소스 만들기:**[!UICONTROL Select the link]** 아이콘을 클릭한 다음 **[!UICONTROL Create]** 아이콘을 클릭합니다.

**[!UICONTROL Publish the marketing resource]** 옵션을 사용하면 리소스 게시를 자동화할 수 있습니다.작업이 **[!UICONTROL Finished]**&#x200B;이면 승인 또는 승인을 위해 제출하지 않았더라도 작업을 완료하는 검토자가 리소스에 정의된 컨텐츠 검토자가 아닌 경우 등 리소스의 상태가 자동으로 **[!UICONTROL Published]**&#x200B;로 전환됩니다.

**[!UICONTROL Publish the resource]** 단추를 사용할 수 있으며 리소스 게시 검토자는 게시할 준비가 되었음을 알리는 알림 이메일을 수신합니다. **[!UICONTROL Edit > Tracking]** 탭에서 작업 검토자가 검토 및 게시하는 것이 표시됩니다. 리소스 사후 처리 워크플로우가 정의된 경우 지금 실행됩니다.

![](assets/mrm_resource_audit_tab.png)

### 그룹화 작업 {#grouping-task}

**[!UICONTROL Grouping task]** 유형 작업을 사용하면 여러 작업을 그룹화하고 진행 상황과 승인을 동기화할 수 있습니다.

그룹핑 작업에는 연결된 비용 또는 리소스가 없습니다.

그룹화 작업에 그룹화된 모든 작업은 자체 대시보드에서 볼 수 있습니다. 이렇게 하면 작업 목록을 필터링하여 관심 있는 작업만 표시할 수 있습니다.

그룹 작업에는 그룹화된 작업을 쉽게 만들 수 있는 링크가 있습니다.

그룹화 작업을 기반으로 그룹화된 그룹화된 작업을 만들려면 캠페인 대시보드로 이동하고 그룹화 작업의 이름을 클릭하여 해당 설명을 표시한 다음 **[!UICONTROL Add a task]**&#x200B;을 클릭합니다.

![](assets/mrm_task_grouped_create.png)

그러나 그룹화 작업에 연결할 작업을 이미 만든 경우 **[!UICONTROL Properties]** 상자의 **[!UICONTROL Linked to]** 필드를 통해 이 작업을 수행할 수 있습니다.

![](assets/s_ncs_user_task_group_with.png)

### 알림 작업 {#notification-task}

알림 작업을 통해 연산자, 연산자 그룹, 서비스 공급자 등에 대한 이메일 배달 일정을 예약할 수 있습니다. 이를 통해 캠페인을 곧 완료한다는 사실을 타인에게 알리거나 캠페인 시작 전에 문서를 전송하여 운영자가 준비할 수 있도록 미리 알림을 예약할 수 있습니다. 즉, 캠페인 또는 프로그램 내에서 커뮤니케이션을 추적하고 수행되는 작업을 자세히 볼 수 있습니다.

#### 라이프 사이클 {#life-cycle}

알림 작업은 승인이 필요하지 않습니다. 이는 표준 작업보다 라이프 사이클이 더 간편하다는 것을 의미합니다.

![](assets/mrm_task_notif_lifecycle.png)

알림 작업의 상태는 다음과 같습니다.

* **[!UICONTROL Scheduled]** 이메일이 전송될 때까지
* **[!UICONTROL In progress]** 전자 메일이 전송되고 종료 날짜가 될 때까지
* **[!UICONTROL Finished]** 종료 날짜가 되면

#### 구성 {#configuration}

![](assets/mrm_task_notif_dashboard.png)

만드는 동안 작업에 다음 요소를 입력해야 합니다.

* **[!UICONTROL Assigned to]** :이메일을 받을 연산자 또는 연산자 그룹입니다. 이메일을 전송한 후 작업을 다시 할당하면 이메일이 새 연산자에게 전송되지 않습니다. 이렇게 하려면 작업을 다시 초기화하고 시작 날짜를 변경해야 합니다.
* **작업 시작 날짜**:알림 이메일을 보낼 날짜입니다. 이 날짜는 작업 기록 시점의 차후에 이루어져야 합니다.
* **작업 종료 날짜**:작업 상태가 변경되는 날짜입니다 **[!UICONTROL Finished]**. 기본적으로 종료 날짜는 시작 날짜와 동일합니다. 그러나 작업에 기간을 할당하면 필요한 경우 작업자가 일정에 따라 수행해야 하는 시간을 나타낼 수 있습니다.
* **[!UICONTROL Description]** :여기에 입력한 텍스트가 알림 이메일 본문에 표시됩니다.

   ![](assets/mrm_task_notif_dashboard_msg.png)

작업 및 알림 이메일에 첨부 파일을 추가할 수 있습니다. 이렇게 하려면 오른쪽 상단의 도구 모음에서 **[!UICONTROL Documents]** 아이콘을 클릭합니다.

## 라이프 사이클 {#life-cycle-1}

### 작업 {#links-between-tasks} 간 링크

각 작업의 **[!UICONTROL Properties]** 단추를 사용하여 캠페인의 작업 간 링크를 정의할 수 있습니다. 그룹화 작업을 사용하여 작업을 하위 작업으로 분할하거나([연결된 작업](#linked-tasks) 참조) 작업 간의 종속성을 정의할 수 있습니다( [그룹화 작업](#grouping-tasks) 참조).

#### 연결된 작업 {#linked-tasks}

**[!UICONTROL Linked task]** 필드를 사용하여 작업을 그룹화 작업과 연결합니다. [작업 유형](#types-of-task)을 참조하십시오.

다음 예에서 타깃팅 승인은 4개의 하위 작업으로 분류됩니다.

![](assets/s_ncs_user_task_linked_tasks.png)

각 하위 작업은 기본 작업에 연결된 표준 작업입니다.

![](assets/s_ncs_user_task_depends_on.png)

#### 그룹화 작업 {#grouping-tasks}

**[!UICONTROL Grouped to]** 필드를 사용하여 작업의 실행이 다른 작업의 실행에 따라 달라지도록 하십시오.

![](assets/s_ncs_user_task_group_with.png)

작업 간 종속성은 캠페인 대시보드의 화살표로 표시됩니다.

![](assets/s_ncs_user_task_dependencies_from_board.png)

그룹화된 작업의 경우 Adobe Campaign은 상위 작업의 종료 날짜를 시작 날짜로 하위 작업에 자동으로 지정합니다. 예를 들어 **초대장 만들기** 작업이 10월 15일 오후 3:30PM에 종료되면 **초대장 이메일 보내기** 하위 작업이 10월 15일 오후 3:30에 시작됩니다.

또한 상위 작업의 끝을 연기하면 하위 작업 중 일부가 영향을 받을 수 있습니다.상태는 **[!UICONTROL Scheduled]**&#x200B;이고 시작 날짜가 상위 작업의 새 종료 날짜보다 빠른 하위 작업입니다. 작업 기간은 동일하게 유지됩니다. 하위 작업의 시작 날짜가 상위 작업의 새 종료 날짜보다 늦은 경우 하위 작업은 영향을 받지 않습니다.

**예제**

10월 9일 오후 5시에 종료될 예정인 상위 태스크에는 2개의 하위 태스크, 태스크 A와 태스크 B가 있습니다. 태스크 A는 10월 10일 오후 2시에 시작할 예정이며 태스크 B는 10월 12일 오전 8시에 시작할 예정입니다.

상위 작업을 연기합니다.10월 11일 오후 1시에 종료됩니다. 작업 A만 연기되고 10월 11일 오후 1시에 시작됩니다.

![](assets/mrm_task_parent_postpones_child.png)

### 작업 실행 상태 {#execution-status-of-a-task}

작업 상태는 작업 맵에서 볼 수 있습니다. 작업의 실행 상태는 연산자 작업에 따라 자동으로 업데이트됩니다.

작업은 다음과 같습니다.**[!UICONTROL Scheduled]**, **[!UICONTROL In progress]**, **[!UICONTROL Finished]**, **[!UICONTROL Canceled]**, **[!UICONTROL Pending approval]** 또는 **[!UICONTROL Rejected]**.

* 작업이 만들어지면 시작 날짜가 미래인 경우 **[!UICONTROL Scheduled]**&#x200B;입니다. 시작 날짜가 될 때까지 이 상태를 유지합니다.
* 작업이 시작되면 작업이 **[!UICONTROL In progress]**&#x200B;입니다. 작업 담당자가 작업을 닫으면 **[!UICONTROL Finished]**&#x200B;으로 변경됩니다.
* 검토자가 정의된 경우 해당 검토자가 검토자를 닫고 검토자가 승인하기 전까지 검토자가 작업을 종료하면 해당 작업은 **[!UICONTROL Pending approval]**&#x200B;이 됩니다. 검토자가 거부하면 작업은 **[!UICONTROL Rejected]**&#x200B;이 됩니다.
* **[!UICONTROL Cancel]** 단추를 클릭하여 대시보드 또는 **[!UICONTROL Task map]**&#x200B;을 통해 책임을 지는 사람이 작업을 취소할 수 있습니다.
* 작업을 예약하려면 나중에 시작 날짜를 입력합니다. 그런 다음 작업 수행과 관련된 Adobe Campaign 운영자에게 첫 번째 알림을 보낼 수 있습니다. [작업 수명 주기 완료](#complete-task-life-cycle)를 참조하십시오.

>[!NOTE]
>
>* 작업 상태는 자동으로 업데이트됩니다.
>* 유효 기간이 끝났더라도 닫히지 않은 작업은 진행 중인 작업 목록에 계속 나타납니다. 경고가 연산자에게 작업이 지연되었음을 알립니다.

>



### 작업의 진행 상태 {#progress-status-of-a-task}

실행 상태 외에 진행 상태와 연결할 수 있습니다.**[!UICONTROL Late]**, **[!UICONTROL To approve]**, **[!UICONTROL To do today]** 또는 **[!UICONTROL To do this week]**. 이 정보는 작업 일정에 따라 자동으로 입력됩니다.

프로세스 또는 진행 상태별로 작업 목록을 필터링할 수 있습니다.

자세한 내용은 [작업 액세스](#accessing-tasks)를 참조하십시오.

### 작업 수명 주기 완료 {#complete-task-life-cycle}

다음은 담당 담당자가 참가자 및 검토자를 정의한 전체 작업 수명 주기 단계입니다.

1. 담당자가 작업을 만들고 다양한 필드에 입력합니다. 자세한 내용은 [새 작업 만들기](#creating-a-new-task)를 참조하십시오.

   작업 시작 날짜에 도달하지 않은 경우 나중에 **예약된 작업**&#x200B;을(를) 만들고 편집할 때 참가자 및 관리자에게 새 작업이 예약되었음을 알리는 알림을 보낼 수 있습니다.

   ![](assets/s_ncs_user_task_planed_send_message.png)

   이 첫 번째 알림을 보내려면 **[!UICONTROL Yes]**&#x200B;을 클릭합니다. 이 알림은 다음 작업에 대해 알려 주고 컨텐츠에 대한 세부 사항 및 마감일까지 남은 일 수를 포함합니다.

   작업이 생성되어 향후에 예약된 경우 작업의 상태는 **[!UICONTROL Scheduled]**&#x200B;입니다.

1. 작업 시작 날짜에 담당자 및 참가자는 작업이 시작되었음을 알리는 알림을 받습니다. 상태는 **[!UICONTROL In progress]**&#x200B;으로 변경됩니다.
1. 참가자는 자신에게 할당된 섹션을 완료한 후 다음 중 하나를 사용하여 작업을 승인할 수 있습니다.

   * 을 알림 이메일을 통해 전송할 수 있습니다.
   * 작업 대시보드에서 콘솔 또는 웹 인터페이스를 통해

      ![](assets/s_ncs_user_task_start_rea.png)

1. 참가자가 작업을 승인할 때마다 작업의 진행 상태가 업데이트됩니다.

   ![](assets/s_ncs_user_task_percentage_done_op.png)

1. 검토자는 운영자가 자신에게 할당된 섹션을 완료했다는 알림 이메일을 수신합니다.

   작업 대시보드의 진행 상태를 따를 수 있습니다.

   ![](assets/s_ncs_user_task_follow_from_dashboard.png)

1. 작업을 담당하는 사람이 작업을 완료했다고 결정하면 작업이 시작될 때 보낸 알림 이메일의 링크, 콘솔 또는 인터페이스를 사용하여 작업을 닫을 수 있습니다.

   ![](assets/s_ncs_user_task_console_ressource_validation.png)

   >[!NOTE]
   >
   >승인이 없어도 작업을 담당하는 사람은 언제든지 작업을 닫을 수 있습니다. 진행 상태는 자동으로 100%로 변경됩니다.

1. 작업 상태가 **[!UICONTROL To approve]**&#x200B;으로 변경되고 알림이 검토자에게 전송됩니다.

   알림 이메일, 콘솔 또는 웹 인터페이스를 통해 작업을 승인합니다.

   캠페인 대시보드를 통해 작업할 수 있습니다.

   ![](assets/s_ncs_user_task_console_validation.png)

   작업 승인 단추를 사용할 수도 있습니다.

   ![](assets/s_ncs_user_task__validation.png)

   >[!NOTE]
   >
   >작업의 **[!UICONTROL Resources]** 창에서 **[!UICONTROL Enable task validation]** 옵션을 활성화한 경우에만 작업 상태가 **[!UICONTROL To approve]**&#x200B;으로 변경됩니다.\
   >검토자가 작업을 거부하면 해당 상태가 **[!UICONTROL Rejected]**&#x200B;으로 변경되고 작업 라이프 사이클이 자동으로 다시 시작됩니다.

1. 작업 상태가 **[!UICONTROL Finished]**&#x200B;으로 변경됩니다. 알림은 모든 관련 사용자에게 전송됩니다.

   >[!NOTE]
   >
   >작업이 완료되면 담당 담당자가 해당 작업의 라이프 사이클을 다시 초기화할 수 있습니다. 이렇게 하려면 작업을 열고 대시보드 아래쪽에 있는 **[!UICONTROL Reset task to execute it again...]** 링크를 클릭합니다.

