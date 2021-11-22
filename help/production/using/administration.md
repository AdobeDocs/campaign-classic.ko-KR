---
product: campaign
title: 관리
description: 관리
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# 관리{#administration}

![](../../assets/v7-only.svg)

Adobe Campaign 모듈의 자동 시작(**웹**, **mta**, **wfserver**&#x200B;등) 는 **nlserver** server.

Adobe Campaign을 설치하면 **nlserver** 부팅 시퀀스 중에 서비스가 시작됩니다.

다음 명령은 Adobe Campaign 서비스를 수동으로 시작하고 종료하는 데 사용됩니다.

* Windows에서:

   * **net start nlserver6**
   * **net stop nlserver6**

* Linux(루트로):

   * **/etc/init.d/nlserver6 시작**
   * **/etc/init.d/nlserver6 중지**

>[!NOTE]
>
>20.1부터 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우). **systectl start nlserver** / **systectl stop nlserver**

다음은 Linux에서 액세스할 수 있는 일반적인 관리 명령 목록입니다 **Adobe Campaign**):

* 시작된 모든 Adobe Campaign 모듈을 표시합니다. **/etc/init.d/nlserver6 pdump** 또는 **/etc/init.d/nlserver6 상태**

   >[!NOTE]
   >
   >추가 **-누가** 매개 변수 **pdump** 명령을 사용하면 현재 연결(사용자 및 프로세스)에 대한 정보를 수집할 수 있습니다.\
   >다음 **/etc/init.d/nlserver6 상태** 명령(&quot;-who&quot; 매개 변수 없이)은 다음을 반환합니다.
   >
   >    * 모든 프로세스가 실행 중인 경우 0입니다.
   >    * 1 프로세스가 누락된 경우
   >    * 2 프로세스를 실행하지 않는 경우
   >    * 오류가 있는 경우 다른 값입니다.


* 다중 인스턴스 또는 모노 인스턴스 모듈 시작/중지(**웹**, **trackinglogd**, **sylogd**, **mta**, **wfserver**, **inmail**):

   **nlserver 시작`<module>[@<instance>]`**

   **nlserver 중지`<module>[@<instance>][-immediate][-noconsole]`**

   를 사용할 수도 있습니다 **nlserver 다시 시작`<module>[@<instance>]`** 모듈을 다시 시작하는 명령

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
   >* 비상 상황이 발생하는 경우 **-immediate** 프로세스를 즉시 중지하기 위한 옵션(Unix 명령에 해당) **kill-9**).
   >* 를 사용하십시오 **-noconsole** 모듈을 시작한 경우 콘솔에 아무 것도 표시되지 않도록 하는 옵션입니다. 해당 로그가 를 통해 디스크에 기록됩니다. **sylogd** 모듈.
   >* 를 사용하십시오 **-verbose** 프로세스 작업에 대한 추가 정보를 표시하는 옵션.

      >
      >   예제:
      >
      >   **nlserver 다시 시작 웹 -verbose**
      >
      >   **nlserver 시작 mta@myinstance -verbose**
      >
      >   이 옵션은 추가 로그를 추가합니다. 다음을 수행하지 않고 프로세스를 다시 시작하는 것이 좋습니다 **-verbose** 로그 오버로드를 방지하기 위해 원하는 정보를 찾은 경우 선택합니다.


* 모든 Adobe Campaign 프로세스를 시작합니다(시작을 위해 **nlserver6** service):

   **nlserver watchdog -noconsole**

* 모든 Adobe Campaign 프로세스를 종료합니다(을 종료하면 **nlserver6** service):

   **nlserver 종료**

* 를 다시 로드합니다. **nlserver 웹** 모듈 구성(해당되는 경우 웹 서버 확장 모듈) **serverConf.xml** 및 **config-`<instance>  .xml </instance>`** 파일이 편집되었습니다.

   **nlserver 구성 -reload**

   >[!NOTE]
   >
   >일부 구성 변경 사항은 동적으로 고려되지 않습니다. Adobe Campaign을 종료한 다음 다시 시작해야 합니다.
