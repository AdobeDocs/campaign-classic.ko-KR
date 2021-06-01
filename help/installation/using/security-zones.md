---
product: campaign
title: 보안 영역 구성
description: 보안 영역을 구성하는 방법 알아보기
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1462'
ht-degree: 1%

---


# 보안 영역 정의(온-프레미스){#defining-security-zones}

각 연산자는 인스턴스에 로그온하기 위해 영역에 연결해야 하며 운영자 IP는 보안 영역에 정의된 주소 또는 주소 세트에 포함해야 합니다. 보안 영역 구성은 Adobe Campaign 서버의 구성 파일에서 수행됩니다.

연산자는 콘솔의 프로필에서 보안 영역에 연결되며 **[!UICONTROL Administration > Access management > Operators]** 노드에서 액세스할 수 있습니다. [자세히 알아보기](#linking-a-security-zone-to-an-operator)

>[!NOTE]
>
>이 절차는 **온-프레미스** 배포로 제한됩니다.
>
>**호스팅된** 고객으로서, [캠페인 Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=ko)에 액세스할 수 있는 경우 보안 영역 셀프 서비스 인터페이스를 사용할 수 있습니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=ko)
>
>다른 **하이브리드/호스팅** 고객은 Adobe 지원 팀에 연락하여 허용 목록에 IP를 추가해야 합니다.


## 보안 영역 만들기 {#creating-security-zones}

영역은 다음과 같이 정의됩니다.

* 하나 이상의 IP 주소 범위(IPv4 및 IPv6)
* 각 IP 주소 범위에 연결된 기술 이름

보안 영역이 상호 잠깁니다. 즉, 다른 영역 내에서 새 영역을 정의하면 각 연산자에 할당된 권한을 증가시키면서 해당 영역에 로그온할 수 있는 운영자 수가 줄어듭니다.

영역은 서버 구성 중에 **serverConf.xml** 파일에서 정의해야 합니다. **serverConf.xml**&#x200B;에서 사용할 수 있는 모든 매개 변수가 [이 섹션](../../installation/using/the-server-configuration-file.md)에 나열되어 있습니다.

각 영역은 다음과 같은 권한을 정의합니다.

* HTTPS가 아닌 HTTP 연결
* 오류 표시(Java 오류, JavaScript, C++ 등)
* 보고서 및 웹 앱 미리 보기
* 로그인/암호를 통한 인증
* 비보안 연결 모드

>[!NOTE]
>
>**각 연산자는 영역에 연결해야 합니다**. 연산자의 IP 주소가 영역에 의해 정의된 범위에 속하면 연산자가 인스턴스에 로그온할 수 있습니다.\
>연산자의 IP 주소는 여러 영역에서 정의할 수 있습니다. 이 경우 연산자는 각 영역에 대해 사용 가능한 권한의 **set**&#x200B;을 수신합니다.

즉시 사용 가능한 **serverConf.xml** 파일에는 다음 세 개의 영역이 포함되어 있습니다.**공용, VPN 및 LAN**

>[!NOTE]
>
>**기본 구성은 안전합니다**. 그러나 이전 버전의 Adobe Campaign에서 마이그레이션하기 전에 새 규칙을 마이그레이션하고 승인하려면 보안을 일시적으로 줄여야 할 수도 있습니다.

**serverConf.xml** 파일에서 영역을 정의하는 방법의 예:

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

* **allowDebug**:webApp을 &quot;debug&quot; 모드로 실행할 수 있도록 설정
* **allowEmptyPassword**:암호 없이 인스턴스에 연결 허용
* **allowHTTP**:HTTPS 프로토콜을 사용하지 않고 세션을 만들 수 있습니다
* **allowUserPassword**:세션 토큰에는 &quot;`<login>/<password>`&quot; 양식이 있을 수 있습니다.
* **sessionTokenOnly**:연결 URL에 보안 토큰이 필요하지 않습니다
* **showErrors**:서버 측 오류가 전달되어 표시됩니다

>[!IMPORTANT]
>
>영역 정의에서 **true** 값이 있는 각 특성은 보안을 줄입니다.

메시지 센터를 사용할 때 실행 인스턴스가 여러 개 있는 경우 **sessionTokenOnly** 특성이 **true**&#x200B;로 정의된 추가 보안 영역을 만들어야 하며, 이때 필요한 IP 주소만 추가해야 합니다. 인스턴스 구성에 대한 자세한 내용은 [이 문서](../../message-center/using/configuring-instances.md)를 참조하십시오.

## 보안 영역에 대한 우수 사례 {#best-practices-for-security-zones}

**lan** 보안 영역의 정의에서 기술 액세스를 정의하는 IP 주소 마스크를 추가할 수 있습니다. 이 추가 기능을 사용하면 서버에서 호스팅되는 모든 인스턴스에 액세스할 수 있습니다.

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

**`config-<instance>.xml`** 파일에서 다음을 수행합니다.

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## 보안 영역 {#sub-networks-and-proxies-in-a-security-zone}의 하위 네트워크 및 프록시

**proxy** 매개 변수는 **subNetwork** 요소에서 사용하여 보안 영역에서 프록시 사용을 지정할 수 있습니다.

프록시가 참조되고 HTTP X-Forwarded-For 헤더를 통해 연결이 이 프록시를 통해 들어오면 확인된 영역이 프록시의 클라이언트(프록시의 클라이언트 아님)입니다.

>[!IMPORTANT]
>
>프록시가 구성되어 있고 재정의할 수 있는 경우(또는 없는 경우), 테스트할 IP 주소를 변경할 수 있습니다.
>
>또한 이제 중계기가 프록시처럼 생성됩니다. 따라서 IP 주소 127.0.0.1을 보안 영역 구성의 프록시 목록에 추가할 수 있습니다.
>
>예제: &quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

다음과 같은 여러 가지 경우가 발생할 수 있습니다.

* 하위 네트워크는 보안 영역에서 직접 참조되며 프록시는 구성되지 않습니다.하위 네트워크 사용자는 Adobe Campaign 서버에 직접 연결할 수 있습니다.

   ![](assets/8101_proxy1.png)

* 보안 영역의 하위 네트워크에 대해 프록시가 지정됩니다.이 하위 네트워크의 사용자는 이 프록시를 통해 Adobe Campaign 서버에 액세스할 수 있습니다.

   ![](assets/8101_proxy2.png)

* 프록시는 보안 영역 하위 네트워크에 포함됩니다.원본에 관계없이 이 프록시를 통해 액세스할 수 있는 사용자는 Adobe Campaign 서버에 액세스할 수 있습니다.

   ![](assets/8101_proxy3.png)

Adobe Campaign 서버에 액세스할 수 있는 프록시의 IP 주소는 해당 **`<subnetwork>`** 및 첫 번째 수준 하위 네트워크 **`<subnetwork name="all"/>`** 모두에 입력해야 합니다. 예를 들어 IP 주소가 10.131.146.102인 프록시의 경우 다음을 수행합니다.

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

영역의 기술 구성은 Campaign Server의 구성 파일에서 수행됩니다.**serverConf.xml**

먼저 **serverConf.xml** 파일에 정의된 영역의 내부 이름에 레이블을 연결하려면 바로 사용 가능한 **[!UICONTROL Security zone]** 열거형을 구성해야 합니다.

이 구성은 Campaign 탐색기에서 수행됩니다.

1. **[!UICONTROL Administration > Platform > Enumerations]** 노드를 클릭합니다.
1. **[!UICONTROL Security zone (securityZone)]** 시스템 열거형을 선택합니다.

   ![](assets/enum_securityzone.png)

1. 서버의 구성 파일에 정의된 각 보안 영역에 대해 **[!UICONTROL Add]** 버튼을 클릭합니다.
1. **[!UICONTROL Internal name]** 필드에 **serverConf.xml** 파일에 정의된 영역의 이름을 입력합니다. 이 값은 `<securityzone>` 요소의 **@name** 속성에 해당합니다. **Label**&#x200B;필드에 내부 이름에 연결된 레이블을 입력합니다.

   ![](assets/enum_addsecurityvalue.png)

1. 확인 을 클릭하고 수정 사항을 저장합니다.

영역이 정의되고 **[!UICONTROL Security zone]** 열거형이 구성되면 각 연산자를 보안 영역에 연결해야 합니다.

1. **[!UICONTROL Administration > Access management > Operators]** 노드를 클릭합니다.
1. 보안 영역을 연결할 연산자를 선택하고 **[!UICONTROL Edit]** 탭을 클릭합니다.
1. **[!UICONTROL Access rights]** 탭으로 이동하여 **[!UICONTROL Edit access parameters...]** 링크를 클릭합니다.

   ![](assets/zone_operator.png)

1. **[!UICONTROL Authorized connection zone]** 드롭다운 목록에서 영역을 선택합니다

   ![](assets/zone_operator_selection.png)

1. **[!UICONTROL OK]** 을 클릭하고 수정 사항을 저장하여 이러한 변경 사항을 적용합니다.



## Recommendations

* 하위 네트워크에서 역방향 프록시가 허용되지 않는지 확인하십시오. 이 경우 **모든** 트래픽이 이 로컬 IP에서 온 것으로 검색되므로 신뢰할 수 있습니다.

* sessionTokenOnly=&quot;true&quot;의 사용을 최소화하십시오.

   * 경고:이 특성이 true로 설정되면 연산자가 **CRSF 공격**&#x200B;에 노출될 수 있습니다.
   * 또한 sessionToken 쿠키가 httpOnly 플래그로 설정되지 않으므로 일부 클라이언트측 javascript 코드는 이를 읽을 수 있습니다.
   * 그러나 여러 실행 셀의 메시지 센터에는 sessionTokenOnly가 필요합니다.sessionTokenOnly가 &quot;true&quot;로 설정된 새 보안 영역을 만들고 이 영역에 필요한 IP만 **추가합니다.**

* 가능하면 모든 allowHTTP, showErrors를 false(localhost가 아님)로 설정하고 확인합니다.

   * allowHTTP = &quot;false&quot;:연산자가 HTTPS를 사용하도록 강제 적용
   * showErrors = &quot;false&quot;:기술 오류(SQL 오류 포함)를 숨깁니다. 이렇게 하면 너무 많은 정보가 표시되지 않지만 마케터가 실수를 해결할 수 있는 기능이 줄어듭니다(관리자의 추가 정보 요청 없이)

* 설문 조사, webApps 및 보고서를 만들어야 하는 마케팅 사용자/관리자가 사용하는 IP에서만 allowDebug를 true로 설정합니다. 이 플래그를 사용하면 이러한 IP가 릴레이 규칙을 표시하고 디버깅할 수 있습니다.

* allowEmptyPassword, allowUserPassword, allowSQLInjection을 true로 설정하지 마십시오. 다음 속성은 v5 및 v6.0에서 원활하게 마이그레이션할 수 있도록 하기 위해서만 해당됩니다.

   * **** allowEmptyPasswordlets 연산자에는 빈 암호가 있습니다. 이러한 경우 모든 운영자에게 마감일이 있는 암호를 설정하도록 요청할 것을 알립니다. 이 기한이 지나면 이 속성을 false로 변경합니다.

   * **** allowUserPasswordlets 연산자는 자격 증명을 매개 변수로 전송하므로 apache/IIS/proxy로 기록됩니다. 이 기능은 이전에는 API 사용을 간소화하는 데 사용되었습니다. Cookbook(또는 사양)에서 일부 타사 애플리케이션에서 이 기능을 사용하는지 확인할 수 있습니다. 그런 경우 API 사용 방법을 변경하고 가능한 한 빨리 이 기능을 제거하도록 알려주어야 합니다.

   * **** allowSQLInjection사용자가 이전 구문을 사용하여 SQL 주입을 수행할 수 있습니다. 이 속성을 false로 설정할 수 있도록 [이 페이지](../../migration/using/general-configurations.md)에 설명된 수정 사항을 가능한 한 빨리 수행합니다. /nl/jsp/ping.jsp?zone=true 를 사용하여 보안 영역 구성을 확인할 수 있습니다. 이 페이지에는 현재 IP에 대한 보안 조치의 활성 상태(이러한 보안 플래그로 계산됨)가 표시됩니다.

* HttpOnly cookie/useSecurityToken:**sessionTokenOnly** 플래그를 참조하십시오.

* 허용 목록에 추가된 IP를 최소화합니다.기본 제공되는 보안 영역에서 개인 네트워크에 대한 3개의 범위를 추가했습니다. 이러한 모든 IP 주소를 사용할 가능성은 없습니다. 필요한 것만 보관하세요

* localhost에서만 액세스할 수 있도록 webApp/internal 연산자를 업데이트합니다.
