---
solution: Campaign Classic
product: campaign
title: Vertica에 대한 액세스 구성
description: FDA에서 Vertica에 대한 액세스를 구성하는 방법을 알아보십시오.
audience: platform
content-type: reference
topic-tags: connectors
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 4%

---


# Vertica에 대한 액세스 구성 {#configure-fda-vertica}

![](../../assets/v7-only.svg)

Campaign **Federated Data Access** (FDA) 옵션을 사용하여 외부 데이터베이스에 저장된 정보를 처리합니다. 아래 절차에 따라 [!DNL Vertica]에 대한 액세스를 구성하십시오.

1. [CentOS](#vertica-centos), [Windows](#vertica-windows) 또는 [Debian](#vertica-debian)에서 [!DNL Vertica] 구성
1. Campaign에서 [!DNL Vertica] [외부 계정](#vertica-external)을 구성합니다


>[!NOTE]
>
>[!DNL Vertica] 커넥터는 하이브리드 및 온-프레미스 배포에 사용할 수 있습니다. 자세한 정보는 이 [페이지](../../installation/using/capability-matrix.md)를 참조하십시오.

![](assets/snowflake_3.png)

## Vertica on CentOS {#vertica-centos}

CentOS에서 [!DNL Vertica]을 구성하려면 아래 단계를 수행하십시오.

1. [!DNL Vertica]용 ODBC 드라이버를 다운로드합니다. [여기](https://www.vertica.com/download/vertica/client-drivers/) 를 클릭하고 최신 Linux RPM을 다운로드합니다.

1. 그러면 다음 명령을 사용하여 unixODBC를 설치해야 합니다.

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. 이전에 [!DNL Vertica] 서버를 설치한 경우에는 ODBC 드라이버가 이미 설치됩니다. 이 경우 다음과 같이 드라이브를 업데이트합니다.

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. 그런 다음 Adobe Campaign에서 [!DNL Vertica] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#vertica-external)을 참조하십시오.

## Windows의 Vertica {#vertica-windows}

1. Windows용 [ODBC 드라이버를 다운로드합니다](https://www.vertica.com/download/vertica/client-drivers/). Windows용 드라이버를 설치하려면 .NET Framework 3.5를 활성화해야 합니다. 그렇지 않으면 설치 마법사에서 자동으로 이 드라이버를 활성화하고 다운로드합니다.

1. Windows에서 ODBC 드라이버를 구성합니다. 자세한 정보는 이 [페이지](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)를 참조하십시오

1. 그런 다음 Adobe Campaign에서 [!DNL Vertica] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#vertical-external)을 참조하십시오.

## 베르티카 온 데비안 {#vertica-debian}

1. [!DNL Vertica]용 ODBC 드라이버를 다운로드합니다. [다운로드 ](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) 재시작 을 클릭합니다.

1. 그러면 다음 명령을 사용하여 unixODBC를 설치해야 합니다.

   ```
   apt-get install unixODBC
   ```

1. 이전에 [!DNL Vertica] 서버를 설치한 경우에는 ODBC 드라이버가 이미 설치됩니다. 이 경우 다음과 같이 드라이브를 업데이트합니다.

   ```
   #Switch to root
   sudo su
   
   #Move or copy the downloaded file and change to /root
   mv vertica_9.3..xx_odbc_x86_64_linux.tar.gz /
   cd /
   
   #Uncompress the file you downloaded
   tar vzxf vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Remove the tar.gz since it is not needed anymore
   rm vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. 그런 다음 Adobe Campaign에서 [!DNL Vertica] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#vertica-external)을 참조하십시오.

## Vertica 외부 계정 {#vertica-external}

Campaign 인스턴스를 [!DNL Vertica] 외부 데이터베이스에 연결하려면 [!DNL Vertica] 외부 계정을 만들어야 합니다.

1. Campaign **[!UICONTROL Explorer]**&#x200B;에서 **[!UICONTROL Administration]** &#39; **[!UICONTROL Platform]**&#39; **[!UICONTROL External accounts]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

1. 외부 계정의 **[!UICONTROL Type]**(으)로 **[!UICONTROL External database]**&#x200B;을(를) 선택합니다.

1. **[!UICONTROL Vertica]** 외부 계정을 구성합니다. 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: 서버의  [!DNL Vertica] URL

   * **[!UICONTROL Account]**: 사용자의 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Database]**: 데이터베이스 이름
   ![](assets/vertica.png)
