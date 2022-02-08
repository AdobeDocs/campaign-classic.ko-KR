---
product: campaign
title: Adobe Campaign Classic에서 게재 기능 모니터링
description: Adobe Campaign Classic의 게재 기능 모니터링에 대한 도구 및 지침에 대해 알아봅니다.
feature: Deliverability
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 1%

---

# 게재 기능 모니터링{#monitoring-deliverability}

![](../../assets/common.svg)

아래에 Adobe Campaign에서 제공하는 다양한 모니터링 도구에 대한 자세한 내용과, 플랫폼의 게재 기능을 모니터링하기 위해 Adobe Campaign에서 제공하는 기능을 활용하는 데 대한 몇 가지 추가 지침이 있습니다.

## 게재 기능 모니터링 기본 정보 {#about-deliverability-monitoring}

이 기능은 Adobe Campaign의 전용 패키지를 통해 사용할 수 있습니다. 사용하려면 이 패키지를 설치해야 합니다. 완료되면 패키지를 고려할 서버를 다시 시작합니다.
* 호스팅 및 하이브리드 클라이언트의 경우, **게재 기능 모니터링** Adobe 기술 지원 및 컨설턴트가 인스턴스에 구성합니다. 자세한 내용은 Adobe 계정 담당자에게 문의하십시오.

* 온-프레미스 설치의 경우 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 를 통해 패키지 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 메뉴 아래의 제품에서 사용할 수 있습니다. 자세한 내용은 [Campaign Classic 표준 패키지 설치](../../installation/using/installing-campaign-standard-packages.md).

Adobe Campaign Classic에서, **게재 기능 모니터링** 는 **[!UICONTROL Refresh for deliverability]** 워크플로우. 기본적으로 모든 인스턴스에 설치되어 있으며 반송 메일 자격 규칙 목록, 도메인 목록 및 MX 목록을 초기화할 수 있습니다. 한 번 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 패키지가 설치되고 이 워크플로우는 매일 밤 실행되어 규칙 목록을 정기적으로 업데이트하고 플랫폼 게재 기능을 능동적으로 관리할 수 있습니다.

게재 기능 패키지를 통해 다음 항목에 액세스할 수 있습니다.

* 다음 [받은 편지함 렌더링 보고서](inbox-rendering.md) 콘텐츠와 평판을 스캔하기 위해 주요 이메일 클라이언트에서 메시지를 미리 볼 수 있도록 합니다.
* 메시지 품질 개요(받은 편지함, 스팸).

## 모니터링 도구 {#monitoring-tools}

다음 도구를 사용할 수도 있습니다.

* 다음 **[!UICONTROL Delivery throughput]** 보고서는 특정 기간 동안의 전체 플랫폼 처리량에 대한 개요를 제공합니다. 자세한 내용은 [이 섹션](../../reporting/using/global-reports.md#delivery-throughput)을 참조하십시오.
* 각 게재는 서로 다른 인터넷 서비스 공급자(ISP)에 대한 브로드캐스트 통계 보고서를 생성합니다. 다음 숫자를 포함하여 게재 능력에 영향을 줄 수 있는 몇 가지 데이터 품질 및 평판 지표를 보여줍니다.
   * **[!UICONTROL Hard bounces]** 데이터 품질을 나타냅니다. 이 숫자는 2% 미만이어야 합니다.
   * **[!UICONTROL Soft bounces]** 평판 표시 이 숫자는 지정된 ISP의 경우 10%보다 크지 않아야 합니다.

   자세한 내용은 [게재 통계](../../reporting/using/global-reports.md#delivery-statistics) 섹션을 참조하십시오.
* 일반적으로 [게재 대시보드](about-delivery-monitoring.md) 다음 항목에 액세스할 수 있습니다.
   * a [게재 요약](delivery-dashboard.md#delivery-summary)- 전송 세부 사항과 성공을 통해 전송, 처리 및 전송할 메시지 수를 보여줍니다.
   * a [게재 로그 및 내역](delivery-dashboard.md#delivery-logs-and-history): 제외된 타겟 및 그 이유를 보여 줍니다.
   * a [추적 로그](delivery-dashboard.md#tracking-logs)- 열기 또는 클릭과 같은 추적 정보를 표시합니다.

## 모니터링 지침 {#monitoring-guidelines}

다음은 게재 기능 모니터링에 대한 몇 가지 추가 지침입니다.

* 정기적으로 [게재 처리량](../../reporting/using/global-reports.md#delivery-throughput) 를 사용하도록 를 설정합니다.
* 확인 [다시 시도](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) 게재 템플릿에서 올바르게 설정(다시 시도 기간의 경우 30분, 20회 이상 다시 시도)됩니다.
* 정기적으로 [바운스](understanding-delivery-failures.md#bounce-mail-management) 사서함에 액세스할 수 있으며 계정이 만료되지 않도록 설정되어 있습니다.
* 각 게재 처리량을 확인하여 [게재 대시보드](delivery-dashboard.md)를 전달하는 컨텐츠의 유효성(예: &#39;플래시 판매&#39;는 며칠이 아니라 몇 분 안에 배달되어야 합니다.
* 사용 시 [파도](steps-sending-the-delivery.md#sending-using-multiple-waves)를 설정하는 경우 다음 웨이브가 트리거되기 전에 각 웨이브를 완료할 시간이 충분한지 확인합니다.
* 오류 수와 새 오류 수를 확인합니다 [격리](understanding-quarantine-management.md) 은 다른 게재와 일치합니다.
* 자세한 내용은 [게재 로그](delivery-dashboard.md#delivery-logs-and-history) 강조 표시된 오류 유형(차단 목록, DNS 문제, 스팸 방지 규칙 등)을 자세히 확인합니다.
