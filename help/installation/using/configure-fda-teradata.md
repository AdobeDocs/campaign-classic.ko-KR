---
solution: Campaign Classic
product: campaign
title: teradata 액세스 구성
description: FDA에서 Teradata 이용 권한 구성 방법 살펴보기
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1613'
ht-degree: 0%

---


# teradata 액세스 구성 {#configure-access-to-teradata}

FDA(Campaign [Federated Data Access](../../installation/using/about-fda.md) ) 옵션을 사용하여 외부 데이터베이스에 저장된 정보를 처리할 수 있습니다. 아래 절차에 따라 Teradata에 대한 액세스를 구성합니다.

1. [Teradata 드라이버 설치 및 구성](#teradata-config)
1. Campaign에서 Teradata [외부 계정](#teradata-external) 구성
1. teradata 및 캠페인 서버에 [대한 추가 구성](#teradata-additional-configurations) 설정

## Teradata 구성 {#teradata-config}

Campaign에 대한 연결을 구현하려면 Teradata의 드라이버를 설치해야 합니다.

1. teradata용 [ODBC 드라이버를 설치합니다](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   Red Hat(또는 CentOS)/Suse에 다음 순서로 설치할 수 있는 세 개의 패키지로 구성됩니다.

   * TeraGSS
   * tdicu1510(setup_wrapper.sh를 사용하여 설치)
   * tdobc1510(setup_wrapper.sh를 사용하여 설치)

1. ODBC 드라이버를 구성합니다. 구성은 표준 파일에서 수행할 수 있습니다. **/etc/odbc.ini** for general parameters and /etc/odbcinst.ini for decoring driver:

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot;은 **odbcinst.ini** 파일의 위치에 해당합니다.

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      teradata=Installed
      
      [teradata]
      Driver=/opt/teradata/client/15.10/lib64/tdata.so
      APILevel=CORE
      ConnectFunctions=YYY
      DriverODBCVer=3.51
      SQLLevel=1
      ```

1. Adobe Campaign 서버의 환경 변수를 지정합니다.

   * **LD_LIBRARY_PATH**:/opt/teradata/client/15.10/lib64와 /opt/teradata/client/15.10/odbc_64/lib.
   * **ODBCINI**:odbc.ini 파일의 위치입니다(예: /etc/odbc.ini).
   * **NLSPATH**:opermsgs.cat 파일의 위치(/opt/teradata/client/15.10/msg/opermsgs.cat)

>[!NOTE]
>
>FDA에서 Teradata 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에서 추가 구성 단계를 수행해야 합니다. [자세히 알아보기](#teradata-additional-configurations)


## Teradata 외부 계정{#teradata-external}

teradata 외부 계정을 사용하면 캠페인 인스턴스를 Teradata 외부 데이터베이스에 연결할 수 있습니다.

1. 캠페인 **[!UICONTROL Explorer]**&#x200B;에서 **[!UICONTROL Administration]** / **[!UICONTROL Platform]** /를 **[!UICONTROL External accounts]**&#x200B;클릭합니다.

1. 을 **[!UICONTROL New]** 클릭하고 **[!UICONTROL External database]** 으로 선택합니다 **[!UICONTROL Type]**.

   ![](assets/ext_account_19.png)

1. 외부 계정을 구성하려면 다음을 **[!UICONTROL Teradata]** 지정해야 합니다.

   * **[!UICONTROL Type]**:유형을 **[!UICONTROL Teradata]** 선택합니다.

   * **[!UICONTROL Server]**:teradata 서버의 URL 또는 이름

   * **[!UICONTROL Account]**:teradata 데이터베이스에 액세스하는 데 사용되는 계정 이름

   * **[!UICONTROL Password]**:teradata 데이터베이스에 연결하는 데 사용되는 암호

   * **[!UICONTROL Database]**:데이터베이스 이름(선택 사항)

   * **[!UICONTROL Options]**:teradata을 통해 제공되는 옵션 다음 형식을 사용하십시오.&#39;parameter=value&#39;. 값 사이의 구분 문자로 세미열을 사용합니다.

   * **[!UICONTROL Timezone]**:teradata에 설정된 표준 시간대 [자세히 알아보기](#timezone)

### 쿼리 밴딩

여러 Adobe Campaign 사용자가 동일한 FDA Teradata 외부 계정에 연결되면 **[!UICONTROL Query banding]** 탭에서 한 세션에서 쿼리 밴드(예: 키/값 쌍 집합)를 설정할 수 있습니다.

![](assets/ext_account_20.png)

이 옵션이 구성되면 Campaign 사용자가 Teradata 데이터베이스에 대해 쿼리를 수행할 때마다 Adobe Campaign은 이 사용자와 연관된 키 목록으로 구성된 메타 데이터를 전송합니다. 그런 다음 이 데이터를 Teradata 관리자가 감사 목적으로 사용하거나 액세스 권한을 관리할 수 있습니다.

>[!NOTE]
>
>For more information on **[!UICONTROL Query banding]**, refer to the [Teradata documentation](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw).

쿼리 밴딩을 구성하려면 아래 단계를 따르십시오.

1. 사용자에게 연결된 쿼리 **[!UICONTROL Default]** 밴드가 없는 경우 사용할 기본 쿼리 밴드를 입력할 수 있습니다. 이 필드를 비워 두면 쿼리 밴드가 없는 사용자는 Teradata을 사용할 수 없습니다.

1. 각 사용자에 대한 쿼리 **[!UICONTROL Users]** 밴드를 지정하려면 필드를 사용합니다. 필요한 만큼 키/값 쌍을 추가할 수 있습니다(예: priority=1;workload=high). 사용자에게 지정된 쿼리 범위가 없으면 필드가 **[!UICONTROL Default]** 적용됩니다.

1. 이 기능 **[!UICONTROL Active]** 을 활성화하려면 확인란을 선택합니다.

#### 외부 계정 문제 해결 {#external-account-troubleshooting}

연결 **TIM-03008 날짜 &#39;2&#39;를 테스트하는 동안 다음 오류가 표시되는 경우:누락된 문자(iRc=-53)** (ODBC 드라이버가 올바르게 설치되어 있고 캠페인 서버에 대해 LD_LIBRARY_PATH(Linux)/PATH(Windows)가 설정되어 있는지 확인하십시오.

오류 **ODB-240000 ODBC 오류: [Microsoft][ODBC Driver Manager] 데이터 원본 이름을 찾을 수 없으며 기본 드라이버가 지정되지 않았습니다.** 16.X 드라이버를 사용하는 경우 Windows에서 발생합니다. Adobe Campaign은 odbcinst.ini에서 teradata의 이름을 &#39;{teradata}&#39;로 지정합니다.

* Campaign 18.10을 시작하면 외부 계정의 옵션에 ODBCDriverName=&quot;Teradata 데이터베이스 ODBC 드라이버 16.10&quot;을 추가할 수 있습니다. 버전 번호는 변경될 수 있으며 정확한 이름은 obcad32.exe를 실행하고 드라이버 탭에 액세스하여 찾을 수 있습니다.

* 이전 캠페인 버전을 사용하는 경우 드라이버 설치로 만든 odbcinst.ini의 Teradata 섹션을 Teradata라는 새 섹션으로 복사해야 합니다. 이 경우 Regedit을 사용할 수 있습니다. 베이스가 latin1인 경우 옵션에서 **APICharSize=1을** 추가해야 합니다.

## 추가 구성 {#teradata-additional-configurations}

<!--
### Compatibility {#teradata-compatibility}

**Based in Unicode**

| Database version | Driver version |  Minimal Campaign version required |  Note |
|:-:|:-:|:-:|:-:|
| 15  |  15 |  Campaign Classic 17.9 | Under Linux: Queries with timestamp may fail (fixed in build 8937 for 18.4 and 8977 for 18.10) In debug mode, warnings relative to bad memory usage in the driver may occur. |
| 15  | 16  | Campaign Classic 17.9  | Recommended setup for a Teradata 15 database under Linux.  |
|  16 | 16  | Campaign Classic 18.10 |  Unicode characters with surrogate pairs are not fully handled. Using surrogate characters in data should work. Using surrogates in a filtering condition of a query will not work without this change. |
| 16  |  15 |  Campaign Classic 19.0 |  &nbsp; |

**Based in Latin1**

Versions previous to Adobe Campaign Classic 17.9 only supported Teradata Latin-1 database.

Starting from Adobe Campaign Classic 17.9, we now support by default Teradata database in Unicode.

Customers with a Latin-1 Teradata database migrating to a recent Campaign Classic release will have to add the parameter APICharSize=1 in the options of the external account.
-->

### 사용자 구성 {#user-configuration}

외부 데이터베이스에 대해 다음 권한이 필요합니다.사용자 지정 절차 만들기/삭제/삽입/선택 Adobe Campaign 인스턴스에서 md5 및 sha2 함수를 사용하려면 사용자 모드 기능을 만들어야 할 수도 있습니다.

올바른 시간대를 구성해야 합니다. Adobe Campaign 인스턴스에서 만든 외부 계정에 설정될 내용과 일치해야 합니다.

Adobe Campaign은 데이터베이스에 만들 개체에 보호 모드(폴백)를 설정하지 않습니다. 다음 쿼리를 사용하여 Adobe Campaign이 Teradata 데이터베이스에 연결하는 데 사용할 사용자에 대한 기본값을 설정해야 할 수 있습니다.

| 기본 폴백 비활성화 |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

### MD5 설치 {#md5-installation}

Adobe Campaign 인스턴스에서 md5 기능을 사용하려면 이 [페이지](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip)에서 Teradata 데이터베이스에 사용자 모드 기능을 설치해야 합니다.

다운로드한 파일의 sha1은 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e와 같습니다.

md5를 설치하려면:

1. md5_20080530.zip 파일의 압축을 해제합니다.

1. md5/src 디렉토리로 이동합니다.

1. bteq를 사용하여 Teradata 데이터베이스에 연결합니다.

1. 다음 bteq 명령을 실행합니다.

   ```
   .run file = hash_md5.btq
   ```

### SHA2 설치 {#sha2-installation}

Adobe Campaign 인스턴스에서 sha2 함수를 사용하려면 이 [페이지](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip)에서 Teradata 데이터베이스에 사용자 모드 기능을 설치해야 합니다.

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

### UDF_UTF16TO8 설치 {#UDF-UTF16TO8-installation}

Adobe Campaign 인스턴스에서 udf_utf16to8 함수를 사용하려면 이 **페이지** (utk_release1.7.0.0.zip)의 [Teradata 유니코드 도구 키트에서 Teradata 데이터베이스에 사용자 모드 기능을 설치해야 합니다](https://downloads.teradata.com/download/tools/unicode-tool-kit) .

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

## Linux용 캠페인 서버 구성 {#campaign-server-linux}

드라이버 설치 시 다음이 필요합니다.

* Teradata ODBC 드라이버 - 이 [페이지에서 찾을 수 있습니다.](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* 이 [페이지에 있는 teradata 도구 및 유틸리티(벌크 로드에 사용)](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

파일 이름 및 sha1:

* tdobc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b847f44fd

* TeradataToolsAndUtilitiesBase__linux_indp.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

Linux 배포를 위한 패키지가 없는 경우 CentOS 7에 설명된 대로(예: docker 사용) 설치한 다음 Adobe Campaign 서버에 /opt/teradata의 컨텐츠를 복사할 수 있습니다.

### ODBC 드라이버 설치 {#odbc-installation}

ODBC 드라이버를 설치하려면:

1. tdobc1620__linux_indpp.16.20.00.00-1.tar.gz 파일을 추출합니다.

1. tdobc1620 디렉토리로 이동합니다.

1. 설치 스크립트를 수정해야 할 수 있습니다.

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. setup_wrapper.sh를 실행합니다.

### Teradata 도구 및 유틸리티 설치 {#teradata-tools-installation}

도구를 설치하려면:

1. TeradataToolsAndUtilitiesBase__linux_indpp.16.20.01.00.tar.gz 파일을 추출합니다.

1. TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu 디렉토리로 이동합니다.

1. setup_wrapper.sh를 실행합니다.

1. TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2 디렉토리로 이동합니다.

1. setup_wrapper.sh를 실행합니다.

1. TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase 디렉토리로 이동합니다.

1. setup_wrapper.sh를 실행합니다.

1. libtelapi.so 파일은 /opt/teradata/client/16.20/lib64에서 사용할 수 있어야 합니다.

## Windows용 캠페인 서버 구성 {#campaign-server-windows}

먼저 Windows용 Teradata 도구 및 유틸리티를 다운로드해야 합니다. 이 [페이지에서 다운로드할 수 있습니다](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

ODBC 드라이버와 Teradata Parallel Transporter Base를 설치해야 합니다. teradata 데이터베이스에서 대량 로드를 수행하는 데 사용되는 telapi.dll을 설치합니다.

드라이버와 유틸리티의 경로가 실행 중에 서버가 보유할 PATH 변수에 있는지 확인합니다. 기본적으로 경로는 C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Program Files\Teradata\Client\15.10\bin on 64 bit입니다.

## 시간대 {#timezone}

Teradata은 표준이 아닌 표준 시간대 이름을 사용하므로 [Teradata 사이트에서 해당 목록을 찾을 수 있습니다](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA). Adobe Campaign은 외부 구성에 지정된 시간대를 Teradata이 이해하는 시간대로 전환하려고 합니다. 통신문을 찾을 수 없는 경우, 옷장 GMT+X(또는 GMT-X) 시간대가 세션에 검색되고 로그에 경고가 표시됩니다.

변환은 다음 데이터 디렉터리에 있어야 하는 teradata_timezones.txt 파일을 읽습니다.linux의 /usr/local/neolane/nl6/datakit 이 파일을 편집하는 경우 소스 코드를 변경하려면 Adobe Campaign 팀에 문의하십시오. 그렇지 않으면 다음 캠페인 업데이트 동안 이 파일을 덮어쓰게 됩니다.

-verbose 스위치로 nlserver를 실행할 때 연결하는 데 사용되는 표준 시간대가 표시됩니다. 예:

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

사용된 시간대가 올바르지 않으면 외부 계정에 &quot;TimeZoneName&quot;이라는 옵션을 추가할 수 있습니다. 이 경우 Teradata 값(예: &quot;TimeZoneName=Europe Central&quot;)을 사용합니다.

teradata 문서에서 벌크 로드 또는 &quot;빠른 로드&quot;를 사용하는 경우 Campaign은 시간대를 표시할 수 없습니다. 따라서 Campaign에서 연결하는 데 사용할 사용자의 기본 시간대를 설정하는 것이 좋습니다.

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```
