---
product: campaign
title: Amazon Redshift 액세스 구성
description: FDA에서 Amazon Redshift에 대한 액세스를 구성하는 방법 알아보기
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
audience: platform
content-type: reference
topic-tags: connectors
source-git-commit: 6939307c0b33ff662fe4ef9ae0192ae7b500a95c
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 6%

---

# Amazon Redshift 액세스 구성 {#configure-access-to-redshift}

Campaign 사용 **페더레이션 데이터 액세스** (FDA) 외부 데이터베이스에 저장된 정보를 처리하는 옵션. Amazon Redshift에 대한 액세스를 구성하려면 아래 단계를 따르십시오.

1. 구성 [Amazon Redshift 데이터베이스](#configuring-redshift)
1. Amazon Redshift 구성 [외부 계정](#redshift-external) 캠페인에서

## Linux의 Amazon Redshift {#redshift-linux}

구성하려면 [!DNL Amazon Redshift] linux의 경우 아래 단계를 수행합니다.

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

1. 스크립트를 실행하기 전에 `--help` 옵션:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./redshift_odbc-setup.sh --help
   ```

1. 스크립트가 있는 디렉토리에 액세스하여 루트 사용자로 다음 스크립트를 실행합니다.

   ```
     cd /usr/local/neolane/nl6/bin/fda-setup-scripts
     ./redshift_odbc-setup.sh
   ```

1. ODBC 드라이버를 설치한 후 Campaign Classic을 다시 시작해야 합니다. 이렇게 하려면 다음 명령을 실행합니다.

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 그런 다음 Campaign에서 다음을 구성할 수 있습니다. [!DNL Amazon Redshift] 외부 계정입니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#redshift-external).

## Amazon Redshift 외부 계정 {#redshift-external}

다음 [!DNL Amazon Redshift] 외부 계정을 사용하면 Campaign 인스턴스를 Amazon Redshift 외부 데이터베이스에 연결할 수 있습니다.

1. Campaign Classic에서 [!DNL Amazon Redshift] 외부 계정입니다. 다음에서 **[!UICONTROL Explorer]**, 클릭 **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

1. 선택 **[!UICONTROL External database]** 외부 계정으로 **[!UICONTROL Type]**.

1. 구성 **[!UICONTROL Amazon Redshift]** 외부 계정에서 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: Amazon Redshift

   * **[!UICONTROL Server]**: DNS 이름

   * **[!UICONTROL Account]**: 사용자 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Database]**: DSN에 지정되지 않은 경우 데이터베이스의 이름입니다. DSN에 지정된 경우 비워 둘 수 있습니다.

   * **[!UICONTROL Working schema]**: 작업 스키마의 이름입니다. [자세히 알아보기](https://docs.aws.amazon.com/redshift/latest/dg/r_Schemas_and_tables.html)

   * **[!UICONTROL Time zone]**: 서버 시간대

   ![](assets/amazon_redshift.png)

1. **[!UICONTROL Save]**&#x200B;를 클릭합니다.
