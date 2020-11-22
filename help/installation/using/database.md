---
solution: Campaign Classic
product: campaign
title: Campaign Classic 데이터베이스 권장 사항
description: 데이터베이스 권장 사항
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 1%

---


# 데이터베이스{#database}

데이터베이스 서버는 응용 프로그램 서버나 서버에서 사용하는 운영 체제에 관계없이 해당 운영 체제에서 실행될 수 있으며, 이러한 운영 체제들 사이에 네트워크 연결이 있는 경우 이 운영 체제에서는 실행되지 않습니다.

Adobe Campaign의 다른 구성 요소와의 연결이 가능한 한 데이터베이스 서버의 운영 체제가 중요하지 않습니다.

데이터베이스 액세스 [레이어](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) 섹션도 확인합니다.

## Microsoft SQL Server {#microsoft-sql-server}

기본 클라이언트는 Adobe Campaign 응용 프로그램 서버에 설치해야 합니다.

ODBC 드라이버 구성 패널의 **SQL Server Native Client 11.0에서 서버의 기본 클라이언트를 확인할 수 있습니다**.

다음 액세스 DLL이 있어야 합니다. **sqlncli11.dll**.

액세스 DLL은 Microsoft 웹 사이트에서 찾을 수 있습니다.

>[!NOTE]
>
>Linux에서 실행 중인 응용 프로그램 서버에서 Microsoft SQL Server에 액세스할 수 없습니다.

## Oracle {#oracle}

>[!NOTE]
>
>멀티바이트 문자가 있는 열 이름은 지원되지 않습니다.

데이터베이스가 유니코드나 ANSI에서 작동하도록 **NLS_NCHAR_CHARACTERSET** 및 **NLS_CHARACTER** 매개 변수를 올바르게 구성해야 합니다.

Adobe Campaign은 기본 Oracle 인코딩을 사용합니다. 다른 인코딩을 사용하면 호환성 문제가 발생할 수 있습니다.이 경우 기술 지원에 문의하십시오.

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

sqlplus에 **로그온하려면** Oracle 사용자 프로필을 사용합니다.

```
su - oracle 
sqlplus 
[login] [password]
```

Linux에서 [Oracle 클라이언트를 참조할 수도 있습니다](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostresSQL {#postgressql}

데이터베이스 엔진을 설치할 때 UTF-8 지원을 설치하는 것이 좋습니다. 이 방법으로 유니코드 데이터베이스를 만들 수 있습니다.

**관련 항목**

* [Adobe Campaign Classic 테이블의 로그인되지 않은 옵션](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
