---
product: campaign
title: Microsoft SQL Server 액세스 구성
description: Microsoft SQL Server에 대한 액세스를 구성하는 방법 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 65ab4577-3126-4579-8fcc-e93772ebd1e8
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 1%

---

# Microsoft SQL Server 액세스 구성 {#configure-fda-sql}



Campaign 사용 **페더레이션 데이터 액세스** (FDA) 외부 Microsoft SQL Server 데이터베이스에 저장된 정보를 처리하는 옵션 액세스 권한을 구성하려면 아래 단계를 따르십시오. [!DNL Microsoft SQL Server].

1. 구성 [!DNL Microsoft SQL Server] 날짜 [센트OS](#sql-centos).
1. 구성 [!DNL Microsoft SQL Server] 날짜 [리눅스](#sql-linux).
1. 구성 [!DNL Microsoft SQL Server] 날짜 [Windows](#sql-windows).
1. 구성 [!DNL Microsoft SQL Server] [외부 계정](#sql-external) 캠페인에서

## CentOS의 Microsoft SQL Server {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server] 는 CentOS 7 및 6에서 사용할 수 있습니다.

구성하려면 [!DNL Microsoft SQL Server] CentOS에서 아래 단계를 수행합니다.

1. 다음 명령을 사용하여 SQL ODBC 드라이버를 다운로드하고 설치합니다.

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. 그런 다음 Adobe Campaign에서 다음을 구성할 수 있습니다. [!DNL Microsoft SQL Server] 외부 계정입니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#sql-external).

## Linux의 Microsoft SQL Server {#sql-linux}

>[!NOTE]
>
> 이전 버전의 Adobe Campaign(7.2.1 이전)를 실행하는 경우 설치해야 합니다 `unix ODBC drivers`.

1. 에서 MS ODBC 드라이버 다운로드 [이 페이지](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/).

1. 루트 사용자로 다음 명령을 실행합니다.

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. 그런 다음 Adobe Campaign에서 다음을 구성할 수 있습니다. [!DNL Microsoft SQL Server] 외부 계정입니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#sql-external).

## Windows의 Microsoft SQL Server {#sql-windows}

구성하려면 [!DNL Microsoft SQL Server] Windows에서:

1. Windows에서 **[!UICONTROL Control Panel]** &#39;>&#39; **[!UICONTROL System and Security]** &#39;>&#39; **[!UICONTROL Administrative Tools]**&#39;>&#39; **[!UICONTROL ODBC Data Sources (64-bit)]**.

1. 다음에서 **[!UICONTROL ODBC Data Sources (64-bit)]** 새 창에서 다음을 클릭: **[!UICONTROL Add...]**.

1. SQL Server Native Client v11이 **[!UICONTROL Create New Data Source]** 창.

1. SQL Server Native Client가 나열되지 않은 경우 [이 페이지](https://www.microsoft.com/en-my/download/details.aspx?id=36434).

1. 그런 다음 Adobe Campaign에서 다음을 구성할 수 있습니다. [!DNL Microsoft SQL Server] 외부 계정입니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#sql-external).

## Microsoft SQL Server 외부 계정 {#sql-external}

다음을 만들어야 합니다. [!DNL Microsoft SQL Server] Campaign 인스턴스를 [!DNL Microsoft SQL Server] 외부 데이터베이스.

1. 출처: Campaign **[!UICONTROL Explorer]**, 클릭 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

1. 선택 **[!UICONTROL External database]** 외부 계정으로 **[!UICONTROL Type]**.

1. 아래 **[!UICONTROL Configuration]**, 선택 [!DNL Microsoft SQL Server] 다음에서 **[!UICONTROL Type]** 드롭다운.

   ![](assets/sql.png)

1. 구성 **[!UICONTROL Microsoft SQL Server]** 외부 계정 인증:

   * **[!UICONTROL Server]**: 의 URL [!DNL Microsoft SQL Server] 서버입니다.

   * **[!UICONTROL Account]**: 사용자의 이름입니다.

   * **[!UICONTROL Password]**: 사용자 계정 암호.

   * **[!UICONTROL Database]**: 데이터베이스 이름(선택 사항).

   * **[!UICONTROL Timezone]**: 표준 시간대 설정 [!DNL Microsoft SQL Server]. [자세히 알아보기](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. 다음을 클릭합니다. **[!UICONTROL Parameters]** 탭을 클릭한 다음 **[!UICONTROL Deploy functions]** 단추를 클릭하여 함수를 만듭니다.

   >[!NOTE]
   >
   >모든 함수를 사용할 수 있으려면 원격 데이터베이스에 Adobe Campaign SQL 함수를 만들어야 합니다. 자세한 내용은 다음을 참조하십시오. [페이지](../../configuration/using/adding-additional-sql-functions.md).

1. 클릭 **[!UICONTROL Save]** 구성이 완료되면.

커넥터는 다음 옵션을 지원합니다.

| 옵션 | 설명 |
|---|---|
| 인증 | 커넥터에서 지원하는 인증 유형입니다. 현재 지원되는 값: ActiveDirectoryMSI. <br> 자세한 내용은 의 예제 8 을 참조하십시오. [Microsoft 설명서](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings). |
| 암호화 | 연결에서 네트워크를 통해 TLS 암호화를 사용하는지 여부를 지정합니다. 가능한 값은 다음과 같습니다 **예/필수(18.0 이상)**, **no/선택 사항(18.0 이상)**, 및 **strict(18.0 이상)**. 기본값은 로 설정되어 있습니다. **예** 버전 18.0 이상 및 **아니요** 이전 버전에서. <br>자세한 내용은 다음을 참조하십시오. [Microsoft 설명서](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt). |
| 트러스트 서버 인증서 | 과 함께 사용할 경우 자체 서명된 서버 인증서를 사용하여 암호화를 활성화합니다. **암호화**. <br>허용된 값: **예** 또는 **아니요** (기본값은 서버 인증서의 유효성을 검사함을 의미합니다.) |
