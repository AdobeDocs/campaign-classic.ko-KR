---
product: campaign
title: Synapse 액세스 구성
description: FDA에서 Synapse에 대한 액세스를 구성하는 방법 알아보기
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 59d0277a-7588-4504-94e3-50f87b60da8a
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 2%

---

# azure synapse 액세스 구성 {#configure-access-to-azure-synapse}



외부 데이터베이스에 저장된 정보를 처리하려면 Campaign [FDA(Federated Data Access](../../installation/using/about-fda.md)) 옵션을 사용하십시오. **Microsoft Azure synapse 분석**&#x200B;에 대한 액세스를 구성하려면 아래 단계를 따르십시오.

1. [CentOS](#azure-centos), [Windows](#azure-windows) 또는 [Debian](#azure-debian)에서 Azure synapse 구성
1. Campaign에서 Azure synapse [외부 계정](#azure-external) 구성

## CentOS의 azure synapse {#azure-centos}

>[!CAUTION]
>
>* ODBC 드라이버를 설치하려면 루트 권한이 필요합니다.
>* Microsoft에서 제공하는 Red Hat Enterprise ODBC 드라이버는 CentOS와 함께 사용하여 SQL Server에 연결할 수도 있습니다.
>* 버전 13.0은 Red Hat 6 및 7에서 작동합니다.

CentOS에서 Azure synapse을 구성하려면 아래 단계를 따르십시오.

1. 먼저 ODBC 드라이버를 설치합니다. 이 [페이지](https://www.microsoft.com/en-us/download/details.aspx?id=50420)에서 찾을 수 있습니다.

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

1. 드라이버를 설치한 후 ODBC 드라이버를 테스트하고 확인하고 필요한 경우 데이터베이스를 쿼리할 수 있습니다. 다음 명령을 실행합니다.

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. 그런 다음 Campaign에서 [!DNL Azure Synapse] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#azure-external)을 참조하세요.

1. azure synapse Analytics는 TCP 1433 포트를 통해 통신하므로 방화벽에서 이 포트를 열어야 합니다. 다음 명령을 사용하십시오.

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >azure synapse 분석 측에서 통신을 허용하려면 공용 허용 목록에 추가하다에 IP를 추가해야 할 수 있습니다. 이렇게 하려면 [Azure 설명서](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)를 참조하세요.

1. iptable의 경우 다음 명령을 실행합니다.

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

## Windows의 azure synapse {#azure-windows}

>[!NOTE]
>
>이 드라이버는 ODBC 드라이버 버전 13에만 사용할 수 있지만 Adobe Campaign Classic은 SQL Server Native Client 드라이버 11.0과 10.0도 사용할 수 있습니다.

Windows에서 Azure synapse을 구성하려면:

1. 먼저 Microsoft ODBC 드라이버를 설치합니다. [이 페이지](https://www.microsoft.com/en-us/download/details.aspx?id=50420)에서 찾을 수 있습니다.

1. 설치할 다음 파일을 선택하십시오.

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. ODBC 드라이버가 설치되면 필요한 경우 테스트할 수 있습니다. 자세한 정보는 이 [페이지](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server)를 참조하십시오.

1. 그런 다음 Campaign Classic에서 [!DNL Azure Synapse] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#azure-external)을 참조하세요.

1. azure synapse Analytics는 TCP 1433 포트를 통해 통신하므로 Windows Defender 방화벽에서 이 포트를 열어야 합니다. 자세한 내용은 [Windows 설명서](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule)를 참조하세요.

## Debian azure synapse {#azure-debian}

**필수 구성 요소:**

* ODBC 드라이버를 설치하려면 루트 권한이 필요합니다.
* msodbcsql 패키지를 설치하려면 Curl이 필요합니다. 설치되지 않은 경우 다음 명령을 실행합니다.

  ```
  sudo apt-get install curl
  ```

Debian에서 Azure synapse을 구성하려면:

1. 먼저 SQL Server용 Microsoft ODBC 드라이버를 설치합니다. 다음 명령을 사용하여 SQL Server용 ODBC 드라이버 13.1을 설치합니다.

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. 다음 오류 **이(가) 발생하면** sudo apt-get update **를 호출할 때 메서드 드라이버 /usr/lib/apt/methods/https를 찾을 수 없습니다.&quot;** 명령을 실행해야 합니다.

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. 이제 다음 명령을 사용하여 mssql-tools 를 설치해야 합니다. Mssq-tools 는 Bulk Copy 프로그램 (또는 BCP) 유틸리티를 사용하고 쿼리를 실행하는 데 필요합니다.

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

1. 드라이버를 설치한 후 ODBC 드라이버를 테스트하고 확인하고 필요한 경우 데이터베이스를 쿼리할 수 있습니다. 다음 명령을 실행합니다.

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. 이제 Campaign Classic에서 [!DNL Azure Synapse] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#azure-external)을 참조하세요.

1. Debian에서 iptables를 구성하여 Azure synapse Analytics와 연결하려면 다음 명령을 사용하여 호스트 이름에 대한 아웃바운드 TCP 1433 포트를 활성화합니다.

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >azure synapse 분석 측에서 통신을 허용하려면 공용 허용 목록에 추가하다에 IP를 추가해야 할 수 있습니다. 이렇게 하려면 [Azure 설명서](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)를 참조하세요.

## 외부 계정 azure synapse {#azure-external}

[!DNL Azure Synapse] 외부 계정을 사용하면 Campaign 인스턴스를 Azure synapse 외부 데이터베이스에 연결할 수 있습니다.

[!DNL Azure Synapse] 외부 계정을 만들려면 아래 단계를 수행하십시오.

1. **[!UICONTROL Explorer]** 캠페인에서 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

1. **[!UICONTROL External database]**&#x200B;을(를) 외부 계정의 **[!UICONTROL Type]**(으)로 선택합니다.

   ![](assets/azure_1.png)

1. **[!UICONTROL Configuration]**&#x200B;의 **[!UICONTROL Type]** 드롭다운에서 **[!UICONTROL Azure Synapse Analytics]**&#x200B;을(를) 선택합니다.

   ![](assets/azure_2.png)

1. [!DNL Azure Synapse] 외부 계정을 구성합니다.

   * 표준 인증의 경우 다음을 지정해야 합니다.

      * **[!UICONTROL Server]**: Azure synapse 서버의 URL

      * **[!UICONTROL Account]**: 사용자 이름

      * **[!UICONTROL Password]**: 사용자 계정 암호

      * **[!UICONTROL Database]**: 데이터베이스 이름

     ![](assets/azure_3.png)

   * 시스템에서 할당한 관리 ID 인증의 경우 다음을 지정해야 합니다.

      * **[!UICONTROL Server]**: Azure synapse 서버의 URL

      * **[!UICONTROL Database]**: 데이터베이스 이름

      * **[!UICONTROL Options]**: 다음 구문을 추가하십시오. `Authentication=ActiveDirectoryMsi`

     ![](assets/azure_4.png)

1. **[!UICONTROL Save]**&#x200B;를 클릭합니다.

커넥터는 다음 옵션을 지원합니다.

| 옵션 | 설명 |
|---|---|
| 인증 | 커넥터에서 지원하는 인증 유형입니다. 현재 지원되는 값: ActiveDirectoryMSI. </br>자세한 내용은 [SQL 문서](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings)(연결 문자열 n°8 예제)를 참조하십시오. |
