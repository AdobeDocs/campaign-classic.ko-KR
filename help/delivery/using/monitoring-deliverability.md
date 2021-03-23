---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic의 모니터링 제공
description: Adobe Campaign Classic의 전달 기능 모니터링에 대한 도구 및 지침을 살펴보십시오.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 5d1a653a9a164c34bb70efcc86ff2d7bdf1130a2
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 2%

---


# 게재 기능 모니터링{#monitoring-deliverability}

아래에서 Adobe Campaign에서 제공하는 다양한 모니터링 도구에 대한 자세한 내용뿐만 아니라 Adobe Campaign에서 제공하는 기능을 활용하여 플랫폼의 제공 여부를 모니터링할 수 있는 몇 가지 추가 지침을 확인할 수 있습니다.

## 게재 기능 모니터링 {#configuration}

이 기능은 Adobe Campaign의 전용 패키지를 통해 사용할 수 있습니다. 이 패키지를 사용하려면 이 패키지를 설치해야 합니다. 작업이 완료되면 패키지를 고려하여 서버를 다시 시작합니다.
* 호스팅된 클라이언트와 하이브리드 클라이언트의 경우, **수신 가능성 모니터링**&#x200B;은 Adobe 기술 지원 및 컨설턴트가 사용자 인스턴스에 구성합니다. 자세한 내용은 Adobe 계정 담당자에게 문의하십시오.

* 온-프레미스 설치의 경우 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 메뉴를 통해 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 패키지를 설치해야 합니다. 자세한 내용은 [Campaign Classic 표준 패키지 설치](../../installation/using/installing-campaign-standard-packages.md)를 참조하십시오.

Adobe Campaign Classic에서 **배달 가능 모니터링**&#x200B;은 **[!UICONTROL Refresh for deliverability]** 작업 과정에서 관리됩니다. 기본적으로 모든 인스턴스에 설치되며 바운스 메일 자격 규칙 목록, 도메인 목록 및 MX 목록을 초기화할 수 있습니다. **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 패키지가 설치되면 이 워크플로우는 매일 밤 실행되어 규칙 목록을 정기적으로 업데이트하고 플랫폼 제공 기능을 능동적으로 관리할 수 있습니다.

제공 패키지는 다음 항목에 대한 액세스 권한을 제공합니다.

* 컨텐트 및 명성을 스캔하기 위해 주요 이메일 클라이언트에서 메시지를 미리 볼 수 있는 [받은 편지함 렌더링 보고서](../../delivery/using/inbox-rendering.md).
* 메시지 품질 개요(받은 편지함, 스팸).

## 모니터링 도구 {#monitoring-tools}

다음 도구를 사용할 수도 있습니다.

* **[!UICONTROL Delivery throughput]** 보고서는 지정된 기간 동안 전체 플랫폼의 처리량에 대한 개요를 제공합니다. 자세한 내용은 [이 섹션](../../reporting/using/global-reports.md#delivery-throughput)을 참조하십시오.
* 각 배달은 서로 다른 인터넷 서비스 공급자(ISP)에 대한 브로드캐스트 통계 보고서를 생성합니다. 다음 수를 포함하여, 배달능력에 영향을 줄 수 있는 데이터 품질 및 평판 지표를 보여줍니다.
   * **[!UICONTROL Hard bounces]** 데이터 품질을 나타냅니다. 이 숫자는 2% 미만이어야 합니다.
   * **[!UICONTROL Soft bounces]** 명성에 대한 정보를 표시합니다. 지정된 ISP의 경우 이 숫자는 10%보다 크면 안 됩니다.

   자세한 내용은 [배달 통계](../../reporting/using/global-reports.md#delivery-statistics) 섹션을 참조하십시오.
* 일반적으로 [배달 대시보드](../../delivery/using/about-delivery-monitoring.md)에서는 다음에 액세스할 수 있습니다.
   * 전송 세부 사항과 전송, 처리 및 성공적으로 보낼 메시지 수를 보여주는 [배달 요약](../../delivery/using/delivery-dashboard.md#delivery-summary);
   * [배달 로그 및 내역](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)(제외된 대상 및 그 이유를 표시);
   * 열기 및 클릭과 같은 추적 정보를 표시하는 [추적 로그](../../delivery/using/delivery-dashboard.md#tracking-logs)입니다.

## 모니터링 지침 {#monitoring-guidelines}

다음은 제공 가능성 모니터링에 대한 몇 가지 추가 지침입니다.

* 전체 플랫폼에 대해 [배달 처리량](../../reporting/using/global-reports.md#delivery-throughput)을 정기적으로 확인하여 원래 설정과 일치하는지 확인합니다.
* 배달 템플릿에서 [재시도](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)이(가) 올바르게 설정되어 있는지 확인합니다(재시도 기간은 30분, 20회 이상).
* [bounce](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) 사서함에 액세스할 수 있으며 계정이 만료되지 않도록 정기적으로 확인합니다.
* [배달 대시보드](../../delivery/using/delivery-dashboard.md)에서 액세스할 수 있는 각 배달 처리량을 확인하여 배달 컨텐츠의 유효성과 일치하는지 확인합니다(예:&#39;flash sales&#39;는 며칠이 아니라 몇 분 내에 배달됩니다.)
* [waves](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)를 사용할 때 다음 웨이브가 트리거되기 전에 각 웨이브가 완료하기에 충분한 시간이 있는지 확인합니다.
* 오류 수와 새 [검역소](../../delivery/using/understanding-quarantine-management.md)가 다른 배달물과 일치하는지 확인합니다.
* 강조 표시된 오류 유형(차단 목록, DNS 문제, 스팸 방지 규칙 등)을 확인하려면 [배달 로그](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)을 자세히 참조하십시오.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
