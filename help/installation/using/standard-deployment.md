---
solution: Campaign Classic
product: campaign
title: 표준 배포
description: 표준 배포
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 1%

---


# 표준 배포{#standard-deployment}

이 구성에서 3대의 컴퓨터가 필요합니다.

* 최종 사용자를 위한 LAN 내 응용 프로그램 서버(캠페인 준비, 보고 등),
* 부하 균형 조정기 뒤에 DMZ에 있는 두 개의 전두엽 서버.

DMZ 내의 두 서버는 추적, 미러 페이지 및 전달을 처리하고 고가용성을 위해 중복됩니다.

LAN의 응용 프로그램 서버는 최종 사용자를 지원하며 모든 반복 프로세스(워크플로 엔진)를 수행합니다. 따라서 정면서버에서 최고 로드가 도달해도 애플리케이션 사용자에게 영향을 주지 않습니다.

데이터베이스 서버는 이러한 3가지 서버로부터 별도의 컴퓨터에 호스팅할 수 있습니다. 그렇지 않은 경우 Adobe Campaign(Linux 또는 Windows)에서 운영 체제를 지원하는 경우 응용 프로그램 서버 및 데이터베이스 서버가 LAN 내에서 동일한 컴퓨터를 공유할 수 있습니다.

서버와 프로세스 간의 일반적인 통신은 다음 스키마에 따라 수행됩니다.

![](assets/s_001_ncs_install_standardconfig.png)

이 유형의 구성은 데이터베이스 서버(및 사용 가능한 대역폭)가 기본 제한 요소이므로 많은 수의 받는 사람(500,000~1,000,000)을 처리할 수 있습니다.

## 기능 {#features}

### 장점 {#advantages}

* 페일오버 기능:하드웨어 문제가 발생할 경우 다른 컴퓨터의 프로세스로 전환하는 기능
* 부하 균형 조정기 뒤에 있는 두 컴퓨터에 MTA 및 리디렉션 함수를 배포할 수 있으므로 전반적인 성능이 향상됩니다. 활성 MTA가 2개 있고 대역폭이 충분하여 시간당 100,000개의 이메일이 있는 지역의 방송율을 달성할 수 있습니다.

## 설치 및 구성 단계 {#installation-and-configuration-steps}

### 사전 요구 사항 {#prerequisites}

* JDK는 컴퓨터 세 대에
* 웹 서버(IIS, Apache)를 두 최전선에서 모두
* 세 대의 컴퓨터에 있는 데이터베이스 서버에
* POP3,
* 2개의 DNS 별칭 생성:

   * 가상 IP 주소(VIP)에서 로드 밸런서를 추적 및 가리키기 위해 처음으로 공개되어 두 개의 전두엽 서버에 배포됩니다.
   * 콘솔을 통해 동일한 응용 프로그램 서버를 가리키기 위해 내부 사용자에게 두 번째 노출.

* STMP(25), DNS(53), HTTP(80), HTTPS(443), SQL(Oracle의 경우 1521, PostgreSQL의 경우 5432) 등을 열도록 구성된 방화벽 포트. 자세한 내용은 [데이터베이스 액세스](../../installation/using/network-configuration.md#database-access) 섹션을 참조하십시오.

### 응용 프로그램 서버 {#installing-the-application-server} 설치

Adobe Campaign 응용 프로그램 서버에서 독립 실행형 인스턴스를 설치하는 단계에 따라 데이터베이스를 만듭니다(12단계). [설치 및 구성(단일 컴퓨터)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-)을 참조하십시오.

컴퓨터가 추적 서버가 아니므로 웹 서버와의 통합을 고려하지 마십시오.

다음 예에서 인스턴스의 매개 변수는 다음과 같습니다.

* 인스턴스의 이름:**demo**
* DNS 마스크:**console.campaign.net***(클라이언트 콘솔 연결 및 보고서에만 해당)
* 언어:영어
* 데이터베이스:**캠페인:demo@dbsrv**

### 2개의 전면 서버 {#installing-the-two-frontal-servers} 설치

설치 및 구성 절차는 두 컴퓨터 모두에서 동일합니다.

이 단계는 다음과 같습니다.

1. Adobe Campaign 서버를 설치합니다.

   자세한 내용은 Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md)에서 [Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md)(Linux)에서 캠페인 설치 사전 요구 사항 및 [캠페인 설치 사전 요구 사항(Windows)을 참조하십시오.

1. 다음 섹션에 설명된 웹 서버 통합 절차(IIS, Apache)를 따르십시오.

   * Linux의 경우:[Linux용 웹 서버에 통합](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Windows의 경우:[Windows용 웹 서버에 통합](../../installation/using/integration-into-a-web-server-for-windows.md)

1. **demo** 인스턴스를 만듭니다. 두 가지 방법이 있습니다.

   * 콘솔을 통해 인스턴스를 만듭니다.

      ![](assets/install_create_new_connexion.png)

      자세한 내용은 [인스턴스 만들기 및](../../installation/using/creating-an-instance-and-logging-on.md)에 로그온을 참조하십시오.

      또는

   * 명령줄을 사용하여 인스턴스를 만듭니다.

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*
      ```

      자세한 내용은 [인스턴스 만들기](../../installation/using/command-lines.md#creating-an-instance)를 참조하십시오.
   인스턴스의 이름은 응용 프로그램 서버의 이름과 같습니다.

   **nlserver web** 모듈(미러 페이지, 구독 취소)이 있는 서버에 대한 연결은 부하 균형 조정기(tracking.campaign.net)의 URL에서 수행됩니다.

1. **internal**&#x200B;을 응용 프로그램 서버와 동일하게 변경합니다.

   자세한 내용은 [내부 식별자](../../installation/using/campaign-server-configuration.md#internal-identifier)를 참조하십시오.

1. 데이터베이스를 인스턴스에 연결:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. **config-default.xml** 및 **config-demo.xml** 파일에서 **web**, **trackinglogd** 및 **mta** 모듈을 활성화합니다.

   자세한 내용은 [프로세스 활성화](../../installation/using/campaign-server-configuration.md#enabling-processes)를 참조하십시오.

1. **serverConf.xml** 파일을 편집하고 다음을 채웁니다.

   * MTA 모듈의 DNS 구성:

      ```
      <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
      ```

      >[!NOTE]
      >
      >**nameServers** 매개 변수는 Windows에서만 사용됩니다.

      자세한 내용은 [배달 설정](../../installation/using/campaign-server-configuration.md#delivery-settings)을 참조하십시오.

   * 리디렉션 매개 변수의 중복 추적 서버:

      ```
      <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
      <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
      ```

      자세한 내용은 [중복 추적](../../installation/using/configuring-campaign-server.md#redundant-tracking)을 참조하십시오.

1. 웹 사이트를 시작하고 URL에서 리디렉션을 테스트합니다.[https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test).

   브라우저에 다음과 같은 메시지가 표시되어야 합니다(부하 균형 조정기가 리디렉션하는 URL에 따라 다름).

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   또는

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   자세한 내용은 다음 섹션을 참조하십시오.

   * Linux의 경우:[웹 서버 시작 및 구성 테스트](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Windows의 경우:[웹 서버 시작 및 구성 테스트](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Adobe Campaign 서버를 시작합니다.
1. Adobe Campaign 콘솔에서 암호 없이 **admin** 로그인을 사용하여 연결하고 배포 마법사를 시작합니다.

   자세한 내용은 [인스턴스 배포](../../installation/using/deploying-an-instance.md)를 참조하십시오.

   구성은 추적 모듈의 구성과 별도로 독립 실행형 인스턴스와 동일합니다.

1. 리디렉션에 사용되는 외부 URL(부하 균형 조정기의 URL)과 2개의 전두엽 서버의 내부 URL을 채웁니다.

   자세한 내용은 [추적 구성](../../installation/using/deploying-an-instance.md#tracking-configuration)을 참조하십시오.

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >이전에 만든 두 추적 서버의 기존 인스턴스를 사용하고 **internal** 로그인을 사용합니다.

