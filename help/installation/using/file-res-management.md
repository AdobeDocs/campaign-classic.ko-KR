---
product: campaign
title: 파일 및 리소스 관리
feature: Installation, Application Settings
description: Campaign에서 파일 및 리소스 관리를 구성하는 방법 알아보기
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 1%

---

# 파일 및 리소스 관리{#file-and-resmanagement}



## 업로드 파일 형식 제한 {#limiting-uploadable-files}

**uploadWhiteList** 특성을 사용하여 Adobe Campaign 서버에서 업로드할 수 있는 파일 형식을 제한하십시오.

이 특성은 **serverConf.xml** 파일의 **dataStore** 요소에서 사용할 수 있습니다. **serverConf.xml**&#x200B;에서 사용할 수 있는 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열되어 있습니다.

이 특성의 기본값은 **입니다.+** 및 을(를) 사용하면 모든 파일 형식을 업로드할 수 있습니다.

가능한 형식을 제한하려면 속성 값을 유효한 Java 정규 표현식으로 바꿉니다. 쉼표로 구분하여 여러 값을 입력할 수 있습니다.

예: **uploadWhiteList=&quot;.&#42;.png,.&#42;.jpg&quot;**&#x200B;을(를) 통해 PNG 및 JPG 형식을 서버에 업로드할 수 있습니다. 다른 형식은 허용되지 않습니다.

웹 서버를 구성하여 중요한 파일이 업로드되지 않도록 할 수도 있습니다. [자세히 알아보기](web-server-configuration.md)

>[!NOTE]
>
>**uploadWhiteList** 특성은 Adobe Campaign 서버에서 업로드할 수 있는 파일 형식을 제한합니다. 그러나 게시 모드가 **추적 서버** 또는 **다른 Adobe Campaign 서버**&#x200B;인 경우 **uploadWhitelist** 특성도 해당 서버에서 업데이트해야 합니다.

## 프록시 연결 구성 {#proxy-connection-configuration}

예를 들어 **파일 전송** 워크플로우 활동을 사용하여 프록시를 통해 Campaign 서버를 외부 시스템에 연결할 수 있습니다. 이렇게 하려면 특정 명령을 통해 **serverConf.xml** 파일의 **proxyConfig** 섹션을 구성해야 합니다. **serverConf.xml**&#x200B;에서 사용할 수 있는 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열되어 있습니다.

가능한 프록시 연결은 HTTP, HTTPS, FTP, SFTP입니다. 20.2 Campaign 릴리스부터 HTTP 및 HTTPS 프로토콜 매개 변수는 **더 이상 사용할 수 없습니다**. 이러한 매개 변수는 9032를 포함하여 이전 빌드에서 계속 사용할 수 있으므로 아래에 계속 언급되어 있습니다.

>[!CAUTION]
>
>기본 인증 모드만 지원됩니다. NTLM 인증이 지원되지 않습니다.
>
>SOCKS 프록시는 지원되지 않습니다.
>

다음 명령을 사용할 수 있습니다.

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

프로토콜 매개 변수는 &#39;http&#39;, &#39;https&#39; 또는 &#39;ftp&#39;일 수 있습니다.

HTTP/HTTPS 트래픽과 동일한 포트에서 FTP를 설정하는 경우 다음을 사용할 수 있습니다.

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

&#39;http&#39; 및 &#39;https&#39; 옵션은 프로토콜 매개 변수가 &#39;ftp&#39;이고 지정된 포트의 터널링이 HTTPS를 통해 수행되는지 또는 HTTP를 통해 수행되는지를 나타내는 경우에만 사용됩니다.

프록시 서버에서 FTP/SFTP 및 HTTP/HTTPS 트래픽에 다른 포트를 사용하는 경우 &#39;ftp&#39; 프로토콜 매개 변수를 설정해야 합니다.


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

HTTPS 연결은 proxyHTTPS 매개 변수에 정의됩니다.

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP/FTPS 연결은 proxyFTP 매개 변수에 정의되어 있습니다.

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

여러 연결 유형에 동일한 프록시를 사용하는 경우 useSingleProxy가 &quot;1&quot; 또는 &quot;true&quot;로 설정된 proxyHTTP만 정의됩니다.

프록시를 거치지 않아야 하는 내부 연결이 있는 경우 재정의 매개 변수에 해당 연결을 추가합니다.

프록시 연결을 일시적으로 비활성화하려면 활성화된 매개 변수를 &quot;false&quot; 또는 &quot;0&quot;으로 설정합니다.

프록시를 통해 iOS HTTP/2 커넥터를 사용해야 하는 경우 다음 HTTP 프록시 모드가 지원됩니다.

* 인증 없이 HTTP
* HTTP 기본 인증

프록시 모드를 활성화하려면 `serverconf.xml` 파일에서 다음 변경을 수행해야 합니다.

```
<nmac useHTTPProxy="true">
```

이 iOS HTTP/2 커넥터에 대한 자세한 내용은 이 [페이지](../../delivery/using/about-mobile-app-channel.md)를 참조하세요.

## 공개 리소스 관리 {#managing-public-resources}

캠페인에 연결된 이메일 및 공개 리소스에 사용되는 이미지를 공개적으로 사용할 수 있으려면 외부에서 액세스할 수 있는 서버에 표시해야 합니다. 그런 다음 외부 수신자 또는 운영자가 사용할 수 있습니다. [자세히 알아보기](../../installation/using/deploying-an-instance.md#managing-public-resources).

공개 리소스는 Adobe Campaign 설치 디렉터리의 **/var/res/instance** 디렉터리에 저장됩니다.

일치하는 URL은 **http://server/res/instance**&#x200B;입니다. 여기서 **instance**&#x200B;은(는) 추적 인스턴스의 이름입니다.

**conf-`<instance>`.xml** 파일에 노드를 추가하여 서버에서 저장소를 구성하여 다른 디렉터리를 지정할 수 있습니다. 즉, 다음 줄을 추가합니다.

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

이 경우 배포 마법사 창의 위쪽에 제공된 공개 리소스에 대한 새 URL이 이 폴더를 가리켜야 합니다.
