---
title: 복제 환경
seo-title: 복제 환경
description: 복제 환경
seo-description: null
page-status-flag: never-activated
uuid: b8fb8083-e3ec-4b1c-9449-73ac03508d89
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 9f7118f4-aef0-469c-bbe1-b62bed674faa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cb44d439c6866d94f8e1201575ab3d3094d6ad79
workflow-type: tm+mt
source-wordcount: '1291'
ht-degree: 0%

---


# 복제 환경{#duplicating-environments}

## 소개 {#introduction}

### 개요 {#overview}

>[!CAUTION]
>
>서버 및 데이터베이스(호스팅 환경)에 대한 액세스 권한이 없는 경우 아래 설명된 절차를 수행할 수 없습니다. Adobe에 문의하십시오.

Adobe Campaign을 사용하려면 하나 이상의 환경을 설치하고 구성해야 합니다. 개발, 테스트, 프리 프로덕션, 프로덕션 등

각 환경에는 Adobe Campaign 인스턴스가 포함되어 있으며 각 Adobe Campaign 인스턴스가 하나 이상의 데이터베이스에 연결되어 있습니다. 응용 프로그램 서버는 하나 이상의 프로세스를 실행할 수 있습니다. 이들 중 거의 모든 것이 인스턴스 데이터베이스에 직접 액세스할 수 있습니다.

이 섹션에서는 소스 환경을 대상 환경으로 복원하여 두 개의 동일한 작업 환경을 만드는 등 Adobe Campaign 환경을 복제하는 데 적용되는 프로세스에 대해 자세히 설명합니다.

To do this, apply the following steps:

1. 소스 환경의 모든 인스턴스에 데이터베이스의 사본을 생성합니다.
1. 대상 환경의 모든 인스턴스에서 이러한 복사본을 복원합니다.
1. 시작하기 전에 **대상 환경에서 nms:동결인스턴스.js** 자막 스크립트를 실행합니다.

   이 프로세스는 서버와 구성에 영향을 주지 않습니다.

   >[!NOTE]
   >
   >In the context of Adobe Campaign, a **cauterization** combines actions that let you stop all processes interacting with the outside: logs, tracking, deliveries, campaign workflows, etc.\
   >This step is necessary to avoid delivering messages several times (once from the nominal environment and one from the duplicated environment).

   >[!CAUTION]
   >
   >하나의 환경에 여러 인스턴스가 포함될 수 있습니다. Each Adobe Campaign instance is subjected to a license contract. Check your license agreement to see how many environments you can have.\
   >The procedure below lets you transfer an environment without impacting the number of environments and instances you have installed.

### Before you start {#before-you-start}

>[!CAUTION]
>
>We strongly recommend running a full backup of the databases for all instances of the source and target environments before starting the transfer process. This way if a problem occurs, you will be able to restore the backups and return to your initial configuration.

In order for this process to work, the source and target environments must have the same number of instances, the same purpose (marketing instance, delivery instance) and similar configurations. 기술 구성은 소프트웨어 사전 요구 사항을 준수해야 합니다. The same components must be installed on both environments.

## 구현 {#implementation}

### Transfer procedure {#transfer-procedure}

This section will help you understand the steps required for transferring a source environment to a target environment via a case study: our aim here is to restore a production environment (**prod** instance) to a development environment (**dev** instance) to work in a context that is as close as possible to the &#39;live&#39; platform.

The following steps must be performed with great care: some processes may still be in progress when the source environment databases are copied. Cauterization (step 3 below) prevents messages from being sent twice and maintains data consistency.

>[!CAUTION]
>
>* 다음 절차는 PostgreSQL 언어로 유효합니다. SQL 언어가 다른 경우(예: Oracle) SQL 쿼리를 수정해야 합니다.
>* 아래 명령은 **prod** 인스턴스 컨텍스트 및 PostgreSQL 아래의 **개발** 인스턴스 내에적용됩니다.
>



### 1단계 - 소스 환경(prod) 데이터의 백업 만들기 {#step-1---make-a-backup-of-the-source-environment--prod--data}

데이터베이스 복사

먼저 소스 환경 데이터베이스를 모두 복사하십시오. 작업은 데이터베이스 엔진에 따라 다르며 데이터베이스 관리자의 책임입니다.

PostgreSQL 아래에서 명령은 다음과 같습니다.

```
pg_dump mydatabase > mydatabase.sql
```

### 2단계 - 대상 환경 구성(개발) 내보내기 {#step-2---export-the-target-environment-configuration--dev-}

대부분의 구성 요소는 각 환경에 대해 다릅니다. 외부 계정(mid-sourcing, routing 등), 기술 옵션(플랫폼 이름, 데이터베이스 ID, 이메일 주소 및 기본 URL 등)

대상 데이터베이스에 소스 데이터베이스를 저장하기 전에 대상 환경(dev) 구성을 내보내야 합니다. 이렇게 하려면 다음 두 표의 컨텐츠를 내보냅니다. **xtkoption** 및 **nmsextaccount**.

This export lets you keep the dev configuration and only refresh dev data (workflows, templates, Web applications, recipients, etc.).

이렇게 하려면 다음 두 요소에 대해 패키지 내보내기를 수행합니다.

* 다음 **내부 이름을 가진 레코드 없이 xtk:option** 테이블을 &#39;options_dev.xml&#39; 파일로 내보냅니다. &#39;WdbcTimeZone&#39;, &#39;NmsServer_LastPostUpgrade&#39; 및 &#39;NmsBroadcast_RegexRules&#39;.
* &#39;extaccount_dev.xml&#39; 파일에서 ID가 0(@id &lt;> 0)이 아닌 모든 레코드에 **대해 nms:extAccount** 테이블을 내보냅니다.

내보낸 옵션/계정 수가 각 파일에서 내보낼 줄 수와 같은지 확인합니다.

>[!NOTE]
>
>패키지 내보내기에서 내보낼 줄 수는 1,000줄입니다. 옵션이나 외부 계정 수가 1,000개를 초과하는 경우, 여러 개의 수출을 수행해야 합니다.
> 
>For more information, refer to [this section](../../platform/using/working-with-data-packages.md#exporting-packages).

>[!NOTE]
>
>nmsextaccount 테이블을 내보낼 때 외부 계정과 관련된 암호(예: 중간 소싱, 메시지 센터 실행, SMPP, IMS 및 기타 외부 계정의 암호)가 내보내지지 않습니다. 외부 계정을 다시 환경에 가져온 후 다시 입력해야 할 수도 있으므로 올바른 암호를 미리 이용할 수 있는지 확인하십시오.

### 3단계 - 대상 환경 중지(개발) {#step-3---stop-the-target-environment--dev-}

모든 대상 환경 서버에서 Adobe Campaign 프로세스를 중지해야 합니다. 이 작업은 운영 체제에 따라 다릅니다.

모든 프로세스를 중지하거나 데이터베이스에 쓰는 프로세스만 중지할 수 있습니다.

모든 프로세스를 중지하려면 다음 명령을 사용합니다.

* Windows:

   ```
   net stop nlserver6
   ```

* Linux:

   ```
   /etc/init.d/nlserver6 stop
   ```

Use the following command to check that all processes have been stopped:

```
nlserver pdump
```

>[!NOTE]
>
>Windows에서는 다른 작업에 영향을 주지 않고 **웹** 프로세스를 계속 실행할 수 있습니다.

실행 중인 시스템 프로세스가 없는지 확인할 수도 있습니다.

To do this, use the following process:

* In Windows: open the **Task manager** and check that there are no **nlserver.exe** processes.
* Linux: ps **aux 실행 | grep nlserver** 명령 및 nlserver **프로세스가 없는지** 확인하십시오.

### Step 4 - Restore the databases in the target environment (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

대상 환경에서 소스 데이터베이스를 복원하려면 다음 명령을 사용합니다.

```
psql mydatabase < mydatabase.sql
```

### Step 5 - Cauterize the target environment (dev) {#step-5---cauterize-the-target-environment--dev-}

잘못된 기능을 방지하려면 대상 환경이 활성화될 때 배달 전송 및 워크플로우 실행에 연결된 프로세스가 자동으로 실행되지 않아야 합니다.

이렇게 하려면 다음 명령을 실행합니다.

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### 6단계 - 확인 {#step-6---check-cauterization}

1. ID가 0으로 설정된 배달부만 있는지 확인하십시오.

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. Check that the delivery status update is correct:

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. Check that the workflow status update is correct:

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### Step 7 - Restart the target environment Web process (dev) {#step-7---restart-the-target-environment-web-process--dev-}

On the target environment, re-start the Adobe Campaign processes for all servers.

>[!NOTE]
>
>Before re-starting Adobe Campaign on the **dev** environment, you can apply an additional safety procedure: start the **web** module only.
>  
>To do this, edit your instance&#39;s configuration file (**config-dev.xml**), then add the &quot;_&quot; character before the autoStart=&quot;true&quot; options for each module (mta, stat, etc.).

Run the following command to start the Web process:

```
nlserver start web
```

Use the following command to check that only the web process has started:

```
nlserver pdump
```

클라이언트 콘솔 기능에 대한 액세스를 확인합니다.

### Step 8 - Import options and external accounts into the target environment (dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!CAUTION]
>
>Only the web process should be started at this step. If this is not the case, stop other running processes before continuing

Above all, check the values of several lines of the files before importing (for example: &#39;NmsTracking_Pointer&#39; for the options table and the delivery or mid-sourcing accounts for the external account table)

To import the configuration from the target environment database (dev):

1. Open the admin console of the database and purge the external accounts (table nms:extAccount) whose ID is not 0 (@id &lt;> 0).
1. In the Adobe Campaign console, import the options_dev.xml package previously created via the import package functionality.

   Check that the options have indeed been updated in the **[!UICONTROL Administration > Platform > Options]** node.

1. In the Adobe Campaign console, import the extaccount_dev.xml previously created via the import package functionality

   Check that external databases have indeed been imported in the **[!UICONTROL Administration > Platform > External accounts]** .

### Step 9 - Restart all processes and change users (dev) {#step-9---restart-all-processes-and-change-users--dev-}

To start the Adobe Campaign processes, use the following commands:

* In Windows:

   ```
   net start nlserver6
   ```

* Linux:

   ```
   /etc/init.d/nlserver6 start
   ```

Use the following command to check that the processes are started:

```
nlserver pdump
```

Change users to find the users that already existed on the dev platform.
