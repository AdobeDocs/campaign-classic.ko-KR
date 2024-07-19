---
product: campaign
title: 관리
description: 관리
feature: Monitoring
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: b7dedddc080d1ea8db700fabc9ee03238b3706cc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 1%

---

# 관리{#administration}

Adobe Campaign 모듈(**web**, **mta**, **wfserver** 등)의 자동 시작 은(는) **nlserver** 서버에서 제공합니다.

Adobe Campaign을 설치하면 부팅 순서 중에 **nlserver** 서비스가 시작되도록 컴퓨터가 자동으로 구성됩니다.

다음 명령은 Adobe Campaign 서비스를 수동으로 시작 및 종료하는 데 사용됩니다.

* Windows에서는:

   * **net start nlserver6**
   * **net stop nlserver6**

* Linux에서(루트로):

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 중지**

>[!NOTE]
>
>20.1부터는 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우). **systemctl start nlserver** / **systemctl stop nlserver**

다음은 Linux에서 액세스할 수 있는 일반적인 관리 명령 목록입니다(**Adobe Campaign**).

* 시작된 모든 Adobe Campaign 모듈 표시: **/etc/init.d/nlserver6 pdump** 또는 **/etc/init.d/nlserver6 상태**

  >[!NOTE]
  >
  >**pdump** 명령에 **-who** 매개 변수를 추가하면 현재 연결(사용자 및 프로세스)에 대한 정보를 수집할 수 있습니다.\
  >**/etc/init.d/nlserver6 status** 명령(&quot;-who&quot; 매개 변수 없음)은 다음을 반환합니다.
  >
  >    * 모든 프로세스가 실행 중인 경우 0입니다.
  >    * 프로세스가 누락된 경우 1.
  >    * 실행 중인 프로세스가 없는 경우 2.
  >    * 오류가 있는 경우 다른 값입니다.
  >

* 다중 인스턴스 또는 모노 인스턴스 모듈(**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**) 시작/중지:

  **nlserver 시작`<module>[@<instance>]`**

  **nlserver 중지`<module>[@<instance>][-immediate][-noconsole]`**

  **nlserver 다시 시작`<module>[@<instance>]`** 명령을 사용하여 모듈을 다시 시작할 수도 있습니다.

  예:

  **nlserver 시작 웹**

  **nlserver 시작 mta@my_instance**

  **nlserver 중지 syslogd**

  **nlserver 중지 wfserver@my_instance**

  **nlserver 웹 중지 -immediate**

  **nlserver 웹 다시 시작**

  >[!NOTE]
  >
  >* 인스턴스를 지정하지 않으면 &quot;기본&quot; 인스턴스가 사용됩니다.
  >* 긴급 상황이 발생하면 **-immediate** 옵션을 사용하여 프로세스를 즉시 중지합니다(Unix 명령 **kill -9**&#x200B;과 동일).
  >* **-noconsole** 옵션을 사용하여 실행된 모듈이 콘솔에 아무 것도 표시되지 않도록 하십시오. 해당 로그는 **syslogd** 모듈을 통해 디스크에 기록됩니다.
  >* 프로세스 작업에 대한 추가 정보를 표시하려면 **-verbose** 옵션을 사용하십시오.
  >
  >   예:
  >
  >   **nlserver 웹 다시 시작 -verbose**
  >
  >   **nlserver 시작 mta@myinstance -verbose**
  >
  >   이 옵션은 로그를 추가합니다. 로그를 오버로드하지 않도록 원하는 정보를 찾으면 **-verbose** 옵션 없이 프로세스를 다시 시작하는 것이 좋습니다.

* 모든 Adobe Campaign 프로세스 시작(**nlserver6** 서비스를 시작하는 것과 동일):

  **nlserver watchdog -noconsole**

* 모든 Adobe Campaign 프로세스를 종료합니다(**nlserver6** 서비스를 종료하는 것과 동일).

  **nlserver 종료**

* **serverConf.xml** 및 **config-`<instance>  .xml </instance>`** 파일을 편집한 경우 **nlserver web** 모듈 구성(및 해당되는 경우 웹 서버 확장 모듈)을 다시 로드하십시오.

  **nlserver 구성 -reload**

  >[!NOTE]
  >
  >일부 구성 변경 사항은 동적으로 고려되지 않습니다. Adobe Campaign을 종료한 다음 다시 시작해야 합니다.
