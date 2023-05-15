---
product: campaign
title: 표준 배포
description: 표준 배포
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 4df126fa-4a6e-46a7-af6e-1e2e97f0072e
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 3%

---

# 표준 배포{#standard-deployment}



이 구성의 경우 3대의 컴퓨터가 필요합니다.

* 최종 사용자를 위한 LAN 내의 애플리케이션 서버(캠페인, 보고 준비 등),
* 로드 밸런서 뒤에 DMZ에 있는 2개의 전두부 서버

DMZ에 있는 두 서버는 추적, 미러 페이지 및 게재를 처리하며 고가용성을 위해 중복됩니다.

LAN의 응용 프로그램 서버는 최종 사용자를 제공하고 모든 반복 프로세스(워크플로우 엔진)를 수행합니다. 따라서 정면서버에서 최대 로드에 도달하면 애플리케이션 사용자에게 영향을 주지 않습니다.

데이터베이스 서버는 이 세 가지 서버와 별도의 컴퓨터에서 호스팅될 수 있습니다. 운영 체제가 Adobe Campaign(Linux 또는 Windows)에서 지원되는 경우 애플리케이션 서버와 데이터베이스 서버가 LAN 내에서 동일한 컴퓨터를 공유할 수 있습니다.

서버와 프로세스 간의 일반 통신은 다음 스키마에 따라 수행됩니다.

![](assets/s_001_ncs_install_standardconfig.png)

이러한 유형의 구성은 데이터베이스 서버(사용 가능한 대역폭)가 주요 제한 요소이므로 많은 수의 수신자(50만~100만 명)를 처리할 수 있습니다.

## 기능 {#features}

### 장점 {#advantages}

* 페일오버 기능: 다른 컴퓨터에서 하드웨어 문제가 발생할 경우 프로세스를 하나의 컴퓨터로 전환할 수 있습니다.
* 부하 분산 장치 뒤의 두 컴퓨터에 MTA 및 리디렉션 기능을 배포할 수 있으므로 전반적인 성능이 향상됩니다. 두 개의 활성 MTA와 충분한 대역폭을 사용하여 시간당 100,000개의 메일들의 방송속도를 달성할 수 있습니다.

## 설치 및 구성 단계 {#installation-and-configuration-steps}

### 전제 조건 {#prerequisites}

* JDK는 세 대의 컴퓨터 모두
* 두 프론트에 있는 웹 서버(IIS, Apache),
* 세 대의 컴퓨터에서 데이터베이스 서버에 액세스하며
* POP3를 통해 액세스할 수 있는 바운스 사서함,
* 두 개의 DNS 별칭 생성:

   * 가상 IP 주소(VIP)에서 로드 밸런서를 추적 및 가리키도록 공개되어 두 개의 전면 서버에 배포됩니다.
   * 콘솔을 통해 액세스할 내부 사용자에게 노출되고 동일한 애플리케이션 서버를 가리키는 두 번째 작업입니다.

* STMP(25), DNS(53), HTTP(80), HTTPS(443), SQL(Oracle의 경우 1521, PostgreSQL의 경우 5432)를 열도록 구성된 방화벽 포트. 자세한 내용은 섹션을 참조하십시오 [데이터베이스 액세스](../../installation/using/network-configuration.md#database-access).

### 애플리케이션 서버 설치 {#installing-the-application-server}

Adobe Campaign 애플리케이션 서버에서 독립형 인스턴스를 설치하는 단계에 따라 데이터베이스를 만듭니다(12단계). 을(를) 참조하십시오. [설치 및 구성(단일 시스템)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

컴퓨터가 추적 서버가 아니므로 웹 서버와의 통합을 고려하지 마십시오.

다음 예에서 인스턴스의 매개 변수는 다음과 같습니다.

* 인스턴스 이름: **데모**
* DNS 마스크: **console.campaign.net&#42;** (클라이언트 콘솔 연결 및 보고서에만 해당)
* 언어: 영어
* 데이터베이스: **campaign:demo@dbsrv**

### 2개의 전면 서버 설치 {#installing-the-two-frontal-servers}

설치 및 구성 절차는 두 컴퓨터 모두에서 동일합니다.

단계는 다음과 같습니다.

1. Adobe Campaign 서버를 설치합니다.

   자세한 내용은 [Linux에서 캠페인 설치 사전 요구 사항](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) 및 [Windows에서 Campaign 설치 사전 요구 사항](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. 다음 섹션에 설명된 웹 서버 통합 절차(IIS, Apache)를 따르십시오.

   * Linux의 경우: [Linux용 웹 서버와 통합](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Windows의 경우: [Windows용 웹 서버에 통합](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 만들기 **데모** 인스턴스. 다음 두 가지 방법으로 데이터를 수집할 수 있습니다.

   * 콘솔을 통해 인스턴스를 생성합니다.

      ![](assets/install_create_new_connexion.png)

      자세한 내용은 [인스턴스 만들기 및 로그온](../../installation/using/creating-an-instance-and-logging-on.md).

      또는

   * 명령줄을 사용하여 인스턴스를 생성합니다.

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*
      ```

      자세한 내용은 [인스턴스 만들기](../../installation/using/command-lines.md#creating-an-instance).
   인스턴스 이름은 애플리케이션 서버의 이름과 같습니다.

   를 사용하여 서버에 연결 **nlserver 웹** 모듈(미러 페이지, 구독 취소)은 로드 밸런서의 URL에서 수행됩니다(tracking.campaign.net).

1. 변경 **내부** 응용 프로그램 서버와 동일하게

   이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#internal-identifier)을 참조하십시오.

1. 데이터베이스를 인스턴스에 연결:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. 에서 **config-default.xml** 및 **config-demo.xml** 파일, 활성화 **웹**, **trackinglogd** 및 **mta** 모듈.

   이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#enabling-processes)을 참조하십시오.

1. 편집 **serverConf.xml** 파일 및 채우기:

   * mta 모듈의 DNS 구성:

      ```
      <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
      ```

      >[!NOTE]
      >
      >다음 **nameServers** 매개 변수는 Windows에서만 사용됩니다.

      자세한 내용은 [게재 설정](configure-delivery-settings.md).

   * 리디렉션 매개 변수의 중복 추적 서버:

      ```
      <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
      <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
      ```

      자세한 내용은 [중복 추적](configuring-campaign-server.md#redundant-tracking).

1. 웹 사이트를 시작하고 URL에서 리디렉션을 테스트합니다. [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test).

   브라우저에 로드 밸런서에서 리디렉션하는 URL에 따라 다음 메시지가 표시됩니다.

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   또는

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   자세한 정보는 다음 섹션을 참조하십시오.

   * Linux의 경우: [웹 서버 시작 및 구성 테스트](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Windows의 경우: [웹 서버 시작 및 구성 테스트](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Adobe Campaign 서버를 시작합니다.
1. Adobe Campaign 콘솔에서 을 사용하여 연결합니다. **관리** 암호 없이 로그인하고 배포 마법사를 시작합니다.

   자세한 내용은 [인스턴스 배포](../../installation/using/deploying-an-instance.md).

   구성은 추적 모듈의 구성과 별도로 독립 실행형 인스턴스와 동일합니다.

1. 리디렉션에 사용되는 외부 URL(로드 밸런서의 URL)과 두 전두서버의 내부 URL을 채웁니다.

   자세한 내용은 [구성 추적](../../installation/using/deploying-an-instance.md#tracking-configuration).

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >이전에 만든 두 추적 서버의 기존 인스턴스를 사용하고 **내부** 로그인.
