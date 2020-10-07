---
title: Linux용 웹 서버와 통합
seo-title: Linux용 웹 서버와 통합
description: Linux용 웹 서버와 통합
seo-description: null
page-status-flag: never-activated
uuid: 7b18d176-4458-46a8-8da4-3621f90c6b13
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 752ba848-aee9-4bb0-b2c5-490f3124f74e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 5%

---


# Linux용 웹 서버와 통합{#integration-into-a-web-server-for-linux}

Adobe Campaign에는 HTTP(및 SOAP)를 통해 응용 프로그램 서버의 진입점으로 작동하는 Apache Tomcat이 포함되어 있습니다.

이 통합된 Tomcat 서버를 사용하여 HTTP 요청을 처리할 수 있습니다.

이 경우:

* 기본 의견 수렴 포트는 8080입니다. 변경하려면 Tomcat [구성을 참조하십시오](../../installation/using/configuring-campaign-server.md#configuring-tomcat).
* 그러면 클라이언트 콘솔이 다음과 같은 URL을 사용하여 연결됩니다.

   ```
   http://<computer>:8080
   ```

그러나 보안 및 관리상의 이유로, Adobe Campaign을 실행 중인 컴퓨터가 인터넷에 노출되고 네트워크 외부의 콘솔에 대한 액세스를 열려는 경우 전용 웹 서버를 HTTP 트래픽의 기본 시작 지점으로 사용하는 것이 좋습니다.

또한 웹 서버를 사용하면 HTTPs 프로토콜을 통해 데이터 기밀성을 보장할 수 있습니다.

마찬가지로 웹 서버에 대한 확장 모듈로만 제공되는 추적 기능을 사용하려면 웹 서버를 사용해야 합니다.

>[!NOTE]
>
>추적 기능을 사용하지 않는 경우 Campaign으로 리디렉션을 사용하여 Apache 또는 IIS의 표준 설치를 수행할 수 있습니다. 추적 웹 서버 확장 모듈은 필요하지 않습니다.

## Debian을 사용하여 Apache 웹 서버 구성 {#configuring-the-apache-web-server-with-debian}

APT 기반 배포 아래에 Apache를 설치한 경우 이 프로세스가 적용됩니다.

다음 단계를 적용합니다.

1. 다음 명령을 사용하여 기본적으로 로드되는 모듈을 비활성화합니다.

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   별칭 **,** authz_host **및** mime **모듈이 여전히 활성화되어 있는지** 확인합니다. 이렇게 하려면 다음 명령을 사용합니다.

   ```
   a2enmod  alias authz_host mime
   ```

1. /etc/apache2/ **mods-available** 파일의 **nlsrv.load를** 만들고 다음 내용을 삽입합니다.

   디베이안 8에서:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. 다음 명령을 **사용하여 /etc/apache2** /mods-available **파일의 nlsrv.conf를** 만듭니다.

   ```
   ln -s /usr/local/[INSTALL]/nl6/tomcat-7/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. 다음 명령을 사용하여 이 모듈을 활성화합니다.

   ```
    a2enmod nlsrv
   ```

   Adobe Campaign 페이지에 대한 **mod_rewrite** 모듈 **을 사용 중인 경우, nlsrv.load** 및 **nlsrv.conf** 파일의 이름을 **zz-nsrv.loadSrv.jz-srv.nconf로 변경해야 합니다** ****. 모듈을 활성화하려면 다음 명령을 실행합니다.

   ```
   a2enmod zz-nlsrv
   ```

1. /etc/apache2/ **envars** 파일을 편집하고 다음 줄을 추가합니다.

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   변경 내용을 저장합니다.

1. 그런 다음 다음 다음 유형의 명령을 사용하여 Apache 사용자 그룹에 Adobe Campaign 사용자를, 그 반대로 추가합니다.

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. Apache를 다시 시작합니다.

   ```
   invoke-rc.d apache2 restart
   ```

## RHEL에서 Apache 웹 서버 구성 {#configuring-apache-web-server-in-rhel}

이 절차는 RPM(RHEL, CentOS 및 Suse) 기반 패키지에 Apache를 설치하고 보안을 설정한 경우에 적용됩니다.

다음 단계를 적용합니다.

1. 파일에서 `httpd.conf` 다음 Apache 모듈을 활성화합니다.

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

   비활성화된 모듈에 연결된 기능에 주석을 설정합니다.

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

1. 폴더에 Adobe Campaign 특정 구성 파일을 `/etc/httpd/conf.d/` 만듭니다. 예제 `CampaignApache.conf`

1. RHEL7 ****&#x200B;의 경우 파일에 다음 지침을 추가합니다.

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/tomcat-7/conf/apache_neolane.conf
   ```

1. RHEL7 **의 경우**:

   다음 컨텐츠로 `/etc/systemd/system/httpd.service` 파일을 추가합니다.

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   시스템에서 사용하는 모듈을 업데이트합니다.

   ```
   systemctl daemon-reload
   ```

1. 그런 다음 명령을 실행하여 Adobe Campaign 연산자를 Apache 연산자 그룹에 추가하거나 그 반대로 추가합니다.

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   사용할 그룹 이름은 Apache 구성 방법에 따라 다릅니다.

1. Apache 및 Adobe Campaign 서버를 실행합니다.

   RHEL7의 경우:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## 웹 서버 시작 및 구성 테스트{#launching-the-web-server-and-testing-the-configuration}

이제 Apache를 시작하여 구성을 테스트할 수 있습니다. 이제 Adobe Campaign 모듈이 콘솔에 배너를 표시해야 합니다(특정 운영 체제의 배너 2개).

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

다음으로 테스트 URL을 제출하여 응답하는지 확인합니다.

다음을 실행하여 명령줄에서 테스트할 수 있습니다.

```
 telnet localhost 80  
```

다음을 얻으십시오.

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

웹 브라우저에서 URL을 요청할 수도 [`https://<computer>`](https://machine/r/test) 있습니다.
