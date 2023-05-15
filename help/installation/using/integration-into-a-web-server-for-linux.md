---
product: campaign
title: Linux용 웹 서버와 통합
description: Campaign을 웹 서버(Linux)에 통합하는 방법을 알아봅니다
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 2%

---

# Linux용 웹 서버와 통합{#integration-into-a-web-server-for-linux}



Adobe Campaign에는 HTTP(및 SOAP)를 통해 애플리케이션 서버에서 시작 지점 역할을 하는 Apache Tomcat이 포함되어 있습니다.

이러한 통합된 Tomcat 서버를 사용하여 HTTP 요청을 제공할 수 있습니다.

이 경우:

* 기본 수신 포트는 8080입니다. 변경하려면 다음을 참조하십시오 [이 섹션](configure-tomcat.md).
* 그런 다음 클라이언트 콘솔은 다음과 같은 URL을 사용하여 연결합니다.

   ```
   http://<computer>:8080
   ```

그러나 보안 및 관리를 위해 Adobe Campaign을 실행 중인 컴퓨터가 인터넷에 노출되어 네트워크 외부의 콘솔에 대한 액세스를 열려는 경우 전용 웹 서버를 HTTP 트래픽의 기본 시작 지점으로 사용하는 것이 좋습니다.

웹 서버에서도 HTTP 프로토콜을 통해 데이터 기밀성을 보장할 수 있습니다.

마찬가지로, 웹 서버에 대한 확장 모듈로만 사용할 수 있는 추적 기능을 사용하려면 웹 서버를 사용해야 합니다.

>[!NOTE]
>
>추적 기능을 사용하지 않는 경우 Campaign으로 리디렉션하여 Apache 또는 IIS의 표준 설치를 수행할 수 있습니다. 추적 웹 서버 확장 모듈은 필요하지 않습니다.

## Debian으로 Apache 웹 서버 구성 {#configuring-the-apache-web-server-with-debian}

APT를 기반으로 한 배포 아래에 Apache를 설치한 경우 이 프로세스가 적용됩니다.

다음 단계를 적용합니다.

1. 다음 명령을 사용하여 기본적으로 로드되는 모듈을 비활성화합니다.

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   다음을 확인합니다. **별칭**, **authz_host** 및 **mime** 모듈이 계속 활성화되어 있습니다. 이렇게 하려면 다음 명령을 사용합니다.

   ```
   a2enmod  alias authz_host mime
   ```

1. 파일 만들기 **nlsrv.load** in **/etc/apache2/mods-available** 다음 내용을 삽입합니다.

   Debian 8에서:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. 파일 만들기 **nlsrv.conf** in **/etc/apache2/mods-available** 다음 명령 사용:

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. 다음 명령을 사용하여 이 모듈을 활성화합니다.

   ```
    a2enmod nlsrv
   ```

   를 사용하는 경우 **mod_rewrite** Adobe Campaign 페이지용 모듈에서는 이름을 변경해야 합니다 **nlsrv.load** 및 **nlsrv.conf** 파일 위치 **zz-nlsrv.load** 및 **zz-nlsrv.conf**. 모듈을 활성화하려면 다음 명령을 실행합니다.

   ```
   a2enmod zz-nlsrv
   ```

1. 편집 **/etc/apache2/envvars** 파일에서 다음 줄을 추가합니다.

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   변경 사항을 저장합니다.

1. 그런 다음 다음 다음 유형의 명령을 사용하여 Adobe Campaign 사용자를 Apache 사용자 그룹에, 그 반대로 추가합니다.

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. Apache를 다시 시작합니다.

   ```
   invoke-rc.d apache2 restart
   ```

## RHEL에서 Apache 웹 서버 구성 {#configuring-apache-web-server-in-rhel}

이 절차는 RPM(RHEL, CentOS 및 Suse) 기반 패키지 아래에 Apache를 설치 및 고정한 경우에 적용됩니다.

다음 단계를 적용합니다.

1. 에서 `httpd.conf` 파일에서 다음 Apache 모듈을 활성화합니다.

   ```
   alias
   authz_host
   mime
   ```

1. 다음 모듈을 비활성화합니다.

   ```
   auth_basic
   authn_file
   authz_default
   authz_user
   autoindex
   cgi
   dir
   env
   negotiation
   userdir
   ```

   비활성화된 모듈에 연결된 함수 설명:

   ```
   DirectoryIndex
   IndexOptions    
   AddIconByEncoding    
   AddIconByType    
   AddIcon    
   DefaultIcon    
   ReadmeName    
   HeaderName    
   IndexIgnore    
   LanguagePriority    
   ForceLanguagePriority
   ```

1. 에서 Adobe Campaign 관련 구성 파일을 만듭니다 `/etc/httpd/conf.d/` 폴더를 입력합니다. 예제 `CampaignApache.conf`

1. 대상 **RHEL7**&#x200B;를 눌러 파일에 다음 지침을 추가합니다.

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. 대상 **RHEL7**:

   추가 `/etc/systemd/system/httpd.service` 다음 컨텐츠가 있는 파일:

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   시스템에서 사용하는 모듈을 업데이트합니다.

   ```
   systemctl daemon-reload
   ```

1. 그런 다음 명령을 실행하여 Adobe Campaign 연산자를 Apache 연산자 그룹에, 그 반대로 추가합니다.

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   사용할 그룹 이름은 Apache 구성 방식에 따라 다릅니다.

1. Apache 및 Adobe Campaign 서버를 실행합니다.

   RHEL7의 경우:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## 웹 서버 시작 및 구성 테스트{#launching-the-web-server-and-testing-the-configuration}

이제 Apache를 시작하여 구성을 테스트할 수 있습니다. 이제 Adobe Campaign 모듈이 콘솔에 배너를 표시해야 합니다(특정 운영 체제에 두 개의 배너).

```
 /etc/init.d/apache start
```

다음 정보가 표시됩니다.

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

다음 테스트 URL을 제출하여 응답하는지 확인합니다.

다음을 실행하여 명령줄에서 이 작업을 테스트할 수 있습니다.

```
 telnet localhost 80  
```

다음을 획득해야 합니다.

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
```

그런 다음 다음을 입력합니다.

```
GET /r/test
```

다음 정보가 표시됩니다.

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
```

URL을 요청할 수도 있습니다 [`https://<computer>`](https://myserver.adobe.com/r/test) 클릭합니다.
