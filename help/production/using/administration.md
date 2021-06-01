---
product: campaign
title: 관리
description: 관리
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# 관리{#administration}

Adobe Campaign 모듈(**웹**, **mta**, **wfserver** 등)의 자동 시작 는 **nlserver** 서버에서 제공합니다.

Adobe Campaign을 설치하면 부팅 시퀀스 동안 **nlserver** 서비스가 시작되도록 시스템이 자동으로 구성됩니다.

다음 명령은 Adobe Campaign 서비스를 수동으로 시작하고 종료하는 데 사용됩니다.

* Windows에서:

   * **net start nlserver6**
   * **net stop nlserver6**

* Linux(루트로):

   * **/etc/init.d/nlserver6 시작**
   * **/etc/init.d/nlserver6 중지**

>[!NOTE]
>
>20.1부터 대신 다음 명령을 사용하는 것이 좋습니다(Linux의 경우).**systemctl start nlserver** / **systemctl stop nlserver**

다음은 Linux에서 액세스할 수 있는 일반적인 관리 명령 목록입니다( **Adobe Campaign**).

* 시작된 모든 Adobe Campaign 모듈을 표시합니다.**/etc/init.d/nlserver6 pdump** 또는 **/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >**-who** 매개 변수를 **pdump** 명령에 추가하면 현재 연결(사용자 및 프로세스)에 대한 정보를 수집할 수 있습니다.\
   >**/etc/init.d/nlserver6 status** 명령(&quot;-who&quot; 매개 변수 없이)은 다음을 반환합니다.
   >
   >    * 모든 프로세스가 실행 중인 경우 0입니다.
   >    * 1 프로세스가 누락된 경우
   >    * 2 프로세스를 실행하지 않는 경우
   >    * 오류가 있는 경우 다른 값입니다.


* 다중 인스턴스 또는 모노 인스턴스 모듈(**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**) 시작/정지:

   **nlserver 시작`<module>[@<instance>]`**

   **nlserver 중지`<module>[@<instance>][-immediate][-noconsole]`**

   **nlserver 다시 시작`<module>[@<instance>]`** 명령을 사용하여 모듈을 다시 시작할 수도 있습니다.

   예제:

   **nlserver 시작 웹**

   **nlserver 시작 mta@my_instance**

   **nlserver 중지 sylogd**

   **nlserver 중지 wfserver@my_instance**

   **nlserver stop web -immediate**

   **nlserver 다시 시작 웹**

   >[!NOTE]
   >
   >* 인스턴스를 지정하지 않으면 &quot;기본&quot; 인스턴스가 사용됩니다.
   >* 긴급한 경우 **-immediate** 옵션을 사용하여 프로세스를 즉시 중지합니다(Unix 명령 **kill -9**&#x200B;에 해당).
   >* **-noconsole** 옵션을 사용하여 실행된 모듈이 콘솔에 아무 것도 표시되지 않도록 합니다. 해당 로그는 **syslogd** 모듈을 통해 디스크에 기록됩니다.
   >* 프로세스 작업에 대한 추가 정보를 표시하려면 **-verbose** 옵션을 사용합니다.

      >
      >   
      예제:
      >
      >   
      **nlserver 다시 시작 웹 -verbose**
      >
      >   
      **nlserver 시작 mta@myinstance -verbose**
      >
      >   
      이 옵션은 추가 로그를 추가합니다. 로그를 오버로드하는 것을 방지하기 위해 원하는 정보를 찾은 경우 **-verbose** 옵션 없이 프로세스를 다시 시작하는 것이 좋습니다.


* 모든 Adobe Campaign 프로세스를 시작합니다(**nlserver6** 서비스 시작에 해당):

   **nlserver watchdog -noconsole**

* 모든 Adobe Campaign 프로세스를 종료합니다(**nlserver6** 서비스를 종료하는 것과 같음).

   **nlserver 종료**

* **serverConf.xml** 및 **config-`<instance>  .xml </instance>`** 파일이 편집되면 **nlserver web** 모듈 구성(및 해당되는 경우 웹 서버 확장 모듈)을 다시 로드합니다.

   **nlserver 구성 -reload**

   >[!NOTE]
   >
   >일부 구성 변경 사항은 동적으로 고려되지 않습니다.Adobe Campaign을 종료한 다음 다시 시작해야 합니다.
