---
product: campaign
title: 게재 모니터링 시작
description: Campaign Classic 게재 모니터링 기능에 대해 자세히 알아보기
feature: Monitoring, Deliverability
role: User
exl-id: 9ce11da0-e37b-459e-8ec7-d2bddf59bdf7
source-git-commit: e60a8391416bc9899548971bddb61705467a80e5
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 1%

---

# 게재 모니터링 시작 {#about-delivery-monitoring}

>[!IMPORTANT]
>
>이 페이지에서는 하이브리드 및 온-프레미스 배포에 대한 **Campaign Classic v7 관련 모니터링 기능**&#x200B;을 설명합니다.

## 모니터링 기능

### 게재 모니터링 {#monitoring-deliveries}

**Campaign Classic v7 하이브리드/온-프레미스 배포의 경우**&#x200B;서버 리소스 및 MTA(메일 전송 에이전트) 구성에 대한 추가 모니터링이 필요합니다.

#### 보류 중인 게재 문제 해결 {#pending-deliveries}

게재가 전송되지 않고 상태가 **보류 중**&#x200B;인 경우 어떻게 합니까?

* 실행 프로세스에서 일부 리소스를 사용할 수 있을 때까지 기다리고 있습니다. MTA가 시작되지 않았을 수 있습니다.
mta@instance 모듈이 MTA 서버에서 시작되었는지 확인하고 필요한 경우 MTA 모듈을 시작합니다. [자세히 알아보기](../../production/using/administration.md)

* 게재는 전송 인스턴스에 구성되지 않은 선호도를 사용하고 있을 수 있습니다.
팁: 트래픽 관리(IP 선호도) 구성을 확인하십시오. 자세한 내용은 발신 SMTP 트래픽 제어 를 참조하십시오.

>[!NOTE]
>
>이러한 단계는 전문가 사용자의 온-프레미스 설치에서만 수행할 수 있습니다.

### 게재 가능성 모니터링 {#deliverability-monitoring}

#### 게재 기능 패키지 설치 {#deliverability-package}

이 기능은 Adobe Campaign의 전용 패키지를 통해 사용할 수 있습니다. 사용하려면 이 패키지를 설치해야 합니다. 작업이 완료되면 패키지를 고려하기 위해 서버를 다시 시작합니다.

* 호스팅 및 하이브리드 클라이언트의 경우 Adobe 기술 지원 및 컨설턴트가 인스턴스에 **게재 가능성 모니터링**&#x200B;을(를) 구성합니다. 자세한 내용은 Adobe 계정 담당자에게 문의하십시오.

* 온-프레미스 설치의 경우 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** > **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** 메뉴를 통해 **[!UICONTROL Import package]** 패키지를 설치해야 합니다. 자세한 내용은 [Campaign Classic 표준 패키지 설치](../../installation/using/installing-campaign-standard-packages.md)를 참조하십시오.

#### 게재 기능 워크플로 {#deliverability-workflow}

Adobe Campaign Classic에서 **게재 가능성 모니터링**&#x200B;은(는) **[!UICONTROL Refresh for deliverability]** 워크플로우에서 관리합니다. 모든 인스턴스에 기본적으로 설치되며 바운스 메일 자격 규칙 목록, 도메인 목록 및 MX 목록을 초기화할 수 있습니다. **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 패키지가 설치되면 이 워크플로가 매일 밤 실행되어 규칙 목록을 정기적으로 업데이트하며 플랫폼 전달성을 능동적으로 관리할 수 있습니다.

**게재 기능 패키지를 통해 다음에 액세스할 수 있습니다.**

* [받은 편지함 렌더링 보고서](inbox-rendering.md)로, 콘텐츠와 평판을 검사하기 위해 주요 전자 메일 클라이언트에서 메시지를 미리 볼 수 있습니다.
* 메시지 품질 개요(받은 편지함, 스팸).

#### 모니터링 도구 {#monitoring-tools}

**온-프레미스 설치**&#x200B;의 경우 다음 모니터링 도구를 사용할 수 있습니다.

* **[!UICONTROL Delivery throughput]** 보고서는 지정된 기간 동안 전체 플랫폼의 처리량에 대한 개요를 제공합니다. 자세한 내용은 [이 섹션](../../reporting/using/global-reports.md#delivery-throughput)을 참조하십시오.
* 각 게재는 다른 인터넷 서비스 공급자(ISP)에 대한 브로드캐스트 통계 보고서를 생성합니다. 다음 숫자를 포함하여 전달성에 영향을 줄 수 있는 일부 데이터 품질 및 신뢰도 지표를 표시합니다.
   * **[!UICONTROL Hard bounces]**&#x200B;은(는) 데이터 품질을 나타냅니다. 이 숫자는 2% 미만이어야 합니다.
   * **[!UICONTROL Soft bounces]**&#x200B;은(는) 평판을 나타냅니다. 이 숫자는 특정 ISP의 경우 10%보다 커서는 안 됩니다.

  자세한 내용은 [게재 통계](../../reporting/using/global-reports.md#delivery-statistics) 섹션을 참조하십시오.

#### 모니터링 지침 {#monitoring-guidelines}

**온-프레미스 설치**&#x200B;의 경우 게재 가능성 모니터링에 대한 몇 가지 추가 지침을 참조하세요.

* 전체 플랫폼에 대한 [게재 처리량](../../reporting/using/global-reports.md#delivery-throughput)을(를) 정기적으로 확인하여 원본 설정과 일치하는지 확인하십시오.
* 게재 템플릿에 [다시 시도](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)가 올바르게 설정되었는지(다시 시도 기간 30분 및 20번 이상 다시 시도) 확인하십시오.
* [바운스](understanding-delivery-failures.md#bounce-mail-management) 사서함에 액세스할 수 있고 계정이 곧 만료되지 않는지 정기적으로 확인하십시오.
* [게재 대시보드](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}에서 액세스할 수 있는 각 게재 처리량을 확인하여 게재 콘텐츠의 유효성과 일치하는지 확인합니다(예: &#39;플래시 판매&#39;는 일 수가 아닌 분 단위로 제공되어야 함).
* 웨이브를 사용할 때 다음 웨이브가 트리거되기 전에 각 웨이브가 완료되기에 충분한 시간이 있는지 확인합니다.
* 오류 수와 새 [격리](understanding-quarantine-management.md)이(가) 다른 게재와 일치하는지 확인하십시오.
* 강조 표시된 오류 종류(차단 목록, DNS 문제, 스팸 방지 규칙 등)를 확인하려면 [게재 로그](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-dashboard#delivery-logs-and-history){target="_blank"}를 자세히 참조하세요.

### 문제 해결 {#delivery-troubleshooting}

**하이브리드/온-프레미스 배포**&#x200B;에서 게재 문제가 발생하면 특정 작업을 수행할 수 있습니다.

* [전달성 문제](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [이미지 표시 문제](../../production/using/image-display-issues.md)
* [게재 성능 문제](delivery-performance-troubleshooting.md)
* [임시 파일 문제](../../production/using/temporary-files.md) - *온-프레미스 고객 전용*

## 게재 모니터링

다음 리소스는 Campaign Classic v7에서 게재 성능을 모니터링하고 추적하는 데 도움이 됩니다.

### 게재 대시보드 액세스

게재 목록에 액세스하고 게재 대시보드를 사용하여 전송 활동을 모니터링하는 방법에 대해 알아봅니다.

* [Campaign UI에서 게재 모니터링](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}(Campaign v8 설명서 - v7 및 v8 모두에 적용)
* [게재 상태](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"}(Campaign v8 설명서)
* [고급: 게재 로그 사용자 지정](customize-delivery-logs.md)(v7 하이브리드/온-프레미스 전용 - 스키마 확장)

### 메시지 상호 작용 추적

게재 열기, 클릭 수 및 수신자 상호 작용을 추적합니다.

* [메시지 추적 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"}(Campaign v8 설명서 - v7 및 v8 모두에 적용)
* [추적된 링크 구성](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"}(Campaign v8 설명서)
* [액세스 추적 로그](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"}(Campaign v8 설명서)

### 게재 성능 최적화

게재 성능 문제에 대한 우수 사례 및 문제 해결:

* [게재 모범 사례](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}(Campaign v8 설명서 - v7 및 v8에 모두 적용)
* [게재 성능 및 문제 해결](delivery-performance-troubleshooting.md)(v7 하이브리드/온-프레미스 특정 구성)

### 실패 및 격리 이해

게재 실패, 반송 메일 및 격리된 주소 관리:

* [게재 오류 이해](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}(Campaign v8 설명서 - v7 및 v8에 대한 포괄적인 안내서)
* [격리 관리](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}(Campaign v8 설명서 - v7 및 v8에 대한 포괄적인 안내서)
* [게재 실패 및 격리 구성](delivery-failures-quarantine.md)(v7 하이브리드/온-프레미스 특정 구성)
