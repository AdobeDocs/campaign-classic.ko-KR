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

(여기서 **eng** 및 **fra** 다음에 대해 가능한 값: `[lang]` 매개 변수)

명령 **nlserver config -addinstance:instance1/demo&#42;/eng** 을(를) 통해 이라는 인스턴스를 **instance1** DNS 마스크 데모 사용&#42;.

## 데이터베이스 선언 {#declaring-a-database}

다음 구문을 사용하여 명령줄에서 기존 데이터베이스를 인스턴스와 연결할 수 있습니다.

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

다음 값은 다음에 대해 가능합니다. **`[rdbms]`** 매개 변수:

* **postgresql**: PostgreSQL의 경우,
* **oracle**: Oracle의 경우
* **mssql**: Microsoft SQL Server의 경우

다음 명령은 **데모** SQL 유형 서버가 있는 인스턴스(알려진 경우) **base6**, 다음에 연결됨 **campaign** 계정 및 해당 **암호** 다음에 있음 **dbsrv** 서버:

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
