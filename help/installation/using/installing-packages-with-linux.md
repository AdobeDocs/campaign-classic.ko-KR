---
product: campaign
title: Linux를 사용하여 패키지 설치
description: Linux를 사용하여 패키지 설치
feature: Installation, Application Settings
badge-v7-prem: label="온-프레미스 및 하이브리드" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 0%

---

# Linux를 사용하여 패키지 설치{#installing-packages-with-linux}



Linux 32비트 플랫폼의 경우 Adobe Campaign 32비트를 설치합니다. Linux 64비트 플랫폼의 경우 Adobe Campaign 64비트를 설치합니다.

이러한 각 버전에 대해 Adobe Campaign에는 하나의 패키지가 제공됩니다. **nlserver**. 이 패키지에는 특정 버전에 대한 바이너리 및 구성 파일이 들어 있습니다.

설치 명령을 사용하여 다음을 수행할 수 있습니다.

* 파일 복사 위치: **/usr/local/neolane**
* 다음을 사용하여 만든 Adobe Campaign Linux 계정(및 관련 그룹) 만들기 **/usr/local/neolane** 홈 디렉터리로
* 자동 스크립트 만들기 **/etc/init.d/nlserver6** 를 시작할 때 사용하거나 시스템 단위(20.1부터)를 만듭니다.

>[!NOTE]
>
>다음 **Neolane** 명령이 실행되기 전에 시스템 사용자가 만들어지지 않아야 합니다. 다음 **Neolane** 설치 중에 사용자가 자동으로 만들어집니다.
>
>다음 **홈** 에 연결된 디렉토리 **Neolane** 사용자는에서 자동으로 생성됩니다. **[!UICONTROL /usr/local/neolane]**. 에 충분한 공간이 있는지 확인하십시오. **[!UICONTROL /usr/local]** 디스크(몇 GB).

다음을 실행할 수 있습니다. **ping`hostname`** 서버에 연결할 수 있는지 확인하는 명령입니다.

## RPM 패키지를 기반으로 배포 {#distribution-based-on-rpm--packages}

RPM(RHEL, CentOS 및 SUSE) 운영 체제에 Adobe Campaign을 설치하려면 다음 단계를 적용합니다.

1. 먼저 Adobe Campaign 패키지를 얻어야 합니다.

   파일 이름은 다음과 같이 지정됩니다. 여기서 **XXXX** 는 Adobe Campaign 빌드 번호입니다. **nlserver6-v7-XXXX-0.x86_64.rpm**.

   >[!CAUTION]
   >
   >이 섹션의 명령 샘플에서 사용 중인 Adobe Campaign 버전에 올바른 파일 이름을 사용해야 합니다.

1. 설치하려면 다음으로 연결 **루트** 다음 명령을 실행합니다. 여기서 **XXXX** 는 Adobe Campaign 빌드 번호입니다).

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   rpm 파일은 CentOS/Red Hat 배포판에서 찾을 수 있는 패키지에 종속되어 있습니다. 이러한 종속성 중 일부를 사용하지 않으려면(예: OpenJDK 대신 Oracle JDK를 사용하려는 경우) rpm의 &quot;nodeps&quot; 옵션을 사용해야 할 수 있습니다.

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

보고서 실행에 필요한 &#39;bc&#39; 명령(참조: [이 섹션](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) 자세한 내용) 모든 Linux 배포판에서 기본적으로 를 사용할 수 없습니다. 명령을 사용할 수 있는지 확인하려면 &#39;which bc&#39; 명령을 실행합니다. 그렇지 않으면 설치해야 합니다.

CentOS를 사용하는 경우 bc.x86_64 패키지: connect as 를 설치해야 합니다. **루트** 다음 명령을 실행합니다.

```
yum install bc.x86_64
```

## APT 기반 배포(Debian) {#distribution-based-on-apt--debian-}

### Debian 64비트 {#in-debian-64-bits}

Debian 64비트 운영 체제에 Adobe Campaign 64비트를 설치하려면 다음 단계를 적용합니다.

1. 먼저 Adobe Campaign 패키지를 얻어야 합니다. **nlserver6-v7-XXXX-linux-2.6-amd64.deb**, 여기서 **XXXX** 는 빌드 번호입니다.

   >[!CAUTION]
   >
   >이 섹션의 명령 샘플에서 사용 중인 Adobe Campaign 버전에 올바른 파일 이름을 사용해야 합니다.

1. 설치하려면 다음으로 연결 **루트** 다음 명령을 실행합니다. 여기서 **XXXX** 는 Adobe Campaign 빌드 번호입니다).

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   누락된 종속성이 있는 경우 다음 명령을 실행합니다.

   ```
   apt-get install -f
   ```

**Debian 8/9 세부 사항**

Debian 8/9 운영 체제에 Adobe Campaign을 설치할 때 다음 사항을 고려하십시오.

* OpenSSL을 미리 설치해야 합니다.
* 다음 명령을 사용하여 libicu52(Debian 8) 또는 libicu57(Debian 9), libprotobuf9(Debian8) 및 libc-ares2를 설치합니다.

  ```
  aptitude install libicu52 (Debian 8) libicu57 (Debian 9)
  ```

  ```
  aptitude install libc-ares2
  ```

  ```
  aptitude install libprotobuf9 (only Debian 8)
  ```

* 다음 명령을 사용하여 JDK7을 설치합니다.

  ```
  aptitude install openjdk-7-jdk (Debian 8)
  ```

  ```
  aptitude install openjdk-7-jdk (Debian 9)
  ```

## 매개 변수 개인화 {#personalizing-parameters}

일부 매개변수는 다음을 통해 개인화할 수 있습니다. **customer.sh** 파일

설치를 처음 수행하는 경우 **customer.sh** 파일이 서버에 아직 없을 수 있습니다. 만들고 실행 권한이 있는지 확인합니다. 그렇지 않은 경우 다음 명령을 입력합니다.

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### 서버 인코딩 {#server-encoding}

기본적으로 서버는 iso8859-15 환경에서 시작됩니다. 그러나 서버는 UTF-8 환경에서 시작할 수 있습니다.

>[!CAUTION]
>
>이 변경 사항은 파일 시스템(워크플로우 또는 JavaScript 스크립트를 통해 로드된 파일)과의 상호 작용 및 파일 인코딩에 영향을 줍니다. 따라서 기본 환경을 사용하는 것이 좋습니다.

그럼에도 불구하고 **일본어 인스턴스**, UTF-8 환경을 사용해야 합니다.

UTF-8 환경을 활성화하려면 다음 명령을 사용합니다.

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### 서버의 기본 언어 {#default-language-for-the-server}

설치는 영어와 프랑스어를 모두 지원합니다. 기본적으로 영어가 사용됩니다.

프랑스어로 전환하려면 다음 명령을 입력합니다.

```
su - neolane
vi nl6/customer.sh
```

다음 줄을 추가합니다.

```
export neolane_LANG=fra
```

시스템 메시지가 올바르게 읽히도록 하려면 콘솔이 해당 언어(프랑스어의 경우 ISO-8859-1 또는 -15)에 해당하는 코드 페이지에 있어야 합니다.

### 환경 변수 {#environment-variables}

다음 환경 변수를 올바르게 정의해야 합니다.

특정 조합에는 Adobe Campaign 실행에 사용되는 환경을 변경해야 합니다. 특정 파일(`/usr/local/neolane/nl6/customer.sh`)을 만들고 편집하여 Adobe Campaign 환경과 관련된 수정 사항을 추가할 수 있습니다.

필요한 경우 **customer.sh** 를 사용하는 파일 **vi customer.sh** 명령 및 구성을 조정하거나 누락된 줄을 추가합니다.

* oracle 클라이언트의 경우:

  ```
  export ORACLE_HOME=/usr/local/instantclient_10_2
  export TNS_ADMIN=/etc/oracle
  export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
  ```

  oracle_HOME 환경 변수의 내용은 Oracle 설치 디렉토리와 일치합니다.

  TNS_ADMIN 변수의 콘텐츠는 의 위치와 일치해야 합니다. **tnsnames.ora** 파일.

* LibreOffice의 경우:

  기존 버전의 LibreOffice에서 Adobe Campaign을 실행하려면 추가 구성이 필요합니다. 설치 디렉터리에 대한 액세스 경로를 지정해야 합니다. 예:

   * Debian

     OOO_INSTALL_DIR 및 OOO_BASIS_INSTALL_DIR의 기본값이 제공됩니다. 다음에서 재정의할 수 있습니다. **customer.sh** LibreOffice 설치 레이아웃이 다른 경우:

     ```
     export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
     export OOO_INSTALL_DIR=/usr/lib/libreoffice/
     ```

   * CentOs

     다음 기본값을 사용합니다.

     ```
     export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
     export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
     ```

* Java 개발 키트(JDK)의 경우:

  기본적으로 Adobe Campaign 환경의 구성 스크립트(`~/nl6/env.sh`)에서 JDK 설치 디렉토리를 검색합니다. 이 동작은 100% 신뢰할 수 없으므로 사용해야 하는 JDK를 지정해야 합니다. 이렇게 하려면 다음을 강제 적용할 수 있습니다. **JDK_HOME** 다음 명령을 사용하는 환경 변수입니다.

  ```
  export JDK_HOME=/usr/java/jdk1.6.0_07
  ```

  >[!NOTE]
  >
  >예. 사용된 JDK 버전이 디렉터리 이름과 일치하는지 확인합니다.

  JDK 구성을 테스트하려면 다음 명령을 사용하여 Adobe Campaign 시스템 사용자로 로그인합니다.

  ```
  su - neolane
  ```

변경 사항을 고려하려면 Adobe Campaign 서비스를 다시 시작해야 합니다.

명령은 다음과 같습니다.

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

20.1부터는 다음 명령을 대신 사용하는 것이 좋습니다.

```
systemctl stop nlserver
systemctl start nlserver
```

### Linux의 oracle 클라이언트 {#oracle-client-in-linux}

Adobe Campaign에서 Oracle을 사용할 때 Linux에서 Oracle 클라이언트 레이어를 구성해야 합니다.

* 전체 클라이언트 사용
* TNS 정의

  설치 단계에서 TNS 정의를 추가해야 합니다. 이렇게 하려면 다음 명령을 사용합니다.

  ```
  cd /etc
  mkdir oracle
  cd oracle
  vi tnsnames.ora
  ```

* 환경 변수

  을(를) 참조하십시오 [환경 변수](../../installation/using/installing-packages-with-linux.md#environment-variables).

* Adobe Campaign 구성

  Adobe Campaign용 Oracle 클라이언트 설치를 완료하려면 **.so** Adobe Campaign에서 사용하는 파일입니다.

  이렇게 하려면 다음 명령을 사용합니다.

  ```
  cd /usr/lib/oracle/10.2.0.4/client/lib
  ln -s libclntsh.so.10.1 libclntsh.so
  ```

문제가 발생하면 패키지에 나열된 패키지가 [Oracle 설치 설명서](https://docs.oracle.com/) 이(가) 올바르게 설치되어 있습니다.

## 설치 확인 {#installation-checks}

이제 다음 명령을 사용하여 초기 설치 테스트를 수행할 수 있습니다.

```
su - neolane
nlserver pdump
```

Adobe Campaign이 시작되지 않은 경우 응답은 다음과 같습니다.

```
no task
```

## 서버의 첫 번째 시작 {#first-start-up-of-the-server}

설치 테스트가 완료되면 다음 명령을 입력합니다.

```
nlserver web
```

그러면 다음 정보가 표시됩니다.

```
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

이 명령을 사용하면 다음을 만들 수 있습니다 **config-default.xml** 및 **serverConf.xml** 구성 파일입니다. 에서 사용할 수 있는 모든 매개 변수 **serverConf.xml** 다음에 나열됨 [섹션](../../installation/using/the-server-configuration-file.md).

누르기 **Ctrl+C** 프로세스를 중지하려면 다음 명령을 입력합니다.

```
nlserver start web
```

그러면 다음 정보가 표시됩니다.

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

중지하려면 다음을 입력합니다.

```
nlserver stop web
```

그러면 다음 정보가 표시됩니다.

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## 내부 식별자 암호 {#password-for-the-internal-identifier}

Adobe Campaign 서버는 이라는 기술 로그인을 정의합니다 **내부** 모든 인스턴스에 대한 모든 권한이 있습니다. 설치 후 로그인에 암호가 없습니다. 하나를 정의해야 합니다.

[이 섹션](../../installation/using/configuring-campaign-server.md#internal-identifier)에서 자세히 알아보십시오.
