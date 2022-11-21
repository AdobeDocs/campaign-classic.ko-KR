---
product: campaign
title: 보안 영역 구성
description: 보안 영역을 구성하는 방법 알아보기
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
source-git-commit: 2594e4943ba24ae65d1fc005da589dc674aa2b0f
workflow-type: tm+mt
source-wordcount: '1464'
ht-degree: 1%

---

# 보안 영역 정의(온-프레미스){#defining-security-zones}

![](../../assets/v7-only.svg)

각 연산자는 인스턴스에 로그온하기 위해 영역에 연결해야 하며 운영자 IP는 보안 영역에 정의된 주소 또는 주소 세트에 포함해야 합니다. 보안 영역 구성은 Adobe Campaign 서버의 구성 파일에서 수행됩니다.

연산자는 콘솔에서 액세스할 수 있는 프로필에서 보안 영역에 연결됩니다 **[!UICONTROL Administration > Access management > Operators]** 노드 아래에 있어야 합니다. [자세히 알아보기](#linking-a-security-zone-to-an-operator)

>[!NOTE]
>
>이 절차는 **온-프레미스** 배포.
>
>로서의 **호스팅** 고객, [캠페인 Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=ko)에서는 보안 영역 셀프 서비스 인터페이스를 사용할 수 있습니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=ko)
>
>기타 **하이브리드/호스팅** 고객은 Adobe 지원 팀에 연락하여에 IP를 추가해야 허용 목록에 추가하다 합니다.

## 보안 영역 만들기 {#creating-security-zones}

영역은 다음과 같이 정의됩니다.

* 하나 이상의 IP 주소 범위(IPv4 및 IPv6)
* 각 IP 주소 범위에 연결된 기술 이름

보안 영역이 상호 잠깁니다. 즉, 다른 영역 내에서 새 영역을 정의하면 각 연산자에 할당된 권한을 증가시키면서 해당 영역에 로그온할 수 있는 운영자 수가 줄어듭니다.

영역은 서버 구성 중에 **serverConf.xml** 파일. 에서 사용할 수 있는 모든 매개 변수 **serverConf.xml** 다음 목록에 나열됩니다. [이 섹션](../../installation/using/the-server-configuration-file.md).

각 영역은 다음과 같은 권한을 정의합니다.

* HTTPS가 아닌 HTTP 연결
* 오류 표시(Java 오류, JavaScript, C++ 등)
* 보고서 및 웹 앱 미리 보기
* 로그인/암호를 통한 인증
* 비보안 연결 모드

>[!NOTE]
>
>**각 연산자는 영역에 연결해야 합니다**. 연산자의 IP 주소가 영역에 의해 정의된 범위에 속하면 연산자가 인스턴스에 로그온할 수 있습니다.\
>연산자의 IP 주소는 여러 영역에서 정의할 수 있습니다. 이 경우 연산자는 **설정** 사용 가능한 각 영역에 대한 권한

즉시 사용 가능한 **serverConf.xml** 파일은 세 개의 영역을 포함합니다. **공용, VPN 및 LAN**.

>[!NOTE]
>
>**기본 구성이 안전합니다**. 그러나 이전 버전의 Adobe Campaign에서 마이그레이션하기 전에 새 규칙을 마이그레이션하고 승인하려면 보안을 일시적으로 줄여야 할 수도 있습니다.

에서 영역을 정의하는 방법의 예 **serverConf.xml** 파일:

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

* **allowDebug**: webApp을 &quot;debug&quot; 모드로 실행할 수 있도록 설정
* **allowEmptyPassword**: 암호 없이 인스턴스에 연결 허용
* **allowHTTP**: HTTPS 프로토콜을 사용하지 않고 세션을 만들 수 있습니다
* **allowUserPassword**: 세션 토큰에는 &quot;`<login>/<password>`&quot;
* **sessionTokenOnly**: 연결 URL에 보안 토큰이 필요하지 않습니다
* **showErrors**: 서버 측 오류가 전달되어 표시됩니다

>[!IMPORTANT]
>
>영역 정의에서 각 속성은 **true** 값을 지정하면 보안이 줄어듭니다.

메시지 센터를 사용할 때 여러 실행 인스턴스가 있는 경우 **sessionTokenOnly** 정의된 속성 **true**- 필요한 IP 주소만 추가해야 합니다. 인스턴스 구성에 대한 자세한 내용은 [이 문서](../../message-center/using/configuring-instances.md).

## 보안 영역에 대한 우수 사례 {#best-practices-for-security-zones}

의 정의에서 **lan** 보안 영역, 기술 액세스를 정의하는 IP 주소 마스크를 추가할 수 있습니다. 이 추가 기능을 사용하면 서버에서 호스팅되는 모든 인스턴스에 액세스할 수 있습니다.

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

특정 인스턴스에만 액세스하는 운영자의 경우 인스턴스 전용 구성 파일에서 직접 IP 주소 범위를 정의하는 것이 좋습니다.

에서 **`config-<instance>.xml`** 파일:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## 보안 영역의 하위 네트워크 및 프록시 {#sub-networks-and-proxies-in-a-security-zone}

다음 **프록시** 매개 변수는 **subNetwork** 보안 영역에서 프록시 사용을 지정할 요소입니다.

프록시가 참조되고 HTTP X-Forwarded-For 헤더를 통해 연결이 이 프록시를 통해 들어오면 확인된 영역이 프록시의 클라이언트(프록시의 클라이언트 아님)입니다.

>[!IMPORTANT]
>
>프록시가 구성되어 있고 재정의할 수 있는 경우(또는 없는 경우), 테스트할 IP 주소를 변경할 수 있습니다.
>
>또한 이제 중계기가 프록시처럼 생성됩니다. 따라서 IP 주소 127.0.0.1을 보안 영역 구성의 프록시 목록에 추가할 수 있습니다.
>
>예제: &quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

다음과 같은 여러 가지 경우가 발생할 수 있습니다.

* 하위 네트워크는 보안 영역에서 직접 참조되며 프록시는 구성되지 않습니다. 하위 네트워크 사용자는 Adobe Campaign 서버에 직접 연결할 수 있습니다.

   ![](assets/8101_proxy1.png)

* 보안 영역의 하위 네트워크에 대해 프록시가 지정됩니다. 이 하위 네트워크의 사용자는 이 프록시를 통해 Adobe Campaign 서버에 액세스할 수 있습니다.

   ![](assets/8101_proxy2.png)

* 프록시는 보안 영역 하위 네트워크에 포함됩니다. 원본에 관계없이 이 프록시를 통해 액세스할 수 있는 사용자는 Adobe Campaign 서버에 액세스할 수 있습니다.

   ![](assets/8101_proxy3.png)

Adobe Campaign 서버에 액세스할 수 있는 프록시의 IP 주소는 **`<subnetwork>`** 관련 및 첫 번째 수준 하위 네트워크 **`<subnetwork name="all"/>`**. 예를 들어 IP 주소가 10.131.146.102인 프록시의 경우 다음을 수행합니다.

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

## 연산자에 보안 영역 연결 {#linking-a-security-zone-to-an-operator}

영역이 정의되면 각 연산자가 하나의 연산자에 연결되어 인스턴스에 로그인할 수 있어야 하며 연산자의 IP 주소가 해당 영역에서 참조되는 주소 또는 주소 범위에 포함되어야 합니다.

영역의 기술 구성은 Campaign Server의 구성 파일에서 수행됩니다. **serverConf.xml**.

먼저 기본 제공 구성을 시작해야 합니다 **[!UICONTROL Security zone]** 열거형을 사용하여 레이블을 **serverConf.xml** 파일.

이 구성은 Campaign 탐색기에서 수행됩니다.

1. 을(를) 클릭합니다. **[!UICONTROL Administration > Platform > Enumerations]** 노드 아래에 있어야 합니다.
1. 을(를) 선택합니다 **[!UICONTROL Security zone (securityZone)]** 시스템 열거형.

   ![](assets/enum_securityzone.png)

1. 서버의 구성 파일에 정의된 각 보안 영역에 대해 **[!UICONTROL Add]** 버튼을 클릭합니다.
1. 에서 **[!UICONTROL Internal name]** 필드에 정의된 영역의 이름을 입력합니다 **serverConf.xml** 파일. 이 변수는 **@name** 의 속성 `<securityzone>`  요소를 생성하지 않습니다. 에서 내부 이름에 연결된 레이블을 입력합니다  **레이블**&#x200B;필드.

   ![](assets/enum_addsecurityvalue.png)

1. 확인 을 클릭하고 수정 사항을 저장합니다.

영역이 정의되고 **[!UICONTROL Security zone]** 열거형이 구성되어 있으면 각 연산자를 보안 영역에 연결해야 합니다.

1. 을(를) 클릭합니다. **[!UICONTROL Administration > Access management > Operators]** 노드 아래에 있어야 합니다.
1. 보안 영역을 연결할 연산자를 선택하고 **[!UICONTROL Edit]** 탭.
1. 로 이동합니다. **[!UICONTROL Access rights]** 탭을 클릭하고 **[!UICONTROL Edit access parameters...]** 링크를 클릭합니다.

   ![](assets/zone_operator.png)

1. 에서 영역 선택 **[!UICONTROL Authorized connection zone]** 드롭다운 목록

   ![](assets/zone_operator_selection.png)

1. 클릭 **[!UICONTROL OK]** 수정 사항을 저장하여 이러한 변경 사항을 적용합니다.



## 권장 사항

* 하위 네트워크에서 역방향 프록시가 허용되지 않는지 확인하십시오. 그렇다면, **모두** 트래픽이 이 로컬 IP에서 오는 것으로 검색되므로 신뢰할 수 있습니다.

* sessionTokenOnly=&quot;true&quot;의 사용을 최소화하십시오.

   * 경고: 이 속성이 true로 설정되면 연산자가 **CRSF 공격**.
   * 또한 sessionToken 쿠키가 httpOnly 플래그로 설정되지 않으므로 일부 클라이언트측 JavaScript 코드는 이를 읽을 수 있습니다.
   * 그러나 여러 실행 셀의 메시지 센터에는 sessionTokenOnly가 필요합니다. sessionTokenOnly를 &quot;true&quot;로 설정하고 추가 **필요한 IP만 해당** 이 영역에 있습니다.

* 가능하면 모든 allowHTTP, showErrors를 false(localhost가 아님)로 설정하고 확인합니다.

   * allowHTTP = &quot;false&quot;: 연산자가 HTTPS를 사용하도록 강제 적용
   * showErrors = &quot;false&quot;: 기술 오류(SQL 오류 포함)를 숨깁니다. 이렇게 하면 너무 많은 정보가 표시되지 않지만 마케터가 실수를 해결할 수 있는 기능이 줄어듭니다(관리자의 추가 정보 요청 없이)

* 설문 조사, webApps 및 보고서를 만들어야 하는 마케팅 사용자/관리자가 사용하는 IP에서만 allowDebug를 true로 설정합니다. 이 플래그를 사용하면 이러한 IP가 릴레이 규칙을 표시하고 디버깅할 수 있습니다.

   * allowDebug가 false로 설정되면 출력은 다음과 같습니다.

      ```
      <redir status='OK' date='...' sourceIP='...'/>
      ```

   * allowDebug가 true로 설정되면 출력은 다음과 같습니다.

      ```
      <redir status='OK' date='...' build='...' OR version='...' sha1='...' instance='...' sourceIP='...' host='...' localHost='...'/>
      ```

* allowEmptyPassword, allowUserPassword, allowSQLInjection을 true로 설정하지 마십시오. 다음 속성은 v5 및 v6.0에서 원활하게 마이그레이션할 수 있도록 하기 위해서만 해당됩니다.

   * **allowEmptyPassword** 연산자에 빈 암호를 지정할 수 있습니다. 이러한 경우 모든 운영자에게 마감일이 있는 암호를 설정하도록 요청할 것을 알립니다. 이 기한이 지나면 이 속성을 false로 변경합니다.

   * **allowUserPassword** 연산자가 자격 증명을 매개 변수로 보낼 수 있도록(apache/IIS/프록시로 기록됨). 이 기능은 이전에는 API 사용을 간소화하는 데 사용되었습니다. Cookbook(또는 사양)에서 일부 타사 애플리케이션에서 이 기능을 사용하는지 확인할 수 있습니다. 그런 경우 API 사용 방법을 변경하고 가능한 한 빨리 이 기능을 제거하도록 알려주어야 합니다.

   * **allowSQLInjection** 이전 구문을 사용하여 SQL 주입을 수행할 수 있습니다. 이 속성은 false로 설정해야 합니다. /nl/jsp/ping.jsp?zone=true 를 사용하여 보안 영역 구성을 확인할 수 있습니다. 이 페이지에는 현재 IP에 대한 보안 조치의 활성 상태(이러한 보안 플래그로 계산됨)가 표시됩니다.

* HttpOnly cookie/useSecurityToken: 참조 **sessionTokenOnly** 플래그.

* 에 추가된 IP를 허용 목록에 추가하다 최소화합니다. 기본 제공되는 보안 영역에서 개인 네트워크에 대한 3개의 범위를 추가했습니다. 이러한 모든 IP 주소를 사용할 가능성은 없습니다. 필요한 것만 보관하세요

* localhost에서만 액세스할 수 있도록 webApp/internal 연산자를 업데이트합니다.
