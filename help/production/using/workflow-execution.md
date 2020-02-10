---
title: 워크플로우 실행
seo-title: 워크플로우 실행
description: 워크플로우 실행
seo-description: null
page-status-flag: never-activated
uuid: 115256f6-bdf2-4594-885c-e90d02a25b80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 7d8828c5-5776-49ca-b4f7-a4a6aaaa9db1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 69b562979f3b32a4d30dfed0695cf3cf6c0fd26a

---


# 워크플로우 실행{#workflow-execution}

아래 섹션에서는 워크플로우 실행과 관련된 일반적인 문제와 이러한 문제를 해결하는 방법에 대한 정보를 제공합니다.

워크플로우에 대한 자세한 내용은 다음 섹션을 참조하십시오.

* [워크플로우 정보](../../workflow/using/about-workflows.md)
* [워크플로우 실행](../../workflow/using/executing-a-workflow.md)
* [워크플로우 사용 시 모범 사례](../../workflow/using/workflow-best-practices.md)

## 캠페인에서 가능한 한 빨리 시작 {#start-as-soon-as-possible-in-campaigns}

경우에 따라 **[!UICONTROL Start]** 단추를 클릭할 때 캠페인에서 실행되는 워크플로우가 시작되지 않습니다. 시작하는 대신 &quot;가능한 한 빨리 시작&quot; 상태로 이동합니다.

이 문제에는 몇 가지 원인이 있을 수 있습니다. 아래 절차에 따라 문제를 해결하십시오.

1. 기술 워크플로우 [**[!UICONTROL operationMgt]**](../../workflow/using/campaign.md) 상태를 확인합니다. 이 워크플로우는 캠페인 내에서 작업 또는 워크플로우를 관리합니다. 실패하면 워크플로우가 시작/중지되지 않습니다. 캠페인 워크플로우 실행을 다시 시작하려면 다시 시작하십시오.

   기술 워크플로우 모니터링에 대한 자세한 내용은 [이 페이지를](../../workflow/using/monitoring-technical-workflows.md)참조하십시오.

   >[참고]
   >
   >워크플로우를 다시 시작한 후 보류 중인 작업을 실행( **[!UICONTROL Scheduler]** 활동/ **[!UICONTROL Execute pending task(s) now]**&#x200B;을 마우스 오른쪽 단추로 클릭)해야 해당 작업이 다시 실패하는지 확인할 수 있습니다.

   워크플로우가 계속 실패하는 경우 감사 로그에서 특정 오류를 확인한 후 문제를 해결한 다음 워크플로우를 다시 시작합니다.

1. Campaign Classic 홈페이지에서 액세스할 수 있는 **[!UICONTROL wfserver]** 탭의 **[!UICONTROL Monitoring]** 모듈 상태를 [확인합니다(모니터링 프로세스](../../production/using/monitoring-processes.md)참조). 이 프로세스는 모든 워크플로우를 실행합니다.

   관리 사용자는 아래 명령을 사용하여 **주 응용 프로그램 서버에서 wfserver@`<instance>`**모듈이 실행되었는지 확인할 수도 있습니다.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   모듈이 실행되고 있지 않으면 Adobe 고객 지원 센터에 문의하십시오. 온-프레미스 설치가 있는 경우 관리 사용자가 아래 명령을 사용하여 서비스를 다시 시작해야 합니다.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >인스턴스 이름으로 **`<instancename>`** 대체합니다(프로덕션, 개발 등). 인스턴스 이름은 구성 파일을 통해 식별됩니다.
   >`[path of application]nl6/conf/config-<instancename>.xml`

   모듈을 다시 시작하는 방법에 대한 자세한 내용은 [이 섹션을](../../production/using/usual-commands.md#module-launch-commands)참조하십시오.

1. 인스턴스에서 실행되는 **캠페인 프로세스** 수가 임계값보다 큰지 확인합니다. 인스턴스에서 동시에 실행할 수 있는 캠페인 프로세스 수에 대한 [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) 옵션에 정의된 제한이 있습니다. 이 제한에 도달하면 실행 중인 워크플로우의 수가 제한보다 많으면 워크플로우는 &quot;가능한 한 빨리 시작&quot; 상태로 유지됩니다.

   이 문제를 해결하려면 원하지 않는 워크플로우를 중지하고 실패한 배달을 삭제합니다. 임계값에 도달하면 새 프로세스를 실행할 수 있습니다.

   인스턴스가 실행되는 워크플로우 수를 확인하려면 **[!UICONTROL Administration]** / **[!UICONTROL Audit]** 폴더에서 기본적으로 액세스할 수 있는 미리 정의된 뷰를 사용하는 것이 좋습니다. 자세한 내용은 [이 페이지를](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)참조하십시오.

   >[주의 사항]
   >
   >옵션 **[!UICONTROL NmsOperation_LimitConcurrency]** 임계값을 늘리면 인스턴스에 성능 문제가 발생할 수 있습니다. 어떤 경우에도 직접 수행하지 말고 Adobe Campaign 담당자에게 문의하십시오.

워크플로우를 모니터링하는 방법에 대한 자세한 내용은 [이 섹션을](../../workflow/using/monitoring-workflow-execution.md)참조하십시오.

## 시작 진행 중 {#start-in-progress}

워크플로가 실행되고 있지 않고 해당 상태가 **시작**&#x200B;상태인 경우 워크플로우 모듈이 실행되지 않을 수 있습니다.

이 확인란을 선택하고 필요한 경우 모듈을 시작하려면 다음 단계를 수행하십시오.

1. Campaign Classic 홈페이지에서 액세스할 수 있는 **[!UICONTROL wfserver]** 탭의 **[!UICONTROL Monitoring]** 모듈 상태를 [확인합니다(모니터링 프로세스](../../production/using/monitoring-processes.md)참조).

   관리 사용자는 아래 명령을 사용하여 **주 응용 프로그램 서버에서 wfserver@`<instance>`**모듈이 실행되었는지 확인할 수도 있습니다.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   모듈을 모니터링하는 방법에 대한 자세한 내용은 [이 섹션을](../../production/using/usual-commands.md#monitoring-commands-)참조하십시오.

1. 모듈이 실행되고 있지 않으면 Adobe 고객 지원 센터에 문의하십시오. 온-프레미스 설치가 있는 경우 관리자는 아래 명령을 사용하여 다시 시작해야 합니다.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >인스턴스 이름으로 **`<instancename>`** 대체합니다(프로덕션, 개발 등). 인스턴스 이름은 구성 파일을 통해 식별됩니다.
   >`[path of application]nl6/conf/config-<instancename>.xml`

   모듈을 다시 시작하는 방법에 대한 자세한 내용은 [이 섹션을](../../production/using/usual-commands.md#module-launch-commands)참조하십시오.

## 실패한 워크플로우 {#failed-workflow}

워크플로우가 실패할 경우 다음 단계를 수행합니다.

1. 워크플로우 저널을 확인합니다. 자세한 내용은 모니터링 워크플로우 실행 [및](../../workflow/using/monitoring-workflow-execution.md) 표시 로그 [섹션을](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) 참조하십시오.
1. 기술 워크플로우 모니터링 For more on this refer to the [this section](../../workflow/using/monitoring-technical-workflows.md).
1. 개별 워크플로우 활동에 대한 오류를 찾습니다.
