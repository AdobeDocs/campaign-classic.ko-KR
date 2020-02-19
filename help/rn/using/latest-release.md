---
title: 최신 릴리스
description: 최신 릴리스
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1206b2dcee8a4b0e95a005e47b947b00388e7e43

---


# 최신 릴리스{#latest-release}

[업그레이드](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) 빌드| [제어판 릴리스](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) | [설명서 업데이트](../../rn/using/documentation-updates.md) | [이전 릴리스](../../rn/using/release--19-2.md) | [더 이상 사용되지 않는 기능](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>일반 가용성</strong></td>
   <td><img src="assets/blue3.png"/><strong>릴리스 후보</strong></td> 
   <td><img src="assets/orange3.png"/><strong>더 이상 사용할 수 없음</strong></td> 
   <td><img src="assets/red3.png"/><strong>가치 하락</strong></td> 
  </tr> 
   <tr> 
   <td>최신 안정적인 빌드를 사용할 수 있습니다. <br>프로덕션에서 인증 강화 </td>
   <td>Adobe에서 인증한 빌드. <br>프로덕션 확인 대기 중입니다. </td>
   <td>버그 수정을 통해 새로운 빌드를 사용할 수 있습니다. <br>업데이트가 필요합니다. </td>
   <td>알려진 회귀 포함 <br>업데이트는 필수입니다. </td>
  </tr> 
 </tbody> 
</table>

안정적인 [마지막 빌드](../../rn/using/release--19-1.md#release-19-1-4-build-9032) (GA)를 보려면 **** 여기를 클릭하십시오.

## ![](assets/blue-2.png) 릴리스 20.1 - 빌드 9122 {#release-20-1-build-XXXX}

_2020년 2월 17일_

**새로운 기능**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Snowflake FDA Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake는 스토리지 및 컴퓨팅 수준에서 확장할 수 있도록 구축된 완전히 관리되는 클라우드 데이터 웨어하우스입니다. 이제 Adobe Campaign은 이 새로운 커넥터를 통해 Snowflake의 강력한 기능을 활용하여 빅데이터 세그멘테이션을 수행할 수 있습니다. 이 커넥터는 Adobe에서 호스팅하는 모든 고객에게 제공됩니다.</p>
    <p>자세한 내용은 <a href="../../platform/using/specific-configuration-database.md#configure-access-to-snowflake">자세한 설명서</a> 및 <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/fda/big-data-segmentation-on-snowflake.html.">자습서 비디오를</a>참조하십시오.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Hadoop FDA 커넥터 개선 사항</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Hadoop FDA Connector가 Hadoop 3.0 및 Cloudera을 지원하도록 개선되었습니다.</p>
    <p>자세한 내용은 <a href="../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3">자세한 설명서를</a>참조하십시오.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

* 클릭재킹으로부터 보호하기 위해 보고서 구성의 보안을 개선했습니다. 이는 새 보고서에 적용됩니다. 이전 보고서의 경우 변경 사항을 적용하려면 다시 게시해야 합니다. (NEO 파섹)

* cryptString의 작은 메모리 문제를 해결합니다. (NEO 파섹)

* 내부 IP 노출 문제를 해결하기 위해 모니터 JSP가 개선되었습니다. (NEO 파섹)

* 관리자가 아닌 사용자에게 스택 추적 정보를 표시할 수 있는 문제를 해결했습니다. (NEO 파섹)

* 이전 세션에서 캐시된 데이터 관리를 개선했습니다. (NEO 파섹)

* logins.log 파일이 IMS를 통한 성공적인 로그인 시도를 기록하지 못했던 문제를 수정했습니다. (NEO 파섹)

**향상된 기능**

* iOS 13은 이제 HTTP2 커넥터에서 지원됩니다.

* 푸시 알림 기능(nms:address 및 nms:appSubscriptionRcp)에서 사용하는 표의 정리 및 격리 관리가 개선되었습니다. iOS(HTTP2 커넥터 전용)의 경우 이제 비활성화된 토큰은 Android의 경우와 동일하게 처리됩니다. 이제 NmsAppSubscriptionRcp 테이블에서 disable 플래그가 설정됩니다. [자세한 내용](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* JavaScript 코드 및 **고급 JavaScript 코드** 워크플로우 활동에 시간 초과 **기간을 정의하는 새로운 옵션이 추가되었습니다** . 이렇게 하면 javascript 실행 단계가 너무 오랫동안 실행되지 않습니다. 제한 시간이 경과하면 워크플로우가 중지됩니다. 기본 제한 시간은 1시간입니다. [자세한 내용](../../workflow/using/sql-code-and-javascript-code.md)

* 이제 mid-sourcing 서버에서 일치하는 관련성이 없으면 배달 분석이 중지되고 해당 오류 메시지가 표시됩니다.

* 이제 게시물에 대한 데이터베이스 장애 조치(failover)가 지원됩니다.데이터베이스 서버가 충돌하고 다시 시작하면 Campaign이 자동으로 다시 연결됩니다.

* [ **시작 보류** 중] 보기가 [관리] > [감사] > [워크플로우 상태] 노드에 추가되었습니다. 이렇게 하면 작업 관리 **프로세스에 의해 시작되기를 기다리는 인스턴스의 모든 워크플로우를 모니터링할 수** 있습니다. 이 보기는 마케팅 캠페인 패키지와 함께 제공됩니다. [자세한 내용](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**기타 변경 사항**

* Linux의 경우, 이제 Nlserver 서비스 시작 시 /etc/init.d/nlserver6 스크립트 대신 시스템 장치를 사용합니다. 20.1 패키지를 설치하면 새 시작 구성표로 마이그레이션됩니다. /etc/init.d/nlserver6는 여전히 제공되지만, nlserver 서비스와 상호 작용(시작, 다시 시작, 중지 등)하려면 systemctl 명령을 직접 사용하는 것이 좋습니다.

* 가장 많이 사용되는 사용자 정의 테이블이 xtkNewId **시퀀스에서** 전용 시퀀스로 이동되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* 불필요한 데이터베이스 연결의 영향을 받을 수 있는 쿼리 성능이 개선되었습니다.

* 데이터베이스 업데이트 마법사의 성능을 개선했습니다.

* 데이터베이스 레코드 관리가 향상되었습니다.

* 연결 풀의 견고성이 개선되어 예기치 않은 연결 오류가 너무 자주 발생하지 않을 수 있습니다.

* 소프트 오류가 발생하는 경우 격리에 주소를 보내는 이메일 주소 유효성 검사 규칙이 향상되었습니다. [자세한 내용](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Debian의 경우 Campaign은 이제 시스템 PCRE 라이브러리를 사용할 수 있을 때 사용합니다.

* 이제 Campaign에서 최신 시스템 ODBC 라이브러리를 사용할 수 있습니다.

* 리치 이미지를 로드하기 위한 연결을 열 때 LINE 서블릿에 시간 초과가 추가되었습니다. 이미지를 로드하는 데 시간이 너무 오래 걸리는 경우 서블릿이 연결을 중지하여 병목 현상을 방지합니다.

**패치**

* Hadoop 커넥터를 사용할 때 계정 키 암호화 문제가 해결되었습니다.

* Windows 서버에서 사용자 연결이 실패하는 SSL 인증 구현으로 인한 회귀 문제를 해결했습니다. (NEO 파섹)

* 부정적인 워크플로우 ID의 경우 증분 쿼리 활동 문제를 수정했습니다. (NEO 파섹)

* Netezza FDA 커넥터를 통해 쿼리를 실행할 때 발생하는 인코딩 문제를 해결했습니다. (NEO 파섹)

* 웹 다운로드 워크플로우 이벤트 활동에서 POST 메서드를 사용할 때 오류가 **발생하는** 문제를 해결했습니다.

* 오퍼 제안 생성과 관련된 문제를 수정했습니다. (NEO 파섹)

* 획득 웹 양식 템플릿을 사용할 때 바닥글 표시 문제가 해결되었습니다.

* 연속 게재 컨텐츠에서 URL을 구문 분석할 때 충돌이 발생할 수 있는 문제를 수정했습니다. (NEO 파섹)

* 새 캠페인을 만들 때 시작 **및** 종료 **필드가** 계산되지 않는 문제를 해결했습니다.

* URL을 사용할 **때 파일 다운로드** 워크플로우 활동 문제를 수정했습니다.

* 보고서의 쿼리 활동에서 가져온 목록을 미리 볼 때 발생하는 문제를 수정했습니다. (NEO 파섹)

* 이메일 편집기에서 Powered by Campaign **개인화 블록을 선택할 때** 오래된 이미지가 표시되는 문제를 해결했습니다.

* 클라이언트와 서버 간의 네트워크 통신이 개선되었습니다.

* 동일한 캠페인에서 너무 많은 워크플로우가 만들어지던 문제를 수정했습니다. 이제 28개 이상의 워크플로우를 만들 수 없습니다. 경고가 표시됩니다.

* 조합 워크플로우 활동에서 열 **선택** 조정 옵션을 사용할 때 **발생하는 문제를** 수정했습니다.

* 워크플로우에서 손상된 농축 목록을 사용할 때 발생할 수 있는 콘솔 충돌 문제가 수정되었습니다. (NEO 파섹)

* 워크플로우에서 발생할 수 있는 다양한 콘솔 충돌 문제가 해결되었습니다(NEO-18010, NEO-18032).

* 외부 신호 **** 워크플로우 활동이 비활성화되었을 때에도 실행될 수 있었던 문제를 수정했습니다. (NEO 파섹)

* 새 스키마를 만들 때 발생하는 문제를 수정했습니다.

* SMS 메시지를 보낼 때 발생하는 추적 문제를 수정했습니다. (NEO 파섹)

* 게재 표시기에 잘못된 타깃팅된 대상 번호가 표시되던 문제를 수정했습니다.

* 워크플로우 활동을 통해 설명 보고서를 생성할 때 잘못된 백분율을 표시하는 문제를 해결했습니다. (NEO 파섹)

* 시간 보기 매개 변수 시 배달 처리량 보고서가 다른 숫자를 표시하는 문제를 해결했습니다. (NEO 파섹)

* 추적 워크플로에서 트랜잭션 메시지 추적 표시기가 업데이트되지 않는 문제를 해결했습니다. (NEO 파섹)

* SOAP를 통해 오퍼를 요청할 때 웹 프로세스가 중단되고 다시 시작되는 회귀 문제를 해결했습니다. (NEO 파섹)

* 업로드 디렉터리가 원격 공유 위치인 경우 공개 리소스에 데이터를 업로드할 수 없는 문제를 해결했습니다. (NEO 파섹)

* Adobe Experience Cloud **기술 워크플로우에서 대상** 가져오기가 지속적으로 실패하는 문제를 해결했습니다. (NEO 파섹)

* Experience Manager에서 가져온 템플릿을 사용할 때 배달이 전송되지 않던 문제를 수정했습니다. (NEO 파섹)

* 9032를 빌드하도록 업그레이드하고 SSL 프로토콜을 통해 인스턴스가 FTP 서버에 연결되지 않는 문제가 해결되었습니다. (NEO 파섹)

* FDA 스키마를 타깃팅 차원으로 사용하는 워크플로우에서 데이터 업데이트 **활동을 사용하여 대량의 데이터를** 삭제, 삽입 또는 업데이트할 때 발생하는 문제를 수정했습니다. (NEO 파섹)

* 태그 외부에서 &#39;if&#39; 문을 사용할 때 이메일이 전송되지 않던 문제를 `body` 수정했습니다.

* 전송된 메시지의 배달 로그에서 미러 페이지를 표시하려고 할 때 발생하는 문제를 수정했습니다. (NEO 파섹)

* 배달에서 HTML 가져오기를 클릭한 **후 텍스트 컨텐츠** 탭에 페이지 **개인화 블록을 미러링하는** 링크가 표시되지 않는 **** 문제를 해결했습니다. (NEO 파섹)

* 만료된 미러 페이지에 대한 링크를 클릭할 때 표시되는 오류 메시지입니다. (NEO 파섹)

* 데이터 배포 **** 생성 화면에서 일부 단추를 사용할 수 없는 문제를 해결했습니다.

* 아시아/콜카타가 있는 인스턴스에서 배달 활동을 시간대로 예약할 때 발생하는 문제를 수정했습니다. (NEO 파섹)

* 이제 게시에 친화성 구성 문제가 있을 때 오류가 표시됩니다.

* 정보 메뉴에 잘못된 버전 태그 번호가 표시되는 문제를 **수정했습니다** .

* 워크플로우의 반복 게재 속성에서 라우팅 계정을 업데이트하려고 할 때 발생하는 문제를 수정했습니다. (NEO 파섹)

* 리디렉션 모듈을 통해 인스턴스에 연결할 때 발생하던 문제를 수정했습니다. 이로 인해 연결이 닫히면 제대로 정리되지 않습니다.
