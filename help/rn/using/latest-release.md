---
product: campaign
title: 최신 릴리스
description: 최신 Campaign Classic v7 릴리스 정보
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: f2e6db9e198f96e1e0250d461b419ac00e39bf45
workflow-type: tm+mt
source-wordcount: '2221'
ht-degree: 88%

---

# 최신 릴리스{#latest-release}

이 페이지에서는 **최신 Campaign v7 릴리스**&#x200B;의 새로운 기능, 개선 사항 및 버그 해결 사항 목록을 확인할 수 있습니다. 모든 새 빌드는 색상으로 상태가 표시됩니다. [이 페이지](rn-overview.md)에서 Campaign Classic v7 빌드 상태에 대해 자세히 알아보십시오.

## 릴리스 7.3.5 - 빌드 9368 {#release-7-3-5}

[!BADGE 일반 공급]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="일반 공급"}


_2023년 12월 5일 수요일_


**향상된 보안 기능**


* Campaign Classic v7.3.5를 통해 인증 프로세스가 개선되고 보호되었습니다. 이제 기술 운영자는 IMS(Adobe Identity Management System)를 사용하여 Campaign에 연결해야 합니다. 에서 기존 기술 계정을 마이그레이션하는 방법을 알아봅니다. [이 기술 노트](../../technotes/using/ims-migration.md).

* 또한 보안 및 인증 프로세스를 강화하기 위한 노력의 일환으로 Adobe Campaign은 최종 사용자 인증 모드를 로그인/암호 기본 인증에서 Adobe Identity Management 시스템(IMS)으로 마이그레이션할 것을 강력히 권장합니다. 에서 연산자를 마이그레이션하는 방법을 알아봅니다. [이 기술 노트](../../technotes/using/migrate-users-to-ims.md).

**패치**

* Google Big Query 데이터베이스의 데이터를 사용하고 Oracle 데이터베이스에서 데이터를 업데이트할 때 발생하는 문제가 해결되었습니다. 모든 키가 로 설정되었습니다. `0` 워크플로 임시 테이블에서 참조할 수 있습니다. (NEO-65091)
* Google Big Query 데이터베이스의 두 쿼리가 **합집합** 워크플로우 활동. (NEO-63705)
* 을(를) 클릭할 때 사용자에게 다시 인증하도록 요청하는 문제를 해결했습니다. `Back` Campaign 보고서의 단추. (NEO-65087)
* 게재 증명 전에 게재를 삭제할 때 발생하는 데이터베이스 정리 워크플로우의 오류를 수정했습니다. (NEO-48114)
* 클라이언트 콘솔에 연결하는 동안 TLS 확인에 대한 최근 업데이트로 연결 오류가 발생하는 문제를 해결했습니다. (NEO-50488)
* Campaign을 7.3.1로 업그레이드 후 HTTP 프록시 인증과 관련된 문제를 해결했습니다. Campaign 워크플로우의 HTTP 요청이 다음과 같이 실패했습니다. `error 407 – proxy auth required is returned`. (NEO-49624)
* 에서 GPG 암호 해독의 중간 오류를 해결했습니다. **스크립트** 워크플로우 활동. 관련 오류 메시지는 다음과 같습니다. `gpg: decryption failed: No secret key`. (NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->

## 릴리스 7.3.4 - 빌드 9364 {#release-7-3-4}

[!BADGE 제한 공개]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="제한 공개"}

>[!CAUTION]
>
>클라이언트 콘솔 업그레이드는 필수입니다. 이 [페이지](../../installation/using/installing-the-client-console.md)에서 클라이언트 콘솔을 업그레이드하는 방법을 알아보십시오.
>
> [Campaign - Microsoft Dynamics CRM 커넥터](../../platform/using/crm-connectors.md)를 사용하는 경우, 이 새로운 빌드를 사용하여 마케팅 및 중간 소싱 서버를 모두 업그레이드해야 합니다.

_2023년 9월 7일_

**보안 개선**

* IMS API의 보안이 개선되었습니다. 클라이언트에 민감한 정보(즉, 액세스 토큰)가 URL 매개 변수에서 제거되었습니다. 이제 이러한 자격 증명이 post 데이터 또는 인증 헤더로 전송되어 더욱 안전한 통신 프로세스가 보장됩니다. (NEO-63045)
* DDOS 공격을 방지하기 위해 웹 앱의 보안이 개선되었습니다. (NEO-50757)
* PII 데이터가 웹 로그 오류에 노출되지 않도록 보안이 향상되었습니다. (NEO-46827)
* 보안 토큰이 Campaign 홈 페이지 URL에 포함되지 않도록 보안이 최적화되었습니다. (NEO-38519)

**호환성 업데이트**

* Tomcat이 버전 8.5.91로 업데이트되었습니다.
* libexpat 라이브러리가 보안을 개선하기 위해 2.5.0으로 업데이트되었습니다. (NEO-51023)

**개선 사항**

* 서버 구성 파일(serverConf.xml)의 MaxWorkingSetMb 매개 변수가 게재에 대한 메모리 할당을 최적화하도록 수정되었습니다. (NEO-49204)
* BigQuery 외부 계정이 GCloud SDK를 설정하는 데 사용되는 새로운 옵션으로 향상되었습니다. (NEO-63879) [자세히 보기](../../installation/using/configure-fda-google-big-query.md#google-external)
* 새 `cusHeader` 섹션이 서버 구성 파일(serverConf.xml)에 추가되었습니다. 외부 서버에서 파일을 업로드할 때 사용자 정의 헤더를 추가할 수 있습니다. (NEO-58339) [자세히 보기](../../installation/using/the-server-configuration-file.md#cusheaders).
* lastMsgId에 대한 부정적인 ID를 방지하기 위해 추적 로그 관리가 개선되었습니다. int32에서 int64로 변경되었습니다. (NEO-52290)
* 중간 소싱(게재 통계) 워크플로우가 즉시 추가되었습니다. 이 새 워크플로우는 게재 통계 데이터(nms:deliveryStat)를 중간에서 마케팅 인스턴스로 동기화합니다. (NEO-36802)

**패치**

* 서비스 요청 호출 인증이 서비스 토큰을 사용하는 경우 IMS 로그인 전에 서비스 요청을 했을 때 발생할 수 있는 문제를 해결했습니다. (NEO-64903)
* 디지털 콘텐츠 편집기를 사용할 때 스크롤 문제로 이어질 수 있는 회귀 문제를 해결했습니다. (NEO-64671, NEO-59256)
* Excel의 콘텐츠를 디지털 콘텐츠 편집기에 붙여넣을 때 발생하는 회귀 문제를 해결했습니다. (NEO-63287)
* 웹 앱이 v5 호환성 모드에서 올바르게 표시되지 않는 문제를 해결했습니다. (NEO-63174)
* 관리자가 아닌 운영자가 webAnalytics 게재를 보낼 수 없는 문제를 해결했습니다. (NEO-62750)
* 게재에서 조건부 콘텐츠를 사용할 때 브라우저에서 공백을 추가하지 못하는 문제를 해결했습니다. (NEO-62132)
* 여러 로그 스키마와 연결된 대상 스키마를 사용할 때 과금 워크플로우에서 활성 연락처 계산이 제대로 작동하지 않는 회귀 문제를 해결했습니다. (NEO-61468)
* 게재 콘텐츠를 편집할 때 오류를 일으키고 스크롤하지 못하는 문제를 해결했습니다. (NEO-61364)
* 이메일 콘텐츠 편집기에서 이미지를 클릭할 때 팝업 창이 열리는 문제를 해결했습니다. (NEO-60752)
* 게재 HTML 콘텐츠의 특수 문자가 여러 브라우저에서 잘못 인코딩될 수 있는 문제를 해결했습니다. (NEO-60081)
* inSMS 워크플로우 활동을 사용할 때 발생할 수 있는 동기화 문제를 해결했습니다. (NEO-59544)
* Big Query 커넥터를 타임스탬프 또는 날짜/시간 필드와 함께 사용할 때 발생하는 문제를 해결했습니다. (NEO-59502, NEO-49768)
* 누적 게재 보고서를 사용할 수 없는 문제를 해결했습니다. (NEO-59211)
* 사용자 핵심 서비스와 대상자를 공유할 때 오류가 발생하는 문제를 해결했습니다. (NEO-58637)
* 게재의 미러 페이지를 표시할 때 발생하는 문제를 해결했습니다. (NEO-58325)
* XtkLibrary.Right() xtk 표현식이 작동하지 않는 문제를 해결했습니다. (NEO-57870)
* 디지털 콘텐츠 편집기에서 이미지를 업로드할 때 본문 태그의 스타일 속성이 변경되는 문제를 해결했습니다. (NEO-57697)
* CRM 커넥터 활동으로 일괄 처리 내보내기를 수행할 때 특수 문자에 발생하는 문제를 해결했습니다. (NEO-54300)
* 데이터 로드 활동 및 Big Query 커넥터를 사용할 때 대량 로드가 “string” 데이터 유형에서 작동하지 않는 문제를 해결했습니다. (NEO-53748)
* 오퍼 렌더링 문제로 이어질 수 있는 캐시 키 문제를 해결했습니다. (NEO-51516, NEO-49995)
* 승인이 있는 targetMapping을 사용하여 DM 게재를 보낼 때 유효성 검사 오류가 발생하는 문제를 해결했습니다. (NEO-50758)
* 게재 성능에 영향을 줄 수 있는 쿼리 관리 문제를 해결했습니다. (NEO-49991)
* 캠페인 워크플로우 게재 활동에서 외부 계정을 사용할 때 외부 계정 구성 문제가 발생하는 문제를 해결했습니다. (NEO-49959)
* 푸시 알림을 전송할 때 발생하는 성능 문제를 해결했습니다. (NEO-49953)
보고서를 내보낼 때 일본어 문자가 잘못 표시되는 문제를 해결했습니다(NEO-49308).
* Tomcat 오류 보고서에 너무 많은 오류 세부 정보가 표시되는 문제를 해결했습니다. (NEO-49029)
* 많은 수의 오퍼를 사용할 때 게재 오류가 발생할 수 있는 문제를 해결했습니다. (NEO-48807)
* **데이터 업데이트** 워크플로우 활동이 제대로 작동하지 않는 문제를 해결했습니다. (NEO-48140)
* 이메일이 아닌 외부 계정을 사용하여 게재에 대해 클릭 추적 데이터가 동기화되지 않는 문제를 해결했습니다.(NEO-47277)
* 메시지 센터 마케팅 인스턴스에서 실시간 추적 로그가 동기화되지 않는 문제를 해결했습니다. (NEO-42540)
* Snowflake 데이터베이스 테이블에 대해 작업 영역 접두사가 스키마의 검색 창에 표시되지 않는 문제를 해결했습니다. (NEO-40297)
* 이메일 콘텐츠에서 `<img-amp>` 태그가 작동하지 않는 문제를 해결했습니다. (NEO-38685)
* HTTP 릴레이를 사용할 때 메시지 센터 보관 워크플로우가 실패하는 문제를 해결했습니다. (NEO-33783)
* 이메일 콘텐츠 편집기에서 글꼴 이름 및 크기 오류를 일으킬 수 있는 문제를 해결했습니다. (NEO-61342)

## 릴리스 7.3.3 - 빌드 9359 {#release-7-3-3}

[!BADGE 제한 공개]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="제한 공개"}

>[!CAUTION]
>
>클라이언트 콘솔 업그레이드는 필수입니다. 이 [페이지](../../installation/using/installing-the-client-console.md)에서 클라이언트 콘솔을 업그레이드하는 방법을 알아보십시오.

_2023년 3월 20일_

**보안 개선**

* 보안을 최적화하기 위해 Tomcat이 버전 8.5.81에서 8.5.85로 업데이트되었습니다. (NEO-56936)

**개선 사항**

* 과금 워크플로우를 개선하여 성능을 최적화했습니다. (NEO-47658)
* 추적 워크플로우를 개선하여 게재 용량이 큰 경우의 성능을 최적화했습니다. (NEO-45064)
* 추적 관리를 개선하여 URL의 동적 매개 변수에 발생할 수 있는 문제를 해결했습니다. 이제 추적 관리 v3가 ajax 유형 URL(‘#’ 뒤에 매개 변수가 있음)을 처리하며 서드파티 도구에서 추적 URL을 수정하지 못하도록 합니다. 이 변경 사항을 적용하려면 Adobe에 문의해야 합니다. (NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

**패치**

* 컨트롤 인스턴스(트랜잭션 메시지 컨텍스트)에서 iOS 증명 푸시 알림이 보내지지 않는 문제를 해결했습니다. (NEO-54713)
* 경우에 따라 DCE(디지털 콘텐츠 편집기)의 **편집** 탭에서 스크롤할 수 없는 문제를 해결했습니다. (NEO-54474)
* 데이터 보강 활동 두 가지가 연결에 동일한 이름 식별자를 사용하여 두 번째 데이터 보강 활동이 첫 번째 활동의 링크를 사용하는 문제를 해결했습니다. (NEO-48851)

## 릴리스 7.3.2 - 빌드 9356 {#release-7-3-2}

[!BADGE 제한 공개]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="제한 공개"}

_2022년 11월 21일_

>[!CAUTION]
>
>클라이언트 콘솔 업그레이드는 필수입니다. 이 [페이지](../../installation/using/installing-the-client-console.md)에서 클라이언트 콘솔을 업그레이드하는 방법을 알아보십시오.

**호환성 업데이트**

* Adobe Campaign이 이제 PostgreSQL 14와 호환됩니다. 자세한 정보는 이 [기술 노트](../../technotes/using/tech-stack-upgrade.md)를 참조하세요.

* Microsoft Internet Explorer 11의 수명 종료에 따라 클라이언트 콘솔 환경에서 대시보드용 HTML 렌더링 엔진은 이제 Microsoft Edge Chromium을 사용합니다. (NEO-20741)

자세한 내용은 [Campaign 호환성 매트릭스](../../rn/using/compatibility-matrix.md#RDBMSservers)를 참조하십시오.

**개선 사항**

* 이제 Google BigQuery 커넥터가 부울 필드를 완전히 지원합니다. (NEO-49181)
* 이제 serverConf.xml 파일의 `Configuration for the redirection service` 섹션에서 IMS 쿠키 유효 기간을 구성할 수 있습니다. 이는 `uuid230`, `nllastdelid` 및 `AMCV_`(NEO-42541) 쿠키에 적용됩니다.
* 이제 `showSourceIP`을(를) serverConf.xml 파일의 리디렉션 노드에서 false로 설정하여 IP를 “/r/test” 요청에서 숨길 수 있습니다. [자세히 보기](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)

**사용되지 않는 기능**

* Facebook을 사용한 소셜 마케팅은 이제 더 이상 사용되지 않습니다. X(이전의 Twitter) 통합을 사용하여 소셜 미디어에 게시하거나, Adobe을 사용하여 사용자 지정 채널을 만들 수 있습니다.
* ACS 커넥터(Prime offering)는 이제 더 이상 사용되지 않습니다. 캠페인 내보내기/가져오기 기능을 사용하여 두 제품의 데이터를 추출하고 삽입할 수 있습니다.

더 자세한 내용은 [사용되지 않거나 제거된 기능 페이지](deprecated-features.md)를 참조하십시오.

**기타 변경 사항**

* 웹 로그가 향상되었습니다. 이제 관리자 권한이 있는 사용자에 대해서만 `logonEscalation` 경고가 표시됩니다. (NEO-47167)
* 오류를 방지하기 위해 **Heatmap 서비스를 위한 데이터 수집**(collectDataHeatMapService) 워크플로우가 기본적으로 중지됩니다. (NEO-33959)
* 캠페인 대시보드의 CPU 사용을 최적화하기 위해 다양한 개선 사항이 구현되었습니다. (NEO-46417)
* 충돌을 방지하기 위해 loadLibraryDebug JS 메서드를 제거했습니다. (NEO-46968)
* log4j 라이브러리에 대한 나머지 참조를 Windows의 Campaign 설치에서 제거했습니다. (NEO-44851)

**패치**

* **선택한 라인 병합** 워크플로우 옵션을 사용할 수 없는 문제를 해결했습니다. (NEO-48488)
* Adobe Campaign Enhanced MTA를 사용할 때 **성공** 게재 표시기가 올바르게 업데이트되지 않는 문제를 해결했습니다. (NEO-50462)
* 이메일 게재에서 콘텐츠 승인을 재설정할 때 다시 승인하지 못하는 문제를 해결했습니다. (NEO-44259)
* **게재 승인** 버튼이 표시되지 않는 문제를 해결했습니다. (NEO-47547)
* 큰 HTML 코드에 대해 발생할 수 있는 게재 HTML 탭의 성능 문제를 해결했습니다. (NEO-47440)
* `FeatureFlag_GZIP_Compression` 옵션이 활성화된 경우 MID 인스턴스에서 게재 로그 상태 업데이트에 영향을 주는 문제를 해결했습니다. (NEO-49183)
* 토큰 기반 인증을 사용하는 동안 실행 인스턴스에서 iOS 모바일 앱 알림을 보내지 못하는 문제를 해결했습니다. (NEO-45961)
* 동기화할 브로드로그가 너무 많으면 **게재 능력을 위해 새로 고침** 워크플로우(게재 가능성 업데이트)가 중단되는 문제를 해결했습니다. (NEO-48287)
* **메시지 센터 동기화**(mcSynch) 워크플로우를 차단한 이벤트 유형 문제를 해결했습니다.
* **쿼리** 워크플로우 활동의 추가 데이터에 **열었던 수신자** (estimatedRecipientOpen) 지표를 추가할 때 오류가 발생하는 문제를 해결했습니다. (NEO-46665)
* 같은 인스턴스에 메시지 센터 제어 및 실행 패키지를 설치할 때 실패한 **과금** 워크플로우 문제를 해결했습니다. (NEO-47674)
* 정수 대신 문자열로 기본 키가 정의된 테이블을 사용할 때 실패한 **과금** 워크플로우 문제를 해결했습니다. (NEO-46254)
* 워크플로우 이름이 너무 길 때 히트맵 필터 문제를 해결했습니다. (NEO-46301)
* Snowflake FDA 커넥터 7.3.1에 도입된 데이터 보강 중에 “0 또는 1 카디널리티 단순 링크”를 사용 시 레코드가 삭제되는 문제를 해결했습니다. (NEO-48737)
* **분할** 워크플로우 활동에서 정렬 매개변수를 사용할 때 Snowflake FFDA 문제를 해결했습니다. (NEO-45899)
* 외부 계정 구성을 저장할 수 없는 문제를 해결했습니다. 이제 파서 기능이 있는 커넥터(Snowflake 및 Google BigQuery)의 경우 연결 테스트 후 외부 계정이 자동으로 저장됩니다. (NEO-47636)
* MSSQL의 **데이터 업데이트** 워크플로우 활동에서 시간 데이터 유형을 삽입할 수 없는 문제를 해결했습니다. (NEO-47763)
* 엔진의 시간대가 설정되지 않은 경우(MSSQL에만 해당) MTA 프로세스가 충돌하는 문제를 해결했습니다. (NEO-46619)
* 이미지 노드(img)에 개인화 필드가 있는 URL이 포함된 경우 HTML 파일 가져오기 문제를 해결했습니다. (NEO-48396)
* serverConf.xml 파일에 `limit` 노드가 구성되지 않은 인스턴스에 연결하려고 할 때 HTTP 500 오류가 발생하는 문제를 해결했습니다.
* `to_nclob`과 같은 NChar가 활성화되지 않은 Oracle 유니코드 데이터베이스를 사용하는 특정 함수를 사용할 때 “문자 집합 불일치” 오류가 발생할 수 있는 문제를 해결했습니다. (NEO-49361)
* nmsDeliveryMapping 폴더에 대한 읽기 액세스 권한이 있는 사용자가 캠페인 또는 워크플로우를 실행하려고 할 때 오류가 발생하는 문제를 해결했습니다. (NEO-48230)
* `JSPContext.sqlExecWithOneParam` 함수가 작동하지 않는 문제를 해결했습니다. (NEO-50066)
* 다양한 리디렉션 오류를 수정했습니다. (NEO-50030)
