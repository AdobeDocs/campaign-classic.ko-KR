---
solution: Campaign Classic
product: campaign
title: FDA 커넥터 구성
description: FDA에 대한 구성 단계 학습
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 6%

---


# FDA 커넥터 구성 {#specific-configurations-by-database-type}

Adobe Campaign에서 액세스할 수 있게 하려는 외부 데이터베이스에 따라 특정 구성을 수행해야 합니다. 이러한 구성은 기본적으로 Adobe Campaign 서버의 각 RDBMS에 속하는 환경 변수를 설치하고 선언하는 것과 관련되어 있습니다.

일반적으로 Adobe Campaign 서버의 외부 데이터베이스에 해당 클라이언트 레이어를 설치해야 합니다.

>[!NOTE]
>
>호환 가능한 버전은 [캠페인 호환성 매트릭스](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)에 나열되어 있습니다.


## 구성 단계 {#fda-configuration-steps}

FDA를 사용하여 외부 데이터베이스에 대한 액세스를 설정하려면 구성 단계는 다음과 같습니다.

1. Adobe Campaign 서버에 데이터베이스에 해당하는 드라이버를 설치합니다. 드라이버는 ](#fda-specific-configuration) 아래에 나열된 데이터베이스 특정 페이지 [에 나열됩니다.
1. [Adobe Campaign과 외부 데이터베이스 ](../../installation/using/connecting-to-database.md) 간의 연결을 설정할 수 있는 외부 계정을 만들고 구성합니다. 캠페인의 외부 계정에 대한 자세한 내용은 [이 페이지](../../installation/using/external-accounts.md)를 참조하십시오.
1. [Adobe Campaign](../../installation/using/creating-data-schema.md) 에서 외부 데이터베이스의 스키마를 만듭니다. 외부 데이터베이스의 데이터 구조를 인식할 수 있습니다.
1. 필요한 경우 [이전에 만든 스키마에서 새 대상 매핑](../../installation/using/defining-data-mapping.md)을 만듭니다. 배달 받는 사람이 외부 데이터베이스에서 온 경우 필요합니다. 이 구현에는 메시지 개인화와 관련된 제한 사항이 있습니다.

데이터 스키마가 만들어지면 Adobe Campaign 워크플로우에서 데이터를 처리할 수 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/accessing-an-external-database--fda-.md)을 참조하십시오.

## 데이터베이스별 구성 {#fda-specific-configuration}

Adobe Campaign에서 액세스할 수 있게 하려는 외부 데이터베이스에 따라 특정 구성을 수행해야 합니다. 이러한 구성은 기본적으로 Adobe Campaign 서버의 각 RDBMS에 속하는 환경 변수를 설치하고 선언하는 것과 관련되어 있습니다.

자세한 내용은 아래 링크를 참조하십시오.

* [azure synapse](../../installation/using/configure-fda-synapse.md)

* [Snowflake](../../installation/using/configure-fda-snowflake.md)

* [Hadoop](../../installation/using/configure-fda-hadoop.md)

* [Oracle](../../installation/using/configure-fda-oracle.md)

* [Netezza](../../installation/using/configure-fda-netezza.md)

* [sybase IQ](../../installation/using/configure-fda-sybase.md)

* [Teradata](../../installation/using/configure-fda-teradata.md)

* [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
