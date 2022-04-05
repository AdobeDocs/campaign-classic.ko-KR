---
product: campaign
title: 서버 구성 파일
description: 서버 구성 파일
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '7961'
ht-degree: 5%

---

# 서버 구성 파일{#the-server-configuration-file}

![](../../assets/v7-only.svg)

Adobe Campaign의 전체 구성은 **serverConf.xml** 파일, 다음 위치에 있음 **conf** 설치 디렉토리의 디렉토리입니다. 이 섹션에는 **serverConf.xml** 파일.

>[!NOTE]
>
>서버측 구성은 Adobe에 의해 호스팅되는 배포에 대해서만 Adobe이 수행할 수 있습니다. 다양한 배포에 대한 자세한 내용은 [호스팅 모델](../../installation/using/hosting-models.md) 또는 [이 페이지](../../installation/using/capability-matrix.md). 호스팅 및 하이브리드 모델의 설치 및 구성 단계는 다음과 같습니다 [섹션](../../installation/using/hosting-models.md).

첫 번째 매개 변수는 **공유** 노드 아래에 있어야 합니다. 인스턴스와 관련이 있습니다. 이는 모든 nlserver 명령(nlserver web, nlserver wfserver 등)에서 사용할 수 있습니다. 다른 섹션은 특정 nlserver 하위 명령과 관련되어 있습니다.

**공유 매개 변수**

* [인증](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [exec](#exec)
* [htmlToPdf](#htmltopdf)
* [ims](#ims)
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
* [파이프라인](#pipelined)
* [복구](#repair)
* [securityZone](#securityzone)
* [sms](#sms)
* [stat](#stat)
* [sylogd](#syslogd)
* [추적](#tracking)
* [trackinglogd](#trackinglogd)
* [웹](#web)
* [wfserver](#wfserver)

## 인증 {#authentication}

다음은 의 다양한 매개 변수입니다 **인증** 노드:

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
   <td> IP 주소 확인을 사용하도록 설정합니다.<br /> </td> 
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
   <td> 긴 세션의 시간 제한(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> 보안 토큰 시간 제한(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> 캐시 기간: 세션 정보의 캐시(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600년<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> 세션 시간 초과(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

다음은 의 다양한 매개 변수입니다 **인증 > XTK** 노드:

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
   <td> 내부 계정 보안 영역: 내부 계정에 대해 인증된 영역입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

다음은 의 다양한 매개 변수입니다 **dataStore** 노드 아래에 있어야 합니다. 여기에서 서버 데이터 소스가 정의됩니다.

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
   <td> 디렉토리 내보내기: 내보낸 데이터의 대상 디렉토리 경로입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxedDirectories<br /> </td> 
   <td> 추가 샌드박스 디렉토리: 샌드박스에 추가할 다른 경로(쉼표로 구분됨).<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '/home/customers/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> 양식 캐시 만료 지연: 캐시 항목이 무효화된 후 시간 초과(초)입니다. 즉, 캐시 항목은 게시 시에만 새로 고침됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600년<br /> </td> 
  </tr> 
  <tr> 
   <td> 호스트<br /> </td> 
   <td> DNS 마스크: 이 인스턴스가 제공하는 DNS 마스크 목록(쉼표로 구분됨, * 및 ? 패턴).<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> 상호 작용 JSSP 캐시 만료 지연: 캐시 항목이 무효화된 후 시간 초과(초)입니다. 음수 값은 캐시가 항상 무효화됨을 의미합니다. '0', 비어 있거나 잘못된 값은 60으로 간주됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300년<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> 인스턴스 언어(열거형). 가능한 값은 'fr_FR'(Français), 'en_GB'(영어(영국)), 'en_US'(영어), 'de_DE'(Deutsch) 및 'ja_JP'(일본어)입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> 업로드 폴더: 업로드된 데이터에 대한 대상 디렉토리의 경로입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> ','로 다운로드할 권한이 있는 파일입니다. 문자열은 유효한 정규 Java 표현식이어야 합니다. 자세한 내용은 <a href="file-res-management.md" target="_blank">업로드 가능한 파일 제한</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> 저장소에 암호 저장: 해시 모음 사용.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> 저장소의 암호 경로<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '/v1/secret/campaign/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> 저장소 토큰이 포함된 파일의 로컬 경로입니다. $(HOME)는 이 경로에서 사용할 수 있지만 다른 env 변수는 사용할 수 없습니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> Hashicorp 자격 증명 모음 URL <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> 뷰 캐시의 유효 기간: 캐시 항목이 무효화된 후 시간 초과(초)입니다. 음수 값은 캐시가 항상 무효화됨을 의미합니다. '0', 비어 있거나 잘못된 값은 60으로 간주됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600년<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> 작업 디렉터리의 XPath입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> workingDirectory : 작업 디렉터리의 XPath입니다. 기본값: '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

다음은 의 다양한 매개 변수입니다 **dataStore > proxyAdjust** 노드 아래에 있어야 합니다. 정규 표현식과 일치하는 URL은 urlBase에 정의된 URL을 기반으로 다시 생성됩니다.

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
   <td> 외부 URL을 생성할 때 사용할 기본 URL입니다. 예: https://server.domain.com<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> URL과 일치하는 정규 표현식입니다. 예: http://server\.lan\.net.*<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

다음은 의 다양한 매개 변수입니다 **dataStore > dataSource** 노드 아래에 있어야 합니다.

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
   <td> 이름<br /> </td> 
   <td> 데이터 소스 이름<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 기본<br /> </td> 
  </tr> 
 </tbody> 
</table>

에서 **dataStore > dataSource > dbcnx** 노드, 연결 설정을 구성합니다.

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
   <td> 엔씨하<br /> </td> 
   <td> 유니코드 저장소<br /> </td> 
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
   <td> 로그인<br /> </td> 
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
   <td> 유형(열거형). 가능한 값은 'Oracle', 'MSSQL'(Microsoft SQL Server), 'PostgreSQL'(PostgreSQL), 'Teradata', 'DB2', 'MySQL', 'Netezza', 'AsterData', 'SAPHANA'(SAP HANA), 'RedShift'(Amazon Redshift), 'ODBC'(ODBC ASE, Sybase IQ), '원격 데이터베이스로 HTTP 릴레이'(HTTP 릴레이)입니다.<br /> </td> 
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
   <td> 시간대<br /> </td> 
   <td> 시간대: 참조 <a href="../../installation/using/time-zone-management.md" target="_blank">시간대 관리</a>.<br /> </td> 
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
   <td> 시간대가 있는 날짜 필드: 참조 <a href="../../installation/using/time-zone-management.md" target="_blank">시간대 관리</a>.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

에서 **dataStore > dataSource > sqlParams** 노드, SQL 매개 변수 구성:

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

에서 **dataStore > dataSource > 풀** 노드, 연결된 연결 풀의 매개 변수를 구성합니다.

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
   <td> 연결 유효성 검사 사이의 지연.<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> 풀에 남아 있는 무료 연결 수입니다.<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> 새 연결을 거부하기 전에 허용되는 최대 연결 수입니다. 다음 보기 <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">기술 정보</a>.<br /> </td> 
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

다음은 의 다양한 매개 변수입니다 **dataStore > virtualDir** 노드 아래에 있어야 합니다. 가상 디렉터리를 실제 디렉터리에 매핑하는 구성입니다.

자세한 내용은 [공개 리소스 관리](file-res-management.md).

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
   <td> 이름<br /> </td> 
   <td> 가상 디렉터리 이름 <br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> 경로<br /> </td> 
   <td> 실제 디렉터리의 전체 경로<br /> </td> 
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

다음은 의 다양한 매개 변수입니다 **dataStore > preprocessCommand** 노드 아래에 있어야 합니다. 이는 &#39;파일 로드&#39; 워크플로우 활동을 사전 처리하기 위한 승인된 명령입니다.

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
   <td> 명령<br /> </td> 
   <td> 명령줄 <br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> 명령줄 레이블<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> 이름<br /> </td> 
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

다음은 의 다양한 매개 변수입니다 **dnsConfig** (DNS 구성) 노드입니다.

자세한 내용은 다음을 참조하십시오 [섹션](../../installation/using/configuring-campaign-server.md).

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
   <td> 도메인 이름: 기본 도메인 이름. SMTP HELO 명령에 사용됩니다. 기본적으로 에서는 Windows에서 선언된 첫 번째 네트워크 인터페이스의 네트워크 매개 변수를 사용합니다. 또는 Linux(도메인 또는 검색 항목)에서 file/etc/resolv.conf을 구문 분석합니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> DNS 서버: 쉼표로 구분된 도메인 이름 서버(DNS) 목록 아래 메모를 참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 다시 시도<br /> </td> 
   <td> DNS 쿼리에 대한 다시 시도 횟수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> 시간 제한<br /> </td> 
   <td> DNS 쿼리에 대한 시간 제한(밀리초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5000년<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>참고 사항 **nameServer**: 기본적으로 은 네트워크를 사용합니다
>Windows에서 선언된 첫 번째 네트워크 인터페이스의 매개 변수
>UNIX에서 정의되지 않았습니다. 도메인 이름 서버(DNS)를 정의합니다
>MTA가 을 사용하여
>도메인.
>
>이 값이 정의되지 않으면 MTA는 호스트 네트워크 구성에서 이 정보를 검색합니다. 여러 DNS가 가능한 경우 다른 DNS 주소는 쉼표로 구분해야 합니다(예: 212.155.207.1,212.155.207.2). 게재 서버에 여러 개의 네트워크 인터페이스가 있는 경우 MTA에서 사용하는 DNS 목록이 첫 번째 인터페이스입니다. 이 경우 **nameServer** 매개 변수를 사용하여 모호성을 방지할 수 있습니다.

>[!CAUTION]
>
>네트워크 호스트 구성에서 DHCP를 사용하는 경우 MTA가 DHCP에서 제공하는 DNS 목록을 찾지 못합니다. 이 경우 Windows 제어판의 네트워크 매개 변수에서 DNS 목록을 지정하는 것이 좋습니다.

## exec {#exec}

다음은 의 다양한 매개 변수입니다 **exec** (명령 실행) 노드 아래에 표시됩니다.

자세한 내용은 [허가된 외부 명령 제한](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands).

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
   <td> 에 추가할 명령이 들어 있는 파일의 허용 목록에 추가하다 경로입니다. <br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> 사용자<br /> </td> 
   <td> 다른 사용자로 명령을 실행합니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

다음은 의 다양한 매개 변수입니다 **htmlToPdf** 노드 아래에 있어야 합니다. 웹 페이지를 PDF 문서로 변환하는 서비스의 구성입니다.

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
   <td> 명령<br /> </td> 
   <td> 변환을 실행하기 위한 명령줄('기타' 모드).<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessusCount<br /> </td> 
   <td> 맥스 한 컴퓨터에서 한 번에 허용되는 전환 프로세스 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> 모드<br /> </td> 
   <td> 변환에 사용할 도구입니다. 가능한 값은 다음과 같습니다. phantomjs, wkhtmltopdf, 기타, 비활성화됨<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> 시간 제한<br /> </td> 
   <td> 전환 시간 제한: 최대 전환 시간(초)입니다. 이 임계값을 벗어나면 변환 프로세스가 중지되고 오류가 발생합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 120년<br /> </td> 
  </tr> 
  <tr> 
   <td> 자세한 정보<br /> </td> 
   <td> 세부 정보 표시 모드: 가능한 오류를 진단하려면 세부 정보 모드로 시작하십시오.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> 프로세스를 기다리는 동안 지연: 모든 프로세스가 동시에 사용되는 경우 지연 시간(초)과 프로세스가 종료되기를 기다리는 경우 지연 시간(초)입니다. 이 지연을 초과하면 전환이 중지되고 오류가 발생합니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

phantomjs의 예:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## ims {#ims}

다음은 의 다양한 매개 변수입니다 **ims** 노드 아래에 있어야 합니다. Campaign이 [IMS](../../integrations/using/about-adobe-id.md).

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
   <td> authIMSClientId<br /> </td> 
   <td> 클라이언트 ID<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSClientSecret<br /> </td> 
   <td> 비밀 키(AES에서 암호화됨)<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSCode<br /> </td> 
   <td> 인증 코드(AES에서 암호화됨)<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSEndpoint<br /> </td> 
   <td> IMS 서버 URL<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'https://ims-na1.adobelogin.com'<br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientId<br /> </td> 
   <td> 기술 계정 클라이언트 ID<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientSecret<br /> </td> 
   <td> 기술 계정 암호 키(AES에서 암호화)<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAId<br /> </td> 
   <td> 기술 계정 ID<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAPribateKey<br /> </td> 
   <td> 기술 계정 개인 키(AES에서 암호화됨)<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## JavaScript {#javascript}

다음은 의 다양한 매개 변수입니다 **javaScript** 노드 아래에 있어야 합니다. JavaScript 인터프리터의 구성입니다.

자세한 내용은 [보고 설명서](../../reporting/using/actions-on-reports.md#memory-allocation).

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
   <td> 512년 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> 킬로 octets의 각 스택 청크의 크기입니다. 대부분의 사용자가 조정해서는 안 되는 메모리 관리 조정 매개 변수입니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

다음은 의 다양한 매개 변수입니다 **mailExchanger** 노드 아래에 있어야 합니다. SMTP 서버의 구성입니다.

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
   <td> SMTP 서버: 전자 메일 전송을 위한 SMTP 서버의 IP 주소입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> 전자 메일 전송에 사용되는 SMTP 서버의 TCP 포트입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 25년<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 모듈 {#module}

다음은 의 다양한 매개 변수입니다 **모듈** 노드 아래에 있어야 합니다. 네임스페이스 제한 모듈 xtk에 대한 구성입니다.

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
   <td> 새 엔터티를 만들 때 사용되는 기본 네임스페이스입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 모니터링 {#monitoring}

다음은 의 다양한 매개 변수입니다 **모니터링** 노드 아래에 있어야 합니다. 모니터링 서비스 구성입니다.

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
   <td> 최대 준비 시간: 게재 작업을 더 이상 준비할 수 없는 기간(초).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 3600년<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> 모니터링 서비스에서 실행한 Unix 스크립트입니다.<br /> </td> 
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

다음은 의 다양한 매개 변수입니다 **oconv** 노드 아래에 있어야 합니다. 문서 변환 서버의 구성입니다.

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
   <td> maxConversion<br /> </td> 
   <td> OpenOffice 서버가 수행할 수 있는 최대 전환 수입니다. 이 수를 초과하면 서버가 다시 시작됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> 강제 닫기 전에 OpenOffice 서버의 최대 유휴 시간입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7200년<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> OpenOffice 서버가 수신 대기하는 포트의 간격입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 8101년-8110년<br /> </td> 
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

다음은 의 다양한 매개 변수입니다 **proxyConfig** 노드 아래에 있어야 합니다. 프록시 매개 변수의 구성입니다.

자세한 내용은 [프록시 연결 구성](file-res-management.md).

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
   <td> 활성화됨<br /> </td> 
   <td> 프록시 서버를 사용합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> 재정의<br /> </td> 
   <td> 예외: 프록시 매개 변수를 무시할 주소 목록입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> 고유 프록시 서버: 모든 유형의 프록시에 대해 동일한 구성을 사용하십시오.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP 프록시/보안 프록시 {#http-proxy---secure-proxy-}

에서 **proxyConfig > HTTP 프록시/보안 프록시** 노드 아래의 매개 변수를 구성합니다.

자세한 내용은 [프록시 연결 구성](file-res-management.md).

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
   <td> 로그인<br /> </td> 
   <td> 프록시 서버에 연결할 로그인<br /> </td> 
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

다음은 의 다양한 매개 변수입니다 **threadPool** 노드 아래에 있어야 합니다.

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

다음은 의 다양한 매개 변수입니다 **urlPermission** 노드 아래에 있어야 합니다. Javascript 코드가 액세스할 수 있는 URL 목록입니다.

Javascript 코드에서 발생한 URL을 Adobe Campaign 서버에서 사용할 수 있는지 여부를 지정하는 도메인 및 정규 표현식 목록입니다.

URL을 찾을 수 없는 경우에는 지정된 기본 모드에 따라 기본 작업이 수행됩니다.

자세한 내용은 [발신 연결 보호](../../installation/using/configuring-campaign-server.md#url-permissions).

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
   <td> 작업<br /> </td> 
   <td> URL이 인증된 목록(열거형)에 없는 경우 기본 작업입니다. 가능한 값은 'ignore'(경고 메시지 없이 승인, 보호를 비활성화해야 함), 'warn'(경고 메시지 승인 및 문제) 및 '거부'(URL에 대한 액세스 금지)입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 거부<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> URL 선택 메커니즘의 디버깅 추적: url 확인 프로세스 중에 추가 메시지가 표시됩니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### url {#url}

각 URL에 대해 **url** 노드(다음 매개 변수 포함):

자세한 내용은 [발신 연결 보호](../../installation/using/configuring-campaign-server.md#url-permissions).

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
   <td> URL에 관련된 도메인 이름 또는 도메인 상위 항목: 확인할 URL 도메인의 전체 또는 일부를 확인하는 것이 좋습니다. URL은 도메인에 dsnSuffix가 포함되어 있는 경우에만 정규 표현식에 대해 확인됩니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> 이 도메인에 속하는 URL의 유효성을 검사하는 정규식입니다. dnsSuffix에 해당하는 경우 URL이 확인해야 하는 정규식입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

레코드가 **dnsSuffix** 하지만 **urlRegEx**&#x200B;로 설정되면 다음 레코드가 검사됩니다.

예를 들어 domain business.com의 모든 URL에 대한 액세스를 승인하기 위해 두 개의 레코드를 정의할 수 있습니다.

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.&#42;&quot;

및 

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.&#42;&quot;

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

다음은 의 다양한 매개 변수입니다 **xtkJobs** 노드 아래에 있어야 합니다. 서버 작업의 구성입니다.

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
   <td> 서버 처리 중 메모리 상태 새로 고침 기간(ms)<br /> </td> 
   <td> Long<br /> </td> 
   <td> 500년<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 보관 {#archiving}

다음은 의 다양한 매개 변수입니다 **보관** 노드 아래에 있어야 합니다. 백그라운드에서 실행된 보관 작업의 구성입니다.

자세한 내용은 [전자 메일 보관 활성화(온-프레미스)](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

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
   <td> 100년<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> 보낸 메시지(열거형)의 보관 전략입니다. 가능한 값은 '0'(보관 없음) 및 '1'(SMTP 서버로 보낸 메시지의 보관을 전송)입니다.<br /> </td> 
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
   <td> 압축된 아카이브 크기: 압축된 보관 파일의 최대 파일 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> 보관(열거형) 중에 사용된 압축 형식입니다. 가능한 값은 '0'(압축 없음) 및 '1'(zip 포맷으로 전송된 메시지 압축)입니다.<br /> </td> 
   <td> 바이트<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> 처리되지 않은 전자 메일의 자동 보관 전 지연: 처리되지 않은 이메일이 보관되기 전 일 수입니다.<br /> </td> 
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
   <td> 메모리 사용량 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600년<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> 각 업데이트 이벤트 간의 지연(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간입니다. 자세한 내용은 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 다시 시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> 처리되지 않은 전자 메일이 삭제되기 전 일 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 먼저 시작되고 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
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
   <td> SMTPS 지원 활성화: 원격 서버에서 지원하는 경우 안전 모드(STARTTLS/SMTPS)에서 전자 메일 게재를 활성화합니다.<br /> </td> 
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
   <td> 사용할 SMTP 릴레이의 DNS 이름 또는 IP 주소의 쉼표로 구분된 목록입니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> SMTP 서버의 IP 포트입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25년<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

다음은 의 다양한 매개 변수입니다 **inMail** 노드 아래에 있어야 합니다. 인바운드 전자 메일 관리 모듈의 구성입니다.

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
   <td> 인스턴스 이름 확인: true인 경우 Message-ID 헤더에 포함된 Adobe Campaign 인스턴스의 이름은 현재 인스턴스와 같아야 합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> 전달 주소: 규칙에 의해 기본 이메일 전송 주소가 처리되지 않습니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> 오류 주소: 잘못된 전자 메일을 전송하는 데 사용되는 기본 주소입니다(잘못된 MIME 인코딩). <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> 메시지 크기 무시: POP3 서버에서 반환된 메시지의 크기를 무시하는 데 사용됩니다. 이 경우 모듈에는 '.'가 필요합니다. 를 클릭합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> 메시지 읽기 기간: 메시지 큐 폴링 빈도<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5개<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> 업데이트할 최대 로그 수: 데이터베이스를 업데이트하기 전에 메모리에 유지할 최대 로그 메시지 수를 정의합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 20년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> POP3 세션 동안 읽을 최대 메시지 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 200년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용량 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> 세션 기간: 메시지 처리 세션의 최대 기간입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100년<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> POP3 폴링 기간<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300년<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> 읽기 메시지의 큐 크기<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100년<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> POP3 서버와의 통신 시간 제한. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 300년<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간입니다. 자세한 내용은 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 다시 시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> 폴링할 계정의 데이터베이스 다시 로드 빈도<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600년<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 먼저 시작되고 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

에서 **inMail > msgDump** 노드 아래의 매개 변수를 구성합니다. 처리된 메시지 덤프의 구성입니다.

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

다음은 의 다양한 매개 변수입니다 **상호 작용** 노드 아래에 있어야 합니다. 인바운드 상호 작용 이벤트에 대한 쓰기 데몬의 구성입니다.

자세한 내용은 [상호 작용 - 데이터 버퍼](../../installation/using/interaction---data-buffer.md).

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
   <td> 맥스 호출 데이터를 위해 공유 메모리에 저장된 문자 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용량 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> 맥스 공유 메모리에 저장된 이벤트 수.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> 통계에 저장할 제안 바로 뒤에 정렬된 최대 적격의 오퍼 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간입니다. 자세한 내용은 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 다시 시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 먼저 시작되고 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> 응답 시간 통계에 대한 집계 기간(초). 0은 통계 저장소가 비활성화되었음을 의미합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600년<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> 맥스 개인을 식별하기 위해 공유 메모리에 저장된 문자 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

다음은 의 다양한 매개 변수입니다 **mta** 노드 아래에 있어야 합니다. 게재 에이전트의 구성입니다.

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
   <td> 보낸 전자 메일의 저장 경로: 비어 있지 않으면 보낸 이메일의 모든 소스 파일이 저장되는 경로가 됩니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> 덤프 디렉터리: 비어 있지 않으면 이 디렉터리에 보낸 메일 메시지의 MIME 편지함을 복사합니다. 문제 해결에 사용됩니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> DNS 쿼리 로그 지연: 로그를 표시하는 시간(밀리초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> 오류 통계 빈도: 데이터베이스의 통계와 저장소 생성 사이의 시간입니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 300년<br /> </td> 
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
   <td> 로그 메시지 수준을 표시합니다. 데이터베이스에 작성된 로그의 심각도 수준입니다. MTA에서 생성된 로그 메시지가 모두 데이터베이스에 기록되는 것은 아닙니다. 이 매개 변수를 사용하여 데이터베이스에 메시지를 작성해야 하는 수준을 정의할 수 있습니다. 레벨 2를 정의하는 경우 레벨 1과 0의 메시지도 작성되지만 레벨 1을 정의하는 경우에는 레벨 1과 0의 메시지만 기록됩니다. 가능한 값은 다음과 같습니다. 0(오류), 1(경고), 2(정보)<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2개<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> mta 프로세스에서 사용할 수 있는 최대 메모리 크기(MB)입니다. 이 제한 이상의 경우, 사용하는 메모리가 시스템에 해제되도록 프로세스가 다시 시작됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1024년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용량 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600년<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> 고려할 연결 임계값입니다. errorPeriodSec에서 지정한 기간의 총 연결 수가 임계값보다 엄격하게 낮은 경우 지정된 경로에 대해 오류 통계가 생성되지 않습니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100년<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> 고려할 오류 임계값: errorPeriodSec에서 지정한 기간의 총 오류 수가 임계값보다 엄격하게 낮은 경우 지정된 경로에 대해 오류 통계가 생성되지 않습니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> 고려할 메시지 임계값입니다. errorPeriodSec에서 지정한 기간 동안 보낸 총 메시지 수가 임계값보다 엄격하게 낮은 경우 지정된 경로에 대해 오류 통계가 생성되지 않습니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000년<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 알림 릴레이: HostName:알림을 중계하는 데 사용되는 포트입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간입니다. 자세한 내용은 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 다시 시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> 보관된 전자 메일이 삭제되기 전 지연: dataLogPath에 지정된 디렉토리에 있는 보관된 이메일을 삭제하기 전 일 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> 손실된 메시지 다시 시도: 하위 프로세스가 중단된 경우 게재 중 일부가 다시 시도됩니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 먼저 시작되고 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> 서명 메커니즘을 활성화합니다. 이에 따라 이메일의 링크 추적 보안이 개선됩니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> 게재 통계 서버의 주소입니다. 
    &lt;dns or="" ip=""&gt; 
      <code>[</code>: 
     &lt;port&gt; 
       <code>]</code>. 자세한 내용은 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">통계 서버의 좌표</a>. 
      <br /> 
     </td> 
   <td> 문자열<br /> </td> 
   <td> 정의되지 않은 경우 기본 포트는 7777입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSsupport<br /> </td> 
   <td> 도메인별 TLS 활성화: mx에서 구성할 수 있는 TLS를 활성화합니다(최신 통계 서버 필요).<br /> </td> 
   <td> 부울<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <tr> 
   <td> statServerVersion<br /> </td> 
   <td> 사용된 프로토콜 버전: 통신 프로토콜 버전(v5.11 및 6.0.2 서버의 경우 1, v6.1 서버의 경우 2).<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 정의되지 않은 경우 최신 버전이 사용됩니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> 를 "true"로 설정하면 인스턴스가 <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">향상된 MTA</a>.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> 확인 모드: 확인 모드를 활성화합니다(메시지의 물리적 전송 없음). 시뮬레이션 및 테스트에 사용됨).<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> 작업 디렉터리: MTA가 하위 프로세스와 통신하는 데 사용하는 임시 파일의 위치입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMail<br /> </td> 
   <td> X-메일 필드: SMTP 메일 헤더의 'X-Mail' 필드 값.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'nlserver, 빌드 $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

에서 **캐시** 노드 아래의 매개 변수를 구성합니다. 로컬 파일 캐시 구성입니다.

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
   <td> 재생 후: 캐시에서 파일을 자동으로 삭제하여 스토리지를 재확보할 수 있는 기간(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> 최대 캐시 크기(Mb)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1024년<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> 제거 빈도: 캐시 제거 메커니즘의 실행 간격(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 3600년<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 릴레이 {#relay}

에서 **mta > 릴레이** 노드 아래의 매개 변수를 구성합니다. 메시지 배달에 대한 메일 서버의 구성입니다.

이 목록은 MX DNS 쿼리에서 반환한 MX 목록과 같은 방식으로 처리됩니다. 일반적으로 첫 번째 MX를 사용할 수 있는 한 사용하고 그 다음 MX를 사용하는 등의 방식입니다.

자세한 내용은 [SMTP 릴레이](../../installation/using/configuring-campaign-server.md#smtp-relay).

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
   <td> 사용할 SMTP 릴레이의 DNS 이름 또는 IP 주소의 쉼표로 구분된 목록입니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> SMTP 서버의 IP 포트입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25년<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 마스터 {#master}

에서 **mta > 마스터** 노드 아래의 매개 변수를 구성합니다. 주 서버의 구성입니다.

자세한 내용은 다음을 참조하십시오 [섹션](../../installation/using/configuring-campaign-server.md#mta-child-processes).

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
   <td> 배달할 작업의 데이터베이스 폴링 빈도입니다. 이 값은 데이터베이스 폴링 빈도(초)를 나타냅니다. 전달을 기다리는 작업 목록을 얻기 위해 MTA는 정기적으로 데이터베이스를 폴링합니다. 작업 대기 시간이 없으면 이 값으로 폴링 기간이 정의됩니다. 그렇지 않으면 작업이 하위 서버로 전송되면 이 폴링 기간은 자동으로 1초로 축소되어 하위 서버를 다시 사용할 수 있게 되는 즉시 새 작업을 다시 처리할 수 있습니다. 이는 하위 서버를 다시 사용할 수 있을 때까지 데이터베이스 쿼리가 매 초마다 수행됨을 의미하지 않습니다. 실제로 하나 이상의 하위 서버를 사용할 수 있는 경우에만 데이터베이스 액세스가 수행됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> 데이터베이스 연결 실패 후 대기 기간입니다. 데이터베이스 연결 오류는 일반적으로 데이터베이스 서버 자체에 의해 발생합니다. 예를 들어 서버를 유지 보수 목적으로 중지할 수도 있습니다. DataBaseRetryDelay 매개 변수는 데이터베이스 연결 실패 시 두 연결 시도 사이의 기간을 정의합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> 개인 키(DomainKeys)의 캐시에 대한 유효 기간입니다. 도메인 키 권장 사항(http://antispam.yahoo.com/domainkeys)에 따라 전자 메일에 서명하는 데 사용되는 개인 키는 데이터베이스에 옵션으로 저장됩니다. domainKeysReloadPeriodSec 매개 변수는 MTA가 이러한 키를 캐시에 유지할 수 있는 시간(초)을 정의합니다. 이 지연 후에 데이터베이스에서 모든 키를 다시 로드해야 합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> 최대 자식 서버 수입니다. 실행 중인 최대 서버 수를 나타냅니다. 서버 메모리 리소스와 최적의 호환으로 이 수를 제한하는 것이 좋습니다. 이는 배달 중에 확인할 수 있습니다. 사용된 메모리는 사용 가능한 실제 메모리의 3분의 1을 초과할 수 없습니다. 그렇지 않으면 스왑 기능이 사용됩니다. 자세한 내용은 <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">MTA 하위 프로세스</a>.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2개<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> 최소 하위 서버 수입니다. MTA는 최소 이 수의 서버를 계속 실행하려고 합니다. 이 값이 작으면 이 값에 도달할 때까지 매 초마다 새 서버를 다시 시작합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> 시작 시 하위 서버 수입니다. 하위 서버 수는 동적으로 모니터링됩니다. MTA가 시작되면 이 값이 나타내는 수만큼 하위 서버가 만들어집니다. 일반적으로 호스트 리소스를 저장하기 위해 1초보다 빠르게 하위 서버를 시작할 수 없습니다. 그러나 MTA가 시작되면 하위 서버를 가능한 한 빨리 사용할 수 있도록 이 제한이 무시됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 하위 {#child}

에서 **mta > 하위** 노드 아래의 매개 변수를 구성합니다. 하위 서버의 구성입니다.

자세한 내용은 [이메일 전송 최적화](../../installation/using/email-deliverability.md#email-sending-optimization).

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
   <td> 명령줄 인수(옵션) <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> 유휴 하위 서버가 중지될 때까지 시간이 초과되었습니다. 하위 서버의 유휴 시간이 이 매개 변수보다 큰 경우 자동으로 종료되어 호스트 리소스를 확보합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> 최대 메시지 보존 시간입니다. 전송률 조절 때문에 준비된 메시지를 보낼 수 없거나 대상 MTA에 연결할 수 없는 경우 메시지가 중단되며 다음 다시 시도 시 처리됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> 각 하위 서버에서 시작한 FCM에 대한 최대 병렬 Http 요청 수.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> 하위 서버당 최대 메시지 수입니다. 각 MTA 하위는 이 수의 메시지를 처리하여 종료합니다. MTA에서 메모리 또는 리소스 누수가 해가 되지 않도록(일반적으로 몇 만 명) 숫자를 지정하는 것이 중요합니다. MTA 코드에 알려진 메모리 누수가 없는 경우에도 포함된 JavaScript 및 XSL 엔진은 완전히 신뢰할 수 없습니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> 보류 중인 메시지: 배달할 메모리에서 대기하는 최대 메시지 수입니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 2000년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> 하위 프로세스에서 사용할 수 있는 최대 메모리 크기(MB)입니다. 이 제한 이상의 경우, 사용하는 메모리가 시스템에 해제되도록 프로세스가 중지됩니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 128년<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> 배달 커넥터에 대한 SOAP 연결이 중단된 후 시간 초과(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600년<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> 항상 우선 순위가 가장 높은 MX로 시작합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> 다시 시작할 때 연속된 최대 시도 횟수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

에서 **mta > child > smtp** 노드 아래의 매개 변수를 구성합니다. SMTP 세션의 구성입니다.

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
   <td> 원격 서버에서 지원하는 경우 안전 모드(STARTTLS/SMTPS)에서 전자 메일 게재를 활성화합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> 유휴 세션 시간 제한. 이 매개 변수는 세션이 지정된 도메인에 여러 메시지를 전송하는 데 재사용되는 경우에만 사용됩니다. MTA가 메시지 전송을 완료하면 SMTP 세션이 사용한 SMTP 세션이 체계적으로 닫히지 않습니다. 동일한 도메인에 대해 메시지를 보낼 준비가 된 경우 동일한 SMTP 세션이 다시 사용되므로 세션이 자동으로 닫히지 않습니다. 매개 변수 IdleSessionTimeout 매개 변수를 사용하면 SMTP 세션이 다른 메시지를 기다리는 동안 활성 상태로 남아 있는 시간을 정의할 수 있습니다. 기간이 경과하면 세션이 자동으로 닫힙니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5개<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> 연결을 재시도하기 전 초기 지연. 연결이 실패할 때마다 이 지연이 두 배로 증가합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> 하위 서버별 최대 SMTP 세션 수입니다. 메시지를 배달하려면 MTA가 수신자 MTA와 SMTP 연결을 초기화합니다. 주어진 자식 서버에 대한 동시 및 활성 SMTP 세션의 최대 수는 이 값으로 제한됩니다. 이 값을 maxSpareServers에 곱하면 주어진 자식 서버에서 동시에 처리할 수 있는 최대 메시지 수를 얻을 수 있습니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000년<br /> </td> 
  </tr> 
 </tbody> 
</table>

에서 **mta > child > smtp > IPAffness** 노드 아래의 매개 변수를 구성합니다. 최적화된 발신 SMTP 트래픽을 위해 IP 주소가 있는 관심 영역 관리를 구성합니다.

자세한 내용은 [사용할 IP 주소 목록](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) 및 [관심도 있는 아웃바운드 SMTP 트래픽 관리](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

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
   <td> 도메인 이름: IP 주소에 연결된 로컬 도메인 이름입니다. SMTP HELO 명령을 실행할 때 사용됩니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> 이름<br /> </td> 
   <td> 논리 이름: 사용자별로 선호도에 연결된 이름 이름은 세미콜론을 사용하여 구분됩니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

에서 **mta > 하위 > smtp > IP** 노드 아래의 매개 변수를 구성합니다.

자세한 내용은 [사용할 IP 주소 목록](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).

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
   <td> 연결된 실제 주소입니다. 예: '192.168.0.1'<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> 연결된 공개 주소 ID입니다. 통계 서버의 키로 사용됩니다. 숫자여야 합니다. 다음 보기 <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">섹션</a>.<br /> </td> 
   <td> Long<br /> </td> 
  </tr> 
  <tr> 
   <td> 가중치<br /> </td> 
   <td> 다른 IP에 상대적인 이 IP에 대한 사용 빈도를 지정합니다(가중치가 클수록 주파수가 높아짐).<br /> </td> 
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

다음은 의 다양한 매개 변수입니다 **nmac** 노드 아래에 있어야 합니다. 푸시 알림 게재에 대한 구성입니다.

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
   <td> useHTTProxy<br /> </td> 
   <td> 공유/proxyHTTP에 정의된 HTTP 프록시를 사용합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 릴레이 {#relay-1}

다음은 의 다양한 매개 변수입니다 **nmac > relay** 노드 아래에 있어야 합니다. 이렇게 하면 메시지 전달에 대한 릴레이 사용(ios http2 커넥터)을 구성합니다.

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
   <td> 443년<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> 인증서 체인(PEM 파일). 모의 서버를 사용할 때 유용합니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 파이프라인 {#pipelined}

다음은 의 다양한 매개 변수입니다 **파이프라인** 노드 아래에 있어야 합니다. 파이프라인 서비스에 대한 이벤트 처리 모듈의 구성입니다.

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
   <td> 공개 키를 저장할 때 개발자 연결에서 생성된 애플리케이션의 이름입니다. <br /> </td> 
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
   <td> 게이트웨이 토큰을 가져오는 URL.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> 토큰을 가져오는 개인 키(XtkKey 옵션을 사용하여 AES에서 암호화).<br /> </td> 
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
   <td> 인증 사용 안 함: 인증 없이 파이프라인 서비스에 연결합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> 2개<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> 파이프라인 서비스 URL을 검색할 URL입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> 상태 저장 기간: 프로세스의 내부 정보가 파일에 저장되는 빈도. 0인 경우 비활성 상태입니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> 수신 대기 URL: 파이프라인 서비스의 수신 URL을 강제 적용합니다. <br /> </td> 
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
   <td> 메모리 사용량 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600년<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> 상태 서버 포트: 프로세스의 상태를 쿼리할 수 있는 HTTP 서버 포트입니다. 0인 경우 비활성 상태입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7781년<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> 이 수의 메시지가 처리될 때마다 포인터가 데이터베이스에 저장됩니다.<br /> </td> 
   <td> <br /> </td> 
   <td> 1000년<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushPeriodSec<br /> </td> 
   <td> 포인터가 저장되기 전 지연: 포인터가 이 기간 동안 적어도 한 번 데이터베이스에 저장됩니다(활동이 낮은 경우 유용합니다.).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5개<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간입니다. 자세한 내용은 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 다시 시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSONhreads<br /> </td> 
   <td> 개인화된 JavaScript 커넥터를 사용하는 이벤트 처리를 위한 스레드 수입니다.<br /> </td> 
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
   <td> 오류가 있는 경우 처리 사이의 지연<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> 이 기간 후 포기: 이 기간 후에도 처리가 계속 실패하면 이벤트를 종료합니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300년<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 먼저 시작되고 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 복구 {#repair}

다음은 의 다양한 매개 변수입니다 **복구** 노드 아래에 있어야 합니다. 데이터베이스 복구 모듈의 구성입니다.

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
   <td> 게재 작업 복구 모듈: 복구 모듈에서 게재 작업을 처리할 수 있는 지연 시간(분)입니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

다음은 의 다양한 매개 변수입니다 **securityZone** 노드 아래에 있어야 합니다.

자세한 내용은 [보안 영역 정의](../../installation/using/security-zones.md).

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
   <td> 웹 응용 프로그램에 대한 디버그 모드를 승인합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> 암호 없이 응용 프로그램을 사용하도록 사용자에게 권한을 부여합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> 운영자 로그온에 HTTP 사용을 승인합니다.<br /> </td> 
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
   <td> 사용자/암호 세션 토큰을 승인합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> 레이블<br /> </td> 
   <td> 레이블<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> 이름<br /> </td> 
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
   <td> 오류 세부 정보 표시<br /> </td> 
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

다음은 의 다양한 매개 변수입니다 **securityZone > subNetwork** 노드 아래에 있어야 합니다.

자세한 내용은 [보안 영역 정의](../../installation/using/security-zones.md).

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
   <td> 레이블<br /> </td> 
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
   <td> 이름<br /> </td> 
   <td> 내부 이름<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> 프록시<br /> </td> 
   <td> 이 하위 네트워크에서 인스턴스에 액세스하는 데 사용하는 프록시 의 마스크 또는 주소입니다. 이 경우 'X-Forwarded-For' 헤더는 이 프록시 대신 테스트됩니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

다음은 의 다양한 매개 변수입니다 **sms** 노드 아래에 있어야 합니다. 인바운드 SMS 관리 모듈의 구성입니다.

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
   <td> 512년<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> 세션 연속성 프레임의 되풀이: 최대. 수신 세션이 여전히 활성화되었음을 알리는 두 프레임 사이의 기간(초)<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용량 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600년<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> 검색 빈도: SMS 계정 폴링 기간입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300년<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간입니다. 자세한 내용은 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 다시 시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> 계정 다시 로드 빈도: 폴링할 계정의 데이터베이스 다시 로드 빈도<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600년<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 먼저 시작되고 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> SR 처리에 대한 지연 시간(초): 현재 시간보다 빠른 복구 날짜에서 srReadDelay에 의해 지정된 기간(초)을 뺀 SR만 사용합니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 600년<br /> </td> 
  </tr> 
  <tr> 
   <td> 시간 제한<br /> </td> 
   <td> SMS 게이트웨이와의 통신 시간 제한.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300년<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

다음은 의 다양한 매개 변수입니다 **sms > netsize** 노드 아래에 있어야 합니다.

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
   <td> Netsize와의 연결을 설정할 때 시간 제한(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

다음은 의 다양한 매개 변수입니다 **stat** 노드 아래에 있어야 합니다. 다음은 MTA 통계 모듈의 구성입니다.

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
   <td> 메모리 사용량 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600년<br /> </td> 
  </tr> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> 서버 수신 대기 포트입니다. 다음 보기 <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">섹션</a>.<br /> </td> 
   <td> Short<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간입니다. 자세한 내용은 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 다시 시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 먼저 시작되고 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## sylogd {#syslogd}

다음은 의 다양한 매개 변수입니다 **sylogd** 노드 아래에 있어야 합니다. 로그 관리 모듈의 구성입니다.

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
   <td> 365년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용량 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600년<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간입니다. 자세한 내용은 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 다시 시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 먼저 시작되고 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 추적 {#tracking}

다음은 의 다양한 매개 변수입니다 **추적** 노드 아래에 있어야 합니다. 추적 서버의 구성입니다.

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
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> 이전 빌드에서 생성된 잘못된 형식의 URL을 비활성화합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> consolidationPeriodSec<br /> </td> 
   <td> 통합 기간<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300년<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> 개구부 중복 제거: Outlook과 같은 메일 독자의 메일 미리 보기 효과를 제한하려면 열려 있는 추적 로그가 중복되지 않습니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> 최대 X%의 오류 무시: 아직 고려되지 않은 분개의 비율이 이 값에 도달하지 않는 한 추적 지표를 업데이트하지 마십시오. <br /> </td> 
   <td> 바이트<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> 오류 표시기 업데이트: 오류 표시기를 다시 계산하기 전의 최대 기간입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorsDuration<br /> </td> 
   <td> 다음 작업 중 표시기 계산: 통합 표시기가 더 이상 계산되지 않는 게재 유효 일자 이후의 기간<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다 <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> 원격 추적 서버 호출에서 요청한 로그 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용량 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600년<br /> </td> 
  </tr> 
  <tr> 
   <td> phisbowelServiceAPIKey<br /> </td> 
   <td> Phisbowel Service Endpoint Integration에 대한 API 키. 따라서 이전 빌드에서 생성된 잘못된 형식의 URL의 리디렉션이 보호됩니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phisbowelServiceEndpoint<br /> </td> 
   <td> Phisbowel Service Endpoint Integration에 대한 끝점입니다. 따라서 이전 빌드에서 생성된 잘못된 형식의 URL의 리디렉션이 보호됩니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간입니다. 자세한 내용은 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 다시 시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 먼저 시작되고 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> 최대 X% 추적 무시: 아직 고려되지 않은 분개의 비율이 이 값에 도달하지 않는 한 추적 지표를 업데이트하지 마십시오.<br /> </td> 
   <td> 바이트<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> 추적 표시기 업데이트: 추적 지표를 다시 계산하기 전의 최대 기간입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> 브라우저 식별자 캐시의 크기입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 500년<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

다음은 의 다양한 매개 변수입니다 **trackinglogd** 노드 아래에 있어야 합니다. 추적 로그 쓰기 데몬의 구성입니다.

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
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다 <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> 최대 쓰기 다시 시도: 로그 파일에서 쓰기 오류가 발생할 경우 만들 수 있는 최대 파일 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5개<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> 최대 로그 크기: 디스크에서 로그에 사용되는 최대 공간(MB)입니다. 100MB 이하일 수 있습니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 500년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용량 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> 최대 로그 수: 공유 메모리에 저장된 최대 로그 수입니다. 10000 이상이어야 합니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간입니다. 자세한 내용은 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 다시 시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> 제거 전 로그 수: 로그 파일 제거를 시작하기 전에 삽입된 로그 수입니다. 50000 이하일 수 없습니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 먼저 시작되고 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
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

## 웹 {#web}

다음은 의 다양한 매개 변수입니다 **웹** 노드 아래에 있어야 합니다. 웹 모듈의 구성입니다.

자세한 내용은 다음을 참조하십시오 [섹션](configuring-campaign-server.md#default-port-for-tomcat).

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
   <td> 5개<br /> </td> 
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
   <td> Tomcat 수신 제어 포트: 참조 <a href="configure-tomcat.md" target="_blank">Tomcat 구성</a>.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 8005년<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP 수신 대기 포트: 참조 <a href="configure-tomcat.md" target="_blank">Tomcat 구성</a>.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 8080년<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> SubmitDelivery 호출에 대한 큐 크기: 큐에 추가할 수 있는 최대 SubmitDelivery SOAP 호출 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용량 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600년<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 알림 릴레이: HostName:알림 릴레이를 활성화하는 포트입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간입니다. 자세한 내용은 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 다시 시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 먼저 시작되고 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
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

다음은 의 다양한 매개 변수입니다 **웹 > jsp** 노드 아래에 있어야 합니다. JSP에서 사용하는 매개 변수의 구성입니다.

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
   <td> 디버그 모드에서 JSP 실행<br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> 다운로드 폴더: 클라이언트 콘솔용 설치 프로그램의 다운로드 경로입니다.<br /> </td> 
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

다음 **웹 > jsp > 클래스 경로** 노드에는 JVM을 시작할 때 사용할 모든 클래스 경로 목록이 들어 있습니다. 다음은 기본 구성입니다.

```
'$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat7-websocket.jar
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

다음은 의 다양한 매개 변수입니다 **웹 > jssp** 노드 아래에 있어야 합니다. JSSP에서 사용하는 매개 변수의 구성입니다.

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
   <td> collectionsGarbageAfterRequest<br /> </td> 
   <td> 각 쿼리 뒤에 JavaScript 컨텍스트의 가비지 수집기를 활성화합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> JavaScript 컨텍스트에서 제공하는 최대 페이지 수입니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000년<br /> </td> 
  </tr> 
 </tbody> 
</table>

다음 **웹 > jsp > 클래스 경로** 노드에는 JVM을 시작할 때 사용할 모든 클래스 경로 목록이 들어 있습니다.

### 릴레이 {#relay-2}

다음은 의 다양한 매개 변수입니다 **웹 > 릴레이** 노드 아래에 있어야 합니다. 두 영역 간의 HTTP 요청에 대한 릴레이의 구성입니다.

자세한 내용은 다음을 참조하십시오 [섹션](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> ForbiddenCharsInAuthority<br /> </td> 
   <td> 금지된 문자(도메인): URI의 'authority' 섹션에 금지된 문자 목록<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> 금지된 문자(경로): URI의 'path' 섹션에 있는 금지된 문자 목록입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> 'mod_dir' 모듈 옵션 값: 폴더의 쿼리 중에 사용할 파일 목록입니다.<br /> </td> 
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
   <td> 웹 서버에서 HTTP 릴레이 모듈을 시작합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> 시간 제한<br /> </td> 
   <td> 금지된 URL을 삭제하기 전에 잠시 기다립니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

추가 **web > relay > url** 다음 매개 변수를 사용하여 릴레이할 각 URL의 노드(삽입 순서 정의 우선 순위)입니다.

자세한 내용은 [동적 페이지 보안 및 릴레이](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) 및 [섹션](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> 공인 IP: 이 마스크에 릴레이를 사용할 수 있는 원본 IP 주소의 쉼표로 구분된 목록입니다.<br /> </td> 
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
   <td> 릴레이할 DNS 별칭: 중계할 DNS 별칭 마스크의 쉼표로 구분된 목록(예: '*.adobe.com').<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> 보안 영역(예: webApps)에 상관없이 HTTP 액세스가 승인되었습니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayHost<br /> </td> 
   <td> 원래 호스트 추가: 릴레이할 때 원본 요청의 HTTP '호스트' 헤더를 사용하십시오.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> 초기 URL 경로 추가: url의 전체 경로를 추가하여 대상 페이지의 URL에 전달합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 상태<br /> </td> 
   <td> 공용 리소스의 동기화 상태(열거형). 가능한 값은 'normal'(일반 실행), '블랙리스트'(오류 404차단 목록의 경우 url이에 추가됨) 및 'spare'(있는 경우 예비 서버에서 파일 업로드)입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 정상<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> 대상 페이지의 URL: 참조 <a href="configure-tomcat.md" target="_blank">Tomcat 구성</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 시간 제한<br /> </td> 
   <td> 중계되는 요청의 최대 실행 시간(초)입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> 릴레이할 URL 마스크(예: '/nl*', '*.jsp')<br /> </td> 
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

추가 **web > relay > responseHeader** 각 HTTP 헤더에서 릴레이에 전달된 응답에 추가할 노드입니다.

자세한 내용은 [HTTP 헤더 관리](../../installation/using/configuring-campaign-server.md#managing-http-headers).

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
   <td> 이름<br /> </td> 
   <td> 헤더 이름<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> 값<br /> </td> 
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

다음은 의 다양한 매개 변수입니다 **웹 > 리디렉션** 노드 아래에 있어야 합니다. 이것은 리디렉션 모듈의 구성입니다.

자세한 내용은 다음을 참조하십시오 [섹션](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> Identity Management 시스템(IMS) 조직 식별자: 방문자 ID 서비스 및 IMS SSO에 특별히 사용되는 Adobe Experience Cloud 내의 고유 조직 식별자입니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PComcatePolicy<br /> </td> 
   <td> 영구 쿠키에 사용되는 정책을 설명하는 값입니다(P3P Compact Policy 형식과 준수). <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'CAO DSP COR CUR A DEVa OUR BUS IND UNI COM NAV'<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> 쿠키를 설정할 도메인을 명시적으로 나타내도록 구성할 도메인으로 구분된 도메인 목록입니다. <br /> </td> 
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
   <td> 호출별 로그 수: GetTrackingLogs 메서드 호출 시 기본적으로 반환되는 로그 수입니다.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> 만료된 리디렉션 페이지: 배달 작업에 대한 리디렉션이 만료되었을 때 리디렉션 서버에서 기본적으로 사용하는 웹 페이지의 URL입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> 최대 작업 수: 캐시의 최대 배달 작업 수입니다. 50보다 작을 수 없습니다. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 100년<br /> </td> 
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
   <td> 웹 추적: 알 수 없는 사용자가 방문한 페이지에 대한 로그 만들기 <br /> </td> 
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

다음은 의 다양한 매개 변수입니다 **웹 > 리디렉션 > spareServer** 노드 아래에 있어야 합니다.

자세한 내용은 [중복 추적](../../installation/using/configuring-campaign-server.md#redundant-tracking).

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
   <td> 다음과 같은 경우 고려합니다. 표현식이 true를 반환하는 경우 추적 서버가 고려됩니다. <br /> </td> 
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

다음은 의 다양한 매개 변수입니다 **web > spamCheck** 노드 아래에 있어야 합니다. 이메일 스팸 방지 점수 평가 매개 변수의 구성입니다.

자세한 내용은 [SpamAssassin 구성](../../installation/using/configuring-spamassassin.md).

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
   <td> 명령<br /> </td> 
   <td> 이메일의 스팸 방지 점수를 평가하는 실행 명령(예: 'perl spamcheck.pl')<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

다음은 의 다양한 매개 변수입니다 **wfserver** 노드 아래에 있어야 합니다. 워크플로우 프로세스 구성입니다.

자세한 내용은 [고가용성 워크플로우 및 관심](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

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
   <td> 20년<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스를 시작할 때 실행할 JavaScript의 ID입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 사용량 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800년<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 사용 경고: 지정된 프로세스에 사용된 RAM 양(Mb)에 대한 경고.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600년<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 알림 릴레이: HostName:알림 릴레이를 활성화하는 포트입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간입니다. 자세한 내용은 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 다시 시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 먼저 시작되고 마지막으로 중지되었습니다. 따라서 syslogd 모듈에는 우선 순위 0이 있어야 합니다.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
