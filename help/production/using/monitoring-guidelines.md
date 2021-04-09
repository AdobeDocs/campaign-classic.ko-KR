---
solution: Campaign Classic
product: campaign
title: 모니터링 지침
description: Campaign 인스턴스 및 프로세스를 모니터링하기 위한 지침과 모범 사례를 알아봅니다.
audience: production
content-type: reference
topic-tags: introduction
exl-id: ca0c33c5-7350-462a-bc65-4cab51e529d9
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 18%

---

# 모니터링 지침 {#monitoring-guidelines}

## 인스턴스 모니터링 대시보드 {#instance-monitoring-dashboard}

Campaign Classic 홈 페이지에서 액세스할 수 있는 **[!UICONTROL Monitoring]** 탭은 인스턴스를 모니터링하는 데 도움이 되는 기본 시작 지점입니다.

이 대시보드는 인스턴스에서 발생하는 사항에 대한 대시보드를 제공합니다.상태(빌드 버전, 설치된 패키지 등), 시스템 표시기, 로그, 현재 실행 중인 워크플로우, 마지막 전송 상태 등

자세한 정보는 [여기](../../production/using/monitoring-processes.md)에서 확인할 수 있습니다.

![](assets/monitoring_tab.png)

## 모니터링 Campaign Classic 프로세스 {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">인스턴스 모니터링</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#moniroting-workflows">워크플로우 모니터링</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">게재 모니터링</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">데이터베이스 모니터링</a></p></td></tr>
</table>

다양한 캠페인 프로세스를 모니터링하는 추가 방법을 사용할 수 있습니다. 또한 여러 가지 방법으로 인스턴스를 모니터링하여 시스템이 건강한지 확인하고 워크플로우를 설정하거나 배달 등을 보낼 때 발생할 수 있는 문제를 해결할 수 있습니다.

### 인스턴스 모니터링 {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**자동 모니터링 툴**

몇 가지 자동 방법을 사용할 수 있습니다. 를 사용하여 인스턴스를 모니터링할 수 있습니다. 예를 들어 감지된 예외 항목이 있는 이메일 보고서를 설정하거나 XML 형식의 지표 목록을 검색할 수 있습니다. 자세한 정보를 보려면 [여기를 클릭](../../production/using/monitoring-processes.md#automatic-monitoring)하십시오.

**감사 추적**

감사 추적을 사용하면 인스턴스 내의 옵션, 워크플로우 및 스키마와 관련된 변경 사항의 전체 내역을 시각화할 수 있습니다. 자세한 정보를 보려면 [여기를 클릭](../../production/using/audit-trail.md)하십시오.

**컨트롤 패널**

Campaign 컨트롤 패널에서는 인스턴스의 여러 설정을 관리할 수 있습니다.URL 권한을 관리하고, 서버의 빌드 버전 등과 같은 인스턴스 세부 정보를 확인합니다. 또한 인스턴스에 연결된 SFTP 서버의 사용 가능한 공간을 모니터링할 수도 있습니다. 자세한 정보를 보려면 [여기를 클릭](https://docs.adobe.com/content/help/ko-KR/control-panel/using/control-panel-home.html)하십시오.

>[!NOTE]
>
>Campaign 컨트롤 패널은 모든 관리 사용자가 액세스할 수 있습니다. 사용자에게 관리자 권한을 부여하는 단계는 [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=ko#discover-control-panel)에 자세히 설명되어 있습니다.
>
>인스턴스는 AWS에서 호스팅되어야 하며 최신 [Gold Standard](../../rn/using/gs-overview.md) 빌드 또는 [최신 GA 빌드(21.1)](../../rn/using/latest-release.md)로 업그레이드해야 합니다. [이 섹션](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)에서 자신의 버전을 확인하는 방법을 알아봅니다. 인스턴스가 AWS에서 호스팅되는지 확인하려면 [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)에 설명된 단계를 따르십시오.

### 워크플로우 모니터링 {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**워크플로우 열 지도**

Workflow HeatMap은 인스턴스에서 실행 중인 모든 워크플로우를 시각적으로 표시합니다. 이를 통해 인스턴스의 로드를 쉽게 모니터링하고 그에 따라 워크플로우를 계획할 수 있습니다. 자세한 정보를 보려면 [여기를 클릭](../../workflow/using/heatmap.md)하십시오.

**감사 추적**

감사 추적을 사용하면 워크플로우에서 수행된 모든 수정 사항뿐만 아니라 현재 상태를 시각화할 수 있습니다. [여기를 클릭하십시오](../../production/using/audit-trail.md).

**워크플로우 문제 해결**

워크플로우 실행과 관련된 문제가 발생할 때 특정 작업을 수행할 수 있습니다. 자세한 정보를 보려면 [여기를 클릭](../../production/using/workflow-execution.md)하십시오

**워크플로우 상태 모니터링**

또한 Heatmap에서는 워크플로우 세트의 상태를 모니터링하고 반복 메시지를 감독자에게 보낼 수 있는 워크플로우를 만들 수 있습니다. 자세한 정보를 보려면 [여기를 클릭](../../workflow/using/supervising-workflows.md)하십시오.

**일반 지침**

워크플로우를 사용할 때 다음 지침과 우수 사례를 통해 성과를 향상시킬 수 있습니다. 자세한 내용은 다음 섹션을 참조하십시오.
* [워크플로우 사용 시 모범 사례](../../workflow/using/workflow-best-practices.md)
* [워크플로우 실행 모니터링](../../workflow/using/monitoring-workflow-execution.md)

### 게재 모니터링 {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP 보고서**

SMTP 보고서는 도메인별 배달 통계와 SMTP 오류를 표시합니다. [자세히 알아보기](../../production/using/monitoring-processes.md)

**모범 사례**

[전달 전송 및 디자인에 대한 모범 사례](../../delivery/using/delivery-best-practices.md) 는 성과를 향상시키는 데 도움이 됩니다.

**배달**
문제 해결배달과 관련된 문제가 발생할 때 특정 작업을 수행할 수 있습니다.
* [전달 가능성 문제](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [이미지 표시 문제](../../production/using/image-display-issues.md)
* [전달 성능 문제](../../delivery/using/delivery-performances.md)
* [임시 파일 문제](../../production/using/temporary-files.md)  -  *온-프레미스 호스팅 모델만*

### 데이터베이스 모니터링 {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**데이터베이스 정리 워크플로우**

데이터베이스 정리 작업 과정에서는 데이터베이스에서 오래된 데이터를 삭제할 수 있습니다. 데이터베이스의 기하급수적인 증가를 피하는 것이 좋습니다. 자세한 정보를 보려면 [여기를 클릭](../../production/using/database-cleanup-workflow.md)하십시오.

**데이터베이스 성능 문제 해결**

데이터베이스 성능 문제가 발생할 때 특정 작업을 수행할 수 있습니다. 자세한 정보를 보려면 [여기를 클릭](../../production/using/database-performances.md)하십시오.

**데이터베이스 유지 관리**

*온-프레미스 및 하이브리드 호스팅 모델만 해당*

디스크 공간 과소비로 데이터베이스 액세스에 영향을 주지 않도록 정기적으로 데이터베이스 유지 관리를 수행하는 것이 좋습니다. 자세한 정보를 보려면 [여기를 클릭](../../production/using/recommendations.md)하십시오.

**백업 및 복원**

*온-프레미스 및 하이브리드 호스팅 모델만 해당*

시스템 상의 문제(물리적 또는 시스템 관련 문제)가 발생할 경우 데이터가 손실되지 않도록 백업하기 위해서는 반드시 필요합니다. 자세한 정보를 보려면 [여기를 클릭](../../production/using/backup.md)하십시오. 복원 절차는 [이 섹션](../../production/using/restoration.md)에 설명되어 있습니다.

## Campaign Classic 기술 원칙 {#campaign-classic-technical-principles}

기술 리소스는 Campaign Classic 설명서에서 확인할 수 있습니다. 인스턴스에 대한 기술 작업을 수행하기 전에 이러한 주제를 숙지하는 것이 좋습니다.

**호스팅 모델 및 기능**

* [Campaign Classic 호스팅 모델](../../installation/using/hosting-models.md)
* [호스팅 모델 기능](../../installation/using/capability-matrix.md)

**서버 구성**

*온-프레미스 및 하이브리드 호스팅 모델만 해당*

* [서버 구성](../../installation/using/configuring-campaign-server.md)
* [Serverconf.xml 파일 구성](../../installation/using/the-server-configuration-file.md)
* [서버 구성 제공](../../installation/using/email-deliverability.md)
* [인스턴스를 만들고 데이터베이스를 선언할 명령줄](../../installation/using/command-lines.md)

**일반 원칙**

* [Campaign Classic 아키텍처](../../production/using/general-architecture.md)
* [Campaign Classic 모듈](../../production/using/operating-principle.md)
* [Campaign Classic 옵션](../../installation/using/configuring-campaign-options.md)
* [모듈의 자동 시작 설정 방법](../../production/using/administration.md)
* [캠페인 구성 원칙](../../production/using/configuration-principle.md)
* [문제 해결 절차](../../production/using/performance-and-throughput-issues.md)
