---
product: campaign
title: 기술 워크플로우
description: Campaign Classic 패키지에서 사용할 수 있는 기술 워크플로우에 대해 자세히 알아보십시오.
audience: workflow
content-type: reference
topic-tags: technical-workflows
exl-id: 9aed2665-cd4b-419c-b9f2-ea04fc1d8f01
source-git-commit: 56470602e3acf777d5b00c293060c644c1fbbc37
workflow-type: tm+mt
source-wordcount: '1712'
ht-degree: 3%

---

# 기술 워크플로우{#about-technical-workflows}

![](../../assets/common.svg)

## 기술 워크플로우 기본 정보 {#overview}

이 섹션에 자세히 설명된 워크플로우는 다양한 Adobe Campaign 기본 제공 패키지와 함께 설치됩니다. 이러한 패키지 및 관련 기술 워크플로우는 사용권 계약에 따라 다릅니다. 기본 제공 패키지는 [이 섹션에 자세히 설명되어 있습니다.](../../installation/using/installing-campaign-standard-packages.md)

기본적으로 기술 워크플로우는 다음 노드의 하위 폴더에서 사용할 수 있습니다. **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

기술 워크플로우는 관리 권한이 있는 운영자만 시작하고 수정할 수 있습니다. 권한에 대한 자세한 내용은 이 [섹션](../../platform/using/access-management-groups.md#default-groups)을 참조하십시오.

>[!NOTE]
>
>메시지 센터 모듈과 관련된 기술 워크플로우는 기본적으로 **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technical workflows]** 노드에서 사용할 수 있습니다.

기술 워크플로우를 모니터링하는 방법에 대한 자세한 내용은 [전용 섹션](monitoring-technical-workflows.md)을 참조하십시오.

## 기술 워크플로우 목록 {#list-technical-workflows}

| 기술 워크플로우 | 패키지 | 설명 |
|------|--------|-----------|
| **별칭 정리** (aliasCleaning) | 게재 | 이 워크플로우는 열거형 값을 표준화합니다. 기본적으로 매일 오전 3시에 트리거됩니다. |
| **청구** (청구) | 게재 | 이 워크플로우는 &#39;청구&#39; 운영자에게 전자 메일로 시스템 활동 보고서를 보냅니다. 마케팅 인스턴스에서 매월 25일에 트리거됩니다. |
| **twitter 통계 계산** (statsTwitter) | 소셜 네트워크(소셜 마케팅) - Campaign v7만 해당 | 이 워크플로우는 Twitter 및 방문 횟수에 연결된 통계를 계산합니다. |
| **캠페인 작업** (operationMgt) | 마케팅 캠페인(캠페인) | 이 워크플로우는 마케팅 캠페인(타겟팅, 파일 추출 등)에 대한 작업을 관리합니다. 또한 반복 및 주기적 캠페인과 관련된 워크플로우를 만듭니다. |
| **HeatMap 서비스를 위한 데이터 수집** (collectDataHeatMapService) | 기본적으로 설치됨 | 이 워크플로우는 HeatMap 서비스에 필요한 데이터를 검색합니다. |
| **개인 정보 보호 요청 수집** (collectPrivacyRequests) | 개인 정보 보호 규정 | 이 워크플로우는 Adobe Campaign에 저장된 수신자의 데이터를 생성하여 개인 정보 보호 요청의 화면에서 다운로드할 수 있도록 합니다. |
| **원가 계산** (budgetMgt) | 마케팅 캠페인(캠페인) | 이 워크플로우는 예산, 계획, 프로그램, 캠페인, 게재 및 작업에 대한 비용 및 비용 라인의 계산을 시작합니다. |
| **데이터베이스 정리** (정리) | 게재 | 이 워크플로우는 데이터베이스 유지 관리 워크플로우입니다. 통계 및 프로세스와 다른 계산을 수행하고 배포 도우미에서 정의된 구성에 따라 데이터베이스에서 오래된 데이터를 삭제합니다. 기본적으로 매일 오전 4시에 트리거됩니다. 자세한 정보는 [이 페이지](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic)를 참조하십시오. |
| **차단된 LINE 사용자 삭제** (deleteBlockedLineUsersV2) | LINE 채널 | 이 워크플로우에서는 LINE V2 사용자가 180일 동안 LINE 공식 계정을 차단하면 데이터가 삭제됩니다. |
| **개인 정보 보호 요청 데이터 삭제** (deletePrivacyRequestsData) | 개인 정보 보호 규정 | 이 워크플로우는 Adobe Campaign에 저장된 수신자의 데이터를 삭제합니다. |
| **게재 표시기** (게재 지표) | 중간 소싱 플랫폼 | 이 워크플로우는 게재에 대한 게재 추적 지표를 업데이트합니다. 이 워크플로우는 기본적으로 매시간 트리거됩니다. |
| **토론 포럼 프로세스** (newsgroupMgt) | 마케팅 리소스(MRM) | 이 워크플로우는 토론 포럼에서 알림 전달을 관리합니다. 승인 신호가 수신되면 트리거됩니다 |
| **분산 마케팅 프로세스** (centralLocalMgt) | 중앙/로컬 마케팅(분산 마케팅) | 이 워크플로우는 분산 마케팅 모듈 사용과 관련된 처리를 시작합니다. 로컬 캠페인 만들기를 시작하고 주문 및 캠페인 패키지 가용성과 관련된 알림을 관리합니다. |
| **이벤트 제거** (webAnalyticsPurgeWebEvents) | 웹 Analytics 커넥터 | 이 워크플로우에서는 [수명] 필드에 구성된 기간에 따라 데이터베이스 필드에서 모든 이벤트를 삭제할 수 있습니다. |
| **Adobe Experience Cloud으로 대상 내보내기** (exportSharedAudience) | Adobe Experience Cloud과 통합 | 이 워크플로우는 대상을 공유 대상/세그먼트로 내보냅니다. 이러한 대상은 사용하는 다양한 Adobe Experience Cloud 솔루션에서 사용할 수 있습니다. |
| **예측** (예측) | 게재 | 이 워크플로우는 임시 달력에 저장된 게재를 분석합니다(임시 로그 만들기). 기본적으로 매일 오전 1시에 트리거됩니다. |
| **전체 합계 계산(propositionrcp 큐브)** (agg_nmspropositionrcp_full) | 오퍼 엔진(상호 작용) | 이 워크플로우는 오퍼 제안 큐브의 전체 합계를 업데이트합니다. 기본적으로 매일 오전 6시에 트리거됩니다. 이 집계는 다음 차원을 캡처합니다. 채널, 게재, 마케팅 오퍼 및 날짜. 그런 다음 오퍼 제안 큐브를 사용하여 오퍼를 기반으로 보고서를 생성합니다. [이 섹션](../../reporting/using/about-cubes.md)에서 큐브에 대해 자세히 알 수 있습니다. |
| **변환된 연락처 식별** (webAnalyticsFindConverted) | 웹 Analytics 커넥터 | 이 워크플로우는 재마케팅 캠페인 후 구매를 마친 사이트 방문자를 인덱싱합니다. 이 워크플로우에서 복구한 데이터는 리마케팅 효율성 보고서에서 액세스할 수 있습니다(이 페이지 참조). |
| **Adobe Experience Cloud에서 대상자 가져오기** (importSharedAudience) | Adobe Experience Cloud과 통합 | 이 워크플로우를 통해 다양한 Adobe Experience Cloud 솔루션의 대상/세그먼트를 Adobe Campaign에 가져올 수 있습니다. |
| **캠페인의 게재 작업** (deliveryMgt) | 마케팅 캠페인(캠페인) | 이 워크플로우는 승인된 게재를 트리거하고 외부 배달을 위해 서비스 공급자의 사후 처리를 시작합니다. 또한 승인 알림과 다시 알림을 보냅니다. |
| **서비스 공급자의 작업** (supplierMgt) | 마케팅 캠페인(캠페인) | 게재가 승인되면 이 워크플로우는 공급자 처리(라우터에 전자 메일 및 사후 처리)를 시작합니다. |
| **LINE V2 액세스 토큰 업데이트** (updateLineV2AccessToken) | LINE 채널 - Campaign v7만 | 이 워크플로우는 액세스 토큰을 LINE V2로 새로 고칩니다. |
| **MID에서 LineUserID로 마이그레이션** (MIDToUserIDMigation) | LINE 채널 | 이 워크플로우는 LINE V1에서 LINE V2로 마이그레이션에 대한 LINE V2 사용자 ID를 생성합니다. |
| **마케팅 리소스 알림** (assetMgt) | 마케팅 리소스(MRM) | 이 워크플로우는 마케팅 리소스의 승인 및 게시에 연결된 알림을 관리합니다. |
| **메시지 센터  &lt;external_account_name>** (mcSynch_&lt;external_account_name>) | 트랜잭션 메시지 제어(메시지 센터 - 제어) | 이 워크플로우는 다음과 같습니다. <ul><li>작업으로 처리된 이벤트 목록을 복구합니다.</li><li>배달 메시지 자격을 복구하기 위해 NmsBroadLogMsg 테이블과 동기화합니다.</li><li>NmsBroadLogMsg 테이블과의 동기화가 완료되는 즉시 이벤트 게재 로그를 복구합니다.</li><li>는 배달 URL에 대한 추적을 복구하기 위해 NmsTrackingUrl 테이블과 동기화합니다.</li><li>NmsTrackingUrl 테이블과의 동기화가 완료되는 즉시 이벤트 추적 URL을 복구합니다.</li><li>게재를 보낸 후 3시간마다 격리된 모든 이메일 주소를 복구할 수 있습니다.</li></ul> |
| **MessageCenter 전체 집계 계산** (agg_messageCenter_full) | 트랜잭션 메시지 제어(메시지 센터 - 제어) | 이 워크플로우는 메시지 센터 큐브의 전체 합계를 업데이트합니다. 기본적으로 매일 오전 3시에 트리거됩니다. 이 집계는 다음 차원을 캡처합니다. 채널, 날짜, 상태 및 이벤트 유형. 그런 다음 메시지 센터 큐브를 사용하여 이벤트를 기반으로 보고서를 생성합니다. [이 섹션](../../reporting/using/about-cubes.md)에서 큐브에 대해 자세히 알아볼 수 있습니다 |
| **중간 소싱(게재 카운터)** (defaultMidSourcingDlv) | 중간 소싱으로 전송 | 이 워크플로우는 중간 소싱 서버의 게재에 대한 카운트 정보를 수집합니다. 카운트 정보에는 전송된 게재 수 등과 같은 일반 게재 지표가 포함되어 있습니다. 열기와 같은 추적 정보는 포함되지 않습니다. 기본적으로 10분마다 트리거됩니다. |
| **중간 소싱(게재 로그)** (defaultMidSourcingLog) | 중간 소싱으로 전송 | 이 워크플로우는 중간 소싱 서버에서 게재 로그를 수집합니다. 기본적으로 매시간 트리거됩니다. |
| **NMAC 옵트아웃 관리** (mobileAppOptOutMgt) | 모바일 앱 채널 | 이 워크플로우는 모바일 장치의 알림 구독 취소를 업데이트합니다. 오전 1시부터 자정까지 6시간마다 시작됩니다. 자세한 내용은 [이 섹션](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)을 참조하십시오. |
| **오퍼 알림** (offerMgt) | 게재 | 이 워크플로우는 오퍼 카탈로그에 포함된 모든 카테고리와 온라인 환경에 승인된 오퍼를 배포합니다. |
| **일시 중지된 워크플로우 정리** (cleanupPausedWorkflows) | 게재 | 이 워크플로우는 심각도가 정상으로 설정된 일시 중지된 워크플로우를 분석하고 너무 오랫동안 일시 중지되면 경고 및 알림을 트리거합니다. 한 달 후 일시 중지된 기술 워크플로우는 무조건 중지됩니다. 기본적으로 매주 월요일 오전 5시에 트리거됩니다. 자세한 내용은 [일시 중지된 워크플로우 처리](monitoring-workflow-execution.md#handling-of-paused-workflows)를 참조하십시오. |
| **개인 정보 보호 요청 정리** (cleanupPrivacyRequests) | 개인 정보 보호 규정 | 이 워크플로우는 90일 이상 경과한 액세스 요청 파일을 지웁니다. |
| **일괄 처리 이벤트** (batchEventsProcessing) | 트랜잭션 메시지 실행(메시지 센터 - 실행) | 이 워크플로우를 사용하면 일괄 처리 이벤트를 메시지 템플릿에 연결하기 전에 큐에 넣을 수 있습니다. |
| **실시간 이벤트 처리** (rtEventsProcessing) | 트랜잭션 메시지 실행(메시지 센터 - 실행) | 이 워크플로우를 사용하면 실시간 이벤트를 메시지 템플릿에 연결하기 전에 큐에 넣을 수 있습니다. |
| **제안 동기화** (provisionSynch) | 실행 인스턴스를 사용하여 오퍼 엔진 제어 | 이 워크플로우는 마케팅 인스턴스와 상호 작용에 사용되는 실행 인스턴스 간의 제안을 동기화합니다. |
| **웹 이벤트 복구** (webAnalyticsGetWebEvents) | 웹 Analytics 커넥터 | 매시간마다 이 워크플로우는 주어진 사이트의 인터넷 사용자 동작에 있는 세그먼트를 다운로드하고, Adobe Campaign 데이터베이스에 지정하고, 리마케팅 워크플로우를 시작합니다. |
| **합계 보고** (reportingAggregates) | 게재 | 이 워크플로우 업데이트는 보고서에 사용되는 합계를 업데이트합니다. 기본적으로 매일 오전 2시에 트리거됩니다. |
| **지표 및 캠페인 속성 보내기** (webAnalyticsSendMetrics) | 웹 Analytics 커넥터 | 이 워크플로우에서는 Adobe® Analytics 커넥터를 통해 Adobe Campaign에서 Adobe Experience Cloud Suite로 이메일 캠페인 표시기를 보낼 수 있습니다. 관련 지표는 다음과 같습니다. 전송(전송됨), 총 열기 수(iTotalRecipientOpen), 클릭한 총 수신자 수(iTotalRecipientClick), 오류(iError), 옵트아웃(옵트아웃). |
| **주식: 주문 및 경고** (stockMgt) | 마케팅 캠페인(캠페인) | 이 워크플로우는 주문 라인에 대한 재고 계산을 시작하고 경고 경고를 관리합니다. |
| **facebook 팬 동기화** (syncFacebookFans) | 소셜 네트워크(소셜 마케팅) - Campaign v7만 해당 | 이 워크플로우는 매일 오전 7시에 Facebook 팬을 Adobe Campaign으로 가져옵니다. |
| **facebook 페이지 동기화** (syncFacebook) | 소셜 네트워크(소셜 마케팅) - Campaign v7만 해당 | 이 워크플로우는 매일 오전 7시에 Facebook 페이지를 Adobe Campaign과 동기화합니다. |
| **twitter 페이지 동기화** (syncTwitter) | 소셜 네트워크(소셜 마케팅) - Campaign v7만 해당 | 이 워크플로우는 매일 오전 7시에 Twitter 팔로워를 Adobe Campaign으로 가져옵니다. |
| **작업 알림** (taskMgt) | 마케팅 리소스(MRM) - Campaign v7만 해당 | 이 워크플로우를 통해 마케팅 캠페인의 작업과 관련된 알림 메시지를 보낼 수 있습니다. |
| **추적** (추적) | 게재 | 이 워크플로우에서는 추적 정보의 복구 및 통합을 수행합니다. 또한 추적 및 게재 통계, 특히 Message Center 아카이빙 워크플로우에서 사용되는 통계 수를 재계산할 수 있습니다. 기본적으로 시간당 한 번 트리거됩니다. |
| **이벤트 상태 업데이트** (updateEventsStatus) | 트랜잭션 메시지 실행(메시지 센터 - 실행) | 이 워크플로우를 통해 이벤트에 상태를 할당할 수 있습니다. 이벤트 상태는 다음과 같습니다.<ul><li>보류 중: 이벤트가 큐에 있습니다. 메시지 템플릿이 아직 연결되어 있지 않습니다.</li><li>게재 보류 중: 이벤트가 큐에 있고 메시지 템플릿이 연결되어 있고 현재 게재에 의해 처리되는 중입니다.</li><li>전송됨: 이 상태는 게재 로그에서 복사됩니다. 게재가 전송되었음을 의미합니다.</li><li>게재에서 무시됨: 이 상태는 게재 로그에서 복사됩니다. 게재가 무시되었음을 의미합니다.</li><li>게재 오류: 이 상태는 게재 로그에서 복사됩니다. 게재가 실패했다는 뜻입니다.</li><li>이벤트가 포함되지 않음: 이벤트를 메시지 템플릿과 연결하지 못했습니다. 이벤트가 다시 처리되지 않습니다.</li></ul> |
| **게재 능력을 위한 업데이트** (게재 가능성 업데이트) | 게재 | 게재 기능 모니터링(전자 메일 게재 기능) 패키지가 설치되면 이 워크플로우는 매일 밤 실행되고 바운스 이메일 자격 규칙과 도메인 및 MX 목록을 관리합니다. 이렇게 하려면 플랫폼에서 HTTPS 포트를 열어야 합니다 |