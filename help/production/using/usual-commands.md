---
product: campaign
title: 일반적인 명령
description: 일반적인 명령
feature: Monitoring
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: b8a6a0db27826309456c285c08d4f1d85de70283
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 4%

---

# 일반적인 명령{#usual-commands}



이 섹션에는 Adobe Campaign의 일반적인 명령이 나열됩니다.

**nlserver** 명령은 전체 Adobe Campaign 응용 프로그램에 대한 입력 명령입니다.

이 명령에는 다음 구문이 있습니다. **nlserver **`<command>`****`<arguments>`****

**`<command>`** 매개 변수는 모듈에 해당합니다.

>[!NOTE]
>
>* 어떤 경우든 **-noconsole** 인수를 추가하여 모듈이 시작되면 표시되는 주석을 삭제할 수 있습니다.
>* 반대로 **-verbose** 인수를 추가하여 자세한 정보를 표시할 수 있습니다.
>

## 명령 모니터링 {#monitoring-commands-}

>[!NOTE]
>
>모든 모듈을 나열하려면 **nlserver pdump** 명령을 사용해야 합니다.

**-who** 매개 변수를 추가하여 진행 중인 연결(데이터베이스 및 응용 프로그램)을 나열할 수 있습니다.

```sql
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

다른 유용한 명령은 **nlserver monitor**&#x200B;입니다. 모니터링 XML 파일(Adobe Campaign 클라이언트 또는 **monitor.jsp** 웹 페이지를 통해 가져옴)이 나열됩니다.

**-missing** 매개 변수를 추가하여 누락된 모듈을 나열할 수 있습니다(모듈, 모듈 종료 등의 오류).

```sql
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

이는 자동 시작이 있지만 실행되지 않은 모듈에 해당합니다.

## 모듈 실행 명령 {#module-launch-commands}

모듈을 시작하는 구문은 여전히 다음 형식을 갖습니다.

```sql
nlserver start <module>@<INSTANCE>
```

```sql
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`**&#x200B;은(는) 구성 파일에 입력한 인스턴스 이름에 해당하거나, 모노 인스턴스 모듈의 경우 **default**&#x200B;입니다.

## 서비스 종료 {#shut-down-services}

Adobe Campaign 서비스를 중지하려면 다음 명령 중 하나를 사용하십시오.

* 루트 또는 관리자 액세스 권한이 있는 경우:

   * Linux에서:

     ```sql
     /etc/init.d/nlserver6 stop
     ```

     >[!NOTE]
     >
     >20.1부터 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우). **systemctl stop nlserver**

   * Windows에서는:

     ```sql
     net stop nlserver6
     ```

* 그렇지 않은 경우 Adobe Campaign 계정에서 다음을 수행합니다.

  ```sql
  nlserver shutdown 
  ```

## 서비스 다시 시작 {#restart-services}

마찬가지로 Adobe Campaign을 다시 시작하려면 다음 명령 중 하나를 사용할 수 있습니다.

* 루트 또는 관리자 액세스 권한이 있는 경우:

   * Linux에서: `/etc/init.d/nlserver6 start`

     >[!NOTE]
     >
     >20.1부터는 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우). **systemctl start nlserver**

   * Windows에서: `net start nlserver6`

* 그렇지 않으면 Adobe Campaign 계정에서 다음을 수행합니다. **nlserver watchdog -svc -noconsole**

## config 명령 {#the-config-command}

**config** 명령을 사용하면 데이터베이스 연결 재구성을 포함하여 서버 구성을 관리할 수 있습니다.

**-setdblogin** 매개 변수와 함께 **nlserver** 실행 파일의 **config** 명령을 사용합니다.

```sql
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```sql
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

암호를 입력합니다.

**내부** 암호를 변경하려면: **nlserver config -internalpassword**

>[!IMPORTANT]
>
>**내부** 식별자로 로그온하려면 미리 암호를 정의해야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#internal-identifier)을 참조하십시오.

>[!NOTE]
>
>* 일반적으로 수동으로 구성 파일을 수정하는 대신 **config** 명령을 사용할 수 있습니다
>* 매개 변수 목록을 가져오려면 **-?** 매개 변수: **nlserver 구성 -?**
>* Oracle 데이터베이스의 경우 계정을 지정하지 않아야 합니다. 구문은 다음과 같습니다.
>
>  `nlserver config -setdblogin:Oracle:test6@dbserver`
>

다음은 MSSQL의 예입니다.

```sql
nlserver config -setdblogin:mssql:<login>/"<password>"@<server> -instance:<instance_name> 
```

* config-&lt;instance_name>.xml 파일의 dataSource 노드에서 로그인(예: account:user) 및 서버를 찾을 수 있습니다.
* 암호는 따옴표 &quot;&quot;로 묶어야 합니다.

