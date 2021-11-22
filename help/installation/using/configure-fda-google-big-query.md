---
product: campaign
title: Google BigQuery에 대한 액세스 구성
description: FDA에서 Google BigQuery에 대한 액세스를 구성하는 방법을 배웁니다.
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 6d53ba957fb567a9a921544418a73a9bde37c97b
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 2%

---

# Google BigQuery에 대한 액세스 구성 {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

Adobe Campaign Classic 사용 **페더레이션 데이터 액세스** (FDA) 옵션을 사용하여 외부 데이터베이스에 저장된 정보를 처리합니다. 아래 절차에 따라 액세스 권한을 구성하십시오 [!DNL Google BigQuery].

1. 구성 [!DNL Google BigQuery] on [Windows](#google-windows) 또는 [Linux](#google-linux)
1. 구성 [!DNL Google BigQuery] [외부 계정](#google-external) Adobe Campaign Classic
1. 설정 [!DNL Google BigQuery] 커넥터 벌크 로드 [Windows](#bulk-load-windows) 또는 [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] 커넥터는 하이브리드 및 온-프레미스 배포에 사용할 수 있습니다. 자세한 정보는 이 [페이지](../../installation/using/capability-matrix.md)를 참조하십시오.

![](assets/snowflake_3.png)

## Windows의 Google BigQuery {#google-windows}

### Windows에서 드라이버 설정 {#driver-window}

1. 다운로드 [Windows용 ODBC 드라이버](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Windows에서 ODBC 드라이버를 구성합니다. 자세한 정보는 이 [페이지](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf)를 참조하십시오.

1. 대상 [!DNL Google BigQuery] 커넥터를 사용하려면 Adobe Campaign Classic에서 연결하려면 다음 매개 변수가 필요합니다.

   * **[!UICONTROL Project]**: 기존 프로젝트를 만들거나 사용합니다.

      자세한 내용은 다음을 참조하십시오 [페이지](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service account]**: 서비스 계정을 만듭니다.

      자세한 내용은 다음을 참조하십시오 [페이지](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**: a **[!UICONTROL Service account]** 를 사용하려면 **[!UICONTROL Key File]** 대상 [!DNL Google BigQuery] ODBC를 통해 연결할 수 있습니다.

      자세한 내용은 다음을 참조하십시오 [페이지](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** 은 ODBC 연결에 선택 사항입니다. 모든 쿼리는 테이블이 있는 데이터 세트를 제공해야 하므로 **[!UICONTROL Dataset]** 에 대해 필수입니다. [!DNL Google BigQuery] Adobe Campaign Classic의 FDA 커넥터.

      자세한 내용은 다음을 참조하십시오 [페이지](https://cloud.google.com/bigquery/docs/datasets).

1. 그런 다음 Adobe Campaign Classic에서 [!DNL Google BigQuery] 외부 계정. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#google-external).

### Windows에서 벌크 로드 설정 {#bulk-load-window}

>[!NOTE]
>
>Google Cloud SDK가 작동하려면 Python이 설치되어 있어야 합니다.
>
>Python3를 사용하는 것이 좋습니다. 다음을 참조하십시오 [페이지](https://www.python.org/downloads/).

벌크 로드 유틸리티를 사용하면 Google Cloud SDK를 통해 보다 신속하게 전송할 수 있습니다.

1. 여기에서 Windows 64비트(x86_64) 아카이브 다운로드 [페이지](https://cloud.google.com/sdk/docs/downloads-versioned-archives) 해당 디렉토리에 추출합니다.

1. 를 실행합니다. `google-cloud-sdk\install.sh` 스크립트. 경로 변수의 설정을 허용해야 합니다.

1. 설치 후 경로 변수를 확인합니다 `...\google-cloud-sdk\bin` 이(가) 설정되어 있습니다. 없는 경우 수동으로 추가합니다.

1. 에서  `..\google-cloud-sdk\bin\bq.cmd` 파일에서 `CLOUDSDK_PYTHON` Python 설치 위치로 리디렉션되는 로컬 변수입니다.

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

1. 다운로드 [강도 Simba Linux ODBC 드라이버(.tar.gz)](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers). 그런 다음 대상 파일을 컴퓨터의 임시 폴더로 전달하거나 wget 명령을 사용합니다.

   ```
   # in this example driver version is 2.3.1.1001
   wget https://storage.googleapis.com/simba-bq-release/odbc/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux.tar.gz
   ```

1. 다음과 같이 기본 타겟팅 파일을 추출합니다. **TarballName** 은 드라이버를 포함하는 타볼 패키지의 이름입니다.

   ```
   tar --directory=/tmp -zxvf [TarballName]
   ```

1. 추출한 폴더에 액세스하여 드라이버 버전에 해당하는 내부 타겟 파일을 추출합니다. 다음 BigQueryDriver 예에서 다른 임시 폴더에 설치합니다.

   ```
   mkdir /tmp/BigQueryDriver/
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   tar --directory=/tmp/BigQueryDriver/ -zxvf SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version].tar.gz
   ```

1. 기본 대상 파일이 추출된 임시 위치에 액세스하여 다음 파일을 복사합니다 `GoogleBigQueryODBC.did` 및 `setup/simba.googlebigqueryodbc.ini` 이전 단계에서 만든 새 폴더에 파일을 넣습니다.

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

1. 바꾸기 `<INSTALLDIR>` with `/opt/simba/googlebigqueryodbc` in `simba.googlebigqueryodbc.ini` 설치 디렉토리에서 다음을 수행합니다.

   ```
   cd /opt/simba/googlebigqueryodbc/lib/
   sed -i 's/<INSTALLDIR>/\/opt\/simba\/googlebigqueryodbc/g' simba.googlebigqueryodbc.ini
   ```

1. 변경 `DriverManagerEncoding` UTF-16 및 `SwapFilePath` in `simba.googlebigqueryodbc.ini`. 필요한 경우 로깅 설정을 변경할 수도 있습니다.

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

1. 시스템 드라이버 파일 또는 현재 파일을 사용하는 경우 `odbcinst.ini` 파일, 구성 `/etc/odbcinst.ini` Google BigQuery 드라이버 위치를 가리키려면 `/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb[Bitness].so`.

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

1. unixODBC 드라이버 관리자 라이브러리의 위치를 찾아 `unixODBC` 및 `googlebigqueryodbc` 에 대한 라이브러리 경로 `LD_LIBRARY_PATH environment` 변수를 채우는 방법을 설명합니다.

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

1. 그런 다음 Adobe Campaign Classic에서 [!DNL Google BigQuery] 외부 계정. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#google-external).

### Linux에서 벌크 로드 설정 {#bulk-load-linux}

>[!NOTE]
>
>Google Cloud SDK가 작동하려면 Python이 설치되어 있어야 합니다.
>
>Python3를 사용하는 것이 좋습니다. 다음을 참조하십시오 [페이지](https://www.python.org/downloads/).

벌크 로드 유틸리티를 사용하면 Google Cloud SDK를 통해 보다 신속하게 전송할 수 있습니다.

1. Linux 64비트(x86_64) 아카이브 다운로드 [페이지](https://cloud.google.com/sdk/docs/downloads-versioned-archives) 및 를 해당 디렉토리에 추출합니다.

1. 를 실행합니다. `google-cloud-sdk\install.sh` 스크립트. 경로 변수의 설정을 허용해야 합니다.

1. 설치 후 경로 변수를 확인합니다 `...\google-cloud-sdk\bin` 이(가) 설정되어 있습니다. 없는 경우 수동으로 추가합니다.

1. 를 사용하지 않으려면 `PATH` 변수를 이동하거나 `google-cloud-sdk` 다른 위치에 있는 디렉토리는 `bqpath` 구성 시 옵션 값 **[!UICONTROL External account]** 시스템에서 bin 디렉토리에 대한 정확한 경로를 지정합니다.

1. 변경 사항을 고려하여 Adobe Campaign Classic을 다시 시작합니다.

## Google BigQuery 외부 계정 {#google-external}

을(를) 만들어야 합니다 [!DNL Google BigQuery] Adobe Campaign Classic 인스턴스를 [!DNL Google BigQuery] 외부 데이터베이스.

1. Adobe Campaign Classic에서 **[!UICONTROL Explorer]**&#x200B;를 클릭합니다. **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

1. 선택 **[!UICONTROL External database]** 외부 계정 **[!UICONTROL Type]**.

1. 구성 [!DNL Google BigQuery] 외부 계정입니다. 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**: 이메일 **[!UICONTROL Service account]**. 자세한 내용은 [Google Cloud 설명서](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Project]**: 사용자 이름 **[!UICONTROL Project]**. 자세한 내용은 [Google Cloud 설명서](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**: 선택 **[!UICONTROL Click here to upload]** Adobe Campaign Classic을 통해 키를 업로드하도록 선택하는 경우.

      * **[!UICONTROL Enter manually the key file path]**: 기존 키를 사용하도록 선택하는 경우 이 필드에 절대 경로를 복사/붙여넣으십시오.
   * **[!UICONTROL Dataset]**: 사용자 이름 **[!UICONTROL Dataset]**. 자세한 내용은 [Google Cloud 설명서](https://cloud.google.com/bigquery/docs/datasets-intro).
   ![](assets/google-big-query.png)
