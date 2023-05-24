---
product: campaign
title: PostgreSQL 액세스 구성
description: PostgreSQL에 대한 액세스를 구성하는 방법 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 1%

---

# PostgreSQL 액세스 구성 {#configure-fda-postgresql}



Campaign 사용 **페더레이션 데이터 액세스** (FDA) 외부 PostgreSQL 데이터베이스에 저장된 정보를 처리하는 옵션입니다.

## PostgreSQL 구성 {#postgresql-configuration}

먼저 Libpq를 설치해야 합니다. Libpq를 사용하면 클라이언트 프로그램에서 PostgreSQL 백엔드 서버로 쿼리를 보내고 이러한 쿼리의 결과를 받을 수 있습니다.

액세스 권한을 구성하려면 아래 단계를 따르십시오. [!DNL PostgreSQL]:

* CentOS의 경우 다음 명령을 실행합니다 `sudo apt-get -y install libpq-dev`.

* Linux의 경우 다음 명령을 실행합니다 `yum install postgresql-devel`.

* Windows의 경우 Libpq는 `libpq.dll` Adobe Campaign 설치에 포함되어 있습니다.

그런 다음 Adobe Campaign에서 다음을 구성할 수 있습니다. [!DNL PostgreSQL] 외부 계정입니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#postgresql-external).

## PostgreSQL 외부 계정 {#postgresql-external}

>[!NOTE]
>
> PostgreSQL은 CentOS 7 및 6에서 사용할 수 있습니다.

다음을 만들어야 합니다. [!DNL PostgreSQL] Campaign 인스턴스를 [!DNL PostgreSQL] 외부 데이터베이스.

1. 출처: Campaign **[!UICONTROL Explorer]**, 클릭 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

1. 선택 **[!UICONTROL External database]** 외부 계정으로 **[!UICONTROL Type]**.

1. 아래 **[!UICONTROL Configuration]**, 선택 [!DNL PostgreSQL, Greenplum] 다음에서 **[!UICONTROL Type]** 드롭다운.

   ![](assets/postgresql_1.png)

1. 구성 **[!UICONTROL PostgreSQL]** 외부 계정 인증:

   * **[!UICONTROL Server]**: 의 URL [!DNL PostgreSQL] 서버입니다.

   * **[!UICONTROL Account]**: 사용자의 이름입니다.

   * **[!UICONTROL Password]**: 사용자 계정 암호.

   * **[!UICONTROL Database]**: 데이터베이스 이름(선택 사항).

   * **[!UICONTROL Working schema]**: 작업 스키마의 이름입니다. [자세히 알아보기](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Timezone]**: 표준 시간대 설정 [!DNL PostgreSQL]. [자세히 알아보기](https://www.postgresql.org/docs/7.2/timezones.html)

1. 다음을 클릭합니다. **[!UICONTROL Parameters]** 탭을 클릭한 다음 **[!UICONTROL Deploy functions]** 단추를 클릭하여 함수를 만듭니다.

   >[!NOTE]
   >
   >모든 함수를 사용할 수 있으려면 원격 데이터베이스에 Adobe Campaign SQL 함수를 만들어야 합니다. 자세한 내용은 다음을 참조하십시오. [페이지](../../configuration/using/adding-additional-sql-functions.md).

1. 클릭 **[!UICONTROL Save]** 구성이 완료되면.

커넥터는 다음 옵션을 지원합니다.

| 옵션 | 설명 |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | 연결 최대 대기 시간(초). <br>자세한 내용은 다음을 참조하십시오. [PostgreSQL 설명서](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT). |
| PGSQL_KEEPALIVES_IDLE | TCP가 서버에 keepalive 메시지를 전송해야 하는 비활성 시간(초)입니다. <br>자세한 내용은 다음을 참조하십시오. [PostgreSQL 설명서](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE). |
| PGSQL_KEEPALIVES_INTBL | 서버에서 승인하지 않은 TCP keepalive 메시지를 다시 전송해야 하는 시간(초).  <br>자세한 내용은 다음을 참조하십시오. [PostgreSQL 설명서](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL). |
| PGSQL_KEEPALIVES_CNT | 클라이언트가 서버에 연결되어 있지 않은 것으로 간주되기 전에 손실될 수 있는 TCP 보관 파일 수입니다. <br>자세한 내용은 다음을 참조하십시오. [PostgreSQL 설명서](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT). |
