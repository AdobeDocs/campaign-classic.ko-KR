---
product: campaign
title: 보안 영역 구성
description: 보안 영역 구성 방법 알아보기
feature: Installation, Instance Settings
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '1452'
ht-degree: 0%

---

# 보안 영역 정의(온-프레미스){#defining-security-zones}



각 연산자는 영역에 연결되어 인스턴스에 로그온해야 하며 연산자 IP는 보안 영역에 정의된 주소 또는 주소 집합에 포함되어야 합니다. 보안 영역 구성은 Adobe Campaign 서버의 구성 파일에서 수행됩니다.

연산자가 콘솔의 프로필에서 보안 영역에 연결되어 **[!UICONTROL Administration > Access management > Operators]** 노드에서 액세스할 수 있습니다. [자세히 알아보기](#linking-a-security-zone-to-an-operator).

>[!NOTE]
>
>이 프로시저는 **온-프레미스** 배포로 제한됩니다.
>
>**호스팅** 고객의 경우 [캠페인 Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=ko)에 액세스할 수 있으면 보안 영역 셀프 서비스 인터페이스를 사용할 수 있습니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=ko)
>
>다른 **하이브리드/호스팅** 고객은 Adobe 지원 팀에 연락하여 허용 목록에 추가하다에 IP를 추가해야 합니다.
>

## 보안 영역 만들기 {#creating-security-zones}

영역은 다음 방법으로 정의됩니다.

* 하나 이상의 IP 주소 범위(IPv4 및 IPv6)
* 각 IP 주소 범위와 연관된 기술 이름

보안 영역이 연동되는데, 다른 영역 내에 새 영역을 정의하면 각 운영자에게 부여되는 권한을 늘리면서 해당 영역에 로그인할 수 있는 운영자 수를 줄인다는 의미다.

**serverConf.xml** 파일에서 서버 구성 중에 영역을 정의해야 합니다. **serverConf.xml**&#x200B;에서 사용할 수 있는 모든 매개 변수가 [이 섹션](../../installation/using/the-server-configuration-file.md)에 나열되어 있습니다.

각 영역은 다음과 같은 권한을 정의합니다.

* HTTPS가 아닌 HTTP 연결
* 오류 표시(Java 오류, JavaScript, C++ 등)
* 보고서 및 웹 앱 미리 보기
* 로그인/암호를 통한 인증
* 비보안 연결 모드

>[!NOTE]
>
>**각 연산자는 영역에 연결되어 있어야 합니다**. 연산자의 IP 주소가 영역에 의해 정의된 범위에 속하는 경우 연산자는 인스턴스에 로그온할 수 있습니다.\
>운영자의 IP 주소는 여러 영역에 정의될 수 있다. 이 경우 연산자는 각 영역에 대해 사용 가능한 권한의 **set**&#x200B;을(를) 받습니다.

기본 제공 **serverConf.xml** 파일에는 **public, VPN 및 LAN**&#x200B;의 세 영역이 포함되어 있습니다.

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

* **allowDebug**: 웹 앱을 &quot;debug&quot; 모드에서 실행할 수 있도록 합니다.
* **allowEmptyPassword**: 암호 없이 인스턴스에 대한 연결을 허용합니다
* **allowHTTP**: HTTPS 프로토콜을 사용하지 않고 세션을 만들 수 있습니다.
* **allowUserPassword**: 세션 토큰에는 &quot;`<login>/<password>`&quot; 양식이 있을 수 있습니다.
* **sessionTokenOnly**: 연결 URL에 보안 토큰이 필요하지 않습니다.
* **showErrors**: 서버측 오류가 전달되고 표시됩니다.

>[!IMPORTANT]
>
>영역 정의에서 **true** 값이 있는 각 특성은 보안을 낮춥니다.

메시지 센터를 사용할 때 실행 인스턴스가 여러 개 있는 경우 **true**(으)로 정의된 **sessionTokenOnly** 특성을 사용하여 추가 보안 영역을 만들어야 합니다. 여기서 필요한 IP 주소만 추가됩니다. 인스턴스 구성에 대한 자세한 내용은 [이 문서](../../message-center/using/configuring-instances.md)를 참조하세요.

## 보안 영역에 대한 우수 사례 {#best-practices-for-security-zones}

**lan** 보안 영역의 정의에서 기술 액세스를 정의하는 IP 주소 마스크를 추가할 수 있습니다. 이 추가를 통해 서버에서 호스팅된 모든 인스턴스에 액세스할 수 있습니다.

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

특정 인스턴스에만 액세스하는 운영자를 위해 인스턴스 전용 구성 파일에서 직접 IP 주소 범위를 정의하는 것이 좋습니다.

**`config-<instance>.xml`** 파일에서:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## 보안 영역의 하위 네트워크 및 프록시 {#sub-networks-and-proxies-in-a-security-zone}

**subNetwork** 요소에서 **proxy** 매개 변수를 사용하여 보안 영역에서 프록시 사용을 지정할 수 있습니다.

프록시가 참조되고 이 프록시(HTTP X-Forwarded-For 헤더를 통해 볼 수 있음)를 통해 연결이 들어갈 때 확인된 영역은 프록시의 클라이언트가 아니라 클라이언트의 영역입니다.

>[!IMPORTANT]
>
>프록시가 구성되어 있고 이를 재정의할 수 있는 경우(또는 존재하지 않는 경우) 테스트할 IP 주소를 수정할 수 있습니다.
>
>또한 이제 릴레이가 프록시처럼 생성됩니다. 따라서 보안 영역 구성의 프록시 목록에 IP 주소 127.0.0.1을 추가할 수 있습니다.
>
>예: &quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

다음과 같은 다양한 경우가 발생할 수 있습니다.

* 보안 영역에서 하위 네트워크를 직접 참조하며 프록시가 구성되지 않습니다. 하위 네트워크 사용자는 Adobe Campaign 서버에 직접 연결할 수 있습니다.

  ![](assets/8101_proxy1.png)

* 보안 영역의 하위 네트워크에 대해 프록시가 지정됩니다. 이 하위 네트워크의 사용자는 이 프록시를 통해 Adobe Campaign 서버에 액세스할 수 있습니다.

  ![](assets/8101_proxy2.png)

* 프록시는 보안 영역 하위 네트워크에 포함되어 있습니다. 이 프록시를 통해 액세스할 수 있는 사용자는 출처에 관계없이 Adobe Campaign 서버에 액세스할 수 있습니다.

  ![](assets/8101_proxy3.png)

Adobe Campaign 서버에 액세스할 수 있는 프록시의 IP 주소를 관련 **`<subnetwork>`**&#x200B;과(와) 첫 번째 수준 하위 네트워크 **`<subnetwork name="all"/>`** 모두에 입력해야 합니다. 예를 들어 IP 주소가 10.131.146.102인 프록시의 경우 다음과 같습니다.

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

영역이 정의되면 각 연산자가 인스턴스에 로그온할 수 있도록 해당 연산자 중 하나에 연결되어 있어야 하며 연산자의 IP 주소가 영역에서 참조되는 주소 또는 주소 범위에 포함되어야 합니다.

영역의 기술 구성은 Campaign 서버의 구성 파일에서 수행됩니다. **serverConf.xml**.

이 작업을 수행하기 전에 먼저 **serverConf.xml** 파일에 정의된 영역의 내부 이름에 레이블을 연결하도록 기본 제공 **[!UICONTROL Security zone]** 열거를 구성해야 합니다.

이 구성은 Campaign 탐색기에서 수행됩니다.

1. **[!UICONTROL Administration > Platform > Enumerations]** 노드를 클릭합니다.
1. **[!UICONTROL Security zone (securityZone)]** 시스템 열거형을 선택하십시오.

   ![](assets/enum_securityzone.png)

1. 서버의 구성 파일에 정의된 각 보안 영역에 대해 **[!UICONTROL Add]** 단추를 클릭합니다.
1. **[!UICONTROL Internal name]** 필드에 **serverConf.xml** 파일에 정의된 영역 이름을 입력합니다. `<securityzone>` 요소의 **@name** 특성에 해당합니다. **레이블** 필드에 내부 이름에 연결된 레이블을 입력합니다.

   ![](assets/enum_addsecurityvalue.png)

1. 확인 을 클릭하고 수정 사항을 저장합니다.

영역이 정의되고 **[!UICONTROL Security zone]** 열거형이 구성되면 각 연산자를 보안 영역에 연결해야 합니다.

1. **[!UICONTROL Administration > Access management > Operators]** 노드를 클릭합니다.
1. 보안 영역을 연결할 연산자를 선택하고 **[!UICONTROL Edit]** 탭을 클릭합니다.
1. **[!UICONTROL Access rights]** 탭으로 이동하여 **[!UICONTROL Edit access parameters...]** 링크를 클릭합니다.

   ![](assets/zone_operator.png)

1. **[!UICONTROL Authorized connection zone]** 드롭다운 목록에서 영역 선택

   ![](assets/zone_operator_selection.png)

1. **[!UICONTROL OK]**&#x200B;을(를) 클릭하고 수정 내용을 저장하여 변경 내용을 적용합니다.



## 권장 사항

* 의 역방향 프록시가 subNetwork에서 허용되지 않는지 확인하십시오. 이 경우 **모두** 트래픽은 이 로컬 IP에서 오는 것으로 검색되므로 신뢰할 수 있습니다.

* sessionTokenOnly=&quot;true&quot; 사용을 최소화하십시오.

   * 경고: 이 특성이 true로 설정되면 연산자가 **CRSF 공격**&#x200B;에 노출될 수 있습니다.
   * 또한 sessionToken 쿠키는 httpOnly 플래그로 설정되지 않으므로 일부 클라이언트측 JavaScript 코드에서 읽을 수 있습니다.
   * 그러나 여러 실행 셀의 메시지 센터에는 sessionTokenOnly가 필요합니다. sessionTokenOnly가 &quot;true&quot;로 설정된 새 보안 영역을 만들고 이 영역에 **필요한 IP만**&#x200B;을(를) 추가하십시오.

* 가능하면 모든 allowHTTP, showErrors를 false(localhost가 아님)로 설정하고 확인합니다.

   * allowHTTP = &quot;false&quot;: 연산자가 HTTPS를 사용하도록 합니다.
   * showErrors = &quot;false&quot;: 기술 오류(SQL 오류 포함)를 숨깁니다. 너무 많은 정보를 표시하지 않도록 하지만, 마케터가 실수를 해결하는 능력이 줄어듭니다(관리자에게 자세한 정보를 요청하지 않음)

* 설문 조사(실제로 미리 보기), 웹 앱 및 보고서를 만들어야 하는 마케팅 사용자/관리자가 사용하는 IP에 대해서만 allowDebug를 true로 설정합니다. 이 플래그를 사용하면 이러한 IP가 릴레이 규칙을 표시하고 디버깅할 수 있습니다.

   * allowDebug가 false로 설정되면 출력은 다음과 같습니다.

     ```
     <redir status='OK' date='...' sourceIP='...'/>
     ```

   * allowDebug가 true로 설정되면 출력은 다음과 같습니다.

     ```
     <redir status='OK' date='...' build='...' OR version='...' sha1='...' instance='...' sourceIP='...' host='...' localHost='...'/>
     ```

* allowEmptyPassword, allowUserPassword, allowSQLInjection을 true로 설정하지 마십시오.

   * **allowEmptyPassword**&#x200B;를 사용하면 연산자의 암호가 비어 있습니다. 이 경우 모든 운영자에게 기한을 지정하여 암호를 설정하도록 알립니다. 이 기한이 지나면 이 속성을 false로 변경하십시오.

   * **allowUserPassword**&#x200B;을(를) 통해 운영자는 자격 증명을 매개 변수로 전송할 수 있습니다(따라서 apache/IIS/프록시로 기록됨). 이 기능은 과거에는 API 사용을 단순화하기 위해 사용되었습니다. 일부 서드파티 애플리케이션에서 쿠키를 사용하는지 여부를 쿠키 북(또는 사양)에서 확인할 수 있습니다. 그렇다면 API 사용 방법을 변경하고 가능한 한 빨리 이 기능을 제거하도록 알려야 합니다.

   * **allowSQLInjection**&#x200B;을(를) 사용하면 이전 구문을 사용하여 SQL 주입을 수행할 수 있습니다. 이 속성은 false로 설정해야 합니다. /nl/jsp/ping.jsp?zones=true 를 사용하여 보안 영역 구성을 확인할 수 있습니다. 이 페이지에는 현재 IP에 대한 보안 조치의 활성 상태(이러한 보안 플래그로 계산)가 표시됩니다.

* HttpOnly 쿠키/useSecurityToken: **sessionTokenOnly** 플래그를 참조하십시오.

* 허용 목록에 추가하다에 추가되는 IP를 최소화합니다. 보안 영역에서 개인 네트워크에 대한 3가지 범위를 추가했습니다. 이러한 IP 주소를 모두 사용할 가능성은 낮습니다. 그러니 필요한 것만 보관하세요.

* localhost에서만 액세스할 수 있도록 webApp/internal 연산자를 업데이트합니다.
