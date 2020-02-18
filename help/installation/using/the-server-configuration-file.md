---
title: 서버 구성 파일
seo-title: 서버 구성 파일
description: 서버 구성 파일
seo-description: null
page-status-flag: never-activated
uuid: 8ef7168b-3543-4830-80b0-65a023158b3f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: da2198a3-7cef-4419-894d-e5bb51bb480c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 09fa3751d94fd71a68470174dd0b4a48d94d3f44

---


# 서버 구성 파일{#the-server-configuration-file}

Adobe Campaign의 전체 구성은 **설치 디렉토리의** conf **디렉토리에 있는 serverConf.xml** 파일에 정의됩니다. 이 섹션에는 serverConf.xml **파일의 다른 모든 노드 및 매개 변수가** 나열됩니다.

>[!NOTE]
>
>서버측 구성은 Adobe가 호스팅하는 배포를 위해서만 Adobe가 수행할 수 있습니다. 다른 배포에 대한 자세한 내용은 호스팅 모델 [섹션](../../installation/using/hosting-models.md) 또는 [이 문서를](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)참조하십시오. 호스팅 및 하이브리드 모델의 설치 및 구성 단계는 이 [섹션에](../../installation/using/hosted-model.md)설명되어 있습니다.

첫 번째 매개 변수는 **공유** 노드 내에 있습니다. 인스턴스와 관련이 있습니다. 이러한 명령은 모든 nlserver 명령(nlserver web, nlserver wfserver 등)에 사용될 수 있습니다. 다른 섹션은 특정 nlserver 하위 명령과 관련되어 있습니다.

**공유 매개 변수**

* [인증](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [exec](#exec)
* [htmlToPdf](#htmltopdf)
* [javaScript](#javascript)
* [mailExchanger](#mailexchanger)
* [모듈](#module)
* [모니터링](#monitoring)
* [oconv](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [xtkJobs](#xtkjobs)

**기타 매개 변수**

* [보관](#archiving)
* [inMail](#inmail)
* [상호 작용](#interactiond)
* [mta](#mta)
* [nmac](#nmac)
* [삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐익살](#pipelined)
* [수리](#repair)
* [securityZone](#securityzone)
* [sms](#sms)
* [stat](#stat)
* [sylogd](#syslogd)
* [추적](#tracking)
* [trackinglogs](#trackinglogd)
* [web](#web)
* [wfserver](#wfserver)

## 인증 {#authentication}

다음은 **인증** 노드의 다른 매개 변수입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> checkIPConsistent<br /> </td> 
   <td> IP 주소 확인을 활성화합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> 기본 식별 모드.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'nl'<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> 긴 세션의 제한 시간(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> 보안 토큰 제한 시간(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> 캐시 지속 시간:세션 정보를 초 단위로 캐시합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> 세션 시간 초과(초)<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

다음은 **인증 > XTK 노드의 다른 매개 변수입니다** .

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> internalPassword<br /> </td> 
   <td> 내부 계정의 암호.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> 내부 계정 보안 영역:내부 계정에 대해 허가된 영역<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

다음은 dataStore 노드의 다른 매개 **변수입니다** . 서버 데이터 소스가 정의된 곳입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportDirectory<br /> </td> 
   <td> 내보내기 디렉토리:내보낸 데이터의 대상 디렉토리 경로입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxedDirectories<br /> </td> 
   <td> 추가 샌드박스 디렉토리:샌드박스에 추가될 다른 경로(혼수상태로 분리)입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '/home/customers/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> 양식 캐시 만료 지연:캐시 항목이 무효화되는 시간(초)입니다. 즉, 캐시 항목은 게시 시에만 새로 고쳐집니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 호스트<br /> </td> 
   <td> DNS 마스크:이 인스턴스가 제공하는 DNS 마스크 목록(쉼표로 구분되어 * 및 ? 사용 가능) 패턴).<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> 상호 작용 JSSP 캐시 만료 지연:캐시 항목이 무효화되는 시간(초)입니다. 음수 값은 캐시가 항상 무효화됨을 의미합니다. '0', 비어 있거나 잘못된 값은 60으로 간주됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> 인스턴스 언어(열거형). 가능한 값은 'fr_FR'(Français), 'en_GB'(영어(영국)), 'en_US'(영어), 'de_DE'(Deutsch) 및 'ja_JP'(일본어)입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> 폴더 업로드:업로드된 데이터의 대상 디렉토리 경로입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadWhitelist<br /> </td> 
   <td> ','로 구분하여 다운로드할 권한이 있는 파일입니다. 문자열은 유효한 정규 java 표현식이어야 합니다. 업로드 <a href="../../installation/using/configuring-campaign-server.md#limiting-uploadable-files" target="_blank">가능한 파일</a>제한을 참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> 자격 증명 모음에 비밀 저장:해시 도구 모음 사용.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> 자격 증명 모음의 비밀 경로<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '/v1/secret/campaign/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> 저장소 토큰이 들어 있는 파일의 로컬 경로입니다. $(HOME)는 이 경로에서 사용할 수 있지만 다른 env 변수는 사용할 수 없습니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> 해시 프로토콜 저장소 URL <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> 뷰 캐시의 유효 기간:캐시 항목이 무효화되는 시간(초)입니다. 음수 값은 캐시가 항상 무효화됨을 의미합니다. '0', 비어 있거나 잘못된 값은 60으로 간주됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> 작업 디렉토리의 XPath.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> workingDirectory :작업 디렉토리의 XPath. 기본값:'$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

다음은 dataStore > proxyAdjust **노드의 다른 매개** 변수입니다. 정규 표현식과 일치하는 URL은 urlBase에 정의된 URL을 기반으로 다시 생성됩니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> urlBase<br /> </td> 
   <td> 외부 URL을 생성할 때 사용할 기본 URL입니다. 예:https://server.domain.com<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> URL과 일치하는 정규 표현식. 예:http://server\.lan\.net.*<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

다음은 dataStore > dataSource **노드의 다른 매개** 변수입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> 데이터 소스 이름<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> default<br /> </td> 
  </tr> 
 </tbody> 
</table>

dataStore **> dataSource > dbcnx** 노드에서 연결 설정을 구성합니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NChar<br /> </td> 
   <td> 유니코드 스토리지<br /> </td> 
   <td> 부울<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> 작업 영역<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 암호화된<br /> </td> 
   <td> 암호화된 암호<br /> </td> 
   <td> 부울<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> 계정<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 암호<br /> </td> 
   <td> 암호<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 공급자<br /> </td> 
   <td> 유형(열거형). 가능한 값은 'Oracle', 'MSSQL'(Microsoft SQL Server), 'PostgreSQL'(PostgreSQL, Greenplum), 'Teradata', 'DB2', 'MySQL', 'Netezza', 'AsterData', 'SAP HANA)입니다. RedShift'(Amazon Redshift), 'ODBC'(ODBC(Sybase ASE, Sybase IQ)), 'Relay'(원격 데이터베이스로 HTTP 릴레이).<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'Oracle'<br /> </td> 
  </tr> 
  <tr> 
   <td> server<br /> </td> 
   <td> 서버<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> timezone<br /> </td> 
   <td> 시간대:시간대 <a href="../../installation/using/time-zone-management.md" target="_blank">관리를</a>참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> 데이터베이스의 유니코드 데이터<br /> </td> 
   <td> 부울<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> 표준 시간대가 있는 날짜 필드:시간대 <a href="../../installation/using/time-zone-management.md" target="_blank">관리를</a>참조하십시오.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

dataStore **> dataSource > sqlParams** 노드에서 SQL 매개 변수를 구성합니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> funcPrefix<br /> </td> 
   <td> 함수 접두사<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

dataStore **> dataSource > 풀** 노드에서 연결된 연결 풀의 매개 변수를 구성합니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> aliveTestDelaySec<br /> </td> 
   <td> 연결 유효성 검사 간 지연.<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> 풀에 있는 무료 연결 수입니다.<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> 새 연결을 거부하기 전에 허용되는 최대 연결 수입니다. 이 <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">기술 문서를</a>참조하십시오.<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> 최대 연결 유휴 시간입니다. 0은 기본값을 의미합니다.<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

다음은 dataStore > virtualDir **노드의 다른 매개** 변수입니다. 가상 디렉토리의 구성을 실제 디렉토리 매핑으로 나타낸 것입니다.

자세한 내용은 공개 [리소스](../../installation/using/configuring-campaign-server.md#managing-public-resources)관리를 참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> 가상 디렉터리 이름 <br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> 경로<br /> </td> 
   <td> 실제 디렉토리의 전체 경로<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

다음은 기본 구성입니다.

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

다음은 dataStore > preprocessCommand **노드의 다른 매개** 변수입니다. 이는 &#39;파일 로드&#39; 워크플로우 활동의 사전 처리를 위한 인가된 명령입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> command<br /> </td> 
   <td> 명령줄 <br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> 명령줄 레이블<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> 명령줄 이름<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

다음은 기본 구성입니다.

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

다음은 DNS 구성( **DNS 구성** ) 노드의 다른 매개 변수입니다.

자세한 내용은 이 [섹션을](../../installation/using/configuring-campaign-server.md)참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> 도메인 이름:기본 도메인 이름. SMTP HELO 명령에 사용됩니다. 기본적으로 는 Windows에서 선언된 첫 번째 네트워크 인터페이스의 네트워크 매개 변수를 사용합니다.Linux(도메인 또는 검색 항목)에서 file/etc/resolv.conf를 구문 분석합니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> DNS 서버:쉼표로 구분된 도메인 이름 서버(DNS) 목록 아래 메모를 참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 재시도<br /> </td> 
   <td> DNS 쿼리에 대한 재시도 횟수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> DNS 쿼리의 시간 초과(밀리초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>이름 **서버 참고**:기본적으로
>windows에서 선언된 첫 번째 네트워크 인터페이스의 매개 변수
>not defined in UNIX. DNS(도메인 이름 서버)를 정의합니다.
>MTA가
>도메인.
>
>이 값이 정의되지 않은 경우 MTA는 호스트 네트워크 구성에서 이 정보를 검색합니다. 여러 DNS가 가능한 경우 다른 DNS 주소는 쉼표로 구분해야 합니다(예:212.155.207.1,212.155.207.2). 배달 서버에 여러 개의 네트워크 인터페이스가 있는 경우 MTA에서 사용하는 DNS 목록이 첫 번째 네트워크 인터페이스입니다. 이 경우 **nameServer** 매개 변수를 지정하여 모호성을 방지하는 것이 좋습니다.

>[!CAUTION]
>
>네트워크 호스트 구성에서 DHCP를 사용하는 경우 MTA는 DHCP에서 제공한 DNS 목록을 찾지 못합니다. 이 경우 Windows 제어판의 네트워크 매개 변수에 DNS 목록을 지정하는 것이 좋습니다.

## exec {#exec}

다음은 **exec** (명령 실행) 노드의 다른 매개 변수입니다.

자세한 내용은 인증된 외부 [명령](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)제한을 참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> blacklistFile<br /> </td> 
   <td> 블랙 리스트 명령이 포함된 파일의 경로입니다. <br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> user<br /> </td> 
   <td> 다른 사용자로 명령을 실행합니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

다음은 htmlToPdf **노드의 다른 매개** 변수입니다. 웹 페이지를 PDF 문서로 변환하는 서비스의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> command<br /> </td> 
   <td> 변환을 실행하기 위한 명령줄('기타' 모드).<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessCount<br /> </td> 
   <td> Max. 한 대의 컴퓨터에서 한 번에 허용되는 전환 프로세스 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> mode<br /> </td> 
   <td> 변환에 사용할 도구입니다. 가능한 값은 다음과 같습니다.phantomjs, wkhtmltopdf, 기타, 사용 안 함<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> 전환 시간 초과:최대 변환 시간(초)입니다. 이 임계값을 초과하면 변환 프로세스가 중지되고 오류가 발생합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> verbose<br /> </td> 
   <td> 세부 정보 표시 모드:세부 정보 모드에서 시작하여 가능한 오류를 진단합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> 프로세스를 기다리는 동안 지연:지연(초)으로, 모든 프로세스가 동시에 사용될 때와 프로세스가 종료되기를 기다릴 때. 이 지연을 초과하면 전환이 중지되고 오류가 발생합니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

phantomjs의 예:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## javaScript {#javascript}

다음은 javaScript **노드의 다른 매개** 변수입니다. JavaScript 인터프리터의 구성입니다.

자세한 내용은 보고 설명서 [및](../../reporting/using/actions-on-reports.md#memory-allocation) 이 [기술 문서를 참조하십시오](https://helpx.adobe.com/campaign/kb/out-of-memory-error-in-js-code-activity-in-workflows.html).

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxMB<br /> </td> 
   <td> 가비지 수집기를 실행하기 전에 최대 크기(MB)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> 각 스택 청크의 크기(킬로 픽셀 단위). 이것은 대부분의 사용자가 조정해서는 안 되는 메모리 관리 조정 매개 변수입니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

다음은 mailExchanger **노드의 다른 매개** 변수입니다. SMTP 서버의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> mxAddress<br /> </td> 
   <td> SMTP 서버:이메일 전송을 위한 SMTP 서버의 IP 주소입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> 이메일 전송에 사용되는 SMTP 서버의 TCP 포트입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 모듈 {#module}

다음은 **모듈** 노드의 다른 매개 변수입니다. 네임스페이스 제한 모듈 xtk에 대한 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> defaultNameSpace<br /> </td> 
   <td> 새 엔티티를 만들 때 사용되는 기본 네임스페이스입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 모니터링 {#monitoring}

다음은 **모니터링** 노드의 다른 매개 변수입니다. 모니터링 서비스 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPreparationJobsSec<br /> </td> 
   <td> 최대 준비 시간:배달 작업이 더 이상 준비되지 않는 시간(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> 모니터링 서비스에서 Unix 스크립트를 실행했습니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> 모니터링 서비스에서 실행할 Windows 스크립트입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## oconv {#ooconv}

다음은 oooconv **노드의 다른 매개** 변수입니다. 문서 변환 서버의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxConversions<br /> </td> 
   <td> OpenOffice 서버가 수행할 수 있는 최대 변환 수입니다. 이 번호 이후에 서버가 다시 시작됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> 강제로 닫기 전에 OpenOffice 서버의 최대 유휴 시간.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> OpenOffice 서버가 수신하는 포트 간격.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> 문서 변환 서버의 URL입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

다음은 proxyConfig **노드의 다른 매개** 변수입니다. 프록시 매개 변수의 구성입니다.

자세한 내용은 프록시 [연결 구성을](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabled<br /> </td> 
   <td> 프록시 서버를 사용합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> 재정의<br /> </td> 
   <td> 예외:프록시 매개 변수를 무시할 주소 목록입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> 고유한 프록시 서버:모든 유형의 프록시에 대해 동일한 구성을 사용합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP 프록시/보안 프록시 {#http-proxy---secure-proxy-}

proxyConfig **> HTTP 프록시/보안 프록시** 노드에서 다음 매개 변수를 구성합니다.

자세한 내용은 프록시 [연결 구성을](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 주소<br /> </td> 
   <td> 프록시 서버 주소<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> 프록시 서버에 대한 연결에 대한 로그인<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> 암호<br /> </td> 
   <td> 프록시 서버와의 연결에 대한 암호<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> 프록시 서버 포트<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

다음은 threadPool **노드의 다른 매개** 변수입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxThreadCount<br /> </td> 
   <td> 풀의 최대 스레드 수입니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

다음은 urlPermission **노드의 다른 매개** 변수입니다. Javascript 코드가 액세스할 수 있는 URL 목록입니다.

Javascript 코드에서 발생한 URL을 Adobe Campaign 서버에서 사용할 수 있는지 여부를 지정하는 도메인 및 정규 표현식 목록입니다.

URL을 찾을 수 없는 경우 지정된 기본 모드에 따라 기본 작업이 수행됩니다.

자세한 내용은 송신 [연결 보호를](../../installation/using/configuring-campaign-server.md#url-permissions)참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> action<br /> </td> 
   <td> URL 파섹 가능한 값은 'ignore'(경고 메시지 없이 승인, 보호를 비활성화해야 함), 'warn'(경고 메시지 승인 및 발행) 및 '거부'(URL에 대한 액세스 금지)입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 거부<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> URL 선택 메커니즘의 추적 디버깅:url 확인 프로세스 동안 추가 메시지를 발행합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### url {#url}

각 URL에 대해 다음 매개 변수를 사용하여 **url** 노드를 추가합니다.

자세한 내용은 송신 [연결 보호를](../../installation/using/configuring-campaign-server.md#url-permissions)참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dnsSuffix<br /> </td> 
   <td> 도메인 이름 또는 도메인 상위(URL에 의해 관련):확인할 URL 도메인의 전체 또는 일부를 확인하는 데 걸리는 시간을 단축할 수 있습니다. URL은 도메인에 dsnSuffix가 포함되어 있는 경우에만 정규 표현식에 대해 확인됩니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> 이 도메인에 속하는 URL의 유효성을 검사하는 정규 표현식:dnsSuffix에 해당하는 경우 URL이 확인해야 하는 정규식입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

레코드가 dnsSuffix를 **충족하지만 url** RegEx **를**&#x200B;충족시키지 않으면 다음 레코드가 검사됩니다.

예를 들어 business.com 도메인의 모든 URL에 대한 액세스를 승인하기 위해 다음 두 개의 레코드를 정의할 수 있습니다.

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.*&quot;

and

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.*&quot;

다음은 기본 구성입니다.

```
<url dnsSuffix="api.omniture.com" urlRegEx="https://api.omniture.com/genesis/i/3.1.*"   />
<url dnsSuffix="omniture.com" urlRegEx="https://api[1-5].omniture.com/genesis/i/3.1.*"  />
<url dnsSuffix="marketing.adobe.com"                     urlRegEx="https://.*"                                    />
<url dnsSuffix="fcm.googleapis.com"                      urlRegEx="https://fcm.googleapis.com/fcm/send.*"       />
<url dnsSuffix="graph.facebook.com"                      urlRegEx="https://.*"                                    />
<url dnsSuffix="api.line.me"                             urlRegEx="https://api.line.me/.*"                      />
<url dnsSuffix="api.twitter.com"                         urlRegEx="https://api.twitter.com/1.1.*"              />
<url dnsSuffix="adobeid-na1.services.adobe.com"          urlRegEx="https://.*"                                    />
<url dnsSuffix="adobeid-na1-stg1.services.adobe.com"     urlRegEx="https://.*"                                    />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/jssp/dm/renderingSeed.jssp" />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/nl/jsp/soaprouter.jsp" />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

다음은 xtkJobs **노드의 다른 매개** 변수입니다. 서버 작업의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> 서버 처리 중 메모리 상태 새로 고침 기간(ms)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 보관 {#archiving}

다음은 **보관** 노드의 다른 매개 변수입니다. 백그라운드에서 실행된 보관 작업의 구성입니다.

자세한 내용은 이메일 [보관 활성화(온-프레미스)를](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-)참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> acquireLimit<br /> </td> 
   <td> 동시에 처리할 EML 수<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> 전송된 메시지(열거)의 보관 전략 가능한 값은 '0'(보관 없음) 및 '1'(SMTP 서버로 보낸 메시지 보관 전송)입니다.<br /> </td> 
   <td> 바이트<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> 시작 매개 변수<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 자동 시작<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> 압축 아카이브 크기:압축된 보관 파일의 최대 파일 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> 보관(열거형) 중에 사용되는 압축 형식입니다. 가능한 값은 '0'(압축 없음) 및 '1'(zip 형식을 사용하여 보낸 메시지 압축)입니다.<br /> </td> 
   <td> 바이트<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> 처리되지 않은 이메일의 자동 보관 전 지연:처리되지 않은 이메일이 보관되기 전 일 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> 각 업데이트 이벤트 간의 지연(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 자동 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">프로세스 다시 시작을</a>참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> 처리되지 않은 이메일이 삭제되기 전 일 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 우선 순위 설정 우선 순위가 낮은 모듈은 처음 시작되었으며 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> 대상 보관<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> SMTPS 지원 활성화:원격 서버에서 지원하는 경우 전자 메일 배달을 안전 모드(STARTTLS/SMTPS)로 활성화합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> 보관 SMTP 서버에 대한 연결 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> 사용할 SMTP 릴레이 DNS 이름 또는 IP 주소의 쉼표로 구분된 목록 <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> SMTP 서버의 IP 포트입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

다음은 inMail **노드의 다른 매개** 변수입니다. 인바운드 이메일 관리 모듈의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 시작 매개 변수<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 자동 시작<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> 인스턴스 이름 확인:true이면 메시지 ID 헤더에 포함된 Adobe Campaign 인스턴스의 이름이 현재 인스턴스와 같아야 합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> 전달 주소:기본 이메일 전송 주소가 규칙에 의해 처리되지 않았습니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> 오류 주소:잘못된 이메일을 전송하는 데 사용되는 기본 주소(잘못된 MIME 인코딩). <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> 메시지 크기 무시:는 POP3 서버에서 반환된 메시지 크기를 무시하는 데 사용됩니다. 이 경우 모듈에 '.'가 필요합니다. 를 클릭합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> 메시지 읽기 기간:메시지 큐 폴링 빈도입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> 업데이트할 최대 로그 수:데이터베이스를 업데이트하기 전에 메모리에 유지할 최대 로그 메시지 수를 정의합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> POP3 세션 동안 읽을 최대 메시지 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> 세션 기간:메시지 처리 세션의 최대 지속 시간입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> POP3 폴링 기간<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> 읽기 메시지의 큐 크기<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> POP3 서버와의 통신 시간 초과. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 자동 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">프로세스 다시 시작을</a>참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reload 파섹<br /> </td> 
   <td> 폴링할 계정의 데이터베이스 다시 로드 빈도<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 우선 순위 설정 우선 순위가 낮은 모듈은 처음 시작되었으며 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

inMail **> msgDump** 노드에서 다음 매개 변수를 구성합니다. 처리된 메시지의 덤프 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 덤프<br /> </td> 
   <td> 모든 인바운드 메시지를 텍스트 형식으로 저장합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> 메시지 덤프 경로입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 상호 작용 {#interactiond}

다음은 interactiond **노드의 다른 매개** 변수입니다. 이것은 인바운드 상호 작용 이벤트에 대한 쓰기 데몬의 구성입니다.

자세한 내용은 상호 작용 - [데이터 버퍼를](../../installation/using/interaction---data-buffer.md)참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 시작 매개 변수<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 자동 시작<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> Max. 호출 데이터에 대한 공유 메모리에 저장된 문자 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Max. 공유 메모리에 저장된 이벤트 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> 통계용으로 저장할 제안 직후의 적합한 오퍼의 최대 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 자동 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">프로세스 다시 시작을</a>참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 우선 순위 설정 우선 순위가 낮은 모듈은 처음 시작되었으며 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> 응답 시간 통계에 대한 집계 기간(초)입니다. 0은 통계 저장소가 비활성화되었음을 의미합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Max. 개인 식별을 위해 공유 메모리에 저장된 문자 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

다음은 **mta 노드의 다른 매개** 변수입니다. 배달 에이전트의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 시작 매개 변수<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '-tracefilter:nlmta' <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 자동 시작<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> 보낸 이메일 경로 저장:비어 있지 않으면 보낸 이메일의 모든 소스 파일이 저장되는 경로입니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> 덤프 디렉터리: 비어 있지 않으면 이 디렉터리에 보낸 메일 메시지의 MIME 편지 봉투를 복사합니다. 문제 촬영에 사용됩니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> DNS 쿼리 로그 지연:시간(밀리초)을 사용하여 로그를 표시합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> 오류 통계 빈도:데이터베이스의 통계 생성과 스토리지 간 시간. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> 오류 통계를 생성하여 데이터베이스에 저장합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> 로그 메시지 표시 수준. 데이터베이스에 기록된 로그의 심각도 수준. MTA로 생성된 로그 메시지가 모두 데이터베이스에 기록되는 것은 아닙니다. 이 매개 변수를 사용하여 데이터베이스에 메시지를 작성해야 하는 수준을 정의할 수 있습니다. 수준 2를 정의하면 수준 1과 0의 메시지도 작성되지만 수준 1을 정의하면 수준 1과 0의 메시지만 기록됩니다. 가능한 값은 다음과 같습니다.0(오류), 1(경고), 2(정보)<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> mta 프로세스에서 사용할 수 있는 최대 메모리 크기(MB)입니다. 이 제한 이상으로, 사용하는 메모리가 시스템에 해제되도록 프로세스가 다시 시작됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> 고려할 연결 임계값. errorPeriodSec에 의해 지정된 기간의 총 연결 수가 임계값보다 엄격하게 낮은 경우 지정된 경로에 대해 오류 통계가 생성되지 않습니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> 고려할 오류 임계값:errorPeriodSec에 의해 지정된 기간의 총 오류 수가 임계값보다 엄격하게 낮으면 지정된 경로에 대해 오류 통계가 생성되지 않습니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> 고려할 메시지 임계값. errorPeriodSec에 의해 지정된 기간 동안 전송된 총 메시지 수가 임계값보다 엄격하게 낮은 경우 지정된 경로에 대해 오류 통계가 생성되지 않습니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 알림 릴레이:HostName:알림을 중계하는 데 사용되는 포트입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 자동 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">프로세스 다시 시작을</a>참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> 보관된 이메일이 삭제되기 전에 지연:dataLogPath에 지정된 디렉토리에 보관된 이메일이 삭제되기 전 일 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> 메시지 손실 다시 시도:하위 프로세스가 중단된 경우 배달 부분을 다시 시도합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 우선 순위 설정 우선 순위가 낮은 모듈은 처음 시작되었으며 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> &lt;dns 또는 ip&gt; [:
     &lt;port&gt; ]. 통계 <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">서버의</a>좌표를 참조하십시오. 
      <br /> 
     </td> 
   <td> 문자열<br /> </td> 
   <td> 정의되지 않은 경우 기본 포트는 7777입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSS지원<br /> </td> 
   <td> 도메인별 TLS 활성화:mx에서 구성할 수 있는 TLS를 활성화합니다(최신 통계 서버 필요).<br /> </td> 
   <td> 부울<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <tr> 
   <td> statServerVersion<br /> </td> 
   <td> 사용된 프로토콜 버전:통신 프로토콜 버전(v5.11 및 6.0.2 서버의 경우 1, v6.1 서버의 경우 2).<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 정의되지 않은 경우 최신 버전이 사용됩니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> useMomum<br /> </td> 
   <td> "true"로 설정된 경우 인스턴스가 향상된 MTA를 <a href="https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html" target="_blank">사용합니다</a>.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> 확인 모드:확인 모드(메시지의 물리적 전송 금지;시뮬레이션 및 테스트에 사용됨).<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> 작업 디렉토리:MTA에서 하위 프로세스와 통신하는 데 사용되는 임시 파일의 위치입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMail<br /> </td> 
   <td> X-메일러 필드:값이 SMTP 메일 헤더에서 'X-Meyer'입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'nlserver, 빌드 $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### 캐시 {#cache}

캐시 **** 노드에서 다음 매개 변수를 구성합니다. 로컬 파일 캐시 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPeriodSec<br /> </td> 
   <td> 재활용 날짜:기간(초 단위)을 나타냅니다. 이 기간 동안 파일은 캐시에서 자동으로 삭제되어 스토리지를 재확보할 수 있습니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> 최대 캐시 크기(Mb)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> 제거 빈도:캐시 제거 메커니즘의 실행 간격(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 릴레이 {#relay}

mta **> 릴레이** 노드에서 다음 매개 변수를 구성합니다. 메시지 배달을 위한 메일 서버의 구성입니다.

자세한 내용은 SMTP 릴레이를 [참조하십시오](../../installation/using/configuring-campaign-server.md#smtp-relay).

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 주소<br /> </td> 
   <td> 사용할 SMTP 릴레이 DNS 이름 또는 IP 주소의 쉼표로 구분된 목록 <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> SMTP 서버의 IP 포트입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 마스터 {#master}

mta **> 마스터** 노드에서 다음 매개 변수를 구성합니다. 기본 서버의 구성입니다.

자세한 내용은 이 [섹션을](../../installation/using/configuring-campaign-server.md#mta-child-processes)참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> 배달될 작업의 데이터베이스 폴링 빈도입니다. 이 값은 데이터베이스 폴링 빈도(초)를 나타냅니다. 배달을 기다리는 작업 목록을 얻기 위해 MTA는 정기적으로 데이터베이스를 폴링합니다. 대기 중인 작업이 없으면 폴링 기간이 이 값으로 정의됩니다. 그렇지 않은 경우 작업이 하위 서버로 전송되면 이 폴링 기간이 1초로 자동 줄어들어 새 작업을 가능한 한 빨리(예: 하위 서버를 다시 사용할 수 있게 되는 즉시) 다시 처리할 수 있습니다. 이것은 자식 서버를 다시 사용할 수 있을 때까지 데이터베이스 쿼리가 초당 수행된다는 의미는 아닙니다. 실제로 데이터베이스 액세스는 하나 이상의 하위 서버를 사용할 수 있는 경우에만 수행됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> 데이터베이스 연결 실패 후 대기 기간입니다. 데이터베이스 연결 오류는 일반적으로 데이터베이스 서버 자체에 의해 발생합니다. 예를 들어 유지 관리 목적으로 서버를 중지할 수도 있습니다. DataBaseRetryDelay 매개 변수는 데이터베이스 연결 실패 시 두 연결 시도 사이의 지속 시간을 정의합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> 개인 키 캐시에 대한 유효성 기간(DomainKeys). DomainKeys 권장 사항(http://antispam.yahoo.com/domainkeys)에 따라 전자 메일에 서명하는 데 사용되는 개인 키는 데이터베이스에 옵션으로 저장됩니다. domainKeysReloadPeriodSec 매개 변수는 MTA가 이러한 키를 캐시에 저장할 수 있는 시간(초)을 정의합니다. 이 지연 후에 모든 키를 데이터베이스에서 다시 로드해야 합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> 최대 하위 서버 수입니다. 실행 중인 최대 서버 수를 나타냅니다. 서버 메모리 리소스와 최적 호환되도록 이 수를 제한하는 것이 좋습니다. 배달 중에 확인할 수 있습니다. 사용된 메모리는 사용 가능한 실제 메모리의 1/3을 초과하지 않아야 하며 그렇지 않으면 스왑 기능이 사용됩니다. MTA <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">하위 프로세스를</a>참조하십시오.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> 최소 하위 서버 수입니다. MTA는 최소 이 수의 서버를 실행하려고 합니다. 값이 작으면 이 값에 도달할 때까지 매 초마다 새 서버를 다시 시작합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> 시작할 때의 하위 서버 수입니다. 하위 서버 수는 동적으로 모니터링됩니다.mta가 시작되면 이 값으로 지정된 수만큼 하위 서버를 만듭니다. 일반적으로 호스트 리소스를 저장하기 위해 하위 서버를 초당 두 서버보다 빠르게 시작할 수 없습니다. 그러나 MTA가 시작되면 이 제한이 무시되므로 하위 서버를 가능한 한 빨리 사용할 수 있습니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 아이 {#child}

mta **> child** 노드에서 다음 매개 변수를 구성합니다. 하위 서버의 구성입니다.

자세한 내용은 이메일 [보내기 최적화를](../../installation/using/email-deliverability.md#email-sending-optimization)참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> extraArgs<br /> </td> 
   <td> 선택적 명령줄 인수 <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> 유휴 하위 서버가 중지될 때까지 시간 초과입니다. 하위 서버에 이 매개 변수보다 더 긴 유휴 시간이 있으면 호스트 리소스를 확보하기 위해 자동으로 종료됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> 최대 메시지 보존 시간입니다. 전송률 조절로 인해 준비된 메시지를 보낼 수 없거나 대상 MTA에 연결할 수 없는 경우 메시지가 중단되며 다음 다시 시도에서 처리됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> 각 하위 서버에서 시작한 FCM에 대한 최대 병렬 Http 요청 수<br /> </td> 
   <td> Long<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> 자식 서버당 최대 메시지 수입니다. 각 MTA 하위 항목은 이 메시지 수를 처리하여 종료됩니다. MTA에서 메모리 또는 리소스 유출은 해가 되지 않도록(일반적으로 수 천 명) 숫자를 지정해야 합니다. MTA 코드에서 알려진 메모리 누수가 없는 경우에도 포함된 JavaScript 및 XSL 엔진은 완전히 신뢰할 수 없습니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> 보류 중인 메시지:배달될 메모리에서 대기 중인 최대 메시지 수입니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> 하위 프로세스에서 사용할 수 있는 최대 메모리 크기(MB)입니다. 이 제한 이상으로, 사용하는 메모리가 시스템에 해제되도록 프로세스가 중지됩니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> 배달 커넥터에 대한 SOAP 연결이 중단된 시간(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> 항상 우선 순위가 가장 높은 MX로 시작합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> 다시 시작될 때 연속된 최대 시도 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

mta > **child > smtp** 노드에서 다음 매개변수를 구성합니다. SMTP 세션의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enableTLS<br /> </td> 
   <td> 원격 서버에서 지원되는 경우 안전 모드(STARTTLS/SMTPS)로 이메일 배달을 활성화합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> 유휴 세션 시간 초과. 이 매개 변수는 세션이 지정된 도메인에 여러 메시지를 전송하는 데 재사용되는 경우에만 사용됩니다. MTA가 메시지 전송을 완료한 경우 SMTP 세션이 체계적으로 닫히지 않습니다. 동일한 도메인에 대해 메시지를 보낼 준비가 되면 동일한 SMTP 세션을 다시 사용할 수 있으므로 세션이 자동으로 닫히지 않습니다. 매개 변수 IdleSessionTimeout 매개 변수를 사용하면 SMTP 세션이 다른 메시지를 대기하는 동안 활성 상태로 유지되는 시간을 정의할 수 있습니다. 기간이 경과하면 세션이 자동으로 닫힙니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> 연결을 다시 시도하기 전에 초기 지연. 연결이 실패할 때마다 지연이 두 배로 증가합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> 하위 서버별 SMTP 세션의 최대 수입니다. 메시지를 전달하기 위해 MTA는 받는 사람 MTA와 SMTP 연결을 초기화합니다. 주어진 하위 서버에 대한 동시 및 활성 SMTP 세션의 최대 수는 이 값으로 제한됩니다. 이 값을 maxSpareServers에 곱하면 지정된 자식 서버에서 동시에 처리할 수 있는 최대 메시지 수를 얻게 됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

mta > **child > smtp > IPAfatness** 노드에서 다음 매개 변수를 구성합니다. 최적화된 나가는 SMTP 트래픽을 위해 IP 주소가 있는 친화성 관리의 구성입니다.

자세한 내용은 친화성이 [있는 아웃바운드 SMTP 트래픽을 사용하고](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) 관리할 [IP 주소 목록을 참조하십시오](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> 도메인 이름:IP 주소에 연결된 로컬 도메인 이름입니다. SMTP HELO 명령을 실행할 때 사용됩니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> 논리 이름:사용자의 관련성에 연결된 이름. 이름은 세미콜론을 사용하여 구분됩니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

mta > **child > smtp > IP** 노드에서 다음 매개 변수를 구성합니다.

자세한 내용은 [사용할](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)IP 주소 목록을 참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 주소<br /> </td> 
   <td> 연결된 실제 주소입니다. 예:'192.168.0.1'<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> 연결된 공개 주소 ID. 통계 서버의 키로 사용됩니다. 숫자여야 합니다. 이 <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">섹션을</a>참조하십시오.<br /> </td> 
   <td> Long<br /> </td> 
  </tr> 
  <tr> 
   <td> 중량<br /> </td> 
   <td> 다른 IP를 기준으로 이 IP의 사용 빈도를 지정합니다(가중치가 클수록 주파수가 높음).<br /> </td> 
   <td> Long<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> 포함할 도메인 마스크의 쉼표로 구분된 목록입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> 제외할 도메인 마스크의 쉼표로 구분된 목록입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> IP 주소에 연결된 컴퓨터 이름입니다. SMTP HELO 명령을 실행할 때 사용됩니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

다음은 nmac 노드의 다른 매개 **변수입니다** . 푸시 알림 전달에 대한 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> useHTTPProxy<br /> </td> 
   <td> 공유/proxyHTTP에 정의된 HTTP 프록시를 사용합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 릴레이 {#relay-1}

다음은 **nmac > 릴레이** 노드의 다른 매개 변수입니다. 이렇게 하면 메시지 전달에 대한 릴레이 사용이 구성됩니다(ios http2 커넥터).

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 주소<br /> </td> 
   <td> 사용할 릴레이의 DNS 주소 또는 이름입니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> 릴레이 포트<br /> </td> 
   <td> Long<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> 인증서 체인(PEM 파일). 모의 서버를 사용할 때 유용합니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐삐익살 {#pipelined}

다음은 **파이프라인** 노드의 다른 매개 변수입니다. 이것은 파이프라인 서비스에 대한 이벤트 처리 모듈의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> appName<br /> </td> 
   <td> 공개 키를 저장할 때 개발자 연결에서 생성된 응용 프로그램의 이름입니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> 시작 매개 변수<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> 게이트웨이 토큰을 얻는 URL.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> 개인 키를 사용하여 토큰을 가져옵니다(XtkKey 옵션을 사용하여 AES에서 암호화).<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 자동 시작 <br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> 인증 비활성화:인증 없이 파이프라인 서비스에 연결 <br /> </td> 
   <td> 부울<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> 파이프라인 서비스 URL을 검색하는 URL입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> 상태 저장 기간:프로세스의 내부 정보가 파일에 저장되는 빈도 0인 경우 비활성화됩니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> 의견 수렴 URL:파이프라인 서비스의 의견 수렴 URL을 강제 적용합니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> 상태 서버 포트:프로세스의 상태를 쿼리할 수 있는 HTTP 서버 포트입니다. 0인 경우 비활성화됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> 포인터 FlushMessageCount<br /> </td> 
   <td> 이 수의 메시지가 처리될 때마다 포인터가 데이터베이스에 저장됩니다.<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> 포인터 FlushPeriodSec<br /> </td> 
   <td> 포인터가 저장되기 전의 지연:이 기간 동안 최소한 한 번 데이터베이스에 포인터가 저장됩니다(활동이 적은 경우 유용함).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 자동 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">프로세스 다시 시작을</a>참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> 개인화된 JavaScript 커넥터를 사용한 이벤트 처리를 위한 스레드 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> 이벤트 처리를 위한 스레드 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> 오류가 있는 경우 처리 사이의 지연.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> 이 기간 이후 포기:이 기간 후에도 처리가 계속 실패하는 경우 이벤트를 종료합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 우선 순위 설정 우선 순위가 낮은 모듈은 처음 시작되었으며 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 수리 {#repair}

다음은 **복구** 노드의 다른 매개 변수입니다. 데이터베이스 복구 모듈의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> repairActionDelayMin<br /> </td> 
   <td> 배달 작업 복구 모듈:복구 모듈에서 배달 작업을 처리할 수 있는 지연(분). <br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

다음은 securityZone 노드의 다른 매개 **변수입니다** .

자세한 내용은 보안 영역 [정의를 참조하십시오](../../installation/using/configuring-campaign-server.md#defining-security-zones).

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> allowDebug<br /> </td> 
   <td> 웹 응용 프로그램에 대한 디버그 모드 인증<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> 사용자가 암호 없이 응용 프로그램을 사용하도록 승인합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> 연산자 로그온에 대한 HTTP 사용을 승인합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjection<br /> </td> 
   <td> 표현식에서 SQLDATA의 사용을 승인합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> 사용자/암호 세션 토큰을 인증합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> 레이블<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> 내부 이름<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> 보안 토큰을 사용하지 마십시오.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> 오류 정보 표시<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

다음은 기본 구성입니다.

```
<securityZone allowDebug="false" allowHTTP="false" allowSQLInjection="false" label="Public Network" name="public">
  <subNetwork name="all" label="All addresses" mask="*" proxy="127.0.0.1, ::1"/>

  <securityZone allowDebug="true" allowHTTP="false" allowSQLInjection="false" label="Private Network (VPN)"
                name="vpn" showErrors="true">

    <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" allowUserPassword="false"
                  allowSQLInjection="false" label="Private Network (LAN)" name="lan" sessionTokenOnly="true"
                  showErrors="true">
      <subNetwork name="lan1" label="Lan 1" mask="192.168.0.0/16" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan2" label="Lan 2" mask="172.16.0.0/12" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan3" label="Lan 3" mask="10.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost" label="Localhost" mask="127.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6"  label="Lan (IPv6)" mask="fc00::/7" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6b" label="Lan (IPv6)" mask="fe80::/10" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost6" label="Localhost (IPv6)" mask="::1/128" proxy="127.0.0.1, ::1"/>
    </securityZone>

  </securityZone>
</securityZone>
```

### subNetwork {#subnetwork}

다음은 securityZone > subNetwork **노드의 다른 매개** 변수입니다.

자세한 내용은 보안 영역 [정의를 참조하십시오](../../installation/using/configuring-campaign-server.md#defining-security-zones).

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> label<br /> </td> 
   <td> 레이블<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> 마스크<br /> </td> 
   <td> 마스크 또는 주소<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> 내부 이름<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> 프록시<br /> </td> 
   <td> 이 하위 네트워크가 인스턴스에 액세스하기 위해 사용하는 프록시의 마스크 또는 주소(역) 이 경우 'X-Forwarded-For' 헤더는 이 프록시 대신 테스트됩니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

다음은 **sms** 노드의 다른 매개 변수입니다. 인바운드 SMS 관리 모듈의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 시작 매개 변수<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 자동 시작<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> SMPP 커넥터에서 보관 중인 파일 작업 최대 일 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> SMPP 작업 파일의 최대 크기(MB)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> 세션 연속성 프레임의 반복:max. 수신 세션이 계속 활성화되었음을 알리는 두 프레임 사이의 기간(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> 검색 빈도:SMS 계정 투표 기간.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 자동 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">프로세스 다시 시작을</a>참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> 계정 다시 로드 빈도:폴링할 계정의 데이터베이스 다시 로드 빈도<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 우선 순위 설정 우선 순위가 낮은 모듈은 처음 시작되었으며 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> SR 처리 지연 시간(초):현재 시간보다 이전 복구 날짜를 가진 SR에서만 srReadDelay가 지정한 시간(초)을 뺀 것입니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> SMS 게이트웨이의 통신 시간 초과.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

다음은 **sms > netsize** 노드의 다른 매개 변수입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> netsizeConnectionTimeout<br /> </td> 
   <td> Netsize와 연결 설정 시 시간 초과(초)<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

다음은 **stat** 노드의 다른 매개 변수입니다. MTA 통계 모듈의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 시작 매개 변수<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 자동 시작<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> 서버 수신 포트입니다. 이 <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">섹션을</a>참조하십시오.<br /> </td> 
   <td> Short<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 자동 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">프로세스 다시 시작을</a>참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 우선 순위 설정 우선 순위가 낮은 모듈은 처음 시작되었으며 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## sylogd {#syslogd}

다음은 syslogd **노드의 다른 매개** 변수입니다. 로그 관리 모듈의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 시작 매개 변수<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 자동 시작<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> 로그 파일의 최대 크기(MB)입니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> 유지할 최대 logins.log 파일 수입니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 자동 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">프로세스 다시 시작을</a>참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 우선 순위 설정 우선 순위가 낮은 모듈은 처음 시작되었으며 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 추적 {#tracking}

다음은 **추적** 노드의 다른 매개 변수입니다. 이것은 추적 서버의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 시작 매개 변수<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 자동 시작<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> consolidationPeriodSec<br /> </td> 
   <td> 통합 기간<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> 중복 제거:열려 있는 추적 로그를 제거하여 Outlook과 같은 메일 독자의 메일 미리 보기 효과를 제한할 수 있습니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> 최대 X% 오류 무시:아직 계산되지 않은 분개의 비율이 이 값에 도달하지 않는 한 추적 표시기를 업데이트하지 마십시오. <br /> </td> 
   <td> 바이트<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> 업데이트 오류 표시기:오류 표시기를 다시 계산하기 전의 최대 지속 시간입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> 표시기 지속 시간<br /> </td> 
   <td> 다음 기간 동안 지표 계산:통합 표시기가 더 이상 계산되지 않는 배달 유효 일자 이후의 기간.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> 원격 추적 서버 호출에서 요청한 로그 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 자동 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">프로세스 다시 시작을</a>참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 우선 순위 설정 우선 순위가 낮은 모듈은 처음 시작되었으며 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> 최대 X% 추적 무시:아직 계산되지 않은 분개의 비율이 이 값에 도달하지 않는 한 추적 표시기를 업데이트하지 마십시오.<br /> </td> 
   <td> 바이트<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> 업데이트 추적 표시기:추적 표시기가 다시 계산되기 전의 최대 지속 시간입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> 브라우저 식별자 캐시의 크기입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogs {#trackinglogd}

다음은 trackinglogd **노드의 다른 매개 변수입니다** . 추적 로그 쓰기 데몬의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 시작 매개 변수<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 자동 시작<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> 최대 쓰기 재시도 횟수:로그 파일에 쓸 수 없는 경우에 만들 수 있는 최대 파일 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> 최대 로그 크기:디스크의 로그에 사용되는 최대 공간(MB)입니다. 100MB 이하여야 합니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> 최대 로그 수:공유 메모리에 저장되는 최대 로그 수입니다. 10000보다 작을 수 없습니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 자동 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">프로세스 다시 시작을</a>참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> 제거 전 로그 수:로그 파일 제거를 시작하기 전에 삽입된 로그 수입니다. 50000 이하일 수 없습니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 우선 순위 설정 우선 순위가 낮은 모듈은 처음 시작되었으며 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> 추가 웹 추적 매개 변수를 위해 공유 메모리에 저장된 최대 문자 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## web {#web}

다음은 **웹** 노드의 다른 매개 변수입니다. 웹 모듈의 구성입니다.

자세한 내용은 이 [섹션을](../../installation/using/configuring-campaign-server.md#default-port-for-tomcat)참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> JVMOptions<br /> </td> 
   <td> 문자열로 전달된 JVM의 옵션.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> MaxThreads<br /> </td> 
   <td> 최대 스레드 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> 최소 스레드 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> 시작 매개 변수<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 자동 시작<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Tomcat 청취 제어 포트:tomcat <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">구성을 참조하십시오</a>.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP 수신 대기 포트:tomcat <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">구성을 참조하십시오</a>.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> SubmitDelivery 호출에 대한 큐의 크기:큐에 올릴 수 있는 SubmitDelivery SOAP 호출의 최대 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb) 수에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 알림 릴레이:HostName:포트 알림의 릴레이를 활성화합니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 자동 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">프로세스 다시 시작을</a>참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 우선 순위 설정 우선 순위가 낮은 모듈은 처음 시작되었으며 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> 모듈 모드에서 SOAP 라우터를 시작합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

다음은 **웹 > jsp** 노드의 다른 매개 변수입니다. JSP에서 사용하는 매개 변수의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 디버그<br /> </td> 
   <td> 디버그 모드에서 JSP의 실행.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> 다운로드 폴더:클라이언트 콘솔용 설치 프로그램의 다운로드 경로.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp'<br /> </td> 
  </tr> 
  <tr> 
   <td> foFileName<br /> </td> 
   <td> .fo 파일의 경로입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soapRouter<br /> </td> 
   <td> SOAP 라우터의 URL(http://myserver/xxx, http://jni 또는 mailto:xxx).<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

웹 **> jsp > 클래스 경로** 노드에는 JVM을 시작할 때 사용할 모든 클래스 경로 목록이 포함되어 있습니다. 다음은 기본 구성입니다.

```
'$(XTK_INSTALL_DIR)/tomcat-7/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-7/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/el-api.jar
          $(XTK_INSTALL_DIR)/java/lib/log4j-1.2.11.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat7-websocket.jar
          $(XTK_INSTALL_DIR)/java/lib/pdfbox-2.0.4.jar
          $(XTK_INSTALL_DIR)/java/lib/FontBox-0.1.0.jar
          $(XTK_INSTALL_DIR)/java/lib/AGJavaEndpoint.22.jar
          $(XTK_INSTALL_DIR)/java/lib/NSGConstants.jar
          $(XTK_INSTALL_DIR)/java/lib/smpp.jar
          $(XTK_INSTALL_DIR)/java/lib/nlweb.jar
          $(XTK_INSTALL_DIR)/java/lib/jcaptcha-all.jar
          $(XTK_INSTALL_DIR)/java/lib/apns-1.0.0.Beta6-jar-with-dependencies.jar
          $(XTK_INSTALL_DIR)/java/lib/commons-collections-3.2.2.jar
          $(XTK_INSTALL_DIR)/java/lib/jcommon-1.0.16.jar
          $(XTK_INSTALL_DIR)/java/lib/jfreechart-1.0.13.jar
          $(XTK_INSTALL_DIR)/java/lib/barcode4j-light.jar
          $(XTK_INSTALL_DIR)/java/lib/zxing.jar
          $(XTK_INSTALL_DIR)/java/lib/raztec.jar
          $(XTK_INSTALL_DIR)/java/lib/gson-2.7.jar
          $(XTK_INSTALL_DIR)/java/lib/alpn-api-1.1.3.v20160715.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-all-4.1.6.Final.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-tcnative-boringssl-static-1.1.33.Fork22.jar
          $(XTK_INSTALL_DIR)/java/lib/pushy-0.8.1.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-api-1.7.21.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-simple-1.7.21.jar'
```

### jssp {#jssp}

다음은 **web > jssp 노드의 다른 매개** 변수입니다. JSSP에서 사용하는 매개 변수의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> collectsGarbageAfterRequest<br /> </td> 
   <td> 각 쿼리 다음에 JavaScript 컨텍스트의 가비지 수집기를 활성화합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> JavaScript 컨텍스트에서 제공되는 최대 페이지 수입니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

웹 **> jsp > 클래스 경로** 노드에는 JVM을 시작할 때 사용할 모든 클래스 경로 목록이 포함되어 있습니다.

### 릴레이 {#relay-2}

다음은 **웹 > 릴레이** 노드의 다른 매개 변수입니다. 두 영역 간의 HTTP 요청에 대한 릴레이 구성입니다.

자세한 내용은 이 [섹션을](../../installation/using/deploying-an-instance.md#synchronizing-public-resources)참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debugRelay<br /> </td> 
   <td> 디버그 모드에서 웹 서버 내에서 HTTP 릴레이 모듈을 시작합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> protectedCharsInAuthority<br /> </td> 
   <td> 금지된 문자(도메인):uri의 'authority' 섹션에 있는 금지된 문자 목록.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> 금지 문자 InPath<br /> </td> 
   <td> 금지된 문자(경로):uri의 'path' 섹션에 있는 금지된 문자 목록.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> 'mod_dir' 모듈 옵션의 값:폴더에서 쿼리 중에 사용할 파일 목록입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> HTTP 릴레이 모듈을 시작합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> 웹 서버 내에서 HTTP 릴레이 모듈을 시작합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> 금지된 URL을 삭제하기 전에 대기 시간입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

다음 매개 변수를 사용하여 각 URL에 대한 **웹 > 릴레이 > url** 노드를 릴레이(삽입 순서는 우선 순위를 정의함)합니다.

자세한 내용은 동적 페이지 [보안 및 릴리스](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) 및 [섹션을](../../installation/using/deploying-an-instance.md#synchronizing-public-resources)참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IPMask<br /> </td> 
   <td> 공인 IP:이 마스크에 릴레이를 사용할 수 있는 소스 IP 주소의 쉼표로 구분된 목록<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 거부<br /> </td> 
   <td> 이러한 URL에 대한 액세스 거부(HTTP 403 오류 반환)<br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> 릴레이 DNS 별칭:릴레이 DNS 별칭 마스크의 쉼표로 구분된 목록(예:'*.adobe.com').<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> 보안 영역(예: webApps)에 상관없이 HTTP 액세스가 인증되었습니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayHost<br /> </td> 
   <td> 원본 호스트 추가:다시 연결할 때 원본 요청의 HTTP '호스트' 헤더를 사용합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> 초기 URL 경로 추가:대상 페이지의 URL에 릴레이할 URL의 전체 경로를 추가합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> status<br /> </td> 
   <td> 공용 리소스의 동기화 상태(열거형). 가능한 값은 'normal'(일반 실행), 'blacklist'(오류 404의 경우 url 블랙) 및 'spare'(있는 경우 예비 서버에 파일 업로드)입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> normal<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> 대상 페이지의 URL:tomcat <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">구성을 참조하십시오</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> 중계되는 요청의 최대 실행 시간(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> 릴레이할 URL의 마스크(예:'/nl*', '*.jsp').<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

다음은 기본 구성입니다.

```
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true"
     status="normal" targetUrl="http://localhost:7781" timeout="" urlPath="/pipelined/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/view/*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="*ooconv.jsp*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/res/*.jsp*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/sc.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/interactionProposal.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/zoneJson.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/barcode.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/captcha.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/webForm.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/xtk/jsp/zoneinfo.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/facebookCallback.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/m.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/s.jsp"/>

<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nms/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/xtk/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nl/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="*.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="true" urlPath="/webApp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/report/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/jssp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/strings/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/interaction/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/barcode/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/lineImage/*"/>

<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/favicon.*"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.md"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.png"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.jpg"/>
```

각 HTTP 헤더에 대해 **웹 > 릴레이 >** responseHeader 노드를 추가하여 릴레이에 전달된 답글에 추가합니다.

자세한 내용은 HTTP 헤더 [관리를 참조하십시오](../../installation/using/configuring-campaign-server.md#managing-http-headers).

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> 헤더 이름<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> value<br /> </td> 
   <td> 헤더 값 <br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

다음은 기본 구성입니다.

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### 리디렉션 {#redirection}

다음은 **웹 > 리디렉션** 노드의 다른 매개 변수입니다. 리디렉션 모듈의 구성입니다.

자세한 내용은 이 [섹션을](../../installation/using/deploying-an-instance.md#synchronizing-public-resources)참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IMSOrgId<br /> </td> 
   <td> IMS 조직 식별자:Adobe Marketing Cloud 내의 고유 조직 ID로, 특히 VisitorID 서비스 및 IMS SSO에 사용됩니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> 영구 쿠키에 사용된 정책을 설명하는 값(P3P 압축 정책 형식 준수). <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'CO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV'<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> 쿠키를 설정할 도메인을 명시적으로 표시하도록 구성할 도메인의 쉼표로 구분된 목록. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> 추적 인스턴스와 연결된 데이터베이스 식별자입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> 호출별 로그 수:getTrackingLogs 메서드 호출 시 기본적으로 반환되는 로그 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> 만료된 방향 페이지:배달 작업의 리디렉션이 만료되었을 때 리디렉션 서버에서 기본적으로 사용하는 웹 페이지의 URL입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> 최대 작업 수:캐시의 최대 배달 작업 수입니다. 50보다 작을 수 없습니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> 리디렉션 서비스를 시작합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> 모듈 모드에서 리디렉션 서비스를 시작합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> 웹 추적:알 수 없는 사용자가 방문한 페이지에 대한 로그 작성. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> 리디렉션 서버에서 사용하는 암호입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

다음은 **웹 > 리디렉션 > spareServer 노드의 다른 매개** 변수입니다.

자세한 내용은 중복 [추적을](../../installation/using/configuring-campaign-server.md#redundant-tracking)참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabledIf<br /> </td> 
   <td> 다음의 경우 고려됨표현식이 true를 반환하면 추적 서버가 고려됩니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> id<br /> </td> 
   <td> 이름<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> 추가 리디렉션 서버 URL<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

다음은 **web > spamCheck 노드의 다른 매개** 변수입니다. 스팸 방지 점수 평가 매개 변수의 구성입니다.

자세한 내용은 Configuring SpamAsser [를 참조하십시오](../../installation/using/configuring-spamassassin.md).

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> command<br /> </td> 
   <td> 이메일(예:perl spamcheck.pl').<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

다음은 wfserver 노드의 다른 매개 **변수입니다** . 워크플로우 프로세스 구성입니다.

자세한 내용은 고가용성 워크플로우 [및 친화성을 참조하십시오](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

<table> 
 <thead> 
  <tr> 
   <th> 매개 변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 친화성<br /> </td> 
   <td> 친화성<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> 시작 매개 변수<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 자동 시작<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> 기간<br /> </td> 
   <td> Long<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고:지정된 프로세스에 의해 사용된 RAM(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 알림 릴레이:HostName:포트 알림의 릴레이를 활성화합니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 자동 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">프로세스 다시 시작을</a>참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 우선 순위 설정 우선 순위가 낮은 모듈은 처음 시작되었으며 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

