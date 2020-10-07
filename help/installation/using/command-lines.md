---
title: 명령줄
seo-title: 명령줄
description: 명령줄
seo-description: null
page-status-flag: never-activated
uuid: fa897d6a-0326-4922-8936-2471af2f213c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 3621d4ec-8839-40c3-a574-486c408f79ba
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 5%

---


# 명령줄{#command-lines}

다음 명령줄을 사용하려면 응용 프로그램 서버에 액세스하는 기능이 필요합니다. Adobe에서 호스팅하는 배포의 경우 이러한 명령은 Adobe에서만 실행할 수 있습니다.

## 인스턴스 만들기 {#creating-an-instance}

명령 행을 사용하여 다음 구문을 사용하여 인스턴스 생성을 실행할 수 있습니다.

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

( **eng** 및 **fra** 는 `[lang]` 매개 변수값이 가능한 경우)

명령 **nlserver config -adinstance:instance1/demo*/eng** 을 사용하면 DNS 마스크 데모*를 사용하여 **instance1** 이라는 인스턴스를 영어로 만들 수 있습니다.

## 데이터베이스 선언 {#declaring-a-database}

다음 구문을 사용하여 기존 데이터베이스를 명령줄에서 있는 인스턴스와 연결할 수 있습니다.

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

매개 변수에는 다음 값을 사용할 수 **`[rdbms]`** 있습니다.

* **postgresql**:for PostgreSQL,
* **oracle**:for Oracle,
* **mssql**:Microsoft SQL Server용,
* **DB2**:for the DB2 engine.

다음 명령은 **campaign** baseServer에 연결된 SQL 유형 서버 **로**&#x200B;데모 **인스턴스를 구성하고** , 해당 **캠페인** 계정 및 해당 **** 암호를에 구성합니다.

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

