---
solution: Campaign Classic
product: campaign
title: 보안 영역 구성
description: 보안 영역을 구성하는 방법 알아보기
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---


# 보안 영역 정의 {#defining-security-zones}

각 연산자를 인스턴스에 로그온하려면 영역에 연결해야 하며 연산자 IP를 보안 영역에 정의된 주소 또는 주소 세트에 포함해야 합니다. 보안 영역 구성은 Adobe Campaign 서버의 구성 파일에서 수행됩니다.

연산자는 콘솔( **[!UICONTROL Administration > Access management > Operators]** 노드)의 프로파일에서 보안 영역에 연결됩니다. [이 섹션](#linking-a-security-zone-to-an-operator)에서 영역을 캠페인 연산자에 연결하는 방법을 알아봅니다.

## 보안 영역 만들기 {#creating-security-zones}

영역은 다음과 같이 정의됩니다.

* 하나 이상의 IP 주소 범위(IPv4 및 IPv6)
* 각 IP 주소 범위에 연결된 기술 이름

보안 영역은 상호 잠깁니다. 즉, 다른 영역 내에서 새 영역을 정의하면 각 연산자에 할당된 권한을 증가시키면서 해당 영역에 로그온할 수 있는 연산자 수가 줄어듭니다.

서버 구성 중에 **serverConf.xml** 파일에서 영역을 정의해야 합니다. **serverConf.xml**&#x200B;에 사용할 수 있는 모든 매개 변수가 [이 섹션](../../installation/using/the-server-configuration-file.md)에 나열됩니다.

각 영역은 다음과 같은 권한을 정의합니다.

* HTTPS가 아닌 HTTP 연결
* 오류 표시(Java 오류, JavaScript, C++ 등)
* 보고서 및 웹 앱 미리 보기
* 로그인/암호를 통한 인증
* 비보안 연결 모드

>[!NOTE]
>
>**각 연산자는 영역에 연결해야 합니다**. 연산자의 IP 주소가 영역에 의해 정의된 범위에 속하는 경우 연산자는 인스턴스에 로그온할 수 있습니다.\
>연산자의 IP 주소는 여러 영역에 정의할 수 있습니다. 이 경우 연산자는 각 영역에 대해 사용 가능한 권한의 **set**&#x200B;을 받습니다.

즉시 사용 가능한 **serverConf.xml** 파일에는 다음 3개의 영역이 포함됩니다.**공개, VPN 및 LAN**.

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
* **allowEmptyPassword**:암호가 없는 인스턴스에 대한 연결을 허용합니다.
* **allowHTTP**:HTTPS 프로토콜을 사용하지 않고 세션을 만들 수 있습니다.
* **allowUserPassword**:세션 토큰에는 &quot;`<login>/<password>`&quot; 양식이 있을 수 있습니다.
* **sessionTokenOnly**:연결 URL에는 보안 토큰이 필요하지 않습니다.
* **showErrors**:서버 쪽의 오류가 전달되고 표시됩니다.

>[!IMPORTANT]
>
>영역 정의에서 **true** 값이 있는 각 특성은 보안을 감소시킵니다.

메시지 센터를 사용할 때 실행 인스턴스가 여러 개 있는 경우 필요한 IP 주소만 추가할 수 있는 **true**&#x200B;로 정의된 **sessionTokenOnly** 특성을 사용하여 추가 보안 영역을 만들어야 합니다. 인스턴스 구성에 대한 자세한 내용은 [이 문서](../../message-center/using/creating-a-shared-connection.md)를 참조하십시오.

## 보안 영역에 대한 우수 사례 {#best-practices-for-security-zones}

**lan** 보안 영역의 정의에서 기술 액세스를 정의하는 IP 주소 마스크를 추가할 수 있습니다. 이렇게 추가하면 서버에 호스팅된 모든 인스턴스에 액세스할 수 있습니다.

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

특정 인스턴스에만 액세스하는 연산자에 대해 인스턴스에 대한 전용 구성 파일에서 직접 IP 주소 범위를 정의하는 것이 좋습니다.

**`config-<instance>.xml`** 파일에서:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## 보안 영역 {#sub-networks-and-proxies-in-a-security-zone}의 하위 네트워크 및 프록시

**proxy** 매개 변수는 **subNetwork** 요소에서 사용하여 보안 영역에서 프록시 사용을 지정할 수 있습니다.

프록시가 참조되고 이 프록시를 통해 연결이 입력될 때(HTTP X-Forwarded-For 헤더를 통해 표시됨) 확인된 영역은 프록시의 클라이언트가 아니라 프록시의 클라이언트여야 합니다.

>[!IMPORTANT]
>
>프록시가 구성되어 있고 재정의할 수 있는 경우(또는 존재하지 않는 경우) 테스트할 IP 주소를 변경할 수 있습니다.
>
>또한 이제 레이가 프록시처럼 생성됩니다. 따라서 보안 영역 구성의 프록시 목록에 IP 주소 127.0.0.1을 추가할 수 있습니다.
>
>예제: &quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

다음과 같은 여러 가지 경우가 발생할 수 있습니다.

* 하위 네트워크가 보안 영역에서 직접 참조되며 프록시가 구성되지 않았습니다.하위 네트워크 사용자는 Adobe Campaign 서버에 직접 연결할 수 있습니다.

   ![](assets/8101_proxy1.png)

* 보안 영역의 하위 네트워크에 대해 프록시가 지정되었습니다.이 하위 네트워크의 사용자는 이 프록시를 통해 Adobe Campaign 서버에 액세스할 수 있습니다.

   ![](assets/8101_proxy2.png)

* 프록시는 보안 영역 하위 네트워크에 포함됩니다.원본에 관계없이 이 프록시를 통해 액세스할 수 있는 사용자는 Adobe Campaign 서버에 액세스할 수 있습니다.

   ![](assets/8101_proxy3.png)

Adobe Campaign 서버에 액세스할 가능성이 있는 프록시의 IP 주소는 해당 **`<subnetwork>`** 및 첫 번째 수준 하위 네트워크 **`<subnetwork name="all"/>`** 모두에 입력해야 합니다. 예를 들어 IP 주소가 10.131.146.102인 프록시의 경우 다음을 수행합니다.

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

## 보안 영역을 연산자 {#linking-a-security-zone-to-an-operator}에 연결

영역이 정의된 후에는 각 연산자를 인스턴스 중 하나에 연결하여 인스턴스를 로그온하고 연산자의 IP 주소를 영역에서 참조하는 주소 또는 범위의 주소에 포함해야 합니다.

영역의 기술 구성은 캠페인 서버의 구성 파일에서 수행됩니다.**serverConf.xml**.

이에 앞서 **serverConf.xml** 파일에 정의된 영역의 내부 이름에 레이블을 링크하기 위해 기본 **[!UICONTROL Security zone]** 열거형을 구성해야 합니다.

이 구성은 캠페인 탐색기에서 수행됩니다.

1. **[!UICONTROL Administration > Platform > Enumerations]** 노드를 클릭합니다.
1. **[!UICONTROL Security zone (securityZone)]** 시스템 열거형을 선택합니다.

   ![](assets/enum_securityzone.png)

1. 서버의 구성 파일에 정의된 각 보안 영역에 대해 **[!UICONTROL Add]** 단추를 클릭합니다.
1. **[!UICONTROL Internal name]** 필드에 **serverConf.xml** 파일에 정의된 영역의 이름을 입력합니다. 이것은 `<securityzone>` 요소의 **@name** 속성에 해당합니다. **레이블**&#x200B;필드에 내부 이름에 연결된 레이블을 입력합니다.

   ![](assets/enum_addsecurityvalue.png)

1. 확인을 클릭하고 수정 내용을 저장합니다.

영역이 정의되고 **[!UICONTROL Security zone]** 열거가 구성되면 각 연산자를 보안 영역에 연결해야 합니다.

1. **[!UICONTROL Administration > Access management > Operators]** 노드를 클릭합니다.
1. 보안 영역을 연결할 연산자를 선택하고 **[!UICONTROL Edit]** 탭을 클릭합니다.
1. **[!UICONTROL Access rights]** 탭으로 이동하여 **[!UICONTROL Edit access parameters...]** 링크를 클릭합니다.

   ![](assets/zone_operator.png)

1. **[!UICONTROL Authorized connection zone]** 드롭다운 목록에서 영역을 선택합니다.

   ![](assets/zone_operator_selection.png)

1. **[!UICONTROL OK]**&#x200B;을 클릭하고 수정 내용을 저장하여 이러한 변경 내용을 적용합니다.
