---
product: campaign
title: 엔터프라이즈 배포
description: 엔터프라이즈 배포
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 38c14010-203a-47ab-b23d-6f431dab9a88
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 3%

---

# 엔터프라이즈 배포{#enterprise-deployment}



가장 완벽한 구성입니다. 보안 및 가용성 향상을 위한 표준 구성을 기반으로 합니다.

* 확장 및 가용성을 위해 HTTP 또는 TCP 로드 밸런서 뒤에 전용 리디렉션 서버
* 향상된 처리량과 페일오버 기능(내결함성)을 제공하는 두 대의 애플리케이션 서버가 LAN에서 격리됩니다.

서버와 프로세스 간의 일반적인 통신은 다음 스키마에 따라 수행됩니다.

![](assets/s_901_ncs_install_enterpriseconfig.png)

이러한 구성 방식을 사용하면 적절한 대역폭과 튜닝으로 시간당 100,000개의 메일을 처리할 수 있습니다.

## 기능 {#features}

### 장점 {#advantages}

* 최적화된 보안: 외부로 노출해야 하는 서버만 DMZ의 컴퓨터에 설치됩니다.
* 고가용성 보장 용이성: 외부에서 볼 수 있는 컴퓨터만 고가용성을 염두에 두고 관리해야 합니다.

### 단점 {#disadvantages}

높은 하드웨어 및 관리 비용.

### 추천 장비 {#recommended-equipment}

* 어플리케이션 서버: 2Ghz 쿼드 코어 CPU, 4GB RAM, 소프트웨어 RAID 1 80GB SATA 하드 드라이브.
* 리디렉션 서버: 2Ghz 쿼드 코어 CPU, 4GB RAM, 소프트웨어 RAID 1 80GB SATA 하드 드라이브.

>[!NOTE]
>
>리디렉션 서버로의 트래픽에 대해 기존 로드 밸런서를 재사용할 수 있습니다.

## 설치 및 구성 단계 {#installation-and-configuration-steps}

### 필수 구성 요소 {#prerequisites}

* 두 애플리케이션 서버의 JDK,
* 양쪽 프론트엔드의 웹 서버(IIS, Apache)
* 두 애플리케이션 서버의 데이터베이스 서버에 액세스
* POP3를 통해 액세스할 수 있는 바운스 사서함,
* 로드 밸런서에서 두 개의 DNS 별칭 생성:

   * 처음으로 공개되어 가상 IP 주소(VIP)의 로드 밸런서를 추적하고 지정한 다음 두 대의 전면 서버에 배포되는 경우
   * 두 번째는 콘솔을 통해 액세스할 수 있도록 내부 사용자에게 표시되며, 가상 IP 주소(VIP)의 로드 밸런서를 가리킨 다음 두 애플리케이션 서버에 배포됩니다.

* STMP(25), DNS(53), HTTP(80), HTTPS(443), SQL(Oracle 1521, PostgreSQL 5432 등)을 열도록 구성된 방화벽 포트입니다. 자세한 내용은 [데이터베이스 액세스](../../installation/using/network-configuration.md#database-access) 섹션을 참조하십시오.

>[!CAUTION]
>
>응용 프로그램 서버가 단일 데이터베이스 인스턴스를 가리키면 한 인스턴스에서 표준 패키지를 가져온 후 패키지에 포함된 스키마가 다른 인스턴스에서 로드되지 않습니다.
>  
>애플리케이션 서버가 단일 데이터베이스 인스턴스를 가리키면 한 인스턴스에서 스키마를 변경한 후 스키마가 다른 인스턴스에서 로드되지 않습니다.
>
>이러한 문제를 복구하려면 오류가 발생한 두 번째 인스턴스에서 &#39;web@default&#39; 프로세스를 다시 부팅해야 합니다.

### 애플리케이션 서버 설치 및 구성 1 {#installing-and-configuring-the-application-server-1}

다음 예에서 인스턴스의 매개 변수는 다음과 같습니다.

* 인스턴스 이름: 데모
* DNS 마스크: tracking.campaign.net&#42;, console.campaign.net&#42;(애플리케이션 서버가 클라이언트 콘솔 연결 및 보고서와 미러 페이지 및 구독 취소 페이지의 URL을 처리)
* 언어: 영어
* 데이터베이스: campaign:demo@dbsrv

첫 번째 서버를 설치하는 단계는 다음과 같습니다.

1. Adobe Campaign 서버의 설치 절차를 따르십시오. **nlserver** 패키지(Linux) 또는 **setup.exe**(Windows).

   자세한 내용은 [Linux에서 캠페인 설치 사전 요구 사항](../../installation/using/prerequisites-of-campaign-installation-in-linux.md)(Linux) 및 [Windows에서 캠페인 설치 사전 요구 사항](../../installation/using/prerequisites-of-campaign-installation-in-windows.md)(Windows)을 참조하십시오.

1. Adobe Campaign 서버가 설치되면 **nlserver web -tomcat** 명령을 사용하여 응용 프로그램 서버(웹)를 시작합니다(웹 모듈을 사용하면 포트 8080에서 수신하는 독립 실행형 웹 서버 모드에서 Tomcat을 시작할 수 있음). Tomcat이 올바르게 시작되는지 확인합니다.

   ```sql
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >웹 모듈을 처음 실행하면 설치 폴더 아래의 **conf** 디렉터리에 **config-default.xml** 및 **serverConf.xml** 파일이 만들어집니다. **serverConf.xml**&#x200B;에서 사용할 수 있는 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열되어 있습니다.

   서버를 중지하려면 **Ctrl+C**&#x200B;를 누르십시오.

   자세한 내용은 다음 섹션을 참조하십시오.

   * Linux의 경우: [서버 처음 시작](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Windows의 경우: [서버의 첫 시작](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. 다음 명령을 사용하여 **internal** 암호를 변경합니다.

   ```
   nlserver config -internalpassword
   ```

   이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#internal-identifier)을 참조하십시오.

1. 추적을 위한 DNS 마스크(이 경우 **tracking.campaign.net**)와 클라이언트 콘솔(이 경우 **console.campaign.net**)에 대한 액세스를 사용하여 **demo** 인스턴스를 만듭니다. 두 가지 방법으로 이 작업을 수행할 수 있습니다.

   * 콘솔을 통해 인스턴스를 만듭니다.

     ![](assets/install_create_new_connexion.png)

     자세한 내용은 [인스턴스 만들기 및 로그온](../../installation/using/creating-an-instance-and-logging-on.md)을 참조하세요.

     또는

   * 명령줄을 사용하여 인스턴스를 생성합니다.

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
     ```

     자세한 내용은 [인스턴스 만들기](../../installation/using/command-lines.md#creating-an-instance)를 참조하세요.

1. **config-demo.xml** 파일(이전 명령을 통해 만들어지고 **config-default.xml** 파일 옆에 있음)을 편집하고 **mta**(배달), **wfserver**(워크플로), **inMail**(리바운드 메일) 및 **stat**(통계) 프로세스가 사용하도록 설정되어 있는지 확인한 다음 **app** 통계 서버의 주소를 구성하십시오.

   ```xml
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

   이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#enabling-processes)을 참조하십시오.

1. **serverConf.xml** 파일을 편집하고 배달 도메인을 지정한 다음 MX 유형 DNS 쿼리에 응답하기 위해 MTA 모듈에서 사용하는 DNS 서버의 IP(또는 호스트) 주소를 지정합니다.

   ```xml
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >**nameServers** 매개 변수는 Windows에서만 사용됩니다.

   자세한 내용은 [Campaign 서버 구성](../../installation/using/configuring-campaign-server.md)을 참조하세요.

1. 클라이언트 콘솔 설치 프로그램 **setup-client-7.XX**, **YYYY.exe**&#x200B;을(를) **/datakit/nl/eng/jsp** 폴더에 복사합니다. [자세히 알아보기](../../installation/using/client-console-availability-for-windows.md).

1. Adobe Campaign 서버(**net start nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux)를 시작하고 **nlserver pdump** 명령을 한 번 더 실행하여 활성화된 모든 모듈이 있는지 확인합니다.

   >[!NOTE]
   >
   >20.1부터는 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우). **systemctl start nlserver**


   ```sql
   12:09:54 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   syslogd@default (7611) - 9.2 MB
   stat@demo (5988) - 1.5 MB
   inMail@demo (7830) - 11.9 MB
   watchdog (27369) - 3.1 MB
   mta@demo (7831) - 15.6 MB
   wfserver@demo (7832) - 11.5 MB
   web@default (28671) - 40.5 MB
   ```

   이 명령을 사용하면 컴퓨터에 설치된 Adobe Campaign 서버의 버전 및 빌드 번호도 알 수 있습니다.

1. URL [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test)을(를) 사용하여 **nlserver web** 모듈을 테스트합니다.

   이 URL을 사용하면 클라이언트 설치 프로그램의 다운로드 페이지에 액세스할 수 있습니다. [자세히 알아보기](../../installation/using/client-console-availability-for-windows.md).

   액세스 제어 페이지에 도달하면 **내부** 로그인 및 관련 암호를 입력하십시오.

   ![](assets/s_ncs_install_access_client.png)

### Application Server 2 설치 및 구성 {#installing-and-configuring-the-application-server-2}

다음 단계를 적용합니다.

1. Adobe Campaign 서버를 설치합니다.
1. 생성한 인스턴스의 파일을 애플리케이션 서버 1에 복사합니다.

   애플리케이션 서버 1과 동일한 인스턴스 이름을 유지합니다.

1. **internal**&#x200B;을(를) 응용 프로그램 서버 1과 동일한 것으로 변경합니다.
1. 인스턴스에 데이터베이스 연결:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. **config-demo.xml** 파일(이전 명령을 통해 만들어지고 **config-default.xml** 파일 옆에 있음)을 편집하고 **mta**(배달), **wfserver**(워크플로), **inMail**(리바운드 메일) 및 **stat**(통계) 프로세스가 사용하도록 설정되어 있는지 확인한 다음 **app** 통계 서버의 주소를 구성하십시오.

   ```xml
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

   이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#enabling-processes)을 참조하십시오.

1. **serverConf.xml** 파일을 편집하고 MTA 모듈의 DNS 구성을 채웁니다.

   ```xml
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >**nameServers** 매개 변수는 Windows에서만 사용됩니다.

   자세한 내용은 [Campaign 서버 구성](../../installation/using/configuring-campaign-server.md)을 참조하세요.

1. Adobe Campaign 서버를 시작합니다.

   자세한 내용은 다음 섹션을 참조하십시오.

   * Linux의 경우: [서버 처음 시작](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Windows의 경우: [서버의 첫 시작](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### 전면 서버 설치 및 구성 {#installing-and-configuring-the-frontal-servers}

설치 및 구성 절차는 두 컴퓨터에서 동일합니다.

단계는 다음과 같습니다.

1. Adobe Campaign 서버 설치,
1. 다음 섹션에 설명된 웹 서버 통합 절차(IIS, Apache)를 준수합니다.

   * Linux의 경우: [Linux용 웹 서버에 통합](../../installation/using/integration-into-a-web-server-for-linux.md),
   * Windows의 경우: [Windows용 웹 서버에 통합](../../installation/using/integration-into-a-web-server-for-windows.md).

1. 설치 중에 만든 **config-demo.xml** 및 **serverConf.xml** 파일을 복사합니다. **config-demo.xml** 파일에서 **trackinglogd** 프로세스를 활성화하고 **mta**, **inmail**, **wfserver** 및 **stat** 프로세스를 비활성화합니다.
1. **serverConf.xml** 파일을 편집하고 리디렉션의 매개 변수에서 중복 추적 서버를 채웁니다.

   ```xml
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. 웹 사이트를 시작하고 URL [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)에서 리디렉션을 테스트합니다.

   브라우저는 로드 밸런서에서 리디렉션된 URL에 따라 다음 메시지를 표시해야 합니다.

   ```xml
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   또는

   ```xml
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   자세한 내용은 다음 섹션을 참조하십시오.

   * Linux의 경우: [웹 서버 시작 및 구성 테스트](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * Windows의 경우: [웹 서버를 시작하고 구성을 테스트합니다](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. Adobe Campaign 서버를 시작합니다.
