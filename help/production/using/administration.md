---
solution: Campaign Classic
product: campaign
title: 관리
description: 관리
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---


# 관리{#administration}

Adobe Campaign 모듈의 자동 시작(**웹**, **mta**, **wfserver** 등) 은 **nlserver** 서버에서 제공합니다.

Adobe Campaign을 설치하면 부팅 시퀀스 동안 **nlserver** 서비스가 시작되도록 시스템이 자동으로 구성됩니다.

다음 명령은 Adobe Campaign 서비스를 수동으로 시작하고 종료하는 데 사용됩니다.

* Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* Linux(루트로):

   * **/etc/init.d서버6 시작**
   * **/etc/init.d서버6 중지**

>[!NOTE]
>
>20.1부터는 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우).**systemctl start nlserver** / **systemctl stop nlserver**

다음은 Linux에서 액세스할 수 있는 일반적인 관리 명령 목록입니다(**Adobe Campaign**).

* 시작된 Adobe Campaign 모듈 모두 표시:**/etc/init.d/nlserver6 dump** 또는 **/etc/init.d/nlserver6 상태**

   >[!NOTE]
   >
   >**-who** 매개 변수를 **pdump** 명령에 추가하면 현재 연결(사용자 및 프로세스)에 대한 정보를 수집할 수 있습니다.\
   >**/etc/init.d/nlserver6 status** 명령(&quot;-who&quot; 매개 변수 없이)이 반환됩니다.
   >
   >    * 모든 프로세스가 실행 중인 경우 0.
   >    * 1 프로세스가 누락된 경우
   >    * 2 프로세스를 실행할 필요가 없는 경우
   >    * 오류가 있는 경우 다른 값입니다.


* 다중 인스턴스 또는 모노 인스턴스 모듈(**웹**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**> ):

   **nlserver 시작`<module>[@<instance>]`**

   **nlserver 중지`<module>[@<instance>][-immediate][-noconsole]`**

   **nlserver 다시 시작`<module>[@<instance>]`** 명령을 사용하여 모듈을 다시 시작할 수도 있습니다.

   예제:

   **nlserver 시작 웹**

   **nlserver 시작 mta@my_instance**

   **nlserver stop sylogd**

   **nlserver 중지 wfserver@my_instance**

   **nlserver stop web -immediate**

   **nlserver 웹 다시 시작**

   >[!NOTE]
   > 
   >    * 인스턴스를 지정하지 않으면 &quot;default&quot; 인스턴스가 사용됩니다.
   >    * 긴급한 경우 **-immediate** 옵션을 사용하여 프로세스를 즉시 중단(Unix 명령 **kill -9**&#x200B;에 해당)합니다.
   >    * **-noconsole** 옵션을 사용하여 시작한 모듈이 콘솔에 아무 것도 표시되지 않도록 합니다. 해당 로그는 **syslogd** 모듈을 통해 디스크에 기록됩니다.
   >    * 프로세스 작업에 대한 추가 정보를 표시하려면 **-verbose** 옵션을 사용합니다.

      >    
      >      
      예제:
      >    
      >      
      **nlserver를 다시 시작하는 웹 -verbose**
      >    
      >      
      **nlserver 시작 mta@myinstance -verbose**
      >    
      >      
      이 옵션은 추가 로그를 추가합니다. 로그가 오버로드되지 않도록 하려면 원하는 정보를 찾은 후 **-verbose** 옵션 없이 프로세스를 다시 시작하는 것이 좋습니다.


* 모든 Adobe Campaign 프로세스 시작(**nlserver6** 서비스 시작과 동일):

   **nlserver watchdog -noconsole**

* 모든 Adobe Campaign 프로세스를 종료합니다(**nlserver6** 서비스를 종료하는 것과 동일).

   **nlserver 종료**

* **serverConf.xml** 및 **config-`<instance>  .xml </instance>`** 파일이 편집되면 **nlserver 웹** 모듈 구성(및 해당되는 경우 웹 서버 확장 모듈)을 다시 로드합니다.

   **nlserver 구성 -reload**

   >[!NOTE]
   >
   >일부 구성 변경 사항은 동적으로 고려되지 않습니다.Adobe Campaign을 종료한 다음 다시 시작해야 합니다.

