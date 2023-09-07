---
product: campaign
title: Google BigQuery에 대한 액세스 구성
description: FDA에서 Google BigQuery에 대한 액세스를 구성하는 방법 알아보기
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: a94c361c5bdd9d61ae9232224af910a78245a889
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 2%

---

# Google BigQuery에 대한 액세스 구성 {#configure-fda-google-big-query}



Adobe Campaign Classic 사용 **페더레이션 데이터 액세스** (FDA) 외부 데이터베이스에 저장된 정보를 처리하는 옵션입니다. 액세스 권한을 구성하려면 아래 단계를 따르십시오. [!DNL Google BigQuery].

1. 구성 [!DNL Google BigQuery] 날짜 [Windows](#google-windows) 또는 [리눅스](#google-linux)
1. 구성 [!DNL Google BigQuery] [외부 계정](#google-external) Adobe Campaign Classic에서
1. 설정 [!DNL Google BigQuery] 커넥터 벌크 로드 [Windows](#bulk-load-windows) 또는 [리눅스](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] 커넥터는 호스팅, 하이브리드 및 온-프레미스 배포에 사용할 수 있습니다. 자세한 정보는 이 [페이지](../../installation/using/capability-matrix.md)를 참조하십시오.

![](assets/snowflake_3.png)

## Windows의 Google BigQuery {#google-windows}

### Windows에서 드라이버 설정 {#driver-window}

1. 다운로드 [Windows용 ODBC 드라이버](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Windows에서 ODBC 드라이버를 구성합니다. 자세한 정보는 이 [페이지](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf)를 참조하십시오.

1. 의 경우 [!DNL Google BigQuery] 커넥터가 작동하려면 Adobe Campaign Classic에서 연결하려면 다음 매개 변수가 필요합니다.

   * **[!UICONTROL Project]**: 기존 프로젝트를 만들거나 사용합니다.

     자세한 내용은 다음을 참조하십시오. [페이지](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service account]**: 서비스 계정을 만듭니다.

     자세한 내용은 다음을 참조하십시오. [페이지](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**: **[!UICONTROL Service account]** 을(를) 필요로 함 **[!UICONTROL Key File]** 용 [!DNL Google BigQuery] ODBC를 통한 연결.

     자세한 내용은 다음을 참조하십시오. [페이지](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** 는 ODBC 연결에 대해 선택 사항입니다. 모든 쿼리는 테이블이 있는 데이터 세트를 제공해야 하므로 **[!UICONTROL Dataset]** 은(는) 의 필수 항목입니다. [!DNL Google BigQuery] Adobe Campaign Classic의 FDA 커넥터.

     자세한 내용은 다음을 참조하십시오. [페이지](https://cloud.google.com/bigquery/docs/datasets).

1. 그런 다음 Adobe Campaign Classic에서 다음을 구성할 수 있습니다. [!DNL Google BigQuery] 외부 계정입니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#google-external).

### Windows에서 대량 로드 설정 {#bulk-load-window}

>[!NOTE]
>
>Google Cloud SDK가 작동하도록 Python을 설치해야 합니다.
>
>Python3를 사용하는 것이 좋습니다. 다음을 참조하십시오. [페이지](https://www.python.org/downloads/).

벌크 로드 유틸리티를 사용하면 Google Cloud SDK를 통해 보다 빠르게 전송할 수 있습니다.

1. 여기에서 Windows 64비트(x86_64) 아카이브 다운로드 [페이지](https://cloud.google.com/sdk/docs/downloads-versioned-archives) 를 누르고 해당 디렉터리에서 압축을 풉니다.

1. 실행 `google-cloud-sdk\install.sh` 스크립트. 경로 변수의 설정을 승인해야 합니다.

1. 설치 후 경로 변수가 있는지 확인합니다 `...\google-cloud-sdk\bin` 이(가) 설정되어 있습니다. 그렇지 않은 경우 수동으로 추가합니다.

1. 다음에서  `..\google-cloud-sdk\bin\bq.cmd` 파일, 추가 `CLOUDSDK_PYTHON` 로컬 변수로, Python 설치 위치로 리디렉션됩니다.

   예제:

   ![](assets/google-big-query_1.png)

1. 변경 사항을 고려하려면 Adobe Campaign Classic을 다시 시작하십시오.

## Linux의 Google BigQuery {#google-linux}

### Linux에서 드라이버 설정 {#driver-linux}

드라이버를 설정하기 전에 루트 사용자가 스크립트와 명령을 실행해야 합니다. 또한 스크립트를 실행하는 동안 Google DNS 8.8.8.8을 사용하는 것이 좋습니다.

구성하려면 [!DNL Google BigQuery] linux의 경우 아래 단계를 수행합니다.

1. ODBC를 설치하기 전에 Linux 배포판에 다음 패키지가 설치되어 있는지 확인하십시오.

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

1. 설치하기 전에 시스템 업데이트:

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

1. 스크립트를 실행하기 전에 —help 인수를 지정하여 자세한 정보를 얻을 수 있습니다.

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh --help
   ```

1. 스크립트가 있는 디렉토리에 액세스하여 루트 사용자로 다음 스크립트를 실행합니다.

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh
   ```

### Linux에 대량 로드 설정 {#bulk-load-linux}

>[!NOTE]
>
>Google Cloud SDK가 작동하도록 Python을 설치해야 합니다.
>
>Python3를 사용하는 것이 좋습니다. 다음을 참조하십시오. [페이지](https://www.python.org/downloads/).

벌크 로드 유틸리티를 사용하면 Google Cloud SDK를 통해 보다 빠르게 전송할 수 있습니다.

1. ODBC를 설치하기 전에 Linux 배포판에 다음 패키지가 설치되어 있는지 확인하십시오.

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

다음을 만들어야 합니다. [!DNL Google BigQuery] Adobe Campaign Classic 인스턴스를 [!DNL Google BigQuery] 외부 데이터베이스.

1. 출처: Adobe Campaign Classic **[!UICONTROL Explorer]**, 클릭 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

1. 선택 **[!UICONTROL External database]** 외부 계정으로 **[!UICONTROL Type]**.

1. 구성 [!DNL Google BigQuery] 외부 계정에서 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**: 의 이메일 **[!UICONTROL Service account]**. 자세한 내용은 다음을 참조하십시오. [Google Cloud 설명서](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Project]**: 의 이름 **[!UICONTROL Project]**. 자세한 내용은 다음을 참조하십시오. [Google Cloud 설명서](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**: 선택 **[!UICONTROL Click here to upload]** Adobe Campaign Classic을 통해 키를 업로드하도록 선택하는 경우.

      * **[!UICONTROL Enter manually the key file path]**: 기존 키를 사용하도록 선택하는 경우 이 필드에 절대 경로를 복사하거나 붙여 넣습니다.

   * **[!UICONTROL Dataset]**: 의 이름 **[!UICONTROL Dataset]**. 자세한 내용은 다음을 참조하십시오. [Google Cloud 설명서](https://cloud.google.com/bigquery/docs/datasets-intro).

   ![](assets/google-big-query.png)

커넥터는 다음 옵션을 지원합니다.

| 옵션 | 설명 |
|:-:|:-:|
| ProxyType | ODBC 및 SDK 커넥터를 통해 BigQuery에 연결하는 데 사용되는 프록시 유형입니다. </br>HTTP(기본값), http_no_tunnel, socks4 및 socks5가 현재 지원됩니다. |
| ProxyHost | 프록시에 연결할 수 있는 호스트 이름 또는 IP 주소입니다. |
| ProxyPort | 프록시가 실행 중인 포트 번호(예: 8080) |
| ProxyUid | 인증된 프록시에 사용되는 사용자 이름 |
| 프록시 로드 | ProxyUid 암호 |
| bqpath | 이 기능은 대량 로드 도구(Cloud SDK)에만 적용할 수 있습니다. </br> PATH 변수를 사용하지 않거나 google-cloud-sdk 디렉토리를 다른 위치로 이동해야 하는 경우 이 옵션을 사용하여 서버의 cloud sdk bin 디렉토리에 대한 정확한 경로를 지정할 수 있습니다. |
| GCloudConfigName | 릴리스 7.3.4 릴리스부터 대량 로드 도구 전용(Cloud SDK)에 적용할 수 있습니다.</br> Google Cloud SDK는 구성을 사용하여 데이터를 BigQuery 테이블에 로드합니다. 이름이 인 구성 `accfda` 데이터를 로드하기 위한 매개 변수를 저장합니다. 그러나 이 옵션을 사용하면 구성에 대해 다른 이름을 지정할 수 있습니다. |
| GCloudDefaultConfigName | 릴리스 7.3.4 릴리스부터 대량 로드 도구 전용(Cloud SDK)에 적용할 수 있습니다.</br> 활성 태그를 새 구성으로 먼저 전송하지 않으면 활성 Google Cloud SDK 구성을 삭제할 수 없습니다. 이 임시 구성은 데이터 로드를 위한 기본 구성을 다시 만드는 데 필요합니다. 임시 구성의 기본 이름은 입니다. `default`, 필요한 경우 변경할 수 있습니다. |
| GCloudRecreateConfig | 릴리스 7.3.4 릴리스부터 대량 로드 도구 전용(Cloud SDK)에 적용할 수 있습니다.</br> 로 설정된 경우 `false`, 벌크 로드 메커니즘은 Google Cloud SDK 구성을 다시 생성, 삭제 또는 수정하지 않습니다. 대신 시스템의 기존 구성을 사용하여 데이터 로드를 계속 진행합니다. 이 기능은 다른 작업이 Google Cloud SDK 구성에 따라 달라질 때 유용합니다. </br> 사용자가 적절한 구성 없이 이 엔진 옵션을 활성화하면 벌크 로드 메커니즘에서 다음과 같은 경고 메시지가 표시됩니다. `No active configuration found. Please either create it manually or remove the GCloudRecreateConfig option`. 추가 오류를 방지하기 위해 기본 ODBC 배열 삽입 대량 로드 메커니즘을 사용하는 것으로 돌아갑니다. |

