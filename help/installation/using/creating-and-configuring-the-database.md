---
product: campaign
title: 데이터베이스 만들기 및 구성
description: 데이터베이스 만들기 및 구성
feature: Installation, Instance Settings
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f40bab8c-5064-40d9-beed-101a9f22c094
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '1329'
ht-degree: 1%

---

# 데이터베이스 만들기 및 구성{#creating-and-configuring-the-database}

데이터베이스를 만들 때 Adobe Campaign은 두 가지 옵션을 제공합니다.

1. 데이터베이스 생성 또는 재활용: 새 데이터베이스를 생성하거나 기존 데이터베이스를 재사용하려면 이 옵션을 선택합니다. 을(를) 참조하십시오 [사례 1: 데이터베이스 만들기/재활용](#case-1--creating-recycling-a-database).
1. 기존 데이터베이스 사용: 관리자가 빈 데이터베이스를 이미 생성했으며 이를 사용하거나 기존 데이터베이스의 구조를 확장하려는 경우 이 옵션을 선택합니다. 을(를) 참조하십시오 [사례 2: 기존 데이터베이스 사용](#case-2--using-an-existing-database).

구성 단계는 아래에 자세히 설명되어 있습니다.

>[!CAUTION]
>
>데이터베이스, 사용자 및 스키마 이름은 숫자로 시작하거나 특수 문자를 포함할 수 없습니다.
>
>만 **내부** 식별자는 이러한 작업을 수행할 수 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#internal-identifier)을 참조하십시오.

## 사례 1: 데이터베이스 만들기/재활용 {#case-1--creating-recycling-a-database}

데이터베이스를 만들거나 기존 기반을 재사용하는 단계는 아래에 나와 있습니다. 일부 구성은 사용되는 데이터베이스 엔진에 따라 다릅니다.

다음 단계가 포함됩니다.

* [1단계 - 데이터베이스 엔진 선택](#step-1---selecting-the-database-engine),
* [2단계 - 서버에 연결](#step-2---connecting-to-the-server),
* [3단계 - 데이터베이스 연결 및 특성](#step-3---connection-and-characteristics-of-the-database),
* [4단계 - 설치할 패키지](#step-4---packages-to-install),
* [5단계 - 만들기 단계](#step-5---creation-steps),
* [6단계 - 데이터베이스 만들기](#step-6---creating-the-database).

### 1단계 - 데이터베이스 엔진 선택 {#step-1---selecting-the-database-engine}

드롭다운 목록에 있는 데이터베이스 엔진 중에서 선택합니다.

![](assets/s_ncs_install_db_select_engine.png)

지원되는 데이터베이스는 Campaign에 나열되어 있습니다. [호환성 매트릭스](../../rn/using/compatibility-matrix.md).

서버를 식별하고 수행할 작업 유형을 선택합니다. 이 경우, **[!UICONTROL Create or recycle a database]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

선택된 데이터베이스 엔진에 따라, 서버 식별 정보는 달라질 수 있다.

* 의 경우 **Oracle** 엔진, 다음을 채우기 **TNS 이름** 응용 프로그램 서버에 대해 정의됩니다.
* 의 경우 **PostgreSql** 또는 **DB2** 데이터베이스 서버에 액세스하려면 애플리케이션 서버에 정의된 DNS 이름(또는 IP 주소)을 지정해야 합니다.
* 의 경우 **Microsoft Server** 엔진, 다음을 정의해야 합니다. 데이터베이스 서버에 액세스하려면 애플리케이션 서버에 정의된 DNS 이름(또는 IP 주소): **DNS** 또는 **DNS`\<instance>`** (인스턴스 모드),

  >[!CAUTION]
  >
  > 20.3부터 Windows NT 인증이 사용 중단됩니다. **[!UICONTROL SQL Server authentication]** 는 이제 Microsoft SQL Server에서 사용할 수 있는 유일한 인증 모드입니다. [자세히 보기](../../rn/using/deprecated-features.md)

  ![](assets/s_ncs_install_db_mssql_creation01.png)

### 2단계 - 서버에 연결 {#step-2---connecting-to-the-server}

다음에서 **[!UICONTROL Server access]** 창에서 데이터베이스 서버 액세스를 정의합니다.

![](assets/s_ncs_install_db_oracle_creation02.png)

이렇게 하려면 의 이름과 암호를 입력합니다. **관리 시스템 계정** 데이터베이스에 액세스할 수 있는 권한, 즉:

* **시스템** oracle 데이터베이스의 경우
* **sa** Microsoft SQL Server 데이터베이스의 경우
* **postgres** PostgreSQL 데이터베이스의 경우
* **db2inst1** DB2 데이터베이스용

### 3단계 - 데이터베이스 연결 및 특성 {#step-3---connection-and-characteristics-of-the-database}

다음 단계에서는 데이터베이스에 로그온하기 위한 설정을 구성할 수 있습니다.

![](assets/s_ncs_install_db_oracle_creation03.png)

다음 설정을 정의해야 합니다.

* 생성할 데이터베이스의 이름을 지정합니다.

  >[!NOTE]
  >
  >DB2 데이터베이스의 경우 데이터베이스 이름은 8자를 초과할 수 없습니다.

* 이 데이터베이스에 연결된 계정의 암호를 입력합니다.
* 데이터베이스가 유니코드로 되어 있어야 하는지 여부를 나타냅니다.

  다음 **[!UICONTROL Unicode database]** 옵션을 사용하면 언어에 관계없이 모든 문자 유형을 유니코드에 저장할 수 있습니다.

  >[!NOTE]
  >
  >oracle 데이터베이스를 사용하면 **[!UICONTROL Unicode storage]** 옵션을 사용하면 다음을 사용할 수 있습니다. **NCLOB** 및 **NVARCHAR** 필드를 입력합니다.
  > 
  >이 옵션을 선택하지 않으면 Oracle 데이터베이스의 문자 세트(charset)가 모든 언어로 데이터 저장을 활성화해야 합니다(AL32UTF8이 권장됨).

* 데이터베이스의 시간대를 선택하고 UTC(가능한 경우)로 설정할지 여부를 지정합니다.

  자세한 내용은 다음을 참조하십시오. [시간대 관리](../../installation/using/time-zone-management.md).

### 4단계 - 설치할 패키지 {#step-4---packages-to-install}

설치할 패키지를 선택합니다.

라이선스 계약을 참조하여 &quot;상호 작용&quot; 또는 &quot;소셜 마케팅&quot;과 같이 설치할 수 있는 솔루션 및 옵션을 확인하십시오.

![](assets/s_ncs_install_modules.png)

### 5단계 - 만들기 단계 {#step-5---creation-steps}

다음 **[!UICONTROL Creation steps]** 창을 사용하면 테이블 작성에 사용되는 SQL 스크립트를 표시하고 편집할 수 있습니다.

![](assets/s_ncs_install_db_oracle_creation04.png)

* oracle, Microsoft SQL Server 또는 PostgreSQL 데이터베이스의 경우 관리자는 **저장소 매개 변수** 데이터베이스 개체를 만들 때 사용됩니다.

  이러한 매개변수는 정확한 테이블스페이스 이름을 수신합니다(경고: 대소문자 구분). 이러한 ID는 각각 **[!UICONTROL Administration > Platform > Options]** 다음 옵션의 노드(참조) [이 섹션](../../installation/using/configuring-campaign-options.md#database)):

   * **WdbcOptions_TableSpaceUser**: 스키마를 기반으로 하는 사용자 테이블
   * **WdbcOptions_TableSpaceIndex**: 스키마를 기반으로 하는 사용자 테이블 인덱스
   * **WdbcOptions_TableSpaceWork**: 스키마가 없는 작업 테이블
   * **WdbcOptions_TableSpaceWorkIndex**: 스키마가 없는 작업 테이블 인덱스

* oracle 데이터베이스의 경우 Adobe Campaign 사용자는 일반적으로 의 멤버로서 Oracle 라이브러리에 액세스할 수 있어야 합니다 **oinstall** 그룹입니다.
* 다음 **[!UICONTROL Set or change the administrator password]** 옵션을 사용하면 관리자 권한이 있는 Adobe Campaign 연산자에 연결된 암호를 입력할 수 있습니다.

  보안을 위해 Adobe Campaign 계정 관리자 암호를 정의하는 것이 좋습니다.

### 6단계 - 데이터베이스 만들기 {#step-6---creating-the-database}

마법사의 마지막 단계에서는 데이터베이스를 만들 수 있습니다. **[!UICONTROL Start]**&#x200B;을(를) 클릭하여 확인합니다.

![](assets/s_ncs_install_db_oracle_creation06.png)

데이터베이스가 생성되면 다시 연결하여 인스턴스 구성을 완료할 수 있습니다.

이제 배포 마법사를 시작하여 인스턴스 구성을 완료해야 합니다. 을(를) 참조하십시오 [배포 마법사](../../installation/using/deploying-an-instance.md#deployment-wizard).

인스턴스에 연결된 데이터베이스의 연결 설정은 파일에 저장됩니다 **`/conf/config-<instance>.xml`** Adobe Campaign 설치 디렉터리에 있습니다.

암호화된 암호를 사용하여 &#39;campaign&#39; 계정에 연결된 base61 데이터베이스의 Microsoft SQL Server 구성의 예:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## 사례 2: 기존 데이터베이스 사용 {#case-2--using-an-existing-database}

데이터베이스 관리자 및 사용자는 데이터베이스 및 액세스 권한이 올바르게 구성되어 있어야 합니다.

예를 들어 Oracle 데이터베이스의 경우 필요한 최소 권한은 GRANT CONNECT, RESOURCE 및 UNLIMITED TABLESPACE입니다.

기존 데이터베이스를 사용하려면 구성 단계는 다음과 같습니다.

* [1단계 - 데이터베이스 엔진 선택](#step-1---choosing-the-database-engine),
* [2단계 - 데이터베이스 연결 설정](#step-2---database-connection-settings),
* [3단계 - 설치할 패키지](#step-3---packages-to-install),
* [4단계 - 만들기 단계](#step-4---creation-steps),
* [5단계 - 데이터베이스 만들기](#step-5---creating-the-database).

### 1단계 - 데이터베이스 엔진 선택 {#step-1---choosing-the-database-engine}

드롭다운 목록에서 데이터베이스 엔진을 선택합니다.

![](assets/s_ncs_install_db_select_engine.png)

서버를 식별하고 수행할 작업 유형을 선택합니다. 이 경우, **[!UICONTROL Use an existing database]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

선택된 데이터베이스 엔진에 따라, 서버 식별 정보는 달라질 수 있다.

* 의 경우 **Oracle** 엔진, 다음을 채우기 **TNS 이름** 응용 프로그램 서버에 대해 정의됩니다.
* 의 경우 **PostgreSql** 또는 **DB2** 데이터베이스 서버에 액세스하려면 애플리케이션 서버에 정의된 DNS 이름(또는 IP 주소)을 지정해야 합니다.
* 의 경우 **Microsoft Server** 엔진, 다음을 정의해야 합니다.

   1. 데이터베이스 서버에 액세스하기 위해 애플리케이션 서버에 정의된 DNS 이름(또는 IP 주소),
   1. Microsoft SQL Server에 액세스하는 데 사용되는 보안 방법: **[!UICONTROL SQL Server authentication]** 또는 **[!UICONTROL Windows NT authentication]**.

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### 2단계 - 데이터베이스 연결 설정 {#step-2---database-connection-settings}

다음에서 **[!UICONTROL Database]** 창에서 데이터베이스 연결 설정을 정의합니다.

![](assets/s_ncs_install_db_oracle_exists_02.png)

다음 설정을 정의해야 합니다.

* 사용할 데이터베이스의 이름을 입력하십시오.
* 이 데이터베이스와 연결된 계정의 이름 및 암호를 입력하십시오.

  >[!NOTE]
  >
  >스키마 이름과 사용자 이름이 모두 일치하는지 확인하십시오. 데이터베이스를 만드는 권장 방법은 campaign 콘솔 클라이언트를 사용하는 것입니다.
  >oracle 데이터베이스의 경우 계정 이름을 입력할 필요가 없습니다.

* 데이터베이스가 유니코드여야 하는지 여부를 나타냅니다.

### 3단계 - 설치할 패키지 {#step-3---packages-to-install}

설치할 패키지를 선택합니다.

라이선스 계약을 참조하여 &quot;상호 작용&quot; 또는 &quot;리드&quot;와 같이 설치할 수 있는 솔루션 및 옵션을 확인하십시오.

![](assets/s_ncs_install_modules.png)

### 4단계 - 만들기 단계 {#step-4---creation-steps}

다음 **[!UICONTROL Creation steps]** 창을 사용하면 테이블 작성에 사용되는 SQL 스크립트를 표시하고 편집할 수 있습니다.

![](assets/s_ncs_install_db_oracle_creation04.png)

* oracle, Microsoft SQL Server 또는 PostgreSQL 데이터베이스의 경우 관리자는 **저장소 매개 변수** 데이터베이스 개체를 만들 때 사용됩니다.
* oracle 데이터베이스의 경우 Adobe Campaign 사용자는 일반적으로 의 멤버로서 Oracle 라이브러리에 액세스할 수 있어야 합니다 **oinstall** 그룹입니다.
* 다음 **[!UICONTROL Set or change the administrator password]** 옵션을 사용하면 관리자 권한이 있는 Adobe Campaign 연산자에 연결된 암호를 입력할 수 있습니다.

  보안을 위해 Adobe Campaign 계정 관리자 암호를 정의하는 것이 좋습니다.

### 5단계 - 데이터베이스 만들기 {#step-5---creating-the-database}

마법사의 마지막 단계에서는 데이터베이스를 만들 수 있습니다. **[!UICONTROL Start]**&#x200B;을(를) 클릭하여 확인합니다.

![](assets/s_ncs_install_db_oracle_creation06.png)

데이터베이스 생성이 완료되면 다시 연결하여 인스턴스 구성을 완료할 수 있습니다.

이제 배포 마법사를 시작하여 인스턴스 구성을 완료해야 합니다. 을(를) 참조하십시오 [배포 마법사](../../installation/using/deploying-an-instance.md#deployment-wizard).

인스턴스에 연결된 데이터베이스의 연결 설정은 파일에 저장됩니다 **`/conf/config-<instance>.xml`** Adobe Campaign 설치 디렉터리에 있습니다.

암호화된 암호를 사용하여 &#39;campaign&#39; 계정에 연결된 base61 데이터베이스의 Microsoft SQL Server 구성의 예:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```
