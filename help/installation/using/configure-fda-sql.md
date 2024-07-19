---
product: campaign
title: Microsoft SQL Server 액세스 구성
description: Microsoft SQL Server에 대한 액세스를 구성하는 방법 알아보기
feature: Installation, Federated Data Access
exl-id: 65ab4577-3126-4579-8fcc-e93772ebd1e8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 1%

---

# Microsoft SQL Server 액세스 구성 {#configure-fda-sql}



Campaign **FDA(Federated Data Access**) 옵션을 사용하여 외부 Microsoft SQL Server 데이터베이스에 저장된 정보를 처리합니다. [!DNL Microsoft SQL Server]에 대한 액세스를 구성하려면 아래 단계를 따르십시오.

1. [CentOS](#sql-centos)에서 [!DNL Microsoft SQL Server]을(를) 구성합니다.
1. [Linux](#sql-linux)에서 [!DNL Microsoft SQL Server]을(를) 구성합니다.
1. [Windows](#sql-windows)에서 [!DNL Microsoft SQL Server]을(를) 구성합니다.
1. Campaign에서 [!DNL Microsoft SQL Server] [외부 계정](#sql-external) 구성

## CentOS의 Microsoft SQL Server {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server]은(는) CentOS 7 및 6에서 사용할 수 있습니다.

CentOS에서 [!DNL Microsoft SQL Server]을(를) 구성하려면 아래 단계를 수행하십시오.

1. 다음 명령을 사용하여 SQL ODBC 드라이버를 다운로드하고 설치합니다.

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. 그런 다음 Adobe Campaign에서 [!DNL Microsoft SQL Server] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#sql-external)을 참조하세요.

## Linux의 Microsoft SQL Server {#sql-linux}

>[!NOTE]
>
> 이전 버전의 Adobe Campaign(7.2.1 이전)를 실행하는 경우 `unix ODBC drivers`을(를) 설치해야 합니다.

1. [이 페이지](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/)에서 MS ODBC 드라이버를 다운로드합니다.

1. 루트 사용자로 다음 명령을 실행합니다.

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. 그런 다음 Adobe Campaign에서 [!DNL Microsoft SQL Server] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#sql-external)을 참조하세요.

## Windows의 Microsoft SQL Server {#sql-windows}

Windows에서 [!DNL Microsoft SQL Server]을(를) 구성하려면

1. Windows에서 **[!UICONTROL Control Panel]** &#39;>&#39; **[!UICONTROL System and Security]** &#39;>&#39; **[!UICONTROL Administrative Tools]**&#39;>&#39; **[!UICONTROL ODBC Data Sources (64-bit)]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL ODBC Data Sources (64-bit)]** 새 창에서 **[!UICONTROL Add...]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL Create New Data Source]** 창에 SQL Server Native Client v11이 나열되어 있는지 확인하십시오.

1. SQL Server Native Client가 목록에 없으면 [이 페이지](https://www.microsoft.com/en-my/download/details.aspx?id=36434)에서 다운로드할 수 있습니다.

1. 그런 다음 Adobe Campaign에서 [!DNL Microsoft SQL Server] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#sql-external)을 참조하세요.

## Microsoft SQL Server 외부 계정 {#sql-external}

Campaign 인스턴스를 [!DNL Microsoft SQL Server] 외부 데이터베이스에 연결하려면 [!DNL Microsoft SQL Server] 외부 계정을 만들어야 합니다.

1. **[!UICONTROL Explorer]** 캠페인에서 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

1. **[!UICONTROL External database]**&#x200B;을(를) 외부 계정의 **[!UICONTROL Type]**(으)로 선택합니다.

1. **[!UICONTROL Configuration]**&#x200B;의 **[!UICONTROL Type]** 드롭다운에서 [!DNL Microsoft SQL Server]을(를) 선택합니다.

   ![](assets/sql.png)

1. **[!UICONTROL Microsoft SQL Server]** 외부 계정 인증을 구성합니다.

   * **[!UICONTROL Server]**: [!DNL Microsoft SQL Server] 서버의 URL.

   * **[!UICONTROL Account]**: 사용자의 이름입니다.

   * **[!UICONTROL Password]**: 사용자 계정 암호입니다.

   * **[!UICONTROL Database]**: 데이터베이스의 이름입니다(선택 사항).

   * **[!UICONTROL Timezone]**: [!DNL Microsoft SQL Server]에 설정된 시간대입니다. [자세히 알아보기](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. **[!UICONTROL Parameters]** 탭을 클릭한 다음 **[!UICONTROL Deploy functions]** 단추를 클릭하여 함수를 만듭니다.

   >[!NOTE]
   >
   >모든 함수를 사용할 수 있으려면 원격 데이터베이스에 Adobe Campaign SQL 함수를 만들어야 합니다. 자세한 정보는 이 [페이지](../../configuration/using/adding-additional-sql-functions.md)를 참조하세요.

1. 구성이 완료되면 **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

커넥터는 다음 옵션을 지원합니다.

| 옵션 | 설명 |
|---|---|
| 인증 | 커넥터에서 지원하는 인증 유형입니다. 현재 지원되는 값: ActiveDirectoryMSI. <br> 자세한 내용은 [Microsoft 설명서](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings)의 예제 8을 참조하십시오. |
| 암호화 | 연결에서 네트워크를 통해 TLS 암호화를 사용하는지 여부를 지정합니다. 가능한 값은 **예/필수(18.0 이상)**, **아니요/선택 사항(18.0 이상)** 및 **엄격(18.0 이상)**&#x200B;입니다. 기본값은 버전 18.0 이상에서는 **yes**, 이전 버전에서는 **no**&#x200B;로 설정되어 있습니다. <br>자세한 내용은 [Microsoft 설명서](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt)를 참조하세요. |
| 트러스트 서버 인증서 | **Encrypt**&#x200B;와 함께 사용할 경우 자체 서명된 서버 인증서를 사용하여 암호화를 사용하도록 설정합니다. <br>허용되는 값: **예** 또는 **아니요**(기본값: 서버 인증서의 유효성을 검사함). |
