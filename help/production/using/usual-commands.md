---
title: 일반적인 명령
seo-title: 일반적인 명령
description: 일반적인 명령
seo-description: null
page-status-flag: never-activated
uuid: f06df8c0-d4ec-4d6b-84d5-f46d852388a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 90718075-87a7-4e9a-935b-571010908e79
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# 일반적인 명령{#usual-commands}

이 섹션에는 Adobe Campaign의 일반적인 명령이 나열됩니다.

명령 **nlserver** 는 전체 Adobe Campaign 애플리케이션에 대한 입력 명령입니다.

이 명령에는 다음 구문이 있습니다. **nlserver **`<command>`****`<arguments>`****

매개 변수는 모듈에 **`<command>`** 해당합니다.

>[!NOTE]
>
>* 어떤 경우든 모듈을 시작한 후 **표시되는 주석을 삭제하기 위해 noconsole** 인수를 추가할 수 있습니다.
>* 반대로 인수 세부 정보를 추가하여 **자세한** 정보를 표시할 수 있습니다.
>



## 모니터링 명령 {#monitoring-commands-}

>[!NOTE]
>
>모든 모듈을 나열하려면 nlserver pdump **명령을 사용해야** 합니다.

매개 변수 **담당자를** 추가하여 진행 중인 연결(데이터베이스 및 응용 프로그램)을 나열할 수 있습니다.

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

다른 유용한 명령은 **nlserver 모니터입니다**. 여기에는 모니터링 XML 파일(Adobe Campaign 클라이언트 또는 **monitor.jsp** 웹 페이지를 통해 얻음)이 나열됩니다.

매개 변수 **누락** (모듈 오류, 모듈 종료 등)을 추가하여 없는 모듈을 나열할 수 있습니다.

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

이것은 자동 시작 기능이 있지만 실행되지 않은 모듈과 일치합니다.

## 모듈 시작 명령 {#module-launch-commands}

모듈 실행 구문에는 여전히 다음 형식이 있습니다.

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** 구성 파일에 입력된 인스턴스 이름 또는 모노 인스턴스 모듈의 **기본값** .

## 서비스 종료 {#shut-down-services}

Adobe Campaign 서비스를 중지하려면 다음 명령 중 하나를 사용하십시오.

* 루트 또는 관리자 액세스 권한이 있는 경우:

   * Linux:

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >20.1부터는 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우). **systemctl stop nlserver**

   * Windows:

      ```
      net stop nlserver6
      ```

* 그렇지 않은 경우 Adobe Campaign 계정에서 다음을 수행합니다.

   ```
   nlserver shutdown 
   ```

## 서비스 다시 시작 {#restart-services}

마찬가지로 Adobe Campaign을 다시 시작하려면 다음 명령 중 하나를 사용할 수 있습니다.

* 루트 또는 관리자 액세스 권한이 있는 경우:

   * Linux:/etc/init.d/nlserver6 시작

      >[!NOTE]
      >
      >20.1부터는 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우). **systemctl start nlserver**

   * Windows:net start nlserver6

* 그렇지 않으면 Adobe Campaign 계정에서 다음을 수행합니다. **nlserver watchdog -svc -noconsole**

## 구성 명령 {#the-config-command}

config **** 명령을 사용하면 데이터베이스 연결 재구성을 포함하여 서버 구성을 관리할 수 있습니다.

nlserver **실행 파일의** config **명령을** -setdblogin **매개 변수와 함께 사용합니다** .

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

암호를 입력합니다.

**내부** 암호를 변경하려면 **nlserver config -internalpassword**

>[!CAUTION]
>
>내부 식별자를 사용하여 **로그온하려면** 미리 암호를 정의해야 합니다. For more on this, refer to [this section](../../installation/using/campaign-server-configuration.md#internal-identifier).

>[!NOTE]
>
>* 일반적으로 구성 파일을 수동으로 수정하는 대신 **config** 명령을 사용할 수 있습니다
>* 매개 변수 목록을 보려면 **-?** parameter: **nlserver config -?**
>* Oracle 데이터베이스의 경우 계정을 지정할 수 없습니다. 구문은 다음과 같습니다.
>
>  
nlserver config -setdblogin:Oracle:test6@dbserver


