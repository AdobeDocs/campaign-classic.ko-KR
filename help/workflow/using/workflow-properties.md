---
title: 워크플로우 속성
description: 캠페인 워크플로우 속성에 대한 자세한 내용
page-status-flag: never-activated
uuid: bd576cc0-2db8-4519-bcb5-52bf5c811f42
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: 71969b30-cc01-4358-9597-f17939720684
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 1%

---


# 워크플로우 속성{#workflow-properties}

## 실행 탭 {#execution-tab}

워크플로우의 창 **[!UICONTROL Execution]** 탭은 **[!UICONTROL Properties]** 세 개의 섹션으로 구분됩니다.

![](assets/wf_execution_tab.png)

### 예약 {#scheduler}

이 섹션은 캠페인 워크플로우에만 표시됩니다.

* **[!UICONTROL Priority]**

   워크플로우 엔진은 이 필드에 정의된 우선 순위 기준을 기반으로 실행할 워크플로우를 처리합니다. 예를 들어, 우선 순위가 있는 모든 워크플로우는 우선 순위가 있는 워크플로우보다 먼저 **[!UICONTROL Average]** **[!UICONTROL Low]** 실행됩니다.

* **[!UICONTROL Schedule execution for a time of low activity]**

   이 옵션은 워크플로우의 시작을 덜 바쁜 기간으로 연기합니다. 일부 워크플로우는 데이터베이스 엔진의 리소스 측면에서 비용이 많이 들 수 있습니다. 활동이 낮은 시간(예: 밤일)에 대해 실행을 예약하는 것이 좋습니다. 낮은 활동 기간은 **[!UICONTROL Processes on campaigns]** 기술 워크플로우에서 정의됩니다.

### 실행 {#execution}

* **[!UICONTROL Default affinity]**

   설치에 여러 개의 워크플로우 서버가 포함되어 있는 경우 이 필드를 사용하여 워크플로우가 실행될 시스템을 선택합니다. 이 필드에 정의된 값이 서버에 없으면 워크플로우는 보류 상태로 유지됩니다.

   Refer to this [section](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

* **[!UICONTROL History in days]**

   데이터베이스의 작업 테이블은 실행 내역(작업, 이벤트, 로그)을 유지합니다. 여기에서 이 워크플로우에 대해 보관할 일 수를 정의할 수 있습니다.정리 프로세스는 하루에 한 번 가장 오래된 아카이브를 삭제합니다. 이 필드의 값이 0이면 아카이브는 삭제되지 않습니다.

* **[!UICONTROL Log SQL queries in the journal]**

   이 기능은 고급 사용자용으로 예약되어 있습니다. 타깃팅 활동(쿼리, 결합, 교차 등)이 포함된 워크플로우에 대해 다룹니다. 이 옵션을 선택하면 워크플로우 실행 중에 데이터베이스로 전송된 SQL 쿼리가 Adobe Campaign에 표시됩니다.즉, 쿼리를 최적화하거나 문제를 진단할 수 있도록 분석할 수 있습니다.

   쿼리는 워크플로우(캠페인 워크플로우 제외)에 추가되는 **[!UICONTROL SQL logs]** 탭에 표시되고 옵션이 활성화되면 **[!UICONTROL Properties]** 활동에 표시됩니다. 이 **[!UICONTROL Audit]** 탭에는 SQL 쿼리도 포함되어 있습니다.

   ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

   이 옵션은 디도청용으로 사용할 수 있으며 제작에서는 사용할 수 없습니다. 이 옵션이 활성화되면 워크플로우는 우선 순위를 차지하며 다른 모든 워크플로우는 이 작업이 완료될 때까지 중지됩니다.

### Error management {#error-management}

* **[!UICONTROL Troubleshooting]**

   이 필드에서는 워크플로우 작업에 오류가 있을 경우 수행할 작업을 정의할 수 있습니다. 다음 두 가지 옵션을 사용할 수 있습니다.

   * **[!UICONTROL Stop the process]**:워크플로가 자동으로 일시 중지됩니다. 워크플로우 상태가 로 변경됩니다 **[!UICONTROL Failed]**. 문제가 해결되면 **[!UICONTROL Start]** 또는 **[!UICONTROL Restart]** 단추를 사용하여 워크플로우를 다시 시작합니다.
   * **[!UICONTROL Ignore]**:오류를 트리거한 작업의 상태가 로 변경되지만 **[!UICONTROL Failed]**&#x200B;워크플로우는 상태를 유지합니다 **[!UICONTROL Started]** . 이 구성은 반복되는 작업에 적합합니다.분기에 스케줄러가 포함되어 있으면 워크플로우가 다음에 실행될 때 정상적으로 시작됩니다.

* **[!UICONTROL Consecutive errors]**

   이 필드는 필드에서 **[!UICONTROL Ignore]** 값을 선택하면 사용할 수 **[!UICONTROL In case of errors]** 있습니다. 프로세스를 중지하기 전에 무시할 수 있는 오류 수를 지정할 수 있습니다. 이 수에 도달하면 워크플로우 상태가 로 변경됩니다 **[!UICONTROL Failed]**. 이 필드의 값이 0이면 오류 수에 관계없이 워크플로우가 중지되지 않습니다.

* **[!UICONTROL Template]**

   이 필드를 사용하면 상태가 로 변경될 때 워크플로우 감독자에게 전송할 알림 템플릿을 선택할 수 있습니다 **[!UICONTROL Failed]**.

   프로필 내에 이메일 주소가 있는 경우 관련 운영자에게 이메일로 알려 줍니다. 워크플로우 감독자를 정의하려면 속성 **[!UICONTROL Supervisor(s)]** 필드(**[!UICONTROL General]** 탭)로 이동합니다.

   ![](assets/wf-properties_select-supervisors.png)

   기본 템플릿에는 **[!UICONTROL Notification to a workflow supervisor]** 웹을 통해 Adobe Campaign 콘솔에 액세스하는 링크가 포함되어 있으므로 수신자가 로그온한 후 문제를 해결할 수 있습니다.

   개인화된 템플릿을 만들려면 로 이동합니다 **[!UICONTROL Administration>Campaign management>Technical deliveries and templates]**.

