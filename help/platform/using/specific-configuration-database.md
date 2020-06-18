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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fecfff477b0750782c87c017a15e306acac4c61d
workflow-type: tm+mt
source-wordcount: '2865'
ht-degree: 0%

---


# 데이터베이스 유형별 특정 구성 {#specific-configurations-by-database-type}

Adobe Campaign에서 액세스할 수 있는 외부 데이터베이스에 따라 특정 구성을 수행해야 합니다. 이러한 구성에는 Adobe Campaign 서버의 각 RDBMS에 속하는 드라이버 설치 및 환경 변수 선언이 포함됩니다.

일반적으로 Adobe Campaign 서버의 외부 데이터베이스에 해당 클라이언트 레이어를 설치해야 합니다.

>[!NOTE]
>
>호환 버전은 [캠페인 호환성 매트릭스에 나와 있습니다](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA).

## Azure Synapse에 대한 액세스 구성 {#configure-access-to-azure-synapse}

### Azure 동기화 외부 계정 {#azure-external}

외부 계정을 사용하면 Campaign 인스턴스를 Azure Sync 외부 데이터베이스에 연결할 수 있습니다. [!DNL Azure] 
외부 계정 [!DNL Azure Synapse] 을 만들려면

1. Campaign Classic에서 [!DNL Azure Synapse] 외부 계정을 구성합니다. 에서 **[!UICONTROL Explorer]**/ **[!UICONTROL Administration]** / **[!UICONTROL Platform]** /를 **[!UICONTROL External accounts]**&#x200B;클릭합니다.

1. **[!UICONTROL Create]**&#x200B;을 클릭합니다.

1. 외부 계정을 [!DNL Azure Synapse] 구성해야 합니다.

   * **[!UICONTROL Type]**: Azure Synapse Analytics

   * **[!UICONTROL Server]**: Azure Synapse 서버의 URL

   * **[!UICONTROL Account]**: 사용자의 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Database]**: 데이터베이스 이름
   ![](assets/azure_1.png)

### CentOS의 Azure 구문 {#azure-centos}

**전제 조건:**

* ODBC 드라이버를 설치하려면 루트 권한이 필요합니다.
* Microsoft에서 제공하는 Red Hat Enterprise ODBC 드라이버는 CentOS와 함께 사용하여 SQL Server에 연결할 수도 있습니다.
* 버전 13.0은 Red Hat 6 및 7과 함께 사용할 수 있습니다.

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

1. Azure Synapse Analytics은 TCP 1433 포트를 통해 통신하므로 방화벽에서 이 포트를 열어야 합니다. 다음 명령을 사용하십시오.

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >Azure Synapse Analytics 측의 통신을 허용하려면 공개 IP를 허용 목록에 추가해야 할 수 있습니다. 이렇게 하려면 [Azure 설명서를 참조하십시오](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

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

1. ODBC 드라이버가 설치되면 필요한 경우 테스트할 수 있습니다. For more on this, refer to this [page](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server).

1. 그런 다음 Campaign Classic에서 [!DNL Azure Synapse] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 이 [섹션을 참조하십시오](../../platform/using/specific-configuration-database.md#azure-external).

1. Azure Synapse Analytics은 TCP 1433 포트를 통해 통신하므로 Windows Defender 방화벽에서 이 포트를 열어야 합니다. For more on this, refer to [Windows documentation](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

### 데비안의 Azure Synapse {#azure-debian}

**전제 조건:**

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

1. Azure Synapse Analytics과의 연결을 위해 Debian에서 iptables를 구성하려면 다음 명령을 사용하여 호스트 이름에 대한 아웃바운드 TCP 1433 포트를 활성화합니다.

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >Azure Synapse Analytics 측의 통신을 허용하려면 공개 IP를 허용 목록에 추가해야 할 수 있습니다. 이렇게 하려면 [Azure 설명서를 참조하십시오](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

## Snowflake 액세스 구성 {#configure-access-to-snowflake}

>[!NOTE]
>
>[!DNL Snowflake] 커넥터는 호스팅 및 온-프레미스 배포에 사용할 수 있습니다. For more on this, refer to [this article](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### Snowflake 외부 계정 {#snowflake-external}

외부 계정을 사용하면 Campaign 인스턴스를 Snowflake 외부 데이터베이스에 연결할 수 있습니다. [!DNL Snowflake]

1. Campaign Classic에서 [!DNL Snowflake] 외부 계정을 구성합니다. 에서 **[!UICONTROL Explorer]**/ **[!UICONTROL Administration]** / **[!UICONTROL Platform]** /를 **[!UICONTROL External accounts]**&#x200B;클릭합니다.

1. 기본 제공 **[!UICONTROL Snowflake]** 외부 계정을 선택합니다.

1. 외부 계정을 **[!UICONTROL Snowflake]** 구성해야 합니다.

   * **[!UICONTROL Server]**: 서버의 [!DNL Snowflake] URL

   * **[!UICONTROL Account]**: 사용자의 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Database]**: 데이터베이스 이름
   ![](assets/snowflake.png)

1. 탭을 **[!UICONTROL Parameters]** 클릭한 다음 **[!UICONTROL Deploy functions]** 단추를 클릭하여 함수를 만듭니다.

   ![](assets/snowflake_2.png)

커넥터는 다음 옵션을 지원합니다.

| 옵션 | 설명 |
|---|---|
| 작업 스키마 | 작업 테이블에 사용할 데이터베이스 스키마 |
| warehouse | 사용할 기본 웨어하우스의 이름입니다. 이 값은 사용자의 기본값을 덮어씁니다. |
| TimeZoneName | 기본적으로 비어 있으면 Campaign Classic 앱 서버의 시스템 시간대가 사용됩니다. 이 옵션을 사용하여 TIMEZONE 세션 매개 변수를 강제 적용할 수 있습니다. <br>자세한 내용은 [이 페이지를 참조하십시오](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | WEEK_START 세션 매개 변수. 기본적으로 0으로 설정됩니다. <br>자세한 내용은 [이 페이지를 참조하십시오](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
| UseCachedResult | USE_CACHED_RESULTS 세션 매개 변수. 기본적으로 TRUE로 설정됩니다. 이 옵션을 사용하여 Snowflake 캐시된 결과를 비활성화할 수 있습니다. <br>자세한 내용은 [이 페이지를 참조하십시오](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

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

### 데비안의 눈꽃 {#snowflake-debian}

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

### Windows에서 눈꽃 {#snowflake-windows}

1. Windows용 [ODBC 드라이버를 다운로드합니다](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). 드라이버를 설치하려면 관리자 수준 권한이 필요합니다. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. ODBC 드라이버를 구성합니다. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. 그런 다음 Campaign Classic에서 [!DNL Snowflake] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 이 [섹션을 참조하십시오](../../platform/using/specific-configuration-database.md#snowflake-external).

## Hadoop 3.0에 대한 액세스 구성 {#configure-access-to-hadoop-3}

FDA에서 Hadoop 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에서 다음 구성이 필요합니다. 이 구성은 Windows 및 Linux 모두에서 사용할 수 있습니다.

1. OS 버전에 따라 Hadoop용 ODBC 드라이버를 다운로드합니다. 드라이버는 [이 페이지에서 찾을 수 있습니다](https://www.cloudera.com/downloads.html).

1. 그런 다음 ODBC 드라이버를 설치하고 하이브 연결에 대한 DSN을 만들어야 합니다. 지침은 [이 페이지에 있습니다.](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. ODBC 드라이버를 다운로드하여 설치한 후 Campaign Classic을 다시 시작해야 합니다. 이렇게 하려면 다음 명령을 실행합니다.

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 그런 다음 Campaign Classic에서 Snowflake 외부 계정을 구성할 수 있습니다. 에서 **[!UICONTROL Explorer]**/ **[!UICONTROL Administration]** / **[!UICONTROL Platform]** /를 **[!UICONTROL External accounts]**&#x200B;클릭합니다.

1. 을 클릭하고 계정 유형 **[!UICONTROL Create]** **[!UICONTROL External database]** 으로 선택합니다.

1. 외부 계정을 **[!UICONTROL  Hadoop]** 구성하려면 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: ODBC(Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: DNS 이름

   * **[!UICONTROL Account]**: 사용자의 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Database]**: DSN에 지정되지 않은 경우 데이터베이스의 이름입니다. DSN에 지정된 경우 비워 둘 수 있습니다.

   * **[!UICONTROL Time zone]**: 서버 시간대
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

   * **Linux용 nz-linuxclient-v7.2.0.0.tar.gz** . 운영 체제(linux 또는 linux64)에 해당하는 폴더를 선택하고 압축 해제 명령을 시작합니다. 기본적으로 제안된 저장소에서 설치하도록 둘 수 있습니다. &quot;/usr/local/nz&quot;
   * **Windows용 nz-winclient-v7.2.0.0.zip** . 파일의 압축을 풀고 운영 체제에 해당하는 실행 스크립트를 시작합니다. nzodbcsetup.exe 또는 nzodbcsetup64.exe. 마법사 지침에 따라 드라이버 설치를 마칩니다.

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

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib 및 /usr/local/nz/lib64. &quot;/usr/local/nz&quot;는 드라이버를 설치할 때 기본적으로 제공되는 설치 저장소에 해당합니다. 여기에서 설치를 위해 선택한 저장소를 지정해야 합니다.
   * **ODBCINI**: odbc.ini 파일의 위치입니다(예: /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: odbc.ini 파일의 위치입니다. 또한 이 두 번째 변수를 사용하여 odbc.ini 파일을 사용해야 합니다.

1. 그런 다음 Campaign Classic에서 Netezza 외부 계정을 구성할 수 있습니다. 에서 **[!UICONTROL Explorer]**/ **[!UICONTROL Administration]** / **[!UICONTROL Platform]** /를 **[!UICONTROL External accounts]**&#x200B;클릭합니다.

1. 을 **[!UICONTROL New]** 클릭하고 **[!UICONTROL External database]** 으로 선택합니다 **[!UICONTROL Type]**.

1. 외부 계정을 구성하려면 다음을 **[!UICONTROL Netezza]** 지정해야 합니다.

   * **[!UICONTROL Type]**: 네테차

   * **[!UICONTROL Server]**: Netezza 서버의 URL

   * **[!UICONTROL Account]**: 사용자의 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Database]**: 데이터베이스 이름

>[!NOTE]
>
>자동으로 생성된 기본 키를 포함하는 스키마에 대한 작업은 고려되지 않습니다.
>
>테이블에 스키마에 정의된 첫 번째 인덱스의 **Organize on** 절을 사용합니다. 이 절은 Netezza와 함께 1-4개의 열로 제한되므로 이 인덱스는 4개 이상의 열을 포함할 수 없습니다.

## Oracle 액세스 권한 구성 {#configure-access-to-oracle}

FDA에서 Oracle 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 아래 추가 구성이 필요합니다.

### Linux용 {#for-linux-1}

1. Oracle 버전에 해당하는 Oracle 전체 클라이언트를 설치합니다.
1. TNS 정의를 설치에 추가합니다. 이렇게 하려면 /etc/oracle 저장소의 tnsnames. **ora** 파일에 지정합니다. 이 저장소가 없으면 만듭니다.

   그런 다음 새 TNS_ADMIN 환경 변수를 만듭니다. TNS_ADMIN=/etc/oracle을 내보내고 시스템을 다시 시작합니다.

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

### Windows {#for-windows-1}

1. Oracle 클라이언트를 설치합니다.
1. C:Oracle 폴더에서 TNS 정의를 **포함하는 tnsnames.ora** 파일을 생성합니다.

   C:Oracle을 값으로 사용하여 TNS_ADMIN 환경 변수를 추가하고 시스템을 다시 시작합니다.

## Sybase IQ에 대한 액세스 구성 {#configure-access-to-sybase-iq}

FDA에서 Sybase IQ 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 추가 구성이 필요합니다.

1. 원본 패키지가 서버에 있는지 확인합니다.
1. iq_odbc **를 설치합니다**. 설치가 끝날 때 오류가 발생할 수 있습니다. 이 오류는 무시될 수 있습니다.
1. iq_client_common을 **설치합니다**. 설치 마지막에 Java 오류가 발생할 수 있습니다. 이 오류는 무시될 수 있습니다.
1. ODBC 드라이버를 구성합니다. 구성은 표준 파일에서 수행할 수 있습니다. /etc/odbc.ini일반 매개 변수 및 드라이버 선언용 /etc/odbcinst.ini을 참조하십시오.

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

   * customer.sh 파일을 사용하여 경로를 선언할 경우: LD_LIBRARY_PATH 변수에 대해 /opt/sybase/IQ-16_0/lib64 경로를 추가합니다.
   * 그렇지 않은 경우 Unix 명령을 사용합니다.

1. 그런 다음 Campaign Classic에서 Sybase IQ 외부 계정을 구성할 수 있습니다. 에서 **[!UICONTROL Explorer]**/ **[!UICONTROL Administration]** / **[!UICONTROL Platform]** /를 **[!UICONTROL External accounts]**&#x200B;클릭합니다.

1. 을 **[!UICONTROL New]** 클릭하고 **[!UICONTROL External database]** 으로 선택합니다 **[!UICONTROL Type]**.

1. 외부 계정을 구성하려면 다음을 **[!UICONTROL Sybase IQ]** 지정해야 합니다.

   * **[!UICONTROL Type]**: ODBC(Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: 5단계에서 정의된 ODBC 연결(`<server_alias>`)에 해당합니다. 서버 자체의 이름이 아닐 수도 있습니다.

   * **[!UICONTROL Account]**: 사용자의 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Database]**: 데이터베이스 이름

>[!NOTE]
>
>Windows의 경우 Adobe Campaign 서버에 Sybase IQ 클라이언트를 설치하고 ODBC 연결을 만들어야 합니다. Adobe Campaign 서버(nlserver)가 Windows에서 서비스로 실행 중일 때 시스템 데이터 소스를 만들어야 합니다.

## 메타데이터 액세스 구성 {#configure-access-to-teradata}

FDA에서 Teradata 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 특정 추가 구성이 필요합니다. Teradata 데이터베이스를 구성하는 방법에 대한 자세한 내용은 이 [문서를 참조하십시오](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html).

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

   * **LD_LIBRARY_PATH**: /opt/teradata/client/15.10/lib64와 /opt/teradata/client/15.10/odbc_64/lib.
   * **ODBCINI**: odbc.ini 파일의 위치입니다(예: /etc/odbc.ini).
   * **NLSPATH**: opermsgs.cat 파일의 위치(/opt/teradata/client/15.10/msg/opermsgs.cat)

1. 그런 다음 Campaign Classic에서 Teradata 외부 계정을 구성할 수 있습니다. 에서 **[!UICONTROL Explorer]**/ **[!UICONTROL Administration]** / **[!UICONTROL Platform]** /를 **[!UICONTROL External accounts]**&#x200B;클릭합니다.

1. 을 **[!UICONTROL New]** 클릭하고 **[!UICONTROL External database]** 으로 선택합니다 **[!UICONTROL Type]**.

1. 외부 계정을 구성하려면 다음을 **[!UICONTROL Teradata]** 지정해야 합니다.

   * **[!UICONTROL Type]**: Teradata

   * **[!UICONTROL Server]**: Teradata 서버의 URL

   * **[!UICONTROL Account]**: 사용자의 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Database]**: 데이터베이스 이름

## SAP HANA에 대한 액세스 구성 {#configure-access-to-sap-hana}

FDA에서 SAP HANA 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 특정 추가 구성이 필요합니다.

1. 사용하는 운영 체제에 따라 SAP HANA용 ODBC 드라이버를 설치합니다.

   * **Linux용 hdb_client_linux.tgz** . 압축을 풀면 hdbinst 명령을 실행하고 지침에 따라 드라이버 설치를 완료하십시오.
   * **Windows용 hdb_client_windows.zip** . 파일의 압축을 풀고 실행 파일을 시작합니다. **hdbinst.exe**. 마법사 지침에 따라 드라이버 설치를 마칩니다.

1. ODBC 드라이버를 구성합니다. 구성은 표준 파일에서 수행할 수 있습니다. /etc/odbc.ini을 참조하십시오.

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

   * **LD_LIBRARY_PATH**: 여기에는 기본적으로 SAP Hana 클라이언트(/usr/sap/hdbclient/libodbcHDB.so)에 대한 링크가 포함되어야 합니다.
   * **ODBCINI**: odbc.ini 파일의 위치입니다(예: /etc/odbc.ini).

1. 그런 다음 Campaign Classic에서 SAP 하나 외부 계정을 구성할 수 있습니다. 에서 **[!UICONTROL Explorer]**/ **[!UICONTROL Administration]** / **[!UICONTROL Platform]** /를 **[!UICONTROL External accounts]**&#x200B;클릭합니다.

1. 을 **[!UICONTROL New]** 클릭하고 **[!UICONTROL External database]** 으로 선택합니다 **[!UICONTROL Type]**.

1. 외부 계정을 구성하려면 다음을 **[!UICONTROL SAP Hana]** 지정해야 합니다.

   * **[!UICONTROL Type]**: SAP 하나

   * **[!UICONTROL Server]**: SAP 하나 서버의 URL

   * **[!UICONTROL Account]**: 사용자의 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호
