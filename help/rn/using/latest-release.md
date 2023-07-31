---
product: campaign
title: 최신 릴리스
description: 최신 Campaign Classic v7 릴리스 정보
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 100%

---

# 최신 릴리스{#latest-release}

이 페이지에서는 **최신 Campaign v7 릴리스**&#x200B;의 새로운 기능, 개선 사항 및 버그 해결 사항 목록을 확인할 수 있습니다. 모든 새 빌드는 색상으로 상태가 표시됩니다. [이 페이지](rn-overview.md)에서 Campaign Classic v7 빌드 상태에 대해 자세히 알아보십시오.

## 릴리스 7.3.3 - 빌드 9359 {#release-7-3-3}

[!BADGE 일반 공급]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="일반 공급"}

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

* Facebook을 사용한 소셜 마케팅은 이제 더 이상 사용되지 않습니다. Twitter 통합을 사용하여 소셜 미디어에 게시하거나 Adobe를 사용하여 사용자 지정 채널을 만들 수 있습니다.
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
