---
title: 엔터프라이즈 배포
seo-title: 엔터프라이즈 배포
description: 엔터프라이즈 배포
seo-description: null
page-status-flag: never-activated
uuid: 2c2b5cef-86cb-4cb5-801a-ca6afeae90bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 066d0ac1-033c-467b-aa6c-43a97ecd8632
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1265'
ht-degree: 0%

---


# 엔터프라이즈 배포{#enterprise-deployment}

이것이 가장 완벽한 구성이다. 보안 및 가용성 향상을 위한 표준 구성을 기반으로 구축됩니다.

* HTTP 또는 TCP 로드 밸런서를 사용하는 전용 리디렉션 서버(확장성 및 가용성)
* 두 개의 애플리케이션 서버를 통해 처리량과 장애 복구 기능(내결함성)을 개선하여 LAN에서 분리됩니다.

서버와 프로세스 간의 일반적인 통신은 다음 스키마에 따라 수행됩니다.

![](assets/s_901_ncs_install_enterpriseconfig.png)

이러한 유형의 구성을 통해 예상되는 처리량은 적절한 대역폭과 튜닝 방식으로 시간당 100,000개의 메일을 초과할 수 있습니다.

## 기능 {#features}

### 장점 {#advantages}

* 최적화된 보안:외부에 노출되어야 하는 서버만 DMZ의 컴퓨터에 설치됩니다.
* 고가용성 보장:외부에서 볼 수 있는 컴퓨터만 고가용성을 염두에 두고 관리해야 합니다.

### 단점 {#disadvantages}

높은 하드웨어 및 관리 비용

### 권장 장비 {#recommended-equipment}

* 애플리케이션 서버:2 Ghz 쿼드 코어 CPU, 4GB RAM, 소프트웨어 RAID 1 80GB SATA 하드 드라이브
* 리디렉션 서버:2 Ghz 쿼드 코어 CPU, 4GB RAM, 소프트웨어 RAID 1 80GB SATA 하드 드라이브

>[!NOTE]
>
>리디렉션 서버에 트래픽을 위해 기존 부하 균형 조정기를 재사용할 수 있습니다.

## 설치 및 구성 단계 {#installation-and-configuration-steps}

### 사전 요구 사항 {#prerequisites}

* 두 애플리케이션 서버의 JDK
* 웹 서버(IIS, Apache)를 두 최전선에서
* 두 응용 프로그램 서버의 데이터베이스 서버에 액세스,
* POP3,
* 부하 균형 조정기에 두 개의 DNS 별칭 생성:

   * 가상 IP 주소(VIP)에서 로드 밸런서를 추적 및 가리키기 위해 처음으로 대중에게 노출되었으며, 이렇게 해서 두 개의 정면 서버로 배포됩니다.
   * 콘솔을 통해 액세스하고 가상 IP 주소(VIP)에서 로드 밸런서를 가리키는 내부 사용자에게 두 번째 노출이 있으며 두 개의 애플리케이션 서버에 배포됩니다.

* STMP(25), DNS(53), HTTP(80), HTTPS(443), SQL(Oracle의 경우 1521, PostgreSQL의 경우 5432) 등을 열도록 구성된 방화벽 포트. 자세한 내용은 데이터베이스 액세스 [섹션을 참조하십시오](../../installation/using/network-configuration.md#database-access).

>[!CAUTION]
>
>응용 프로그램 서버가 단일 데이터베이스 인스턴스를 가리키면 한 인스턴스에서 표준 패키지를 가져온 후 패키지에 포함된 스키마가 다른 인스턴스에서 로드되지 않습니다.
>  
>응용 프로그램 서버가 단일 데이터베이스 인스턴스를 가리키면 한 인스턴스에서 스키마를 변경한 후 다른 인스턴스에서 스키마가 로드되지 않습니다.
>
>이러한 문제를 복구하려면 오류가 발생한 두 번째 인스턴스에서 &#39;web@default&#39; 프로세스를 재부팅해야 합니다.

### 응용 프로그램 서버 설치 및 구성 1 {#installing-and-configuring-the-application-server-1}

다음 예에서 인스턴스의 매개 변수는 다음과 같습니다.

* 인스턴스의 이름:데모
* DNS 마스크:tracking.campaign.net*, console.campaign.net*(애플리케이션 서버는 클라이언트 콘솔 연결 및 보고서, 미러 페이지 및 구독 취소 페이지의 URL을 처리합니다.)
* 언어:영어
* 데이터베이스:캠페인:demo@dbsrv

첫 번째 서버를 설치하는 단계는 다음과 같습니다.

1. Adobe Campaign 서버의 설치 절차를 따르십시오. **nlserver** package on Linux 또는 **setup.exe** (Windows)

   자세한 내용은 Linux [(Linux)에서](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) 캠페인 설치 사전 요구 사항 및 Windows [(Windows)에서 캠페인](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) 설치 사전 요구 사항을 참조하십시오.

1. Adobe Campaign 서버가 설치되면 nlserver web -tomcat **** 명령 명령을 사용하여 응용 프로그램 서버(웹)를 시작하고 Tomcat이 포트 8080의 독립 실행형 웹 서버 모드에서 Tomcat을 시작하고 올바르게 시작하는지 확인합니다.

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >웹 모듈을 처음 실행하면 설치 폴더 아래의 **conf** 디렉토리에 config-default.xml **및** serverConf.xml **파일이** 생성됩니다. serverConf.xml에서 사용할 수 있는 모든 매개 변수가 이 **섹션에 나열되어 있습니다** [](../../installation/using/the-server-configuration-file.md).

   서버를 **중지하려면 Ctrl+C** 키를 누릅니다.

   자세한 내용은 다음 섹션을 참조하십시오.

   * Linux용: [서버의 첫 번째 시작](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Windows의 경우: [서버의 첫 번째 시작](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. 다음 명령을 사용하여 **내부** 암호를 변경합니다.

   ```
   nlserver config -internalpassword
   ```

   For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

1. 추적(이 경우 **tracking.campaign.net** )을 위한 DNS 마스크와 클라이언트 콘솔(이 경우 **console.campaign.net**)을 사용하여 데모 **인스턴스를 만듭니다**. 다음 두 가지 방법으로 작업을 수행할 수 있습니다.

   * 콘솔을 통해 인스턴스를 만듭니다.

      ![](assets/install_create_new_connexion.png)

      자세한 내용은 인스턴스 [만들기 및 로그인을 참조하십시오](../../installation/using/creating-an-instance-and-logging-on.md).

      또는

   * 명령줄을 사용하여 인스턴스를 만듭니다.

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      자세한 내용은 인스턴스 [만들기를 참조하십시오](../../installation/using/command-lines.md#creating-an-instance).

1. config-demo.xml **파일(이전 명령을 통해** 생성되어 config-default.xml **파일 옆에 있음)을** 편집하고, mta **(배달, wffdefault.** 서버 **), 워크플로(워크플로), 리바운드 메일** (리바운딩) 및 리바운딩MailBlaundAppMails가 활성화된 다음 응용 프로그램의 주소를 구성합니다 **** **** **** .

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. serverConf.xml **** 파일을 편집하고 배달 도메인을 지정한 다음 MTA 모듈에서 MX 유형 DNS 쿼리에 응답하기 위해 사용하는 DNS 서버의 IP(또는 호스트) 주소를 지정합니다.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >nameServers **매개** 변수는 Windows에서만 사용됩니다.

   자세한 내용은 [캠페인 서버 구성을 참조하십시오](../../installation/using/campaign-server-configuration.md).

1. v7 또는 v7용 클라이언트 설정 프로그램(**setup-client-7.XX**, **YYYY.****** v7 또는 **setup-client-6.XX의 경우,** **** EXE for yyyyy v6.1)를 /dataknl/jspnl 폴더에 복사합니다.

   자세한 내용은 다음 섹션을 참조하십시오.

   * Linux용: [Linux용 클라이언트 콘솔 가용성](../../installation/using/client-console-availability-for-linux.md)
   * Windows의 경우: [Windows용 클라이언트 콘솔 가용성](../../installation/using/client-console-availability-for-windows.md).

1. Adobe Campaign 서버를 시작(Windows의&#x200B;**net start nlserver6** , Linux의 **/etc/init.d/nlserver6 시작****)하고 명령 nlserver dump를** 한 번 더 실행하여 활성화된 모든 모듈의 존재 여부를 확인합니다.

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

   또한 컴퓨터에 설치된 Adobe Campaign 서버의 버전과 빌드 번호를 알 수 있습니다.

1. URL을 **사용하여 서버 웹** 모듈을 테스트합니다. [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   이 URL을 사용하면 클라이언트 설정 프로그램의 다운로드 페이지에 액세스할 수 있습니다.

   액세스 제어 페이지에 도달하면 **내부** 로그인 및 관련 암호를 입력합니다.

   ![](assets/s_ncs_install_access_client.png)

   자세한 내용은 다음 섹션을 참조하십시오.

   * Linux용: [Linux용 클라이언트 콘솔 가용성](../../installation/using/client-console-availability-for-linux.md)
   * Windows의 경우: [Windows용 클라이언트 콘솔 가용성](../../installation/using/client-console-availability-for-windows.md)

### 응용 프로그램 서버 2 설치 및 구성 {#installing-and-configuring-the-application-server-2}

다음 단계를 적용합니다.

1. Adobe Campaign 서버를 설치합니다.
1. 생성된 인스턴스의 파일을 응용 프로그램 서버 1에 복사합니다.

   응용 프로그램 서버 1과 동일한 인스턴스 이름을 유지합니다.

1. 내부 **를** 응용 프로그램 서버 1과 동일하게 변경합니다.
1. 데이터베이스를 인스턴스에 연결:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. config-demo.xml **파일(이전 명령을 통해** 생성되어 config-default.xml **파일 옆에 있음)을** 편집하고, mta **(배달, wffdefault.** 서버 **), 워크플로(워크플로), 리바운드 메일** (리바운딩) 및 리바운딩MailBlaundAppMails가 활성화된 다음 응용 프로그램의 주소를 구성합니다 **** **** **** .

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. serverConf.xml **** 파일을 편집하고 MTA 모듈의 DNS 구성을 채웁니다.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >nameServers **매개** 변수는 Windows에서만 사용됩니다.

   자세한 내용은 [캠페인 서버 구성을 참조하십시오](../../installation/using/campaign-server-configuration.md).

1. Adobe Campaign 서버를 시작합니다.

   자세한 내용은 다음 섹션을 참조하십시오.

   * Linux용: [서버의 첫 번째 시작](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Windows의 경우: [서버의 첫 번째 시작](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### 중앙 서버 설치 및 구성 {#installing-and-configuring-the-frontal-servers}

설치 및 구성 절차는 두 컴퓨터 모두에서 동일합니다.

단계는 다음과 같습니다.

1. Adobe Campaign 서버 설치,
1. 다음 섹션에 설명된 웹 서버 통합 절차(IIS, Apache)를 준수합니다.

   * For Linux: [Integration into a Web server for Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * For Windows: [Integration into a Web server for Windows](../../installation/using/integration-into-a-web-server-for-windows.md).

1. 설치 중에 **생성된 config-demo.xml** 및 **serverConf.xml** 파일을 복사합니다. config-demo.xml **파일에서** trackinglogd **프로세스를 활성화하고 mta** mta **, mail** infserver, **wfserver및 wfstatStat**&#x200B;프로세스를 비활성화하십시오 **** **** .
1. serverConf.xml **** 파일을 편집하고 리디렉션의 매개 변수에 중복 추적 서버를 채웁니다.

   ```
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. 웹 사이트를 시작하고 URL에서 리디렉션을 테스트합니다. [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   브라우저에 다음과 같은 메시지가 표시되어야 합니다(로드 밸런서가 리디렉션하는 URL에 따라).

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   또는

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   자세한 내용은 다음 섹션을 참조하십시오.

   * Linux용: [웹 서버 실행 및 구성 테스트](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * Windows의 경우: [웹 서버를 실행하고 구성을 테스트합니다](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. Adobe Campaign 서버를 시작합니다.

