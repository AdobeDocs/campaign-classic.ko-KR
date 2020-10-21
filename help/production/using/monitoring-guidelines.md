---
title: 모니터링 지침
description: Campaign 인스턴스 및 프로세스를 모니터링하기 위한 지침과 모범 사례를 알아봅니다.
page-status-flag: never-activated
uuid: cf0d782d-47bf-40ae-ab6f-d1d47fa15792
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: 8b33e6af-15c3-4b30-8ad6-d76a1f33be21
translation-type: tm+mt
source-git-commit: 3acf2359c74a3dc4b18c8976fee14dcbaf3fa510
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 7%

---


# 모니터링 지침 {#monitoring-guidelines}

## 인스턴스 모니터링 대시보드 {#instance-monitoring-dashboard}

Campaign Classic 홈 페이지에서 액세스할 수 있는 **[!UICONTROL Monitoring]** 탭은 인스턴스를 모니터링하는 데 도움이 되는 기본 시작 지점입니다.

이 대시보드는 인스턴스에서 발생하는 사항에 대한 대시보드를 제공합니다.상태(빌드 버전, 설치된 패키지 등), 시스템 표시기, 로그, 현재 실행 중인 워크플로우, 마지막 전송 상태 등

자세한 정보는 [여기](../../production/using/monitoring-processes.md)에서 확인할 수 있습니다.

![](assets/monitoring_tab.png)

## Monitoring Campaign Classic processes {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">인스턴스 모니터링</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#moniroting-workflows">워크플로우 모니터링</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">전달 모니터링</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">데이터베이스 모니터링</a></p></td></tr>
</table>

다른 캠페인 프로세스를 모니터링하는 추가 방법을 사용할 수 있습니다. 이러한 기능은 여러 가지 방법으로 인스턴스를 모니터링하여 시스템이 건강한지 확인하고 워크플로우 설정, 배달 전송 등에서 발생할 수 있는 문제를 최종적으로 해결할 수 있습니다.

### 인스턴스 모니터링 {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**자동 모니터링 툴**

몇 가지 자동 방법을 사용할 수 있습니다. 를 사용하여 인스턴스를 모니터링할 수 있습니다. 예를 들어, 검색된 예외 항목이 있는 이메일 보고서를 설정하고, XML 형식의 지표 목록을 검색하는 등의 작업을 할 수 있습니다. [자세한 내용을 보려면 여기를](../../production/using/monitoring-processes.md#automatic-monitoring) 클릭하십시오.

**감사 추적**

감사 추적을 사용하면 인스턴스 내의 옵션, 워크플로우 및 스키마와 관련된 변경 사항의 전체 내역을 시각화할 수 있습니다. [자세한 내용을 보려면 여기를](../../production/using/audit-trail.md) 클릭하십시오.

**컨트롤 패널**

Campaign 컨트롤 패널을 사용하면 인스턴스의 여러 설정을 관리할 수 있습니다.URL 권한을 관리하고 서버의 빌드 버전 등과 같은 인스턴스 세부 정보를 확인합니다. 또한 인스턴스에 연결된 SFTP 서버의 사용 가능한 공간을 모니터링할 수 있습니다. [자세한 내용을 보려면 여기를](https://docs.adobe.com/content/help/ko-KR/control-panel/using/control-panel-home.html) 클릭하십시오.

>[!NOTE]
>
>Campaign 컨트롤 패널은 관리 사용자에게만 액세스 가능하며 Adobe Managed Services를 사용하는 모든 고객은 사용할 수 있습니다.

### 워크플로우 모니터링 {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**워크플로우 열 지도**

Workflow HeatMap은 인스턴스에서 실행 중인 모든 워크플로우를 시각적으로 표시합니다. 이를 통해 인스턴스의 로드를 쉽게 모니터링하고 그에 따라 워크플로우를 계획할 수 있습니다. [자세한 내용을 보려면 여기를](../../workflow/using/heatmap.md) 클릭하십시오.

**감사 추적**

감사 추적을 사용하면 워크플로우에서 수행한 모든 수정 사항뿐만 아니라 현재 상태를 시각화할 수 있습니다. [여기를 클릭하십시오](../../production/using/audit-trail.md).

**워크플로우 문제 해결**

워크플로우 실행과 관련된 문제가 발생할 때 특정 작업을 수행할 수 있습니다. [자세한 내용을 보려면 여기를](../../production/using/workflow-execution.md) 클릭하십시오.

**워크플로우 상태 모니터링**

또한 Heatmap을 통해 워크플로우 세트를 모니터링하고 반복적인 메시지를 감독자에게 전송할 수 있는 워크플로우를 만들 수 있습니다. [자세한 내용을 보려면 여기를](../../workflow/using/supervising-workflows.md) 클릭하십시오.

**일반 지침**

워크플로우를 사용할 때 다음 지침과 우수 사례를 통해 성과를 향상시킬 수 있습니다. 자세한 내용은 다음 섹션을 참조하십시오.
* [워크플로우 사용 시 모범 사례](../../workflow/using/workflow-best-practices.md)
* [워크플로우 실행 모니터링](../../workflow/using/monitoring-workflow-execution.md)

### 게재 모니터링 {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP 보고서**

SMTP 보고서는 도메인별 배달 통계 및 SMTP 오류를 표시합니다. [자세히 알아보기](../../production/using/monitoring-processes.md)

**모범 사례**

[전송 및 디자인에](../../delivery/using/delivery-best-practices.md) 대한 모범 사례를 통해 이들의 성과를 향상시킬 수 있습니다.

**배달 문제 해결**&#x200B;과 관련된 문제가 발생할 때 특정 작업을 수행할 수 있습니다.
* [전달 가능성 문제](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [이미지 표시 문제](../../production/using/image-display-issues.md)
* [전달 성능 문제](../../delivery/using/monitoring-a-delivery.md#performance_issues)
* [임시 파일 문제](../../production/using/temporary-files.md) - *온-프레미스 호스팅 모델만*

### 데이터베이스 모니터링 {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**데이터베이스 정리 워크플로우**

데이터베이스 정리 작업 과정을 사용하면 데이터베이스에서 오래된 데이터를 삭제할 수 있습니다. 데이터베이스의 기하급수적인 증가를 피하는 것이 좋습니다. [자세한 내용을 보려면 여기를](../../production/using/database-cleanup-workflow.md) 클릭하십시오.

**데이터베이스 성능 문제 해결**

데이터베이스 성능 문제가 발생할 때 특정 작업을 수행할 수 있습니다. [자세한 내용을 보려면 여기를](../../production/using/database-performances.md) 클릭하십시오.

**데이터베이스 유지 관리**

*온-프레미스 및 하이브리드 호스팅 모델만 해당*

디스크 공간 과소비로 데이터베이스 액세스에 영향을 주지 않도록 정기적으로 데이터베이스 유지 관리를 수행하는 것이 좋습니다. [자세한 내용을 보려면 여기를](../../production/using/recommendations.md) 클릭하십시오.

**백업 및 복원**

*온-프레미스 및 하이브리드 호스팅 모델만 해당*

시스템 상의 문제(물리적 또는 시스템 관련 문제)가 발생하는 경우 데이터가 손실되지 않도록 백업하려면 반드시 필요합니다. [자세한 내용을 보려면 여기를](../../production/using/backup.md) 클릭하십시오. 복원 절차는 [이 섹션에 설명되어 있습니다](../../production/using/restoration.md).

## Campaign Classic 기술 원칙 {#campaign-classic-technical-principles}

기술 리소스는 Campaign Classic 문서에서 제공됩니다. 인스턴스에 대한 기술 작업을 수행하기 전에 이러한 주제를 숙지하는 것이 좋습니다.

**호스팅 모델 및 기능**

* [Campaign Classic 호스팅 모델](../../installation/using/hosting-models.md)
* [호스팅 모델 기능](../../installation/using/capability-matrix.md)

**서버 구성**

*온-프레미스 및 하이브리드 호스팅 모델만 해당*

* [필수 서버 구성](../../installation/using/campaign-server-configuration.md)
* [Serverconf.xml 파일 구성](../../installation/using/the-server-configuration-file.md)
* [전달을 위한 서버 구성](../../installation/using/email-deliverability.md)
* [인스턴스를 만들고 데이터베이스를 선언할 명령줄](../../installation/using/command-lines.md)

**일반 원칙**

* [Campaign Classic 건축](../../production/using/general-architecture.md)
* [Campaign Classic 모듈](../../production/using/operating-principle.md)
* [Campaign Classic 옵션](../../installation/using/configuring-campaign-options.md)
* [모듈의 자동 시작 설정 방법](../../production/using/administration.md)
* [캠페인 구성 원칙](../../production/using/configuration-principle.md)
* [문제 해결 절차](../../production/using/performance-and-throughput-issues.md)
