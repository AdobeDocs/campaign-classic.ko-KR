---
title: 관리
seo-title: 관리
description: 관리
seo-description: null
page-status-flag: never-activated
uuid: 376efec1-1647-43b4-b72f-2603214c7cc6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 860be8be-f28c-4836-b4fb-e91c6a4616c6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# 관리{#administration}

Adobe Campaign 모듈의 자동 시작(**웹**, **mta**, **wfserver**&#x200B;등) 은 nlserver 서버에서 **제공합니다** .

Adobe Campaign을 설치하면 컴퓨터가 자동으로 구성되므로 부팅 **시퀀스** 동안 nlserver 서비스가 시작됩니다.

다음 명령은 Adobe Campaign 서비스를 수동으로 시작하고 종료하는 데 사용됩니다.

* Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* Linux(루트로):

   * **/etc/init.d/nlserver6 시작**
   * **/etc/init.d/nlserver6 중지**

다음은 Linux(Adobe Campaign)에서 액세스할 수 있는 일반적인 관리 **명령 목록입니다**.

* 시작된 모든 Adobe Campaign 모듈 표시: **/etc/init.d/nlserver6 pdump** 또는 **/etc/init.d/nlserver6 상태**

   >[!NOTE]
   >
   >pdump 명령에 **who** 매개 변수를 추가하면 **** 현재 연결(사용자 및 프로세스)에 대한 정보를 수집할 수 있습니다.\
   >&quot;- **who&quot; 매개 변수 없이 /etc/init.d/nlserver6 상태** 명령이 반환됩니다.
   >
   >    * 0(모든 프로세스가 실행 중인 경우)
   >    * 1 프로세스가 누락된 경우
   >    * 2 프로세스를 실행하지 않는 경우
   >    * 오류가 있는 경우 다른 값을 사용하십시오.


* 시작/중지 인스턴스 또는 모노 인스턴스 모듈(**웹**, ************&#x200B;추적 **,** syslog d **, mta**, 다중호스트 서버, 다중 호스트 서버, 전자 메일 삽입):

   **nlserver 시작`<module>[@<instance>]`**

   **nlserver 중지`<module>[@<instance>][-immediate][-noconsole]`**

   nlserver **restart`<module>[@<instance>]`**명령을 사용하여 모듈을 다시 시작할 수도 있습니다.

   예:

   **nlserver 시작 웹**

   **nlserver 시작 mta@my_instance**

   **nlserver stop syslogd**

   **nlserver 중지 wfserver@my_instance**

   **nlserver stop web -immediate**

   **nlserver 웹 다시 시작**

   >[!NOTE]

   >* 인스턴스를 지정하지 않으면 &quot;default&quot; 인스턴스가 사용됩니다.
   >    
   >    
   >    * 긴급한 경우 **즉시** 옵션을 사용하여 프로세스를 즉시 중지합니다(Unix 명령 **kill -9**&#x200B;준수와 동일).
   * noconsole **** 옵션을 사용하여 시작한 모듈이 콘솔에 아무 것도 표시되지 않도록 합니다. 로그가 **syslogd 모듈을 통해 디스크에 기록됩니다** .
   * 자세한 **정보** 옵션을 사용하여 프로세스 작업에 대한 추가 정보를 표시합니다.


      예:


      **nlserver에서 웹 다시 시작 -verbose**


      **nlserver start mta@myinstance -verbose**


      이 옵션은 추가 로그를 추가합니다. 로그를 오버로딩하지 않도록 원하는 정보를 찾은 후 **세부 정보** 옵션 없이 프로세스를 다시 시작하는 것이 좋습니다.


* 모든 Adobe Campaign 프로세스를 시작합니다(nlserver6 **서비스를 시작하는** 것과 같음).

   **nlserver watchdog -noconsole**

* 모든 Adobe Campaign 프로세스를 종료합니다(nlserver6 **서비스를 종료하는** 것과 같음).

   **nlserver 종료**

* serverConf.xml **및** 구성- **파일이 편집되면 Nlserver 웹** 모듈 구성(및 해당되는 경우 웹 서버 확장 모듈)을 다시 불러옵니다 **`<instance>  .xml </instance>`**.

   **nlserver config -reload**

   >[!NOTE]
   일부 구성 변경 사항은 동적으로 고려되지 않습니다.Adobe Campaign을 종료한 다음 다시 시작해야 합니다.

