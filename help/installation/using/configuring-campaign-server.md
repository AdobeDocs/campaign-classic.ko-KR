---
title: 캠페인 서버 구성
seo-title: 캠페인 서버 구성
description: 캠페인 서버 구성
seo-description: null
page-status-flag: never-activated
uuid: be21ae4b-ca2a-4952-b256-cd8dc51309cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 1a94c94e-ab6b-45c2-a0f3-6adeec7e2d2d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1e8492d8e91d679ac13da875974e27d0f7791dc3

---


# 캠페인 서버 구성{#configuring-campaign-server}

아래 섹션에서는 요구 사항 및 환경 사양에 맞게 수행할 수 있는 서버측 구성에 대해 자세히 설명합니다.

이러한 구성은 관리자가 수행해야 하며 **온-프레미스** 호스팅 모델만 수행해야 합니다. 호스팅 **배포의** 경우 서버측 설정은 Adobe에서만 구성할 수 있습니다. 그러나 일부 설정은 제어판(예: IP 허용 목록 또는 URL 권한)에서 설정할 수 있습니다.

자세한 내용은 다음 섹션을 참조하십시오.

* [제어판 설명서](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)
* [호스팅 모델](../../installation/using/hosting-models.md)
* [Campaign Classic 온-프레미스 및 호스팅 기능 매트릭스](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)
* [하이브리드 및 호스팅 모델 구성 단계](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_About_hybrid_and_hosted_models.html)

Campaign Classic 구성 파일은 Adobe Campaign 설치 폴더의 **conf** 폴더에 저장됩니다. 구성은 다음 두 파일에 분산됩니다.

* **serverConf.xml**:일반 구성. 이 파일은 Adobe Campaign 서버의 기술 매개 변수를 결합합니다.모든 인스턴스에서 공유됩니다. 이러한 매개 변수 중 일부에 대한 설명은 아래에 자세히 설명되어 있습니다. 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열된 다른 노드 및 매개 변수입니다.
* **config-`<instance>`.xml** (여기서 **인스턴스는** 인스턴스의 이름입니다):인스턴스의 특정 구성. 여러 인스턴스 간에 서버를 공유하는 경우 관련 파일의 각 인스턴스에 해당하는 매개 변수를 입력하십시오.

## 보안 영역 정의 {#defining-security-zones}

### 보안 영역 정보 {#about-security-zones}

각 연산자를 인스턴스에 로그온하려면 영역에 연결해야 하며 연산자 IP가 보안 영역에 정의된 주소 또는 주소 세트에 포함되어야 합니다. 보안 영역 구성은 Adobe Campaign 서버의 구성 파일에서 수행됩니다.

연산자는 콘솔( **[!UICONTROL Administration > Access management > Operators]** 노드)의 프로필에서 보안 영역에 연결됩니다. 영역을 [이 섹션에서](#linking-a-security-zone-to-an-operator)캠페인 연산자에 연결하는 방법을 알아봅니다.

### 보안 영역 만들기 {#creating-security-zones}

영역은 다음과 같이 정의됩니다.

* 하나 이상의 IP 주소 범위(IPv4 및 IPv6)
* 각 IP 주소 범위에 연결된 기술 이름

보안 영역은 상호 잠겨있으므로 다른 영역 내에서 새 영역을 정의하면 각 연산자에 할당된 권한을 증가시키면서 해당 영역에 로그온할 수 있는 연산자의 수가 줄어듭니다.

서버 구성 중에 serverConf.xml **파일에서 영역을 정의해야** 합니다. serverConf.xml에서 사용할 수 있는 **모든 매개 변수가** 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열됩니다.

각 영역은 다음과 같은 권한을 정의합니다.

* HTTPS가 아닌 HTTP 연결
* 오류 표시(Java 오류, JavaScript, C++ 등)
* 보고서 및 웹 앱 미리 보기
* 로그인/암호를 통한 인증
* 비보안 연결 모드

>[!NOTE]
>
>**각 연산자는 영역에**&#x200B;연결되어 있어야 합니다. 연산자의 IP 주소가 영역에 의해 정의된 범위에 속하는 경우 연산자는 인스턴스에 로그온할 수 있습니다.\
>연산자의 IP 주소는 여러 영역에 정의할 수 있습니다. 이 경우 연산자는 각 영역에 대해 사용 가능한 권한 **세트를** 받습니다.

곧바로 사용 가능한 serverConf. **xml** 파일에는 다음 세 개의 영역이 포함되어 있습니다.공개, **VPN 및 LAN**.

>[!NOTE]
>
>**기본 구성은 안전합니다**. 그러나 이전 버전의 Adobe Campaign에서 마이그레이션하기 전에 새 규칙을 마이그레이션하고 승인하려면 일시적으로 보안을 줄여야 할 수 있습니다.

serverConf.xml 파일에서 영역을 정의하는 **방법의 예** :

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" name="public">
<subNetwork label="All addresses" mask="*" name="all"/>

<securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)"
              name="vpn" showErrors="true">

  <securityZone allowDebug="true" allowEmptyPassword="true" allowHTTP="true"
                allowUserPassword="false" label="Private Network (LAN)" name="lan"
                sessionTokenOnly="true" showErrors="true">
    <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
    <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
    <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
    <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
    <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
    <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  </securityZone>

</securityZone>
</securityZone>
```

영역을 정의하는 모든 권한은 다음과 같습니다.

* **allowDebug**:webApp을 &quot;디버그&quot; 모드로 실행할 수 있도록 합니다.
* **allowEmptyPassword**:암호 없이 인스턴스에 대한 연결 권한 부여
* **allowHTTP**:HTTPS 프로토콜을 사용하지 않고 세션을 만들 수 있습니다.
* **allowUserPassword**:세션 토큰에는 &quot;`<login>/<password>`&quot; 양식이 있을 수 있습니다.
* **sessionTokenOnly**:연결 URL에 보안 토큰이 필요하지 않습니다.
* **showErrors**:서버측의 오류가 전달되어 표시됩니다.

>[!CAUTION]
>
>영역 정의에서 **true** 값이 있는 각 속성은 보안을 감소시킵니다.

메시지 센터를 사용할 때, 실행 인스턴스가 여러 개 있을 경우 **true로** 정의된 sessionTokenOnly ****&#x200B;속성을 사용하여 추가 보안 영역을 만들어야 합니다. 여기서 필요한 IP 주소만 추가해야 합니다. 인스턴스 구성에 대한 자세한 내용은 [이 문서를](../../message-center/using/creating-a-shared-connection.md)참조하십시오.

### 보안 영역에 대한 우수 사례 {#best-practices-for-security-zones}

LAN **보안 영역의** 정의에서 기술 액세스를 정의하는 IP 주소 마스크를 추가할 수 있습니다. 이렇게 추가하면 서버에 호스팅된 모든 인스턴스에 액세스할 수 있습니다.

```
<securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true"
                    allowUserPassword="false" label="Private Network (LAN)" name="lan"
                    sessionTokenOnly="true" showErrors="true">
        <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
        <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
        <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
        <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
        <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
        <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  
        <!-- Customer internal IPs -->
        <subNetwork id="internalNetwork" mask="a.b.c.d/xx"/>

      </securityZone>
```

특정 인스턴스에만 액세스하는 연산자에 대해 인스턴스에 전용 구성 파일에서 직접 IP 주소 범위를 정의하는 것이 좋습니다.

파일에서 **`config-<instance>.xml`** 다음을 수행합니다.

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

### 보안 영역의 하위 네트워크 및 프록시 {#sub-networks-and-proxies-in-a-security-zone}

프록시 **매개 변수는** subNetwork **** 요소에서 보안 영역에서 프록시 사용을 지정할 수 있습니다.

프록시가 참조되고 이 프록시를 통해 연결이 들어오는 경우(HTTP X-Forwarded-For 헤더를 통해 표시됨) 확인된 영역은 프록시의 클라이언트가 아니라 프록시 클라이언트의 영역입니다.

>[!CAUTION]
>
>프록시가 구성되어 있고 재정의할 수 있는 경우(또는 존재하지 않는 경우), 테스트할 IP 주소는 위조될 수 있습니다.
>
>또한 이제 레이가 프록시처럼 생성됩니다. 따라서 보안 영역 구성의 프록시 목록에 IP 주소 127.0.0.1을 추가할 수 있습니다.
>
>예:&quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

다음과 같은 여러 가지 경우가 발생할 수 있습니다.

* 하위 네트워크는 보안 영역에서 직접 참조되며 프록시가 구성되지 않았습니다.하위 네트워크 사용자는 Adobe Campaign 서버에 직접 연결할 수 있습니다.

   ![](assets/8101_proxy1.png)

* 보안 영역의 하위 네트워크에 대해 프록시가 지정되었습니다.이 하위 네트워크의 사용자는 이 프록시를 통해 Adobe Campaign 서버에 액세스할 수 있습니다.

   ![](assets/8101_proxy2.png)

* 프록시는 보안 영역 하위 네트워크에 포함됩니다.이 프록시를 통해 액세스하는 사용자는 원본에 관계없이 Adobe Campaign 서버에 액세스할 수 있습니다.

   ![](assets/8101_proxy3.png)

Adobe Campaign 서버에 액세스할 수 있는 프록시의 IP 주소는 **`<subnetwork>`** 관련 및 첫 번째 수준 하위 네트워크에 모두 입력해야 합니다 **`<subnetwork name="all"/>`**. 예를 들어 IP 주소가 10.131.146.102인 프록시는 다음과 같습니다.

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" 
                      name="public">
    <subNetwork label="All addresses" mask="*" name="all"
                      proxy="10.131.146.102,127.0.0.1, ::1"/>

    <securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)" 
                      name="vpn" showErrors="true">
        <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" 
                      allowUserPassword="false" label="Private Network (LAN)" 
                      name="lan" sessionTokenOnly="true" showErrors="true">
            <subNetwork label="Lan proxy" mask="10.131.193.182" name="lan3" 
                      proxy="10.131.146.102,127.0.0.1, ::1"/>
            <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" 
                      proxy="127.0.0.1, ::1"/>

        </securityZone>
    </securityZone>
</securityZone>
```

### 연산자에 보안 영역 연결 {#linking-a-security-zone-to-an-operator}

영역이 정의되면 각 연산자는 인스턴스에 로그온할 수 있도록 각 연산자 중 하나에 연결되어 있어야 하며 연산자의 IP 주소는 영역에서 참조하는 주소 또는 주소 범위에 포함되어야 합니다.

영역의 기술 구성은 캠페인 서버의 구성 파일에서 수행됩니다.server **Conf.xml**.

그 전에 serverConf.xml 파일에 정의된 영역의 내부 이름에 레이블을 연결하도록 기본 **[!UICONTROL Security zone]** 열거 **기능을 구성해야** 합니다.

이 구성은 캠페인 탐색기에서 수행됩니다.

1. 노드를 **[!UICONTROL Administration > Platform > Enumerations]** 클릭합니다.
1. 시스템 열거형을 **[!UICONTROL Security zone (securityZone)]** 선택합니다.

   ![](assets/enum_securityzone.png)

1. 서버의 구성 파일에 정의된 각 보안 영역에 대해 **[!UICONTROL Add]** 단추를 클릭합니다.
1. 필드에 serverConf.xml 파일에 정의된 영역의 이름을 **[!UICONTROL Internal name]** 입력합니다 **** . 요소의 **@name** 특성에 해당합니다 `<securityzone>` . 레이블 필드에 내부 이름에 연결된 레이블을 ****&#x200B;입력합니다.

   ![](assets/enum_addsecurityvalue.png)

1. 확인을 클릭하고 수정 내용을 저장합니다.

영역이 정의되고 **[!UICONTROL Security zone]** 열거형이 구성되면 각 연산자를 보안 영역에 연결해야 합니다.

1. 노드를 **[!UICONTROL Administration > Access management > Operators]** 클릭합니다.
1. 보안 영역을 연결할 연산자를 선택하고 **[!UICONTROL Edit]** 탭을 클릭합니다.
1. 탭으로 이동한 후 **[!UICONTROL Access rights]** **[!UICONTROL Edit access parameters...]** 링크를 클릭합니다.

   ![](assets/zone_operator.png)

1. 드롭다운 목록에서 **[!UICONTROL Authorized connection zone]** 영역 선택

   ![](assets/zone_operator_selection.png)

1. 수정 내용을 **[!UICONTROL OK]** 클릭하고 저장하여 변경 내용을 적용합니다.

## Tomcat 구성 {#configuring-tomcat}

### Tomcat의 기본 포트 {#default-port-for-tomcat}

Tomcat 서버의 8080 의견 수렴 포트가 구성에 필요한 다른 애플리케이션으로 이미 사용 중인 경우 8080 포트를 무료 포트(예: 8090)로 교체해야 합니다. 변경하려면 Adobe Campaign 설치 폴더의 **/tomcat-7/conf** 디렉토리에 저장된 **server.xml** 파일을 편집합니다.

그런 다음 JSP 릴레이 페이지의 포트를 수정합니다. 이렇게 하려면 Adobe **Campaign 설치 디렉토리의** /conf **디렉토리에 저장된 serverConf.xml** 파일을 변경합니다. serverConf.xml에서 사용할 수 있는 **모든 매개 변수가** 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열됩니다.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

### Tomcat에서 폴더 매핑 {#mapping-a-folder-in-tomcat}

고객별 설정을 정의하려면 **/tomcat-7/conf** 폴더에 **context.xml** 파일도 **포함하는 user_contexts.xml** 파일을 만들 수 있습니다.

이 파일에는 다음 유형의 정보가 포함됩니다.

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

필요한 경우 이 작업을 서버측에서 재현할 수 있습니다.

## 전달 매개 변수 개인화 {#personalizing-delivery-parameters}

전달 매개 변수는 serverConf. **xml** 구성 파일에 정의됩니다. serverConf.xml에서 사용할 수 있는 **모든 매개 변수가** 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열됩니다.

일반 서버 구성 및 명령은 Campaign [서버 구성에](../../installation/using/campaign-server-configuration.md)자세히 설명되어 있습니다.

사용자의 요구 사항과 설정에 따라 다음 구성을 수행할 수도 있습니다.

### SMTP 릴레이 {#smtp-relay}

MTA 모듈은 SMTP 브로드캐스트(포트 25)에 대한 기본 메일 전송 에이전트 역할을 합니다.

그러나 보안 정책에 필요한 경우 릴레이 서버로 바꿀 수 있습니다. 이 경우, 글로벌 처리량은 릴레이 하나가 됩니다(릴레이 서버 처리량이 Adobe Campaign 1보다 낮다고 가정).

이 경우 이러한 매개 변수는 **`<relay>`** 섹션에서 SMTP 서버를 구성하여 설정됩니다. 메일을 전송하는 데 사용되는 SMTP 서버의 IP 주소 또는 호스트(기본적으로 25개)를 지정해야 합니다.

```
<relay address="192.0.0.3" port="25"/>
```

>[!CAUTION]
>
>이 운영 모드는 릴레이 서버 내부 성능(지연, 대역폭...)으로 인해 처리량을 크게 줄일 수 있으므로 배달 시 심각한 제한 사항을 의미합니다. 또한 SMTP 트래픽을 분석하여 감지된 동기 배달 오류를 평가할 수 있는 용량은 제한되며 릴레이 서버를 사용할 수 없을 경우 전송을 수행할 수 없습니다.

### MTA 하위 프로세스 {#mta-child-processes}

서버의 CPU 성능 및 사용 가능한 네트워크 리소스에 따라 브로드캐스트 성능을 최적화하기 위해 하위 프로세스(기본적으로 maxSpareServers)의 모집단을 제어할 수 있습니다. 이 구성은 각 개별 컴퓨터의 MTA 구성 **`<master>`** 섹션에서 이루어집니다.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

이메일 [보내기 최적화를](../../installation/using/email-deliverability.md#email-sending-optimization)참조하십시오.

### 친화성이 있는 아웃바운드 SMTP 트래픽 관리 {#managing-outbound-smtp-traffic-with-affinities}

>[!CAUTION]
>
>친화성 구성은 한 서버에서 다른 서버로 일관되어야 합니다. MTA를 실행하는 모든 애플리케이션 서버에서 구성 변경 사항을 복제해야 하므로 선호도 구성을 위해 Adobe에 문의하는 것이 좋습니다.

IP 주소가 있는 친화성을 통해 아웃바운드 SMTP 트래픽을 개선할 수 있습니다.

이렇게 하려면 다음 단계를 적용합니다.

1. serverConf.xml 파일의 **`<ipaffinity>`** 섹션에 **해당 기능을 입력합니다** .

   **선호도 하나에는 여러 개의 이름이 있을 수 있습니다.구분하려면**;문자.

   예:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   관련 매개변수를 보려면 serverConf.xml **파일을** 참조하십시오.

1. 드롭다운 목록에서 친화성 선택을 활성화하려면 IPAfferity 열거형에 친화성 이름을 **추가해야** 합니다.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >열거형은 [이 문서에](../../platform/using/managing-enumerations.md)자세히 설명되어 있습니다.

   그런 다음 유형 분류에 대해 아래에 표시된 것처럼 사용할 친화성을 선택할 수 있습니다.

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >배달 서버 구성을 [참조할](../../installation/using/email-deliverability.md#delivery-server-configuration)수도 있습니다.

## URL 권한 {#url-permissions}

JavaScript 코드(워크플로우 등)에서 호출할 수 있는 URL의 기본 목록 캠페인 클래식 인스턴스는 제한됩니다. 이러한 URL은 인스턴스가 제대로 작동하도록 하는 URL입니다.

기본적으로 인스턴스는 외부 URL에 연결할 수 없습니다. 하지만, 인스턴스가 URL에 연결할 수 있도록 외부 URL을 인증된 URL 목록에 추가할 수 있습니다. 이렇게 하면 파일 및/또는 데이터 전송을 활성화하기 위해 SFTP 서버나 웹 사이트와 같은 외부 시스템에 Campaign 인스턴스를 연결할 수 있습니다.

URL이 추가되면 인스턴스의 구성 파일(serverConf.xml)에서 참조됩니다.

URL 권한을 관리하는 방법은 호스팅 모델에 따라 다릅니다.

* **하이브리드** 또는 **온-프레미스**:serverConf.xml 파일에 ****&#x200B;허용하도록 URL을 추가합니다. 자세한 내용은 아래 섹션에 나와 있습니다.
* **호스팅**:제어판을 통해 허용할 URL을 **추가합니다**. 자세한 내용은 [전용 설명서를](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/url-permissions.html)참조하십시오.

Hybrid **및** On-premise **호스팅** 모델을 사용하는 관리자는 ServerConf **.xml** 파일의 새 **** url Permission을 참조해야 합니다. serverConf.xml에서 사용할 수 있는 **모든 매개 변수가** 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열됩니다.

연결 보호 모드는 다음과 같습니다.

* **차단**:허용 목록에 속하지 않은 모든 URL이 차단되고 오류 메시지가 표시됩니다. 업그레이드 후 기본 모드입니다.
* **자유로운**:허용 목록에 속하지 않은 모든 URL이 허용됩니다.
* **경고**:흰색이 아닌 모든 URL은 허용되지만 JS 인터프리터는 관리자가 수집할 수 있도록 경고를 전송합니다. 이 모드에서는 JST-310027 경고 메시지가 추가됩니다.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!CAUTION]
>
>기본적으로 새 고객의 클라이언트는 **차단 모드를**&#x200B;사용합니다. 새로운 URL을 허용해야 하는 경우 관리자에게 연락하여 허용 목록에 추가해야 합니다.
>
>마이그레이션에서 오는 기존 고객은 잠시 동안 **경고 모드를** 사용할 수 있습니다. 동시에 URL을 인증하기 전에 아웃바운드 트래픽을 분석해야 합니다. 인증된 URL 목록이 정의된 후에는 관리자에게 문의하여 URL을 허용 목록에 표시하고 **차단 모드를**&#x200B;활성화해야 합니다.

## 동적 페이지 보안 및 릴리스 {#dynamic-page-security-and-relays}

기본적으로 모든 동적 페이지는 웹 모듈이 시작된 컴퓨터의 **로컬** Tomcat 서버와 자동으로 연결됩니다. 이 구성은 ServerConf.xml 파일에 대한 쿼리 릴레이 구성 **`<url>`** 섹션에 **입력됩니다** . serverConf.xml에서 사용할 수 있는 **모든 매개 변수가** 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열됩니다.

**원격** 서버에서 동적 페이지 실행을 릴레이 실행하려면웹 모듈이 컴퓨터에서 활성화되지 않은 경우 이렇게 하려면 **localhost를** JSP 및 JSSP, 웹 애플리케이션, 보고서 및 문자열에 대한 원격 컴퓨터의 이름으로 교체해야 합니다.

사용 가능한 다양한 매개 변수에 대한 자세한 내용은 serverConf. **xml** 구성 파일을 참조하십시오.

JSP 페이지의 경우 기본 구성은 다음과 같습니다.

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign은 다음 JSP 페이지를 사용합니다.

* /nl/jsp/**soaprouter.jsp**:클라이언트 콘솔 및 웹 서비스 연결(SOAP API),
* /nl/jsp/**m.jsp**:미러 페이지,
* /nl/jsp/**logon.jsp**:보고서 및 클라이언트 콘솔의 배포에 대한 웹 기반 액세스,
* /nl/jsp/**s.jsp** :바이럴 마케팅(후원 및 소셜 네트워크) 사용

모바일 앱 채널에 사용되는 JSSP는 다음과 같습니다.

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**예:**

클라이언트 컴퓨터가 외부에 연결되지 않도록 할 수 있습니다. 이렇게 하려면 Computer.jsp **의** 실행을 제한하고 미러 페이지, 바이럴 링크, 웹 양식 및 공개 리소스의 실행만 승인합니다.

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

이 예에서 이 **`<IP_addresses>`** 값은 이 마스크에 릴레이 모듈을 사용할 수 있도록 허가된 IP 주소 목록(쉼표로 구분)과 일치합니다.

>[!NOTE]
>
>값은 사용자의 구성 및 네트워크 제약 조건에 따라 조정되며, 특히 특정 구성이 설치용으로 개발된 경우 그러합니다.

## 허가된 외부 명령 제한 {#restricting-authorized-external-commands}

>[!NOTE]
>
>다음 구성은 온-프레미스 설치에만 필요합니다.

빌드 8780에서 기술 관리자는 Adobe Campaign에서 사용할 수 있는 인증된 외부 명령 목록을 제한할 수 있습니다.

이렇게 하려면 다음 등과 같이 사용할 수 없게 하려는 명령 목록이 포함된 텍스트 파일을 만들어야 합니다.

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

>[!CAUTION]
>
>이 목록은 완전하지 않습니다.

서버 구성 파일의 **exec** 노드에서 이전에 만든 파일을 **blacklistFile 속성에 참조해야** 합니다.

**Linux 전용**:서버 구성 파일에서 보안 구성을 개선하기 위해 외부 명령 실행에 전용 사용자를 지정하는 명령을 다시 수행합니다. 이 사용자는 구성 파일의 **실행** 노드에 설정됩니다. serverConf.xml에서 사용할 수 있는 **모든 매개 변수가** 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열됩니다.

>[!NOTE]
>
>사용자를 지정하지 않으면 모든 명령이 Adobe Campaign 인스턴스의 사용자 컨텍스트에서 실행됩니다. 사용자는 Adobe Campaign을 실행하는 사용자와 달라야 합니다.

예:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

이 사용자를 &#39;Neolane&#39; Adobe Campaign 연산자의 사용자 목록에 추가해야 합니다.

>[!CAUTION]
>
>사용자 정의 sudo를 사용하면 안 됩니다. 시스템에 표준 소프트웨어를 설치해야 합니다.

## HTTP 헤더 관리 {#managing-http-headers}

기본적으로 모든 HTTP 헤더는 전달되지 않습니다. 릴레이로 보낸 답글에 특정 헤더를 추가할 수 있습니다. 이렇게 하려면:

1. serverConf. **xml** 파일로 이동합니다. serverConf.xml에서 사용할 수 있는 **모든 매개 변수가** 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열됩니다.
1. 노드에서 **`<relay>`** 릴레이된 HTTP 헤더 목록으로 이동합니다.
1. 다음 속성을 사용하여 **`<responseheader>`** 요소를 추가합니다.

   * **이름**:헤더 이름
   * **값**:값 이름.
   예:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## 중복 추적 {#redundant-tracking}

리디렉션에 여러 서버를 사용하는 경우 리디렉션할 URL의 정보를 공유하려면 SOAP 호출을 통해 서로 통신할 수 있어야 합니다. 배달 시작 시 모든 리디렉션 서버를 사용할 수 없을 수 있습니다.따라서 그들은 같은 수준의 정보를 가지고 있지 않을 수도 있습니다.

>[!NOTE]
>
>표준 또는 엔터프라이즈 아키텍처를 사용할 때는 각 컴퓨터에서 추적 정보를 업로드할 수 있는 주 응용 프로그램 서버가 인증되어야 합니다.

중복 서버의 URL은 serverConf.xml 파일을 통해 리디렉션 구성에서 **지정해야** 합니다. serverConf.xml에서 사용할 수 있는 **모든 매개 변수가** 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열됩니다.

**예:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

enable **If** 속성은 선택 사항이며(기본적으로 비어 있음) 결과가 참인 경우에만 연결을 활성화할 수 있습니다.이렇게 하면 모든 리디렉션 서버에서 동일한 구성을 얻을 수 있습니다.

컴퓨터의 호스트 이름을 얻으려면 다음 명령을 실행합니다. **hostname -s**.

## 공공 자원 관리 {#managing-public-resources}

공공자원은 [공공자원](../../installation/using/deploying-an-instance.md#managing-public-resources)관리에 제시된다.

Adobe Campaign 설치 디렉토리의 **/var/res/instance** 디렉토리에 저장됩니다.

일치하는 URL은 다음과 같습니다.http://server/res/instance **** where **instance** is the name of the tracking instance.

노드를 **conf-`<instance>`.xml** 파일에 추가하여 서버의 스토리지를 구성하여 다른 디렉토리를 지정할 수 있습니다. 즉, 다음 줄을 추가합니다.

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

여러 워크플로 서버(wfserver)를 구성하고 두 개 이상의 컴퓨터에 배포할 수 있습니다. 이 유형의 아키텍처를 선택하는 경우 Adobe Campaign 액세스에 따라 로드 밸런서의 연결 모드를 구성합니다.

웹에서 액세스하려면 **로드 밸런서** 모드를 선택하여 연결 시간을 제한합니다.

Adobe Campaign 콘솔을 통해 액세스하는 경우 **해시** 또는 **고정 ip** 모드를 선택합니다. 이렇게 하면 리치 클라이언트와 서버 간의 연결을 유지할 수 있으며 가져오기 또는 내보내기 작업 중에 사용자 세션이 중단되는 것을 방지할 수 있습니다.

특정 컴퓨터에서 워크플로우 또는 워크플로우 활동을 강제로 실행하도록 선택할 수 있습니다. 이렇게 하려면 관련 워크플로우 또는 활동에 대해 하나 이상의 친화성을 정의해야 합니다.

1. 필드에 워크플로우 또는 활동을 입력하여 해당 활동의 친화성을 **[!UICONTROL Affinity]** 만듭니다.

   친화성 이름을 자유롭게 선택할 수 있습니다. 그러나 공백이나 구두점 표시는 사용하지 않도록 하십시오. 다른 서버를 사용하는 경우 다른 이름을 지정합니다.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   드롭다운 목록에는 이전에 사용한 친화성이 포함되어 있습니다. 입력한 값이 다른 시간에 따라 완료됩니다.

1. nl6/ **conf/config-`<instance>.xml`**파일을 엽니다.
1. 다음과 같이 **[!UICONTROL wfserver]** 모듈과 일치하는 라인을 수정합니다.

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   여러 가지 친화성을 정의하는 경우 공백 없이 쉼표로 구분해야 합니다.

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   친화성이 정의되지 않은 워크플로우를 실행하려면 친화성 이름 다음에 쉼표가 필요합니다.

   선호도가 정의된 워크플로우만 실행하려면 친화성 목록의 끝에 쉼표를 추가하지 마십시오. 예를 들어 다음과 같이 라인을 수정합니다.

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## 자동 프로세스 다시 시작 {#automatic-process-restart}

기본적으로 다른 Adobe Campaign 프로세스는 매일 오전 6시(서버 시간)에 자동으로 다시 시작됩니다.

하지만 이 구성을 변경할 수 있습니다.

이렇게 하려면 **설치의 conf** 보관소에 있는 serverConf.xml **** 파일로 이동합니다. serverConf.xml에서 사용할 수 있는 **모든 매개 변수가** 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열됩니다.

이 파일에 구성된 각 프로세스에는 processRestartTime **특성이** 있습니다. 이 속성의 값을 수정하여 각 프로세스의 재시작 시간을 필요에 따라 조정할 수 있습니다.

>[!CAUTION]
>
>이 속성을 삭제하지 마십시오. 모든 프로세스는 매일 다시 시작해야 합니다.

## 업로드 가능한 파일 제한 {#limiting-uploadable-files}

새 속성 **uploadWhiteList를** 사용하면 Adobe Campaign 서버에서 업로드할 수 있는 파일 유형을 제한할 수 있습니다.

이 속성은 serverConf. **xml** 파일의 dataStore 요소 내에서 사용할 **수** 있습니다. serverConf.xml에서 사용할 수 있는 **모든 매개 변수가** 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열됩니다.

이 속성의 기본값은 **입니다.+** 모든 파일 유형을 업로드할 수 있습니다.

가능한 형식을 제한하려면 속성 값을 유효한 java 정규 표현식으로 바꿔야 합니다. 여러 값을 쉼표로 구분하여 입력할 수 있습니다.

예: **uploadWhiteList=&quot;*.png,*.jpg&quot;** 를 사용하면 서버에서 PNG 및 JPG 형식을 업로드할 수 있습니다. 다른 포맷은 허용되지 않습니다.

>[!CAUTION]
>
>Internet Explorer에서는 전체 파일 경로를 정규 표현식으로 확인해야 합니다.

## 프록시 연결 구성 {#proxy-connection-configuration}

예를 들어 파일 전송 워크플로우 활동을 사용하여 프록시를 통해 Campaign 서버를 외부에 연결해야 하는 경우 명령을 통해 serverConf의 proxyConfig 섹션을 구성해야 합니다. 다음과 같은 프록시 연결이 가능합니다.HTTP, HTTPS, FTP, SFTP. serverConf.xml에서 사용할 수 있는 **모든 매개 변수가** 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열됩니다.

>[!NOTE]
>
>SOCKS 프록시는 지원되지 않습니다.

다음 명령을 사용합니다.

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


예:

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

여러 연결 유형에 대해 동일한 프록시를 사용하는 경우 useSingleProxy를 &quot;1&quot; 또는 &quot;true&quot;로 설정하여 proxyHTTP만 정의됩니다.

프록시를 통과해야 하는 내부 연결이 있는 경우 override 매개 변수에 추가합니다.

일시적으로 프록시 연결을 비활성화하려면 활성화된 매개 변수를 &quot;false&quot; 또는 &quot;0&quot;으로 설정합니다.
