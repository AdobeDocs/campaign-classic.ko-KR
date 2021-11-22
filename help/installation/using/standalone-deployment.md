---
product: campaign
title: 독립형 배포
description: 독립형 배포
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1086'
ht-degree: 2%

---

# 독립형 배포{#standalone-deployment}

![](../../assets/v7-only.svg)

이 구성에는 동일한 컴퓨터에 있는 모든 구성 요소가 포함됩니다.

* 응용 프로그램 프로세스(웹),
* 전달 프로세스(mta),
* 리디렉션 프로세스(추적),
* 워크플로우 프로세스 및 예약된 작업(wfserver),
* 반송 메일 프로세스(inMail),
* 통계 프로세스(stat).

프로세스 간의 전체 통신은 다음 스키마에 따라 수행됩니다.

![](assets/s_900_ncs_install_standaloneconfig.png)

이 유형의 구성은 10만 명 미만의 수신자의 목록을 관리하고, 예를 들어 다음 소프트웨어 계층을 사용하여 실행할 수 있습니다.

* Linux,
* Apache,
* PostgreSQL,
* Qmail.

볼륨이 증가하면 이 아키텍처의 변형으로 데이터베이스 서버를 다른 컴퓨터로 이동하여 성능이 향상됩니다.

>[!NOTE]
>
>기존 데이터베이스 서버가 충분한 리소스가 있는 경우에도 사용할 수 있습니다.

## 기능 {#features}

### 장점 {#advantages}

* 전체 독립형 및 낮은 구성 비용(아래에 나열된 오픈 소스 소프트웨어를 사용하는 경우 청구 가능한 라이센스가 필요 없음)
* 간편한 설치 및 네트워크 구성

### 단점 {#disadvantages}

* 사고 시 중요한 컴퓨터.
* 메시지를 브로드캐스트할 때 제한된 대역폭(당사 경험에서 시간당 약 수만 개의 메일)입니다.
* 방송 시 응용 프로그램의 잠재적 둔화.
* 응용 프로그램 서버는 리디렉션 서버를 호스트하므로 외부에서(예를 들어 DMZ에 있는 동안) 사용할 수 있어야 합니다.

## 설치 및 구성 단계 {#installation-and-configuration-steps}

### 필수 구성 요소 {#prerequisites}

* JDK,
* 웹 서버(IIS, Apache),
* 데이터베이스 서버에 대한 액세스,
* POP3를 통해 액세스할 수 있는 바운스 사서함,
* 두 개의 DNS 별칭 생성:

   * 공용 IP에서 컴퓨터를 추적하고 가리키기 위해 처음으로 대중에게 노출됨
   * 콘솔 액세스를 위해 내부 사용자에게 노출되고 동일한 컴퓨터를 가리키는 두 번째 별칭입니다.

* SMTP(25), DNS(53), HTTP(80), HTTPS(443), SQL(Oracle의 경우 1521, PostgreSQL의 경우 5432)를 열도록 구성된 방화벽 포트. 자세한 내용은 [네트워크 구성](../../installation/using/network-configuration.md).

다음 예에서 인스턴스의 매개 변수는 다음과 같습니다.

* 인스턴스 이름: **데모**
* DNS 마스크: **console.campaign.net*** (클라이언트 콘솔 연결 및 보고서에만 해당)
* 데이터베이스: **campaign:demo@dbsrv**

### 설치 및 구성(단일 시스템) {#installing-and-configuring--single-machine-}

다음 단계를 적용합니다.

1. Adobe Campaign 서버의 설치 절차를 따르십시오. **nlserver** Linux 또는 **setup.exe** Windows

   자세한 내용은 [Linux에서 캠페인 설치 사전 요구 사항](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) 및 [Windows에서 Campaign 설치 사전 요구 사항](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Adobe Campaign 서버가 설치되면 명령을 사용하여 애플리케이션 서버(웹)를 시작합니다 **nlserver web -tomcat** (웹 모듈을 사용하면 포트 8080에서 수신 대기하는 독립 실행형 웹 서버 모드로 Tomcat을 시작하고 Tomcat이 올바르게 시작하는지 확인할 수 있습니다.)

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >웹 모듈이 처음 실행되면 **config-default.xml** 및 **serverConf.xml** 의 파일 **conf** 디렉토리 아래에 있습니다. 에서 사용할 수 있는 모든 매개 변수 **serverConf.xml** 여기에 나열되어 있습니다. [섹션](../../installation/using/the-server-configuration-file.md).

   누르기 **Ctrl+C** 서버를 중지하려면 다음을 수행하십시오.

   자세한 정보는 다음 섹션을 참조하십시오.

   * Linux의 경우: [서버의 첫 번째 시작](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Windows의 경우: [서버의 첫 번째 시작](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

1. 변경 **내부** 명령을 사용하여 암호:

   ```
   nlserver config -internalpassword
   ```

   이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#internal-identifier)을 참조하십시오.

1. 만들기 **데모** 추적할 DNS 마스크가 있는 인스턴스(이 경우 **tracking.campaign.net**) 및 클라이언트 콘솔에 액세스합니다(이 경우 **console.campaign.net**). 다음 두 가지 방법으로 데이터를 수집할 수 있습니다.

   * 콘솔을 통해 인스턴스를 생성합니다.

      ![](assets/install_create_new_connexion.png)

      자세한 내용은 [인스턴스 만들기 및 로그온](../../installation/using/creating-an-instance-and-logging-on.md).

      또는

   * 명령줄을 사용하여 인스턴스를 생성합니다.

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      자세한 내용은 [인스턴스 만들기](../../installation/using/command-lines.md#creating-an-instance).

1. 편집 **config-demo.xml** 파일(다음 이전 단계에서 생성됨) **config-default.xml**) 및에 대해 **mta** (게재), **wfserver** (워크플로우), **inMail** (바운스 메일) 및 **stat** (통계) 프로세스가 활성화됩니다. 그런 다음 통계 서버의 주소를 구성합니다.

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="localhost"/>
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#enabling-processes)을 참조하십시오.

1. 편집 **serverConf.xml** MX 유형 DNS 쿼리에 응답하기 위해 MTA 모듈에서 사용하는 DNS 서버의 IP(또는 호스트) 주소를 지정하고 전달 도메인을 지정합니다.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >다음 **nameServers** 매개 변수는 Windows에서만 사용됩니다.

   자세한 내용은 [Campaign 서버 구성](../../installation/using/configuring-campaign-server.md).

1. 클라이언트 콘솔 설정 프로그램 복사(**setup-client-7.XX**, **YYYY.exe** v7 또는 **setup-client-6.XX**, **YYYY.exe** v6.1의 경우) **/datakit/nl/eng/jsp** 폴더를 입력합니다. [자세히 알아보기](../../installation/using/client-console-availability-for-windows.md)

1. 다음 섹션에 설명된 웹 서버 통합 절차(IIS, Apache)를 따르십시오.

   * Linux의 경우: [Linux용 웹 서버와 통합](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Windows의 경우: [Windows용 웹 서버에 통합](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 웹 사이트를 시작하고 URL을 사용하여 리디렉션을 테스트합니다. https://tracking.campaign.net/r/test

   브라우저에 다음 메시지가 표시되어야 합니다.

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   자세한 정보는 다음 섹션을 참조하십시오.

   * Linux의 경우: [웹 서버 시작 및 구성 테스트](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Windows의 경우: [웹 서버 시작 및 구성 테스트](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Adobe Campaign 서버 시작(**net start nlserver6** Windows에서는 **/etc/init.d/nlserver6 시작** Linux에서)에서 명령을 실행합니다. **nlserver pdump** 사용 가능한 모든 모듈이 있는지 한 번 더 확인하십시오.

   >[!NOTE]
   >
   >20.1부터 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우). **systectl start nlserver**

   ```
   12:09:54 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   syslogd@default (7611) - 9.2 MB
   stat@demo (5988) - 1.5 MB
   inMail@demo (7830) - 11.9 MB
   watchdog (27369) - 3.1 MB
   mta@demo (7831) - 15.6 MB
   wfserver@demo (7832) - 11.5 MB
   web@default (28671) - 40.5 MB
   ```

   또한 이 명령을 사용하여 컴퓨터에 설치된 Adobe Campaign 서버의 버전 및 빌드 번호를 알 수 있습니다.

1. 테스트 **nlserver 웹** URL을 사용하는 모듈: https://console.campaign.net/nl/jsp/logon.jsp

   이 URL을 사용하면 클라이언트 설정 프로그램의 다운로드 페이지에 액세스할 수 있습니다.

   을(를) 입력합니다. **내부** 액세스 제어 페이지에 도달하면 로그인 및 관련 암호입니다. [자세히 알아보기](../../installation/using/client-console-availability-for-windows.md)

   ![](assets/s_ncs_install_access_client.png)

1. Adobe Campaign 클라이언트 콘솔을 시작합니다(이전 다운로드 페이지에서 또는 Windows 설치를 위해 서버에서 직접 시작). 서버 연결 URL을 https://console.campaign.net으로 설정하고 를 사용하여 연결합니다. **내부** 로그인.

   을(를) 참조하십시오. [이 페이지](../../installation/using/creating-an-instance-and-logging-on.md) 및 [이 섹션](../../installation/using/configuring-campaign-server.md#internal-identifier).

   처음으로 로그인하면 데이터베이스 생성 마법사가 나타납니다.

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   마법사의 단계에 따라 연결 인스턴스와 연결된 데이터베이스를 만듭니다.

   자세한 내용은 [데이터베이스 만들기 및 구성](../../installation/using/creating-and-configuring-the-database.md).

   데이터베이스가 만들어지면 로그오프합니다.

1. 를 사용하여 클라이언트 콘솔에 다시 로그온합니다. **관리** 암호 없이 로그인하고 배포 마법사를 시작합니다( **[!UICONTROL Tools > Advanced]** 메뉴)을 클릭하여 인스턴스 구성을 완료합니다.

   자세한 내용은 [인스턴스 배포](../../installation/using/deploying-an-instance.md).

   설정할 기본 매개 변수는 다음과 같습니다.

   * 이메일 게재: 반송 메일의 보낸 사람 및 회신 주소 및 오류 사서함입니다.
   * 추적: 리디렉션에 사용되는 외부 URL과 내부 URL을 채우고 **추적 서버에 등록** 그런 다음 유효성 검사를 수행합니다 **데모** 추적 서버의 인스턴스입니다.

      자세한 내용은 [구성 추적](../../installation/using/deploying-an-instance.md#tracking-configuration).

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      Adobe Campaign 서버가 응용 프로그램 서버와 리디렉션 서버로 모두 사용되므로 추적 로그를 수집하고 URL을 전송하는 데 사용되는 내부 URL은 Tomcat(https://localhost:8080)에 대한 직접 내부 연결입니다.

   * 바운스 관리: 반송 메일을 처리할 매개 변수를 입력합니다. **처리되지 않은 바운스 메일** 섹션을 고려합니다.)
   * 액세스 위치: 보고서, 웹 양식 및 미러 페이지에 대한 두 URL을 제공합니다.

      ![](assets/d_ncs_install_web_url.png)
