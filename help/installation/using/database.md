---
product: campaign
title: 데이터베이스 권장 사항 Campaign Classic
description: 데이터베이스 권장 사항
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 2%

---

# 데이터베이스{#database}



데이터베이스 서버는 해당 운영 체제에서 응용 프로그램 서버 또는 서버에서 사용하는 운영 체제와 상관없이 해당 운영 체제 간에 네트워크 연결이 있는 한 실행할 수 있습니다.

Adobe Campaign의 다른 구성 요소와의 연결을 사용할 수 있는 한 데이터베이스 서버의 운영 체제는 중요하지 않습니다.

또한 [데이터베이스 액세스 레이어](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) 섹션을 참조하십시오.

## Microsoft SQL Server {#microsoft-sql-server}

기본 클라이언트는 Adobe Campaign 애플리케이션 서버에 설치해야 합니다.

ODBC 드라이버 구성 패널의 **SQL Server Native Client 11.0**.

다음 액세스 DLL이 있어야 합니다. **sqlncli11.dll**.

액세스 DLL은 Microsoft 웹 사이트에서 찾을 수 있습니다.

>[!NOTE]
>
>Linux에서 실행되는 애플리케이션 서버에서 Microsoft SQL Server에 대한 액세스가 지원되지 않습니다.

## Oracle {#oracle}

>[!NOTE]
>
>멀티바이트 문자가 있는 열 이름은 지원되지 않습니다.

다음 **NLS_NCHAR_CHARACTERSET** 및 **NLS_CHARACTERSET** 데이터베이스가 유니코드 또는 ANSI로 작동하려면 매개 변수를 올바르게 구성해야 합니다.

Adobe Campaign은 기본 Oracle 인코딩을 사용합니다. 다른 인코딩을 사용하면 호환성 문제가 발생할 수 있습니다. 이 경우 기술 지원 센터에 문의하십시오.

인코딩에 대해 알아보려면 다음을 사용하십시오 **sqlplus** 명령:

```
SELECT * FROM nls_database_parameters ;
```

* 유니코드 설치의 경우 지원되는 인코딩은 다음과 같습니다.

   ```
   NLS_NCHAR_CHARACTERSET         AL16UTF16
   NLS_CHARACTERSET         AL32UTF8
   ```

* ANSI 설치(유니코드 아님)의 경우 다음 인코딩만 지원됩니다.

```
  NLS_CHARACTERSET WE8MSWIN1252
```

에 로그인하려면 **sqlplus**, Oracle 사용자 프로필 사용:

```
su - oracle 
sqlplus 
[login] [password]
```

다음을 의미할 수도 있습니다 [Linux의 oracle 클라이언트](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

데이터베이스 엔진을 설치할 때 UTF-8 지원을 설치하는 것이 좋습니다. 이렇게 하면 유니코드 데이터베이스를 만들 수 있습니다.

**관련 항목**

* [Adobe Campaign Classic 테이블에서 로그되지 않은 옵션](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
