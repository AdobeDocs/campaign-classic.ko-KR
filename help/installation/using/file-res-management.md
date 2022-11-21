---
product: campaign
title: 파일 및 리소스 관리
description: Campaign에서 파일 및 리소스 관리를 구성하는 방법을 배웁니다
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 2594e4943ba24ae65d1fc005da589dc674aa2b0f
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# 파일 및 리소스 관리{#file-and-resmanagement}

![](../../assets/v7-only.svg)

## 업로드 파일 형식 제한 {#limiting-uploadable-files}

를 사용하십시오 **uploadWhiteList** Adobe Campaign 서버에서 업로드할 수 있는 파일 유형을 제한하는 속성입니다.

이 속성은 다음 내에서 사용할 수 있습니다 **dataStore** 요소의 요소 **serverConf.xml** 파일. 에서 사용할 수 있는 모든 매개 변수 **serverConf.xml** 여기에 나열되어 있습니다. [섹션](../../installation/using/the-server-configuration-file.md).

이 속성의 기본값은 입니다. **.+** 및 을 사용하면 모든 파일 유형을 업로드할 수 있습니다.

가능한 형식을 제한하려면 속성 값을 유효한 Java 정규 표현식으로 바꿉니다. 여러 값을 쉼표로 구분하여 입력할 수 있습니다.

예: **uploadWhiteList=&quot;.&#42;.png,&#42;.jpg&quot;** 에서는 서버에서 PNG 및 JPG 형식을 업로드할 수 있습니다. 다른 형식은 허용되지 않습니다.

웹 서버를 구성하여 중요한 파일이 업로드되지 않도록 할 수도 있습니다. [자세히 알아보기](web-server-configuration.md)

>[!NOTE]
>
>다음 **uploadWhiteList** 속성은 Adobe Campaign 서버에서 업로드할 수 있는 파일 유형을 제한합니다. 그러나 게시 모드가 **추적 서버** 또는 **기타 Adobe Campaign 서버**, **uploadWhitelist** 또한 해당 서버에서 속성을 업데이트해야 합니다.

## 프록시 연결 구성 {#proxy-connection-configuration}

프록시를 사용하여 Campaign 서버를 외부 시스템에 연결할 수 있습니다. **파일 전송** 예를 들어 워크플로우 활동. 이를 위해서는 다음을 구성해야 합니다 **proxyConfig** 섹션 **serverConf.xml** 특정 명령을 통해 파일을 작성합니다. 에서 사용할 수 있는 모든 매개 변수 **serverConf.xml** 여기에 나열되어 있습니다. [섹션](../../installation/using/the-server-configuration-file.md).

다음 프록시 연결이 가능합니다. HTTP, HTTPS, FTP, SFTP. 20.2 Campaign 릴리스부터 HTTP 및 HTTPS 프로토콜 매개 변수는 다음과 같습니다 **더 이상 사용할 수 없음**. 이러한 매개 변수는 9032를 포함하여 이전 빌드에서 사용할 수 있으므로 여전히 아래에 언급되어 있습니다.

>[!CAUTION]
>
>기본 인증 모드만 지원됩니다. NTLM 인증은 지원되지 않습니다.
>
>SOCKS 프록시는 지원되지 않습니다.

다음 명령을 사용할 수 있습니다.

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

프로토콜 매개 변수는 &#39;http&#39;, &#39;https&#39; 또는 &#39;ftp&#39;일 수 있습니다.

HTTP/HTTPS 트래픽과 동일한 포트에서 FTP를 설정하는 경우 다음을 사용할 수 있습니다.

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

&#39;http&#39; 및 &#39;https&#39; 옵션은 프로토콜 매개 변수가 &#39;ftp&#39;인 경우에만 사용되며, 지정된 포트의 터널링이 HTTPS 또는 HTTP를 통해 수행되는지 여부를 나타냅니다.

프록시 서버를 통해 FTP/SFTP 및 HTTP/HTTPS 트래픽을 위해 다른 포트를 사용하는 경우 &#39;ftp&#39; 프로토콜 매개 변수를 설정해야 합니다.


예제:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

그런 다음 암호를 입력합니다.

HTTP 연결은 proxyHTTP 매개 변수에 정의됩니다.

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

HTTPS 연결은 proxyHTTPS 매개 변수에서 정의됩니다.

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP/FTPS 연결은 proxyFTP 매개 변수에서 정의됩니다.

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

여러 연결 유형에 대해 동일한 프록시를 사용하는 경우 proxyHTTP만 useSingleProxy가 &quot;1&quot; 또는 &quot;true&quot;로 설정된 상태로 정의됩니다.

프록시를 통과해야 하는 내부 연결이 있는 경우 재정의 매개 변수에 추가합니다.

프록시 연결을 일시적으로 비활성화하려면 enabled 매개 변수를 &quot;false&quot; 또는 &quot;0&quot;으로 설정합니다.

프록시를 통해 iOS HTTP/2 커넥터를 사용해야 하는 경우 다음 HTTP 프록시 모드가 지원됩니다.

* 인증이 없는 HTTP
* HTTP 기본 인증

프록시 모드를 활성화하려면 `serverconf.xml` 파일:

```
<nmac useHTTPProxy="true">
```

이 iOS HTTP/2 커넥터에 대한 자세한 내용은 다음을 참조하십시오 [페이지](../../delivery/using/about-mobile-app-channel.md).

## 공개 리소스 관리 {#managing-public-resources}

공개적으로 사용할 수 있도록 하려면 캠페인에 연결된 이메일 및 공개 리소스에 사용되는 이미지가 외부에서 액세스할 수 있는 서버에 있어야 합니다. 그런 다음 외부 수신자 또는 연산자가 사용할 수 있습니다. [자세히 알아보기](../../installation/using/deploying-an-instance.md#managing-public-resources)

공용 리소스는 **/var/res/instance** Adobe Campaign 설치 디렉토리의 디렉토리.

일치하는 URL은 다음과 같습니다. **http://server/res/instance** 여기서 **인스턴스** 는 추적 인스턴스의 이름입니다.

노드에 노드를 추가하여 다른 디렉토리를 지정할 수 있습니다 **conf-`<instance>`.xml** 서버에서 스토리지를 구성할 파일입니다. 즉, 다음 라인을 추가합니다.

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

이 경우 배포 마법사의 창 상단에 있는 공개 리소스에 대한 새 URL은 이 폴더를 가리켜야 합니다.
