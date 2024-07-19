---
product: campaign
title: 명령줄
description: 명령줄
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 4%

---

# 명령줄{#command-lines}



다음 명령줄에는 응용 프로그램 서버에 액세스하는 기능이 필요합니다. Adobe에서 호스팅하는 배포의 경우 이러한 명령은 Adobe에서만 실행할 수 있습니다.

## 인스턴스 만들기 {#creating-an-instance}

다음 구문을 사용하는 명령줄을 사용하여 인스턴스 생성을 실행할 수 있습니다.

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

(여기서 **eng** 및 **fra**&#x200B;은(는) `[lang]` 매개 변수에 사용할 수 있는 값입니다.)

**nlserver config -addinstance:instance1/demo&#42;/eng** 명령을 사용하면 DNS 마스크 demo&#42;을(를) 사용하여 영어로 **instance1**&#x200B;이라는 인스턴스를 만들 수 있습니다.

## 데이터베이스 선언 {#declaring-a-database}

다음 구문을 사용하여 명령줄에서 기존 데이터베이스를 인스턴스와 연결할 수 있습니다.

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

**`[rdbms]`** 매개 변수에는 다음 값을 사용할 수 있습니다.

* **postgresql**: PostgreSQL의 경우
* **oracle**: Oracle,
* **mssql**: Microsoft SQL Server의 경우

다음 명령은 **dbsrv** 서버에서 **campaign** 계정 및 해당 **password**&#x200B;에 연결된 SQL 유형 서버(**base6**)를 사용하여 **demo** 인스턴스를 구성합니다.

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
