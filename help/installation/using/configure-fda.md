---
product: campaign
title: FDA 커넥터 구성
description: FDA에 대한 구성 단계 알아보기
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 4%

---

# FDA 커넥터 구성 {#specific-configurations-by-database-type}



Adobe Campaign에서 액세스할 수 있게 하려는 외부 데이터베이스에 따라 특정 구성을 수행해야 합니다. 이러한 구성은 기본적으로 드라이버를 설치하고 Adobe Campaign 서버의 각 RDBMS에 속하는 환경 변수를 선언하는 것입니다.

일반적으로 Adobe Campaign 서버의 외부 데이터베이스에 해당 클라이언트 레이어를 설치해야 합니다.

>[!NOTE]
>
>호환 가능한 버전은 [Campaign 호환성 매트릭스](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)에 나와 있습니다.
>

## 구성 단계 {#fda-configuration-steps}

FDA를 사용하여 외부 데이터베이스에 대한 액세스를 설정하려면 구성 단계를 수행합니다.

1. 드라이버를 설치하고 Adobe Campaign 서버의 데이터베이스에 해당하는 외부 계정을 설정합니다. 데이터베이스 관련 페이지 [아래 목록](#fda-specific-configuration)을 참조하세요.
1. 외부 계정을 테스트하거나 Adobe Campaign과 외부 데이터베이스 간에 임시 연결을 만듭니다. [자세히 알아보기](../../installation/using/connecting-to-database.md)
1. Adobe Campaign에서 외부 데이터베이스의 스키마를 만듭니다. 이렇게 하면 외부 데이터베이스의 데이터 구조를 식별할 수 있습니다. [자세히 알아보기](../../installation/using/creating-data-schema.md)
1. 필요한 경우 이전에 만든 스키마에서 새 대상 매핑을 만듭니다. 게재 수신자가 외부 데이터베이스에서 온 경우 필요합니다. 이 구현에는 메시지 개인화와 관련된 제한 사항이 있습니다. [자세히 알아보기](../../installation/using/defining-data-mapping.md)

데이터 스키마가 만들어지면 Adobe Campaign 워크플로우에서 데이터를 처리할 수 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/accessing-an-external-database-fda.md)을 참조하십시오.

## 데이터베이스별 구성 {#fda-specific-configuration}

Adobe Campaign에서 액세스할 수 있게 하려는 외부 데이터베이스에 따라 특정 구성을 수행해야 합니다. 이러한 구성에는 기본적으로 드라이버를 설치하고 Adobe Campaign 서버의 각 RDBMS에 속하는 환경 변수를 선언하고 외부 계정을 구성하는 작업이 포함됩니다.

자세한 내용은 아래 링크를 참조하십시오.

* Campaign과 [Amazon Redshift](../../installation/using/configure-fda-redshift.md) 연결
* Campaign과 [Azure synapse](../../installation/using/configure-fda-synapse.md) 연결
* Campaign과 [Google BigQuery](../../installation/using/configure-fda-google-big-query.md) 연결
* Campaign과 [Hadoop](../../installation/using/configure-fda-hadoop.md) 연결
* Campaign과 [Microsoft SQL Server 연결](../../installation/using/configure-fda-sql.md)
* Campaign과 [Netezza](../../installation/using/configure-fda-netezza.md) 연결
* Campaign과 [Oracle](../../installation/using/configure-fda-oracle.md) 연결
* Campaign과 [PostgreSQL](../../installation/using/configure-fda-postgresql.md) 연결
* Campaign과 [SAP HANA](../../installation/using/configure-fda-sap-hana.md) 연결
* Campaign과 [Snowflake](../../installation/using/configure-fda-snowflake.md) 연결
* Campaign과 [Sybase IQ](../../installation/using/configure-fda-sybase.md) 연결
* Campaign과 [Teradata](../../installation/using/configure-fda-teradata.md) 연결
* Campaign과 [Vertica analytics](../../installation/using/configure-fda-vertica.md) 연결
