---
product: campaign
title: 일반적인 명령
description: 일반적인 명령
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 3%

---

# 일반적인 명령{#usual-commands}

![](../../assets/v7-only.svg)

이 섹션에는 Adobe Campaign의 일반적인 명령이 나열됩니다.

명령 **nlserver** 는 전체 Adobe Campaign 애플리케이션에 대한 입력 명령입니다.

이 명령에는 다음 구문이 있습니다. **nlserver **`<command>`****`<arguments>`****

매개 변수 **`<command>`** 는 모듈에 해당합니다.

>[!NOTE]
>
>* 어떤 경우든, **-noconsole** 모듈이 시작되면 표시되는 주석을 삭제하는 인수입니다.
>* 반대로 인수를 추가할 수 있습니다 **-verbose** 추가 정보를 표시합니다.

>


## 명령 모니터링 {#monitoring-commands-}

>[!NOTE]
>
>모든 모듈을 나열하려면 **nlserver pdump** 명령.

매개 변수를 추가할 수 있습니다 **-누가** 진행 중인 연결(데이터베이스 및 응용 프로그램)을 나열하려면 다음을 수행하십시오.

```
nlserver pdump -who
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
web@default (9984) - 50.1 Mo
watchdog (2273) - 6.6 Mo
syslogd@default (9931) - 7.0 Mo
trackinglogd@default (9985) - 45.6 Mo
mta@test (9986) - 9.6 Mo
wfserver@test (9987) - 8.8 Mo

Connections ------------------------------------------------------
Last Access IP Instance Login 
DD/MM/YYYY HH:MM:SS 127.0.0.1 default formation_fr|tracking
DD/MM/YYYY HH:MM:SS 127.0.0.1 default internal|monitoring

Connection pool --------------------------------------------------
Datasource Server Provider Login 
default xxxxx myserver myprovider test400
```

또 다른 유용한 명령은 다음과 같습니다 **nlserver 모니터**. 여기에는 모니터링 XML 파일(Adobe Campaign 클라이언트에서 또는 **monitor.jsp** 웹 페이지).

매개 변수를 추가할 수 있습니다 **-missing** 누락된 모듈(모듈, 모듈 종료 등의 오류)을 나열하려면

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

이 모듈은 자동 시작 모듈에 해당하지만 실행되지 않았습니다.

## 모듈 실행 명령 {#module-launch-commands}

launch 모듈 구문은 여전히 다음 형식을 갖습니다.

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** 는 구성 파일에 입력된 인스턴스의 이름에 해당하거나 **기본** 단일 인스턴스 모듈용.

## 서비스 종료 {#shut-down-services}

Adobe Campaign 서비스를 중지하려면 다음 명령 중 하나를 사용합니다.

* 루트 또는 관리자 액세스 권한이 있는 경우:

   * Linux의 경우:

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >20.1부터 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우). **systectl stop nlserver**

   * Windows에서:

      ```
      net stop nlserver6
      ```

* 없는 경우 Adobe Campaign 계정에서 다음을 수행합니다.

   ```
   nlserver shutdown 
   ```

## 서비스 다시 시작 {#restart-services}

마찬가지로 Adobe Campaign을 다시 시작하기 위해 다음 명령 중 하나를 사용할 수 있습니다.

* 루트 또는 관리자 액세스 권한이 있는 경우:

   * Linux의 경우: /etc/init.d/nlserver6 시작

      >[!NOTE]
      >
      >20.1부터 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우). **systectl start nlserver**

   * Windows에서: net start nlserver6

* 그렇지 않으면 Adobe Campaign 계정에서 다음을 수행합니다. **nlserver watchdog -svc -noconsole**

## 구성 명령 {#the-config-command}

다음 **config** 명령을 사용하면 데이터베이스 연결의 재구성을 포함하여 서버 구성을 관리할 수 있습니다.

를 사용하십시오 **config** 명령 **nlserver** 실행 가능한 파일 **-setdblogin** 매개 변수.

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

암호를 입력합니다.

를 변경하려면 **내부** 암호: **nlserver 구성 -internalpassword**

>[!IMPORTANT]
>
>을 사용하여 로그온하려면 **내부** 식별자, 미리 암호를 정의해야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#internal-identifier)을 참조하십시오.

>[!NOTE]
>
>* 일반적으로 구성 파일을 수동으로 수정하는 대신 **config** 명령
>* 매개 변수 목록을 가져오려면 **-?** 매개 변수: **nlserver 구성 -?**
>* oracle 데이터베이스의 경우 계정을 지정하지 않아야 합니다. 구문은 다음과 같습니다.
>
>  nlserver 구성 -setdblogin:Oracle:test6@dbserver
