---
product: campaign
title: Synapse에 대한 액세스 구성
description: FDA에서 Synapse에 대한 액세스를 구성하는 방법을 배웁니다.
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 59d0277a-7588-4504-94e3-50f87b60da8a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 2%

---

# azure synapse 액세스 구성 {#configure-access-to-azure-synapse}



캠페인 사용 [페더레이션 데이터 액세스](../../installation/using/about-fda.md) (FDA) 옵션을 사용하여 외부 데이터베이스에 저장된 정보를 처리합니다. 아래 절차에 따라 액세스 권한을 구성하십시오 **Microsoft Azure synapse 분석**.

1. azure synapse 구성 [CentOS](#azure-centos), [Windows](#azure-windows) 또는 [데비안](#azure-debian)
1. azure synapse 구성 [외부 계정](#azure-external) in Campaign

## CentOS의 azure synapse {#azure-centos}

>[!CAUTION]
>
>* ODBC 드라이버를 설치하려면 루트 권한이 필요합니다.
>* Microsoft에서 제공하는 Red Hat Enterprise ODBC 드라이버는 CentOS와 함께 사용하여 SQL Server에 연결할 수도 있습니다.
>* 버전 13.0은 Red Hat 6 및 7에서 작동합니다.


CentOS에서 Azure synapse을 구성하려면 아래 단계를 수행하십시오.

1. 먼저 ODBC 드라이버를 설치합니다. 여기에서는 찾을 수 있습니다 [페이지](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

   >[!NOTE]
   >
   >ODBC 드라이버 버전 13에만 사용할 수 있습니다.

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

1. Campaign에서 다음을 구성할 수 있습니다 [!DNL Azure Synapse] 외부 계정. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#azure-external).

1. azure synapse Analytics는 TCP 1433 포트를 통해 통신하므로 방화벽에서 이 포트를 열어야 합니다. 다음 명령을 사용하십시오.

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >Analytics Azure synapse 측에서 통신할 수 있도록 하려면 공개 IP를에 추가해야 할 수 허용 목록에 추가하다 있습니다. 이렇게 하려면 다음을 참조하십시오 [Azure 설명서](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

1. iptable의 경우 다음 명령을 실행합니다.

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

## Windows의 azure synapse {#azure-windows}

>[!NOTE]
>
>ODBC 드라이버 버전 13에만 사용할 수 있지만 Adobe Campaign Classic에서는 SQL Server Native Client 드라이버 11.0 및 10.0을 사용할 수도 있습니다.

Windows에서 Azure synapse을 구성하려면

1. 먼저 Microsoft ODBC 드라이버를 설치합니다. 여기에서 찾을 수 있습니다 [이 페이지](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

1. 설치할 파일 선택:

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. ODBC 드라이버가 설치되면 필요한 경우 테스트할 수 있습니다. 자세한 정보는 이 [페이지](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server)를 참조하십시오.

1. 그런 다음 Campaign Classic에서 [!DNL Azure Synapse] 외부 계정. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#azure-external).

1. azure synapse Analytics는 TCP 1433 포트를 통해 통신하므로 Windows Defender Firewall에서 이 포트를 열어야 합니다. 자세한 내용은 [Windows 설명서](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

## 데비안 azure synapse {#azure-debian}

**필수 구성 요소:**

* ODBC 드라이버를 설치하려면 루트 권한이 필요합니다.
* msodbcsql 패키지를 설치하려면 curl이 필요합니다. 설치되어 있지 않으면 다음 명령을 실행합니다.

   ```
   sudo apt-get install curl
   ```

Debian에서 Azure synapse을 구성하려면 다음을 수행하십시오.

1. 먼저 SQL Server용 Microsoft ODBC 드라이버를 설치합니다. 다음 명령을 사용하여 SQL Server용 ODBC 드라이버 13.1을 설치합니다.

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. 다음 오류가 발생하면 **&quot;메서드 드라이버 /usr/lib/apt/methods/https를 찾을 수 없습니다.&quot;** 호출 시 **sudo apt get update**&#x200B;로 지정하는 경우 다음 명령을 실행해야 합니다.

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. 이제 다음 명령을 사용하여 mssql-tools를 설치해야 합니다. 대량 복사 프로그램(또는 BCP) 유틸리티를 사용하고 쿼리를 실행하려면 Mssq-tools가 필요합니다.

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

1. 이제 Campaign Classic에서 다음을 구성할 수 있습니다 [!DNL Azure Synapse] 외부 계정. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#azure-external).

1. Debian에서 iptable을 구성하여 Analytics와 연결하도록 하려면 다음 명령을 사용하여 호스트 이름에 대한 아웃바운드 TCP 1433 포트를 활성화합니다.

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >Analytics Azure synapse 측에서 통신할 수 있도록 하려면 공개 IP를에 추가해야 할 수 허용 목록에 추가하다 있습니다. 이렇게 하려면 다음을 참조하십시오 [Azure 설명서](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

## 외부 계정 azure synapse {#azure-external}

다음 [!DNL Azure Synapse] 외부 계정을 사용하면 Campaign 인스턴스를 Azure synapse 외부 데이터베이스에 연결할 수 있습니다.

을(를) 만들려면 [!DNL Azure Synapse] 외부 계정은 아래 단계를 수행합니다.

1. Campaign에서 **[!UICONTROL Explorer]**&#x200B;를 클릭합니다. **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

1. 선택 **[!UICONTROL External database]** 외부 계정 **[!UICONTROL Type]**.

   ![](assets/azure_1.png)

1. 아래 **[!UICONTROL Configuration]**, 선택 **[!UICONTROL Azure Synapse Analytics]** 에서 **[!UICONTROL Type]** 드롭다운.

   ![](assets/azure_2.png)

1. 구성 [!DNL Azure Synapse] 외부 계정:

   * 표준 인증의 경우 다음을 지정해야 합니다.

      * **[!UICONTROL Server]**: azure synapse 서버의 URL

      * **[!UICONTROL Account]**: 사용자의 이름

      * **[!UICONTROL Password]**: 사용자 계정 암호

      * **[!UICONTROL Database]**: 데이터베이스 이름

      ![](assets/azure_3.png)

   * 시스템 지정 관리 ID 인증의 경우 다음을 지정해야 합니다.

      * **[!UICONTROL Server]**: azure synapse 서버의 URL

      * **[!UICONTROL Database]**: 데이터베이스 이름

      * **[!UICONTROL Options]**: 다음 구문을 추가합니다 `Authentication=ActiveDirectoryMsi`

      ![](assets/azure_4.png)



1. **[!UICONTROL Save]**&#x200B;를 클릭합니다.

커넥터는 다음 옵션을 지원합니다.

| 옵션 | 설명 |
|---|---|
| 인증 | 커넥터에서 지원하는 인증 유형입니다. 현재 지원되는 값: ActiveDirectoryMSI입니다. </br>자세한 내용은 [SQL 문서](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings) (°8 연결 문자열 예). |
