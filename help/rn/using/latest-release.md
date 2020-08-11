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
source-git-commit: 251244225076dd11a319d1c4b2124c0d05168eaa
workflow-type: tm+mt
source-wordcount: '1976'
ht-degree: 3%

---


# 최신 릴리스{#latest-release}

![](assets/do-not-localize/cp-icon.png) **활성 프로파일 모니터링, 하위 도메인 전달 기능 감사 및 GPG 키 관리가 포함된 새로운 Campaign 컨트롤 패널 6월 릴리스** . [자세히 알아보기](https://docs.adobe.com/content/help/ko-KR/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/blue_2.png) 릴리스 20.2.2 - 빌드 9180 {#release-20-2-2-build-9180}

_2020년 7월 22일_

* 서명 기능이 비활성화되었을 때 추적을 수행할 수 없는 문제를 해결했습니다. (NEO-26411)
* 개인화된 도메인에서 비서명되지 않은 링크가 허용되어야 하는 문제가 해결되었습니다. (NEO-25210)
* 특정 이전 버전의 Outlook을 사용할 때 추적 URL을 열거나 클릭하지 못하는 문제를 해결했습니다. (NEO-25688)
* 페이지 URL이 이메일 배달에서 잘못 정의되던 문제를 수정했습니다. (NEO-26084)
* 피싱 방지 서비스에서 인코딩 URL 관리 문제가 해결되었습니다. (NEO-25283)
* 개인화 매개 변수의 조각을 사용하여 URL을 추적할 수 없는 문제(파운드 기호가 있는 앵커 태그)가 수정되었습니다. (NEO-25774)
* 특정 사용자 지정 추적 공식을 사용할 때의 추적 문제를 수정했습니다. (NEO-25277)&quot;알림 클릭&quot; 추적이 작동하지 않는 문제(iOS 및 Android 푸시 알림)를 수정했습니다. (NEO-25965)
* 워크플로우의 계산된 필드에 영향을 주는 회귀 문제를 수정했습니다. (NEO-25194)
* 웹 추적 URL을 신속하게 만들 수 없는 회귀 문제를 해결했습니다. (NEO-20999)
* PDF로 내보낼 때 잘렸던 기본 제공 보고서 문제를 수정했습니다. (NEO-25757)
* 배포 마법사의 충돌 문제가 해결되었습니다.
* 업그레이드 후 오퍼 알림 워크플로우가 제대로 작동하지 않는 문제를 해결했습니다.
* iOS HTTP2 커넥터가 개선되었습니다(타사 업데이트 및 오류 관리). (NEO-25904, NEO-25903)
* catalina.properties의 jarToSkip 목록이 더 이상 사용되지 않은 jar 파일에 대한 참조를 제거하도록 업데이트되었습니다(iOS 알림).
* 업그레이드 후 배달 준비를 차단하는 문제를 수정했습니다.
* 새 시퀀스 ID 메커니즘으로 전환 [](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)후 받는 사람 테이블을 업데이트하는 모든 웹 응용 프로그램이 업그레이드 후 다시 게시됩니다.
* 배달 컨텐츠의 잠재적 XSS 취약성 문제가 해결되었습니다. (NEO-17987, NEO-26073)

## ![](assets/do-not-localize/orange_2.png) 릴리스 20.2.1 - 빌드 9178 {#release-20-2-1-build-9178}

_2020년 6월 8일_

**새로운 소식**

<table> 
 <thead> 
  <tr> 
   <th> <strong>이모티콘 지원</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Campaign에서 메시지를 디자인할 때 이제 전용 단추를 사용하여 메시지 본문에 이모티콘을 쉽게 삽입할 수 있습니다. 이메일 제목 줄에도 추가할 수 있습니다. 인터페이스에서 사용 가능한 이모티콘 목록을 사용자 정의할 수 있습니다.</p>
    <p>이모티콘 추가에 대한 자세한 내용은 <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">자세한 설명서를 참조하십시오</a>. 이 섹션에서 이모티콘 목록 <a href="../../delivery/using/customizing-emoticon-list.md">을 사용자 지정하는 방법을 알아봅니다</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA 커넥터</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>이제 캠페인 인스턴스를 Azure Synapse 외부 데이터베이스에 연결할 수 있습니다. 이 연결은 새 외부 계정을 통해 관리됩니다.</p>
    <p>Azure 시냅스는 하이브리드 및 온-프레미스 환경에서만 사용할 수 있습니다. 자세한 내용은 <a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse">세부 설명서</a>를 참조하십시오.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>태국 및 브라질 개인정보 보호 법</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>태국 개인정보 보호법(PDPA)은 태국에 대한 데이터 보호 요구 사항을 통합하고 현대화한 새로운 개인 정보 보호법입니다. </p>
   <p>브라질의 레이제랄 드 프로테카앙 데 도도스(LGPD)는 8월 16일부터 브라질의 개인 데이터를 수집하거나 처리하는 모든 회사에 대해 효력을 발휘한다.</p>
   <p>이러한 규정은 해당 국가에 있는 데이터 주체의 데이터를 보유하고 있는 Adobe Campaign 고객에게 적용됩니다. Adobe는 Adobe Campaign에서 이미 사용 가능한 개인 정보 보호 기능(동의 관리, 데이터 보존 설정 및 사용자 역할 포함) 이외에도 다음과 같은 추가 기능을 추가하여 PDPA 및 LGPD에 대한 귀하의 준비를 도울 수 있습니다.</p>
   <ul> 
     <li><p>액세스 권한 및 삭제 권한: Adobe는 GDPR 및 CCPA에 추가된 기능을 활용하고 있습니다. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">자세한 내용</a></p></li> 
     <li> <p>캠페인 인터페이스 또는 API를 사용하여 개인 정보 요청을 만들 때 이제 <strong>규정</strong> 유형을 선택합니다.PDPA, LGPD, GDPR, CPA. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">자세한 내용</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

* 이메일 링크 추적에 대한 보안 기능이 모든 고객에 대해 기본적으로 활성화되어 있습니다. 고객 지원 센터에 연락하여 활성화할 수 있는 향상된 추가 보안 기능을 사용할 수 있습니다. 호스팅되지 않은 고객이 이 기능을 사용하도록 설정하는 기능 및 단계에 대한 자세한 내용은 [보안 및 개인 정보 확인 목록에서 확인할 수 있습니다](https://helpx.adobe.com/campaign/kb/acc-security.html). (NEO-24232)

* 보안을 최적화하기 위해 파일 이름을 생성하는 데 사용되는 MD5 해싱 알고리즘이 공개 파일 업로드를 위해 sha256으로 보강되었습니다. (NEO-17044)

* XSS 공격에 대한 보안을 강화하려면 미러 페이지를 실행할 때 클라이언트측 스크립트가 비활성화됩니다. (NEO-17987)

* 개인 정보 요청 정리 **기술 워크플로우가 조정 데이터를 삭제하지** 못하는 문제를 해결했습니다. (NEO-25168, NEO-21004)

* SFTP 키 기반 인증이 Debian 9에서 작동하지 않는 **파일 전송** 활동 문제를 해결했습니다. (NEO-23183)

**향상된 호환성**

이제 다음 시스템이 Campaign에서 지원됩니다.
* 운영 체제:데비안 10
* RDBMS:Oracle 18c 및 Oracle 19c
* FDA:Azure 구문 분석

자세한 내용은 [캠페인 호환성 매트릭스를 참조하십시오](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

**향상된 기능**

* 트랜잭션 메시지 기능이 개선되어 사용자 경험이 향상되었습니다. 이제 실행 인스턴스에서 삭제되는 트랜잭션 메시지 템플릿을 게시 취소할 수 있습니다. [자세히 알아보기](../../message-center/using/template-unpublication.md).

* 이미지나 첨부 파일이 포함된 이메일을 보낼 때 제한을 설정하는 새로운 옵션을 사용할 수 있습니다. 이러한 경고는 성능 문제를 방지할 수 있으며 이는 트랜잭션 메시징에서 특히 유용합니다. [자세한 내용](../../installation/using/configuring-campaign-options.md#delivery)

* 새로운 **데이터베이스** 제공 부분 준비 옵션을 사용하면 데이터베이스 내에서 직접 배달 준비를 수행할 수 있으므로 분석 시간을 크게 단축할 수 있습니다. 이 옵션은 특정 구성에만 사용할 수 있습니다. [자세히 알아보기](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* Microsoft Dynamics용 [CRM 커넥터 작업](../../workflow/using/crm-connector.md) 성능이 향상되었습니다. (NEO-13303, NEO-12710)

* 공유 메모리 버전이 증가했습니다.

   >[!WARNING]
   >
   >이 개선 사항은 업그레이드를 수행한 후 추가 단계가 필요합니다. 아래의 **기술 발전** 섹션을 참조하십시오.

* 정리 워크플로우가 향상되었습니다. 이제 삭제된 모든 워크플로우의 고아 작업 테이블도 정리 워크플로우에 의해 자동으로 삭제됩니다. [자세히 알아보기](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* 이제 푸시 알림을 전송하기 전에 iOS HTTP2 커넥터를 사용하는 iOS 모바일 응용 프로그램에 대한 인증서의 유효성을 검사하여 인증서 만료로 인해 배달이 실패하지 못하도록 합니다.

* HTTP 프록시 연결 관리가 향상되었습니다. [자세히 알아보기](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

**기타 변경 사항**

* 기존 SMS 커넥터는 이제 더 이상 사용되지 않습니다. 더 이상 사용되지 않는 [기능 페이지를 참조하십시오](../../rn/using/deprecated-features.md).

* 더 이상 자신의 리트머스 계정을 사용하여 Adobe Campaign에서 받은 편지함 렌더링을 제공하고 사용할 수 없습니다. [자세히 알아보기](../../delivery/using/inbox-rendering.md).

* 뷰를 폴더와 구분하기 위해 뷰 이름의 색상이 짙은 파란색에서 어두운 청록색으로 변경되었습니다. [자세한 내용](../../platform/using/access-management.md#about-views)

* 이제 Campaign Classic을 영국, 인도 및 캐나다 지역에서 호스팅되는 Microsoft Dynamics CRM 계정에 연결할 수 있습니다. 이는 Office 365 및 온-프레미스(Dynamics 2015) 배포 유형에 적용됩니다.

* 이제 Campaign에서 TLS 확인을 수행하여 서버의 호스트 이름이 제공된 인증서의 호스트 이름과 일치하는지 확인합니다.

* 이제 배달 및 추적 통계 표에는 배달 수신자당 하나의 항목이 아니라 SMS 채널에 대해 전달당 하나의 항목이 표시됩니다.

* 다운로드한 파일이 디스크 공간보다 클 때 사용자에게 경고하기 위해 로그 파일에 오류 메시지가 추가되었습니다.

* 이제 Snowflake 커넥터에 다음 기능을 사용할 수 있습니다.MonthiesAgoInt, ToDateTime, YearsAgo.

**기술 발전**

이 새로운 빌드는 공유 메모리를 업데이트하며 업그레이드를 수행하는 추가 단계가 필요합니다. 캠페인 관리자는 메모리 세그먼트를 제거해야 합니다. 이전 세그먼트로 인해 nlserver/nlsrvmod가 시작되지 않게 되므로 이러한 단계는 필수입니다.

Windows에서는 시스템을 다시 시작해야 합니다.

Debian/CentOs에서 공유 메모리 삭제가 필요합니다. 다음은 단계입니다.

업그레이드 전에 다음 단계를 수행해야 합니다.

1. 실행 중인 경우 apache2(CentOS의 http2) 서비스를 중지합니다.
1. 실행 중인 경우 nlserver(이전 빌드의 경우 nlserver6) 서비스를 중지합니다.

업그레이드 후:

1. 버전이 현재 버전보다 오래된 경우 **ipcrm** 명령을 사용하여 공유 메모리를 제거합니다.
1. 실행 중인 경우 nlserver 서비스를 시작합니다.
1. Apache2 서비스가 실행 중이면 서비스를 시작합니다.

다음은 Debian의 명령줄입니다.

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

Linux의 예는 이 [페이지에서 확인할 수 있습니다](../../configuration/using/additional-parameters.md#redirection-server-configuration).

**패치**

* 정리 워크플로우 로그에서 사소한 회귀 문제를 해결했습니다.
* WSDL 파일을 구문 분석할 때 **SOAP(Workflow Loading)** 작업의 문제를 수정했습니다.
* 많은 수의 워크플로우를 효율적으로 처리하기 위해 **설문 조사** 활동을 사용하여 많은 워크플로우를 업그레이드할 때 오류가 발생하는 문제를 해결했습니다.
* 향상된 MTA에서 inMail 메시지를 처리하는 동안 간헐적인 연결 문제가 해결되었습니다. (NEO-20380)
* HTML에서 이미지가 100% 폭으로 표시될 때 핫 클릭 비율이 제대로 표시되지 않는 문제를 해결했습니다. (NEO-23203)
* 게재 조건부 컨텐츠가 핫 클릭 보고서에 완전히 표시되지 않는 문제를 해결했습니다. (NEO-18729)
* 반복 배달을 보내는 워크플로우를 다시 시작할 때 타겟 승인 단계를 건너뛰던 문제를 수정했습니다. (NEO-18166)
* 워크플로우에서 오류를 수정한 후 메시지 **다시 시작 준비** 단추가 배달을 다시 시작하지 못하는 문제를 해결했습니다. (NEO-13488)
* 타겟이 일본어 이메일 포맷에 수신자를 포함하는 램프 업 단계 중 중간 소싱 모드에서 배달이 실패할 수 있는 문제를 수정했습니다. (NEO-23846)
* Snowflake 커넥터의 표준 시간대 변환 문제가 해결되었습니다(NEO-20105).
* SSL을 통해 FTP를 사용하는 외부 계정 문제를 해결했습니다. (NEO-20498)
* 라인 배달에서 이미지가 표시되지 않는 문제를 해결했습니다. (NEO-23207)
* 오퍼를 게시할 때 오류가 발생하던 문제를 수정했습니다. (NEO-23312)
* 인증서가 만료된 경우에도 모바일 애플리케이션에서 테스트 연결이 작동되도록 허용하는 푸시 알림 문제가 해결되었습니다. (NEO-22991)
* 고주파로 전송할 때 푸시 알림에 영향을 줄 수 있는 문제를 해결했습니다. (NEO-20516)
* 추적 로그가 기록하지 않았음에도 불구하고 추적 데이터에 중복 항목이 포함되는 문제를 해결했습니다. (NEO-20040)
* 추적 서버 통신 오류가 해결된 후 중복 트랜잭션 이메일이 전송되던 문제를 수정했습니다. (NEO-23640)
* 추적 URL에서 리디렉션할 때 인코딩 매개 변수 값을 삭제한 문제를 수정했습니다. (NEO-25637)
* 부동 숫자를 비교할 때 쿼리가 작동하지 않던 문제를 수정했습니다. (NEO-23243)
* 워크플로우를 다시 시작한 후 수정자 **** 열 컨텐츠가 표시되지 않는 문제를 해결했습니다. (NEO-23035)
* 두 번째 컨테이너에서 로그를 다운로드할 때 추적 기술 워크플로가 실패하는 문제를 해결했습니다. (NEO-23159)
* 데이터 연계 강화 활동을 실행할 때 워크플로가 **실패할 수 있는 문제를** 수정했습니다. (NEO-17338)
* null 또는 음수 값을 입력할 수 없도록 데이터 중복 제거 **작업 과정** 에 필드를 **유지하기 위한 확인이** Double에 추가되었습니다.
* 시간 및 시간 **이 언급되지 않도록 반복 캠페인에서 스케줄러 마법사를** 제거했습니다. 날짜만 고려한다.
* 스크립트 **워크플로우 활동의 스크립트로** 계산됨 옵션을 통해 배달을 만들 때 추가 스토리지 필드 **문제를** 수정했습니다. (NEO-20609)
* 데이터베이스 정리 작업 내에서 고스트 워크플로가 삭제되지 않는 문제를 해결했습니다.
* 청구(활성 **프로필)** 기술 워크플로가 실패하는 문제를 해결했습니다. (NEO-19777)
* acsDefaultAccount 외부 계정의 연결을 테스트할 때 발생하는 문제가 해결되었습니다. (NEO-23433)
* Hadoop 테이블이 있는 열이 여러 개인 기본 키에 스키마 확장을 만들 수 없는 문제를 수정했습니다. (NEO-17390)
* WSDL 파일이 URL에서 로드되지 않도록 **하는 로드(SOAP)** 작업의 문제를 해결했습니다. (NEO-16924)
* 여러 활성 워크플로 서버가 로드 밸런싱을 했을 때 콘솔을 **통해** 무조건적 정지를 수행하지 못하는 문제가 해결되었습니다. (NEO-19556)
* 정리 워크플로가 충돌하는 회귀 문제를 해결했습니다.
* 실행 인스턴스에 템플릿을 게시할 때 발생할 수 있는 문제를 해결했습니다.
* collectPrivacyRequests 기술 워크플로가 실행되지 않는 문제를 해결했습니다. (NEO-20513, NEO-25169)
* 9080을 빌드하여 Audience Manager에 연결하려고 할 때 발생하는 문제가 해결되었습니다. (NEO-20511, NEO-25167)
* 보고서를 PDF 또는 XLS 형식으로 내보낼 때 발생하는 문제가 해결되었습니다. (NEO-20982, NEO-23493, NEO-23348)
* 전송 후 배달 목록에 배달을 두 번 표시할 수 있는 문제를 수정했습니다.
* 중간 소싱을 통해 배달을 전송하도록 라우팅 구성을 설정할 때 발생할 수 있는 배달 준비 문제를 수정했습니다.
* 라인 메시지 내에서 웹 응용 프로그램 링크를 클릭할 때 오류 메시지가 표시되는 문제를 해결했습니다.
* Microsoft Dynamics CRM에서 모든 엔터티를 검색할 수 없는 문제를 해결했습니다. (NEO-24528)
* 정리 워크플로우를 실행한 후 **증분 쿼리** 활동 내역을 삭제한 문제를 수정했습니다.
* NmsMidSourcing_LastBroadLog_&lt;InternalName> 옵션이 누락된 중간 소싱 외부 계정을 만들 때 발생하는 문제가 해결되었습니다.
