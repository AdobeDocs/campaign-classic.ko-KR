---
product: campaign
title: 서버 구성 파일
description: 서버 구성 파일
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '7962'
ht-degree: 40%

---

# 서버 구성 파일{#the-server-configuration-file}



Adobe Campaign의 전체 구성은 **serverConf.xml** 파일, 위치: **conf** 설치 디렉토리 디렉토리. 이 섹션에는 의 다양한 노드와 매개 변수가 모두 나열되어 있습니다. **serverConf.xml** 파일.

>[!NOTE]
>
>서버측 구성은 Adobe에서 호스팅하는 배포에 대해 Adobe에 의해서만 수행될 수 있습니다. 다양한 배포에 대한 자세한 내용은 [호스팅 모델](../../installation/using/hosting-models.md) 섹션 또는 종료 [이 페이지](../../installation/using/capability-matrix.md). 호스팅 및 하이브리드 모델에 대한 설치 및 구성 단계는 다음과 같습니다 [섹션](../../installation/using/hosting-models.md).

첫 번째 매개 변수는 **공유됨** 노드. 인스턴스와 관련되어 있습니다. 모든 nlserver 명령(nlserver web, nlserver wfserver 등)에서 사용할 수 있습니다. 다른 섹션은 특정 nlserver 하위 명령과 관련되어 있습니다.

**공유 매개 변수**

* [인증](#authentication)
* [데이터 저장소](#datastore)
* [dnsConfig](#dnsconfig)
* [exec](#exec)
* [htmlToPdf](#htmltopdf)
* [ims](#ims)
* [javaScript](#javascript)
* [mailExchange](#mailexchanger)
* [모듈](#module)
* [모니터링](#monitoring)
* [ooconv](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [xtkJobs](#xtkjobs)

**기타 매개 변수**

* [보관](#archiving)
* [inMail](#inmail)
* [interactiond](#interactiond)
* [MTA](#mta)
* [nmac](#nmac)
* [파이프라인됨](#pipelined)
* [복구](#repair)
* [보안 영역](#securityzone)
* [sms](#sms)
* [통계](#stat)
* [syslogd](#syslogd)
* [추적](#tracking)
* [trackinglogd](#trackinglogd)
* [웹](#web)
* [wfserver](#wfserver)

## 인증 {#authentication}

다음은 의 다양한 매개 변수입니다. **인증** 노드:

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> checkIPConsistent<br /> </td> 
   <td> IP 주소 확인 활성화.<br /> </td> 
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
   <td> 길게<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> 보안 토큰 시간 제한(초).<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> 캐시 기간: 세션 정보의 캐시(초).<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> 세션 시간 제한(초)입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

다음은 의 다양한 매개 변수입니다. **인증 > XTK** 노드:

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> internalPassword<br /> </td> 
   <td> 내부 계정 암호.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> 내부 계정 보안 영역: 내부 계정에 대해 승인된 영역입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 데이터 저장소 {#datastore}

다음은 의 다양한 매개 변수입니다. **데이터 저장소** 노드. 여기서 서버 데이터 소스를 정의합니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportDirectory<br /> </td> 
   <td> 내보내기 디렉토리: 내보낸 데이터의 대상 디렉토리 경로입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxedDirectory<br /> </td> 
   <td> 추가 샌드박스 디렉터리: 샌드박스에 추가될 다른 경로(쉼표로 구분).<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '/home/customers/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> 양식 캐시 만료 지연: 캐시 항목이 무효화되는 시간 제한(초) O는 캐시 항목이 게시 시간에만 새로 고침됨을 의미합니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 호스트<br /> </td> 
   <td> DNS 마스크: 이 인스턴스가 제공하는 DNS 마스크 목록(쉼표로 구분, * 및 ? pattern)을 참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> 상호 작용 JSSP 캐시 만료 지연: 캐시 항목이 무효화되는 시간 제한(초) 음수 값은 캐시가 항상 무효화됨을 의미합니다. '0', 비어 있거나 잘못된 값은 60으로 간주됩니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> 인스턴스 언어(열거). 가능한 값은 'fr_FR'(Français), 'en_GB'(영어), 'en_US'(영어), 'de_DE'(Deutsch) 및 'ja_JP'(일본어)입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> 업로드 폴더: 업로드한 데이터의 대상 디렉토리 경로.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> 다운로드할 승인된 파일은 ','로 구분됨. 문자열은 유효한 Java 정규 표현식이어야 합니다. 다음을 참조하십시오 <a href="file-res-management.md" target="_blank">업로드 가능한 파일 제한</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> 자격 증명 모음에 암호 저장: Hashicorp 자격 증명 모음을 사용합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> 자격 증명 모음의 암호 경로<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '/v1/secret/campaign/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> 자격 증명 모음 토큰이 포함된 파일의 로컬 경로. $(HOME)은 이 경로에서 사용할 수 있습니다(다른 환경 변수는 사용할 수 없음).<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> Hashicorp Vault URL <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> 캐시 보기의 유효 기간: 캐시 항목이 무효화되는 시간 제한(초). 음수 값은 캐시가 항상 무효화됨을 의미합니다. '0', 비어 있거나 잘못된 값은 60으로 간주됩니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> 작업 디렉터리의 XPath.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> workingDirectory : 작업 디렉토리의 XPath. 기본값: '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

다음은 의 다양한 매개 변수입니다. **dataStore > proxyAdjust** 노드. 정규 표현식과 일치하는 URL은 urlBase에 정의된 URL을 기반으로 재생성됨.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> urlBase<br /> </td> 
   <td> 외부 URL 생성 시 사용할 기본. 예: https://server.domain.com<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> URL과 일치하는 정규 표현식. 예: http://server\.lan\.net.*<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

다음은 의 다양한 매개 변수입니다. **dataStore > 데이터 소스** 노드.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 이름<br /> </td> 
   <td> 데이터 소스 이름<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 기본값<br /> </td> 
  </tr> 
 </tbody> 
</table>

다음에서 **dataStore > dataSource > dbcnx** 노드, 연결 설정을 구성합니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 앤하르<br /> </td> 
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
   <td> 암호화됨<br /> </td> 
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
   <td> 유형(열거형). 가능한 값은 'Oracle', 'MSSQL'(Microsoft SQL Server), 'PostgreSQL'(PostgreSQL), 'Teradata', 'DB2', 'MySQL', 'Netezza', 'AsterData', 'SAPHANA'(SAP HANA), 'RedShift'(Amazon Redshift), 'ODBC'(ODBC(Sybase ASE, Sybase IQ)), '릴레이'(원격 데이터베이스에 대한 HTTP 릴레이)입니다.<br /> </td> 
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
   <td> 유니코드 데이터<br /> </td> 
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

다음에서 **dataStore > dataSource > sqlParams** 노드를 생성하고 SQL 매개변수를 구성합니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
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

다음에서 **dataStore > dataSource > 풀** 노드, 연결된 연결 풀의 매개 변수를 구성합니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> aliveTestDelaySec<br /> </td> 
   <td> 연결 유효성 검사 사이의 지연.<br /> </td> 
   <td> 짧음<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> 풀에 보관된 무료 연결 수.<br /> </td> 
   <td> 짧음<br /> </td> 
  </tr> 
  <tr> 
   <td> 최대 제한<br /> </td> 
   <td> 새 연결을 거부하기 이전에 허용된 최대 연결 수. 이 항목 보기 <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">기술 노트</a>.<br /> </td> 
   <td> 짧음<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> 최대 연결 유휴 시간. 0은 기본값을 의미함.<br /> </td> 
   <td> 짧음<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

다음은 의 다양한 매개 변수입니다. **dataStore > virtualDir** 노드. 가상 디렉터리와 실제 디렉터리 간 매핑의 구성입니다.

자세한 내용은 다음을 참조하십시오. [공개 리소스 관리](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
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

기본 구성은 다음과 같습니다.

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

다음은 의 다양한 매개 변수입니다. **dataStore > preprocessCommand** 노드. 다음은 &#39;파일 로드&#39; 워크플로우 활동의 사전 처리를 위해 승인된 명령입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
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

기본 구성은 다음과 같습니다.

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

다음은 의 다양한 매개 변수입니다. **dnsConfig** (DNS 구성) 노드

자세한 내용은 다음을 참조하십시오. [섹션](../../installation/using/configuring-campaign-server.md).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> 도메인 이름: 기본 도메인 이름. SMTP HELO 명령에 사용됩니다. 기본적으로 은 Windows에서 선언된 첫 번째 네트워크 인터페이스의 네트워크 매개 변수를 사용하거나 Linux(도메인 또는 검색 항목)에서 file/etc/resolv.conf을 구문 분석합니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 이름 서버<br /> </td> 
   <td> DNS 서버: 쉼표로 구분된 도메인 이름 서버(DNS) 목록입니다. 아래 참고 사항을 참조하십시오.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 다시 시도<br /> </td> 
   <td> DNS 쿼리의 재시도 수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> 시간 제한<br /> </td> 
   <td> DNS 쿼리의 시간 제한(밀리초)입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>다음에 대한 참고 사항: **nameServers**: 기본적으로 은 네트워크를 사용합니다
>Windows에서 선언된 첫 번째 네트워크 인터페이스의 매개 변수
>UNIX에서 정의되지 않았습니다. 도메인 이름 서버(DNS)를 정의합니다.
>MTA에서 다음에 대해 선언된 메일 교환기를 가져오는 데 사용됨
>도메인.
>
>이 값이 정의되지 않으면 MTA는 호스트 네트워크 구성에서 이 정보를 찾습니다. 여러 DNS가 가능한 경우 다른 DNS 주소는 쉼표로 구분해야 합니다(예: 212.155.207.1,212.155.207.2). 게재 서버에 여러 네트워크 인터페이스가 있는 경우 MTA에서 사용하는 DNS 목록이 첫 번째 목록입니다. 이 경우 다음을 지정하는 것이 좋습니다. **nameServer** 매개 변수를 사용하십시오.

>[!CAUTION]
>
>네트워크 호스트 구성에서 DHCP를 사용하는 경우 MTA가 DHCP에서 제공하는 DNS 목록을 찾지 못합니다. 이 경우 Windows 제어판의 네트워크 매개 변수에서 DNS 목록을 지정하는 것이 좋습니다.

## exec {#exec}

다음은 의 다양한 매개 변수입니다. **exec** (명령 실행) 노드

자세한 내용은 다음을 참조하십시오. [승인된 외부 명령 제한](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> blacklistFile<br /> </td> 
   <td> 허용 목록에 추가하다에 추가할 명령이 포함된 파일의 경로입니다. <br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> 사용자<br /> </td> 
   <td> 다른 사용자로 명령 실행.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

다음은 의 다양한 매개 변수입니다. **htmlToPdf** 노드. 웹 페이지를 PDF 문서로 변환하는 서비스의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
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
   <td> 최대. 한 대의 컴퓨터에서 한 번에 허용되는 전환 프로세스 수입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> 모드<br /> </td> 
   <td> 변환에 사용할 도구입니다. 가능한 값: phantomjs, wkhtmltopdf, other, disabled<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> 시간 제한<br /> </td> 
   <td> 전환 시간 제한: 최대 전환 시간(초). 이 임계값을 초과하면 전환 프로세스가 중지되고 오류가 발생합니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> 장황해<br /> </td> 
   <td> 상세 표시 모드: 상세 표시 모드에서 시작하여 가능한 오류를 진단합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> 프로세스 대기 시 지연: 모든 프로세스를 동시에 사용하고 프로세스를 확보할 때까지 대기하는 경우 초 단위로 지연됩니다. 이 지연을 초과하면 전환이 중지되고 오류가 발생합니다. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

phantomjs의 예:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## ims {#ims}

다음은 의 다양한 매개 변수입니다. **ims** 노드. 다음을 사용하여 다른 서비스에 연결하는 Campaign 구성입니다. [IMS](../../integrations/using/about-adobe-id.md).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
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
   <td> 암호 키(AES로 암호화)<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSCode<br /> </td> 
   <td> 인증 코드(AES로 암호화)<br /> </td> 
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
   <td> 기술 계정 암호 키(AES로 암호화)<br /> </td> 
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
   <td> authIMSTAPrivateKey<br /> </td> 
   <td> 기술 계정 비공개 키(AES로 암호화)<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## JavaScript {#javascript}

다음은 의 다양한 매개 변수입니다. **javaScript** 노드. JavaScript 인터프리터의 구성입니다.

자세한 내용은 [보고 설명서](../../reporting/using/actions-on-reports.md#memory-allocation).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 최대 MB<br /> </td> 
   <td> 가비지 수집기를 실행하기 전의 최대 크기(MB)입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> 스택 크기KB<br /> </td> 
   <td> 각 스택별 크기(킬로 옥텟). 대부분의 사용자가 조정해서는 안 되는 메모리 관리 조정 매개 변수입니다. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchange {#mailexchanger}

다음은 의 다양한 매개 변수입니다. **mailExchange** 노드. SMTP 서버의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> mxAddress<br /> </td> 
   <td> SMTP 서버: 전자 메일 전송에 사용할 SMTP 서버의 IP 주소.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> 이메일 전송에 사용되는 SMTP 서버의 TCP 포트.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 모듈 {#module}

다음은 의 다양한 매개 변수입니다. **모듈** 노드. 네임스페이스 제한 모듈 xtk에 대한 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 기본 이름 공간<br /> </td> 
   <td> 새 엔티티 생성 시 사용되는 기본 네임스페이스.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 모니터링 {#monitoring}

다음은 의 다양한 매개 변수입니다. **모니터링** 노드. 모니터링 서비스 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPreparationJobsSec<br /> </td> 
   <td> 최대 준비 시간: 이후 게재 작업이 더 이상 준비되지 않아야 하는 기간(초)입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> 모니터링 서비스에서 실행된 Unix 스크립트.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> 모니터링 서비스에서 실행할 Windows 스크립트.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## ooconv {#ooconv}

다음은 의 다양한 매개 변수입니다. **ooconv** 노드. 문서 변환 서버의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxConversions<br /> </td> 
   <td> OpenOffice 서버가 수행할 수 있는 최대 전환 수. 이 수를 초과하면 서버가 다시 시작됩니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> 강제 종료 이전 OpenOffice 서버의 최대 유휴 시간.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> OpenOffice 서버가 수신하는 포트 간격.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> URL<br /> </td> 
   <td> 문서 전환 서버 URL.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

다음은 의 다양한 매개 변수입니다. **proxyConfig** 노드. 프록시 매개 변수의 구성입니다.

자세한 내용은 다음을 참조하십시오. [프록시 연결 구성](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 활성화됨<br /> </td> 
   <td> 프록시 서버 사용.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> 재정의<br /> </td> 
   <td> 예외: 프록시 매개변수를 무시할 수 있는 주소 목록.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> 고유 프록시 서버: 모든 유형의 프록시에 대해 동일한 구성을 사용합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP 프록시/보안 프록시 {#http-proxy---secure-proxy-}

다음에서 **proxyConfig > HTTP 프록시/보안 프록시** 노드에서 다음 매개 변수를 구성합니다.

자세한 내용은 다음을 참조하십시오. [프록시 연결 구성](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
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
   <td> 프록시 서버 연결 로그인<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> 암호<br /> </td> 
   <td> 프록시 서버 연결용 암호<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> 프록시 서버 포트<br /> </td> 
   <td> 짧음<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

다음은 의 다양한 매개 변수입니다. **threadPool** 노드.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxThreadcount<br /> </td> 
   <td> 풀의 최대 스레드 수. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

다음은 의 다양한 매개 변수입니다. **urlPermission** 노드. Javascript 코드가 액세스할 수 있는 URL 목록입니다.

Javascript 코드에서 발견된 URL을 Adobe Campaign 서버에서 사용할 수 있는지 여부를 지정하는 도메인 및 정규 표현식 목록입니다.

URL을 찾을 수 없는 경우 지정된 기본 모드에 따라 기본 작업이 수행됩니다.

자세한 내용은 다음을 참조하십시오. [발신 연결 보호](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 작업<br /> </td> 
   <td> URL이 승인된 목록(열거형)에 없는 경우 기본 작업입니다. 가능한 값은 '무시'(경고 메시지 없이 승인, 보호 해제 필요), '경고'(경고 메시지 승인 및 발행) 및 '거부'(URL에 대한 액세스 금지)입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 거부<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> URL 선택 메커니즘의 디버깅 추적: URL 확인 프로세스 중에 추가 메시지를 발행합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### URL {#url}

각 URL에 대해 **url** 다음 매개 변수가 있는 노드:

자세한 내용은 다음을 참조하십시오. [발신 연결 보호](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dns 접미사<br /> </td> 
   <td> URL과 관련된 도메인 이름 또는 도메인 상위(확인할 URL 도메인의 전체 또는 일부)로, 확인 속도를 높입니다. 해당 도메인에 dsnSuffix가 포함된 경우 URL은 정규 표현식과 관련해서만 확인됩니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> 이 도메인에 속한 유효성 검사 URL을 미세 조정하는 정규 표현식: URL이 dnsSuffix와 일치해야 하는 정규 표현식입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

레코드가 다음 조건을 충족하는 경우 **dns 접미사** 그러나 아님 **urlRegEx**, 다음 레코드를 검사합니다.

예를 들어 business.com 도메인의 모든 URL에 대한 액세스 권한을 부여하려면 다음 두 가지 레코드를 정의할 수 있습니다.

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.&#42;&quot;

및

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.&#42;&quot;

기본 구성은 다음과 같습니다.

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
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

다음은 의 다양한 매개 변수입니다. **xtkJobs** 노드. 서버 작업의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> 서버 처리 시 메모리 상태 새로 고침 기간(밀리초).<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 보관 {#archiving}

다음은 의 다양한 매개 변수입니다. **보관** 노드. 백그라운드에서 실행된 보관 작업의 구성입니다.

자세한 내용은 다음을 참조하십시오. [전자 메일 보관 활성화(온-프레미스)](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> acquireLimit<br /> </td> 
   <td> 동시에 처리할 EML 수<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> 보관 유형<br /> </td> 
   <td> 보낸 메시지의 보관 전략(열거). 가능한 값은 '0'(보관 안 함)과 '1'(보낸 메시지의 보관을 SMTP 서버로 전송)입니다.<br /> </td> 
   <td> 바이트<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 인수<br /> </td> 
   <td> 시작 매개변수<br /> </td> 
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
   <td> 압축 일괄 처리 크기<br /> </td> 
   <td> 압축된 아카이브 크기: 압축된 아카이브의 최대 파일 수입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> 압축 형식<br /> </td> 
   <td> 보관(열거) 중에 사용되는 압축 형식입니다. 가능한 값은 '0'(압축 안 함)과 '1'(zip 형식을 사용하여 보낸 메시지 압축)입니다.<br /> </td> 
   <td> 바이트<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> 처리되지 않은 이메일의 자동 보관 이전 지연: 처리되지 않은 이메일이 보관되기까지의 일수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스 시작 시 실행할 JavaScript의 ID.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 소모 경고: 지정된 프로세스에서 소비한 RAM의 양(MB)에 대한 경고입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 소모 경고: 주어진 프로세스에서 소비한 RAM의 양(MB)에 대한 경고.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> 각 업데이트 이벤트 간의 지연(초)입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 다음을 참조하십시오 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 재시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> 처리되지 않은 이메일이 삭제되기까지의 일수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 처음 시작되고 마지막으로 중지됩니다. 따라서 syslogd 모듈의 우선 순위는 0이어야 합니다.<br /> </td> 
   <td> 짧음<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> 대상 보관 중<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> SMTPS 지원 활성화: 원격 서버에서 지원하는 경우 안전 모드(STARTTLS/SMTPS)에서 이메일 게재를 활성화합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> 보관 중인 SMTP 서버 연결 수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> 사용할 SMTP 릴레이의 쉼표로 구분된 DNS 이름 또는 IP 주소 목록. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> SMTP 서버의 IP 포트.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

다음은 의 다양한 매개 변수입니다. **inMail** 노드. 인바운드 이메일 관리 모듈의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 인수<br /> </td> 
   <td> 시작 매개변수<br /> </td> 
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
   <td> 인스턴스 이름 확인: true인 경우 Message-ID 헤더에 포함된 Adobe Campaign 인스턴스 이름은 현재 인스턴스와 동일해야 합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> 전달 주소: 규칙에 의해 처리되지 않는 기본 이메일 전송 주소. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> 오류 주소: 잘못된 이메일(잘못된 MIME 인코딩)을 전송하는 데 사용되는 기본 주소입니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> 메시지 크기 무시: POP3 서버에서 반환된 메시지의 크기를 무시하는 데 사용됩니다. 이 경우 모듈에는 '.'가 필요합니다. 메시지 끝에. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> 메시지 읽기 기간: 메시지 대기열 폴링 빈도.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스 시작 시 실행할 JavaScript의 ID.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadlog<br /> </td> 
   <td> 업데이트할 최대 로그 수: 데이터베이스를 업데이트하기 전에 메모리에 보관할 최대 로그 메시지 수를 정의합니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> POP3 세션 도중 읽을 수 있는 최대 메시지 수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 소모 경고: 지정된 프로세스에서 소비한 RAM의 양(MB)에 대한 경고입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 소모 경고: 주어진 프로세스에서 소비한 RAM의 양(MB)에 대한 경고.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> 세션 기간: 메시지 처리 세션의 최대 기간입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> POP3 폴링 기간<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> 읽은 메시지의 대기열 크기<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> POP3 서버와의 통신 시간 제한. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 다음을 참조하십시오 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 재시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> 다시 로드 기간 초<br /> </td> 
   <td> 폴링할 계정의 데이터베이스 리로드 빈도.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 처음 시작되고 마지막으로 중지됩니다. 따라서 syslogd 모듈의 우선 순위는 0이어야 합니다.<br /> </td> 
   <td> 짧음<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msg덤프 {#msgdump}

다음에서 **inMail > msg덤프** 노드에서 다음 매개 변수를 구성합니다. 처리된 메시지 덤프의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 덤프<br /> </td> 
   <td> 텍스트 포맷의 모든 인바운드 메시지를 저장합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> 메시지 덤프 경로.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interactiond {#interactiond}

다음은 의 다양한 매개 변수입니다. **interactiond** 노드. 인바운드 상호 작용 이벤트에 대한 쓰기 디먼의 구성입니다.

자세한 내용은 다음을 참조하십시오. [상호 작용 - 데이터 버퍼](../../installation/using/interaction---data-buffer.md).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 인수<br /> </td> 
   <td> 시작 매개변수<br /> </td> 
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
   <td> 최대. 호출 데이터에 대해 공유 메모리에 저장된 문자 수입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스 시작 시 실행할 JavaScript의 ID<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 소모 경고: 지정된 프로세스에서 소비한 RAM의 양(MB)에 대한 경고입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 소모 경고: 주어진 프로세스에서 소비한 RAM의 양(MB)에 대한 경고.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntry<br /> </td> 
   <td> 최대. 공유 메모리에 저장된 이벤트 수입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> 통계에 저장하기 위해 제안 바로 뒤에 정렬되는 최대 적격 오퍼 수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 다음을 참조하십시오 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 재시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 처음 시작되고 마지막으로 중지됩니다. 따라서 syslogd 모듈의 우선 순위는 0이어야 합니다.<br /> </td> 
   <td> 짧음<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> 응답 시간 통계에 대한 집계 기간(초)입니다. 0은 통계 저장소가 비활성화되었음을 의미합니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 대상 키 크기<br /> </td> 
   <td> 최대. 개인 식별을 위해 공유 메모리에 저장된 문자 수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## MTA {#mta}

다음은 의 다양한 매개 변수입니다. **mta** 노드. 게재 에이전트 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 인수<br /> </td> 
   <td> 시작 매개변수<br /> </td> 
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
   <td> 데이터 로그 경로<br /> </td> 
   <td> 보낸 이메일 경로 저장: 비어 있지 않으면 보낸 이메일의 모든 소스 파일이 저장되는 경로입니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> 덤프 디렉터리:i비어 있지 않으면 이 디렉터리에 있는 보낸 메일 메시지의 MIME 봉투를 복사합니다. 문제 해결에 사용됩니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> DNS 쿼리 로그 지연: 로그를 표시하는 시간(밀리초).<br /> </td> 
   <td> 길게<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> 오류 통계 빈도: 통계 생성과 데이터베이스 저장 사이의 시간입니다. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스 시작 시 실행할 JavaScript의 ID.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailError<br /> </td> 
   <td> 오류 통계를 생성하고 데이터베이스에 저장합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> 로그 메시지 레벨 표시 데이터베이스에 기록된 로그의 심각도 수준입니다. MTA에서 생성된 로그 메시지가 항상 데이터베이스에 기록되는 것은 아닙니다. 이 매개 변수를 사용하면 데이터베이스에 메시지를 작성해야 하는 수준을 정의할 수 있습니다. 레벨 2를 정의하면 레벨 1과 0의 메시지도 작성되지만, 레벨 1을 정의하면 레벨 1과 0의 메시지만 작성됩니다. 가능한 값은 0(오류), 1(경고), 2(정보)입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> 최대 메모리(M)<br /> </td> 
   <td> MTA 프로세스가 사용할 수 있는 최대 메모리 크기(MB). 이 제한을 초과하면 사용하는 메모리가 시스템에 릴리스되도록 프로세스가 다시 시작됩니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 소모 경고: 지정된 프로세스에서 소비한 RAM의 양(MB)에 대한 경고입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 소모 경고: 주어진 프로세스에서 소비한 RAM의 양(MB)에 대한 경고.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> 고려해야 할 연결 임계값. errorPeriodSec에서 지정한 기간 동안 총 연결 수가 임계값보다 엄격히 낮은 경우 특정 경로에 대해 오류 통계가 생성되지 않습니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> 고려해야 할 오류 임계값: errorPeriodSec에서 지정한 기간 동안 총 오류 수가 임계값보다 엄격히 낮은 경우 특정 경로에 대해 오류 통계가 생성되지 않습니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessageToLog<br /> </td> 
   <td> 고려해야 할 메시지 임계값. errorPeriodSec에서 지정한 기간 동안 총 보낸 메시지 수가 임계값보다 엄격히 낮은 경우 특정 경로에 대해 오류 통계가 생성되지 않습니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 알림 릴레이: 알림을 릴레이하는 데 사용되는 HostName:Port.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 다음을 참조하십시오 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 재시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogdelay<br /> </td> 
   <td> 보관된 이메일을 삭제하기 전 지연: dataLogPath에 지정된 디렉터리에 보관된 이메일이 제거되기까지의 일수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessage<br /> </td> 
   <td> 손실된 메시지 다시 시도: 하위 프로세스가 중단되면 게재의 일부가 다시 시도됩니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 처음 시작되고 마지막으로 중지됩니다. 따라서 syslogd 모듈의 우선 순위는 0이어야 합니다.<br /> </td> 
   <td> 짧음<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLink<br /> </td> 
   <td> 서명 메커니즘을 활성화합니다. 이렇게 하면 이메일의 링크 추적에 대한 보안이 강화됩니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> 통계 서버 주소<br /> </td> 
   <td> 다음으로 지정된 게재 통계 서버 주소 
    &lt;dns or="" ip=""&gt; 
      <code>[</code>: 
     &lt;port&gt; 
       <code>]</code>. 다음을 참조하십시오 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">통계 서버의 좌표</a>. 
      <br /> 
     </td> 
   <td> 문자열<br /> </td> 
   <td> 정의되지 않은 경우 기본 포트는 7777입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSsupport<br /> </td> 
   <td> 도메인별 TLS 활성화: MX별로 구성할 수 있는 TLS를 활성화합니다(최신 통계 서버 필요).<br /> </td> 
   <td> 부울<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <!--tr> 
   <td> statServerVersion<br /> </td> 
   <td> Protocol version used: communication protocol version (1 for a v5.11 and 6.0.2 server, 2 for a v6.1 server).<br /> </td> 
   <td> String<br /> </td> 
   <td> If undefined, the latest version is used. <br /> </td> 
  </tr--> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> "true"로 설정하면 인스턴스가 <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">향상된 MTA</a>.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifymode<br /> </td> 
   <td> 확인 모드: 확인 모드를 활성화합니다(실제 메시지 전송 없음, 시뮬레이션 및 테스트에 사용).<br /> </td> 
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
   <td> xMailer<br /> </td> 
   <td> X-Mailer 필드: SMTP 메일 헤더의 'X-Mailer' 필드 값.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'nlserver, $(PRODUCT_VERSION) 빌드'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

다음에서 **캐시** 노드에서 다음 매개 변수를 구성합니다. 로컬 파일 캐시 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPeriodSec<br /> </td> 
   <td> 다음 시기 이후에 재활용: 스토리지 회수를 위해 파일이 캐시에서 자동으로 삭제되는 기간(초 단위로 표시됨).<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> 최대 캐시 크기(MB)<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> 삭제 기간 초<br /> </td> 
   <td> 제거 빈도: 캐시 제거 메커니즘 실행 사이의 기간(초).<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 릴레이 {#relay}

다음에서 **mta > 릴레이** 노드에서 다음 매개 변수를 구성합니다. 메시지 게재를 위한 메일 서버 구성입니다.

이 목록은 MX DNS 쿼리에서 반환된 MX 목록과 동일한 방식으로 처리됩니다. 일반적으로 첫 번째 MX는 사용 가능한 한 사용한 다음 MX가 사용됩니다.

자세한 내용은 다음을 참조하십시오. [SMTP 릴레이](../../installation/using/configuring-campaign-server.md#smtp-relay).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 주소<br /> </td> 
   <td> 사용할 SMTP 릴레이의 쉼표로 구분된 DNS 이름 또는 IP 주소 목록. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> SMTP 서버의 IP 포트.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 마스터 {#master}

다음에서 **mta > 마스터** 노드에서 다음 매개 변수를 구성합니다. 주 서버의 구성입니다.

자세한 내용은 다음을 참조하십시오. [섹션](../../installation/using/configuring-campaign-server.md#mta-child-processes).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 데이터 베이스 풀 기간<br /> </td> 
   <td> 게재할 작업의 데이터베이스 폴링 빈도. 해당 값은 데이터베이스 폴링 빈도(단위: 초)를 보여 줍니다. 게재 대기 중인 작업 목록을 얻으려면 MTA는 정기적으로 데이터베이스를 폴링합니다. 대기 중인 작업이 없는 경우 폴링 기간은 이 값에 따라 정의됩니다. 작업이 하위 서버로 전송되면 새 작업이 빠른 시일 내에 다시 처리될 수 있도록(예: 하위 서버를 다시 사용하는 대로) 이 폴링 기간은 자동으로 1초까지 줄어들게 됩니다. 즉, 하위 서버를 다시 사용할 때까지 데이터베이스 쿼리를 수행할 수 없습니다. 실제로, 하나 이상의 하위 서버를 사용하는 경우에만 데이터베이스에 액세스할 수 있습니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> 데이터베이스 연결 실패 이후 대기 기간. 데이터베이스 연결 실패는 일반적으로 데이터베이스 서버 자체에 의해 발생합니다. 예: 유지 관리 목적으로 서버가 중단될 수도 있음. DataBaseRetryDelay 매개변수는 데이터베이스 연결 실패 시 2회 연결 시도 기간을 정의합니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> 비공개 키(DomainKeys) 캐시의 유효 기간. DomainKeys 추천(http://antispam.yahoo.com/domainkeys)에 따라 이메일 서명에 사용되는 비공개 키는 데이터베이스에서 옵션으로 저장됩니다. domainKeysReloadPeriodSec 매개변수는 MTA가 캐시에 해당 키를 보관할 수 있는 시간(초)을 정의합니다. 이 지연 후에는 모든 키를 데이터베이스에서 다시 로드해야 합니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpare 서버<br /> </td> 
   <td> 최대 하위 서버 수. 실행 중인 최대 서버 수를 나타냅니다. 서버 메모리 리소스와 호환되는 이 수를 제한하는 것이 좋습니다. 게재 중에 이를 확인할 수 있습니다. 사용된 메모리는 사용 가능한 실제 메모리의 3분의 1을 초과할 수 없습니다. 그렇지 않을 경우 스왑이 사용됩니다. 다음을 참조하십시오 <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">MTA 하위 프로세스</a>.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpare 서버<br /> </td> 
   <td> 최소 하위 서버 수. MTA는 실행 중인 이 서버 수를 최소한 유지하려고 합니다. 수가 적은 경우 이 값에 도달할 때까지 매초마다 새 서버를 다시 시작합니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> 시작 시 하위 서버 수. 하위 서버의 수는 동적으로 모니터링됩니다. MTA가 시작되면 이 값이 표시하는 수만큼 하위 서버를 생성합니다. 일반적으로 하위 서버는 호스트 리소스를 저장하기 위해 초당 한 대의 서버보다 더 빠르게 시작할 수 없습니다. 하지만 MTA가 시작되면 최대한 빠른 시일 내에 하위 서버를 사용할 수 있도록 이 제한을 무효화합니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 하위 {#child}

다음에서 **mta > 하위** 노드에서 다음 매개 변수를 구성합니다. 하위 서버 구성입니다.

자세한 내용은 다음을 참조하십시오. [이메일 전송 최적화](../../installation/using/email-deliverability.md#email-sending-optimization).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> extraArgs<br /> </td> 
   <td> 명령줄 인수(선택 사항)<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> 유휴 하위 서버가 중지될 때까지 시간 제한. 하위 서버의 유휴 시간이 이 매개변수보다 클 경우 하위 서버는 자동 종료하여 호스트 리소스를 확보할 수 있습니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> 최대 메시지 보존 시간. 조절로 인해 준비된 메시지를 보낼 수 없거나 대상 MTA에 연결할 수 없는 경우 메시지가 중단되고 다음 재시도에서 처리될 수 있습니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> 각 하위 서버에서 시작된 FCM에 대한 최대 병렬 HTTP 요청.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> 하위 서버당 최대 메시지 수. 각 MTA 하위 항목은 이 메시지 수를 처리하고 삭제됩니다. MTA의 메모리 또는 리소스 누락이 해를 미치지 않도록(보통 수천 개 정도) 숫자를 지정해야 합니다. MTA 코드에 알려진 메모리 누락이 없더라도 임베드된 JavaScript 및 XSL 엔진을 완전히 신뢰할 수 없습니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> 보류 중인 메시지: 메모리에 대기 중인 전달할 최대 메시지 수. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> 하위 프로세스가 사용할 수 있는 최대 메모리 크기(MB). 이 제한을 초과하면 사용하는 메모리가 시스템에 릴리스되도록 프로세스가 중단됩니다. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> 시간 초과(단위: 초), 이후 게재 커넥터의 SOAP 연결이 중단됩니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMx<br /> </td> 
   <td> 항상 우선 순위가 가장 높은 MX로 시작.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> 재개 시 최대 연속 시도 수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

다음에서 **mta > 하위 > smtp** 노드에서 다음 매개 변수를 구성합니다. SMTP 세션의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enableTLS<br /> </td> 
   <td> 원격 서버에서 지원하는 경우 안전 모드(STARTTLS/SMTPS)에서 이메일 게재를 활성화합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> 유휴 세션 시간 제한<br /> </td> 
   <td> 유휴 세션 시간 제한 이 매개변수는 특정 도메인에 여러 메시지를 전송하는 데 세션을 재사용하는 경우에만 사용됩니다. MTA가 메시지 전송을 완료하면 사용된 SMTP 세션은 체계적으로 닫히지 않습니다. 이 동일한 도메인에 메시지를 보낼 준비가 되면 동일한 SMTP 세션이 재사용되므로 세션이 자동으로 닫히지 않습니다. 매개변수 IdleSessionTimeout 매개변수를 사용하면 SMTP 세션이 다른 메시지를 대기하며 활성 상태를 유지할 수 있는 시간을 정의할 수 있습니다. 기간이 경과하면 세션이 자동으로 닫힙니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> 초기 지연<br /> </td> 
   <td> 연결 재시도 이전의 초기 지연. 이 지연은 연결이 실패할 때마다 두 배가 됩니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> 하위 서버별 최대 SMTP 세션 수. 메시지 게재를 위해 MTA는 수신자 MTA로 SMTP 연결을 초기화합니다. 해당 값으로 특정 하위 서버의 최대 동시 및 활성 SMTP 세션 수를 제한합니다. maxSpareServers로 해당 값을 곱하면 특정 하위 서버에서 동시에 처리할 수 있는 최대 메시지 수를 얻습니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

다음에서 **mta > 하위 > smtp > IPAffinity** 노드에서 다음 매개 변수를 구성합니다. 발신 SMTP 트래픽 최적화를 위해 IP 주소로 선호도를 관리하는 구성입니다.

자세한 내용은 다음을 참조하십시오. [사용할 IP 주소 목록](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) 및 [관심도와 함께 아웃바운드 SMTP 트래픽 관리](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> 도메인 이름: IP 주소에 연결된 로컬 도메인 이름입니다. SMTP HELO 명령 발행 시 사용됩니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> 이름<br /> </td> 
   <td> 논리적 이름: 사용자가 선호도에 연결한 이름입니다. 이름은 세미콜론으로 구분됩니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

다음에서 **mta > 하위 > smtp > IP** 노드에서 다음 매개 변수를 구성합니다.

자세한 내용은 다음을 참조하십시오. [사용할 IP 주소 목록](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 주소<br /> </td> 
   <td> 연계된 실제 주소. 예: '192.168.0.1'<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> 연계된 공개 주소 ID. 통계 서버의 키로 사용됩니다. 숫자여야 합니다. 이 <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">섹션</a>을 참조하십시오.<br /> </td> 
   <td> 길게<br /> </td> 
  </tr> 
  <tr> 
   <td> 두께<br /> </td> 
   <td> 다른 IP와 비교해 이 IP의 사용 빈도를 지정합니다(가중치가 클수록 빈도가 높아짐).<br /> </td> 
   <td> 길게<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> 포함할 도메인 마스크를 쉼표로 구분한 목록.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> 제외할 도메인 마스크를 쉼표로 구분한 목록.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> IP 주소에 연결된 컴퓨터 이름. SMTP HELO 명령 발행 시 사용됩니다.<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

다음은 의 다양한 매개 변수입니다. **nmac** 노드. 푸시 알림 게재에 대한 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> useHTTPProxy<br /> </td> 
   <td> shared/proxyHTTP에 정의된 HTTP 프록시 사용. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 릴레이 {#relay-1}

다음은 의 다양한 매개 변수입니다. **nmac > 릴레이** 노드. 메시지 게재를 위한 릴레이(ios http2 커넥터) 사용을 구성합니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 주소<br /> </td> 
   <td> 사용할 릴레이의 DNS 주소 또는 이름. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> 릴레이 포트<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> 인증서 체인(PEM 파일). 모의 서버 사용 시 유용함.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 파이프라인됨 {#pipelined}

다음은 의 다양한 매개 변수입니다. **파이프라인됨** 노드. 파이프라인 서비스에 대한 이벤트 처리 모듈의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> appName<br /> </td> 
   <td> 공개 키 저장 시 개발자 연결에서 생성되는 애플리케이션 이름. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 인수<br /> </td> 
   <td> 시작 매개변수<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> 게이트웨이 토큰을 얻기 위한 URL.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> 토큰을 얻기 위한 비공개 키(XtkKey 옵션으로 AES에서 암호화).<br /> </td> 
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
   <td> 인증 비활성화: 인증 없이 파이프라인 서비스에 연결합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> 파이프라인 서비스 URL을 검색하는 URL.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> 덤프 상태 기간 초<br /> </td> 
   <td> 상태 저장 기간: 프로세스 내부 정보가 파일에 저장되는 빈도. 0이면 비활성화. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> 수신 URL: 파이프라인 서비스의 수신 URL을 강제 실행합니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스 시작 시 실행할 JavaScript의 ID.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 소모 경고: 지정된 프로세스에서 소비한 RAM의 양(MB)에 대한 경고입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 소모 경고: 주어진 프로세스에서 소비한 RAM의 양(MB)에 대한 경고.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> 모니터 서버 포트<br /> </td> 
   <td> 상태 서버 포트: 프로세스 상태를 쿼리할 수 있는 HTTP 서버 포트입니다. 0이면 비활성화.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> 포인터는 이 메시지 수가 처리될 때마다 데이터베이스에 저장됩니다.<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushPeriodSec<br /> </td> 
   <td> 포인터를 저장하기 전 지연: 이 기간 동안 포인터가 데이터베이스에 적어도 한 번 저장됩니다(활동이 적은 경우 유용함).<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 다음을 참조하십시오 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 재시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> 맞춤형 JavaScript 커넥터로 이벤트를 처리하는 데 필요한 스레드 수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> 처리 스레드<br /> </td> 
   <td> 이벤트 처리에 필요한 스레드 수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> 다시 시도 기간 초<br /> </td> 
   <td> 실패가 있는 경우 처리 사이에서 지연.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> 이 기간이 지난 후 중단: 이 기간이 지난 후에도 처리가 계속 실패하는 경우 이벤트를 중단합니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 처음 시작되고 마지막으로 중지됩니다. 따라서 syslogd 모듈의 우선 순위는 0이어야 합니다.<br /> </td> 
   <td> 짧음<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 복구 {#repair}

다음은 의 다양한 매개 변수입니다. **복구** 노드. 데이터베이스 복구 모듈의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 복구 작업 지연 시간<br /> </td> 
   <td> 게재 작업 복구 모듈: 지연(분). 이후 복구 모듈에서 게재 작업을 처리할 수 있습니다. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 보안 영역 {#securityzone}

다음은 의 다양한 매개 변수입니다. **보안 영역** 노드.

자세한 내용은 다음을 참조하십시오. [보안 영역 정의](../../installation/using/security-zones.md).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> allowDebug<br /> </td> 
   <td> 웹 애플리케이션의 디버그 모드 승인.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> 사용자가 암호 없이 애플리케이션을 사용할 수 있도록 승인.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> 연산자 로그인에 HTTP 사용 승인.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjection<br /> </td> 
   <td> 표현식에서 SQLDATA 사용 승인.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserpassword<br /> </td> 
   <td> 사용자/암호 세션 토큰 승인.<br /> </td> 
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
   <td> 이름<br /> </td> 
   <td> 내부 이름<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenonly<br /> </td> 
   <td> 보안 토큰 사용 안 함.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showError<br /> </td> 
   <td> 오류 세부 정보 표시<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

기본 구성은 다음과 같습니다.

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

### 하위 네트워크 {#subnetwork}

다음은 의 다양한 매개 변수입니다. **securityZone > 하위 네트워크** 노드.

자세한 내용은 다음을 참조하십시오. [보안 영역 정의](../../installation/using/security-zones.md).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
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
   <td> 이름<br /> </td> 
   <td> 내부 이름<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> 프록시<br /> </td> 
   <td> 인스턴스에 액세스할 수 있는 이 하위 네트워크에서 사용하는 (역방향) 프록시의 마스크 또는 주소. 이 경우 이 프록시 대신 'X-Forwarded-For' 헤더를 테스트합니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

다음은 의 다양한 매개 변수입니다. **sms** 노드. 인바운드 SMS 관리 모듈의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 인수<br /> </td> 
   <td> 시작 매개변수<br /> </td> 
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
   <td> SMPP 커넥터가 보관하는 파일을 작업 중인 파일의 최대 일수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> 데이터 크기<br /> </td> 
   <td> SMPP 작업 파일의 최대 크기(MB).<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스 시작 시 실행할 JavaScript의 ID.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> 세션 연속성 프레임 반복: 최대 수신 세션이 여전히 활성화되어 있음을 알리는 두 프레임 사이의 기간(초)입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 소모 경고: 지정된 프로세스에서 소비한 RAM의 양(MB)에 대한 경고입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 소모 경고: 주어진 프로세스에서 소비한 RAM의 양(MB)에 대한 경고.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> 검색 빈도: SMS 계정 폴 기간.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 다음을 참조하십시오 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 재시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> 계정 재로드 빈도: 폴링할 계정의 데이터베이스 재로드 빈도.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 처음 시작되고 마지막으로 중지됩니다. 따라서 syslogd 모듈의 우선 순위는 0이어야 합니다.<br /> </td> 
   <td> 짧음<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> SR 처리 지연 시간(초): 현재 시간에서 srReadDelay에 지정된 기간(초)을 뺀 일정보다 빠른 복구 날짜가 있는 SR만 해당됩니다. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 시간 제한<br /> </td> 
   <td> SMS 게이트웨이와의 통신 시간 제한.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

다음은 의 다양한 매개 변수입니다. **sms > netsize** 노드.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> netsizeConnectionTimeout<br /> </td> 
   <td> Netsize로 연결 설정 시 시간 제한(초).<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 통계 {#stat}

다음은 의 다양한 매개 변수입니다. **통계** 노드. MTA 통계 모듈의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 인수<br /> </td> 
   <td> 시작 매개변수<br /> </td> 
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
   <td> 프로세스 시작 시 실행할 JavaScript의 ID.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 소모 경고: 지정된 프로세스에서 소비한 RAM의 양(MB)에 대한 경고입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 소모 경고: 주어진 프로세스에서 소비한 RAM의 양(MB)에 대한 경고.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> 서버 수신 포트. 이 <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">섹션</a>을 참조하십시오.<br /> </td> 
   <td> 짧음<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 다음을 참조하십시오 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 재시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 처음 시작되고 마지막으로 중지됩니다. 따라서 syslogd 모듈의 우선 순위는 0이어야 합니다.<br /> </td> 
   <td> 짧음<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

다음은 의 다양한 매개 변수입니다. **syslogd** 노드. 로그 관리 모듈의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 인수<br /> </td> 
   <td> 시작 매개변수<br /> </td> 
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
   <td> 프로세스 시작 시 실행할 JavaScript의 ID.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> 로그 파일의 최대 크기(MB)입니다. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> 최대 로그인 수 파일<br /> </td> 
   <td> 유지할 최대 logins.log 파일 수. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 소모 경고: 지정된 프로세스에서 소비한 RAM의 양(MB)에 대한 경고입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 소모 경고: 주어진 프로세스에서 소비한 RAM의 양(MB)에 대한 경고.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 다음을 참조하십시오 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 재시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 처음 시작되고 마지막으로 중지됩니다. 따라서 syslogd 모듈의 우선 순위는 0이어야 합니다.<br /> </td> 
   <td> 짧음<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 추적 {#tracking}

다음은 의 다양한 매개 변수입니다. **추적** 노드. 이는 추적 서버의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 인수<br /> </td> 
   <td> 시작 매개변수<br /> </td> 
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
   <td> 이전 빌드에서 생성된 형식이 잘못된 URL을 비활성화합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> consolidationPeriodSec<br /> </td> 
   <td> 통합 기간<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> 열기 중복 제거: 중복 열기 추적 로그를 제거하여 Outlook과 같은 메일 리더에서 메일 미리 보기의 효과를 제한합니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> 오류 무시 퍼센트<br /> </td> 
   <td> 최대 오류 X% 무시: 아직 고려되지 않은 분개의 비율이 이 값에 도달하지 않는 한 추적 지표를 업데이트하지 마십시오. <br /> </td> 
   <td> 바이트<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> 오류 지표 업데이트: 오류 지표가 다시 계산되기 전 최대 기간.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorsDuration<br /> </td> 
   <td> 다음 기간 동안 지표 계산: 게재 유효일자 이후 통합 지표가 더 이상 계산되지 않는 기간.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스 시작 시 실행할 JavaScript의 ID <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> 원격 추적 서버 호출에 의해 요청된 로그 수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 소모 경고: 지정된 프로세스에서 소비한 RAM의 양(MB)에 대한 경고입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 소모 경고: 주어진 프로세스에서 소비한 RAM의 양(MB)에 대한 경고.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> Phishbowl 서비스 엔드포인트 통합에 대한 API 키입니다. 이렇게 하면 이전 빌드에서 생성된 잘못된 URL의 리디렉션을 보호합니다. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Phishbowl 서비스 엔드포인트 통합에 대한 엔드포인트입니다. 이렇게 하면 이전 빌드에서 생성된 잘못된 URL의 리디렉션을 보호합니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 다음을 참조하십시오 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 재시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 처음 시작되고 마지막으로 중지됩니다. 따라서 syslogd 모듈의 우선 순위는 0이어야 합니다.<br /> </td> 
   <td> 짧음<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> 최대 추적 X% 무시: 아직 고려되지 않은 분개의 비율이 이 값에 도달하지 않는 한 추적 지표를 업데이트하지 마십시오.<br /> </td> 
   <td> 바이트<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> 추적 지표 업데이트: 추적 지표가 다시 계산되기 전의 최대 기간.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> 사용자 에이전트 캐시 크기<br /> </td> 
   <td> 브라우저 식별자 캐시의 크기입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

다음은 의 다양한 매개 변수입니다. **trackinglogd** 노드. 추적 로그 기록 데몬의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 인수<br /> </td> 
   <td> 시작 매개변수<br /> </td> 
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
   <td> 프로세스 시작 시 실행할 JavaScript의 ID <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> 최대 쓰기 재시도 수: 로그 파일에 쓰기 실패가 발생한 경우 만들 수 있는 최대 파일 수입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> 최대 로그 크기: 디스크의 로그에서 사용되는 최대 공간(MB). 100MB 이상일 수 있습니다. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 소모 경고: 지정된 프로세스에서 소비한 RAM의 양(MB)에 대한 경고입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 소모 경고: 주어진 프로세스에서 소비한 RAM의 양(MB)에 대한 경고.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> 최대 로그 수: 공유 메모리에 저장된 최대 로그 수입니다. 10000보다 작을 수 없습니다. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 다음을 참조하십시오 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 재시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> 제거 전 로그 수: 로그 파일 제거를 시작하기 전에 삽입된 로그 수입니다. 50000보다 작을 수 없습니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 처음 시작되고 마지막으로 중지됩니다. 따라서 syslogd 모듈의 우선 순위는 0이어야 합니다.<br /> </td> 
   <td> 짧음<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamsize<br /> </td> 
   <td> 추가 웹 추적 매개변수를 위해 공유 메모리에 저장되는 최대 문자 수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 웹 {#web}

다음은 의 다양한 매개 변수입니다. **웹** 노드. 웹 모듈의 구성입니다.

자세한 내용은 다음을 참조하십시오. [섹션](configuring-campaign-server.md#default-port-for-tomcat).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
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
   <td> 최대 스레드 수<br /> </td> 
   <td> 최대 스레드 수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> 최소 스페어 스레드<br /> </td> 
   <td> 최소 스레드 수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> 인수<br /> </td> 
   <td> 시작 매개변수<br /> </td> 
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
   <td> Tomcat 수신 제어 포트: 을 참조하십시오. <a href="configure-tomcat.md" target="_blank">Tomcat 구성</a>.<br /> </td> 
   <td> 짧음<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP 수신 포트: 다음을 참조하십시오. <a href="configure-tomcat.md" target="_blank">Tomcat 구성</a>.<br /> </td> 
   <td> 짧음<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스 시작 시 실행할 JavaScript의 ID.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> SubmitDelivery 호출에 대한 대기열 크기: 대기열에 추가할 수 있는 최대 SubmitDelivery SOAP 호출 수.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 소모 경고: 지정된 프로세스에서 소비한 RAM의 양(MB)에 대한 경고입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 소모 경고: 주어진 프로세스에서 소비한 RAM의 양(MB)에 대한 경고<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 알림 릴레이: 알림의 릴레이를 활성화하는 HostName:Port.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 다음을 참조하십시오 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 재시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 처음 시작되고 마지막으로 중지됩니다. 따라서 syslogd 모듈의 우선 순위는 0이어야 합니다.<br /> </td> 
   <td> 짧음<br /> </td> 
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

다음은 의 다양한 매개 변수입니다. **웹 > jsp** 노드. JSP에서 사용하는 매개변수의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 디버그<br /> </td> 
   <td> 디버그 모드에서 JSP 실행 여부.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> 다운로드 폴더: 클라이언트 콘솔용 설치 프로그램의 다운로드 경로.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp'<br /> </td> 
  </tr> 
  <tr> 
   <td> fo파일 이름<br /> </td> 
   <td> .fo 파일 경로.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soap라우터<br /> </td> 
   <td> SOAP 라우터의 URL(http://myserver/xxx, http://jni 또는 mailto:xxx).<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

다음 **웹 > jsp > 클래스 경로** 노드에는 JVM을 시작할 때 사용할 모든 클래스 경로 목록이 포함되어 있습니다. 기본 구성은 다음과 같습니다.

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

다음은 의 다양한 매개 변수입니다. **웹 > jssp** 노드. JSSP에서 사용하는 매개 변수의 구성입니다.

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> collectsGarbageAfterRequest<br /> </td> 
   <td> 각 쿼리 후에 JavaScript 컨텍스트의 가비지 수집기를 활성화합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> JavaScript 컨텍스트에서 제공하는 최대 페이지 수. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

다음 **웹 > jsp > 클래스 경로** 노드에는 JVM을 시작할 때 사용할 모든 클래스 경로 목록이 포함되어 있습니다.

### 릴레이 {#relay-2}

다음은 의 다양한 매개 변수입니다. **웹 > 릴레이** 노드. 두 영역 간의 HTTP 요청에 대한 릴레이의 구성입니다.

자세한 내용은 다음을 참조하십시오. [섹션](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debugRelay<br /> </td> 
   <td> 디버그 모드의 웹 서버 내에서 HTTP 릴레이 모듈을 시작합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> 금지된 문자(도메인): URI의 '기관' 섹션에서 금지된 문자 목록입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> 금지된 문자(경로): URI의 '경로' 섹션에서 금지된 문자 목록입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> 'mod_dir' 모듈 옵션의 값: 폴더에서 쿼리 시 사용할 파일 목록입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> HTTP 릴레이 모듈 시작.<br /> </td> 
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
   <td> 시간 제한<br /> </td> 
   <td> 금지 URL 삭제 전 대기 시간.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

추가 **웹 > 릴레이 > url** 릴레이할 각 URL의 노드(삽입 순서는 우선순위를 정의함).

자세한 내용은 다음을 참조하십시오. [다이내믹 페이지 보안 및 릴레이](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) 및 [섹션](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IPMask<br /> </td> 
   <td> 승인된 IP: 이 마스크에 대해 릴레이를 사용할 수 있도록 허용된 소스 IP 주소를 쉼표로 구분한 목록입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 거부<br /> </td> 
   <td> 이 URL에 대한 액세스 거부(HTTP 403 오류 반환)<br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> 릴레이할 DNS 앨리어스: 릴레이할 DNS 앨리어스 마스크를 쉼표로 구분한 목록(예: '*.adobe.com').<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllow<br /> </td> 
   <td> 보안 영역(예: webApps)에 관계없이 인증된 HTTP 액세스. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 릴레이 호스트<br /> </td> 
   <td> 원래 호스트 추가: 릴레이할 때 원래 요청의 HTTP '호스트' 헤더를 사용합니다.<br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 릴레이 경로<br /> </td> 
   <td> 초기 URL 경로 추가: 대상 페이지의 URL로 릴레이할 URL의 전체 경로를 추가합니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 상태<br /> </td> 
   <td> 공개 리소스의 동기화 상태(열거)입니다. 가능한 값은 '일반'(일반 실행), '블랙리스트'(오류 404의 경우 url이 차단 목록에 추가하다에 추가됨) 및 '예비'(존재하는 경우 예비 서버에 파일 업로드)입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 표준<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> 대상 페이지의 URL: 참조 <a href="configure-tomcat.md" target="_blank">Tomcat 구성</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 시간 제한<br /> </td> 
   <td> 릴레이 중인 요청의 최대 실행 시간(초)입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> 릴레이할 URL 마스크(예: '/nl*', '*.jsp').<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

기본 구성은 다음과 같습니다.

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

추가 **웹 > 릴레이 > responseHeader** 릴레이로 전달되는 응답에 추가할 각 HTTP 헤더에 대한 노드.

자세한 내용은 다음을 참조하십시오. [HTTP 헤더 관리](../../installation/using/configuring-campaign-server.md#managing-http-headers).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
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

기본 구성은 다음과 같습니다.

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### 리디렉션 {#redirection}

다음은 의 다양한 매개 변수입니다. **웹 > 리디렉션** 노드. 리디렉션 모듈의 구성입니다.

자세한 내용은 다음을 참조하십시오. [섹션](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IMSOrgId<br /> </td> 
   <td> 조직 ID: 특히 VisitorID 서비스 및 IMS SSO에 사용되는 Adobe Experience Cloud 내의 고유 조직 식별자입니다. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> 영구 쿠키에 사용되는 정책을 설명하는 값(P3P 압축 정책 형식 준수). <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> 'CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV'<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> 쿠키를 설정할 도메인을 명시적으로 표시하기 위해 구성할 도메인을 쉼표로 구분한 목록. <br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> 추적 인스턴스와 연결된 데이터베이스 식별자.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> 호출별 로그 수: GetTrackingLogs 메서드 호출 시 기본적으로 반환되는 로그 수입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> 만료 URL<br /> </td> 
   <td> 만료된 리디렉션용 페이지: 게재 작업의 리디렉션이 만료된 경우 리디렉션 서버에서 기본적으로 사용하는 웹 페이지의 URL입니다.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> 최대 작업 수: 캐시의 최대 게재 작업 수. 50보다 작을 수 없습니다. <br /> </td> 
   <td> 길게<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> showSourceIP<br /> </td> 
   <td> false로 설정된 경우 r/test에서 반환된 응답의 sourceIP 값은 빈 문자열입니다. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> true<br /> </td> 
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
   <td> trackWebVisitor<br /> </td> 
   <td> 웹 추적: 알 수 없는 사용자가 방문한 페이지에 대한 로그 생성. <br /> </td> 
   <td> 부울<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> 리디렉션 서버에서 사용하는 암호.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

다음은 의 다양한 매개 변수입니다. **웹 > 리디렉션 > 스페어 서버** 노드.

자세한 내용은 다음을 참조하십시오. [중복 추적](../../installation/using/configuring-campaign-server.md#redundant-tracking).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabledIf<br /> </td> 
   <td> 가정: 표현식이 true를 반환하는 경우 추적 서버를 고려합니다. <br /> </td> 
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
   <td> URL<br /> </td> 
   <td> 추가 리디렉션 서버 URL<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### 스팸 확인 {#spamcheck}

다음은 의 다양한 매개 변수입니다. **웹 > spamCheck** 노드. 이메일 스팸 방지 점수 평가 매개 변수를 구성하는 것입니다.

자세한 내용은 다음을 참조하십시오. [SpamAssassin 구성](../../installation/using/configuring-spamassassin.md).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 명령<br /> </td> 
   <td> 이메일의 스팸 방지 점수를 평가하기 위해 실행할 명령(예: 'perl spamcheck.pl').<br /> </td> 
   <td> 문자열<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

다음은 의 다양한 매개 변수입니다. **wfserver** 노드. 워크플로우 프로세스 구성입니다.

자세한 내용은 다음을 참조하십시오. [고가용성 워크플로 및 관심도](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

<table> 
 <thead> 
  <tr> 
   <th> 매개변수 </th> 
   <th> 설명 </th> 
   <th> 유형 </th> 
   <th> 기본 값 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 선호도<br /> </td> 
   <td> 선호도<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 인수<br /> </td> 
   <td> 시작 매개변수<br /> </td> 
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
   <td> 데이터 베이스 풀 기간<br /> </td> 
   <td> 기간<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 프로세스 시작 시 실행할 JavaScript의 ID.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 메모리 소모 경고: 지정된 프로세스에서 소비한 RAM의 양(MB)에 대한 경고입니다.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 메모리 소모 경고: 주어진 프로세스에서 소비한 RAM의 양(MB)에 대한 경고.<br /> </td> 
   <td> 길게<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 알림 릴레이: 알림의 릴레이를 활성화하는 HostName:Port.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 프로세스가 자동으로 다시 시작되는 시간. 다음을 참조하십시오 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">자동 프로세스 재시작</a>.<br /> </td> 
   <td> 문자열<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 시작 시 우선 순위. 우선 순위가 낮은 모듈이 처음 시작되고 마지막으로 중지됩니다. 따라서 syslogd 모듈의 우선 순위는 0이어야 합니다.<br /> </td> 
   <td> 짧음<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
