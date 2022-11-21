---
product: campaign
title: Linux 플랫폼을 Adobe Campaign v7로 마이그레이션
description: Linux 플랫폼을 Adobe Campaign v7로 마이그레이션하는 방법 알아보기
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 9dc0699c-0fbf-4f8e-81f7-8ca3d7e98798
source-git-commit: 2594e4943ba24ae65d1fc005da589dc674aa2b0f
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# Linux 플랫폼을 Campaign v7로 마이그레이션{#migrating-in-linux-for-adobe-campaign-v}

![](../../assets/v7-only.svg)

Linux의 마이그레이션 단계는 다음과 같습니다.

1. 모든 서비스 중지 - [추가 정보](#service-stop).
1. 데이터베이스 저장 - [추가 정보](#back-up-the-database).
1. 이전 Adobe Campaign 버전 패키지 제거 - [추가 정보](#uninstalling-adobe-campaign-previous-version-packages).
1. 플랫폼 마이그레이션 - [추가 정보](#deploying-adobe-campaign-v7).
1. 서비스 다시 시작 - [추가 정보](#re-starting-services).

## 서비스 중지 {#service-stop}

먼저 관련 모든 컴퓨터에서 데이터베이스에 대한 액세스 권한을 가진 모든 프로세스를 중지합니다.

1. 다음으로 로그인 **루트**.
1. 리디렉션 모듈을 사용하는 모든 서버(**webmdl** 서비스)를 중지해야 합니다. Apache의 경우 다음 명령을 실행합니다.

   ```
   /etc/init.d/apache2 stop
   ```

1. 다음으로 다시 로그인합니다. **루트**.
1. 모든 서버에서 Adobe Campaign 이전 버전 서비스를 중지합니다.

   ```
   /etc/init.d/nlserver6 stop
   ```

<!--
   If you are migrating from v5.11, run the following command:

   ```
   /etc/init.d/nlserver5 stop
   ```

-->

1. Adobe Campaign 서비스가 각 서버에서 중지되었는지 확인합니다.

   ```
   ps waux | grep nlserver
   ```

   활성 프로세스 목록이 해당 ID(PID)와 함께 표시됩니다.

1. 몇 분 후에도 하나 이상의 Adobe Campaign 프로세스가 여전히 활성 상태이거나 차단되면 해당 프로세스를 종료하십시오.

   ```
   killall nlserver
   ```

1. 일부 프로세스가 몇 분 후에도 여전히 활성 상태인 경우 명령을 사용하여 해당 프로세스를 강제로 닫을 수 있습니다.

   ```
   killall -9 nlserver
   ```

## 데이터베이스 백업 {#back-up-the-database}

<!--

### For Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Make a backup of the Adobe Campaign database. 
1. Log in as **neolane** and make a backup of the **nl5** directory using the following command:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **nl5.back** folder and save it to a secure location other than the server.

1. Edit the **config-`<instance name>`.xml** (in the **nl5.back** folder), to prevent the **mta**, **wfserver**, **stat** etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart** (still as **neolane**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

-->

<!--

### For Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Make a backup of the Adobe Campaign database. 
1. Log in as **neolane** and make a backup of the **nl6** directory using the following command:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **nl6.back** folder and save it to a secure location other than the server.

1. Edit the **config-`<instance name>`.xml** (in the **nl6.back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart** (still as **Adobe Campaign**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

-->

1. Adobe Campaign 데이터베이스를 백업합니다.
1. 다음으로 로그인 **네올란** 그리고 **nl6** 다음 명령을 사용하는 디렉토리:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >예방 조치로, **nl6.back** 폴더를 만든 후 서버가 아닌 보안 위치에 저장합니다.

## Adobe Campaign 이전 버전 패키지 제거 {#uninstalling-adobe-campaign-previous-version-packages}

<!--

### For v5 packages {#uninstalling-adobe-campaign-v5-packages}

1. Log in as **root**.
1. Identify the Adobe Campaign packages installed using the following command.

    * In **Debian**:

      ```    
      dpkg -l | grep nl
      ```    
    
      The list of installed packages is displayed:

      ```    
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

    * In **Red Hat**:

      ```    
      rpm -qa | grep nl
      ```

1. Uninstall Adobe Campaign v5 packages.

    * In **Debian**:

      ```    
      dpkg --purge nlserver5 nlthirdparty5
      ```

    * In **Red Hat**:

      ```    
      rprm -ev nlserver5 nlthirdparty5
      ```

-->

이 섹션에서는 Adobe Campaign v6.1 패키지를 제거하는 방법을 보여줍니다.

1. 다음으로 로그인 **루트**.
1. 다음 명령을 사용하여 설치된 Adobe Campaign 패키지를 식별합니다.

   * in **데비안**:

      ```
      dpkg -l | grep nl
      ```

      설치된 패키지 목록이 표시됩니다.

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * in **빨간색 모자**:

      ```
      rpm -qa | grep nl
      ```

1. Adobe Campaign v6 패키지를 제거합니다.

   * in **데비안**:

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * in **빨간색 모자**:

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## Adobe Campaign v7 배포 {#deploying-adobe-campaign-v7}

v7를 배포하는 절차는 다음과 같습니다.

<!--

### From Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

Deploying Adobe Campaign involves two stages:

* Installing Adobe Campaign v7 packages: this operation must be performed on each server.
* The post upgrade: this command must be started on each instance.

To deploy Adobe Campaign, apply the following steps:

1. Install the most recent Adobe Campaign v7 packages using the following command:

    * In **Debian**:

      ```    
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

    * In **Red Hat**:

      ```    
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```

   >[!IMPORTANT]
   >
   >You must install the packages successfully before going on to the next step.

   >[!NOTE]
   >
   >When migrating from v5.11, Adobe Campaign is installed in the **/usr/local/neolane/nl6/** directory by default.
   >
   >Once the packages are installed, the following message is displayed: **'WdbcTimeZone' option is missing**. This is normal.

1. To make the client console installation program available, copy it into the Adobe Campaign installation directory:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >For more on how to install Adobe Campaign in Linux, refer to [this section](../../installation/using/installing-campaign-standard-packages.md).

1. Modify the **.bashrd** file which matches the **neolane** user. Log on as **neolane** and run the following command:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >When you log in as **neolane**, the following message is displayed: **nl5/env.sh : No such file or directory**. This is normal.

   At the end of the file, replace **nl5/env.sh** with **nl6/env.sh**.

1. Log in as **root** and prepare the instance using the following commands:

   ```
   /etc/init.d/nlserver6 start   
   Starting nlserver6: [  OK  ]
   ```

   ```
   /etc/init.d/nlserver6 stop
   Stopping nlserver6: [  OK  ]
   ```

   >[!NOTE]
   >
   >These commands let you create the Adobe Campaign v6 internal files system: **conf** directory (with the **config-default.xml** and **serverConf.xml** files), **var** directory.

1. Go to the **nl5.back** backup folder and copy (overwrite) the configuration files and sub-folders of each instance. Log in as **neolane** and run the following command:

   >[!IMPORTANT]
   >
   >For the first command below, do not copy the **config-default.xml** file.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. In the Adobe Campaign v7 **serverConf.xml** and **config-default.xml** files, apply the specific configurations that you had for Adobe Campaign v5. For the **serverConf.xml** file, use the **nl5/conf/serverConf.xml.diff** file.

   >[!NOTE]
   >
   >When reporting configurations from Adobe Campaign v5 to Adobe Campaign v7, make sure the paths to the physical directories lead to Adobe Campaign v7 and not Adobe Campaign v5.

1. Since migration is not a generic installation, you need to force the re-starting of the **trackinglogd** service. To do this, open the **nl6/conf/config-default.xml** file and make sure the **trackinglogd** service is activated (only on the tracking/redirection server(s)):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >If the **trackinglogd** service is not started on the tracking server, no tracking information will be forwarded.

1. Reload the Adobe Campaign v7 configuration using the following command:

   ```
   nlserver config -reload
   ```

1. Start the postupgrade process using the following command (still as **neolane**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >You must specify which timezone to use as a reference during the postupgrade (using the **-timezone** option). In this case, we are using the Europe/Paris timezone **-timezone: "Europe/Paris"**.

   >[!NOTE]
   >
   >We strongly recommend upgrading your base to "multi timezone". For further information about timezone options, refer to the [Time zones](../../migration/using/general-configurations.md#time-zones) section.

>[!IMPORTANT]
>
>Do not start Adobe Campaign services yet: changes still need to be made in Apache.

### From Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

Deploying Adobe Campaign involves two stages:

* Installing Adobe Campaign v7 packages: this operation must be performed on each server.
* The post upgrade: this command must be started on each instance.

To deploy Adobe Campaign, apply the following steps:

1. Install the most recent Adobe Campaign v7 packages using the following command:

    * In **Debian**:

      ```    
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

    * In **Red Hat**:

      ```    
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```

   >[!IMPORTANT]
   >
   >You must install the packages successfully before going on to the next step.

   >[!NOTE]
   >
   >Adobe Campaign v7 is installed in the same directory by default as Adobe Campaign v6.02: **/usr/local/neolane/nl6/**.

1. To make the client console installation program available, copy it into the Adobe Campaign installation directory:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >For more on how to install Adobe Campaign in Linux, refer to [this section](../../installation/using/installing-campaign-standard-packages.md).

1. Since migration is not a generic installation, you need to force the re-starting of the **trackinglogd** service. To do this, open the **nl6/conf/config-default.xml** file and make sure the **trackinglogd** service is activated (only on the tracking/redirection server(s)):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >If the **trackinglogd** service is not started on the tracking server, no tracking information will be forwarded.

1. Go to the **nl6.back** backup folder and copy (overwrite) the configuration files and sub-folders of each instance. Log in as **neolane** and run the following command:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Reload the Adobe Campaign v7 configuration using the following command:

   ```
   nlserver config -reload
   ```

1. Start the postupgrade process using the following command (still as **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >The "multi timezone" mode was only available in v6.02 for PostgreSQL database engines. It is now available no matter what version of database engine is being used. We strongly recommend upgrading your base to "multi timezone". For further information about timezone options, refer to the [Time zones](../../migration/using/general-configurations.md#time-zones) section.

-->

Adobe Campaign 배포에는 두 단계가 있습니다.

* Adobe Campaign v7 패키지 설치: 이 작업은 각 서버에서 수행해야 합니다.
* 업그레이드 후: 이 명령은 각 인스턴스에서 시작해야 합니다.

Adobe Campaign을 배포하려면 다음 단계를 수행합니다.

1. 다음 명령을 사용하여 최신 Adobe Campaign v7 패키지를 설치합니다.

   * in **데비안**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * in **빨간색 모자**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >다음 단계로 이동하기 전에 패키지를 제대로 설치해야 합니다.

   >[!NOTE]
   >
   >Adobe Campaign v7은 **/usr/local/neolane/nl6/** 기본적으로 디렉토리.

1. 클라이언트 콘솔 설치 프로그램을 사용 가능하게 하려면 Adobe Campaign 설치 디렉토리에 복사합니다.

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Linux에서 Adobe Campaign을 설치하는 방법에 대한 자세한 내용은 [이 섹션](../../installation/using/installing-campaign-standard-packages.md).

1. 로 이동합니다. **nl6.back** 백업 폴더 및 각 인스턴스의 구성 파일과 하위 폴더를 복사(덮어쓰기)합니다. 다음으로 로그인 **네올란** 다음 명령을 실행합니다.

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. 다음 명령을 사용하여 Adobe Campaign v7 구성을 다시 로드합니다.

   ```
   nlserver config -reload
   ```

1. 다음 명령을 사용하여 업그레이드 후 프로세스를 시작합니다. **네올란**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

<!--

## Migrate the redirection server (Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>This section only applies when migrating from Adobe Campaign v5.11.

At this stage, Apache needs to be stopped. Refer to: [Service stop](#service-stop).

1. Log in as **root**.
1. Change the Apache environment variables to make them link to the **nl6** directory.

    * In **Debian**:

      ```    
      vi /etc/apache2/envvars
      ```

    * In **Red Hat**:

      ```    
      vi /usr/local/apache2/bin/envvars
      ```

1. Then run the following commands:

    * In **Debian**:

      In the **nlsrv.load** file, replace **nl5** with **nl6**.

      ```    
      vi /etc/apache2/mods-available/nlsrv.load
      ```    
    
      Delete the link of the **nlsrv.conf** file and create a new one.

      ```    
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

    * In **Red Hat**:

      Go to the **/usr/local/apache2/conf** directory, edit the **http.conf** file and replace **nl5** with **nl6** in the following lines.

      In **RHEL 7/Debian 8**:

      ```    
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Go to the **alias.conf** file and replace all **nl5** with **nl6**. To do this in Debian, run the following command:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

-->

<!--

## Security zones {#security-zones}

If you are migrating from v6.02 or earlier, you must configure your security zones before starting services. For more information, refer to [Security](../../migration/using/general-configurations.md#security).

-->

## 서비스 다시 시작 {#re-starting-services}

서비스를 다시 시작하는 절차는 다음과 같습니다.

<!--

### For Adobe Campaign v5 {#migrating-from-adobe-campaign-v5_11-2}

In the **config-`<instance name>`.xml** files, reactivate the automatic startup of the **mta**, **wfserver**, **stat**, etc. services.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="localhost"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Start Apache and Adobe Campaign services on each of the following servers:

1. Tracking and redirection server.
1. Mid-sourcing server.
1. Marketing server.

Before going on to the next step, run a full test of the new installation, make sure there are no regressions and that everything works by following all the recommendations in the [General configurations](../../migration/using/general-configurations.md) section.

### For Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

In the **config-`<instance name>`.xml** files, reactivate the automatic startup of the **mta**, **wfserver**, **stat**, etc. services.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="myStatServer"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Start Apache and Adobe Campaign services on each of the following servers:

1. Tracking and redirection server.
1. Mid-sourcing server.
1. Marketing server.

Fully test the new installation, check that it does not regress and make sure that everything is working correctly by following all the recommendations in the [General configurations](../../migration/using/general-configurations.md) section.

-->

다음 각 서버에서 Apache 및 Adobe Campaign 서비스를 시작합니다.

1. 추적 및 리디렉션 서버입니다.
1. 중간 소싱 서버.
1. 마케팅 서버입니다.

새 설치를 완전히 테스트하고, 다시 사용되지 않는지 확인하고, 모든 것이 제대로 작동하는지 확인합니다.

<!--

## Delete the Adobe Campaign previous version {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>This section only applies when migrating from Adobe Campaign v5.11.

Before you delete and cleanse the Adobe Campaign v5 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v5 once you are certain that no rollback is necessary.

Delete the **nl5.back** directory. Log in as **neolane** and run the following command:

```
su - neolane
rm -rf nl5.back
```

Re-start the server.

-->
