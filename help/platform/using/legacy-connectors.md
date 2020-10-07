---
title: 기존 커넥터
seo-title: 기존 커넥터
description: 기존 커넥터
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 0%

---


# 기존 커넥터 {#legacy-connectors}

레거시 FDA 커넥터는 여전히 Adobe에서 지원됩니다. 하지만 이 [페이지에 나열된 보다 최근의 대체 항목으로 대체할 것을 권장합니다](../../platform/using/specific-configuration-database.md).

## Hadoop 2.1에 대한 액세스 구성 {#configure-access-to-hadoop}

### Windows {#for-windows}

1. Windows용 ODBC 및 [Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886) 드라이버를 설치합니다.
1. ODBC DataSource 관리자 도구를 실행하여 DSN(데이터 원본 이름)을 만듭니다. 하이브에 대한 시스템 DSN 샘플이 수정되어 있습니다.

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. Hadoop 외부 계정을 만듭니다( [이 페이지](../../platform/using/external-accounts.md#hadoop-external-account) 섹션에 자세히 표시됨).

### Linux용 {#for-linux}

1. Linux용 통합 설치

   ```
   apt-get install unixodbc
   ```

1. HortonWorks에서 Apache Hive용 ODBC 드라이버 다운로드 및 설치: [https://www.hortonworks.com/downloads/](https://www.hortonworks.com/downloads/).

   ```
   dpkg -i hive-odbc-native_2.1.10.1014-2_amd64.deb
   ```

1. ODBC 파일 위치를 확인합니다.

   ```
   root@campadpac71:/tmp# odbcinst -j
   unixODBC 2.3.1
   DRIVERS............: /etc/odbcinst.ini
   SYSTEM DATA SOURCES: /etc/odbc.ini
   FILE DATA SOURCES..: /etc/ODBCDataSources
   USER DATA SOURCES..: /root/.odbc.ini
   SQLULEN Size.......: 8
   SQLLEN Size........: 8
   SQLSETPOSIROW Size.: 8
   ```

1. DSN(데이터 원본 이름)을 만들고 odbc.ini 파일을 편집합니다. 그런 다음 하이브 연결에 대한 DSN을 만듭니다.

   다음은 HDInsight가 &quot;viral&quot;이라는 연결을 설정하는 예입니다.

   ```
   [ODBC Data Sources]
   vorac 
   
   [vorac]
   Driver=/usr/lib/hive/lib/native/Linux-amd64-64/libhortonworkshiveodbc64.so
   HOST=vorac.azurehdinsight.net
   PORT=443
   Schema=sm_tst611
   HiveServerType=2
   AuthMech=6
   UID=admin
   PWD=<your password here>
   HTTPPath=
   UseNativeQuery=1
   ```

   >[!NOTE]
   >
   >여기서 **UseNativeQuery** 매개 변수는 매우 중요합니다. 캠페인은 하이브 인식이며 UseNativeQuery가 설정되지 않으면 올바르게 작동하지 않습니다. 일반적으로 드라이버 또는 하이브 SQL 커넥터는 쿼리를 다시 작성하고 열 순서를 변경합니다.

   인증 설정은 하이브/Hadoop 구성에 따라 다릅니다. 예를 들어 HD Insight의 경우 [여기에 설명된 대로 사용자/암호 인증에는 AuthMtech=6을 사용합니다](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm).

1. 변수를 내보냅니다.

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. /usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini를 통해 Hortonworks 드라이버를 설정합니다.

   Campaign 및 unix-odbc(libodbcinst)와 연결할 수 있으려면 UTF-16을 사용해야 합니다.

   ```
   [Driver]
   
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=/usr/lib/hive/lib/native/hiveodbc/ErrorMessages/
   LogLevel=0
   LogPath=/tmp/hive
   SwapFilePath=/tmp
   
   ODBCInstLib=libodbcinst.so
   ```

1. 이제 isql을 사용하여 연결을 테스트할 수 있습니다.

   ```
   isql vorac
   isql vorac -v
   ```

1. Hadoop 외부 계정을 만듭니다( [이 페이지](../../platform/using/external-accounts.md#hadoop-external-account) 섹션에 자세히 표시됨).

## Netezza 액세스 구성 {#configure-access-to-netezza}

FDA에서 Netezza 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 아래 추가 구성이 필요합니다.

1. 사용하는 운영 체제에 따라 Netezza용 ODBC 드라이버를 설치합니다.

   * **Linux용 nz-linuxclient-v7.2.0.0.tar.gz** . 운영 체제(linux 또는 linux64)에 해당하는 폴더를 선택하고 압축 해제 명령을 시작합니다. 기본적으로 제안된 저장소에서 설치되도록 둘 수 있습니다.&quot;/usr/local/nz&quot;
   * **Windows용 nz-winclient-v7.2.0.0.zip** . 파일의 압축을 풀고 운영 체제에 해당하는 실행 스크립트를 시작합니다.nzodbcsetup.exe 또는 nzodbcsetup64.exe. 마법사 지침에 따라 드라이버 설치를 마칩니다.

1. ODBC 드라이버를 구성합니다. 구성은 표준 파일에서 수행할 수 있습니다. **/etc/odbc.ini** for general parameters and **/etc/odbcinst.ini** for decoring driver.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot;은 odbcinst.ini 파일의 위치에 해당합니다.

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. Adobe Campaign 서버의 환경 변수를 지정합니다.

   * **LD_LIBRARY_PATH**:/usr/local/nz/lib 및 /usr/local/nz/lib64. &quot;/usr/local/nz&quot;는 드라이버를 설치할 때 기본적으로 제공되는 설치 저장소에 해당합니다. 여기에서 설치를 위해 선택한 저장소를 지정해야 합니다.
   * **ODBCINI**:odbc.ini 파일의 위치입니다(예: /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**:odbc.ini 파일의 위치입니다. 또한 이 두 번째 변수를 사용하여 odbc.ini 파일을 사용해야 합니다.

1. 그런 다음 Campaign Classic에서 Netezza 외부 계정을 구성할 수 있습니다. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 을 **[!UICONTROL New]** 클릭하고 **[!UICONTROL External database]** 으로 선택합니다 **[!UICONTROL Type]**.

1. 외부 계정을 구성하려면 다음을 **[!UICONTROL Netezza]** 지정해야 합니다.

   * **[!UICONTROL Type]**:네테차

   * **[!UICONTROL Server]**:Netezza 서버의 URL

   * **[!UICONTROL Account]**:사용자의 이름

   * **[!UICONTROL Password]**:사용자 계정 암호

   * **[!UICONTROL Database]**:데이터베이스 이름

>[!NOTE]
>
>자동으로 생성된 기본 키를 포함하는 스키마에 대한 작업은 고려되지 않습니다.
>
>테이블에 스키마에 정의된 첫 번째 인덱스의 **Organize on** 절을 사용합니다. 이 절은 Netezza와 함께 1-4개의 열로 제한되므로 이 인덱스는 4개 이상의 열을 포함할 수 없습니다.

## Sybase IQ에 대한 액세스 구성 {#configure-access-to-sybase-iq}

FDA에서 Sybase IQ 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 추가 구성이 필요합니다.

1. 원본 패키지가 서버에 있는지 확인합니다.
1. iq_odbc **를 설치합니다**. 설치가 끝날 때 오류가 발생할 수 있습니다. 이 오류는 무시될 수 있습니다.
1. iq_client_common을 **설치합니다**. 설치 마지막에 Java 오류가 발생할 수 있습니다. 이 오류는 무시될 수 있습니다.
1. ODBC 드라이버를 구성합니다. 구성은 표준 파일에서 수행할 수 있습니다./etc/odbc.ini일반 매개 변수 및 드라이버 선언용 /etc/odbcinst.ini을 참조하십시오.

   * **/etc/odbc.ini** (문자와 같은 `<server_alias>` 값 대신 사용자 정의):

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. LD_LIBRARY_PATH 변수에 새 libobc16.so 라이브러리의 경로를 추가합니다. 이를 위해서는 다음을 수행하십시오.

   * customer.sh 파일을 사용하여 경로를 선언할 경우:LD_LIBRARY_PATH 변수에 대해 /opt/sybase/IQ-16_0/lib64 경로를 추가합니다.
   * 그렇지 않은 경우 Unix 명령을 사용합니다.

1. 그런 다음 Campaign Classic에서 Sybase IQ 외부 계정을 구성할 수 있습니다. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 을 **[!UICONTROL New]** 클릭하고 **[!UICONTROL External database]** 으로 선택합니다 **[!UICONTROL Type]**.

1. 외부 계정을 구성하려면 다음을 **[!UICONTROL Sybase IQ]** 지정해야 합니다.

   * **[!UICONTROL Type]**:ODBC(Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**:5단계에서 정의된 ODBC 연결(`<server_alias>`)에 해당합니다. 서버 자체의 이름이 아닐 수도 있습니다.

   * **[!UICONTROL Account]**:사용자의 이름

   * **[!UICONTROL Password]**:사용자 계정 암호

   * **[!UICONTROL Database]**:데이터베이스 이름

>[!NOTE]
>
>Windows의 경우 Sybase IQ 클라이언트를 Adobe Campaign 서버에 설치하고 ODBC 연결을 만들어야 합니다. Windows에서 Adobe Campaign 서버(nlserver)가 서비스로 실행 중일 때 시스템 데이터 소스를 만들어야 합니다.

## 메타데이터 액세스 구성 {#configure-access-to-teradata}

FDA에서 Teradata 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 특정 추가 구성이 필요합니다. Teradata 데이터베이스를 구성하는 방법에 대한 자세한 내용은 이 [페이지를 참조하십시오](../../platform/using/appendices-fda.md#teradata-configuration).

1. Teradata용 [ODBC 드라이버를 설치합니다](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

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

1. 그런 다음 Campaign Classic에서 Teradata 외부 계정을 구성할 수 있습니다. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 을 **[!UICONTROL New]** 클릭하고 **[!UICONTROL External database]** 으로 선택합니다 **[!UICONTROL Type]**.

1. 외부 계정을 구성하려면 다음을 **[!UICONTROL Teradata]** 지정해야 합니다.

   * **[!UICONTROL Type]**:Teradata

   * **[!UICONTROL Server]**:Teradata 서버의 URL

   * **[!UICONTROL Account]**:사용자의 이름

   * **[!UICONTROL Password]**:사용자 계정 암호

   * **[!UICONTROL Database]**:데이터베이스 이름

## SAP HANA에 대한 액세스 구성 {#configure-access-to-sap-hana}

FDA에서 SAP HANA 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 특정 추가 구성이 필요합니다.

1. 사용하는 운영 체제에 따라 SAP HANA용 ODBC 드라이버를 설치합니다.

   * **Linux용 hdb_client_linux.tgz** . 압축을 풀면 hdbinst 명령을 실행하고 지침에 따라 드라이버 설치를 완료하십시오.
   * **Windows용 hdb_client_windows.zip** . 파일의 압축을 풀고 실행 파일을 시작합니다. **hdbinst.exe**. 마법사 지침에 따라 드라이버 설치를 마칩니다.

1. ODBC 드라이버를 구성합니다. 구성은 표준 파일에서 수행할 수 있습니다./etc/odbc.ini을 참조하십시오.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      &quot;InstallDir&quot;은 **odbcinst.ini** 파일의 위치에 해당합니다.

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Adobe Campaign 서버의 환경 변수를 지정합니다.

   * **LD_LIBRARY_PATH**:여기에는 기본적으로 SAP Hana 클라이언트(/usr/sap/hdbclient/libodbcHDB.so)에 대한 링크가 포함되어야 합니다.
   * **ODBCINI**:odbc.ini 파일의 위치입니다(예: /etc/odbc.ini).

1. 그런 다음 Campaign Classic에서 SAP 하나 외부 계정을 구성할 수 있습니다. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 을 **[!UICONTROL New]** 클릭하고 **[!UICONTROL External database]** 으로 선택합니다 **[!UICONTROL Type]**.

1. 외부 계정을 구성하려면 다음을 **[!UICONTROL SAP Hana]** 지정해야 합니다.

   * **[!UICONTROL Type]**:SAP 하나

   * **[!UICONTROL Server]**:SAP 하나 서버의 URL

   * **[!UICONTROL Account]**:사용자의 이름

   * **[!UICONTROL Password]**:사용자 계정 암호
