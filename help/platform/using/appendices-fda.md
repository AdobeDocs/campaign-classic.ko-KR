---
title: 부록
seo-title: FDA 부록
description: FDA 부록
seo-description: null
page-status-flag: never-activated
uuid: 2596fabc-679a-45c8-a62a-165c221654b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: a84a73a9-9930-449f-8b81-007a0e9d5233
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7cf3b189f328cd1ea6ca8b67a3fc4c0c0bddd84
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 0%

---


# 부록 {#fda-appendices}

## 추가 구성 메타데이터 {#teradata-configuration}

### 호환성 {#teradata-compatibility}

**유니코드 기반**

| 데이터베이스 버전 | 드라이버 버전 | 최소 캠페인 버전 필요 | 참고 |
|:-:|:-:|:-:|:-:|
| 15 | 15 | Campaign Classic 17.9 | Linux에서 다음을 수행합니다. 타임스탬프가 있는 쿼리가 실패할 수 있습니다(빌드 8937에서 18.4 및 8977에서 해결됨). 디버그 모드에서 드라이버의 잘못된 메모리 사용과 관련된 경고가 발생할 수 있습니다. |
| 15 | 16 | Campaign Classic 17.9 | Linux에서 Teradata 15 데이터베이스를 설정하는 것이 좋습니다. |
| 16 | 16 | Campaign Classic 18.10 | 대용 쌍을 가진 유니코드 문자는 완전히 처리되지 않습니다. 데이터에 대리 문자를 사용하는 것이 효과적입니다. 이 변경 사항이 없으면 쿼리의 필터링 조건에 서루게이트를 사용하면 작동하지 않습니다. |
| 16 | 15 | 지원되지 않음 |   |

**Based in Latin1**

Library Classic 17.9의 이전 버전에는 Teradata Latin-1 데이터베이스만 지원됩니다.

이제 Adobe Campaign Classic 17.9부터 유니코드의 기본 Teradata 데이터베이스를 지원합니다.

최신 Campaign Classic 릴리스로 마이그레이션하는 Latin-1 Teradata 데이터베이스를 사용하는 고객은 외부 계정의 옵션에 APICharSize=1 매개 변수를 추가해야 합니다.

### 데이터베이스 구성 {#database-configuration}

#### 사용자 구성 {#user-configuration}

다음 권한이 필요합니다. 사용자 지정 절차 만들기/삭제/삽입/선택 Adobe Campaign 인스턴스에서 md5 및 sha2 함수를 사용하려면 사용자 모드 기능을 만들어야 할 수도 있습니다.

올바른 시간대를 구성해야 합니다. Adobe Campaign 인스턴스에서 만들 외부 계정에 설정할 내용과 일치해야 합니다.

Adobe Campaign은 데이터베이스에 만들 개체에 보호 모드(폴백)를 설정하지 않습니다. 다음 쿼리를 사용하여 Teradata 데이터베이스에 연결하는 데 사용할 Adobe Campaign의 기본값을 설정해야 할 수 있습니다.

| 기본 폴백 비활성화 |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

#### MD5 설치 {#md5-installation}

Adobe Campaign 인스턴스에서 md5 함수를 사용하려면 이 [페이지](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip)에서 Teradata 데이터베이스에 사용자 모드 기능을 설치해야 합니다.

다운로드한 파일의 sha1은 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e와 같습니다.

md5를 설치하려면:

1. md5_20080530.zip 파일의 압축을 해제합니다.

1. md5/src 디렉토리로 이동합니다.

1. bteq를 사용하여 Teradata 데이터베이스에 연결합니다.

1. 다음 bteq 명령을 실행합니다.

   ```
   .run file = hash_md5.btq
   ```

#### SHA2 설치 {#sha2-installation}

Adobe Campaign 인스턴스에서 sha2 함수를 사용하려면 이 [페이지](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip)에서 Teradata 데이터베이스에 사용자 모드 함수를 설치해야 합니다.

다운로드한 파일의 sha1은 다음과 같습니다. e87438d37424836358bd3902cf1adeb629349780.

sha2를 설치하려면:

1. teradata-udf-sha2-1.0.zip 파일의 압축을 해제합니다.

1. teradata-udf-sha2-1.0/src 디렉토리로 이동합니다.

1. bteq를 사용하여 Teradata 데이터베이스에 연결합니다.

1. 다음 두 가지 bteq 명령을 실행합니다.

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

#### UDF_UTF16TO8 설치 {#UDF-UTF16TO8-installation}

Adobe Campaign 인스턴스에서 udf_utf16to8 함수를 사용하려면 이 **페이지의** Teradata 도구 키트 [](https://downloads.teradata.com/download/tools/unicode-tool-kit) (utk_release1.7.0.0.zip)에서 Teradata 데이터베이스에 사용자 모드 기능을 설치해야 합니다.

다운로드한 파일의 sha1은 e58235f434f52c71316a577cb48e20b97d24f470과 같습니다.

udf_utf16to8을 설치하려면:

1. utk_release1.7.0.0.zip 파일의 압축을 해제합니다.

1. 추출한 파일에서 udf_utf16to8.o를 찾고 파일이 포함된 디렉토리로 이동합니다. 이름은 utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/.

1. bteq를 사용하여 Teradata 데이터베이스에 연결합니다.

1. 다음 bteq 명령을 입력합니다.

   ```
   REPLACE FUNCTION udf_utf16to8 (
   inputString VARCHAR(8000) CHARACTER SET UNICODE
   ) RETURNS VARCHAR(16000) CHARACTER SET LATIN
   LANGUAGE C
   NO SQL
   EXTERNAL NAME 'CO!i18n103!udf_utf16to8.o!F!udf_utf16to8'
   PARAMETER STYLE SQL;
   
   -- Test: should return 410042
   SELECT CAST(Char2HexInt(UDF_UTF16to8(_UNICODE'004100000042'XC)) AS VARCHAR(100));
   ```

### Linux용 캠페인 서버 구성 {#campaign-server-linux}

드라이버 설치 시 다음이 필요합니다.

* 이 [페이지에서 찾을 수 있는 Teradata ODBC 드라이버](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* 이 [페이지에서 찾을 수 있는 메타데이터 도구 및 유틸리티(벌크 로드에 사용)](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

파일 이름 및 sha1:

* tdobc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b847f44fd

* TeradataToolsAndUtilitiesBase__linux_indp.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

Linux 배포를 위한 패키지가 없는 경우 CentOS 7에 설명된 대로(예: docker 사용) 설치한 다음 Adobe Campaign 서버에 /opt/teradata의 내용을 복사할 수 있습니다.

#### ODBC 드라이버 설치 {#odbc-installation}

ODBC 드라이버를 설치하려면:

1. tdobc1620__linux_indpp.16.20.00.00-1.tar.gz 파일을 추출합니다.

1. tdobc1620 디렉토리로 이동합니다.

1. 설치 스크립트를 수정해야 할 수 있습니다.

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. setup_wrapper.sh를 실행합니다.

#### 메타데이터 도구 및 유틸리티 설치 {#teradata-tools-installation}

도구를 설치하려면:

1. TeradataToolsAndUtilitiesBase__linux_indpp.16.20.01.00.tar.gz 파일을 추출합니다.

1. TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu 디렉토리로 이동합니다.

1. setup_wrapper.sh를 실행합니다.

1. TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2 디렉토리로 이동합니다.

1. setup_wrapper.sh를 실행합니다.

1. TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase 디렉토리로 이동합니다.

1. setup_wrapper.sh를 실행합니다.

1. libtelapi.so 파일은 /opt/teradata/client/16.20/lib64에서 사용할 수 있어야 합니다.

#### 드라이버 구성 {#driver-configuration}

드라이버 구성에 대한 자세한 내용은 이 [섹션을 참조하십시오](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

#### 환경 변수 {#environment-varaiables}

Adobe Campaign 서버의 환경 변수에 대한 자세한 내용은 이 [섹션을 참조하십시오](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

### Windows #campaign-server-windows}용 캠페인 서버 구성

먼저 Windows용 메타데이터 도구 및 유틸리티를 다운로드해야 합니다. 이 [페이지에서 다운로드할 수 있습니다](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

ODBC 드라이버와 Teradata Parallel Transporter Base를 설치해야 합니다. Teradata 데이터베이스에서 벌크 로드를 수행하는 데 사용되는 telapi.dll을 설치합니다.

드라이버와 유틸리티의 경로가 실행 중에 서버가 보유할 PATH 변수에 있는지 확인합니다. 기본적으로 경로는 C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Program Files\Teradata\Client\15.10\bin on 64 bit입니다.

### 외부 계정 문제 해결 {#external-account-troubleshooting}

연결 **TIM-03008 날짜 &#39;2&#39;를 테스트하는 동안 다음 오류가 표시되는 경우: 누락된 문자(iRc=-53)** (ODBC 드라이버가 올바르게 설치되어 있고 캠페인 서버에 대해 LD_LIBRARY_PATH(Linux)/PATH(Windows)가 설정되어 있는지 확인하십시오.

오류 **ODB-240000 ODBC 오류:[Microsoft][ODBC Driver Manager]데이터 원본 이름을 찾을 수 없으며 기본 드라이버가 지정되지 않았습니다.** 16.X 드라이버를 사용하는 경우 Windows에서 발생합니다. Adobe Campaign은 odbcinst.ini에서 &#39;{teradata}&#39;라는 메타데이터를 예상합니다.
18.10 Adobe Campaign 서버 버전이 있는 경우 외부 계정의 옵션에 ODBCDriverName=&quot;Teradata Database ODBC Driver 16.10&quot;을 추가할 수 있습니다. 버전 번호는 변경될 수 있으며 정확한 이름은 obcad32.exe를 실행하고 드라이버 탭에 액세스하여 찾을 수 있습니다.
18.10 이하 버전의 경우 드라이버 설치로 만든 odbcinst.ini의 Teradata 섹션을 Teradata, regedit을 사용할 수 있습니다.

베이스가 latin1인 경우 옵션에서 APICharSize=1을 추가해야 합니다.

### 시간대 {#timezone}

Teradata는 표준이 아닌 시간대 이름을 사용하므로 Teradata [사이트에서 목록을 찾을 수 있습니다](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA). Adobe Campaign은 외부 구성에 지정된 시간대를 Teradata가 이해하는 시간대로 변환하려고 합니다. 통신문을 찾을 수 없는 경우, 옷장 GMT+X(또는 GMT-X) 시간대가 세션에 검색되고 로그에 경고가 표시됩니다.

변환은 다음 데이터 디렉터리에 있어야 하는 teradata_timezones.txt 파일을 읽습니다. linux의 /usr/local/neolane/nl6/datakit 이 파일을 편집하는 경우 소스 코드를 변경하려면 Adobe Campaign 팀에 문의하십시오. 그렇지 않으면 다음 캠페인 업데이트 동안 이 파일을 덮어쓰게 됩니다.

-verbose 스위치로 nlserver를 실행할 때 연결하는 데 사용되는 표준 시간대가 표시됩니다. 예:

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

사용된 시간대가 올바르지 않으면 외부 계정에 &quot;TimeZoneName&quot;이라는 옵션을 추가할 수 있습니다. 이 경우 &quot;TimeZoneName=Europe Central&quot;과 같은 메타데이터 값을 사용합니다.

벌크 로드를 사용하거나 Teradata 문서에서 &quot;빠른 로드&quot;를 사용할 때 Campaign은 표준 시간대를 표시할 수 없습니다. 따라서 Campaign에서 연결하는 데 사용할 사용자의 기본 시간대를 설정하는 것이 좋습니다.

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```

## MySQL 5.7 구성 {#mysql-57-configuration}

### 서버 구성 {#server-configuration-mysql}

서버 구성에는 특정 설치 단계가 필요하지 않습니다. Adobe Campaign은 latin1 데이터베이스, MySQL의 기본값 또는 유니코드 데이터베이스에서 작동해야 합니다.

### 드라이버 설치 {#driver-installation-mysql}

#### 데비안 {#debian-mysql}

이 [페이지에서 mysql-apt-config.deb를 다운로드합니다](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en).

클라이언트 라이브러리 설치:

```
$ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
$ apt update
$ apt install libmysqlclient20
```

#### Windows {#windows-mysql}

이 [페이지에서 C 커넥터를 다운로드합니다](https://dev.mysql.com/downloads/connector/c). 버전 5.7을 다운로드하는 것이 좋습니다.

libmyqlclient.dll이 들어 있는 디렉토리가 nlserver에서 사용할 PATH 환경 변수에 추가되어 있는지 확인합니다.

#### CentOS {#centos-mysql}

이 [페이지에서 mysql57-community-release.noarch.rpm을 다운로드합니다](https://dev.mysql.com/downloads/repo/yum).

클라이언트 라이브러리 설치:

$ yum install mysql57-community-release-el7-9.noarch.rpm$ yum install mysql-community-libs

### 외부 계정 구성 {#external-account-mysql}

외부 계정 구성에는 특정 단계가 필요하지 않습니다. 표준 시간대 및 유니코드 데이터가 데이터베이스에 따라 설정되어 있는지 확인합니다.
