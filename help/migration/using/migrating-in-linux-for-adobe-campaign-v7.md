---
product: campaign
title: Linux에서 Adobe Campaign v7으로 마이그레이션
description: Linux에서 Adobe Campaign v7으로 마이그레이션
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 9dc0699c-0fbf-4f8e-81f7-8ca3d7e98798
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1890'
ht-degree: 1%

---

# Linux에서 Adobe Campaign v7으로 마이그레이션{#migrating-in-linux-for-adobe-campaign-v}

![](../../assets/v7-only.svg)

## 일반 절차 {#general-procedure}

Linux의 마이그레이션 단계는 다음과 같습니다.

1. 서비스 중지: 참조 [서비스 중지](#service-stop).
1. 데이터베이스를 저장합니다. 참조 [데이터베이스 및 기존 설치 백업](#back-up-the-database-and-the-existing-installation).
1. 이전 Adobe Campaign 버전 패키지 제거: 참조 [Adobe Campaign 이전 버전 패키지 제거](#uninstalling-adobe-campaign-previous-version-packages).
1. 플랫폼 마이그레이션: 참조 [Adobe Campaign v7 배포](#deploying-adobe-campaign-v7).
1. 서비스 다시 시작: 참조 [서비스 다시 시작](#re-starting-services).

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

   v5.11에서 마이그레이션하는 경우 다음 명령을 실행하십시오.

   ```
   /etc/init.d/nlserver5 stop
   ```

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

## 데이터베이스 및 기존 설치 백업 {#back-up-the-database-and-the-existing-installation}

절차는 Adobe Campaign 이전 버전에 따라 다릅니다.

### Adobe Campaign v5.11에서 마이그레이션 {#migrating-from-adobe-campaign-v5-11}

1. Adobe Campaign 데이터베이스를 백업합니다.
1. 다음으로 로그인 **네올란** 그리고 **nl5** 다음 명령을 사용하는 디렉토리:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >예방 조치로, **nl5.back** 폴더를 만든 후 서버가 아닌 보안 위치에 저장합니다.

1. 편집 **config-`<instance name>`.xml** ( **nl5.back** 폴더)로 이동하는 경우 **mta**, **wfserver**, **stat** 등. 서비스가 자동으로 시작됩니다. 예를 들어, **autoStart** with **_autoStart** (계속) **네올란**).

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

1. Adobe Campaign 데이터베이스를 백업합니다.
1. 다음으로 로그인 **네올란** 그리고 **nl6** 다음 명령을 사용하는 디렉토리:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >예방 조치로, **nl6.back** 폴더를 만든 후 서버가 아닌 보안 위치에 저장합니다.

1. 편집 **config-`<instance name>`.xml** ( **nl6.back** 폴더)를 클릭하여 **mta**, **wfserver**, **stat**&#x200B;등 서비스가 자동으로 시작됩니다. 예를 들어, **autoStart** with **_autoStart** (계속) **Adobe Campaign**).

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

절차는 Adobe Campaign 이전 버전에 따라 다릅니다.

### Adobe Campaign v5 패키지 제거 {#uninstalling-adobe-campaign-v5-packages}

1. 다음으로 로그인 **루트**.
1. 다음 명령을 사용하여 설치된 Adobe Campaign 패키지를 식별합니다.

   * in **데비안**:

      ```
      dpkg -l | grep nl
      ```

      설치된 패키지 목록이 표시됩니다.

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * in **빨간색 모자**:

      ```
      rpm -qa | grep nl
      ```

1. Adobe Campaign v5 패키지를 제거합니다.

   * in **데비안**:

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * in **빨간색 모자**:

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### Adobe Campaign v6 패키지 제거 {#uninstalling-adobe-campaign-v6-packages}

이 섹션에서는 Adobe Campaign v6.02 또는 v6.1 패키지를 제거하는 방법을 보여줍니다.

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

절차는 Adobe Campaign 이전 버전에 따라 다릅니다.

### Adobe Campaign v5.11에서 마이그레이션 {#migrating-from-adobe-campaign-v5_11-1}

Adobe Campaign 배포에는 두 단계가 있습니다.

* Adobe Campaign v7 패키지 설치: 이 작업은 각 서버에서 수행해야 합니다.
* 업그레이드 후: 이 명령은 각 인스턴스에서 시작해야 합니다.

Adobe Campaign을 배포하려면 다음 단계를 수행합니다.

1. 다음 명령을 사용하여 최신 Adobe Campaign v7 패키지를 설치합니다.

   * in **데비안**:

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * in **빨간색 모자**:

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >다음 단계로 이동하기 전에 패키지를 제대로 설치해야 합니다.

   >[!NOTE]
   >
   >v5.11에서 마이그레이션할 때 Adobe Campaign은 **/usr/local/neolane/nl6/** 기본적으로 디렉토리.
   >
   >패키지가 설치되면 다음 메시지가 표시됩니다. **&#39;WdbcTimeZone&#39; 옵션이 없습니다.**. 이는 정상적인 현상입니다.

1. 클라이언트 콘솔 설치 프로그램을 사용 가능하게 하려면 Adobe Campaign 설치 디렉토리에 복사합니다.

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Linux에서 Adobe Campaign을 설치하는 방법에 대한 자세한 내용은 [이 섹션](../../installation/using/installing-campaign-standard-packages.md).

1. 수정 **.bashrd** 일치하는 파일 **네올란** 사용자. 다음으로 로그온 **네올란** 다음 명령을 실행합니다.

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >으로 로그인하는 경우 **네올란**, 다음 메시지가 표시됩니다. **nl5/env.sh : 해당 파일 또는 디렉터리가 없습니다.**. 이는 정상적인 현상입니다.

   파일의 끝 부분에서 **nl5/env.sh** with **nl6/env.sh**.

1. 다음으로 로그인 **루트** 다음 명령을 사용하여 인스턴스를 준비합니다.

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
   >이러한 명령을 사용하여 Adobe Campaign v6 내부 파일 시스템을 만들 수 있습니다. **conf** 디렉토리( **config-default.xml** 및 **serverConf.xml** 파일), **var** 디렉토리.

1. 로 이동합니다. **nl5.back** 백업 폴더 및 각 인스턴스의 구성 파일과 하위 폴더를 복사(덮어쓰기)합니다. 다음으로 로그인 **네올란** 다음 명령을 실행합니다.

   >[!IMPORTANT]
   >
   >아래 첫 번째 명령에 대해 **config-default.xml** 파일.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. Adobe Campaign v7에서 **serverConf.xml** 및 **config-default.xml** 파일에서 Adobe Campaign v5에 대해 지정한 특정 구성을 적용합니다. 대상 **serverConf.xml** 파일에서 **nl5/conf/serverConf.xml.diff** 파일.

   >[!NOTE]
   >
   >Adobe Campaign v5에서 Adobe Campaign v7로 구성을 보고하는 경우, 실제 디렉토리에 대한 경로가 Adobe Campaign v5가 아니라 Adobe Campaign v7로 연결되는지 확인하십시오.

1. 마이그레이션은 일반 설치가 아니므로 를 강제로 다시 시작해야 합니다 **trackinglogd** 서비스. 이렇게 하려면 **nl6/conf/config-default.xml** 파일 및 **trackinglogd** 서비스가 활성화됨(추적/리디렉션 서버에서만):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >만약 **trackinglogd** 서비스가 추적 서버에서 시작되지 않았으므로 추적 정보가 전달되지 않습니다.

1. 다음 명령을 사용하여 Adobe Campaign v7 구성을 다시 로드합니다.

   ```
   nlserver config -reload
   ```

1. 다음 명령을 사용하여 업그레이드 후 프로세스를 시작합니다. **네올란**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >업그레이드 후 를 사용하여 참조로 사용할 시간대를 지정해야 합니다 **-timezone** 선택 사항). 이 경우 유럽/파리 시간대 를 사용합니다 **-timezone: &quot;유럽/파리&quot;**.

   >[!NOTE]
   >
   >기본 시간대를 &quot;다중 시간대&quot;로 업그레이드하는 것이 좋습니다. 시간대 옵션에 대한 자세한 내용은 [시간대](../../migration/using/general-configurations.md#time-zones) 섹션을 참조하십시오.

>[!IMPORTANT]
>
>아직 Adobe Campaign 서비스를 시작하지 마십시오. 여전히 Apache에서 변경 작업을 수행해야 합니다.

### Adobe Campaign v6.02에서 마이그레이션 {#migrating-from-adobe-campaign-v6_02-1}

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
   >Adobe Campaign v7는 기본적으로 Adobe Campaign v6.02와 동일한 디렉토리에 설치됩니다. **/usr/local/neolane/nl6/**.

1. 클라이언트 콘솔 설치 프로그램을 사용 가능하게 하려면 Adobe Campaign 설치 디렉토리에 복사합니다.

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Linux에서 Adobe Campaign을 설치하는 방법에 대한 자세한 내용은 [이 섹션](../../installation/using/installing-campaign-standard-packages.md).

1. 마이그레이션은 일반 설치가 아니므로 를 강제로 다시 시작해야 합니다 **trackinglogd** 서비스. 이렇게 하려면 **nl6/conf/config-default.xml** 파일 및 **trackinglogd** 서비스가 활성화됨(추적/리디렉션 서버에서만):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >만약 **trackinglogd** 서비스가 추적 서버에서 시작되지 않았으므로 추적 정보가 전달되지 않습니다.

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

   >[!NOTE]
   >
   >&quot;다중 시간대&quot; 모드는 PostgreSQL 데이터베이스 엔진용 v6.02에서만 사용할 수 있습니다. 이제 사용 중인 데이터베이스 엔진 버전에 관계없이 사용할 수 있습니다. 기본 시간대를 &quot;다중 시간대&quot;로 업그레이드하는 것이 좋습니다. 시간대 옵션에 대한 자세한 내용은 [시간대](../../migration/using/general-configurations.md#time-zones) 섹션을 참조하십시오.

### Adobe Campaign v6.1에서 마이그레이션 {#migrating-from-adobe-campaign-v6_1-1}

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

## 리디렉션 서버 마이그레이션(Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>이 섹션은 Adobe Campaign v5.11에서 마이그레이션할 때만 적용됩니다.

이 단계에서 Apache를 중지해야 합니다. 다음을 참조하십시오. [서비스 중지](#service-stop).

1. 다음으로 로그인 **루트**.
1. Apache 환경 변수를 로 연결하여 **nl6** 디렉토리.

   * in **데비안**:

      ```
      vi /etc/apache2/envvars
      ```

   * in **빨간색 모자**:

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. 그런 다음 다음 다음 명령을 실행합니다.

   * in **데비안**:

      에서 **nlsrv.load** 파일, 바꾸기 **nl5** with **nl6**.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      링크 삭제 **nlsrv.conf** 파일을 만들고 새 파일을 만듭니다.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * in **빨간색 모자**:

      로 이동합니다. **/usr/local/apache2/conf** 디렉토리, 편집 **http.conf** 파일 및 바꾸기 **nl5** with **nl6** 를 클릭합니다.

      in **RHEL 7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. 로 이동합니다. **alias.conf** 모두 바꾸기 **nl5** with **nl6**. Debian에서 이렇게 하려면 다음 명령을 실행하십시오.

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## 보안 영역 {#security-zones}

v6.02 이전 버전에서 마이그레이션하는 경우 서비스를 시작하기 전에 보안 영역을 구성해야 합니다. 자세한 내용은 [보안](../../migration/using/general-configurations.md#security).

## 서비스 다시 시작 {#re-starting-services}

절차는 Adobe Campaign 이전 버전에 따라 다릅니다.

### Adobe Campaign v5.11에서 마이그레이션 {#migrating-from-adobe-campaign-v5_11-2}

에서 **config-`<instance name>`.xml** 파일을 사용하여 자동 시작 **mta**, **wfserver**, **stat**&#x200B;등 서비스.

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

1. 추적 및 리디렉션 서버입니다.
1. 중간 소싱 서버.
1. 마케팅 서버입니다.

다음 단계로 이동하기 전에 새 설치에 대한 전체 테스트를 실행하고 회귀를 수행하지 않는지 그리고 모든 기능이 의 모든 권장 사항을 수행하여 작동하는지 확인합니다 [일반 구성](../../migration/using/general-configurations.md) 섹션을 참조하십시오.

### Adobe Campaign v6.02에서 마이그레이션 {#migrating-from-adobe-campaign-v6_02-2}

에서 **config-`<instance name>`.xml** 파일을 사용하여 자동 시작 **mta**, **wfserver**, **stat**&#x200B;등 서비스.

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

1. 추적 및 리디렉션 서버입니다.
1. 중간 소싱 서버.
1. 마케팅 서버입니다.

새 설치를 완전히 테스트하고, 다시 사용되지 않는지 확인하고, 의 모든 권장 사항을 수행하여 모든 것이 제대로 작동하는지 확인합니다. [일반 구성](../../migration/using/general-configurations.md) 섹션을 참조하십시오.

### Adobe Campaign v6.1에서 마이그레이션 {#migrating-from-adobe-campaign-v6_1-2}

다음 각 서버에서 Apache 및 Adobe Campaign 서비스를 시작합니다.

1. 추적 및 리디렉션 서버입니다.
1. 중간 소싱 서버.
1. 마케팅 서버입니다.

새 설치를 완전히 테스트하고, 다시 사용되지 않는지 확인하고, 의 모든 권장 사항을 수행하여 모든 것이 제대로 작동하는지 확인합니다. [일반 구성](../../migration/using/general-configurations.md) 섹션을 참조하십시오.

## Adobe Campaign v5 삭제 및 정리 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>이 섹션은 Adobe Campaign v5.11에서 마이그레이션할 때만 적용됩니다.

Adobe Campaign v5 설치를 삭제하고 정리하려면 먼저 다음 권장 사항을 적용해야 합니다.

* 기능 팀이 새 설치를 모두 점검하도록 합니다.
* 롤백이 필요하지 않은지 확인한 후 Adobe Campaign v5만 제거하십시오.

삭제 **nl5.back** 디렉토리. 다음으로 로그인 **네올란** 다음 명령을 실행합니다.

```
su - neolane
rm -rf nl5.back
```

서버를 다시 시작합니다.
