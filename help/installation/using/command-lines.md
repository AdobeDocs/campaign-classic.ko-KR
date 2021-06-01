---
product: campaign
title: 명령줄
description: 명령줄
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# 명령줄{#command-lines}

다음 명령줄을 사용하려면 응용 프로그램 서버에 액세스할 수 있어야 합니다. Adobe으로 호스팅되는 배포의 경우 이러한 명령은 Adobe로만 실행할 수 있습니다.

## 인스턴스 {#creating-an-instance} 만들기

다음 구문을 사용하여 명령줄을 사용하여 인스턴스 생성을 실행할 수 있습니다.

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(여기서 **eng** 및 **fra**&#x200B;는 `[lang]` 매개 변수에 사용할 수 있는 값)

**nlserver config -adinstance:instance1/demo*/eng** 명령을 사용하면 DNS 마스크 데모*를 사용하여 영어로 **instance1**&#x200B;라는 인스턴스를 만들 수 있습니다.

## 데이터베이스 선언 {#declaring-a-database}

다음 구문을 사용하여 기존 데이터베이스를 명령줄에서 인스턴스와 연결할 수 있습니다.

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

**`[rdbms]`** 매개 변수에는 다음 값을 사용할 수 있습니다.

* **postgresql**:PostgreSQL용,
* **oracle**:oracle,
* **mssql**:Microsoft SQL Server용,
* **DB2**:DB2 엔진의 경우

다음 명령은 **campaign** 계정 및 **dbsrv** 서버의 **암호**&#x200B;에 연결된 **base6**&#x200B;이라는 SQL 유형 서버로 **데모** 인스턴스를 구성합니다.

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
