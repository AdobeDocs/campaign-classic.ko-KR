---
product: campaign
title: 관리
description: 관리
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# 관리{#administration}



Adobe Campaign 모듈 자동 시작(**웹**, **mta**, **wfserver**&#x200B;등) 에서 제공합니다. **nlserver** 서버입니다.

Adobe Campaign을 설치하면 **nlserver** 부팅 순서 중에 서비스가 시작됩니다.

다음 명령은 Adobe Campaign 서비스를 수동으로 시작 및 종료하는 데 사용됩니다.

* Windows에서는:

   * **net start nlserver6**
   * **net stop nlserver6**

* Linux에서(루트로):

   * **/etc/init.d/nlserver6 시작**
   * **/etc/init.d/nlserver6 중지**

>[!NOTE]
>
>20.1부터 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우). **systemctl start nlserver** / **systemctl stop nlserver**

다음은 Linux에서 액세스할 수 있는 일반적인 관리 명령 목록입니다 **Adobe Campaign**):

* 시작된 모든 Adobe Campaign 모듈 표시: **/etc/init.d/nlserver6 pdump** 또는 **/etc/init.d/nlserver6 상태**

   >[!NOTE]
   >
   >추가 **-후** 매개 변수를 **덤프** 명령을 사용하면 현재 연결(사용자 및 프로세스)에 대한 정보를 수집할 수 있습니다.\
   >다음 **/etc/init.d/nlserver6 상태** 명령(&quot;-who&quot; 매개 변수 없음)은 다음을 반환합니다.
   >
   >    * 모든 프로세스가 실행 중인 경우 0입니다.
   >    * 프로세스가 누락된 경우 1.
   >    * 실행 중인 프로세스가 없는 경우 2.
   >    * 오류가 있는 경우 다른 값입니다.


* 다중 인스턴스 또는 모노 인스턴스 모듈 시작/중지(**웹**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**):

   **nlserver 시작`<module>[@<instance>]`**

   **nlserver 중지`<module>[@<instance>][-immediate][-noconsole]`**

   다음을 사용할 수도 있습니다 **nlserver 다시 시작`<module>[@<instance>]`** 모듈을 다시 시작하는 명령.

   예제:

   **nlserver 시작 웹**

   **nlserver 시작 mta@my_instance**

   **nlserver syslogd 중지**

   **nlserver 중지 wfserver@my_instance**

   **nlserver stop web -immediate**

   **nlserver 웹 다시 시작**

   >[!NOTE]
   >
   >* 인스턴스를 지정하지 않으면 &quot;기본&quot; 인스턴스가 사용됩니다.
   >* 긴급 상황 발생 시 **-immediate** 프로세스를 즉시 중단하는 옵션(Unix 명령과 동일) **킬 -9**).
   >* 사용 **-noconsole** 옵션을 사용하여 실행된 모듈이 콘솔에 아무 것도 표시되지 않도록 합니다. 해당 로그는 를 통해 디스크에 기록됩니다. **syslogd** 모듈.
   >* 사용 **-verbose** 프로세스 작업에 대한 추가 정보를 표시하는 옵션.

      >
      >   예제:
      >
      >   **nlserver 다시 시작 웹 -verbose**
      >
      >   **nlserver 시작 mta@myinstance -verbose**
      >
      >   이 옵션은 로그를 추가합니다. 을(를) 제외하고 프로세스를 다시 시작하는 것이 좋습니다. **-verbose** 원하는 정보를 찾으면 옵션을 사용하여 로그를 오버로드할 수 있습니다.


* 모든 Adobe Campaign 프로세스 시작(다음을 시작하는 것과 동일) **nlserver6** service):

   **nlserver watchdog -noconsole**

* 모든 Adobe Campaign 프로세스를 종료합니다(를 종료하는 것과 동일). **nlserver6** service):

   **nlserver 종료**

* 다시 로드 **nlserver 웹** 모듈 구성(및 해당되는 경우 웹 서버 확장 모듈) **serverConf.xml** 및 **config-`<instance>  .xml </instance>`** 파일이 편집되었습니다.

   **nlserver 구성 -reload**

   >[!NOTE]
   >
   >일부 구성 변경 사항은 동적으로 고려되지 않습니다. Adobe Campaign을 종료한 다음 다시 시작해야 합니다.
