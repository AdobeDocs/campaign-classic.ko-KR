---
product: campaign
title: Google BigQuery에 대한 액세스 구성
description: FDA에서 Google BigQuery에 대한 액세스를 구성하는 방법을 배웁니다.
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 0cfe8439007b56014eba497c511904c4f11b39ce
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 2%

---

# Google BigQuery에 대한 액세스 구성 {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

Adobe Campaign Classic **Federated Data Access** (FDA) 옵션을 사용하여 외부 데이터베이스에 저장된 정보를 처리합니다. 아래 절차에 따라 [!DNL Google BigQuery]에 대한 액세스를 구성하십시오.

1. [Windows](#google-windows) 또는 [Linux](#google-linux)에서 [!DNL Google BigQuery] 구성
1. Adobe Campaign Classic에서 [!DNL Google BigQuery] [외부 계정](#google-external)을 구성합니다
1. [Windows](#bulk-load-windows) 또는 [Linux](#bulk-load-linux)에서 [!DNL Google BigQuery] 커넥터 벌크 로드를 설정합니다.

>[!NOTE]
>
> [!DNL Google BigQuery] 커넥터는 하이브리드 및 온-프레미스 배포에 사용할 수 있습니다. 자세한 정보는 이 [페이지](../../installation/using/capability-matrix.md)를 참조하십시오.

![](assets/snowflake_3.png)

## Windows의 Google BigQuery {#google-windows}

### Windows에서 드라이버 설정 {#driver-window}

1. Windows용 [ODBC 드라이버를 다운로드합니다](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Windows에서 ODBC 드라이버를 구성합니다. 자세한 정보는 이 [페이지](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf)를 참조하십시오.

1. [!DNL Google BigQuery] 커넥터가 작동하려면 Adobe Campaign Classic에서 연결할 다음 매개 변수가 필요합니다.

   * **[!UICONTROL Project]**: 기존 프로젝트를 만들거나 사용합니다.

      자세한 내용은 이 [page](https://cloud.google.com/resource-manager/docs/creating-managing-projects)을 참조하십시오.

   * **[!UICONTROL Service account]**: 서비스 계정을 만듭니다.

      자세한 내용은 이 [page](https://cloud.google.com/iam/docs/creating-managing-service-accounts)을 참조하십시오.

   * **[!UICONTROL Key File Path]**: ODBC **[!UICONTROL Service account]** 를  **[!UICONTROL Key File]** 통해  [!DNL Google BigQuery] 연결하려면 가 필요합니다.

      자세한 내용은 이 [page](https://cloud.google.com/iam/docs/creating-managing-service-account-keys)을 참조하십시오.

   * **[!UICONTROL Dataset]**:  **[!UICONTROL Dataset]** 은 ODBC 연결에 선택 사항입니다. 모든 쿼리는 테이블이 있는 데이터 세트를 제공해야 하므로 Adobe Campaign Classic의 [!DNL Google BigQuery] FDA 커넥터에 **[!UICONTROL Dataset]**&#x200B;을(를) 지정해야 합니다.

      자세한 내용은 이 [page](https://cloud.google.com/bigquery/docs/datasets)을 참조하십시오.

1. 그런 다음 Adobe Campaign Classic에서 [!DNL Google BigQuery] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#google-external)을 참조하십시오.

### Windows에서 벌크 로드 설정 {#bulk-load-window}

>[!NOTE]
>
>Google Cloud SDK가 작동하려면 Python이 설치되어 있어야 합니다.
>
>Python3를 사용하는 것이 좋습니다. 이 [page](https://www.python.org/downloads/)을 참조하십시오.

벌크 로드 유틸리티를 사용하면 Google Cloud SDK를 통해 보다 신속하게 전송할 수 있습니다.

1. 이 [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives)에서 Windows 64비트(x86_64) 아카이브를 다운로드하여 해당 디렉터리에 추출합니다.

1. `google-cloud-sdk\install.sh` 스크립트를 실행합니다. 경로 변수의 설정을 수락해야 합니다.

1. 설치 후 경로 변수 `...\google-cloud-sdk\bin`이(가) 설정되어 있는지 확인합니다. 없는 경우 수동으로 추가합니다.

1. `..\google-cloud-sdk\bin\bq.cmd` 파일에서 `CLOUDSDK_PYTHON` 로컬 변수를 추가하여 Python 설치 위치로 리디렉션합니다.

   예제:

   ![](assets/google-big-query_1.png)

1. 변경 사항을 고려하여 Adobe Campaign Classic을 다시 시작합니다.

## Linux의 Google BigQuery {#google-linux}

### Linux에서 드라이버 설정 {#driver-linux}

1. ODBC 드라이버를 설치하기 전에 시스템을 업데이트해야 합니다. Linux 또는 CentOS에서 다음 명령을 실행합니다.

   ```
   yum update
   # install unixODBC driver manager
   yum install unixODBC
   ```

1. 그러면 다음 명령을 사용하여 unixODBC 드라이버 관리자를 설치해야 합니다.

   ```
   # switch to root user
   sudo su
   ```

   Debian에서:

   ```
   apt-get update
   apt-get upgrade
   # install unixODBC driver manager
   apt-get install unixODBC
   ```

1. [Magnitude Simba Linux ODBC 드라이버(.tar.gz)](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers)를 다운로드합니다. 그런 다음 대상 파일을 컴퓨터의 임시 폴더로 전달하거나 wget 명령을 사용합니다.

   ```
   # in this example driver version is 2.3.1.1001
   wget https://storage.googleapis.com/simba-bq-release/odbc/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux.tar.gz
   ```

1. 기본 대상 파일을 다음과 같이 추출합니다. 여기서 **TarballName**&#x200B;은 드라이버를 포함하는 타볼 패키지의 이름입니다.

   ```
   tar --directory=/tmp -zxvf [TarballName]
   ```

1. 추출한 폴더에 액세스하여 드라이버 버전에 해당하는 내부 타겟 파일을 추출합니다. 다음 BigQueryDriver 예에서 다른 임시 폴더에 설치합니다.

   ```
   mkdir /tmp/BigQueryDriver/
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   tar --directory=/tmp/BigQueryDriver/ -zxvf SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version].tar.gz
   ```

1. 기본 대상 파일이 추출된 임시 위치에 액세스하고 `GoogleBigQueryODBC.did` 및 `setup/simba.googlebigqueryodbc.ini` 파일을 이전 단계에서 만든 새 폴더에 복사합니다.

   ```
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   cp GoogleBigQueryODBC.did /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   cp setup/simba.googlebigqueryodbc.ini /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   ```

1. 다음과 같이 설치 디렉토리를 만듭니다.

   ```
   mkdir -p /opt/simba/googlebigqueryodbc/
   ```

1. 디렉토리의 내용을 새 설치 디렉토리에 복사합니다.

   ```
   cp -r /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/* /opt/simba/googlebigqueryodbc/
   ```

1. 설치 디렉토리의 `<INSTALLDIR>`을 `simba.googlebigqueryodbc.ini`의 `/opt/simba/googlebigqueryodbc`으로 바꿉니다.

   ```
   cd /opt/simba/googlebigqueryodbc/lib/
   sed -i 's/<INSTALLDIR>/\/opt\/simba\/googlebigqueryodbc/g' simba.googlebigqueryodbc.ini
   ```

1. `DriverManagerEncoding`을 UTF-16으로 변경하고 `simba.googlebigqueryodbc.ini`에서 `SwapFilePath`을(를) 변경합니다. 필요한 경우 로깅 설정을 변경할 수도 있습니다.

   다음은 업데이트된 드라이버 전체 구성 파일의 예입니다.

   ```
   # /opt/simba/googlebigqueryodbc/lib/simba.googlebigqueryodbc.ini
   [Driver]
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=opt/simba/googlebigqueryodbc/ErrorMessages
   LogLevel=6
   LogPath=/tmp
   SwapFilePath=/tmp
   ```

1. 시스템 드라이버 파일 또는 현재 `odbcinst.ini` 파일을 사용하는 경우 `/etc/odbcinst.ini`을 구성하여 Google BigQuery 드라이버 위치 `/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb[Bitness].so`를 가리킵니다.

   예제:

   ```
   # /etc/odbcinst.ini
   # Make sure to use Simba ODBC Driver for Google BigQuery as a driver name.
   
   [ODBC Drivers]
   Simba ODBC Driver for Google BigQuery=Installed
   
   [Simba ODBC Driver for Google BigQuery]
   Description=Simba ODBC Driver for Google BigQuery(64-bit)
   Driver=/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   ```

1. unixODBC 드라이버 관리자 라이브러리의 위치를 찾고 `unixODBC` 및 `googlebigqueryodbc` 라이브러리 경로를 `LD_LIBRARY_PATH environment` 변수에 추가합니다.

   ```
   find / -name 'lib*odbc*.so*' -print
   #output:
   /usr/lib/x86_64-linux-gnu/libodbccr.so.2
   /usr/lib/x86_64-linux-gnu/libodbcinst.so.2.0.0
   /usr/lib/x86_64-linux-gnu/libodbccr.so.1
   .
   .
   /opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   
   #the command would look like this
   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/simba/googlebigqueryodbc:/usr/lib
   ```

1. 그런 다음 Adobe Campaign Classic에서 [!DNL Google BigQuery] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#google-external)을 참조하십시오.

### Linux에서 벌크 로드 설정 {#bulk-load-linux}

>[!NOTE]
>
>Google Cloud SDK가 작동하려면 Python이 설치되어 있어야 합니다.
>
>Python3를 사용하는 것이 좋습니다. 이 [page](https://www.python.org/downloads/)을 참조하십시오.

벌크 로드 유틸리티를 사용하면 Google Cloud SDK를 통해 보다 신속하게 전송할 수 있습니다.

1. 이 [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives)에 있는 Linux 64비트(x86_64) 아카이브를 다운로드하고 해당 디렉토리에서 추출합니다.

1. `google-cloud-sdk\install.sh` 스크립트를 실행합니다. 경로 변수의 설정을 허용해야 합니다.

1. 설치 후 경로 변수 `...\google-cloud-sdk\bin`이(가) 설정되어 있는지 확인합니다. 없는 경우 수동으로 추가합니다.

1. `PATH` 변수를 사용하지 않으려는 경우 또는 `google-cloud-sdk` 디렉토리를 다른 위치로 이동하려는 경우 **[!UICONTROL External account]**&#x200B;을 구성할 때 `bqpath` 옵션 값을 사용하여 시스템의 bin 디렉토리에 대한 정확한 경로를 지정합니다.

1. 변경 사항을 고려하여 Adobe Campaign Classic을 다시 시작합니다.

## Google BigQuery 외부 계정 {#google-external}

Adobe Campaign Classic 인스턴스를 [!DNL Google BigQuery] 외부 데이터베이스에 연결하려면 [!DNL Google BigQuery] 외부 계정을 만들어야 합니다.

1. Adobe Campaign Classic **[!UICONTROL Explorer]**&#x200B;에서 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]**&#39; **[!UICONTROL External accounts]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

1. 외부 계정의 **[!UICONTROL Type]**(으)로 **[!UICONTROL External database]**&#x200B;을(를) 선택합니다.

1. [!DNL Google BigQuery] 외부 계정을 구성합니다. 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**: 이메일  **[!UICONTROL Service account]**. 자세한 내용은 [Google Cloud 설명서](https://cloud.google.com/iam/docs/creating-managing-service-accounts)를 참조하십시오.

   * **[!UICONTROL Project]**: 사용자  **[!UICONTROL Project]**&#x200B;이름. 자세한 내용은 [Google Cloud 설명서](https://cloud.google.com/resource-manager/docs/creating-managing-projects)를 참조하십시오.

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**: Adobe Campaign Classic을 통해 키를 업로드하도록 선택하는  **[!UICONTROL Click here to upload]** 경우 을(를) 선택합니다.

      * **[!UICONTROL Enter manually the key file path]**: 기존 키를 사용하도록 선택하는 경우 이 필드에 절대 경로를 복사/붙여넣으십시오.
   * **[!UICONTROL Dataset]**: 사용자  **[!UICONTROL Dataset]**&#x200B;이름. 자세한 내용은 [Google Cloud 설명서](https://cloud.google.com/bigquery/docs/datasets-intro)를 참조하십시오.
   ![](assets/google-big-query.png)
