---
product: campaign
title: 최신 릴리스
description: 최신 Campaign Classic v7 릴리스 정보
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: cdbcfc5aa0614e41ce76cb777fec58fbd01797d2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 최신 릴리스 {#latest-release}

이 페이지에서는 **최신 Campaign v7 릴리스**&#x200B;의 새로운 기능, 개선 사항 및 버그 해결 사항 목록을 확인할 수 있습니다. 모든 새 빌드는 색상으로 상태가 표시됩니다. [이 페이지](rn-overview.md)에서 Campaign Classic v7 빌드 상태에 대해 자세히 알아보십시오.

## 릴리스 7.4.2  {#release-7-4-2}

### 빌드 9391 {#build-9391}

[!BADGE 제한 공개]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="제한 공개"}

_2025년 5월 12일_

이 빌드에는 다음 수정 사항이 포함되어 있습니다.

* 비 Oracle 설정에서 발생한 업그레이드 후 문제를 해결했습니다. (NEO-87012)
* 클라이언트 콘솔과 서버 모두에 영향을 주는 TLS/HTTPS 백엔드 문제를 해결했습니다. (NEO-87432)

### 빌드 9390 {#build-9390}

[!BADGE 일반 공급]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="일반 공급"}

_2025년 4월 2일_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

**보안 개선 사항**

이 릴리스에서는 여러 보안 문제를 해결합니다.

보안을 강화하기 위해 **[!UICONTROL Adobe Experience Cloud]** 외부 계정을 통한 Adobe 솔루션 및 앱 연결을 업데이트했습니다.

**주요 수정 사항**

이 릴리스에서는 다음과 같은 주요 문제가 해결되었습니다.

* TLS/SMPP 연결 - SMPP 안정성 문제를 해결했습니다.

* Google BigQuery 문제 해결:

   * 부울 데이터 유형에 대한 회귀 문제를 해결했습니다.
   * 프록시 설정 문제를 해결했습니다.
   * DATETIME 데이터 유형에 대한 회귀 문제를 해결했습니다.
   * 대량 로드 안정성 문제를 해결했습니다.
   * ODBC 버전에 대한 내부 테스트를 개선했습니다.
   * 연결 문자열의 특수 문자에 발생하는 문제를 해결했습니다.
   * Google BigQuery 쿼리에서 기본 시간 제한(5분)을 제거했습니다.

* 메일 전송 에이전트(MTA) - 분리된 MTA 하위 요소가 **[!UICONTROL Start pending]** 상태에서 중단되는 문제를 해결했습니다.


**기타 수정 사항**

이 릴리스에서는 다음 문제도 해결합니다.

* **데이터 로드(파일)** 활동이 서버에 파일을 업로드하지 못하던 문제를 해결했습니다<!--after an upgrade to version 8.3.8-->. 이제 진행이 중단되거나 콘솔 오류가 발생하지 않고 파일을 성공적으로 업로드할 수 있습니다. (NEO-47269)

* Apache 세분화 오류 문제를 해결했습니다 <!--following an upgrade to Adobe Campaign Classic 7.2.2 build 9349-->. 이 수정 패치는 코어 파일 생성을 방지하여 안정적인 서버 운영을 보장합니다. (NEO-59059)

* Google BigQuery 데이터베이스의 연결 문제를 해결했습니다 <!--after upgrading to version 7.3.3 build 9359-->. 이제 사용자가 GCP 외부 계정을 사용하여 연결을 성공적으로 테스트할 수 있습니다. (NEO-62455)

* Federated Data Access(FDA)를 사용한 Google BigQuery 테이블의 부울 및 날짜/시간 열 업데이트에 대한 호환성을 개선했습니다. 이 수정 사항은 삽입/업데이트 작업 중에 데이터 유형을 적절하도록 보장합니다. (NEO-65774)

* 공격자가 이메일 엔드포인트에 HTML 요소를 삽입할 수 있는 리소스 주입 취약점을 해결했습니다. 이 보안 개선 사항으로 무단 액세스와 피싱 시도를 방지할 수 있습니다. (NEO-66462)

* Google BigQuery 테이블에 데이터를 삽입할 때 HTTP 콘텐츠 또는 전송 인코딩 문제로 인해 간헐적으로 발생하는 오류를 해결했습니다. 이 수정 사항은 안정적인 데이터 로드 워크플로를 보장합니다. (NEO-66989)

* 워크플로 내에서 `File.list()` 메서드의 경로 탐색 취약성을 해결했습니다. 이 보안 개선 사항은 무단 디렉터리 액세스를 방지하고 중요한 파일을 보호합니다. (NEO-77898)

* SMS 게재 로그가 &quot;모바일에서 수신됨&quot; 상태로 올바르게 업데이트되지 않는 문제를 해결했습니다. 이 개선 사항은 정확한 게재 보고를 보장합니다. (NEO-78843)

* Azure Federated Data Access(FDA)를 사용할 때 Adobe Campaign Classic에서 발생하는 로그인 오류를 해결했습니다. 이제 사용자는 클라이언트 콘솔을 통해 성공적으로 로그인할 수 있습니다. (NEO-79373)

* `CCurlAzureBlobStorage::UploadStream()` 메서드로 인해 워크플로가 충돌하는 문제를 해결했습니다. 이 개선 사항은 안정적인 워크플로 실행을 보장합니다. (NEO-79598)

* 제품 보안을 강화하고 악용 위험을 완화하기 위해 Windows에서 중요한 컴파일 플래그 두 개(`ControlFlowGuard` 및 `StackProtection`)를 활성화했습니다. (NEO-80145)

* broadlog가 실패 상태일 때 이벤트 상태가 잘못 전송되는 문제를 해결했습니다. 이 개선 사항은 정확한 이벤트 보고를 보장합니다. (NEO-80245)

* POP3 OAuth 새로 고침 및 액세스 토큰이 이제 데이터베이스에 저장되고, 더 이상 새로 고침 토큰이 만료된 후 `Authentication failure: unknown user name or bad password` 오류가 표시되지 않습니다. (NEO-80683)

* 이제 Adobe Analytics에 연결할 클라이언트 ID의 값으로 Marketing Cloud(MAC) 외부 계정의 클라이언트 ID를 사용하는 대신 `XApiKey` 옵션을 사용합니다. (NEO-80434)

* inMail 사용자에게 토큰 만료로 인한 인증 오류가 발생하는 문제를 해결했습니다. 이제 사용자는 연결을 테스트하고 서버를 다시 시작하여 유사한 문제를 해결할 수 있습니다. (NEO-80683)

* 임의의 클라이언트 ID로 전환할 때에도 모든 분석 호출이 인증에 일관된 API 키(Campaign1)를 사용하도록 분석 API 기능을 개선했습니다. 이를 통해 매끄러운 분석 추적이 가능합니다. (NEO-80434)

* 사용자가 쿼리의 시간 제한 길이를 조정할 수 있도록 BigQuery Federated Data Access(FDA) 커넥터를 개선했습니다. 이 개선 사항은 오래 실행되는 쿼리의 시간 초과 오류를 방지합니다. (NEO-81222)

* 필요한 종속성을 포함하도록 Campaign <!--7.4.1--> 릴리스 업그레이드 프로세스를 업데이트했습니다. 이 개선 사항은 사용자의 업그레이드 프로세스를 간소화합니다. (NEO-81433)

* 하위 워크플로를 `enum` 필드와 함께 사용할 때 발생하는 콘솔 충돌 문제를 해결했습니다. 이 개선 사항은 안정적인 워크플로 실행을 보장합니다. (NEO-81864)

* MTA 하위 프로세스가 중단되어 게재 슬롯이 막히는 문제를 해결했습니다. 이 수정 사항은 푸시 및 WhatsApp 커뮤니케이션에 대한 원활한 게재 작업을 보장합니다. (NEO-82351)

* 일시 중지된 게재 활동으로 인해 게재가 개인화 보류 중 상태에서 멈추는 문제를 해결했습니다. 이 개선 사항은 성공적인 게재 실행을 보장합니다. (NEO-82781)

* 인증에 CampaignIO 엔드포인트를 활용하여 IMS 로그인 기능을 개선했습니다. 이 개선 사항은 로그인 프로세스를 간소화합니다. (NEO-82838)

* 핫픽스 배포 후 안정적인 쿼리 실행을 위해 Google BigQuery Federated Data Access(FDA) 시간 초과 오류를 다시 해결했습니다. (NEO-82923)

* 대용량 데이터를 Teradata 테이블로 로드할 때 발생하는 공간 문제를 해결했습니다. 이 개선 사항은 안정적인 데이터 로드 작업을 보장합니다. (NEO-83252)

* 날짜와 타임스탬프 비교가 일치하지 않아 GCP 쿼리가 실패하는 문제를 해결했습니다 <!--after upgrading to version 9383-->. 이 개선 사항은 쿼리 호환성을 보장합니다. (NEO-83826)

* 일시 중지된 게재 활동을 다시 시작하면 게재에 실패하는 문제를 해결했습니다. 이 수정 사항은 성공적인 게재 실행을 보장합니다. (NEO-83809)

* 비공개 키 인증을 사용할 때 Snowflake Federated Data Access(FDA) 커넥터에서 발생하는 인증 오류를 수정했습니다. 이 개선 사항은 성공적인 데이터베이스 연결을 보장합니다. (NEO-84024)

* 중단된 프로세스로 인한 MTA 하위 슬롯 차단을 해결하기 위해 워치독 변경을 구현했습니다. 이 개선 사항은 원활한 게재 작업을 보장합니다. (NEO-84553)

* 작업 중인 프로세스로 인해 발생하는 MTA 하위 슬롯 차단을 해결하기 위해 Javascript 대기 검사를 강화했습니다. 이 수정 사항은 안정적인 게재 작업을 보장합니다. (NEO-85150)

