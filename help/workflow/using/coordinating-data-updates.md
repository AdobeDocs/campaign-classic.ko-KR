---
title: 데이터 업데이트 조정
seo-title: 데이터 업데이트 조정
description: 데이터 업데이트 조정
seo-description: null
page-status-flag: never-activated
uuid: 003d63f8-3169-4190-882e-e360a83ccafb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: efe09c66-b74b-48f0-9042-5da4342e014e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# 데이터 업데이트 조정{#coordinating-data-updates}

이 사용 사례에서는 워크플로우의 여러 실행을 사용할 때 컨텐츠 업데이트를 관리할 수 있는 워크플로우 작성을 자세히 설명합니다.

다른 업데이트 작업을 실행하기 전에 업데이트 프로세스가 종료되었는지 확인하는 것이 목표입니다. 이를 위해 인스턴스 변수를 설정하고, 인스턴스가 실행 중인지 여부를 Workflow가 테스트하여 워크플로우 실행을 계속할지 여부를 결정하고 업데이트를 수행하도록 합니다.

![](assets/uc_dataupdate_wkf.png)

이 워크플로우는 다음과 같이 구성됩니다.

* 특정 **빈도에** 따라 워크플로우를 실행하는 스케줄러 활동.
* 워크플로우가 **이미** 실행 중인지 확인하는 테스트 활동.
* **워크플로가** 아직 실행되고 있지 않을 경우 쿼리 및 **업데이트 데이터** 활동 다음에 워크플로우 인스턴스 변수를 **false로 다시** 초기화하는 종료 활동이 있습니다.
* 워크플로우가 **이미** 실행 중인 경우 종료 활동.

워크플로우를 빌드하려면 아래 단계를 따르십시오.

1. 스케줄러 **활동을** 추가한 다음 필요에 따라 빈도를 구성합니다.
1. Test **활동을** 추가하여 워크플로우가 이미 실행 중인지 확인한 다음 아래와 같이 구성합니다.

   >[!NOTE]
   >
   >&quot;isRunning&quot;은 이 예제에 대해 선택한 인스턴스 변수 이름입니다. 이 변수는 내장 변수가 아닙니다.

   ![](assets/uc_dataupdate_test.png)

1. 종료 **활동을 포크** 없음에 **추가합니다** . 이렇게 하면 워크플로우가 이미 실행되고 있으면 아무 것도 실행되지 않습니다.
1. 원하는 활동을 예 포크에 **추가합니다** . Adobe의 경우 데이터 **쿼리** 및 **업데이트** 활동을 참조하십시오.
1. 첫 번째 활동을 연 다음 **탭에서 instance.vars.isRunning = true** **[!UICONTROL Advanced]** 명령을 추가합니다. 이렇게 하면 인스턴스 변수가 실행 중인 것으로 설정됩니다.

   ![](assets/uc_dataupdate_query.png)

1. 포크의 **끝에** 종료 **[!UICONTROL Yes]** 활동을 추가한 다음 **탭에서** instance.vars.isRunning = false **[!UICONTROL Advanced]** 명령을 추가합니다.

   이렇게 하면 워크플로우가 실행되는 동안에는 아무 작업도 실행되지 않습니다.

   ![](assets/uc_dataupdate_end.png)

**관련 항목:**

* [동시 다중 실행 방지](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [데이터 활동 업데이트](../../workflow/using/update-data.md)

