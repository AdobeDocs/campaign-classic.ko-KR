---
product: campaign
title: Campaign Classic 데이터베이스 권장 사항
description: 데이터베이스 권장 사항
feature: Installation, Instance Settings
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 2%

---

# 데이터베이스{#database}



데이터베이스 서버는 애플리케이션 서버나 서버 간에 네트워크 연결이 있는 한 애플리케이션 서버에서 사용하는 운영 체제와 상관없이 지정된 운영 체제에서 실행할 수 있습니다.

Adobe Campaign의 다양한 구성 요소와의 연결을 사용할 수 있는 한 데이터베이스 서버의 운영 체제는 중요하지 않습니다.

[데이터베이스 액세스 계층](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) 섹션도 확인하십시오.

## Microsoft SQL Server {#microsoft-sql-server}

Adobe Campaign 애플리케이션 서버에 기본 클라이언트를 설치해야 합니다.

**SQL Server Native Client 11.0**&#x200B;의 ODBC 드라이버 구성 패널을 통해 서버의 네이티브 클라이언트를 확인할 수 있습니다.

액세스 DLL **sqlncli11.dll**&#x200B;이(가) 있어야 합니다.

액세스 DLL은 Microsoft 웹 사이트에 있습니다.

>[!NOTE]
>
>Linux에서 실행 중인 응용 프로그램 서버에서 Microsoft SQL Server에 액세스할 수 없습니다.

## Oracle {#oracle}

>[!NOTE]
>
>멀티바이트 문자가 있는 열 이름은 지원되지 않습니다.

데이터베이스가 유니코드 또는 ANSI로 작동하려면 **NLS_NCHAR_CHARACTERSET** 및 **NLS_CHARACTERSET** 매개 변수를 올바르게 구성해야 합니다.

Adobe Campaign은 기본 Oracle 인코딩을 사용합니다. 다른 인코딩을 사용하면 호환성 문제가 트리거될 수 있습니다. 이 경우 기술 지원에 문의하십시오.

인코딩에 대해 알아보려면 다음 **sqlplus** 명령을 사용하십시오.

```
SELECT * FROM nls_database_parameters ;
```

* 유니코드 설치의 경우 지원되는 인코딩은 다음과 같습니다.

  ```
  NLS_NCHAR_CHARACTERSET         AL16UTF16
  NLS_CHARACTERSET         AL32UTF8
  ```

* ANSI 설치(비유니코드)의 경우 다음 인코딩만 지원됩니다.

```
  NLS_CHARACTERSET WE8MSWIN1252
```

**sqlplus**&#x200B;에 로그온하려면 Oracle 사용자 프로필을 사용하십시오.

```
su - oracle 
sqlplus 
[login] [password]
```

Linux에서 [Oracle 클라이언트](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux)도 참조할 수 있습니다.

## PostgresSQL {#postgressql}

데이터베이스 엔진을 설치할 때 UTF-8 지원을 설치하는 것이 좋습니다. 이렇게 하면 유니코드 데이터베이스를 만들 수 있습니다.

**관련 항목**

* [Adobe Campaign Classic 테이블의 로그되지 않은 옵션](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
