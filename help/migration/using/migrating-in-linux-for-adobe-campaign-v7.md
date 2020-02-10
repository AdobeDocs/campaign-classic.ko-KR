---
title: Linux에서 Adobe Campaign v7 마이그레이션
seo-title: Linux에서 Adobe Campaign v7 마이그레이션
description: Linux에서 Adobe Campaign v7 마이그레이션
seo-description: null
page-status-flag: never-activated
uuid: 47870ea4-b07b-4db7-8094-7a8b6f4b6936
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: 8f6519e8-5c8d-4974-b193-a9f1cf78b3a3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Linux에서 Adobe Campaign v7 마이그레이션{#migrating-in-linux-for-adobe-campaign-v}

## 일반 절차 {#general-procedure}

Linux의 마이그레이션 단계는 다음과 같습니다.

1. 서비스 중지:서비스 [중지](#service-stop)보기,
1. 데이터베이스를 저장합니다.데이터베이스 [및 기존 설치](#back-up-the-database-and-the-existing-installation)백업을 참조하십시오.
1. 이전 Adobe Campaign 버전 패키지 제거:adobe [Campaign 이전 버전 패키지](#uninstalling-adobe-campaign-previous-version-packages)제거,
1. 플랫폼 마이그레이션:adobe [Campaign v7](#deploying-adobe-campaign-v7)배포를 참조하십시오.
1. 서비스 다시 시작:서비스 [재시작을](#re-starting-services)참조하십시오.

## 서비스 중지 {#service-stop}

먼저, 관련된 모든 컴퓨터에서 데이터베이스에 대한 액세스 권한을 가진 모든 프로세스를 중지합니다.

1. 루트로 **로그인합니다**.
1. 리디렉션 모듈(**webmdl** 서비스)을 사용하는 모든 서버를 중지해야 합니다. Apache의 경우 다음 명령을 실행합니다.

   ```
   /etc/init.d/apache2 stop
   ```

1. 다시 **루트로**&#x200B;로그인합니다.
1. 모든 서버에서 Adobe Campaign 이전 버전 서비스를 중지합니다.

   ```
   /etc/init.d/nlserver6 stop
   ```

   v5.11에서 마이그레이션하는 경우 다음 명령을 실행합니다.

   ```
   /etc/init.d/nlserver5 stop
   ```

1. 각 서버에서 Adobe Campaign 서비스가 중지되었는지 확인합니다.

   ```
   ps waux | grep nlserver
   ```

   활성 프로세스 목록은 ID(PID)와 함께 표시됩니다.

1. 몇 분 후에도 하나 이상의 Adobe Campaign 프로세스가 활성 상태이거나 차단된 경우 프로세스를 종료합니다.

   ```
   killall nlserver
   ```

1. 몇 분 후에도 일부 프로세스가 여전히 활성 상태인 경우 다음 명령을 사용하여 프로세스를 강제로 닫을 수 있습니다.

   ```
   killall -9 nlserver
   ```

## 데이터베이스 및 기존 설치 백업 {#back-up-the-database-and-the-existing-installation}

절차는 Adobe Campaign 이전 버전에 따라 다릅니다.

### Adobe Campaign v5.11에서 마이그레이션 {#migrating-from-adobe-campaign-v5-11}

1. Adobe Campaign 데이터베이스의 백업을 만듭니다.
1. 다음 명령을 **사용하여 Neolane** 으로 로그인하고 **nl5** 디렉토리를 백업합니다.

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!CAUTION]
   >
   >예방 차원에서, **nl5.back** 폴더를 압축한 후 서버 이외의 보안 위치에 저장하는 것이 좋습니다.

1. config- **`<instance name>`.xml** ( **nl5.back** 폴더)을 편집하여 **mta, wfserver, FormatsFormats,** StatFormats 등을 ******** 방지합니다. 서비스가 자동으로 시작됩니다. 예를 들어 autoStart를 **_autoStart** ( **neolane** )로 **바꿉니다**.

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

### Adobe Campaign v6.02에서 마이그레이션 {#migrating-from-adobe-campaign-v6-02}

1. Adobe Campaign 데이터베이스의 백업을 만듭니다.
1. 다음 명령을 **사용하여 Neolane** 으로 로그인하고 **nl6** 디렉토리를 백업합니다.

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!CAUTION]
   >
   >예방 차원에서, **nl6.back** 폴더를 압축한 후 서버 이외의 보안 위치에 저장하는 것이 좋습니다.

1. mta, wfserver, **costatStatStatus, etc를`<instance name>`방지하려면** nl6.back **폴더에서** config- **.xml을 편집합니다**********. 서비스가 자동으로 시작됩니다. 예를 들어 autoStart를 **_autoStart** (여전히 Adobe Campaign **으로** )로 **바꿉니다**.

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

### Adobe Campaign v6.1에서 마이그레이션 {#migrating-from-adobe-campaign-v6-1}

1. Adobe Campaign 데이터베이스의 백업을 만듭니다.
1. 다음 명령을 **사용하여 Neolane** 으로 로그인하고 **nl6** 디렉토리를 백업합니다.

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!CAUTION]
   >
   >예방 차원에서, **nl6.back** 폴더를 압축한 후 서버 이외의 보안 위치에 저장하는 것이 좋습니다.

## Adobe Campaign 이전 버전 패키지 제거 {#uninstalling-adobe-campaign-previous-version-packages}

절차는 Adobe Campaign 이전 버전에 따라 다릅니다.

### Adobe Campaign v5 패키지 제거 {#uninstalling-adobe-campaign-v5-packages}

1. 루트로 **로그인합니다**.
1. 다음 명령을 사용하여 설치된 Adobe Campaign 패키지를 식별합니다.

   * 디베이어 ****:

      ```
      dpkg -l | grep nl
      ```

      설치된 패키지 목록이 표시됩니다.

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * Red **Hat**:

      ```
      rpm -qa | grep nl
      ```

1. Adobe Campaign v5 패키지를 제거합니다.

   * 디베이어 ****:

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * Red **Hat**:

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### Adobe Campaign v6 패키지 제거 {#uninstalling-adobe-campaign-v6-packages}

이 섹션에서는 Adobe Campaign v6.02 또는 v6.1 패키지를 제거하는 방법을 보여 줍니다.

1. 루트로 **로그인합니다**.
1. 다음 명령을 사용하여 설치된 Adobe Campaign 패키지를 식별합니다.

   * 디베이어 ****:

      ```
      dpkg -l | grep nl
      ```

      설치된 패키지 목록이 표시됩니다.

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * Red **Hat**:

      ```
      rpm -qa | grep nl
      ```

1. Adobe Campaign v6 패키지를 제거합니다.

   * 디베이어 ****:

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * Red **Hat**:

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## Adobe Campaign v7 배포 {#deploying-adobe-campaign-v7}

절차는 Adobe Campaign 이전 버전에 따라 다릅니다.

### Adobe Campaign v5.11에서 마이그레이션 {#migrating-from-adobe-campaign-v5_11-1}

Adobe Campaign 배포에는 두 가지 단계가 포함됩니다.

* Adobe Campaign v7 패키지 설치:이 작업은 각 서버에서 수행해야 합니다.
* 업그레이드 후:이 명령은 각 인스턴스에서 시작해야 합니다.

Adobe Campaign을 배포하려면 다음 단계를 적용합니다.

1. 다음 명령을 사용하여 최신 Adobe Campaign v7 패키지를 설치합니다.

   * 디베이어 ****:

      ```
      dpkg -i nlserver6-v7-XXXX-linux-2.6-intel.deb
      ```

   * Red **Hat**:

      ```
      rpm -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
      ```
   >[!CAUTION]
   >
   >다음 단계로 진행하기 전에 패키지를 성공적으로 설치해야 합니다.

   >[!NOTE]
   >
   >v5.11에서 마이그레이션할 때 Adobe Campaign은 기본적으로 **/usr/local/neolane/nl6/** 디렉토리에 설치됩니다.
   >
   >패키지가 설치되면 다음 메시지가 표시됩니다.&#39; **WdbcTimeZone&#39; 옵션이 없습니다**. 정상입니다.

1. 클라이언트 콘솔 설치 프로그램을 사용 가능하게 하려면 Adobe Campaign 설치 디렉토리에 복사합니다.

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Linux에서 Adobe Campaign을 설치하는 방법에 대한 자세한 내용은 [이 섹션을](../../installation/using/installing-campaign-standard-packages.md)참조하십시오.

1. neolane **사용자와 일치하는 .bashrd** 파일을 **** 수정합니다. Neolane으로 **로그온하고** 다음 명령을 실행합니다.

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >Neolane으로 **로그인하면**&#x200B;다음 메시지가 표시됩니다. **nl5/env.sh :해당 파일이나 디렉토리가**&#x200B;없습니다. 정상입니다.

   파일의 끝에서 nl5/env.sh를 nl6/env.sh **로** 바꿉니다 ****.

1. 루트로 **로그인하고** 다음 명령을 사용하여 인스턴스를 준비합니다.

   ```
   /etc/init.d/nlserver6-v7 start   
   Starting nlserver6-v7: [  OK  ]
   ```

   ```
   /etc/init.d/nlserver6-v7 stop
   Stopping nlserver6-v7: [  OK  ]
   ```

   >[!NOTE]
   >
   >다음 명령을 사용하여 Adobe Campaign v6 내부 파일 시스템을 만들 수 있습니다.conf **디렉토리(** config-default.xml **및** serverConf.xml **파일 포함)** 는 var **** 디렉토리입니다.

1. nl5. **back** 백업 폴더로 이동하여 각 인스턴스의 구성 파일과 하위 폴더를 복사(덮어쓰기)합니다. neolane으로 **로그인하고** 다음 명령을 실행합니다.

   >[!CAUTION]
   >
   >아래의 첫 번째 명령에 대해서는 **config-default.xml** 파일을 복사하지 마십시오.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. Adobe Campaign v7 **serverConf.xml** 및 **config-default.xml** 파일에서 Adobe Campaign v5에 대해 가지고 있던 특정 구성을 적용합니다. serverConf. **xml** 파일의 경우 nl5/conf/serverConf.xml. **diff** 파일을 사용합니다.

   >[!NOTE]
   >
   >Adobe Campaign v5에서 Adobe Campaign v7로 구성을 보고할 때 실제 디렉토리 경로가 Adobe Campaign v5가 아닌 Adobe Campaign v7으로 연결되는지 확인하십시오.

1. 마이그레이션은 일반 설치가 아니므로 추적 **로그 서비스의 다시 시작을 수행해야 합니다** . 이렇게 하려면 nl6/conf/config-default.xml **파일을** 열고 **trackinglogd** 서비스가 활성화되었는지 확인합니다(추적/리디렉션 서버에서만).

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!CAUTION]
   >
   >추적 **로그** 서비스가 추적 서버에서 시작되지 않으면 추적 정보가 전달되지 않습니다.

1. 다음 명령을 사용하여 Adobe Campaign v7 구성을 다시 로드합니다.

   ```
   nlserver config -reload
   ```

1. 다음 명령을 사용하여 업그레이드 후 프로세스를 시작합니다(여전히 **neolane**).

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!CAUTION]
   >
   >사후 업그레이드 시 참조할 표준 시간대를 지정해야 합니다( **-timezone** 옵션 사용). 이 경우 유럽/파리 시간대 **시간대를 사용합니다.&quot;유럽/파리&quot;**.

   >[!NOTE]
   >
   >&quot;다중 시간대&quot;로 업그레이드할 것을 적극 권장합니다. 시간대 옵션에 대한 자세한 내용은 시간대 [섹션을](../../migration/using/general-configurations.md#time-zones) 참조하십시오.

>[!CAUTION]
>
>Adobe Campaign 서비스를 아직 시작하지 마십시오.변경 사항은 Apache에서 계속 수행해야 합니다.

### Adobe Campaign v6.02에서 마이그레이션 {#migrating-from-adobe-campaign-v6_02-1}

Adobe Campaign 배포에는 두 가지 단계가 포함됩니다.

* Adobe Campaign v7 패키지 설치:이 작업은 각 서버에서 수행해야 합니다.
* 업그레이드 후:이 명령은 각 인스턴스에서 시작해야 합니다.

Adobe Campaign을 배포하려면 다음 단계를 적용합니다.

1. 다음 명령을 사용하여 최신 Adobe Campaign v7 패키지를 설치합니다.

   * 디베이어 ****:

      ```
      dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
      ```

   * Red **Hat**:

      ```
      rpm -Uvh nlserver6-v7-XXXX-x86_64_rhX.rpm
      ```
   >[!CAUTION]
   >
   >다음 단계로 진행하기 전에 패키지를 성공적으로 설치해야 합니다.

   >[!NOTE]
   >
   >Adobe Campaign v7은 기본적으로 Adobe Campaign v6.02와 동일한 디렉토리에 설치됩니다./usr/local/neolane/nl6/ ****.

1. 클라이언트 콘솔 설치 프로그램을 사용 가능하게 하려면 Adobe Campaign 설치 디렉토리에 복사합니다.

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Linux에서 Adobe Campaign을 설치하는 방법에 대한 자세한 내용은 [이 섹션을](../../installation/using/installing-campaign-standard-packages.md)참조하십시오.

1. 마이그레이션은 일반 설치가 아니므로 추적 **로그 서비스의 다시 시작을 수행해야 합니다** . 이렇게 하려면 nl6/conf/config-default.xml **파일을** 열고 **trackinglogd** 서비스가 활성화되었는지 확인합니다(추적/리디렉션 서버에서만).

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!CAUTION]
   >
   >추적 **로그** 서비스가 추적 서버에서 시작되지 않으면 추적 정보가 전달되지 않습니다.

1. nl6. **back** 백업 폴더로 이동하여 각 인스턴스의 구성 파일과 하위 폴더를 복사(덮어쓰기)합니다. neolane으로 **로그인하고** 다음 명령을 실행합니다.

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

1. 다음 명령을 사용하여 업그레이드 후 프로세스를 시작합니다(여전히 **neolane**).

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >&quot;multi timezone&quot; 모드는 PostgreSQL 데이터베이스 엔진에 대해 v6.02에서만 사용할 수 있었습니다. 이제 사용 중인 데이터베이스 엔진 버전에 관계없이 사용할 수 있습니다. &quot;다중 시간대&quot;로 업그레이드할 것을 적극 권장합니다. 시간대 옵션에 대한 자세한 내용은 시간대 [섹션을](../../migration/using/general-configurations.md#time-zones) 참조하십시오.

### Adobe Campaign v6.1에서 마이그레이션 {#migrating-from-adobe-campaign-v6_1-1}

Adobe Campaign 배포에는 두 가지 단계가 포함됩니다.

* Adobe Campaign v7 패키지 설치:이 작업은 각 서버에서 수행해야 합니다.
* 업그레이드 후:이 명령은 각 인스턴스에서 시작해야 합니다.

Adobe Campaign을 배포하려면 다음 단계를 적용합니다.

1. 다음 명령을 사용하여 최신 Adobe Campaign v7 패키지를 설치합니다.

   * 디베이어 ****:

      ```
      dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
      ```

   * Red **Hat**:

      ```
      rpm -Uvh nlserver6-v7-XXXX-x86_64_rhX.rpm
      ```
   >[!CAUTION]
   >
   >다음 단계로 진행하기 전에 패키지를 성공적으로 설치해야 합니다.

   >[!NOTE]
   >
   >Adobe Campaign v7은 기본적으로 **/usr/local/neolane/nl6/** 디렉토리에 설치됩니다.

1. 클라이언트 콘솔 설치 프로그램을 사용 가능하게 하려면 Adobe Campaign 설치 디렉토리에 복사합니다.

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Linux에서 Adobe Campaign을 설치하는 방법에 대한 자세한 내용은 [이 섹션을](../../installation/using/installing-campaign-standard-packages.md)참조하십시오.

1. nl6. **back** 백업 폴더로 이동하여 각 인스턴스의 구성 파일과 하위 폴더를 복사(덮어쓰기)합니다. neolane으로 **로그인하고** 다음 명령을 실행합니다.

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

1. 다음 명령을 사용하여 업그레이드 후 프로세스를 시작합니다(여전히 **neolane**).

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## 리디렉션 서버 마이그레이션(Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>이 섹션은 Adobe Campaign v5.11에서 마이그레이션할 때만 적용됩니다.

이 단계에서 Apache를 중지해야 합니다. 참조:서비스 [중지](#service-stop).

1. 루트로 **로그인합니다**.
1. Apache 환경 변수를 변경하여 **nl6** 디렉토리로 연결합니다.

   * 디베이어 ****:

      ```
      vi /etc/apache2/envvars
      ```

   * Red **Hat**:

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. 그런 다음 다음 다음 명령을 실행합니다.

   * 디베이어 ****:

      nlsrv.load **파일에서** nl5를 **nl6로** 바꿉니다 ****.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      nlsrv.conf **파일의 링크를** 삭제하고 새 파일을 만듭니다.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * Red **Hat**:

      사용자/usr/local/local/conf **디렉토리로 이동하여** http.conf **파일을 편집하고** nl5 **를** nl6 **** 로 바꿉니다.

      RHEL **6/Debian 7**:

      ```
      LoadModule requesthandler22_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

      RHEL **7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. alias.conf **파일로 이동하여 모든** nl5를 **nl6로** 바꿉니다 ****. Debian에서 이렇게 하려면 다음 명령을 실행하십시오.

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## 보안 영역 {#security-zones}

v6.02 이전 버전에서 마이그레이션하는 경우 서비스를 시작하기 전에 보안 영역을 구성해야 합니다. 자세한 내용은 보안을 [참조하십시오](../../migration/using/general-configurations.md#security).

## 서비스 다시 시작 {#re-starting-services}

절차는 Adobe Campaign 이전 버전에 따라 다릅니다.

### Adobe Campaign v5.11에서 마이그레이션 {#migrating-from-adobe-campaign-v5_11-2}

config- **.xml`<instance name>`파일에서** mta **, Wfserver,** stat **Behance, etc******&#x200B;의 자동 시작을 다시 활성화합니다. 서비스.

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

다음 각 서버에서 Apache 및 Adobe Campaign 서비스를 시작합니다.

1. 추적 및 리디렉션 서버
1. 중간 소싱 서버.
1. 마케팅 서버.

다음 단계로 이동하기 전에 새 설치에 대한 전체 테스트를 실행하고 일반 구성 [](../../migration/using/general-configurations.md) 섹션의 모든 권장 사항을 수행하여 회귀 현상이 없는지 확인합니다.

### Adobe Campaign v6.02에서 마이그레이션 {#migrating-from-adobe-campaign-v6_02-2}

config- **.xml`<instance name>`파일에서** mta **, Wfserver,** stat **Behance, etc******&#x200B;의 자동 시작을 다시 활성화합니다. 서비스.

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

다음 각 서버에서 Apache 및 Adobe Campaign 서비스를 시작합니다.

1. 추적 및 리디렉션 서버
1. 중간 소싱 서버.
1. 마케팅 서버.

새 설치를 완전히 테스트하고, 보고서가 등록되지 않는지 확인하고, 일반 구성 [섹션의 모든 권장 사항을 수행하여 모든 것이 제대로 작동하는지](../../migration/using/general-configurations.md) 확인합니다.

### Adobe Campaign v6.1에서 마이그레이션 {#migrating-from-adobe-campaign-v6_1-2}

다음 각 서버에서 Apache 및 Adobe Campaign 서비스를 시작합니다.

1. 추적 및 리디렉션 서버
1. 중간 소싱 서버.
1. 마케팅 서버.

새 설치를 완전히 테스트하고, 보고서가 등록되지 않는지 확인하고, 일반 구성 [섹션의 모든 권장 사항을 수행하여 모든 것이 제대로 작동하는지](../../migration/using/general-configurations.md) 확인합니다.

## Adobe Campaign v5 삭제 및 정리 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>이 섹션은 Adobe Campaign v5.11에서 마이그레이션할 때만 적용됩니다.

Adobe Campaign v5 설치를 삭제하고 정리하기 전에 다음 권장 사항을 적용해야 합니다.

* 기능 팀에서 새로운 설치 상태를 모두 점검합니다.
* 롤백이 필요하지 않다고 확신하면 Adobe Campaign v5만 제거합니다.

nl5. **back** 디렉토리를 삭제합니다. neolane으로 **로그인하고** 다음 명령을 실행합니다.

```
su - neolane
rm -rf nl5.back
```

서버를 다시 시작합니다.
