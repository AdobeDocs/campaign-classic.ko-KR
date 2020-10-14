---
title: Adobe Campaign Classic의 전달 능력 향상을 위한 기술 추천
description: Adobe Campaign Classic을 통해 전달률을 향상시키는 데 사용할 수 있는 기법, 구성 및 툴을 살펴볼 수 있습니다.
page-status-flag: never-activated
uuid: 71be1087-e5ff-4a7a-85ca-36803839e72f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: fc95538b-b54d-44ec-81aa-f51b62982699
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '2432'
ht-degree: 0%

---


# 기술 추천{#technical-recommendations}

배달율을 향상시키는 데 사용할 수 있는 몇 가지 기법, 구성 및 도구는 아래에 나와 있습니다.

## 구성 {#configuration}

### DNS 반전 {#reverse-dns}

Adobe Campaign은 IP 주소에 대해 역 DNS가 제공되는지 그리고 이것이 IP를 올바르게 가리키는지 확인합니다.

네트워크 구성의 중요한 점은 보내는 메시지의 각 IP 주소에 대해 올바른 역방향 DNS가 정의되어 있는지 확인하는 것입니다. 즉, 지정된 IP 주소의 경우, 일치하는 DNS(A 레코드)가 초기 IP 주소로 다시 루프되는 PTR 레코드(역방향 DNS 레코드)가 있습니다.

역 DNS에 대한 도메인 선택은 특정 ISP를 처리할 때 영향을 줍니다. 특히 AOL은 역방향 DNS와 동일한 도메인에 주소가 있는 피드백 루프만 [허용합니다(피드백 루프 참조](#feedback-loop)).

다음 도구를 사용하여 도메인 구성을 확인할 수 있습니다. [https://mxtoolbox.com/SuperTool.aspx](https://mxtoolbox.com/SuperTool.aspx).

### MX 규칙 {#mx-rules}

MX 규칙(메일 교환기)은 전송 서버와 수신 서버 간의 통신을 관리하는 규칙입니다.

보다 정확하게 캠페인 MTA(메시지 전송 에이전트)가 각 개별 이메일 도메인 또는 ISP(예: hotmail.com, comcast.net)로 이메일을 보내는 속도를 제어하는 데 사용됩니다. 이러한 규칙은 일반적으로 ISP가 게시한 제한을 기준으로 합니다(예: 각 SMTP 연결당 20개 이상의 메시지가 포함되지 않음).

For more on MX management, refer to [this section](../../installation/using/email-deliverability.md#mx-configuration).

### TLS {#tls}

TLS(전송 계층 보안)는 두 개의 이메일 서버 간의 연결을 보호하고 이메일 컨텐츠가 의도한 수신자가 아닌 다른 사람이 읽지 못하도록 보호하는 데 사용할 수 있는 암호화 프로토콜입니다.

## 인증 {#authentication}

### SPF {#spf}

SPF(Sender Policy Framework)는 도메인 소유자가 해당 도메인을 대신하여 이메일을 보낼 수 있는 이메일 서버를 지정할 수 있는 이메일 인증 표준입니다. 이 표준은 이메일의 &quot;반환 경로&quot; 헤더에 있는 도메인을 사용합니다(&quot;수신 주소&quot; 라고도 함).

SPF 레코드를 확인하는 도구를 사용할 수 있습니다. [https://www.kitterman.com/spf/validate.html](https://www.kitterman.com/spf/validate.html)

SPF는 이메일에 사용된 도메인 이름이 위조되지 않도록 일정 범위 내에서 사용자가 확인할 수 있는 기술입니다. 도메인에서 메시지를 받으면 도메인의 DNS 서버를 쿼리합니다. 이 응답은 이 도메인에서 이메일을 보낼 수 있는 서버를 자세히 설명하는 짧은 레코드(SPF 레코드)입니다. 도메인 소유자만 이 레코드를 변경할 수 있는 방법을 가지고 있다고 가정할 경우, 보낸 사람 주소를 위조할 수 없도록 이 방법을 고려할 수 있습니다. 적어도 &quot;@&quot;의 오른쪽의 부분이 아닙니다.

최종 [RFC 4408 규격에서 메시지 요소](https://www.rfc-editor.org/info/rfc4408)두 개를 사용하여 보낸 사람으로 간주되는 도메인을 결정합니다.SMTP &quot;HELO&quot;(또는 &quot;EHLO&quot;) 명령에 의해 지정된 도메인 및 &quot;반환 경로&quot;(또는 &quot;MAIL FROM&quot;) 헤더의 주소로 지정된 도메인(바운스 주소)입니다. 서로 다른 고려 사항을 사용하면 이러한 값 중 하나만 고려할 수 있습니다.두 소스 모두 동일한 도메인을 지정하도록 하는 것이 좋습니다.

SPF를 검사하면 보낸 사람 도메인의 유효성을 평가할 수 있습니다.

* **없음**:평가를 수행할 수 없습니다.
* **중립**:쿼리된 도메인이 평가를 활성화하지 않습니다.
* **통과**:그 도메인은 진짜인 것으로 여겨집니다
* **실패**:그 도메인은 위조되고 메시지는 거부되어야 합니다
* **소프트 실패**:도메인은 위조된 것일 수 있지만, 이러한 결과의 근거만으로 메시지가 거부되어서는 안 됩니다.
* **임시 오류**:일시적인 오류가 평가를 중지했습니다. 메시지는 거부할 수 있습니다.
* **PermError**:도메인의 SPF 레코드가 잘못되었습니다.

DNS 서버 수준에서 생성된 레코드를 고려하는 데 최대 48시간이 걸릴 수 있다는 점을 주목해 보십시오. 이 지연은 수신 서버의 DNS 캐시가 새로 고쳐지는 빈도에 따라 다릅니다.

### DKIM {#dkim}

DKIM(DomainKeys Identified Mail) 인증은 SPF의 후속 조치로, 받는 이메일 서버가 보낸 것이라고 주장하는 사람 또는 엔티티가 메시지를 실제로 보냈는지, 메시지 컨텐츠가 원래 전송(및 DKIM &quot;signed&quot;)된 시간과 메시지 수신 시간 사이에 변경되었는지 여부를 확인하는 공개 키 암호화를 사용합니다. 이 표준은 일반적으로 &quot;보낸 사람&quot; 또는 &quot;보낸 사람&quot; 헤더의 도메인을 사용합니다. DKIM의 보안 수준을 보장하기 위해, 1024b는 권장 암호화 크기입니다. DKIM 키가 낮으면 대부분의 액세스 공급자가 유효한 것으로 간주하지 않습니다.

DKIM은 DomainKeys, Yahoo! Cisco Identified Internet Mail 인증 원칙을 준수하고 발신자 도메인의 신뢰성을 확인하고 메시지의 무결성을 보증하는 데 사용됩니다.

DKIM이 **DomainKeys 인증을** 대체했습니다.

DKIM을 사용하려면 몇 가지 전제 조건이 필요합니다.

* **보안**:암호화는 DKIM의 주요 요소로서 2013년 봄, 1024b가 권장되는 암호화 크기인 DKIM의 보안 수준을 보장합니다. DKIM 키가 낮으면 대부분의 액세스 공급자가 유효한 것으로 간주하지 않습니다.
* **평판**:명성은 IP 및/또는 도메인을 기반으로 하지만 덜 투명한 DKIM 선택기도 고려해야 할 주요 요소입니다. 선택기를 선택하는 것이 중요합니다.누구나 사용할 수 있는 &quot;기본값&quot;을 유지하지 않아도 되며, 따라서 매우 약합니다. 고객 **유지와 고객 확보 커뮤니케이션과 인증을 위해** 다른 선택기를 구현해야 합니다.
* **Adobe Campaign 옵션 선언**:adobe 캠페인에서 DKIM 개인 키는 DKIM 선택기 및 도메인을 기반으로 합니다. 현재 선택기가 다른 동일한 도메인/하위 도메인에 대해 여러 개의 개인 키를 만들 수 없습니다. 플랫폼 또는 이메일 모두에서 인증에 사용할 선택기 도메인/하위 도메인을 정의할 수 없습니다. 플랫폼이 개인 키 중 하나를 선택할 수도 있습니다. 즉, 인증이 실패할 가능성이 높습니다.

>[!NOTE]
>
>* Adobe Campaign 인스턴스에 대해 DomainKeys를 구성한 경우 **도메인 관리 규칙에서** DKIM을 선택하기만 하면 됩니다 [](../../delivery/using/understanding-delivery-failures.md#domain-management). 그렇지 않은 경우 DomainKeys와 동일한 구성 단계(개인/공개 키)를 따릅니다.
>* DKIM과 동일한 도메인에 대해 DomainKeys와 DKIM을 모두 사용할 필요는 없습니다.
>* 다음 도메인은 현재 DKIM의 유효성을 검사합니다.AOL, Gmail.


>[!IMPORTANT]
>
>호스팅 또는 하이브리드 설치의 경우 [향상된 MTA로 업그레이드한 경우 모든 도메인에 포함된 모든 메시지에 대해 향상된 MTA에서](https://helpx.adobe.com/kr/campaign/kb/acc-campaign-enhanced-mta.html)DKIM 이메일 인증 서명을 수행합니다.

### DMARC {#dmarc}

DMARC(도메인 기반 메시지 인증, 보고 및 적합성)는 가장 최근 이메일 인증 방식이며, SPF 및 DKIM 인증을 통해 이메일 전달 여부를 확인합니다. DMARC는 매우 중요한 두 가지 방법으로 독특하고 강력합니다.

* 적합성 - 발신자가 인증하지 못한 메시지(예: 승인하지 않음)를 사용하여 ISP에 수행할 작업을 지시할 수 있도록 해줍니다.
* 보고 - 발신자에게 DMARC 인증에 실패한 모든 메시지와 각각에 사용되는 &quot;보낸 사람&quot; 도메인 및 IP 주소를 보여주는 자세한 보고서를 제공합니다. 이를 통해 회사는 인증이 실패하고 일부 유형의 &quot;수정&quot;(예: SPF 레코드에 IP 주소 추가) 및 이메일 도메인에서 피싱 시도 소식과 출현이 필요한 합법적 이메일을 식별할 수 있습니다.

DMARC는 [250ok로 생성된 보고서를 활용할 수 있습니다](https://250ok.com/).

<!--#### Configuring the application {#configuring-the-application}

To define the domain used for the HELO command, edit the instance's configuration file (conf/config-instance.xml) and define a "localDomain" attribute as follows:

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

The MAIL FROM domain is the domain used in technical bounce messages. This address is defined in the deployment wizard or via the NmsEmail_DefaultErrorAddr option.

#### DNS configuration {#dns-configuration}

An SPF record can currently be defined on a DNS server as a TXT type record (code 16) or an SPF type record (code 99). An SPF record takes the form of a character string. For example:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

defines the 2 IP addresses 12.34.56.78 and 12.34.56.79 as authorized to send emails for the domain. **~all** means that any other address should be interpreted as a SoftFail.

Recommendations for defining an SPF record:

* Add **~all** (SoftFail) or **-all** (Fail) at the end to reject all servers other than those defined. Without this, servers will be able to forge this domain (with a Neutral evaluation).
* Do not add **ptr** (openspf.org recommends against this as costly and unreliable).-->

## 피드백 루프 {#feedback-loop}

피드백 루프는 ISP 수준에서 메시지를 전송하는 데 사용되는 IP 주소 범위에 대해 지정된 이메일 주소를 선언하여 작동합니다. ISP는 이 사서함에 바운스 메시지에 대해 수행되는 작업과 유사한 방법으로 받는 사람이 스팸으로 보고한 메시지를 보냅니다. 이 플랫폼은 불평한 사용자에 대한 향후 제공을 차단하도록 구성해야 합니다. 적절한 옵트아웃 링크를 사용하지 않더라도 더 이상 연락하지 않는 것이 중요합니다. ISP가 IP 주소를에 추가하는 것은 이러한 차단 목록 불만 사항을 기초로 합니다. ISP에 따라, 약 1%의 불만 비율은 IP 주소를 차단하게 됩니다.

현재 피드백 루프 메시지의 형식을 정의하기 위해 표준을 작성하고 있습니다.ARF( [남용된 피드백 보고 형식)](https://tools.ietf.org/html/rfc6650).

인스턴스에 대한 피드백 루프를 구현하려면 다음이 필요합니다.

* 인스턴스 전용 사서함(바운스 사서함)
* 인스턴스에 전용 IP 전송 주소

Adobe Campaign에서 단순 피드백 루프를 구현하면 바운스 메시지 기능이 사용됩니다. 피드백 루프 사서함은 바운스 사서함으로 사용되고 이러한 메시지를 감지하도록 규칙이 정의됩니다. 스팸으로 메시지를 신고한 받는 사람의 이메일 주소가 격리 목록에 추가됩니다.

* 거부됨 및 하드 유형 **과 함께 바운스 메일 규칙**&#x200B;인 Feedback_loop **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** 를 만들거나 **** 수정합니다 ****.
* 피드백 루프에 대한 사서함이 특별히 정의된 경우 새 외부 바운스 메일 계정을 만들어 액세스할 매개 변수를 정의합니다 **[!UICONTROL Administration > Platform > External accounts]**.

이 메커니즘은 불만 알림을 처리하는 즉시 작동합니다. 이 규칙이 제대로 작동하는지 확인하려면, 계정이 이러한 메시지를 수집하지 않도록 일시적으로 계정을 비활성화한 다음, 피드백 루프 사서함의 내용을 수동으로 확인할 수 있습니다. 서버에서 다음 명령을 실행합니다.

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

여러 인스턴스에 대해 하나의 피드백 루프 주소를 사용해야 하는 경우 다음을 수행해야 합니다.

* 메일박스에서 받은 메시지를 인스턴스 수만큼 복제하고
* 각 사서함을 하나의 인스턴스로 선택하도록
* 관련 메시지만 처리하도록 인스턴스를 구성합니다.인스턴스 정보는 Adobe Campaign이 보낸 메시지의 메시지 ID 헤더에 포함되어 있으므로 피드백 루프 메시지도 찾을 수 있습니다. 인스턴스 구성 파일에 **checkInstanceName** 매개 변수를 간단히 지정하기만 하면 됩니다(기본적으로 인스턴스가 확인되지 않으며 이로 인해 특정 주소가 잘못 격리될 수 있음).

   ```
   <serverConf>
     <inMail checkInstanceName="true"/>
   </serverConf>
   ```

Adobe Campaign의 Delivery Ability 서비스는 다음 ISP에 대한 피드백 루프 서비스 구독을 관리합니다.AOL, BlueTie, Comcast, EarthLink, FastMail, Gmail, HostedEmail, Libero, Mail.ru, MailTrust, OpenSRS, QQ, RoadRunner, Synacor, Telenor, UnitedOnline, USA 4ALL, Yahoo, Yandex, Zoho

## 목록 구독 취소 {#list-unsubscribe}

### 목록 가입 해지 정보 {#about-list-unsubscribe}

최적의 전달 능력 관리를 위해 **List-Unsubscription** 이라는 SMTP 헤더를 추가해야 합니다.

이 헤더는 &quot;스팸으로 신고&quot; 아이콘의 대안으로 사용할 수 있습니다. 이메일 인터페이스에 구독 취소 링크로 표시됩니다.

이 기능을 사용하면 평판 및 피드백을 보호하는 데 도움이 되며 사용료 지불 요금제가 적용되지 않는 것으로 실행됩니다.

>[!NOTE]
>
>이 기능은 빌드 6831에서 사용할 수 있습니다.

목록 가입 해지 기능을 사용하려면 다음과 유사한 명령줄을 입력해야 합니다.

```
List-Unsubscribe: mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe
```

>[!IMPORTANT]
>
>위의 예는 수신자 테이블을 기반으로 합니다. 다른 테이블에서 데이터베이스 구현이 수행되면 올바른 정보로 명령줄을 다시 입력해야 합니다.

다음 명령줄을 사용하여 동적 **목록-구독 취소를 만들 수 있습니다**.

```
List-Unsubscribe: mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%
```

Gmail, Outlook.com 및 Microsoft Outlook은 이 방법을 지원하며, 구독 취소 단추는 인터페이스에서 바로 사용할 수 있습니다. 이 방법을 사용하면 불만 횟수가 줄어듭니다.

![](assets/s_tn_del_msn_unsubscribe_list.png)

![](assets/s_tn_del_gmail_unsubscribe_list.png)

다음과 같은 방법으로 **목록-구독 취소를** 구현할 수 있습니다.

* 전달 템플릿에서 명령줄을 직접 추가하는 방법 - [이 섹션](#adding-a-command-line-in-a-delivery-template),
* 또는, 분류 규칙 만들기 - [이 섹션을 참조하십시오](#creating-a-typology-rule).

### 배달 템플릿에서 명령줄 추가 {#adding-a-command-line-in-a-delivery-template}

이메일의 SMTP 헤더의 추가 섹션에 명령줄을 추가해야 합니다.

이러한 추가 작업은 각 이메일 또는 기존 배달 템플릿에서 수행할 수 있습니다. 이 기능을 포함하는 새 배달 템플릿을 만들 수도 있습니다.

### 유형화 규칙 만들기 {#creating-a-typology-rule}

규칙에는 명령줄을 생성하는 스크립트가 포함되어야 하며, 이 스크립트는 이메일 헤더에 포함되어야 합니다.

>[!NOTE]
>
>다음과 같은 유형 규칙을 만드는 것이 좋습니다.목록 구독 취소 기능은 각 이메일에 자동으로 추가됩니다.

1. 목록 구독 취소:&lt;mailto:unsubscribe@domain.com>

   가입 **해지** 링크를 클릭하면 사용자의 기본 이메일 클라이언트가 열립니다. 이러한 유형 규칙을 이메일을 만드는 데 사용되는 유형 분석에 추가해야 합니다.

1. 목록 구독 취소: `<https://domain.com/unsubscribe.jsp>`

   구독 **취소** 링크를 클릭하면 사용자가 구독 취소 양식으로 리디렉션됩니다.

   예제:

   ![](assets/s_tn_del_unsubscribe_param.png)

## 이메일 최적화 {#email-optimization}

### SMTP {#smtp}

SMTP(Simple mail transfer protocol)는 이메일 전송을 위한 인터넷 표준입니다.

규칙으로 확인하지 않는 SMTP 오류는 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Delivery log qualification]** 폴더에 나열됩니다. 이러한 오류 메시지는 기본적으로 접근 불가능한 소프트 오류로 해석됩니다. SMTP 서버의 피드백을 올바르게 평가하려면 가장 일반적인 오류를 식별하고 해당 규칙을 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Mail rule sets]** 에 추가해야 합니다. 이렇게 하지 않으면 플랫폼에서는 불필요한 재시도를 하거나(알 수 없는 사용자의 경우) 지정된 테스트 수 이후에 특정 수신자를 격리하도록 잘못 지정합니다.

### 전용 IP {#dedicated-ips}

Adobe은 명성을 구축하고 전달 성능을 최적화하기 위해 고객마다 구현 IP를 제공하는 전용 IP 전략을 제공합니다.

## IP 인증 {#ip-certification}

IP 인증은 스팸 방지 필터나 기타 이메일 차단 시스템에 의해 차단되지 않고 이메일을 수신하도록 지원하는 전송 모범 사례 프로그램입니다.

현재 두 개의 공급업체에서 IP 인증을 제공합니다.반환 경로 및 인증된 보낸 사람 연합.

인증된 전송자는 글로벌 사서함 제공업체 및 이메일 보안 회사가 사용하는 이메일 허용 목록에 추가됩니다. 이러한 상용 허용 목록은 발신자가 스팸 필터를 모두 우회하거나 시스템에 들어갈 때 점차적으로 포인트를 할당할 수 있는 시스템을 기반으로 합니다.

반품 [경로 인증](https://www.validity.com/products/returnpath/certification/) 프로그램은 다음을 포함한 다양한 혜택을 제공합니다.

* Microsoft, AOL, Yahoo, Gmail, Comcast, Orange, Mail.ru와 같은 상위 사서함 제공업체에서 받은 편지함 배치로 상당한 증가
* Cloudmark, SpamAsser 및 Cisco Ironport와 같은 중요한 필터에서 평판 및 대우
* 24시간 연중무휴 모니터링 전담 규정 준수 팀, 보안 경고 제공 및 모든 조회의 해결
* KPI, 배치 및 인증 성능에 대한 자세한 정보를 제공하는 사서함 공급자 데이터
* 새로운 IP 주소 마이그레이션 또는 확보 시 높은 명성과 인지도를 포함하여 IP가 더욱 빠르고 간편해졌습니다.

ACA( [Certified Sender Alliance](https://certified-senders.org/certification-process/) ) 인증은 다음과 같은 여러 가지 이점을 제공합니다.

* 고품질 표준을 준수하는 상업용 이메일 전송자 인증
* 상업용 이메일의 전달 및 전달 기능이 향상되어 받은 편지함 배치 비율을 높이고 스팸 필터링 감소
* 법률 표준을 완벽하게 준수하여 법적 및 재정적 위험으로부터 보호
* CSA 불만 사항 사무소 및 일일 스팸 트랩 보고서로부터 조기 경고를 통해 평판 보호

ISP는 이러한 서비스를 무료로 사용할 수 있으며 ISP의 수는에 따라 달라질 수 허용 목록에 추가하다 있습니다.

그러나 점점 더 많은 ISP가 메시지 내용 자체를 분석하지 않고 각 받은 편지함 소유자의 행동에 따라 스팸 방지 필터를 만들기 때문에 IP 인증을 사용하는 것은 받은 편지함 배치나 전달을 보장할 수 없습니다.
