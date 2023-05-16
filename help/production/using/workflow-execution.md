---
product: campaign
title: 워크플로우 실행
description: 워크플로우 실행
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: 4b13e310fcee9ba24e83b697fca57bc494505642
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 3%

---

# 워크플로우 실행{#workflow-execution}



아래 섹션에서는 워크플로우 실행과 관련된 일반적인 문제와 이러한 문제를 해결하는 방법에 대한 정보를 제공합니다.

워크플로우에 대한 자세한 내용은 다음 섹션을 참조하십시오.

* [워크플로우 정보](../../workflow/using/about-workflows.md)
* [워크플로우 시작](../../workflow/using/starting-a-workflow.md)
* [워크플로우 수명 주기](../../workflow/using/workflow-life-cycle.md)
* [워크플로우 사용 모범 사례](../../workflow/using/workflow-best-practices.md)

## 캠페인에서 가능한 한 빨리 시작 {#start-as-soon-as-possible-in-campaigns}

경우에 따라 캠페인에서 실행되는 워크플로우가 **[!UICONTROL Start]** 버튼을 클릭합니다. 시작하는 대신 &quot;가능한 한 빨리 시작&quot; 상태로 이동합니다.

이 문제에 대한 몇 가지 이유가 있을 수 있으며, 아래 단계에 따라 문제를 해결하십시오.

1. 을(를) 확인합니다. [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) 기술 워크플로우 상태. 이 워크플로우는 캠페인 내의 작업 또는 워크플로우를 관리합니다. 실패하면 워크플로우가 시작/중지되지 않습니다. 캠페인 워크플로우 실행을 재개하려면 다시 시작합니다.

   기술 워크플로우 모니터링에 대한 자세한 내용은 [이 페이지](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >워크플로우를 다시 시작한 후 보류 중인 작업을 실행해야 합니다( **[!UICONTROL Scheduler]** 활동 / **[!UICONTROL Execute pending task(s) now]**)를 클릭하여 활동 중 하나에서 다시 실패하는지 확인합니다.

   워크플로우가 계속 실패하면 감사 로그에서 특정 오류를 확인하고 그에 따라 문제를 해결한 다음 워크플로우를 다시 시작합니다.

1. 을(를) 확인합니다. **[!UICONTROL wfserver]** 의 모듈 상태 **[!UICONTROL Monitoring]** 탭, Campaign Classic 홈페이지에서 액세스할 수 있습니다( [프로세스 모니터링](../../production/using/monitoring-processes.md)). 이 프로세스는 모든 워크플로우를 실행해야 합니다.

   관리자는 또한 **wfserver@`<instance>`** 모듈은 아래 명령을 사용하여 주 애플리케이션 서버에서 실행됩니다.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   모듈이 실행되고 있지 않으면 Adobe 고객 지원 센터에 문의하십시오. 온-프레미스 설치가 있는 경우 관리 사용자가 아래 명령을 사용하여 서비스를 다시 시작해야 합니다.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >바꾸기 **`<instance-name>`** 인스턴스(프로덕션, 개발 등)의 이름으로 인스턴스 이름은 구성 파일을 통해 식별됩니다.
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   모듈을 다시 시작하는 방법에 대한 자세한 내용은 [이 섹션](../../production/using/usual-commands.md#module-launch-commands).

1. 다음을 확인하십시오. **실행 중인 캠페인 프로세스 수** 인스턴스에서 임계값보다 큽니다. 에는 [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) 인스턴스에서 동시에 실행할 수 있는 캠페인 프로세스 수에 대한 옵션입니다. 이 제한에 도달하면 실행 중인 워크플로우 수가 제한을 초과하는 한 워크플로우는 &quot;가능한 한 빨리 시작&quot; 상태로 유지됩니다.

   이 문제를 해결하려면 원하지 않는 워크플로우를 중지하고 실패한 게재를 삭제합니다. 임계값에 도달하면 새 프로세스를 실행할 수 있습니다.

   인스턴스에서 실행 중인 워크플로우 수를 확인하려면 기본적으로 **[!UICONTROL Administration]** / **[!UICONTROL Audit]** 폴더를 입력합니다. 자세한 정보는 [이 페이지](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)를 참조하십시오.

   >[!IMPORTANT]
   >
   >증가 **[!UICONTROL NmsOperation_LimitConcurrency]** 옵션 임계값은 인스턴스에 성능 문제를 일으킬 수 있습니다. 어떤 경우든 직접 이러한 작업을 수행하지 말고 Adobe Campaign 담당자에게 문의하십시오.

워크플로우를 모니터링하는 방법에 대한 자세한 내용은 [이 섹션](../../workflow/using/monitoring-workflow-execution.md).

## 시작 진행 중 {#start-in-progress}

워크플로우가 실행되고 있지 않고 워크플로우의 상태가 **시작 진행 중**&#x200B;을 의미하는 것은 워크플로우 모듈이 실행되지 않음을 의미할 수 있습니다.

이 옵션을 확인하고 필요한 경우 모듈을 시작하려면 다음 단계를 수행합니다.

1. 을(를) 확인합니다. **[!UICONTROL wfserver]** 의 모듈 상태 **[!UICONTROL Monitoring]** 탭, Campaign Classic 홈페이지에서 액세스할 수 있습니다( [프로세스 모니터링](../../production/using/monitoring-processes.md)).

   관리자는 또한 **wfserver@`<instance>`** 모듈은 아래 명령을 사용하여 주 애플리케이션 서버에서 실행됩니다.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   모듈을 모니터링하는 방법에 대한 자세한 내용은 [이 섹션](../../production/using/usual-commands.md#monitoring-commands-).

1. 모듈이 실행되고 있지 않으면 Adobe 고객 지원 센터에 문의하십시오. 온-프레미스 설치가 있는 경우 관리자가 아래 명령을 사용하여 다시 시작해야 합니다.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >바꾸기 **`<instance-name>`** 인스턴스(프로덕션, 개발 등)의 이름으로 인스턴스 이름은 구성 파일을 통해 식별됩니다.
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   모듈을 다시 시작하는 방법에 대한 자세한 내용은 [이 섹션](../../production/using/usual-commands.md#module-launch-commands).

## 실패한 워크플로우 {#failed-workflow}

워크플로우가 실패하면 다음 단계를 수행합니다.

1. 워크플로우 저널을 확인합니다. 자세한 내용은 [워크플로우 실행 모니터링](../../workflow/using/monitoring-workflow-execution.md) 및 [로그 표시](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) 섹션에 자세히 설명되어 있습니다.
1. 기술 워크플로우 모니터링. 자세한 내용은 [이 섹션](../../workflow/using/monitoring-technical-workflows.md).
1. 개별 워크플로우 활동에서 오류를 찾습니다.
