---
title: 캠페인 서버 구성
seo-title: 캠페인 서버 구성
description: 캠페인 서버 구성
seo-description: null
page-status-flag: never-activated
uuid: a1fadad2-e888-4dd8-bc1f-04df16ba7d46
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: f296676e-3bf1-47da-8239-f5ae54e52fc0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4869eb41f942a89c48bc213913c44b70ae777bfc

---


# 캠페인 서버 구성{#campaign-server-configuration}

다음 섹션에서는 대부분의 설정에 대해 Adobe Campaign의 효율적인 운영을 보장하는 필수 서버 구성에 대해 자세히 설명합니다.

캠페인 서버 [](../../installation/using/configuring-campaign-server.md)구성에서 추가 구성이 제공됩니다.

>[!NOTE]
>
>서버측 구성은 Adobe가 호스팅하는 배포에 대해서만 수행할 수 있습니다. 서로 다른 배포에 대한 자세한 내용은 호스팅 모델 [](../../installation/using/hosting-models.md) 섹션 또는 [이 문서를](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)참조하십시오.

## 내부 식별자 {#internal-identifier}

내부 **** 식별자는 설치, 관리 및 유지 관리 목적으로 사용되는 기술 로그인입니다. 이 로그인은 인스턴스와 연결되어 있지 않습니다.

이 로그인을 사용하여 연결된 연산자는 모든 인스턴스에 대한 모든 권한을 가집니다. 새 설치의 경우 이 로그인에 암호가 없습니다. 이 암호를 수동으로 정의해야 합니다.

다음 명령을 사용합니다.

```
nlserver config -internalpassword
```

그러면 다음 정보가 표시됩니다. 암호를 입력하고 확인합니다.

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## 구성 파일 {#configuration-files}

구성 파일은 Adobe Campaign 설치 폴더의 **conf** 폴더에 저장됩니다. 구성은 다음 두 파일에 분산됩니다.

* **`config-<instance>.xml`** (여기서 **instance** is the name of the instance):인스턴스의 특정 구성. 여러 인스턴스 간에 서버를 공유하는 경우 관련 파일의 각 인스턴스에 해당하는 매개 변수를 입력하십시오.
* **serverConf.xml**:일반 구성. 이 파일은 Adobe Campaign 서버의 기술 매개 변수를 결합합니다.모든 인스턴스에서 공유됩니다. 이러한 매개 변수 중 일부에 대한 설명은 아래에 자세히 설명되어 있습니다. 사용 가능한 모든 매개 변수를 보려면 파일 자체를 참조하십시오. 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열된 다른 노드 및 매개 변수입니다.

Adobe Campaign 데이터의 저장소 디렉토리(**var** 디렉토리)를 구성할 수 있습니다(로그, 다운로드, 리디렉션 등). 이렇게 하려면 XTK_VAR_ **DIR 시스템 변수를** 사용합니다.

* Windows에서는 XTK_VAR_DIR **시스템 변수에 다음 값을** 지정합니다

   ```
   D:\log\AdobeCampaign
   ```

* Linux에서 **customer.sh** 파일로 이동하여 다음을 표시합니다.XTK_VAR_DIR=/app/log/AdobeCampaign을 **내보냅니다**.

   자세한 내용은 매개 변수 [개인화를](../../installation/using/installing-packages-with-linux.md#personalizing-parameters)참조하십시오.

## 프로세스 활성화 {#enabling-processes}

서버의 Adobe Campaign 프로세스는 **config-default.xml** 및 **`config-<instance>.xml`** 파일을 통해 활성화(및 비활성화)됩니다.

이러한 파일에 변경 사항을 적용하려면 Adobe Campaign 서비스가 시작된 경우 **nlserver config -reload** 명령을 실행해야 합니다.

두 가지 유형의 프로세스가 있습니다.다중 인스턴스 및 단일 인스턴스.

* **다중 인스턴스**:하나의 프로세스가 모든 인스턴스에 대해 시작됩니다. 이는 **웹**, **syslogd** 및 **trackinglogd** 프로세스의 경우입니다.

   Enablement는 **config-default.xml** 파일에서 구성할 수 있습니다.

   클라이언트 콘솔에 액세스하고 리디렉션(추적)을 위해 Adobe Campaign 서버를 선언합니다.

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   이 예제에서는 Linux에서 **vi** 명령을 사용하여 파일을 편집합니다. 모든 **.txt** 또는 **.xml** 편집기를 사용하여 편집할 수 있습니다.

* **모노 인스턴스**:각 인스턴스에 대해 하나의 프로세스가 시작됩니다(모듈: **mmm****,** wfserver **,** inMail **의** sms ta **,** and statstat).

   인스턴스의 구성 파일을 사용하여 활성화를 구성할 수 있습니다.

   ```
   config-<instance>.xml
   ```

   배달 서버 선언, 워크플로우 인스턴스 실행 및 바운스 메일 복구:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

## 배달 설정 {#delivery-settings}

배달 매개 변수는 serverConf.xml **폴더에** 구성해야 합니다.

* **DNS 구성**:mta 모듈에서 MX 유형 DNS 쿼리에 응답하는 데 사용되는 DNS 서버의 배달 도메인 및 IP 주소(또는 호스트)를 **`<dnsconfig>`** 계속 지정합니다.

   >[!NOTE]
   >
   >nameServers **** 매개 변수는 Windows에서 설치하는 데 반드시 필요합니다. Linux에서 설치하려면 비워 두어야 합니다.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

이 파일에서 사용할 수 있는 다른 배달 매개 변수는 [배달 매개 변수](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters)개인화에 제공됩니다.

이메일 [전달을 참조하십시오](../../installation/using/email-deliverability.md).
