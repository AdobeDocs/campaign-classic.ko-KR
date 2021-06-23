---
product: campaign
title: Adobe Campaign Classic에서 게재 기능 모니터링
description: Adobe Campaign Classic의 게재 기능 모니터링에 대한 도구 및 지침에 대해 알아봅니다.
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 2%

---

# 전달성 모니터링{#monitoring-deliverability}

아래에 Adobe Campaign에서 제공하는 다양한 모니터링 도구에 대한 자세한 내용과, 플랫폼의 게재 기능을 모니터링하기 위해 Adobe Campaign에서 제공하는 기능을 활용하는 데 대한 몇 가지 추가 지침이 있습니다.

## 게재 기능 모니터링 {#configuration}

이 기능은 Adobe Campaign의 전용 패키지를 통해 사용할 수 있습니다. 사용하려면 이 패키지를 설치해야 합니다. 완료되면 패키지를 고려할 서버를 다시 시작합니다.
* 호스팅 및 하이브리드 클라이언트의 경우, **게재 기능 모니터링**&#x200B;이 Adobe 기술 지원 및 컨설턴트에 의해 인스턴스에 구성됩니다. 자세한 내용은 Adobe 계정 담당자에게 문의하십시오.

* 온-프레미스 설치의 경우 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 메뉴를 통해 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 패키지를 설치해야 합니다. 자세한 내용은 [Campaign Classic 표준 패키지 설치](../../installation/using/installing-campaign-standard-packages.md)를 참조하십시오.

Adobe Campaign Classic에서 **게재 기능 모니터링**&#x200B;은 **[!UICONTROL Refresh for deliverability]** 워크플로우에서 관리합니다. 기본적으로 모든 인스턴스에 설치되어 있으며 반송 메일 자격 규칙 목록, 도메인 목록 및 MX 목록을 초기화할 수 있습니다. **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 패키지가 설치되면 이 워크플로우는 매일 밤 실행되어 규칙 목록을 정기적으로 업데이트하고 플랫폼 게재 능력을 능동적으로 관리할 수 있습니다.

게재 기능 패키지를 통해 다음 항목에 액세스할 수 있습니다.

* 컨텐츠 및 평판을 스캔하기 위해 주요 이메일 클라이언트에서 메시지를 미리 볼 수 있는 [받은 편지함 렌더링 보고서](inbox-rendering.md)입니다.
* 메시지 품질 개요(받은 편지함, 스팸).

## 모니터링 도구 {#monitoring-tools}

다음 도구를 사용할 수도 있습니다.

* **[!UICONTROL Delivery throughput]** 보고서는 지정된 기간 동안 전체 플랫폼의 처리량에 대한 개요를 제공합니다. 자세한 내용은 [이 섹션](../../reporting/using/global-reports.md#delivery-throughput)을 참조하십시오.
* 각 게재는 서로 다른 인터넷 서비스 공급자(ISP)에 대한 브로드캐스트 통계 보고서를 생성합니다. 다음 숫자를 포함하여 게재 능력에 영향을 줄 수 있는 몇 가지 데이터 품질 및 평판 지표를 보여줍니다.
   * **[!UICONTROL Hard bounces]** 데이터 품질을 나타냅니다. 이 숫자는 2% 미만이어야 합니다.
   * **[!UICONTROL Soft bounces]** 평판 표시 이 숫자는 지정된 ISP의 경우 10%보다 크지 않아야 합니다.

   자세한 내용은 [게재 통계](../../reporting/using/global-reports.md#delivery-statistics) 섹션을 참조하십시오.
* 일반적으로 [게재 대시보드](about-delivery-monitoring.md)는 다음 항목에 액세스할 수 있도록 합니다.
   * [게재 요약](delivery-dashboard.md#delivery-summary)을(를) 참조하십시오.
   * 제외된 타겟 및 그 이유를 보여주는 [게재 로그 및 기록](delivery-dashboard.md#delivery-logs-and-history);
   * 열기 및 클릭과 같은 추적 정보를 표시하는 [추적 로그](delivery-dashboard.md#tracking-logs)입니다.

## 모니터링 지침 {#monitoring-guidelines}

다음은 게재 기능 모니터링에 대한 몇 가지 추가 지침입니다.

* 전체 플랫폼에 대한 [게재 처리량](../../reporting/using/global-reports.md#delivery-throughput)을 정기적으로 확인하여 원래 설정과 일치하는지 확인합니다.
* [다시 시도](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)가 게재 템플릿에서 올바르게 설정되었는지(다시 시도 기간은 30분, 20번 이상 다시 시도) 확인합니다.
* [바운스](understanding-delivery-failures.md#bounce-mail-management) 사서함이 액세스할 수 있고 계정이 만료되지 않았는지 정기적으로 확인합니다.
* [게재 대시보드](delivery-dashboard.md)에서 액세스할 수 있는 각 게재 처리량을 확인하여 게재 컨텐츠의 유효성(예:&#39;플래시 판매&#39;는 며칠이 아니라 몇 분 안에 배달되어야 합니다.
* [waves](steps-sending-the-delivery.md#sending-using-multiple-waves)를 사용할 때 다음 웨이브가 트리거되기 전에 각 웨이브를 완료할 시간이 충분한지 확인합니다.
* 오류 수 및 새 [격리](understanding-quarantine-management.md)가 다른 게재와 일치하는지 확인합니다.
* 강조 표시된 오류 유형(차단 목록, DNS 문제, 스팸 방지 규칙 등)을 확인하려면 [게재 로그](delivery-dashboard.md#delivery-logs-and-history)를 자세히 참조하십시오.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
