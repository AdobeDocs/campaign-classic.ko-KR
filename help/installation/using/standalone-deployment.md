---
solution: Campaign Classic
product: campaign
title: 독립형 배포
description: 독립형 배포
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---


# 독립형 배포{#standalone-deployment}

이 구성에는 동일한 컴퓨터에 있는 모든 구성 요소가 포함됩니다.

* 응용 프로그램 프로세스(웹),
* 배달 프로세스(mta),
* 리디렉션 프로세스(추적),
* 워크플로우 프로세스 및 예약된 작업(wfserver),
* 바운스 메일 프로세스(inMail),
* 통계 프로세스(시작).

프로세스 간의 전체 통신은 다음 스키마에 따라 수행됩니다.

![](assets/s_900_ncs_install_standaloneconfig.png)

이러한 유형의 구성은 수신자가 100,000명 미만인 목록을 관리하고 예를 들어 다음 소프트웨어 레이어를 사용하여 실행할 수 있습니다.

* Linux,
* Apache,
* PostgreSQL,
* Qmail.

볼륨이 증가하면 이 아키텍처의 변형으로 데이터베이스 서버를 다른 컴퓨터로 이동하여 성능을 향상시킵니다.

>[!NOTE]
>
>기존 데이터베이스 서버가 충분한 리소스를 갖고 있는 경우에도 사용할 수 있습니다.

## 기능 {#features}

### 장점 {#advantages}

* 전체 독립 실행형 및 낮은 구성 비용(아래 나열된 오픈 소스 소프트웨어를 사용하는 경우 청구 가능한 라이선스 필요 없음).
* 설치 및 네트워크 구성 간소화

### 단점 {#disadvantages}

* 사고 시 중요한 컴퓨터.
* 메시지를 브로드캐스트할 때 제한된 대역폭입니다(Adobe 경험에서 시간당 수 만 개의 메일).
* 방송 시 응용 프로그램의 속도가 느려질 수 있습니다.
* 응용 프로그램 서버는 리디렉션 서버를 호스팅하기 때문에 DMZ에 있는 동안 바깥쪽에서 사용할 수 있어야 합니다.

## 설치 및 구성 단계 {#installation-and-configuration-steps}

### 사전 요구 사항 {#prerequisites}

* JDK,
* 웹 서버(IIS, Apache),
* 데이터베이스 서버에 대한 액세스,
* POP3,
* 2개의 DNS 별칭 생성:

   * 공개 IP에서 컴퓨터를 추적하고 가리키는 것을 대중에게 처음으로 노출되는 것;
   * 콘솔 액세스 및 동일한 컴퓨터를 가리키기 위해 내부 사용자에게 표시되는 두 번째 별칭입니다.

* SMTP(25), DNS(53), HTTP(80), HTTPS(443), SQL(Oracle의 경우 1521, PostgreSQL의 경우 5432) 열도록 구성된 방화벽 포트. 자세한 내용은 [네트워크 구성](../../installation/using/network-configuration.md)을 참조하십시오.

다음 예에서 인스턴스의 매개 변수는 다음과 같습니다.

* 인스턴스의 이름:**demo**
* DNS 마스크:**console.campaign.net***(클라이언트 콘솔 연결 및 보고서에만 해당)
* 데이터베이스:**캠페인:demo@dbsrv**

### 설치 및 구성(단일 컴퓨터) {#installing-and-configuring--single-machine-}

다음 단계를 적용합니다.

1. Adobe Campaign 서버에 대한 설치 절차를 따르십시오.Linux의 경우 **nlserver** 패키지 또는 Windows의 경우 **setup.exe**.

   자세한 내용은 Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md)에서 [Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md)(Linux)에서 캠페인 설치 사전 요구 사항 및 [캠페인 설치 사전 요구 사항(Windows)을 참조하십시오.

1. Adobe Campaign 서버가 설치되면 **nlserver web -tomcat** 명령을 사용하여 응용 프로그램 서버(웹)를 시작하고 Tomcat이 포트 8080에서 수신 대기 중인 독립 실행형 웹 서버 모드에서 시작할 수 있으며 Tomcat가 올바르게 시작하는지 확인합니다.

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >웹 모듈을 처음 실행하면 설치 폴더 아래의 **conf** 디렉토리에 **config-default.xml** 및 **serverConf.xml** 파일이 생성됩니다. **serverConf.xml**&#x200B;에 사용 가능한 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열됩니다.

   서버를 중지하려면 **Ctrl+C**&#x200B;을 누릅니다.

   자세한 내용은 다음 섹션을 참조하십시오.

   * Linux의 경우:[서버](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Windows의 경우:[서버](../../installation/using/installing-the-server.md#first-start-up-of-the-server)의 첫 번째 시작.

1. 다음 명령을 사용하여 **내부** 암호를 변경합니다.

   ```
   nlserver config -internalpassword
   ```

   자세한 내용은 [내부 식별자](../../installation/using/campaign-server-configuration.md#internal-identifier)를 참조하십시오.

1. 추적을 위해 DNS 마스크가 있는 **demo** 인스턴스를 만들고(이 경우 **tracking.campaign.net**) 클라이언트 콘솔에 액세스합니다(이 경우 **console.campaign.net**). 두 가지 방법이 있습니다.

   * 콘솔을 통해 인스턴스를 만듭니다.

      ![](assets/install_create_new_connexion.png)

      자세한 내용은 [인스턴스 만들기 및](../../installation/using/creating-an-instance-and-logging-on.md)에 로그온을 참조하십시오.

      또는

   * 명령줄을 사용하여 인스턴스를 만듭니다.

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      자세한 내용은 [인스턴스 만들기](../../installation/using/command-lines.md#creating-an-instance)를 참조하십시오.

1. **config-demo.xml** 파일(**config-default.xml** 옆의 이전 단계에서 생성)을 편집하고 **mta**(배달), **wfserver**(워크플로), **inMail**(메일) 및 &lt;a메일) a10/>통계&#x200B;**(통계) 프로세스가 활성화됩니다.** 그런 다음 통계 서버의 주소를 구성합니다.

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

   자세한 내용은 [프로세스 활성화](../../installation/using/campaign-server-configuration.md#enabling-processes)를 참조하십시오.

1. **serverConf.xml** 파일을 편집하고 배달 도메인을 지정한 다음 MTA 모듈에서 MX 유형 DNS 쿼리에 응답하는 DNS 서버의 IP(또는 호스트) 주소를 지정합니다.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >**nameServers** 매개 변수는 Windows에서만 사용됩니다.

   자세한 내용은 [캠페인 서버 구성](../../installation/using/campaign-server-configuration.md)을 참조하십시오.

1. 클라이언트 콘솔 설정 프로그램(**setup-client-7.XX**, **YYYY.exe**, v7 또는 **setup-client-6.XX**, **YYY.exe**)을 **/datakit/로 복사합니다. nl/eng/jsp** 폴더.

   자세한 내용은 다음 섹션을 참조하십시오.

   * Linux의 경우:[Linux용 클라이언트 콘솔 사용 가능 시기](../../installation/using/client-console-availability-for-linux.md)
   * Windows의 경우:[Windows](../../installation/using/client-console-availability-for-windows.md)에 대한 클라이언트 콘솔 가용성

1. 다음 섹션에 설명된 웹 서버 통합 절차(IIS, Apache)를 따르십시오.

   * Linux의 경우:[Linux용 웹 서버에 통합](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Windows의 경우:[Windows용 웹 서버에 통합](../../installation/using/integration-into-a-web-server-for-windows.md)

1. URL을 사용하여 웹 사이트를 시작하고 리디렉션을 테스트합니다.https://tracking.campaign.net/r/test을 참조하십시오.

   브라우저에 다음 메시지가 표시되어야 합니다.

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   자세한 내용은 다음 섹션을 참조하십시오.

   * Linux의 경우:[웹 서버 시작 및 구성 테스트](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Windows의 경우:[웹 서버 시작 및 구성 테스트](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Adobe Campaign 서버(**Net start nlserver6**, Windows의 경우 **/etc/init.d/nlserver6 start**)를 시작하고 **nlserver dump** 명령을 한 번 더 실행하여 활성화된 모든 모듈의 존재를 확인합니다.

   >[!NOTE]
   >
   >20.1부터는 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우).**systemctl 시작 nlserver**

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

1. URL을 사용하여 **nserver 웹** 모듈을 테스트합니다.https://console.campaign.net/nl/jsp/logon.jsp

   이 URL을 통해 클라이언트 설정 프로그램의 다운로드 페이지에 액세스할 수 있습니다.

   액세스 제어 페이지에 도달하면 **내부** 로그인 및 관련 암호를 입력합니다.

   ![](assets/s_ncs_install_access_client.png)

   자세한 내용은 다음 섹션을 참조하십시오.

   * Linux의 경우:[Linux용 클라이언트 콘솔 사용 가능 시기](../../installation/using/client-console-availability-for-linux.md)
   * Windows의 경우:[Windows](../../installation/using/client-console-availability-for-windows.md)에 대한 클라이언트 콘솔 가용성

1. Adobe Campaign 클라이언트 콘솔을 시작(이전 다운로드 페이지에서 또는 Windows 설치의 경우 서버에서 직접 시작)하고 서버 연결 URL을 https://console.campaign.net으로 설정하고 **internal** 로그인을 사용하여 연결합니다.

   [인스턴스 만들기 및](../../installation/using/creating-an-instance-and-logging-on.md) 및 [내부 식별자](../../installation/using/campaign-server-configuration.md#internal-identifier)를 참조하십시오.

   처음으로 로그인하면 데이터베이스 만들기 마법사가 나타납니다.

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   마법사의 단계에 따라 연결 인스턴스와 연결된 데이터베이스를 만듭니다.

   자세한 내용은 [데이터베이스 만들기 및 구성을 참조하십시오](../../installation/using/creating-and-configuring-the-database.md).

   데이터베이스가 만들어지면 로그오프하십시오.

1. 암호 없이 **admin** 로그인을 사용하여 클라이언트 콘솔에 다시 로그온하고 배포 마법사( **[!UICONTROL Tools > Advanced]** 메뉴)를 시작하여 인스턴스 구성을 완료합니다.

   자세한 내용은 [인스턴스 배포](../../installation/using/deploying-an-instance.md)를 참조하십시오.

   설정할 기본 매개 변수는 다음과 같습니다.

   * 이메일 배달:보낸 사람 및 답글 주소와 바운스 메일의 오류 사서함.
   * 추적:리디렉션에 사용되는 외부 URL과 내부 URL을 채우고 추적 서버&#x200B;**에서**&#x200B;등록을 클릭한 다음 추적 서버의 **demo** 인스턴스에서 확인합니다.

      자세한 내용은 [추적 구성](../../installation/using/deploying-an-instance.md#tracking-configuration)을 참조하십시오.

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      Adobe Campaign 서버가 응용 프로그램 서버와 리디렉션 서버로 사용되므로 추적 로그를 수집하고 URL을 전송하는 데 사용되는 내부 URL은 Tomcat(https://localhost:8080)에 직접 내부 연결됩니다.

   * 바운스 관리:바운스 메일을 처리할 매개 변수를 입력합니다. **처리되지 않은 바운스 메일** 섹션을 고려하지 마십시오.
   * 액세스 위치:보고서, 웹 양식 및 미러 페이지에 대한 2개의 URL을 제공합니다.

      ![](assets/d_ncs_install_web_url.png)

