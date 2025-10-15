---
product: campaign
title: Adobe Campaign의 전달성 모니터링
description: Adobe Campaign의 전달성 모니터링에 대한 도구 및 지침에 대해 알아봅니다
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Deliverability
role: User, Admin
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 1%

---

# 게재 가능성 모니터링{#monitoring-deliverability}

아래에서는 Adobe Campaign에서 제공하는 다양한 모니터링 도구에 대한 세부 정보와 Adobe Campaign에서 제공하는 기능을 활용하여 플랫폼의 전달성을 모니터링하는 방법에 대한 몇 가지 추가 지침을 확인할 수 있습니다.

## 게재 기능 모니터링 정보 {#about-deliverability-monitoring}

이 기능은 Adobe Campaign의 전용 패키지를 통해 사용할 수 있습니다. 사용하려면 이 패키지를 설치해야 합니다. 작업이 완료되면 패키지를 고려하기 위해 서버를 다시 시작합니다.
* 호스팅 및 하이브리드 클라이언트의 경우 Adobe 기술 지원 및 컨설턴트가 인스턴스에 **게재 가능성 모니터링**&#x200B;을(를) 구성합니다. 자세한 내용은 Adobe 계정 담당자에게 문의하십시오.

* 온-프레미스 설치의 경우 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** > **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** 메뉴를 통해 **[!UICONTROL Import package]** 패키지를 설치해야 합니다. 자세한 내용은 [Campaign Classic 표준 패키지 설치](../../installation/using/installing-campaign-standard-packages.md)를 참조하십시오.

Adobe Campaign Classic에서 **게재 가능성 모니터링**&#x200B;은(는) **[!UICONTROL Refresh for deliverability]** 워크플로우에서 관리합니다. 모든 인스턴스에 기본적으로 설치되며 바운스 메일 자격 규칙 목록, 도메인 목록 및 MX 목록을 초기화할 수 있습니다. **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 패키지가 설치되면 이 워크플로가 매일 밤 실행되어 규칙 목록을 정기적으로 업데이트하며 플랫폼 전달성을 능동적으로 관리할 수 있습니다.

게재 기능 패키지를 통해 다음에 액세스할 수 있습니다.

* [받은 편지함 렌더링 보고서](inbox-rendering.md)로, 콘텐츠와 평판을 검사하기 위해 주요 전자 메일 클라이언트에서 메시지를 미리 볼 수 있습니다.
* 메시지 품질 개요(받은 편지함, 스팸).

## 모니터링 도구 {#monitoring-tools}

다음 도구를 사용할 수도 있습니다.

* **[!UICONTROL Delivery throughput]** 보고서는 지정된 기간 동안 전체 플랫폼의 처리량에 대한 개요를 제공합니다. 자세한 내용은 [이 섹션](../../reporting/using/global-reports.md#delivery-throughput)을 참조하십시오.
* 각 게재는 다른 인터넷 서비스 공급자(ISP)에 대한 브로드캐스트 통계 보고서를 생성합니다. 다음 숫자를 포함하여 전달성에 영향을 줄 수 있는 일부 데이터 품질 및 신뢰도 지표를 표시합니다.
   * **[!UICONTROL Hard bounces]**&#x200B;은(는) 데이터 품질을 나타냅니다. 이 숫자는 2% 미만이어야 합니다.
   * **[!UICONTROL Soft bounces]**&#x200B;은(는) 평판을 나타냅니다. 이 숫자는 특정 ISP의 경우 10%보다 커서는 안 됩니다.

  자세한 내용은 [게재 통계](../../reporting/using/global-reports.md#delivery-statistics) 섹션을 참조하십시오.
* 일반적으로 [게재 대시보드](about-delivery-monitoring.md)를 통해 다음에 액세스할 수 있습니다.
   * 전송 세부 정보 및 전송, 처리 및 전송 완료 시 보낼 메시지 수를 보여 주는 [게재 요약](delivery-dashboard.md#delivery-summary);
   * 제외된 대상 및 이유를 보여 주는 [게재 로그 및 기록](delivery-dashboard.md#delivery-logs-and-history);
   * 열기 및 클릭 수와 같은 추적 정보를 표시하는 [추적 로그](delivery-dashboard.md#tracking-logs).

## 모니터링 지침 {#monitoring-guidelines}

다음은 게재 가능성 모니터링에 대한 몇 가지 추가 지침입니다.

* 전체 플랫폼에 대한 [게재 처리량](../../reporting/using/global-reports.md#delivery-throughput)을(를) 정기적으로 확인하여 원본 설정과 일치하는지 확인하십시오.
* 게재 템플릿에 [다시 시도](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)가 올바르게 설정되었는지(다시 시도 기간 30분 및 20번 이상 다시 시도) 확인하십시오.
* [바운스](understanding-delivery-failures.md#bounce-mail-management) 사서함에 액세스할 수 있고 계정이 곧 만료되지 않는지 정기적으로 확인하십시오.
* [게재 대시보드](delivery-dashboard.md)에서 액세스할 수 있는 각 게재 처리량을 확인하여 게재 콘텐츠의 유효성과 일치하는지 확인합니다(예: &#39;플래시 판매&#39;는 일 수가 아닌 분 단위로 제공되어야 함).
* 웨이브를 사용할 때 다음 웨이브가 트리거되기 전에 각 웨이브가 완료되기에 충분한 시간이 있는지 확인합니다. [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/configure-and-send.html?lang=ko#sending-using-multiple-waves){target="_blank"}를 참조하세요.
* 오류 수와 새 [격리](understanding-quarantine-management.md)이(가) 다른 게재와 일치하는지 확인하십시오.
* 강조 표시된 오류 종류(차단 목록, DNS 문제, 스팸 방지 규칙 등)를 확인하려면 [게재 로그](delivery-dashboard.md#delivery-logs-and-history)를 자세히 참조하세요.
