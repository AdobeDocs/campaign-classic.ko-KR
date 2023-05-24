---
product: campaign
title: Adobe Campaign의 전달성 모니터링
description: Adobe Campaign의 전달성 모니터링에 대한 도구 및 지침에 대해 알아봅니다
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 1%

---

# 게재 가능성 모니터링{#monitoring-deliverability}



아래에서는 Adobe Campaign에서 제공하는 다양한 모니터링 도구에 대한 세부 정보와 Adobe Campaign에서 제공하는 기능을 활용하여 플랫폼의 전달성을 모니터링하는 방법에 대한 몇 가지 추가 지침을 확인할 수 있습니다.

## 게재 기능 모니터링 정보 {#about-deliverability-monitoring}

이 기능은 Adobe Campaign의 전용 패키지를 통해 사용할 수 있습니다. 사용하려면 이 패키지를 설치해야 합니다. 작업이 완료되면 패키지를 고려하기 위해 서버를 다시 시작합니다.
* 호스팅 및 하이브리드 클라이언트의 경우, **게재 가능성 모니터링** 는 Adobe 기술 지원 및 컨설턴트에 의해 인스턴스에 구성됩니다. 자세한 내용은 Adobe 계정 담당자에게 문의하십시오.

* 온-프레미스 설치의 경우 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 를 통한 패키지 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 메뉴 아래의 제품에서 사용할 수 있습니다. 자세한 내용은 [Campaign Classic 표준 패키지 설치](../../installation/using/installing-campaign-standard-packages.md).

Adobe Campaign Classic, **게재 가능성 모니터링** 에서 관리함 **[!UICONTROL Refresh for deliverability]** 워크플로입니다. 모든 인스턴스에 기본적으로 설치되며 바운스 메일 자격 규칙 목록, 도메인 목록 및 MX 목록을 초기화할 수 있습니다. 한 번 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 패키지가 설치되었습니다. 이 워크플로우는 매일 밤 실행되어 규칙 목록을 정기적으로 업데이트하며 플랫폼 전달성을 능동적으로 관리할 수 있습니다.

게재 기능 패키지를 통해 다음에 액세스할 수 있습니다.

* 다음 [받은 편지함 렌더링 보고서](inbox-rendering.md) 주요 이메일 클라이언트에서 메시지를 미리 보고 콘텐츠와 평판을 스캔할 수 있습니다.
* 메시지 품질 개요(받은 편지함, 스팸).

## 모니터링 도구 {#monitoring-tools}

다음 도구를 사용할 수도 있습니다.

* 다음 **[!UICONTROL Delivery throughput]** 보고서는 주어진 기간 동안 전체 플랫폼의 처리량에 대한 개요를 제공합니다. 자세한 내용은 [이 섹션](../../reporting/using/global-reports.md#delivery-throughput)을 참조하십시오.
* 각 게재는 다른 인터넷 서비스 공급자(ISP)에 대한 브로드캐스트 통계 보고서를 생성합니다. 다음 숫자를 포함하여 전달성에 영향을 줄 수 있는 일부 데이터 품질 및 신뢰도 지표를 표시합니다.
   * **[!UICONTROL Hard bounces]** 데이터 품질을 나타냅니다. 이 숫자는 2% 미만이어야 합니다.
   * **[!UICONTROL Soft bounces]** 평판을 나타냅니다. 이 숫자는 특정 ISP의 경우 10%보다 커서는 안 됩니다.

   자세한 내용은 [게재 통계](../../reporting/using/global-reports.md#delivery-statistics) 섹션.
* 일반적으로 [게재 대시보드](about-delivery-monitoring.md) 에 대한 액세스 권한을 부여합니다.
   * 다음 [게재 요약](delivery-dashboard.md#delivery-summary), 전송 세부 정보 및 정상적으로 전송, 처리 및 전송된 메시지 수를 보여 줍니다.
   * 다음 [게재 로그 및 내역](delivery-dashboard.md#delivery-logs-and-history): 제외된 타겟 및 이유를 보여 줍니다.
   * 다음 [추적 로그](delivery-dashboard.md#tracking-logs): 열림 및 클릭과 같은 추적 정보를 표시합니다.

## 모니터링 지침 {#monitoring-guidelines}

다음은 게재 가능성 모니터링에 대한 몇 가지 추가 지침입니다.

* 다음을 정기적으로 확인합니다. [게재 처리량](../../reporting/using/global-reports.md#delivery-throughput) 전체 플랫폼이 원본 설정과 일치하는지 확인합니다.
* 다음을 확인: [다시 시도](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) 게재 템플릿에서 올바르게 설정됩니다(재시도 기간: 30분, 20회 이상 재시도).
* 정기적으로 다음을 확인합니다. [바운스](understanding-delivery-failures.md#bounce-mail-management) 사서함에 액세스할 수 있으며 계정이 곧 만료되지 않습니다.
* 다음에서 액세스할 수 있는 각 게재 처리량 확인 [게재 대시보드](delivery-dashboard.md)를 사용하여 게재 콘텐츠의 유효성과 일치하는지 확인합니다(예: &#39;플래시 판매&#39;는 일 수가 아닌 분 단위로 제공되어야 함).
* 사용 시 [예약된 일괄 처리](steps-sending-the-delivery.md#sending-using-multiple-waves)를 클릭하고, 각 웨이브가 다음 웨이브가 트리거되기 전에 완료할 시간이 충분한지 확인합니다.
* 오류 및 새 항목 수를 확인합니다. [격리](understanding-quarantine-management.md) 다른 게재와 일치합니다.
* 다음을 주의 깊게 참조하십시오. [게재 로그](delivery-dashboard.md#delivery-logs-and-history) 강조 표시된 오류 유형(차단 목록, DNS 문제, 스팸 방지 규칙 등)을 확인하는 세부 정보입니다.
