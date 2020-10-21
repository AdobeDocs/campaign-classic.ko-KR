---
title: 외부 데이터베이스 액세스
seo-title: 외부 데이터베이스 액세스
description: 외부 데이터베이스 액세스
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
source-git-commit: 3acf2359c74a3dc4b18c8976fee14dcbaf3fa510
workflow-type: tm+mt
source-wordcount: '1826'
ht-degree: 3%

---


# FDA 커넥터 구성 {#specific-configurations-by-database-type}

Adobe Campaign에서 액세스할 수 있는 외부 데이터베이스에 따라 특정 구성을 수행해야 합니다. 이러한 구성은 본질적으로 드라이버를 설치하고 Adobe Campaign 서버의 각 RDBMS에 속하는 환경 변수를 선언하는 것과 관련되어 있습니다.

Teradata, Hadoop 2.1 또는 Netezza와 같은 기존 커넥터에 대한 자세한 내용은 이 [페이지를 참조하십시오](../../platform/using/legacy-connectors.md).

일반적으로, Adobe Campaign 서버의 외부 데이터베이스에 해당 클라이언트 레이어를 설치해야 합니다.

>[!NOTE]
>
>호환 버전은 [캠페인 호환성 매트릭스에 나와 있습니다](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA).

## Azure Synapse에 대한 액세스 구성 {#configure-access-to-azure-synapse}

### Azure 동기화 외부 계정 {#azure-external}

외부 계정을 사용하면 Campaign 인스턴스를 Azure Sync 외부 데이터베이스에 연결할 수 있습니다. [!DNL Azure] 
외부 계정 [!DNL Azure Synapse] 을 만들려면

1. Campaign Classic에서 [!DNL Azure Synapse] 외부 계정을 구성합니다. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. **[!UICONTROL New]**&#x200B;을(를) 클릭합니다.

1. 외부 계정 **[!UICONTROL External database]** 으로 선택합니다 **[!UICONTROL Type]**.

1. 외부 계정을 [!DNL Azure Synapse] 구성해야 합니다.

   * **[!UICONTROL Type]**:Azure 구문 분석

   * **[!UICONTROL Server]**:Azure Synapse 서버의 URL

   * **[!UICONTROL Account]**:사용자의 이름

   * **[!UICONTROL Password]**:사용자 계정 암호

   * **[!UICONTROL Database]**:데이터베이스 이름

   ![](assets/azure_1.png)

### CentOS의 Azure 구문 {#azure-centos}

**사전 요구 사항:**

* ODBC 드라이버를 설치하려면 루트 권한이 필요합니다.
* Microsoft에서 제공하는 Red Hat Enterprise ODBC 드라이버는 CentOS와 함께 사용하여 SQL Server에 연결할 수도 있습니다.
* 버전 13.0은 Red Hat 6 및 7과 함께 작동합니다.

CentOS에서 Azure 동기화를 구성하려면:

1. 먼저 ODBC 드라이버를 설치합니다. 이 [페이지에서 찾을 수](https://www.microsoft.com/en-us/download/details.aspx?id=50420)있습니다

   >[!NOTE]
   >
   >ODBC 드라이버 버전 13에만 적용됩니다.

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   # Uninstall if already installed Unix ODBC driver
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   
   sudo ACCEPT_EULA=Y yum install msodbcsql
   
   sudo ACCEPT_EULA=Y yum install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   
   # the Microsoft driver expects unixODBC to be here /usr/lib64/libodbc.so.1, so add soft links to the '.so.2' files
   cd /usr/lib64
   sudo ln -s libodbccr.so.2   libodbccr.so.1
   sudo ln -s libodbcinst.so.2 libodbcinst.so.1
   sudo ln -s libodbc.so.2     libodbc.so.1
   
   # Set the path for unixODBC
   export ODBCINI=/usr/local/etc/odbc.ini
   export ODBCSYSINI=/usr/local/etc
   source ~/.bashrc
   
   #Add a DSN information to /etc/odbc.ini
   sudo vi /etc/odbc.ini
   
   #Add the following:
   [Azure Synapse Analytics]
   Driver      = ODBC Driver 13 for SQL Server
   Description = Azure Synapse Analytics DSN
   Trace       = No
   Server      = [insert your server here]
   ```

1. 필요한 경우 다음 명령을 실행하여 unixODBC 개발 헤더를 설치할 수 있습니다.

   ```
   sudo yum install unixODBC-devel
   ```

1. 드라이버를 설치한 후 ODBC 드라이버를 테스트 및 확인하고 필요한 경우 데이터베이스를 쿼리할 수 있습니다. 다음 명령을 실행합니다.

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. 그런 다음 Campaign Classic에서 [!DNL Azure Synapse] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 이 [섹션을 참조하십시오](../../platform/using/specific-configuration-database.md#azure-external).

1. Azure Synapse Analytics는 TCP 1433 포트를 통해 통신하므로 방화벽에서 이 포트를 열어야 합니다. 다음 명령을 사용하십시오.

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >Azure Synapse Analytics에서 통신을 허용하려면 공개 IP를에 추가해야 할 수 허용 목록에 추가하다 있습니다. 이렇게 하려면 [Azure 설명서를 참조하십시오](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

1. iptables의 경우 다음 명령을 실행합니다.

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

### Windows의 Azure 구문 {#azure-windows}

>[!NOTE]
>
>ODBC 드라이버 버전 13에서만 사용할 수 있지만 Adobe Campaign Classic에서는 SQL Server Native Client 드라이버 11.0 및 10.0을 사용할 수도 있습니다.

Windows에서 Azure 동기화를 구성하려면:

1. 먼저 Microsoft ODBC 드라이버를 설치합니다. 이 [페이지에서 찾을 수](https://www.microsoft.com/en-us/download/details.aspx?id=50420)있습니다

1. 설치할 파일을 선택하십시오.

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. ODBC 드라이버가 설치되면 필요한 경우 테스트할 수 있습니다. 자세한 정보는 이 [페이지](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server)를 참조하십시오.

1. 그런 다음 Campaign Classic에서 [!DNL Azure Synapse] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 이 [섹션을 참조하십시오](../../platform/using/specific-configuration-database.md#azure-external).

1. Azure Synapse Analytics는 TCP 1433 포트를 통해 통신하므로 Windows Defender 방화벽에서 이 포트를 열어야 합니다. For more on this, refer to [Windows documentation](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

### 데비안의 Azure Synapse {#azure-debian}

**사전 요구 사항:**

* ODBC 드라이버를 설치하려면 루트 권한이 필요합니다.
* msodbcsql 패키지를 설치하려면 curl이 필요합니다. 설치되어 있지 않은 경우 다음 명령을 실행하십시오.

   ```
   sudo apt-get install curl
   ```

Debian에서 Azure 구문을 구성하려면:

1. 먼저 SQL Server용 Microsoft ODBC 드라이버를 설치합니다. 다음 명령을 사용하여 SQL Server용 ODBC 드라이버 13.1을 설치합니다.

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. sudo apt-get update **를 호출할 때 &quot;메서드 드라이버 /usr/lib/apt/methods/https를 찾을 수 없습니다&quot;** 오류가 발생하는 경우 **명령을 실행해야 합니다**.

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. 이제 다음 명령을 사용하여 mssql-tools를 설치해야 합니다. 일괄 복사 프로그램(또는 BCP) 유틸리티를 사용하고 쿼리를 실행하려면 Mssq-tools가 필요합니다.

   ```
   sudo ACCEPT_EULA=Y apt-get install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

1. 필요한 경우 다음 명령을 실행하여 unixODBC 개발 헤더를 설치할 수 있습니다.

   ```
   sudo yum install unixODBC-devel
   ```

1. 드라이버를 설치한 후 ODBC 드라이버를 테스트 및 확인하고 필요한 경우 데이터베이스를 쿼리할 수 있습니다. 다음 명령을 실행합니다.

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. 이제 Campaign Classic에서 [!DNL Azure Synapse] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 이 [섹션을 참조하십시오](../../platform/using/specific-configuration-database.md#azure-external).

1. Azure Synapse Analytics와의 연결을 위해 Debian에 iptables를 구성하려면 다음 명령을 사용하여 호스트 이름에 대한 아웃바운드 TCP 1433 포트를 활성화합니다.

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >Azure Synapse Analytics에서 통신을 허용하려면 공개 IP를에 추가해야 할 수 허용 목록에 추가하다 있습니다. 이렇게 하려면 [Azure 설명서를 참조하십시오](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

## Snowflake 액세스 구성 {#configure-access-to-snowflake}

>[!NOTE]
>
>[!DNL Snowflake] 커넥터는 호스팅 및 온-프레미스 배포에 사용할 수 있습니다. 자세한 정보는 이 [페이지](../../installation/using/capability-matrix.md)를 참조하십시오.

![](assets/snowflake_3.png)

### Snowflake 외부 계정 {#snowflake-external}

외부 계정을 사용하면 [!DNL Snowflake] 캠페인 인스턴스를 Snowflake 외부 데이터베이스에 연결할 수 있습니다.

1. Campaign Classic에서 [!DNL Snowflake] 외부 계정을 구성합니다. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. **[!UICONTROL New]**&#x200B;을(를) 클릭합니다.

1. 외부 계정 **[!UICONTROL External database]** 으로 선택합니다 **[!UICONTROL Type]**.

1. 외부 계정을 **[!UICONTROL Snowflake]** 구성해야 합니다.

   * **[!UICONTROL Type]**: [!DNL Snowflake]

   * **[!UICONTROL Server]**:서버의 [!DNL Snowflake] URL

   * **[!UICONTROL Account]**:사용자의 이름

   * **[!UICONTROL Password]**:사용자 계정 암호

   * **[!UICONTROL Database]**:데이터베이스 이름

   ![](assets/snowflake.png)

1. 탭을 **[!UICONTROL Parameters]** 클릭한 다음 **[!UICONTROL Deploy functions]** 단추를 클릭하여 함수를 만듭니다.

   ![](assets/snowflake_2.png)

커넥터는 다음 옵션을 지원합니다.

| 옵션 | 설명 |
|---|---|
| 작업 스키마 | 작업 테이블에 사용할 데이터베이스 스키마 |
| warehouse | 사용할 기본 웨어하우스의 이름입니다. 이 값은 사용자의 기본값을 덮어씁니다. |
| TimeZoneName | 기본적으로 비어 있으면 Campaign Classic 앱 서버의 시스템 시간대가 사용됩니다. 이 옵션을 사용하여 TIMEZONE 세션 매개 변수를 강제 적용할 수 있습니다. <br>자세한 정보는 이 [페이지](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone)를 참조하십시오. |
| WeekStart | WEEK_START 세션 매개 변수. 기본적으로 0으로 설정됩니다. <br>자세한 정보는 이 [페이지](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start)를 참조하십시오. |
| UseCachedResult | USE_CACHED_RESULTS 세션 매개 변수. 기본적으로 TRUE로 설정됩니다. 이 옵션을 사용하여 Snowflake 캐시된 결과를 비활성화할 수 있습니다. <br>자세한 정보는 이 [페이지](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html)를 참조하십시오. |

### CentOS의 Snowflake {#snowflake-centos}

1. ODBC 드라이버를 다운로드하십시오 [!DNL Snowflake]. [다운로드를 시작하려면 여기를](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) 클릭하십시오.
1. 그런 다음 다음 다음 명령을 사용하여 CentOs에 ODBC 드라이버를 설치해야 합니다.

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. ODBC 드라이버를 다운로드하여 설치한 후 Campaign Classic을 다시 시작해야 합니다. 이렇게 하려면 다음 명령을 실행합니다.

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. 그런 다음 Campaign Classic에서 [!DNL Snowflake] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 이 [섹션을 참조하십시오](../../platform/using/specific-configuration-database.md#snowflake-external).

### 데비안의 Snowflake {#snowflake-debian}

1. ODBC 드라이버를 다운로드하십시오 [!DNL Snowflake]. [다운로드를](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) 시작합니다.

1. 그런 다음 다음 다음 명령을 사용하여 Debian에 ODBC 드라이버를 설치해야 합니다.

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. ODBC 드라이버를 다운로드하여 설치한 후 Campaign Classic을 다시 시작해야 합니다. 이렇게 하려면 다음 명령을 실행합니다.

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 그런 다음 Campaign Classic에서 [!DNL Snowflake] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 이 [섹션을 참조하십시오](../../platform/using/specific-configuration-database.md#snowflake-external).

### Windows의 Snowflake {#snowflake-windows}

1. Windows용 [ODBC 드라이버를 다운로드합니다](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). 드라이버를 설치하려면 관리자 수준 권한이 필요합니다. 자세한 정보는 이 [페이지](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)를 참조하십시오

1. ODBC 드라이버를 구성합니다. 자세한 정보는 이 [페이지](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)를 참조하십시오

1. 그런 다음 Campaign Classic에서 [!DNL Snowflake] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 이 [섹션을 참조하십시오](../../platform/using/specific-configuration-database.md#snowflake-external).

## Hadoop 3.0에 대한 액세스 구성 {#configure-access-to-hadoop-3}

### Hadoop 외부 계정 {#hadoop-external}

외부 계정을 사용하여 Campaign 인스턴스를 Hadoop 외부 데이터베이스에 연결할 수 있습니다. [!DNL Hadoop]

1. Campaign Classic에서 [!DNL Hadoop] 외부 계정을 구성합니다. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. **[!UICONTROL New]**&#x200B;을(를) 클릭합니다.

1. 외부 계정 **[!UICONTROL External database]** 으로 선택합니다 **[!UICONTROL Type]**.

1. 외부 계정을 **[!UICONTROL Hadoop]** 구성해야 합니다.

   * **[!UICONTROL Type]**:ODBC(Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**:DNS 이름

   * **[!UICONTROL Account]**:사용자의 이름

   * **[!UICONTROL Password]**:사용자 계정 암호

   * **[!UICONTROL Database]**:DSN에 지정되지 않은 경우 데이터베이스의 이름입니다. DSN에 지정된 경우 비워 둘 수 있습니다.

   * **[!UICONTROL Time zone]**:서버 시간대

   ![](assets/hadoop3.png)

커넥터는 다음과 같은 ODBC 옵션을 지원합니다.

| 이름 | 값 |
|---|---|
| ODBCMgr | iODBC |
| warehouse | 1/2/4 |

커넥터는 다음과 같은 하이브 옵션도 지원합니다.

| 이름 | 값 | 설명 |
|---|---|---|
| bulkKey | Azure blob 또는 DataLake 액세스 키 | wasb:// 또는 wasbs:// 벌크 로더의 경우(벌크 로드 도구가 wasb:// 또는 wasbs://으로 시작하는 경우). <br>벌크 로드를 위한 물방울 또는 DataLake 버킷의 액세스 키입니다. |
| hdfsPort | 기본적으로 8020으로 <br>설정된 포트 번호 | HDFS 벌크 로드의 경우(벌크 로드 도구가 webhdfs:// 또는 webhdfss://으로 시작하는 경우) |
| 버킷 수 | 20 | 클러스터형 테이블을 만들 때의 버킷 수입니다. |
| fileFormat | 쪽모이 세공 | 작업 표의 기본 파일 형식입니다. |

### Hadoop 3.0 구성 {#configuring-hadoop}

FDA에서 Hadoop 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에서 다음 구성이 필요합니다. 이 구성은 Windows 및 Linux 모두에서 사용할 수 있습니다.

1. OS 버전에 따라 Hadoop용 ODBC 드라이버를 다운로드합니다. 드라이버는 [이 페이지에서 찾을 수 있습니다](https://www.cloudera.com/downloads.html).

1. 그런 다음 ODBC 드라이버를 설치하고 하이브 연결에 대한 DSN을 만들어야 합니다. 지침은 [이 페이지에 있습니다.](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. ODBC 드라이버를 다운로드하여 설치한 후 Campaign Classic을 다시 시작해야 합니다. 이렇게 하려면 다음 명령을 실행합니다.

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 그런 다음 Campaign Classic에서 [!DNL Hadoop] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 이 [섹션을 참조하십시오](../../platform/using/specific-configuration-database.md#hadoop-external).

## Oracle 액세스 권한 구성 {#configure-access-to-oracle}

### Oracle 외부 계정 {#oracle-external}

외부 계정을 사용하여 Campaign 인스턴스를 Hadoop 외부 데이터베이스에 연결할 수 있습니다. [!DNL Oracle]

1. Campaign Classic에서 [!DNL oracle] 외부 계정을 구성합니다. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. **[!UICONTROL New]**&#x200B;을(를) 클릭합니다.

1. 외부 계정 **[!UICONTROL External database]** 으로 선택합니다 **[!UICONTROL Type]**.

1. 외부 계정을 **[!UICONTROL Oracle]** 구성해야 합니다.

   * **[!UICONTROL Type]**:Oracle

   * **[!UICONTROL Server]**:DNS 이름

   * **[!UICONTROL Account]**:사용자의 이름

   * **[!UICONTROL Password]**:사용자 계정 암호

   * **[!UICONTROL Time zone]**:서버 시간대

   ![](assets/oracle_config.png)

### Linux 기반의 Oracle {#for-linux-1}

FDA에서 Oracle 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 아래 추가 구성이 필요합니다.

1. Oracle 버전에 해당하는 Oracle 전체 클라이언트를 설치합니다.
1. TNS 정의를 설치에 추가합니다. 이렇게 하려면 /etc/oracle 저장소의 tnsnames. **ora** 파일에 지정합니다. 이 저장소가 없으면 만듭니다.

   그런 다음 새 TNS_ADMIN 환경 변수를 만듭니다.TNS_ADMIN=/etc/oracle을 내보내고 시스템을 다시 시작합니다.

1. Oracle을 Adobe Campaign 서버(nlserver)에 통합합니다. 이렇게 하려면 **customer.sh** 파일이 Adobe Campaign 서버 트리 구조의 &quot;nl6&quot; 폴더에 있으며 Oracle 라이브러리에 대한 링크가 포함되어 있는지 확인하십시오.

   예를 들어 11.2에 있는 클라이언트의 경우

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >이러한 값(특히 ORACLE_HOME)은 설치 저장소에 따라 다릅니다. 이러한 값을 참조하기 전에 트리 구조를 확인해야 합니다.

1. Oracle에 필요한 라이브러리를 설치합니다.

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

1. 그런 다음 Campaign Classic에서 [!DNL Oracle] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 이 [섹션을 참조하십시오](../../platform/using/specific-configuration-database.md#oracle-external).

### Windows 기반의 Oracle {#for-windows-1}

FDA에서 Oracle 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 아래 추가 구성이 필요합니다.

1. Oracle 클라이언트를 설치합니다.

1. C:Oracle 폴더에서 TNS 정의를 **포함하는 tnsnames.ora** 파일을 생성합니다.

1. C:Oracle을 값으로 사용하여 TNS_ADMIN 환경 변수를 추가하고 시스템을 다시 시작합니다.

1. 그런 다음 Campaign Classic에서 [!DNL Oracle] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 이 [섹션을 참조하십시오](../../platform/using/specific-configuration-database.md#oracle-external).