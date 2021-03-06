---
product: campaign
title: Google BigQuery에 대한 액세스 구성
description: FDA에서 Google BigQuery에 대한 액세스를 구성하는 방법을 배웁니다.
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '779'
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
> [!DNL Google BigQuery] 커넥터는 호스팅, 하이브리드 및 온-프레미스 배포에 사용할 수 있습니다. 자세한 정보는 이 [페이지](../../installation/using/capability-matrix.md)를 참조하십시오.

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

드라이버를 설정하기 전에 루트 사용자가 스크립트 및 명령을 실행해야 합니다. 스크립트를 실행하는 동안 Google DNS 8.8.8.8을 사용하는 것이 좋습니다.

구성하려면 [!DNL Google BigQuery] linux에서 아래 단계를 수행하십시오.

1. ODBC 설치 전에 Linux 배포에 다음 패키지가 설치되어 있는지 확인하십시오.

   * Red Hat/CentOS의 경우:

      ```
      yum update
      yum upgrade
      yum install -y grep sed tar wget perl curl
      ```

   * Debian의 경우:

      ```
      apt-get update
      apt-get upgrade
      apt-get install -y grep sed tar wget perl curl
      ```

1. 설치 전 시스템 업데이트:

   * Red Hat/CentOS의 경우:

      ```
      # install unixODBC driver manager
      yum install -y unixODBC
      ```

   * Debian의 경우:

      ```
      # install unixODBC driver manager
      apt-get install -y odbcinst1debian2 libodbc1 odbcinst unixodbc
      ```

1. 스크립트가 있는 디렉토리에 액세스하여 다음 스크립트를 실행합니다.

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh
   ```

### Linux에서 벌크 로드 설정 {#bulk-load-linux}

>[!NOTE]
>
>Google Cloud SDK가 작동하려면 Python이 설치되어 있어야 합니다.
>
>Python3를 사용하는 것이 좋습니다. 다음을 참조하십시오 [페이지](https://www.python.org/downloads/).

벌크 로드 유틸리티를 사용하면 Google Cloud SDK를 통해 보다 신속하게 전송할 수 있습니다.

1. ODBC 설치 전에 Linux 배포에 다음 패키지가 설치되어 있는지 확인하십시오.

   * Red Hat/CentOS의 경우:

      ```
      yum update
      yum upgrade
      yum install -y python3
      ```

   * Debian의 경우:

      ```
      apt-get update
      apt-get upgrade
      apt-get install -y python3
      ```

1. 스크립트가 있는 디렉토리에 액세스하여 다음 스크립트를 실행합니다.

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_sdk-setup.sh
   ```

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

커넥터는 다음 옵션을 지원합니다.

| 옵션 | 설명 |
|:-:|:-:|
| ProxyType | ODBC 및 SDK 커넥터를 통해 BigQuery에 연결하는 데 사용되는 프록시 유형입니다. </br>HTTP(기본값), http_no_tunnel, socks4 및 socks5가 현재 지원됩니다. |
| ProxyHost | 프록시에 도달할 수 있는 호스트 이름 또는 IP 주소입니다. |
| ProxyPort | 프록시가 실행 중인 포트 번호(예: 8080) |
| ProxyUid | 인증된 프록시에 사용된 사용자 이름 |
| ProxyPwd | ProxyUid 암호 |
| bqpath | 이 기능은 벌크 로드 도구 전용(Cloud SDK)에 적용됩니다. </br> PATH 변수를 사용하지 않거나 google-cloud-sdk 디렉토리를 다른 위치로 이동해야 하는 경우 이 옵션을 사용하여 서버의 cloud sdk bin 디렉토리에 대한 정확한 경로를 지정할 수 있습니다. |
