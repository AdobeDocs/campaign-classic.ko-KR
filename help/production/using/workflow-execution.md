---
solution: Campaign Classic
product: campaign
title: 워크플로우 실행
description: 워크플로우 실행
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: a9d58e25ab17baaabf4ff8c109b53e83c7d93218
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
* [워크플로우 사용 시 모범 사례](../../workflow/using/workflow-best-practices.md)

## 캠페인 {#start-as-soon-as-possible-in-campaigns}에서 가능한 빨리 시작

경우에 따라 캠페인에서 실행되는 워크플로우는 **[!UICONTROL Start]** 단추를 클릭할 때 시작되지 않습니다. 시작하는 대신 &quot;가능한 한 빨리 시작&quot; 상태로 이동합니다.

이 문제에는 몇 가지 원인이 있을 수 있으며 아래 단계에 따라 문제를 해결하십시오.

1. [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) 기술 워크플로우 상태를 확인합니다. 이 워크플로우는 캠페인 내의 작업 또는 워크플로우를 관리합니다. 실패하면 워크플로우가 시작/중지되지 않습니다. 캠페인 워크플로우 실행을 재개하려면 다시 시작합니다.

   기술 워크플로우 모니터링에 대한 자세한 내용은 [이 페이지](../../workflow/using/monitoring-technical-workflows.md)를 참조하십시오.

   >[!NOTE]
   >
   >워크플로우를 다시 시작한 후 보류 중인 작업을 실행(**[!UICONTROL Scheduler]** 활동 / **[!UICONTROL Execute pending task(s) now]** 마우스 오른쪽 단추를 클릭)하여 모든 활동에서 다시 실패하는지 확인합니다.

   워크플로우가 계속 실패하는 경우 감사 로그에서 특정 오류를 확인하고 그에 따라 문제를 해결한 다음 워크플로우를 다시 시작합니다.

1. Campaign Classic 홈 페이지에서 액세스할 수 있는 **[!UICONTROL Monitoring]** 탭의 **[!UICONTROL wfserver]** 모듈 상태를 확인합니다([모니터링 프로세스](../../production/using/monitoring-processes.md) 참조). 이 프로세스는 모든 워크플로우 실행을 책임집니다.

   관리자는 아래 명령을 사용하여 **wfserver@`<instance>`** 모듈이 기본 응용 프로그램 서버에서 시작되었는지 확인할 수도 있습니다.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   모듈이 실행되고 있지 않으면 Adobe 고객 지원 센터에 문의하십시오. 온-프레미스 설치가 있는 경우 관리자 사용자는 아래 명령을 사용하여 서비스를 다시 시작해야 합니다.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >**`<instancename>`**을(를) 인스턴스 이름(프로덕션, 개발 등)으로 바꿉니다. 인스턴스 이름은 구성 파일을 통해 식별됩니다.
   >`[path of application]nl6/conf/config-<instancename>.xml`

   모듈을 다시 시작하는 방법에 대한 자세한 내용은 [이 섹션](../../production/using/usual-commands.md#module-launch-commands)을 참조하십시오.

1. 인스턴스에서 **을(를) 실행하는 캠페인 프로세스의**&#x200B;개수가 임계값보다 큰지 확인합니다. 인스턴스에서 동시에 실행할 수 있는 캠페인 프로세스의 수에 대한 제한은 [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) 옵션으로 정의됩니다. 이 제한에 도달하면 실행 중인 워크플로우 수가 제한보다 많은 경우 워크플로우는 &quot;가능한 한 빨리 시작&quot; 상태로 유지됩니다.

   이 문제를 해결하려면 원치 않는 워크플로우를 중지하고 실패한 배달을 삭제합니다. 임계값에 도달하면 새 프로세스를 실행할 수 있습니다.

   인스턴스의 작업 흐름 수를 확인하려면 **[!UICONTROL Administration]** / **[!UICONTROL Audit]** 폴더에서 기본적으로 액세스할 수 있는 미리 정의된 보기를 사용하는 것이 좋습니다. 자세한 정보는 [이 페이지](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)를 참조하십시오.

   >[!IMPORTANT]
   >
   >**[!UICONTROL NmsOperation_LimitConcurrency]** 옵션 임계값을 늘리면 인스턴스에서 성능 문제가 발생할 수 있습니다. 어떤 경우에도 이 작업을 직접 수행하지 말고 Adobe Campaign 담당자에게 문의하십시오.

작업 과정을 모니터링하는 방법에 대한 자세한 내용은 [이 섹션](../../workflow/using/monitoring-workflow-execution.md)을 참조하십시오.

## 시작 진행 중 {#start-in-progress}

워크플로가 실행되고 있지 않고 해당 상태가 **진행 중 시작**&#x200B;인 경우 워크플로우 모듈이 시작되지 않은 것일 수 있습니다.

이 내용을 확인하고 필요한 경우 모듈을 시작하려면 다음 단계를 수행하십시오.

1. Campaign Classic 홈 페이지에서 액세스할 수 있는 **[!UICONTROL Monitoring]** 탭의 **[!UICONTROL wfserver]** 모듈 상태를 확인합니다([모니터링 프로세스](../../production/using/monitoring-processes.md) 참조).

   관리자는 아래 명령을 사용하여 **wfserver@`<instance>`** 모듈이 기본 응용 프로그램 서버에서 시작되었는지 확인할 수도 있습니다.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   모듈 모니터링 방법에 대한 자세한 내용은 [이 섹션](../../production/using/usual-commands.md#monitoring-commands-)을 참조하십시오.

1. 모듈이 실행되고 있지 않으면 Adobe 고객 지원 센터에 문의하십시오. 온-프레미스 설치가 있는 경우 관리자는 아래 명령을 사용하여 이를 다시 시작해야 합니다.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >**`<instancename>`**을(를) 인스턴스 이름(프로덕션, 개발 등)으로 바꿉니다. 인스턴스 이름은 구성 파일을 통해 식별됩니다.
   >`[path of application]nl6/conf/config-<instancename>.xml`

   모듈을 다시 시작하는 방법에 대한 자세한 내용은 [이 섹션](../../production/using/usual-commands.md#module-launch-commands)을 참조하십시오.

## 워크플로 {#failed-workflow} 실패

워크플로우에 실패하면 다음 단계를 수행하십시오.

1. 워크플로우 분개를 확인합니다. 자세한 내용은 [모니터링 워크플로 실행](../../workflow/using/monitoring-workflow-execution.md) 및 [표시 로그](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) 섹션을 참조하십시오.
1. 기술 워크플로우 모니터링 자세한 내용은 [이 섹션](../../workflow/using/monitoring-technical-workflows.md)을 참조하십시오.
1. 개별 워크플로우 활동에 대한 오류를 찾습니다.
