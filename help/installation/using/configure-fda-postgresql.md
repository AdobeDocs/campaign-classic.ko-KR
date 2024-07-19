---
product: campaign
title: PostgreSQL 액세스 구성
description: PostgreSQL에 대한 액세스를 구성하는 방법 알아보기
feature: Installation, Instance Settings
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 2%

---

# PostgreSQL 액세스 구성 {#configure-fda-postgresql}



Campaign **FDA(Federated Data Access**) 옵션을 사용하여 외부 PostgreSQL 데이터베이스에 저장된 정보를 처리합니다.

## PostgreSQL 구성 {#postgresql-configuration}

먼저 Libpq를 설치해야 합니다. Libpq를 사용하면 클라이언트 프로그램에서 PostgreSQL 백엔드 서버로 쿼리를 보내고 이러한 쿼리의 결과를 받을 수 있습니다.

[!DNL PostgreSQL]에 대한 액세스를 구성하려면 아래 단계를 따르십시오.

* CentOS의 경우 `sudo apt-get -y install libpq-dev` 명령을 실행합니다.

* Linux의 경우 `yum install postgresql-devel` 명령을 실행합니다.

* Windows의 경우 Libpq는 Adobe Campaign 설치에 포함된 `libpq.dll`을(를) 통해 구현됩니다.

그런 다음 Adobe Campaign에서 [!DNL PostgreSQL] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#postgresql-external)을 참조하세요.

## PostgreSQL 외부 계정 {#postgresql-external}

>[!NOTE]
>
> PostgreSQL은 CentOS 7 및 6에서 사용할 수 있습니다.

Campaign 인스턴스를 [!DNL PostgreSQL] 외부 데이터베이스에 연결하려면 [!DNL PostgreSQL] 외부 계정을 만들어야 합니다.

1. **[!UICONTROL Explorer]** 캠페인에서 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

1. **[!UICONTROL External database]**&#x200B;을(를) 외부 계정의 **[!UICONTROL Type]**(으)로 선택합니다.

1. **[!UICONTROL Configuration]**&#x200B;의 **[!UICONTROL Type]** 드롭다운에서 [!DNL PostgreSQL, Greenplum]을(를) 선택합니다.

   ![](assets/postgresql_1.png)

1. **[!UICONTROL PostgreSQL]** 외부 계정 인증을 구성합니다.

   * **[!UICONTROL Server]**: [!DNL PostgreSQL] 서버의 URL.

   * **[!UICONTROL Account]**: 사용자의 이름입니다.

   * **[!UICONTROL Password]**: 사용자 계정 암호입니다.

   * **[!UICONTROL Database]**: 데이터베이스의 이름입니다(선택 사항).

   * **[!UICONTROL Working schema]**: 작업 스키마의 이름입니다. [자세히 알아보기](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Timezone]**: [!DNL PostgreSQL]에 설정된 시간대입니다. [자세히 알아보기](https://www.postgresql.org/docs/7.2/timezones.html)

1. **[!UICONTROL Parameters]** 탭을 클릭한 다음 **[!UICONTROL Deploy functions]** 단추를 클릭하여 함수를 만듭니다.

   >[!NOTE]
   >
   >모든 함수를 사용할 수 있으려면 원격 데이터베이스에 Adobe Campaign SQL 함수를 만들어야 합니다. 자세한 정보는 이 [페이지](../../configuration/using/adding-additional-sql-functions.md)를 참조하세요.

1. 구성이 완료되면 **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

커넥터는 다음 옵션을 지원합니다.

| 옵션 | 설명 |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | 연결 최대 대기 시간(초). <br>자세한 내용은 [PostgreSQL 설명서](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT)를 참조하세요. |
| PGSQL_KEEPALIVES_IDLE | TCP가 서버에 keepalive 메시지를 전송해야 하는 비활성 시간(초)입니다. <br>자세한 내용은 [PostgreSQL 설명서](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE)를 참조하세요. |
| PGSQL_KEEPALIVES_INTBL | 서버에서 승인하지 않은 TCP keepalive 메시지를 다시 전송해야 하는 시간(초).  <br>자세한 내용은 [PostgreSQL 설명서](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL)를 참조하세요. |
| PGSQL_KEEPALIVES_CNT | 클라이언트가 서버에 연결되어 있지 않은 것으로 간주되기 전에 손실될 수 있는 TCP 보관 파일 수입니다. <br>자세한 내용은 [PostgreSQL 설명서](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT)를 참조하세요. |
