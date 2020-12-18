---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic을 통한 제공 능력 향상을 위한 기술 추천
description: Adobe Campaign Classic을 통해 전달률을 향상시키는 데 사용할 수 있는 기법, 구성 및 툴을 살펴볼 수 있습니다.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2432'
ht-degree: 0%

---


# 기술 추천{#technical-recommendations}

배달률을 향상시키는 데 사용할 수 있는 몇 가지 기법, 구성 및 도구는 아래에 나와 있습니다.

## 구성 {#configuration}

### 역방향 DNS {#reverse-dns}

Adobe Campaign은 IP 주소에 대해 역 DNS가 제공되었는지 그리고 이것이 IP를 올바르게 가리키는지 확인합니다.

네트워크 구성의 중요한 점은 보내는 메시지의 각 IP 주소에 대해 올바른 역방향 DNS가 정의되어 있는지 확인합니다. 즉, 지정된 IP 주소의 경우 일치하는 DNS(A 레코드)가 초기 IP 주소로 다시 루핑되는 PTR 레코드(역방향 DNS 레코드)가 있습니다.

역 DNS에 대한 도메인 선택은 특정 ISP를 처리할 때 영향을 줍니다. 특히 AOL은 역방향 DNS와 동일한 도메인에 주소가 있는 피드백 루프만 허용합니다([피드백 루프](#feedback-loop) 참조).

도메인의 구성을 확인하는 데 사용할 수 있는 도구는 다음과 같습니다.[https://mxtoolbox.com/SuperTool.aspx](https://mxtoolbox.com/SuperTool.aspx).

### MX 규칙 {#mx-rules}

MX 규칙(메일 교환기)은 전송 서버와 수신 서버 간의 통신을 관리하는 규칙입니다.

보다 정확하게 캠페인 MTA(메시지 전송 에이전트)가 각 개별 이메일 도메인 또는 ISP(예: hotmail.com, comcast.net)로 이메일을 보내는 속도를 제어하는 데 사용됩니다. 이러한 규칙은 일반적으로 ISP가 게시한 제한을 기반으로 합니다(예: 각 SMTP 연결당 20개 이상의 메시지가 포함되지 않음).

MX 관리에 대한 자세한 내용은 [이 섹션](../../installation/using/email-deliverability.md#mx-configuration)을 참조하십시오.

### TLS {#tls}

TLS(전송 레이어 보안)는 두 이메일 서버 간의 연결을 보호하고 대상 받는 사람 이외의 다른 사람이 이메일 컨텐츠를 읽지 못하도록 보호하는 데 사용할 수 있는 암호화 프로토콜입니다.

## 인증 {#authentication}

### SPF {#spf}

SPF(Sender Policy Framework)는 도메인 소유자가 해당 도메인을 대신하여 이메일을 보낼 수 있는 이메일 서버를 지정할 수 있도록 하는 이메일 인증 표준입니다. 이 표준은 이메일의 &quot;반환 경로&quot; 헤더에 있는 도메인을 사용합니다(&quot;편지 봉투 보낸 사람&quot; 주소라고도 함).

SPF 레코드를 확인하는 도구를 사용할 수 있습니다.[https://www.kitterman.com/spf/validate.html](https://www.kitterman.com/spf/validate.html)

SPF는 이메일에 사용된 도메인 이름이 위조되지 않도록 어느 정도 할 수 있는 기술입니다. 도메인에서 메시지를 받으면 도메인의 DNS 서버를 쿼리합니다. 이 응답은 이 도메인에서 이메일을 보낼 수 있도록 허가된 서버를 자세히 설명하는 짧은 레코드(SPF 레코드)입니다. 도메인 소유자만 이 레코드를 변경할 수 있는 수단을 가지고 있다고 가정할 경우, 적어도 &quot;@&quot; 오른쪽의 부분이 아닌 보낸 사람 주소를 위조할 수 없습니다.

최종 [RFC 4408 사양](https://www.rfc-editor.org/info/rfc4408)에서 메시지 요소 두 개를 사용하여 보낸 사람으로 간주되는 도메인을 결정합니다.SMTP &quot;HELO&quot;(또는 &quot;EHLO&quot;) 명령에 의해 지정된 도메인과 &quot;반환 경로&quot;(또는 &quot;MAIL FROM&quot;) 헤더의 주소로 지정된 도메인(바운스 주소)입니다. 서로 다른 고려 사항을 사용하면 이러한 값 중 하나만 고려할 수 있습니다.두 소스 모두 동일한 도메인을 지정하도록 하는 것이 좋습니다.

SPF를 검사하면 보낸 사람 도메인의 유효성을 평가할 수 있습니다.

* **없음**:평가를 수행할 수 없습니다.
* **중립**:쿼리된 도메인이 평가를 활성화하지 않습니다.
* **통과**:도메인은 진짜인 것으로 간주됩니다
* **실패**:도메인은 위조되고 메시지는 거부되어야 합니다
* **소프트 실패**:그 도메인은 아마도 위조된 것일 것이지만, 메시지가 이 결과에 근거해서 거부되어서는 안됩니다.
* **임시 오류**:일시적인 오류가 평가를 중지했습니다. 메시지는 거부될 수 있습니다.
* **PermError**:도메인의 SPF 레코드가 잘못되었습니다.

DNS 서버 수준에서 수행된 기록을 고려하는 데 최대 48시간이 걸릴 수 있다는 점을 주목하십시오. 이 지연은 수신 서버의 DNS 캐시가 새로 고쳐지는 빈도에 따라 다릅니다.

### DKIM {#dkim}

DKIM(DomainKeys Identified Mail) 인증은 SPF의 후임자로, 받는 이메일 서버가 메시지를 보냈다고 주장하는 사람 또는 엔티티가 보낸 메시지인지, 메시지 컨텐츠가 원래 전송(및 DKIM &quot;signed&quot;)된 시간 사이에 변경되었는지 여부와 메시지 컨텐트가 수신될 때까지 변경되었는지 여부를 확인할 수 있도록 해주는 공개 키 암호화를 사용합니다. 이 표준은 일반적으로 &quot;보낸 사람&quot; 또는 &quot;보낸 사람&quot; 헤더의 도메인을 사용합니다. DKIM의 보안 수준을 보장하려면 1024b가 Best Practices 권장 암호화 크기입니다. 낮은 DKIM 키는 대부분의 액세스 공급자가 유효한 것으로 간주하지 않습니다.

DKIM은 DomainKeys, Yahoo! 및 Cisco Identified Internet Mail 인증 원칙을 준수하고 발신자 도메인의 신뢰성을 확인하고 메시지의 무결성을 보장하는 데 사용됩니다.

DKIM은 **DomainKeys** 인증을 대체했습니다.

DKIM을 사용하려면 몇 가지 전제 조건이 필요합니다.

* **보안**:암호화는 DKIM의 핵심 요소로서 2013년 봄, 1024b가 Best Practices 권장 암호화 크기인 DKIM의 보안 수준을 보장합니다. 낮은 DKIM 키는 대부분의 액세스 공급자가 유효한 것으로 간주하지 않습니다.
* **평판**:명성은 IP 및/또는 도메인을 기반으로 하지만 투명하지 않은 DKIM 선택기도 고려해야 할 핵심 요소입니다. 선택기를 선택하는 것은 중요합니다.누구나 사용할 수 있고 따라서 매우 약한 평판을 가진 &quot;기본값&quot;을 유지하지 마십시오. **유지 vs. 획득 통신** 및 인증에 대해 다른 선택기를 구현해야 합니다.
* **Adobe Campaign 옵션 선언**:adobe 캠페인에서 DKIM 개인 키는 DKIM 선택기 및 도메인을 기반으로 합니다. 현재 선택기가 다른 동일한 도메인/하위 도메인에 대해 여러 개의 개인 키를 만들 수 없습니다. 플랫폼 또는 이메일에서 인증에 어느 선택기 도메인/하위 도메인을 사용해야 하는지를 정의할 수 없습니다. 플랫폼에서 개인 키 중 하나를 선택할 수도 있습니다. 즉, 인증이 실패할 가능성이 높습니다.

>[!NOTE]
>
>* Adobe Campaign 인스턴스에 대해 DomainKeys를 구성한 경우 [도메인 관리 규칙](../../delivery/using/understanding-delivery-failures.md#domain-management)에서 **dkim**&#x200B;을 선택하기만 하면 됩니다. 그렇지 않은 경우 DomainKeys와 동일한 구성 단계(개인/공개 키)를 따릅니다.
>* DKIM과 동일한 도메인에 대해 DomainKeys와 DKIM을 모두 사용할 필요는 없습니다. 이는 DomainKeys의 향상된 버전입니다.
>* 다음 도메인은 현재 DKIM의 유효성을 검사합니다.AOL, Gmail.


>[!IMPORTANT]
>
>호스팅 또는 하이브리드 설치의 경우, [향상된 MTA](https://helpx.adobe.com/kr/campaign/kb/acc-campaign-enhanced-mta.html)로 업그레이드한 경우 모든 도메인의 모든 메시지에 대해 향상된 MTA가 DKIM 이메일 인증 서명을 수행합니다.

### DMARC {#dmarc}

DMARC(도메인 기반 메시지 인증, 보고 및 준수)는 가장 최신 이메일 인증 양식이며, SPF 및 DKIM 인증을 통해 이메일 전달 여부를 확인합니다. DMARC는 매우 중요한 두 가지 방법으로 독특하고 강력합니다.

* 적합성 - 발신자가 인증하지 못한 메시지(예: 승인하지 않음)를 ISP에 지시할 수 있도록 해줍니다.
* 보고 - &quot;보낸 사람&quot; 도메인 및 각 항목에 사용되는 IP 주소와 함께 DMARC 인증에 실패한 모든 메시지를 표시하는 자세한 보고서를 전송자에게 제공합니다. 이를 통해 회사는 인증이 실패하고 있고 일부 유형의 &quot;수정&quot;(예: SPF 레코드에 IP 주소 추가) 및 이메일 도메인에서 피싱 시도 소인과 출현을 필요로 하는 정당한 이메일을 식별할 수 있습니다.

DMARC는 [250ok](https://250ok.com/)에서 생성된 보고서를 활용할 수 있습니다.

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

피드백 루프는 메시지를 전송하는 데 사용되는 IP 주소 범위에 대해 ISP 수준에서 지정된 이메일 주소를 선언하여 작동합니다. ISP는 이 사서함에 바운스 메시지에 대해 수행되는 작업과 유사한 방법으로 받는 사람이 스팸으로 보고한 메시지를 보냅니다. 불만 사항이 있는 사용자에 대한 향후 제공을 차단하도록 플랫폼을 구성해야 합니다. 적절한 옵트아웃 링크를 사용하지 않더라도 더 이상 연락하지 않는 것이 중요합니다. ISP가 IP 주소를 해당에 추가하는 것은 이러한 불만 사항을 바탕으로 차단 목록 합니다. ISP에 따라, 약 1%의 불만 비율은 IP 주소를 차단하게 됩니다.

현재 피드백 루프 메시지의 형식을 정의하기 위해 표준을 작성하고 있습니다.[ARF(피드백 보고 형식)](https://tools.ietf.org/html/rfc6650).

인스턴스에 대한 피드백 루프를 구현하려면 다음이 필요합니다.

* 인스턴스 전용 사서함(바운스 사서함)입니다.
* 인스턴스에 전용 IP 전송 주소

Adobe Campaign에서 단순 피드백 루프를 구현하면 바운스 메시지 기능이 사용됩니다. 피드백 루프 사서함은 바운스 사서함으로 사용되고 이러한 메시지를 감지하는 규칙이 정의됩니다. 메시지를 스팸으로 보고한 수신자의 이메일 주소가 격리 목록에 추가됩니다.

* **거부됨** 및 **하드** 유형으로 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]**&#x200B;에 바운스 메일 규칙 **Feedback_loop**&#x200B;을 만들거나 수정합니다.
* 피드백 루프를 위해 사서함이 특별히 정의된 경우 **[!UICONTROL Administration > Platform > External accounts]**&#x200B;에 새 외부 바운스 메일 계정을 만들어 액세스할 매개 변수를 정의합니다.

이 메커니즘은 불만 알림을 처리하는 즉시 작동합니다. 이 규칙이 제대로 작동하는지 확인하려면 계정을 일시적으로 비활성화하여 이러한 메시지를 수집하지 않도록 한 다음 피드백 루프 사서함의 내용을 수동으로 확인할 수 있습니다. 서버에서 다음 명령을 실행합니다.

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

여러 인스턴스에 대해 하나의 피드백 루프 주소를 사용해야 하는 경우 다음을 수행해야 합니다.

* 인스턴스가 있는 수만큼 사서함에서 받은 메시지를 복제합니다.
* 각 우편함을 한 번의 인스턴스씩 가져와야 합니다
* 관련 메시지만 처리하도록 인스턴스를 구성합니다.인스턴스 정보는 Adobe Campaign에서 보낸 메시지의 메시지 ID 헤더에 포함되므로 피드백 루프 메시지도 찾을 수 있습니다. 인스턴스 구성 파일에서 **checkInstanceName** 매개 변수를 지정하기만 하면 됩니다(기본적으로 인스턴스가 확인되지 않으며 이로 인해 특정 주소가 잘못 격리될 수 있음).

   ```
   <serverConf>
     <inMail checkInstanceName="true"/>
   </serverConf>
   ```

Adobe Campaign의 Deliverability Service는 다음 ISP에 대한 피드백 루프 서비스 구독을 관리합니다.AOL, BlueTie, Comcast, Cox, EarthLink, FastMail, Hotmail, HostedEmail, Libero, Mail.ru, MailTrust, OpenSRS, OpenQ, RoadRunner, Synacor, Telarry, UnitedOnline, USA, XS ALL, Yahoo, Yandex, Zoho

## 목록-가입 해지 {#list-unsubscribe}

### 목록-가입 해지 정보 {#about-list-unsubscribe}

최적의 배달 가능성 관리를 위해 **List-Unsubscribe**&#x200B;라는 SMTP 헤더를 추가해야 합니다.

이 헤더를 &quot;스팸으로 신고&quot; 아이콘의 대안으로 사용할 수 있습니다. 이메일 인터페이스에 구독 취소 링크로 표시됩니다.

이 기능을 사용하면 평판이 보호되고 피드백은 구독이 없는 것으로 실행됩니다.

>[!NOTE]
>
>이 기능은 빌드 6831에서 사용할 수 있습니다.

목록-가입 해지를 사용하려면 다음과 유사한 명령줄을 입력해야 합니다.

```
List-Unsubscribe: mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe
```

>[!IMPORTANT]
>
>위의 예는 수신자 테이블을 기반으로 합니다. 다른 테이블에서 데이터베이스 구현이 수행된 경우 올바른 정보로 명령줄을 다시 표기해야 합니다.

다음 명령줄을 사용하여 동적 **List-Unsubscribe**&#x200B;을 만들 수 있습니다.

```
List-Unsubscribe: mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%
```

Gmail, Outlook.com 및 Microsoft Outlook은 이 방법을 지원하고 구독 취소 단추는 인터페이스에서 직접 사용할 수 있습니다. 이 방법은 불만 사항을 줄여줍니다.

![](assets/s_tn_del_msn_unsubscribe_list.png)

![](assets/s_tn_del_gmail_unsubscribe_list.png)

다음과 같이 **List-Unsubscribe**&#x200B;을(를) 구현할 수 있습니다.

* 배달 템플릿에서 명령줄을 직접 추가합니다. [이 섹션](#adding-a-command-line-in-a-delivery-template),
* 또는 분류 규칙 만들기 - [이 섹션](#creating-a-typology-rule)을 참조하십시오.

### 배달 템플릿 {#adding-a-command-line-in-a-delivery-template}에 명령줄 추가

이메일의 SMTP 헤더의 추가 섹션에 명령줄을 추가해야 합니다.

이 추가 작업은 각 이메일 또는 기존 배달 템플릿에서 수행할 수 있습니다. 이 기능을 포함하는 새 배달 템플릿을 만들 수도 있습니다.

### 유형화 규칙 만들기 {#creating-a-typology-rule}

규칙에는 명령줄을 생성하는 스크립트가 포함되어야 하며 이 스크립트는 이메일 헤더에 포함되어야 합니다.

>[!NOTE]
>
>다음과 같은 유형 규칙을 만드는 것이 좋습니다.목록 구독 취소 기능은 각 이메일에 자동으로 추가됩니다.

1. 목록 구독 취소:&lt;mailto:unsubscribe@domain.com>

   **가입 해지** 링크를 클릭하면 사용자의 기본 이메일 클라이언트가 열립니다. 이 유형 규칙을 이메일을 만드는 데 사용되는 유형 분석에 추가해야 합니다.

1. 목록 구독 취소:`<https://domain.com/unsubscribe.jsp>`

   **가입 해지** 링크를 클릭하면 사용자가 구독 취소 양식으로 리디렉션됩니다.

   예제:

   ![](assets/s_tn_del_unsubscribe_param.png)

## 이메일 최적화 {#email-optimization}

### SMTP {#smtp}

SMTP(Simple mail transfer protocol)는 이메일 전송을 위한 인터넷 표준입니다.

규칙에서 검사하지 않는 SMTP 오류는 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Delivery log qualification]** 폴더에 나열됩니다. 이러한 오류 메시지는 기본적으로 연결할 수 없는 소프트 오류로 해석됩니다. SMTP 서버의 피드백을 올바르게 검증하려면 가장 일반적인 오류를 식별하고 해당 규칙을 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Mail rule sets]**&#x200B;에 추가해야 합니다. 이 옵션을 사용하지 않으면 플랫폼에서 불필요한 재시도를 하거나(알 수 없는 사용자의 경우) 지정된 테스트 수 이후에 특정 받는 사람을 격리 대상으로 잘못 지정합니다.

### 전용 IP {#dedicated-ips}

Adobe은 명성을 구축하고 전달 성능을 최적화하기 위해 각 고객에게 구현 IP를 제공하는 전용 IP 전략을 제공합니다.

## IP 인증 {#ip-certification}

IP 인증은 스팸 방지 필터 또는 기타 이메일 차단 시스템에 의해 차단되지 않고 이메일을 수신하도록 돕는 전송 우수 사례 프로그램입니다.

현재 두 개의 공급업체에서 IP 인증을 제공합니다.반환 경로 및 인증된 보낸 사람 연합.

인증된 전송자는 글로벌 사서함 공급자 및 이메일 보안 회사가 사용하는 이메일 허용 목록에 추가됩니다. 이러한 상업용 허용 목록은 발신자가 스팸 방지 필터를 모두 우회하거나 시스템에 들어갈 때 증분 포인트를 할당할 수 있는 시스템을 기반으로 합니다.

[Return Path Certification](https://www.validity.com/products/returnpath/certification/) 프로그램은 다음을 포함한 다양한 혜택을 제공합니다.

* Microsoft, AOL, Yahoo, Gmail, Comcast, Orange, Mail.ru와 같은 주요 사서함 제공업체에서 상당한 양의 받은 편지함 배치 증가
* Cloudmark, SpamAssist 및 Cisco Ironport와 같은 중요한 필터에서 평판 및 대우에 부합하는 요소
* 24x7 모니터링 전담 규정 준수 팀 보안 경고를 제공하고 어떠한 타협도 해결할 수 있도록 귀사와 협력하고 있습니다.
* KPI, 배치 및 인증 성능에 대한 자세한 정보를 제공하는 사서함 공급자 데이터
* 새로운 IP 주소를 마이그레이션 또는 획득할 때 높은 명성과 인식을 포함하여, 간소화되고 빠른 IP 온난화

[인증된 보낸 사람 제휴](https://certified-senders.org/certification-process/) 인증은 다음과 같은 여러 가지 이점을 제공합니다.

* 고품질 표준을 준수하는 상업용 이메일 전송자 인증
* 받은 편지함 배치 비율을 늘리고 스팸 필터링을 줄이기 위해 상업용 이메일의 전달 및 전달 기능이 개선되었습니다.
* 법률 표준을 완벽하게 준수하여 법적 및 재정적 위험으로부터 보호
* CSA 불만 접수 및 일일 스팸 트랩 보고서로부터 조기 경고를 통해 평판 보호

ISP는 이러한 서비스를 무료로 사용할 수 있으며 ISP의 수는에 따라 허용 목록에 추가하다 다를 수 있습니다.

그러나 ISP가 메시지 내용 자체를 분석하지 않고 각 받은 편지함 소유자의 행동을 기반으로 스팸 방지 필터를 만드는 경우가 많기 때문에 IP 인증을 사용하는 것은 받은 편지함 배치 또는 전달을 보장하는 것은 아닙니다.
