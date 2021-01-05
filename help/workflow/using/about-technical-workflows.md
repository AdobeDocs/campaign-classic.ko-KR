---
solution: Campaign Classic
product: campaign
title: 기술 워크플로우
description: Campaign Classic 패키지와 함께 사용할 수 있는 기술 워크플로우에 대한 자세한 내용을 살펴보십시오.
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: a80f611140a5fb03e3547a8de228ecd8c96e8862
workflow-type: tm+mt
source-wordcount: '1816'
ht-degree: 5%

---


# 기술 워크플로우{#about-technical-workflows}

## 기술 워크플로우 기본 정보 {#overview}

이 섹션에 설명된 워크플로우는 다양한 Adobe Campaign 내장 패키지와 함께 설치됩니다. 이러한 패키지 및 관련 기술 워크플로우는 라이선스 계약에 따라 다릅니다. 내장 패키지는 [이 섹션](../../installation/using/installing-campaign-standard-packages.md)에 자세히 설명되어 있습니다.

기본적으로 기술 워크플로우는 다음 노드의 하위 폴더에서 사용할 수 있습니다.**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

>[!NOTE]
>
>메시지 센터 모듈과 관련된 기술 워크플로우는 기본적으로 **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technical workflows]** 노드에서 사용할 수 있습니다.

기술 워크플로우를 모니터링하는 방법에 대한 자세한 내용은 [전용 섹션](../../workflow/using/monitoring-technical-workflows.md)을 참조하십시오.

## 기술 워크플로우 목록 {#list-technical-workflows}

| 기술 워크플로우 | 패키지 | 설명 |
|------|--------|-----------|
| **별칭 정리** (aliasCleaning) | 게재 | 이 워크플로우는 열거형 값을 표준화합니다. 기본적으로 매일 오전 3시에 트리거됩니다. |
| **청구** (청구) | 게재 | 이 워크플로우는 시스템 활동 보고서를 이메일로 &#39;과금&#39; 운영자에게 보냅니다. 기본적으로 매월 25일에 트리거됩니다. |
| **Twitter 통계**  계산(statsTwitter) | 소셜 네트워크(소셜 마케팅) | 이 워크플로우는 리트윗 및 Twitter 방문 횟수에 연결된 통계를 계산합니다. |
| **캠페인 작업** (operationMgt) | 마케팅 캠페인(캠페인) | 이 워크플로우는 마케팅 캠페인(타깃팅, 파일 추출 등 시작)에 대한 작업을 관리합니다. 또한 반복되는 캠페인과 관련된 워크플로우를 만듭니다. |
| **HeatMap 서비스에 대한 데이터 수집** (collectDataHeatMapService) | 기본적으로 설치됨 | 이 워크플로우는 HeatMap 서비스에 필요한 데이터를 검색합니다. |
| **개인 정보 요청 수집** (collectPrivacyRequests) | 개인 정보 보호 규정 | 이 워크플로우는 Adobe Campaign에 저장된 수신자의 데이터를 생성하여 개인 정보 요청의 화면에서 다운로드할 수 있도록 합니다. |
| **비용 계산** (budgetMgt) | 마케팅 캠페인(캠페인) | 이 워크플로우는 예산, 계획, 프로그램, 캠페인, 납품 및 태스크에 대한 비용 및 원가 라인의 계산을 시작합니다. |
| **데이터베이스 정리** (정리) | 게재 | 이 워크플로우는 데이터베이스 유지 관리 워크플로입니다.통계 및 프로세스와 다른 계산을 수행하고 배포 도우미의 정의된 구성에 따라 데이터베이스에서 오래된 데이터를 삭제합니다. 기본적으로 매일 오전 4시에 트리거됩니다. 자세한 정보는 [이 페이지](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic)를 참조하십시오. |
| **차단된 LINE 사용자**  삭제(deleteBlockedLineUsersV2) | LINE 채널 | 이 워크플로우에서는 LINE V2 사용자가 180일 동안 LINE 공식 계정을 차단하면 데이터가 삭제됩니다. |
| **개인 정보 요청 데이터 삭제** (deletePrivacyRequestsData) | 개인 정보 보호 규정 | 이 워크플로우에서는 Adobe Campaign에 저장된 수신자 데이터를 삭제합니다. |
| **배달 표시기** (deliveryIndicator) | 중간 소싱 플랫폼 | 이 워크플로우는 전달에 대한 배달 추적 표시기를 업데이트합니다. 이 워크플로우는 기본적으로 매 시간마다 트리거됩니다. |
| **토론 포럼 프로세스** (newsgroupMgt) | 마케팅 리소스(MRM) | 이 워크플로우는 토론 포럼의 알림 전송을 관리합니다. 승인 신호가 수신될 때 트리거됩니다. |
| **분산 마케팅 프로세스** (centralLocalMgt) | 중앙/로컬 마케팅(분산 마케팅) | 이 워크플로우는 분산 마케팅 모듈 사용과 관련된 처리를 시작합니다. 로컬 캠페인 만들기를 실행하고 주문 및 캠페인 패키지 가용성과 관련된 알림을 관리합니다. |
| **이벤트 제거** (webAnalyticsPurgeWebEvents) | 웹 분석 커넥터 | 이 워크플로우에서는 [수명] 필드에 구성된 기간에 따라 데이터베이스 필드에서 모든 이벤트를 삭제할 수 있습니다. |
| **Adobe Experience Cloud** (exportSharedAudience)로 대상 내보내기 | Adobe Experience Cloud과 통합 | 이 워크플로우에서는 대상을 공유 대상/세그먼트로 내보냅니다. 이러한 대상은 사용하는 다른 Adobe Experience Cloud 솔루션에서 사용할 수 있습니다. |
| **예측** (예측) | 게재 | 이 워크플로우는 임시 달력에 저장된 배달 정보를 분석합니다(임시 로그 만들기). 기본적으로 매일 오전 1시에 트리거됩니다. |
| **전체 합계 계산(propositionrcp cube)** (agg_nmspropositionrcp_full) | 오퍼 엔진(상호 작용) | 이 워크플로우는 오퍼 제안 큐브에 대한 전체 합계를 업데이트합니다. 기본적으로 매일 오전 6시에 트리거됩니다. 이 집계는 다음 차원을 캡처합니다.채널, 전달, 마케팅 제안 및 날짜. 그런 다음 오퍼 제안 큐브를 사용하여 오퍼를 기반으로 보고서를 생성합니다. [이 섹션](../../reporting/using/about-cubes.md)에서 큐브에 대해 자세히 알아볼 수 있습니다. |
| **변환된 연락처**  식별(webAnalyticsFindConverted) | 웹 분석 커넥터 | 이 워크플로우는 재마케팅 캠페인 후 구매를 완료한 사이트 방문자를 인덱싱합니다. 이 워크플로우로 복구된 데이터는 재마케팅 효율성 보고서에서 액세스할 수 있습니다(이 페이지 참조). |
| **Adobe Experience Cloud에서 대상 가져오기** (importSharedAudience) | Adobe Experience Cloud과 통합 | 이 워크플로우에서는 다른 Adobe Experience Cloud 솔루션의 대상/세그먼트를 Adobe Campaign으로 가져올 수 있습니다. |
| **캠페인의 배달에서 작업** (deliveryMgt) | 마케팅 캠페인(캠페인) | 이 워크플로우는 승인된 배달을 트리거하고 외부 배달을 위해 서비스 공급자의 사후 처리를 시작합니다. 또한 승인 알림과 미리 알림을 보냅니다. |
| **서비스 공급자의 작업** (supplierMgt) | 마케팅 캠페인(캠페인) | 배달이 승인되면 이 워크플로우는 공급자(라우터에 전자 메일 및 사후 처리)를 처리하기 시작합니다. |
| **LINE V2 액세스 토큰 업데이트** (updateLineV2AccessToken) | LINE 채널 | 이 워크플로우는 액세스 토큰을 LINE V2로 새로 고칩니다. |
| **MID에서 LineUserID 마이그레이션** (MIDToUserIDMigation) | LINE 채널 | 이 워크플로우에서는 LINE V1에서 LINE V2로 마이그레이션하기 위한 LINE V2 사용자 ID를 생성합니다. |
| **마케팅 리소스 알림** (assetMgt) | 마케팅 리소스(MRM) | 이 워크플로우는 마케팅 리소스의 승인 및 게시에 연결된 알림을 관리합니다. |
| **메시지 센터  &lt;external_account_name>** (mcSynch_&lt;external_account_name>) | 트랜잭션 메시지 제어(메시지 센터 - 제어) | 이 작업 과정: <ul><li>작업에 의해 처리된 이벤트 목록을 복구합니다.</li><li>배달 메시지 자격 조건을 복구하기 위해 NmsBroadLogMsg 테이블과 동기화합니다.</li><li>NmsBroadLogMsg 테이블과의 동기화가 완료되는 즉시 이벤트 배달 로그를 복구합니다.</li><li>배달 URL에 대한 추적을 복구하기 위해 NmsTrackingUrl 테이블과 동기화합니다.</li><li>NmsTrackingUrl 테이블과의 동기화가 완료되는 즉시 이벤트 추적 URL을 복구합니다.</li><li>배달을 보낸 후 3시간마다 격리에 있는 모든 이메일 주소를 복구할 수 있습니다.</ul> |
| **MessageCenter 전체 집계 계산** (agg_messageCenter_full) | 트랜잭션 메시지 제어(메시지 센터 - 제어) | 이 워크플로우는 메시지 센터 큐브의 전체 합계를 업데이트합니다. 기본적으로 매일 오전 3시에 트리거됩니다. 이 집계는 다음 차원을 캡처합니다.채널, 날짜, 상태 및 이벤트 유형. 그런 다음 메시지 센터 큐브를 사용하여 이벤트를 기반으로 보고서를 생성합니다. [이 섹션](../../reporting/using/about-cubes.md)에서 큐브에 대해 자세히 알아볼 수 있습니다. |
| **중간 소싱(배달 카운터)** (defaultMidSourcingDlv) | 중간 소싱으로 전송 | 이 워크플로우는 중간 소싱 서버에서 납품에 대한 카운트 정보를 수집합니다. 개수 정보에는 전송 횟수 등과 같은 일반 배달 지표가 포함되어 있습니다. 열기와 같은 추적 정보는 포함되지 않습니다. 기본적으로 10분마다 트리거됩니다. |
| **중간 소싱(배달 로그)** (defaultMidSourcingLog) | 중간 소싱으로 전송 | 이 워크플로우는 중간 소싱 서버의 배달 로그를 수집합니다. 기본적으로 매 시간마다 트리거됩니다. |
| **NMAC 옵트아웃 관리** (mobileAppOptOutMgt) | 모바일 앱 채널 | 이 워크플로우는 모바일 장치의 알림 구독 취소를 업데이트합니다. 오전 1시부터 자정까지 6시간마다 트리거됩니다 자세한 내용은 [이 섹션](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)을 참조하십시오. |
| **활성 청구 프로필 수** (billingActiveContactCount) | 게재 | 이 워크플로우는 활성 프로필 수를 계산합니다. 기본적으로 매일 밤 1시에 트리거됩니다. &quot;프로필&quot;은 최종 고객, 잠재 고객 또는 리드를 나타내는 정보의 기록(예: 쿠키 ID, 고객 ID, 모바일 식별자 또는 특정 채널과 관련된 기타 정보가 포함된 외부 테이블 또는 nmsRecipient 테이블의 레코드)을 나타냅니다. 청구 시 &quot;활성&quot; 프로필만 고려됩니다. 지난 12개월 이내에 채널을 통해 프로파일을 타깃팅하거나 커뮤니케이션한 경우 프로파일은 &quot;활성&quot;으로 간주됩니다. 페이스북과 트위터 채널은 고려되지 않습니다. 관리 > 캠페인 관리 > 고객 지표 메뉴에서 활성 프로필 수에 대한 개요를 알 수 있습니다. |
| **오퍼 알림** (offerMgt) | 게재 | 이 워크플로우는 오퍼 카탈로그에 포함된 모든 카테고리는 물론, 승인된 오퍼를 온라인 환경에 배포합니다. |
| **일시 중지된 워크플로 정리** (cleanupPausedWorkflows) | 게재 | 이 워크플로우는 심각도가 정상으로 설정된 일시 중지된 워크플로우를 분석하고 너무 오랫동안 일시 중지되었을 때 경고 및 알림을 트리거합니다. 한 달 후 일시 중지된 기술 워크플로우는 무조건 중지됩니다. 기본적으로 매주 월요일 오전 5시에 트리거됩니다. 자세한 내용은 [일시 중지된 워크플로우 처리](../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows)를 참조하십시오. |
| **개인 정보 요청 정리** (cleanupPrivacyRequests) | 개인 정보 보호 규정 | 이 워크플로우는 90일 이상 된 액세스 요청 파일을 삭제합니다. |
| **일괄 처리 이벤트** (batchEventsProcessing) | 트랜잭션 메시지 실행(메시지 센터 - 실행) | 이 워크플로우에서는 일괄 처리 이벤트를 메시지 템플릿과 연결하기 전에 큐에 넣을 수 있습니다. |
| **실시간 이벤트**  처리(rtEventsProcessing) | 트랜잭션 메시지 실행(메시지 센터 - 실행) | 이 워크플로우에서는 실시간 이벤트를 메시지 템플릿과 연결하기 전에 큐에 넣을 수 있습니다. |
| **제안 동기화** (제안 동기화) | 실행 인스턴스가 있는 오퍼 엔진 제어 | 이 작업 과정은 마케팅 인스턴스와 상호 작용에 사용된 실행 인스턴스 간에 proposition을 동기화합니다. |
| **웹 이벤트**  복구(webAnalyticsGetWebEvents) | 웹 분석 커넥터 | 이 워크플로우는 매 시간마다 특정 사이트의 인터넷 사용자 동작에 대한 세그먼트를 다운로드하고 Adobe Campaign 데이터베이스에 저장하고 다시 마케팅 워크플로우를 실행합니다. |
| **집계 보고** (reportingAggregments) | 게재 | 이 워크플로 업데이트는 보고서에 사용된 집계입니다. 기본적으로 매일 오전 2시에 트리거됩니다. |
| **표시기 및 캠페인 특성**  전송(webAnalyticsSendMetrics) | 웹 분석 커넥터 | 이 워크플로우에서는 Adobe® Genesis 커넥터를 통해 Adobe Campaign에서 Adobe Experience Cloud Suite로 이메일 캠페인 표시기를 보낼 수 있습니다. 관련 표시기는 전송(iSent), 총 열기 수(iTotalRecipientOpen), 클릭한 총 받는 사람 수(iTotalRecipientClick), 오류(iError), 옵트아웃(옵트아웃)(iOptOut) 등과 같습니다. |
| **Stock:주문 및 경고** (stockMgt) | 마케팅 캠페인(캠페인) | 이 워크플로우는 주문 라인에 대한 재고 계산을 실행하고 경고 경보 임계값을 관리합니다. |
| **Facebook 팬 동기화** (syncFacebookFans) | 소셜 네트워크(소셜 마케팅) | 이 워크플로우는 매일 오전 7시에 Facebook 팬을 Adobe Campaign으로 가져옵니다. |
| **Facebook 페이지 동기화** (syncFacebook) | 소셜 네트워크(소셜 마케팅) | 이 워크플로우는 매일 오전 7시에 Adobe Campaign과 Facebook 페이지를 동기화합니다. |
| **Twitter 페이지 동기화** (syncTwitter) | 소셜 네트워크(소셜 마케팅) | 이 워크플로우는 매일 오전 7시에 Twitter 팔로워를 Adobe Campaign으로 가져옵니다. |
| **작업 알림** (taskMgt) | 마케팅 리소스(MRM) | 이 워크플로우에서는 마케팅 캠페인의 작업과 관련된 알림 메시지를 보낼 수 있습니다. |
| **추적** (추적) | 게재 | 이 워크플로우는 추적 정보의 복구 및 통합을 수행합니다. 또한 Message Center 아카이빙 워크플로우에서 사용되는 추적 및 전달 통계 정보(특히 Message Center 아카이빙 워크플로우에서 사용하는 통계 정보)를 다시 계산할 수 있습니다. 기본적으로 시간당 한 번 트리거됩니다. |
| **이벤트 상태 업데이트** (updateEventsStatus) | 트랜잭션 메시지 실행(메시지 센터 - 실행) | 이 워크플로우에서는 이벤트에 상태를 할당할 수 있습니다. 이벤트 상태는 다음과 같습니다.<ul><li>보류 중:이벤트가 큐에 있습니다. 아직 연결된 메시지 템플릿이 없습니다.</li><li>배달 대기 중:이벤트가 큐에 있고, 메시지 템플릿이 연결되어 있으며 현재 배달에서 처리 중입니다.</li><li>전송:이 상태는 배달 로그에서 복사됩니다. 배달이 전송되었음을 의미합니다.</li><li>배달에서 무시됨:이 상태는 배달 로그에서 복사됩니다. 배달이 무시되었음을 의미합니다.</li><li>배달 오류:이 상태는 배달 로그에서 복사됩니다. 배달이 실패했다는 의미입니다.</li><li>다루지 않은 이벤트:이벤트를 메시지 템플릿과 연결하지 못했습니다. 이벤트는 다시 처리되지 않습니다.</li></ul> |
| **제공**  가능성 업데이트(deliveryUpdate) | 게재 | 배달 가능성 모니터링(이메일 배달 가능) 패키지가 설치되면 이 워크플로우는 야간에 실행되고 도메인 및 MX 목록과 함께 바운스 이메일 자격 규칙을 관리합니다. 이 경우 플랫폼에서 HTTPS 포트를 열어야 합니다. |
| **받은 편지함 렌더링을 위한 시드 네트워크 업데이트** (updateRenderingSeed) | 받은 편지함 렌더링(IR) | 이 워크플로우는 받은 편지함 렌더링에 사용되는 이메일 주소를 업데이트하며, HTTPS 포트가 deliverability.neolane.net용으로 열려 있는 경우에만 작동합니다. |
