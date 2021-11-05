---
product: campaign
title: 최신 릴리스
description: 최신 Campaign Classic 릴리스 정보
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: ebd5b04c30c54142433056904a5d80f5a8744ded
workflow-type: tm+mt
source-wordcount: '2459'
ht-degree: 100%

---

# 최신 릴리스{#latest-release}

![](../../assets/v7-only.svg)

이 페이지에서는 **최신 Campaign Classic 릴리스**&#x200B;의 새로운 기능, 개선 사항, 버그 해결 사항 목록을 확인할 수 있습니다.

[이 페이지](rn-overview.md)에서 캠페인 빌드 상태를 이해할 수 있습니다.


## ![](assets/do-not-localize/green_2.png) 릴리스 21.1.4 - 빌드 9343 {#release-21-1-4-build-9343}

_2021년 10월 8일_

**패치**

* **상호 작용** 모듈을 사용할 때 [파워 부스터](../../installation/using/power-booster-and-power-cluster.md) 옵션을 설정한 경우 오퍼 관리가 적절하게 이루어지지 않는 문제를 해결했습니다. (NEO-39263)

* 다중 중간 소스 인스턴스에서 두 개 이상의 IP 친화성을 사용할 때 게재 전송 중 [중간 서버 xxx에서 ip 친화성 xxx를 찾을 수 없음] 오류가 발생하는 현상을 해결했습니다. (NEO-37514)


## ![](assets/do-not-localize/orange_2.png) 릴리스 21.1.4 - 빌드 9342 {#release-21-1-4-build-9342}

_2021년 9월 7일_

**보안 개선**

* 디렉토리 횡단 공격으로부터 보호를 강화하기 위해 보안 문제를 해결했습니다. (NEO-28547)

**개선 사항**

* 수명 종료에 따라 Flash를 Campaign의 기능과 구성 요소에서 제거하고 HTML5로 대체했습니다. 차트의 **측정** 유형이 제거되었습니다. (NEO-30330) [자세히 보기](../../reporting/using/creating-a-chart.md)
* 이제 Windows에 클라이언트 콘솔을 설치할 때 설치 관리자에서 상위 레지스트리 노드가 있는지 확인하고 누락된 경우 클라이언트 콘솔을 만듭니다. 따라서 콘솔을 시작할 때 발생할 수 있는 문제를 방지할 수 있습니다. (NEO-34854)
* 서드파티 도구(이메일 클라이언트, 인터넷 브라우저 등)의 특수문자 처리 방식과 관련된 오류를 방지하기 위해 추적 서명 기능이  개선되었습니다. 이제 URL 매개 변수가 인코딩됩니다.

**기타 변경 사항**

* 사용 종료된 Microsoft CRM 커넥터(Office 365 및 온프레미스 배포)를 인터페이스에서 제거했습니다. [자세히 알아보기](../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft)
* Tomcat 8로 마이그레이션한 후 IIS 설정 스크립트를 업데이트하여 IIS 통합 문제를 해결했습니다. (NEO-31019)
* [청구 기술 워크플로우](../../production/using/monitoring-processes.md#billing-report)를 마케팅 인스턴스에서만 실행할 수 있도록 하기 위해 가드레일이 추가되었습니다.
* 워크플로우 전환의 **모집단 보기** 창에서 데이터 및 스키마 탭에서 데이터 소스 식별이 개선되었습니다.
* 데이터베이스 업데이트 문제를 방지하기 위해 누락된 데이터베이스 인덱스가 xtk:rights, nms:dlvExclusion, nms:seedMember, nms:trackingUrl 스키마에 추가되었습니다. 

**패치**

* 오퍼가 게재에 연결되어 있을 때 핫 클릭 보고서가 작동하지 않는 문제를 해결했습니다. (NEO-26295)
* 실행 시 출력 테이블이 생성되지 않는 경우 발생하는 **하위 워크플로우** 활동 문제를 해결했습니다. (NEO-36242)
* **설명 분석** 보고서를 PDF로 내보낼 때 발생하는 다양한 문제를 해결했습니다. (NEO-25847)
* 외부 메일 전송을 사용할 때 게재 실패를 유발할 수 있는 문제를 해결했습니다. (NEO-37435)
* 웹 API를 사용하여 Microsoft CRM에 연결할 때 발생하는 오류를 수정했습니다. 기능에 영향을 주지 않으므로 오류 메시지를 제거했습니다.
* 추적과 마케팅 서버 간의 중계기로 Mid 서버가 설정되었을 때 발생하는 추적 로그 중복 제거 문제를 수정했습니다. (NEO-36285)
* Vault가 특정 코드 저장소로 사용되지 않는 회귀 문제를 해결했습니다.
* 수신되는 전환이 FDA 데이터 소스에서 온 경우 **데이터 보강** 워크플로우 활동에서 변수를 사용할 수 없는 문제를 해결했습니다.
* 이메일 메시지에서 URL의 손상을 유발할 수 있는 문제를 해결했습니다.

## ![](assets/do-not-localize/orange_2.png) 릴리스 21.1.3 - 빌드 9330 {#release-21-1-3-build-9330}

_2021년 6월 5일_

**새로운 기능**


<table>
<thead>
<tr>
<th><strong>새로운 워크플로우 활동: 데이터 소스 변경</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>새로 추가된 <b>데이터 소스 변경</b> 워크플로우 활동을 사용하면 워크플로우의 작업 테이블의 데이터 소스를 변경할 수 있습니다. 이를 통해 다양한 데이터 소스(FDA 및 로컬 데이터베이스)에서 데이터를 유연하게 관리할 수 있습니다.</p>
<p>Adobe Campaign 워크플로우에서 데이터는 작업(또는 임시) 테이블을 사용하여 관리됩니다. 워크플로우를 실행하면 작업 테이블이 여러 워크플로우 활동 간에 데이터를 공유합니다. 기본 설정에서 작업 테이블은 쿼리하는 데이터의 소스와 동일한 데이터베이스에 생성됩니다.</p>
<p>자세한 내용은 <a href="../../workflow/using/change-data-source.md">세부 설명서</a>를 참조하세요.</p>
</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr>
<th><strong>Adobe Journey Orchestration과 통합</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>이제 Journey Orchestration과 Adobe Campaign Classic 간의 통합이 GA됩니다. 이를 통해 Journey Orchestration은 Adobe Campaign Classic 트랜잭션 메시지 기능을 사용하여 이메일, 푸시 알림 및 SMS를 전송할 수 있습니다.</p>
<p>Journey Orchestration 인스턴스와 Campaign Classic 인스턴스 간의 연결은 프로비저닝 시 Adobe에 의해 설정됩니다.</p>
<p>자세한 내용은 <a href="https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=ko">Journey Orchestration 설명서</a>를 참조하십시오. 이 <a href="https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=ko">섹션</a>에 단계별 사용 사례가 나와 있습니다</p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>LINE 채널 개선 사항</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>LINE 채널에 다음과 같은 개선 사항이 추가되었습니다.
</p>
<ul> 
<li><p>LINE 비디오 메시지 유형 지원</p></li>
<li><p>LINE 파트너 등록 API 지원</p></li>
<li><p>LINE 서버 측 오류 또는 네트워크 시간제한 이벤트에서 메시지 전송을 다시 시도할 수 있도록 지원합니다.</p></li>
</ul>
<p>자세한 내용은 <a href="../../delivery/using/line-channel.md">세부 설명서</a>를 참조하십시오.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Vertica FDA 커넥터</strong><br/> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>이제 Adobe Campaign Classic 인스턴스를 Vertica 외부 데이터베이스에 연결할 수 있습니다. 이 연결은 새 외부 계정을 통해 관리됩니다.</p>
<p>자세한 내용은 <a href="../../installation/using/configure-fda-vertica.md">세부 설명서</a>를 참조하십시오.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Google Big Query FDA 커넥터</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>이제 Adobe Campaign Classic 인스턴스를 Google Big Query 외부 데이터베이스에 연결할 수 있습니다. 이 연결은 새 외부 계정을 통해 관리됩니다.
</p>
<p>자세한 내용은 <a href="../../installation/using/configure-fda-google-big-query.md">세부 설명서</a>를 참조하십시오.</p>
</td> 
</tr> 
</tbody> 
</table>

**향상된 보안 기능**

* 전체 데이터베이스 연결 세부 정보를 반환하는 **xtk:session#GetCnxInfo** API 메서드에 대한 액세스는 이제 관리 사용자로만 제한됩니다. (NEO-27779)
* 사용되지 않는 decryptString 함수가 CRM 관련 JavaScript 파일에서 decryptPassword로 대체되었습니다.
* 추적 서명 기능은 타사 도구(이메일 클라이언트, 인터넷 브라우저, 안전한 링크 보안 도구)가 추적된 링크를 수정할 때 리디렉션 오류 추적을 줄이기 위해 개선되었습니다.
* 대문자를 포함할 때 추적된 URL이 작동하지 않는 문제를 수정했습니다. 추적된 URL 서명 메커니즘은 이제 대소문자를 구분합니다. (NEO-28414)

**호환성 업데이트**

이제 다음 시스템이 Campaign에서 지원됩니다.
* Google Big Query FDA 커넥터
* Vertica FDA 커넥터
* PostgreSQL 13

자세한 내용은 [Campaign 호환성 매트릭스](../../rn/using/compatibility-matrix.md)를 참조하십시오.

**사용되지 않는 기능**

* Campaign 21.1 릴리스부터 Adobe Analytics 데이터 커넥터는 사용 중단됩니다. 이 커넥터를 사용하는 경우 새로운 커넥터인 Adobe Analytics 커넥터에 맞게 구현을 조정해야 합니다.
자세한 내용은 [세부 설명서](../../technotes/using/aa-connector-migration.md)를 참조하십시오.
* Debian 8에 대한 지원은 이제 중단되었습니다.
* 20.3에서 Oracle CRM의 사용 중단 이후, 관련 외부 계정이 인터페이스에서 제거되었습니다.

더 자세한 내용은 [사용되지 않거나 제거된 기능 페이지](../../rn/using/deprecated-features.md)를 참조하십시오.

**개선 사항**

* 워크플로우를 저장할 때 활동 이름이 고유하고 전환 뒤에 활동이 표시되는지 확인하기 위한 추가 검사가 추가되었습니다.
* 이제 **청구(billing)** 기술 워크플로우에는 이전에 제거되었던 **활성 청구 프로필 수**(billingActiveContactCount) 워크플로우에서 원래 수행한 작업이 포함됩니다. 워크플로우가 매월 보내는 이메일 보고서는 이제 인스턴스의 활성 프로필 수에 대한 정보를 제공합니다. [자세한 내용](../../workflow/using/about-technical-workflows.md).
* 메모 데이터 작업에 키를 사용할 수 있도록 새 **_keyOnMData** 특성이 추가되었습니다.

**기타 변경 사항**

* Windows용 openssl 타사 버전이 버전 1.1.1h로 업데이트되었습니다.
* Debian 패키지 설명에서 nlserver가 Adobe Campaign Classic 서버로 변경되었습니다.

**패치**

* 사용자가 설정된 시간 후에도 계속 로그인한 상태로 남아 있는 특정 시간 후에 사용자를 로그아웃하도록 세션 시간제한을 편집할 때 발생하는 문제를 수정했습니다.
* 게재가 읽기 전용으로 표시되었지만, 게재 속성에서 계속 편집할 수 있는 문제가 해결되었습니다.
* 웹 애플리케이션을 디자인할 때 편집 도구 모음이 사라지는 오류를 수정했습니다.
* 이메일에 링크를 추가할 때 Adobe Campaign Classic 헤더가 있는 이메일의 텍스트 버전을 표시하는 오류를 수정했습니다. (NEO-29211
* HTTPs 연결을 통해 FDA를 사용할 때 **중간 소싱(게재 로그)**(defaultMidSourcingLog) 워크플로우가 **NmsMidSourcing_LogsPeriodHour** 옵션에 의해 설정된 시간대에 중단되었습니다. 이렇게 하면 이 설정 일정 후에 발생한 데이터로 레코드가 업데이트되지 않습니다. (NEO-30833)
* 메시지 센터 동기화 워크플로우를 실행한 후 발생하는 문제를 해결했습니다. 게재 개체 폴더를 사용자 지정 폴더로 이동할 때마다 워크플로우는 게재를 일반 **트랜잭션 메시지 기록** 폴더로 다시 이동합니다. (NEO-27445)
* **브로드캐스트 통계**, **추적 표시기** 및 **공유 활동 통계** 보고서를 표시하려고 할 때 오류 메시지가 표시되는 문제를 수정했습니다.
* **Oracle On Demand** 워크플로우 활동이 Oracle CRM 커넥터 사용 중단 후 인터페이스에서 제거되었습니다.
* 워크플로우 서버(wfserver) 모듈이 매일 다시 시작한 후 처리 워크플로우 실행이 중지되는 문제를 해결했습니다. (NEO-30047)
* MX 관리 문서가 업데이트되지 않고 IP 평판에 부정적인 영향을 줄 수 있는 문제를 해결했습니다. (NEO-29897)
* SOAP 호출을 받을 때 웹 프로세스 충돌이 발생하는 문제를 해결했습니다. (NEO-28796) (NEO-29600)
* SAP HANA FDA 색인 작성에 실패하는 문제를 해결했습니다. (NEO-29664)
* 헤더가 포함된 SOAP 호출을 수행할 때 트랜잭션 메시지를 **대기 중** 상태에 남겨 놓을 수 있는 문제를 해결했습니다. (NEO-28737)
* Teradata FDA 커넥터를 사용할 때, 모든 임시 테이블이 클러스터의 한 노드에서만 생성되고, 이로 인해 전체 스풀 공간이 소모되며 Teradata 충돌이 발생할 수 있는 문제를 해결했습니다. 이제 임시 테이블이 여러 노드에서 생성됩니다. (NEO-28230)
* 추적 태그가 **nms:trackingURL** 스키마에 잘못된 기본 키를 생성하는 웹 애플리케이션을 사용할 때 발생하는 문제를 수정했습니다. (NEO-27931)
* 오류 메시지의 정확성을 보장하기 위해 ODBC 3.x와의 호환성이 향상되었습니다.
* 사용자 지정 콘텐츠 템플릿을 이메일 게재에서 사용할 때 콘솔 충돌이 발생하는 문제를 수정했습니다. (NEO-31547)
* 느린 연결 또는 큰 응답 크기로 인해 Tomcat에서 유효한 응답을 보내지 못하는 문제를 해결했습니다.
* PostgreSQL 데이터베이스에서 UUID를 읽을 때 발생할 수 있는 문제를 수정했습니다.
* 오퍼에 연결된 제안 데이터를 검색할 때 성능 문제가 발생하는 문제를 해결했습니다. (NEO-27554)
* IMS 서비스가 활성화되었으나 응답이 없는 경우 웹 프로세스가 응답하지 않는 문제를 해결했습니다.
* 게재 개인화에 실패한 특정 조인 메커니즘으로 인해 증명 그룹과 함께 게재를 보낼 수 없는 문제를 수정했습니다. (NEO-14391)
* 쿼리 및 데이터 보강 활동이 게재 테이블을 타겟팅한 경우 경고 활동으로 경고를 보내지 못하는 문제를 해결했습니다. (NEO-25157)

## ![](assets/do-not-localize/red_2.png) 릴리스 21.1.2 - 빌드 9282 {#release-21-1-2-build-9282}

_2021년 4월 15일_

* 암호 관리가 보안을 최적화하기 위해 개선되었습니다.
* MTA 작동 중단을 발생시킬 수 있는 문제를 수정했습니다.

## ![](assets/do-not-localize/red_2.png) 릴리스 21.1.1 - 빌드 9277 {#release-21-1-1-build-9277}

_2021년 2월 22일_

**향상된 보안 기능**

* 보안을 최적화하도록 콘솔 인증 메커니즘이 개선되었습니다. (NEO-26944)
* SSRF(Server Side Request Forgery) 공격으로부터 보호를 강화하기 위해 보안 문제를 해결했습니다. (NEO-28532)

**호환성 업데이트**

이제 다음 시스템이 Campaign에서 지원됩니다.

* Salesforce API 버전 49가 이제 Salesforce CRM 외부 계정을 사용할 때 지원됩니다.

**사용되지 않는 기능**

이제 **기술 제공 모니터링** 보고서를 더 이상 사용하지 않습니다.

더 자세한 내용은 [사용되지 않거나 제거된 기능 페이지](../../rn/using/deprecated-features.md)를 참조하십시오.

**개선 사항**

**EFS(이메일 피드백 서비스)**&#x200B;는 Enhanced MTA의 피드백을 바로 캡처하여 보고 정확도를 향상하는 확장 가능한 서비스입니다. 이 기능은 개인 베타 버전으로 출시되며 모든 고객은 향후 릴리스에서 점진적으로 사용할 수 있습니다.

* 이제 완벽하고 정밀한 보고를 위해 모든 카테고리의 피드백을 캡처합니다.
* 이제 게재됨 표시기의 계산은 정확도 및 반응도 향상을 위해 Enhanced MTA의 실시간 피드백을 기반으로 합니다.
* EFS는 동기식 소프트 바운스 보고로 지연되는 문제를 해결합니다.

자세한 내용은 [세부 설명서](../../delivery/using/sending-with-enhanced-mta.md#efs)를 참조하십시오.
이 개인 베타에 참가하려면 [양식](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u)을 작성해 주십시오. 그러면 연락을 드리겠습니다.

**기타 변경 사항**

* 압축을 사용하여 큰 추적 로그에 대한 전송 속도가 향상되었습니다.
* 여러 작업으로 워크플로우를 실행 시 시간 초과를 방지하기 위해 Workflow Heatmap을 개선했습니다. (NEO-27423).
* 종료 날짜가 지나도 오퍼를 표시할 수 있는 문제를 해결했습니다. 이제 Campaign Classic은 종료 날짜만 계산하지 않고 전체 타임스탬프를 고려합니다. (NEO-27590)
* Google+ 링크가 **소셜 네트워크 공유 링크** 개인화 블록에서 제거되었습니다.
* 마지막 릴리스에서 버그 수정 구현 후 문제를 해결했습니다. SMS 게재 실패를 유발하는 SSL/TLS를 통해 연결할 때 호스트 이름에 검사가 추가되었습니다. 프록시가 있는 POP3, SMS, HTTP 등 대부분의 프로토콜에 대해 호스트 이름 확인이 비활성화되었으며, SMS 외부 계정에 대한 인증서 검사가 3가지 값으로 향상되었습니다(NEO-29581). [자세히 알아보기](../../delivery/using/sms-protocol.md#skip-tls)

**패치**

* Tab, Enter 및 Escape 단축키가 새 로그온 화면에서 작동하지 않던 문제를 해결했습니다.
* 새로 만든 워크플로우의 이름이 저장 후 기본값으로 대체되는 새로 고침 문제를 해결했습니다(NEO-26106).
* 워크플로우를 실행할 때 **외부 파일** 타겟 매핑을 사용하여 **게재** 활동 이전에 **데이터 보강** 활동의 일부로 새 필드가 추가되는 문제가 해결되었습니다. 원치 않는 필드가 **외부 파일** 타겟 매핑에 추가되었습니다. (NEO-27687)
* 이전에 만들어 저장한 웹 애플리케이션을 다시 열 때 소스 코드의 일부 문자가 변경되는 문제를 해결했습니다. (NEO-27597)
* 링크 추적을 위한 새 서명 메커니즘을 포함한 빌드로 업그레이드할 때 발생할 수 있는 문제가 해결되었습니다(빌드 19.1.4 및 Campaign 20.2부터). 여러 템플릿이 하나의 이벤트에 연결되어 있는 경우 업그레이드하면 트랜잭션 메시지를 보낼 때 잘못된 템플릿이 선택될 수 있습니다. (NEO-28326)
* MTA가 응답하지 않고 다시 시작하지 않으면 게재를 처리할 수 없는 문제를 해결했습니다. (NEO-27455)
* 날짜/시간 형식 열에 대한 대량 로드 작업 중 타임스탬프 관리와 관련된 MSSQL 데이터베이스의 문제를 수정했습니다.
* Redshift xtk 함수를 사용할 때 발생하는 워크플로우 쿼리 문제를 해결했습니다. 이제 SubDays, SubSeconds, SubMinutes 및 SubHours는 두 Redshift 타임스탬프 유형(NEO-24962)을 모두 허용합니다.
* 익명 액세스 권한이 있는 보고서를 미리 보기할 때 스크립트 오류 메시지가 표시되는 문제를 해결했습니다. (NEO-27081)
* 게재 분석을 수행할 때 서버의 메모리 사용을 줄일 수 있는 문제를 해결했습니다.
* 복잡한 특정 쿼리를 실행하려 할 때 인스턴스가 작동하지 않는 문제를 해결했습니다.
* **Twitter 페이지 동기화** 기술 워크플로우가 실행되지 않는 문제를 해결했습니다. (NEO-28634)
* **트윗(twitter)** 게재 템플릿을 사용하여 Twitter에 게시하려고 할 때 decryptPassword 기능과 관련된 오류 메시지를 표시할 수 있는 문제를 수정했습니다. (NEO-28216)
* 워크플로우에서 **JavaScript** 활동을 사용하여 HTTP 요청을 할 때 발생하는 문제를 해결했습니다. 호스트 이름에서 포트 번호를 정의한 후 다음 오류로 호출이 실패합니다(NEO-29146).

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* 타켓 데이터 개인화를 통한 새 게재를 보낼 수 없는 문제를 해결했습니다(NEO-30323).
* 마케팅 인스턴스에서 코어 파일을 발생시키는 몇 가지 충돌 문제를 해결습니다.
* 다음 오류로 인해 **추적** 워크플로우가 실패하던 문제를 해결했습니다(NEO-25206).

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* 캠페인의 **타겟팅 및 워크플로우** 탭 내에서 게재를 만들고 저장할 때 발생하는 문제를 해결했습니다. 다음 오류로 미리 보기가 실패합니다(NEO-29440).

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* 마케팅 인스턴스와 Adobe Campaign Standard 인스턴스 또는 Campaign Classic 중간 소싱 인스턴스 간에 외부 계정을 설정하고 &quot;DisableFOH2=1&quot; 옵션을 사용할 때 발생하는 오류를 해결했습니다. 외부 계정에서 &quot;DisableFOH2=1&quot; 옵션을 사용할 때 연결이 올바르게 닫혀 있지 않고 충돌하면 다음 오류가 발생합니다(NEO-26258).

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* 서버와 공급자 간에 연결 문제가 발생하는 경우 SMS 오류를 해결습니다. 그러면 MTA 하위 모듈에 의해 연결이 자동으로 비활성화됩니다. 새 하위 모듈이 시작되지 않은 경우 Adobe Campaign Classic은 이 실패한 연결에 연결하지 않습니다.
