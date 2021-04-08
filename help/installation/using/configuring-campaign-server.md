---
solution: Campaign Classic
product: campaign
title: Campaign 서버 구성
description: Campaign 서버 구성
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
translation-type: tm+mt
source-git-commit: 0c83c989c7e3718a989a4943f5cde7ad4717fddc
workflow-type: tm+mt
source-wordcount: '2810'
ht-degree: 6%

---

# Campaign 서버 구성{#configuring-campaign-server}

아래 섹션에서는 요구 사항 및 환경 사양에 맞게 수행할 수 있는 서버측 구성에 대해 자세히 설명합니다.

이러한 구성은 관리자가 수행해야 하고 **온-프레미스** 호스팅 모델에만 사용해야 합니다.

**호스팅** 배포의 경우 서버측 설정은 Adobe에서만 구성할 수 있습니다. 그러나 Campaign 컨트롤 패널 내에서 일부 설정을 설정할 수 있습니다(예: IP 허용 목록에 추가하다 관리 또는 URL 권한).

>[!NOTE]
>
>Campaign 컨트롤 패널은 모든 관리 사용자가 액세스할 수 있습니다. 사용자에게 관리자 권한을 부여하는 단계는 [이 섹션](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=ko#discover-control-panel)에 자세히 설명되어 있습니다.
>
>인스턴스는 AWS에서 호스팅되어야 하며 최신 [Gold Standard](../../rn/using/gs-overview.md) 빌드 또는 [최신 GA 빌드(21.1)](../../rn/using/latest-release.md)로 업그레이드해야 합니다. [이 섹션](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)에서 자신의 버전을 확인하는 방법을 알아봅니다. 인스턴스가 AWS에서 호스팅되는지 확인하려면 [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)에 설명된 단계를 따르십시오.

자세한 내용은 다음 섹션을 참조하십시오.

* [Campaign 컨트롤 패널 설명서](https://docs.adobe.com/content/help/ko-KR/control-panel/using/control-panel-home.html)
* [호스팅 모델](../../installation/using/hosting-models.md)
* [Campaign Classic 온-프레미스 및 호스팅 기능 매트릭스](../../installation/using/capability-matrix.md)
* [하이브리드 및 호스트 모델 구성 단계](../../installation/using/hosting-models.md)

Campaign Classic 구성 파일은 Adobe Campaign 설치 폴더의 **conf** 폴더에 저장됩니다. 구성은 2개의 파일에 분산됩니다.

* **serverConf.xml**:모든 인스턴스에 대한 일반 구성. 이 파일은 Adobe Campaign 서버의 기술 매개 변수를 결합합니다.모든 인스턴스에서 공유됩니다. 이러한 매개 변수 중 일부에 대한 설명은 아래에 자세히 나와 있습니다. 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열된 다른 노드 및 매개 변수입니다.
* **config-`<instance>`.xml** (여기서  **** instanceis the name of the instance):인스턴스의 특정 구성. 여러 인스턴스 간에 서버를 공유하는 경우 관련 파일의 각 인스턴스에 해당하는 매개 변수를 입력하십시오.

## {#configuring-tomcat} Tomcat 구성

### Tomcat {#default-port-for-tomcat}의 기본 포트

Tomcat 서버의 8080 수신 대기 포트가 구성에 필요한 다른 애플리케이션으로 이미 사용 중인 경우 8080 포트를 무료 포트(예: 8090)로 교체해야 합니다. 변경하려면 Adobe Campaign 설치 폴더의 **/tomcat-8/conf** 디렉토리에 저장된 **server.xml** 파일을 편집합니다.

그런 다음 JSP 릴레이 페이지의 포트를 수정합니다. 이렇게 하려면 Adobe Campaign 설치 디렉토리의 **/conf** 디렉토리에 저장된 **serverConf.xml** 파일을 변경합니다. **serverConf.xml**&#x200B;에 사용 가능한 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열됩니다.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

### Tomcat {#mapping-a-folder-in-tomcat}의 폴더 매핑

고객별 설정을 정의하려면 **contexts.xml** 파일도 포함하는 **/tomcat-8/conf** 폴더에 **user_contexts.xml** 파일을 만들 수 있습니다.

이 파일에는 다음 정보 유형이 포함됩니다.

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

필요한 경우 이 작업을 서버측에서 재현할 수 있습니다.

## 배달 매개 변수 사용자 정의 {#personalizing-delivery-parameters}

전달 매개 변수는 **serverConf.xml** 구성 파일에 정의됩니다. **serverConf.xml**&#x200B;에 사용 가능한 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열됩니다.

일반 서버 구성 및 명령은 [캠페인 서버 구성](../../installation/using/campaign-server-configuration.md)에 자세히 설명되어 있습니다.

필요에 따라 다음 구성을 수행할 수도 있습니다.

### SMTP 릴레이 {#smtp-relay}

MTA 모듈은 SMTP 브로드캐스트(포트 25)에 대한 기본 메일 전송 에이전트 역할을 합니다.

그러나 보안 정책에 필요한 경우 릴레이 서버로 바꿀 수 있습니다. 이 경우, 글로벌 처리량은 릴레이 처리량이 됩니다(릴레이 서버 처리량이 Adobe Campaign 처리량보다 낮음).

이 경우 이러한 매개 변수는 **`<relay>`** 섹션에서 SMTP 서버를 구성하여 설정합니다. 메일 및 관련 포트(기본적으로 25개)를 전송하는 데 사용되는 SMTP 서버의 IP 주소(또는 호스트)를 지정해야 합니다.

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>이 운영 모드는 릴레이 서버 내부 성능(지연, 반밴드..)으로 인해 처리량을 크게 줄일 수 있으므로 배달 시 심각한 제한 사항을 의미합니다. 또한, SMTP 트래픽을 분석하여 감지된 동기 배달 오류를 평가할 수 있는 능력이 제한되며 릴레이 서버를 사용할 수 없을 경우 전송을 수행할 수 없습니다.

### MTA 하위 프로세스 {#mta-child-processes}

서버의 CPU 성능 및 사용 가능한 네트워크 리소스에 따라 브로드캐스트 성능을 최적화하기 위해 하위 프로세스(기본적으로 maxSpareServer 2)의 채우기를 제어할 수 있습니다. 이 구성은 각 개별 컴퓨터에서 MTA 구성의 **`<master>`** 섹션에서 수행합니다.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

또한 [이메일 전송 최적화](../../installation/using/email-deliverability.md#email-sending-optimization)를 참조하십시오.

### 친화성 {#managing-outbound-smtp-traffic-with-affinities}이(가) 있는 아웃바운드 SMTP 트래픽 관리

>[!IMPORTANT]
>
>친화성 구성은 한 서버에서 다른 서버로 일관되어야 합니다. MTA를 실행하는 모든 응용 프로그램 서버에서 구성 변경 사항을 복제해야 하므로 선호도 구성을 위해 Adobe에 문의하는 것이 좋습니다.

IP 주소가 있는 친화성을 통해 아웃바운드 SMTP 트래픽을 개선할 수 있습니다.

이렇게 하려면 다음 단계를 적용합니다.

1. **serverConf.xml** 파일의 **`<ipaffinity>`** 섹션에 친화성을 입력합니다.

   친화성 하나는 여러 다른 이름을 가질 수 있습니다.구분하려면 **;** 문자를 사용합니다.

   예제:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   관련 매개 변수를 보려면 **serverConf.xml** 파일을 참조하십시오.

1. 드롭다운 목록에서 친화성 선택을 활성화하려면 **IPAfferity** 열거형에 친화성 이름을 추가해야 합니다.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >열거형은 [이 문서](../../platform/using/managing-enumerations.md)에 자세히 설명되어 있습니다.

   그런 다음 유형 유형 분류에 대해 아래에 표시된 것처럼 사용할 선호도를 선택할 수 있습니다.

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >[배달 서버 구성](../../installation/using/email-deliverability.md#delivery-server-configuration)을 참조할 수도 있습니다.

## URL 권한 {#url-permissions}

Campaign Classic 인스턴스에서 워크플로우 등의 JavaScript 코드를 통해 호출할 수 있는 URL의 기본 목록은 제한되어 있습니다. 인스턴스는 이러한 URL이 있어야 정상 작동합니다.

기본적으로 인스턴스는 외부 URL에 연결할 수 없습니다. 그러나 외부 URL을 승인된 URL 목록에 추가할 수 있으므로 인스턴스가 URL에 연결할 수 있습니다. 이렇게 하면 파일 및/또는 데이터를 전송할 수 있도록 SFTP 서버나 웹 사이트 등의 외부 시스템에 Campaign 인스턴스를 연결할 수 있습니다.

추가한 URL은 인스턴스의 구성 파일(serverConf.xml)에서 참조됩니다.

URL 권한을 관리할 수 있는 방법은 호스팅 모델에 따라 다릅니다.

* **하이브리더** 온-프레미스 ****:serverConf.xml 파일에 허용하도록 URL **을 추가합니다**. 자세한 정보는 아래 섹션에 있습니다.
* **호스팅**:Campaign 컨트롤 패널을 통해 허용할 URL을  **추가합니다**. 자세한 내용은 [전용 설명서](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/url-permissions.html)를 참조하십시오.

   >[!NOTE]
   >
   >Campaign 컨트롤 패널은 모든 관리 사용자가 액세스할 수 있습니다. 사용자에게 관리자 권한을 부여하는 단계는 [이 섹션](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel)에 자세히 설명되어 있습니다.
   >
   >인스턴스는 AWS에서 호스팅되어야 하며 최신 [Gold Standard](../../rn/using/gs-overview.md) 빌드로 업그레이드해야 합니다. [이 섹션](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)에서 자신의 버전을 확인하는 방법을 알아봅니다. 인스턴스가 AWS에서 호스팅되는지 확인하려면 [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)에 설명된 단계를 따르십시오.

**하이브리드** 및 **온-프레미스** 호스팅 모델을 사용하여 관리자는 **serverConf.xml** 파일의 새 **urlPermission**&#x200B;을 참조해야 합니다. **serverConf.xml**&#x200B;에 사용 가능한 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열됩니다.

연결 보호 모드는 다음과 같이 3가지가 있습니다.

* **차단**:에 허용 목록에 추가하다 속하지 않은 모든 URL이 차단되고 오류 메시지가 표시됩니다. 업그레이드 후 기본 모드입니다.
* **자유로운**:에 속하지 않는 모든 허용 목록에 추가하다 URL이 허용됩니다.
* **경고**:에 속하지 않는 모든 URL은 허용 목록에 추가하다 허용되지만 JS 인터프리터는 관리자가 수집할 수 있도록 경고를 전송합니다. 이 모드에서는 JST-310027 경고 메시지가 추가됩니다.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>기본적으로 새 고객의 클라이언트는 **차단 모드**&#x200B;를 사용합니다. 새 URL을 허용해야 하는 경우 관리자에게 문의하여에 추가해야 허용 목록에 추가하다 합니다.
>
>마이그레이션에서 오는 기존 고객은 당분간 **경고 모드**&#x200B;를 사용할 수 있습니다. 동시에 URL을 인증하기 전에 아웃바운드 트래픽을 분석해야 합니다. 인증된 URL 목록이 정의된 후에는 관리자에게 문의하여 URL을에 추가하고 허용 목록에 추가하다 **차단 모드**&#x200B;를 활성화해야 합니다.

## 동적 페이지 보안 및 다시 표시 {#dynamic-page-security-and-relays}

기본적으로 모든 동적 페이지는 웹 모듈이 시작된 컴퓨터의 **local** Tomcat 서버와 자동으로 연결됩니다. 이 구성은 **ServerConf.xml** 파일의 쿼리 릴레이 구성의 **`<url>`** 섹션에 입력됩니다. **serverConf.xml**&#x200B;에 사용 가능한 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열됩니다.

**remote** 서버에서 동적 페이지의 실행을 중계하려면컴퓨터에서 웹 모듈이 활성화되지 않은 경우 이렇게 하려면 **localhost**&#x200B;를 JSP 및 JSSP, 웹 애플리케이션, 보고서 및 문자열에 대한 원격 컴퓨터의 이름으로 바꾸어야 합니다.

사용 가능한 다양한 매개 변수에 대한 자세한 내용은 **serverConf.xml** 구성 파일을 참조하십시오.

JSP 페이지의 기본 구성은 다음과 같습니다.

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign은 다음 JSP 페이지를 사용합니다.

* /nl/jsp/**soaprouter.jsp**:클라이언트 콘솔 및 웹 서비스 연결(SOAP API),
* /nl/jsp/**m.jsp**:페이지,
* /nl/jsp/**logon.jsp**:보고서에 대한 웹 기반 액세스 및 클라이언트 콘솔 배포,
* /nl/jsp/**s.jsp** :바이러스 마케팅(후원 및 소셜 네트워크) 사용

모바일 앱 채널에 사용되는 JSSP는 다음과 같습니다.

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**예제:**

클라이언트 컴퓨터가 외부에서 연결되지 않도록 할 수 있습니다. 이렇게 하려면 **soprouter.jsp**&#x200B;의 실행을 제한하고 미러 페이지, 바이럴 링크, 웹 양식 및 공개 리소스의 실행만 승인합니다.

매개 변수는 다음과 같습니다.

```
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/> 
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="m.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="s.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="webForm.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/webApp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/jssp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/strings/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/interaction/pub*"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/>
```

이 예제에서 **`<IP_addresses>`** 값은 이 마스크에 릴레이 모듈을 사용할 수 있는 IP 주소(쉼표로 구분) 목록과 일치합니다.

>[!NOTE]
>
>특히 특정 구성이 설치용으로 개발된 경우, 구성 및 네트워크 제한에 따라 값이 조정됩니다.

## 허가된 외부 명령 제한 {#restricting-authorized-external-commands}

>[!NOTE]
>
>다음 구성은 온-프레미스 설치에만 필요합니다.

기술 관리자는 빌드 8780에서 Adobe Campaign에서 사용할 수 있는 인증된 외부 명령 목록을 제한할 수 있습니다.

이렇게 하려면 다음과 같이 사용할 수 없게 하려는 명령 목록이 포함된 텍스트 파일을 만들어야 합니다.

```
ln
dd
openssl
curl
wget
python
python3
perl
ruby
sh
```

>[!IMPORTANT]
>
>이 목록은 완전하지 않다.

서버 구성 파일의 **exec** 노드에서 이전에 만든 파일을 **blacklistFile** 특성에서 참조해야 합니다.

**Linux 전용**:서버 구성 파일에서 보안 구성을 강화하기 위해 외부 명령 실행에 전용 사용자를 지정하는 명령을 다시 수행합니다. 이 사용자는 구성 파일의 **exec** 노드에서 설정됩니다. **serverConf.xml**&#x200B;에 사용 가능한 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열됩니다.

>[!NOTE]
>
>사용자를 지정하지 않으면 Adobe Campaign 인스턴스의 사용자 컨텍스트에서 모든 명령이 실행됩니다. 사용자는 Adobe Campaign을 실행하는 사용자와 달라야 합니다.

예제:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

이 사용자를 &#39;Neolane&#39; Adobe Campaign 연산자의 사용자 목록에 추가해야 합니다.

>[!IMPORTANT]
>
>사용자 정의 sudo를 사용하면 안 됩니다. 표준 사용자를 시스템에 설치해야 합니다.

## HTTP 헤더 관리 {#managing-http-headers}

기본적으로 모든 HTTP 헤더는 전달되지 않습니다. 릴레이로 보낸 답글에 특정 헤더를 추가할 수 있습니다. 방법은 다음과 같습니다.

1. **serverConf.xml** 파일로 이동합니다. **serverConf.xml**&#x200B;에 사용 가능한 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열됩니다.
1. **`<relay>`** 노드에서 릴레이된 HTTP 헤더 목록으로 이동합니다.
1. 다음 특성을 사용하여 **`<responseheader>`** 요소를 추가합니다.

   * **이름**:헤더 이름
   * **값**:값 이름.

   예제:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## 중복된 추적 {#redundant-tracking}

리디렉션에 여러 서버를 사용하는 경우 리디렉션할 URL에서 정보를 공유하려면 SOAP 호출을 통해 서로 통신할 수 있어야 합니다. 배달 시작 시 일부 리디렉션 서버를 사용할 수 없을 수 있습니다.따라서 같은 수준의 정보를 가지고 있지 않을 수도 있습니다.

>[!NOTE]
>
>표준 또는 엔터프라이즈 아키텍처를 사용할 때는 각 컴퓨터에서 추적 정보를 업로드할 수 있는 기본 응용 프로그램 서버가 인증되어야 합니다.

중복 서버의 URL은 리디렉션 구성에서 **serverConf.xml** 파일을 통해 지정해야 합니다. **serverConf.xml**&#x200B;에 사용 가능한 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열됩니다.

**예제:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

**enableIf** 속성은 선택 사항이며(기본적으로 비어 있음) 결과가 true인 경우에만 연결을 활성화할 수 있습니다.이렇게 하면 모든 리디렉션 서버에서 동일한 구성을 얻을 수 있습니다.

컴퓨터의 호스트 이름을 얻으려면 다음 명령을 실행하십시오.**hostname -s**.

## 공용 리소스 관리 {#managing-public-resources}

공용 리소스는 [공용 리소스 관리](../../installation/using/deploying-an-instance.md#managing-public-resources)에 제공됩니다.

Adobe Campaign 설치 디렉토리의 **/var/res/instance** 디렉토리에 저장됩니다.

일치하는 URL은 다음과 같습니다.**http://server/res/instance**&#x200B;여기서 **instance**&#x200B;은 추적 인스턴스의 이름입니다.

서버에서 저장소를 구성하기 위해 **conf-`<instance>`.xml** 파일에 노드를 추가하여 다른 디렉토리를 지정할 수 있습니다. 즉, 다음 줄을 추가합니다.

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

이 경우 배포 마법사 창의 위쪽 부분에 있는 공개 리소스에 대한 새 URL은 이 폴더를 가리켜야 합니다.

## 고가용성 워크플로우 및 친화성 {#high-availability-workflows-and-affinities}

여러 워크플로 서버(wfserver)를 구성하고 두 대 이상의 컴퓨터에 배포할 수 있습니다. 이 유형의 아키텍처를 선택하는 경우 Adobe Campaign 액세스에 따라 부하 분산 장치의 연결 모드를 구성합니다.

웹에서 액세스하려면 **부하 균형 조정기** 모드를 선택하여 연결 시간을 제한합니다.

Adobe Campaign 콘솔을 통해 액세스하는 경우 **해시** 또는 **고정 ip** 모드를 선택합니다. 이렇게 하면 리치 클라이언트와 서버 간의 연결을 유지할 수 있으며 가져오기 또는 내보내기 작업 중 사용자 세션이 중단되는 것을 방지할 수 있습니다.

특정 컴퓨터에서 워크플로우 또는 워크플로우 활동을 강제로 실행하도록 선택할 수 있습니다. 이를 수행하려면 관련 워크플로우 또는 활동에 대해 하나 이상의 친화성을 정의해야 합니다.

1. **[!UICONTROL Affinity]** 필드에 워크플로우 또는 활동의 친화성을 입력합니다.

   친화성 이름을 자유롭게 선택할 수 있습니다. 그러나 공백이나 구두점 표시를 사용하지 않도록 해야 합니다. 다른 서버를 사용하는 경우 다른 이름을 지정합니다.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   드롭다운 목록에는 이전에 사용한 친화성이 포함되어 있습니다. 입력한 값이 다른 시간에 따라 완료됩니다.

1. **nl6/conf/config-`<instance>.xml`** 파일을 엽니다.
1. 다음과 같이 **[!UICONTROL wfserver]** 모듈과 일치하는 행을 수정합니다.

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   여러 친화성을 정의하는 경우 공백 없이 쉼표로 구분해야 합니다.

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   친화성이 정의되지 않은 워크플로우를 실행하려면 친화성 이름 뒤에 오는 쉼표가 필요합니다.

   선호도가 정의된 워크플로우만 실행하려면 친화성 목록의 끝에 쉼표를 추가하지 마십시오. 예를 들어 다음과 같이 라인을 수정합니다.

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## 자동 프로세스가 {#automatic-process-restart}을(를) 다시 시작합니다.

기본적으로 서로 다른 Adobe Campaign 프로세스는 매일 오전 6시(서버 시간)에 자동으로 다시 시작됩니다.

하지만 이 구성을 변경할 수 있습니다.

이렇게 하려면 설치의 **conf** 저장소에 있는 **serverConf.xml** 파일로 이동합니다. **serverConf.xml**&#x200B;에 사용 가능한 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열됩니다.

이 파일에 구성된 각 프로세스에는 **processRestartTime** 특성이 있습니다. 이 속성의 값을 수정하여 각 프로세스의 재시작 시간을 필요에 따라 조정할 수 있습니다.

>[!IMPORTANT]
>
>이 특성을 삭제하지 마십시오. 모든 프로세스는 매일 다시 시작해야 합니다.

## 업로드 가능한 파일 제한 {#limiting-uploadable-files}

새 특성 **uploadWhiteList**&#x200B;을 사용하면 Adobe Campaign 서버에서 업로드할 수 있는 파일 유형을 제한할 수 있습니다.

이 속성은 **serverConf.xml** 파일의 **dataStore** 요소 내에서 사용할 수 있습니다. **serverConf.xml**&#x200B;에 사용 가능한 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열됩니다.

이 속성의 기본값은 **입니다.+**&#x200B;을(를) 사용하여 모든 파일 유형을 업로드할 수 있습니다.

가능한 형식을 제한하려면 속성 값을 유효한 java 정규 표현식으로 바꿔야 합니다. 여러 값을 쉼표로 구분하여 입력할 수 있습니다.

예:**uploadWhiteList=&quot;*.png,*.jpg&quot;**&#x200B;에서 PNG 및 JPG 형식을 서버에 업로드할 수 있습니다. 다른 형식은 허용되지 않습니다.

>[!IMPORTANT]
>
>Internet Explorer에서 전체 파일 경로는 정규 표현식으로 확인해야 합니다.

## 프록시 연결 구성 {#proxy-connection-configuration}

예를 들어 **파일 전송** 워크플로우 활동을 사용하여 프록시를 통해 캠페인 서버를 외부 시스템에 연결할 수 있습니다. 이를 수행하려면 특정 명령을 통해 **serverConf.xml** 파일의 **proxyConfig** 섹션을 구성해야 합니다. **serverConf.xml**&#x200B;에 사용 가능한 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열되어 있습니다.

다음 프록시 연결이 가능합니다.HTTP, HTTPS, FTP, SFTP. 20.2 캠페인 릴리스부터 HTTP 및 HTTPS 프로토콜 매개 변수는 **더 이상 사용할 수 없습니다**&#x200B;라는 점에 유의하십시오. 이러한 매개 변수는 9032를 포함하여 이전 빌드에서 사용할 수 있으므로 여전히 아래에 언급됩니다.

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

&#39;http&#39; 및 &#39;https&#39; 옵션은 프로토콜 매개 변수가 &#39;ftp&#39;인 경우에만 사용되며 지정된 포트의 터널링이 HTTPS 또는 HTTP를 통해 수행되는지 여부를 나타냅니다.

프록시 서버를 통한 FTP/SFTP 및 HTTP/HTTPS 트래픽에 대해 다른 포트를 사용하는 경우 &#39;ftp&#39; 프로토콜 매개 변수를 설정해야 합니다.


예제:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

암호를 입력합니다.

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

FTP/FTPS 연결은 proxyFTP 매개 변수에 정의됩니다.

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

여러 연결 유형에 동일한 프록시를 사용하는 경우 useSingleProxy를 &quot;1&quot; 또는 &quot;true&quot;로 설정하여 proxyHTTP만 정의됩니다.

프록시를 통과해야 하는 내부 연결이 있는 경우 override 매개 변수에 추가합니다.

일시적으로 프록시 연결을 비활성화하려면 enabled 매개 변수를 &quot;false&quot; 또는 &quot;0&quot;으로 설정합니다.
