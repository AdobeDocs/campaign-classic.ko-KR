---
product: campaign
title: 일반적인 명령
description: 일반적인 명령
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 4%

---

# 일반적인 명령{#usual-commands}



이 섹션에는 Adobe Campaign의 일반적인 명령이 나열됩니다.

명령 **nlserver** 는 전체 Adobe Campaign 애플리케이션에 대한 입력 명령입니다.

이 명령에는 다음 구문이 있습니다. **nlserver **`<command>`****`<arguments>`****

매개 변수 **`<command>`** 모듈에 해당합니다.

>[!NOTE]
>
>* 원하는 경우 다음을 추가할 수 있습니다. **-noconsole** 모듈이 시작되면 표시되는 주석을 삭제하는 인수
>* 반대로 인수를 추가할 수 있습니다 **-verbose** 을 클릭하여 추가 정보를 표시합니다.
>


## 명령 모니터링 {#monitoring-commands-}

>[!NOTE]
>
>모든 모듈을 나열하려면 **nlserver 덤프** 명령입니다.

매개 변수를 추가할 수 있습니다 **-후** 진행 중인 연결을 나열합니다(데이터베이스 및 응용 프로그램).

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

또 다른 유용한 명령은 입니다. **nlserver 모니터**. Adobe Campaign 클라이언트에서 또는 를 통해 얻은 모니터링 XML 파일이 나열됩니다. **monitor.jsp** 웹 페이지).

매개 변수를 추가할 수 있습니다 **-missing** 누락된 모듈을 나열하려면(모듈 오류, 모듈 종료 등)

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

이는 자동 시작이 있지만 실행되지 않은 모듈에 해당합니다.

## 모듈 실행 명령 {#module-launch-commands}

모듈을 시작하는 구문은 여전히 다음 형식을 갖습니다.

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** 는 구성 파일에 입력한 인스턴스 이름에 해당합니다. 또는 **기본값** 단일 인스턴스 모듈의 경우.

## 서비스 종료 {#shut-down-services}

Adobe Campaign 서비스를 중지하려면 다음 명령 중 하나를 사용하십시오.

* 루트 또는 관리자 액세스 권한이 있는 경우:

   * Linux에서:

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >20.1부터 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우). **systemctl stop nlserver**

   * Windows에서는:

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

   * Linux에서: /etc/init.d/nlserver6 start

      >[!NOTE]
      >
      >20.1부터 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우). **systemctl start nlserver**

   * Windows: net start nlserver6

* 그렇지 않으면 Adobe Campaign 계정에서 다음을 수행합니다. **nlserver watchdog -svc -noconsole**

## config 명령 {#the-config-command}

다음 **config** 명령을 사용하면 데이터베이스 연결 재구성을 포함하여 서버 구성을 관리할 수 있습니다.

사용 **config** 명령 **nlserver** 이 포함된 실행 파일 **-setdblogin** 매개 변수.

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

암호를 입력합니다.

을(를) 변경하려면 **내부** 암호: **nlserver 구성 -internalpassword**

>[!IMPORTANT]
>
>로 로그온하려면 **내부** 식별자, 암호를 미리 정의해야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#internal-identifier)을 참조하십시오.

>[!NOTE]
>
>* 일반적으로 구성 파일을 직접 수정하는 대신 **config** 명령
>* 매개 변수 목록을 가져오려면 **-?** 매개 변수: **nlserver 구성 -?**
>* oracle 데이터베이스의 경우 계정을 지정하지 않아야 합니다. 구문은 다음과 같습니다.
>
>  nlserver config -setdblogin:Oracle:test6@dbserver
