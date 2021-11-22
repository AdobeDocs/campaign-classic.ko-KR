---
product: campaign
title: 명령줄
description: 명령줄
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# 명령줄{#command-lines}

![](../../assets/v7-only.svg)

다음 명령줄을 사용하려면 응용 프로그램 서버에 액세스할 수 있어야 합니다. Adobe으로 호스팅되는 배포의 경우 이러한 명령은 Adobe로만 실행할 수 있습니다.

## 인스턴스 만들기 {#creating-an-instance}

다음 구문을 사용하여 명령줄을 사용하여 인스턴스 생성을 실행할 수 있습니다.

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(다음과 같은 경우) **eng** 및 **fra** 에 사용할 수 있는 값은 다음과 같습니다 `[lang]` parameter)

명령 **nlserver config -addinstance:instance1/demo*/eng** 이라는 인스턴스를 만들 수 있습니다. **instance1** DNS 마스크 데모*를 사용하여 영어로 표시합니다.

## 데이터베이스 선언 {#declaring-a-database}

다음 구문을 사용하여 기존 데이터베이스를 명령줄에서 인스턴스와 연결할 수 있습니다.

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

다음 값은 **`[rdbms]`** 매개 변수:

* **postgresql**: PostgreSQL용,
* **oracle**: oracle,
* **mssql**: Microsoft SQL Server용,
* **DB2**: DB2 엔진의 경우

다음 명령은 **데모** SQL 유형 서버가 있는 인스턴스로서, **base6**&#x200B;에 연결된 **campaign** 계정 및 해당 **암호** on **dbsrv** server:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
