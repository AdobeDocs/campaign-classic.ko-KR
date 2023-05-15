---
product: campaign
title: FDA 커넥터 구성
description: FDA에 대한 구성 단계 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 5%

---

# FDA 커넥터 구성 {#specific-configurations-by-database-type}



Adobe Campaign에서 액세스할 수 있는 외부 데이터베이스에 따라 특정 구성을 수행해야 합니다. 이러한 구성에는 기본적으로 드라이버를 설치하고 Adobe Campaign 서버의 각 RDBMS에 속하는 환경 변수를 선언하는 작업이 포함됩니다.

일반적으로 Adobe Campaign 서버의 외부 데이터베이스에 해당 클라이언트 레이어를 설치해야 합니다.

>[!NOTE]
>
>호환 버전은 다음과 같습니다. [Campaign 호환성 매트릭스](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

## 구성 단계 {#fda-configuration-steps}

FDA를 사용하여 외부 데이터베이스에 대한 액세스를 설정하려면 구성 단계는 다음과 같습니다.

1. 드라이버를 설치하고 Adobe Campaign 서버에 데이터베이스에 해당하는 외부 계정을 설정합니다. 데이터베이스별 페이지를 참조하십시오 [아래에 나열된](#fda-specific-configuration)
1. 외부 계정을 테스트하거나 Adobe Campaign과 외부 데이터베이스 간의 임시 연결을 만듭니다. [자세히 알아보기](../../installation/using/connecting-to-database.md)
1. Adobe Campaign에서 외부 데이터베이스의 스키마를 만듭니다. 외부 데이터베이스의 데이터 구조를 식별할 수 있습니다. [자세히 알아보기](../../installation/using/creating-data-schema.md)
1. 필요한 경우 이전에 만든 스키마에서 새 대상 매핑을 만듭니다. 게재 수신자가 외부 데이터베이스에서 온 경우 필요합니다. 이 구현에는 메시지 개인화와 관련된 제한 사항이 포함되어 있습니다. [자세히 알아보기](../../installation/using/defining-data-mapping.md)

데이터 스키마가 만들어지면 Adobe Campaign 워크플로우에서 데이터를 처리할 수 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/accessing-an-external-database--fda-.md)을 참조하십시오.

## 데이터베이스별 구성 {#fda-specific-configuration}

Adobe Campaign에서 액세스할 수 있는 외부 데이터베이스에 따라 특정 구성을 수행해야 합니다. 이러한 구성은 기본적으로 드라이버 설치 및 Adobe Campaign 서버의 각 RDBMS에 속하는 환경 변수 선언, 외부 계정 구성 등이 포함됩니다.

자세한 내용은 아래 링크를 참조하십시오.

* Campaign 및 연결 [azure synapse](../../installation/using/configure-fda-synapse.md)
* Campaign 및 연결 [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* Campaign 및 연결 [Hadoop](../../installation/using/configure-fda-hadoop.md)
* Campaign 및 연결 [Microsoft SQL Server](../../installation/using/configure-fda-sql.md)
* Campaign 및 연결 [Netezza](../../installation/using/configure-fda-netezza.md)
* Campaign 및 연결 [Oracle](../../installation/using/configure-fda-oracle.md)
* Campaign 및 연결 [PostgreSQL](../../installation/using/configure-fda-postgresql.md)
* Campaign 및 연결 [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Campaign 및 연결 [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Campaign 및 연결 [sybase IQ](../../installation/using/configure-fda-sybase.md)
* Campaign 및 연결 [Teradata](../../installation/using/configure-fda-teradata.md)
* Campaign 및 연결 [vertica analytics](../../installation/using/configure-fda-vertica.md)
