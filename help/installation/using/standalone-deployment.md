---
product: campaign
title: 독립형 배포
description: 독립형 배포
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 2%

---

# 독립형 배포{#standalone-deployment}



이 구성에는 동일한 컴퓨터의 모든 구성 요소가 포함됩니다.

* 애플리케이션 프로세스(웹),
* 게재 프로세스(mta),
* 리디렉션 프로세스(추적),
* 워크플로우 프로세스 및 예약된 작업(wfserver),
* 반송 메일 프로세스(inMail),
* 통계 프로세스(stat).

프로세스 간의 전체 통신은 다음 스키마에 따라 수행됩니다.

![](assets/s_900_ncs_install_standaloneconfig.png)

이러한 유형의 구성은 예를 들어 다음 소프트웨어 계층을 사용하여 100,000명 미만의 수신자 목록을 관리할 때 실행할 수 있습니다.

* Linux,
* 아파치
* PostgreSQL,
* Qmail.

볼륨이 커지면 이 아키텍처의 변형으로 데이터베이스 서버가 다른 컴퓨터로 이동하여 성능이 향상됩니다.

>[!NOTE]
>
>리소스가 충분한 경우 기존 데이터베이스 서버를 사용할 수도 있습니다.

## 기능 {#features}

### 장점 {#advantages}

* 완전히 독립형 상태로 저렴한 구성 비용(아래 나열된 오픈 소스 소프트웨어를 사용하는 경우 청구 가능한 라이센스가 필요하지 않음).
* 간편한 설치 및 네트워크 구성

### 단점 {#disadvantages}

* 사고 발생 시 중요한 컴퓨터.
* 메시지를 브로드캐스트할 때 대역폭이 제한됨(경험상 시간당 수만 개의 메일 수).
* 브로드캐스팅 시 애플리케이션의 잠재적인 느려짐.
* 응용 프로그램 서버는 리디렉션 서버를 호스팅하므로 외부에서 사용할 수 있어야 합니다(예: DMZ에 있는 경우).

## 설치 및 구성 단계 {#installation-and-configuration-steps}

### 필수 구성 요소 {#prerequisites}

* JDK,
* 웹 서버(IIS, Apache),
* 데이터베이스 서버에 대한 액세스,
* POP3를 통해 액세스할 수 있는 바운스 사서함,
* 두 개의 DNS 별칭 생성:

   * 처음으로 공개 IP에서 컴퓨터를 추적하고 가리키기 위해 대중에게 노출되었습니다.
   * 콘솔 액세스를 위해 내부 사용자에게 노출되고 동일한 컴퓨터를 가리키는 두 번째 별칭입니다.

* SMTP(25), DNS(53), HTTP(80), HTTPS(443), SQL(Oracle의 경우 1521, PostgreSQL의 경우 5432 등)을 열도록 구성된 방화벽 포트입니다. 자세한 내용은 [네트워크 구성](../../installation/using/network-configuration.md)을 참조하세요.

다음 예에서 인스턴스의 매개 변수는 다음과 같습니다.

* 인스턴스 이름: **demo**
* DNS 마스크: **console.campaign.net&#42;**(클라이언트 콘솔 연결 및 보고서용)
* 데이터베이스: **campaign:demo@dbsrv**

### 설치 및 구성(단일 시스템) {#installing-and-configuring--single-machine-}

다음 단계를 적용합니다.

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

   * Linux의 경우: [서버 처음 시작](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Windows의 경우: [서버를 처음 시작](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

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

1. **config-demo.xml** 파일(**config-default.xml** 옆의 이전 단계에서 생성됨)을 편집하고 **mta**(게재), **wfserver**(워크플로우), **inMail**(바운스 메일) 및 **stat**(통계) 프로세스가 사용하도록 설정되어 있는지 확인하십시오. 그런 다음 통계 서버 주소를 구성합니다.

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

1. **serverConf.xml** 파일을 편집하고 배달 도메인을 지정한 다음 MX 유형 DNS 쿼리에 응답하기 위해 MTA 모듈에서 사용하는 DNS 서버의 IP(또는 호스트) 주소를 지정합니다.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >**nameServers** 매개 변수는 Windows에서만 사용됩니다.

   자세한 내용은 [Campaign 서버 구성](../../installation/using/configuring-campaign-server.md)을 참조하세요.

1. 클라이언트 콘솔 설치 프로그램 **setup-client-7.XXX.exe**&#x200B;을(를) **/datakit/nl/eng/jsp** 폴더에 복사합니다. [자세히 알아보기](../../installation/using/client-console-availability-for-windows.md).

1. 다음 섹션에 설명된 웹 서버 통합 절차(IIS, Apache)를 따릅니다.

   * Linux의 경우: [Linux용 웹 서버에 통합](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Windows의 경우: [Windows용 웹 서버에 통합](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 웹 사이트를 시작하고 URL https://tracking.campaign.net/r/test 을 사용하여 리디렉션을 테스트합니다.

   브라우저에 다음 메시지가 표시되어야 합니다.

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   자세한 내용은 다음 섹션을 참조하십시오.

   * Linux의 경우: [웹 서버 시작 및 구성 테스트](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Windows의 경우: [웹 서버 시작 및 구성 테스트](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

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

1. URL을 사용하여 **nlserver web** 모듈을 테스트합니다. https://console.campaign.net/nl/jsp/logon.jsp

   이 URL을 사용하면 클라이언트 설치 프로그램의 다운로드 페이지에 액세스할 수 있습니다.

   액세스 제어 페이지에 도달하면 **내부** 로그인 및 관련 암호를 입력하십시오. [자세히 알아보기](../../installation/using/client-console-availability-for-windows.md).

   ![](assets/s_ncs_install_access_client.png)

1. 이전 다운로드 페이지에서 Adobe Campaign 클라이언트 콘솔을 시작하거나 Windows 설치를 위해 서버에서 직접 실행하고 서버 연결 URL을 https://console.campaign.net으로 설정한 다음 **내부** 로그인을 사용하여 연결합니다.

   [이 페이지](../../installation/using/creating-an-instance-and-logging-on.md) 및 [이 섹션](../../installation/using/configuring-campaign-server.md#internal-identifier)을 참조하세요.

   처음으로 로그인하면 Database Creation Assistant가 나타납니다.

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   도우미의 단계에 따라 연결 인스턴스와 연결된 데이터베이스를 만듭니다.

   자세한 내용은 [데이터베이스 만들기 및 구성](../../installation/using/creating-and-configuring-the-database.md)을 참조하세요.

   데이터베이스가 생성되면 로그오프합니다.

1. 암호 없이 **admin** 로그인을 사용하여 클라이언트 콘솔에 다시 로그온하고 배포 마법사(**[!UICONTROL Tools > Advanced]** 메뉴)를 시작하여 인스턴스 구성을 완료합니다.

   자세한 내용은 [인스턴스 배포](../../installation/using/deploying-an-instance.md)를 참조하세요.

   설정할 주요 매개 변수는 다음과 같습니다.

   * 이메일 게재: 반송 메일의 발신자 및 회신 주소와 오류 사서함.
   * 추적: 리디렉션에 사용되는 외부 URL과 내부 URL을 채우고 추적 서버에서 **등록**&#x200B;을 클릭한 다음 추적 서버의 **데모** 인스턴스에서 유효성을 검사합니다.

     자세한 내용은 [추적 구성](../../installation/using/deploying-an-instance.md#tracking-configuration)을 참조하세요.

     ![](assets/s_ncs_install_deployment_wiz_09.png)

     Adobe Campaign 서버가 애플리케이션 서버와 리디렉션 서버로 모두 사용되므로 추적 로그를 수집하고 URL을 전송하는 데 사용되는 내부 URL은 Tomcat(https://localhost:8080)에 대한 직접 내부 연결입니다.

   * 바운스 관리: 바운스 메일을 처리할 매개 변수를 입력합니다(**처리되지 않은 바운스 메일** 섹션은 고려하지 않음).
   * 다음에서 액세스: 보고서, 웹 양식 및 미러 페이지에 대한 두 URL을 제공합니다.

     ![](assets/d_ncs_install_web_url.png)
