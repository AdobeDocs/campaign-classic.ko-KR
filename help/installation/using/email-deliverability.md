---
title: 이메일 전달
seo-title: 이메일 전달
description: 이메일 전달
seo-description: null
page-status-flag: never-activated
uuid: 983aec6b-60f6-4c9b-a75a-1693958626c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 86c18986-1f65-40ff-80dc-1fbff37f406d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 21d808695bfde2fb3220964c066558ad30952443

---


# 이메일 전달{#email-deliverability}

## 개요 {#overview}

다음 섹션에서는 메시지를 전달할 때 Adobe Campaign 인스턴스의 출력을 제어하는 데 필요한 구성에 대한 개요를 제공합니다.

>[!NOTE]
>
>일부 구성은 Adobe가 호스팅하는 배포를 위해서만 수행할 수 있습니다. 예를 들어 서버 및 인스턴스 구성 파일에 액세스하려면 다른 배포에 대한 자세한 내용은 호스팅 모델 [섹션](../../installation/using/hosting-models.md) 또는 [이 문서를](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)참조하십시오.\
>제공 능력과 관련된 개념과 모범 사례를 설명하는 [시작 안내서를](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) 참조하십시오.

제공 능력과 관련된 개념과 우수 사례에 대한 자세한 내용은 이 [섹션을](../../delivery/using/about-deliverability.md)참조하십시오.

Adobe Campaign 플랫폼이 메시지를 효율적으로 전송하고 수신하는 것과 관련된 모든 기술 권장 사항은 이 [섹션에](../../delivery/using/technical-recommendations.md)있습니다.

## 운영 원칙 {#operating-principle}

도메인에 따라 전송되는 이메일 수를 제한하기 위해 하나 이상의 Adobe Campaign 인스턴스의 출력을 제어할 수 있습니다. 예를 들어, 다른 모든 도메인에 대해 시간당 100,000개의 메시지를 구성하는 동안 **yahoo.com** 주소에 대해 출력을 시간당 20,000으로 제한할 수 있습니다.

메시지 출력을 배달 서버(**mta**)에서 사용하는 각 IP 주소에 대해 제어해야 합니다. 여러 **대의** 시스템으로 분류되고 다양한 Adobe Campaign 인스턴스에 속한 여러 개의 데이터가 이메일 전달에 대해 동일한 IP 주소를 공유할 수 있습니다.이 IP 주소의 사용을 조정하기 위해 프로세스를 설정해야 합니다.

통계 **모듈이** 수행하는 작업은 다음과 같습니다.IP 주소 집합에 대해 메일 서버로 보낼 모든 연결 요청 및 메시지를 전달합니다. 통계 서버는 게재 추적을 유지하며 설정된 할당량에 따라 전송을 활성화하거나 비활성화할 수 있습니다.

![](assets/s_ncs_install_mta.png)

* 통계 서버(**통계**)는 Adobe Campaign 베이스에 연결되어 구성을 로드합니다.
* 배달 서버(**mta**)는 UDP를 사용하여 자신의 인스턴스에 항상 속하지 않는 통계 서버에 연결합니다.

### 배달 서버 {#delivery-servers}

mta **모듈은** 해당 하위 모듈에 메시지를 **배포합니다** . 각 **필드는** 통계 서버에서 승인을 요청하고 보내기 전에 메시지를 준비합니다.

단계는 다음과 같습니다.

1. mta **는** 자격 조건을 갖춘 메시지를 선택하고 사용 가능한 **일치하는 항목을 할당합니다**.
1. 이 **항목은** 메시지 작성에 필요한 모든 정보(컨텐츠, 개인화 요소, 첨부 파일, 이미지 등)를 로드합니다. 메시지를 이메일 트래픽 **표시기로 전달합니다**.
1. 이메일 트래픽 셰이프가 통계 서버의 권한(**smtp 상태**)을 받자마자 메시지가 수신자에게 전송됩니다.

![](assets/s_ncs_install_email_traffic_shaper.png)

### 이메일 서버 통계 및 제한 사항 {#email-server-statistics-and-limitations}

통계 서버는 메시지를 수신하는 각 이메일 서버에 대해 다음 통계를 유지합니다.

* 열려 있는 시점 연결 수,
* 지난 1시간 동안 보낸 메시지 수,
* 성공/거부된 연결 비율,
* 연결할 수 없는 서버에 대한 연결 비율입니다.

동시에 모듈은 특정 이메일 서버에 대한 제한 목록을 로드합니다.

* 최대 동시 연결 수,
* 시간당 최대 메시지 수,
* 연결당 최대 메시지 수입니다.

### IP 주소 관리 {#managing-ip-addresses}

통계 서버는 동일한 공개 IP 주소로 여러 인스턴스 또는 여러 컴퓨터를 결합할 수 있습니다. 따라서 특정 인스턴스에는 연결되지 않지만, 도메인당 제한을 복구하려면 인스턴스에 연결해야 합니다.

각 대상 MX 및 각 소스 IP에 대한 배달 통계가 유지됩니다. 예를 들어 타깃팅된 도메인에 5개의 MX가 있고 플랫폼에 3개의 서로 다른 IP 주소를 사용할 수 있는 경우 서버는 이 도메인에 대해 최대 15개의 지표 시리즈를 관리할 수 있습니다.

원본 IP 주소는 공개 IP 주소(즉, 원격 이메일 서버에서 보는 주소와 일치합니다. NAT 라우터가 제공되는 경우 이 IP 주소는 **데이터를**&#x200B;호스팅하는 시스템의 주소와 다를 수 있습니다. 통계 서버가 공용 IP(publicId)와 일치하는 식별자를 사용하는&#x200B;**이유입니다**. 로컬 주소와 이 식별자 간의 연결은 **serverConf.xml** 구성 파일에서 선언됩니다. serverConf.xml에서 사용할 수 있는 **모든 매개 변수가** 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열됩니다.

## 전달 출력 제어 {#delivery-output-controlling}

이메일 서버로 메시지를 전달하려면 이메일 트래픽 **공유** 구성 요소가 통계 서버로부터 연결을 요청합니다. 요청이 수락되면 연결이 열립니다.

메시지를 보내기 전에 모듈은 서버에서 &#39;토큰&#39;을 요청합니다. 이러한 토큰은 일반적으로 서버에 대한 쿼리 수를 줄이는 10개 이상의 토큰 세트입니다.

서버는 연결 및 게재와 관련된 모든 통계를 저장합니다. 재부팅할 경우 정보가 일시적으로 손실됩니다.각 클라이언트는 전송 통계의 로컬 복사본을 보관하고 정기적으로(2분마다) 서버로 반환합니다. 그런 다음 서버가 데이터를 다시 집계할 수 있습니다.

다음 섹션에서는 이메일 트래픽 셰이퍼 구성 요소의 메시지 처리에 대해 **설명합니다** .

### 메시지 전달 {#message-delivery}

메시지가 전송되면 세 가지 가능한 결과가 있습니다.

1. **성공**:메시지가 전송되었습니다. 메시지가 업데이트됩니다.
1. **메시지 실패**:연결된 서버에서 선택한 받는 사람에 대한 메시지를 거부했습니다. 이 결과는 반환 코드 550~599와 일치하지만 예외를 정의할 수 있습니다.
1. **세션 실패** (5.11 이상):mta **가** 이 메시지에 대한 답변을 받으면 메시지가 중단됩니다(메시지 포기 [참조](#message-abandonment)). 다른 경로를 사용할 수 없는 경우 메시지가 다른 경로로 전송되거나 보류 중으로 [설정됩니다](#message-pending).

   >[!NOTE]
   >
   >경로는 **Adobe Campaign** mta와 대상 **mta** 간의 **연결입니다**. Adobe Campaign **mta** 는 여러 시작 IP 및 여러 대상 도메인 IP에서 선택할 수 있습니다.

### 메시지 포기 {#message-abandonment}

중단된 메시지는 **mta로** 반환되며 더 이상 matchild에서 관리하지 **않습니다**.

이 **메시지는** 복구, 포기, 격리 등 이 메시지의 절차를 결정합니다. 응답 코드와 규칙에 따라 다릅니다.

### 메시지 보류 중 {#message-pending}

메시지가 활성 대기열에 도달해도 사용할 수 있는 경로가 없으면 보류 상태가 됩니다.

일반적으로 경로는 연결 오류 후 가변 시간에 대해 사용할 수 없는 것으로 표시됩니다. 사용 불능 기간은 오류 빈도와 기간에 따라 다릅니다.

## 통계 서버 구성 {#statistics-server-configuration}

통계 서버는 다음과 같은 여러 인스턴스에서 사용할 수 있습니다.사용할 인스턴스와 별도로 구성해야 합니다.

구성을 호스팅할 Adobe Campaign 데이터베이스를 정의하여 시작합니다.

### 구성 시작 {#start-configuration}

기본적으로 **통계** 모듈은 각 인스턴스에 대해 시작됩니다. 인스턴스가 동일한 시스템에서 상호 구성되거나 인스턴스가 동일한 IP 주소를 공유하는 경우 단일 통계 서버가 사용됩니다.다른 사람들은 장애인이 되어야 합니다.

### 서버 포트 정의 {#definition-of-the-server-port}

기본적으로 통계 서버는 포트 7777에서 수신합니다. 이 포트는 serverConf. **xml** 파일에서 수정할 수 있습니다. serverConf.xml에서 사용할 수 있는 **모든 매개 변수가** 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열됩니다.

```
<stat port="1234"/>
```

## MX 구성 {#mx-configuration}

### MX 규칙 정보 {#about-mx-rules}

MX 규칙(Mail Xchanger)은 송신 서버와 수신 서버 간의 통신을 관리하는 규칙입니다.

>[!IMPORTANT]
>
>호스팅 또는 하이브리드 설치의 경우 향상된 MTA로 업그레이드한 경우 더 이상 **[!UICONTROL MX management]** 배달 처리량 규칙이 사용되지 않습니다. Enhanced MTA는 고유한 MX 규칙을 사용하여 사용자의 이전 이메일 명성에 따라 도메인별로 처리량을 사용자 정의하고 이메일을 전송하는 도메인에서 오는 실시간 피드백을 제공합니다.
>
>Adobe Campaign 향상된 MTA에 대한 자세한 내용은 이 [문서를](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html)참조하십시오.

이러한 규칙은 클라이언트 인스턴스를 정기적으로 제공하기 위해 매일 아침 6AM(서버 시간)에 자동으로 다시 로드됩니다.

자재 용량 및 내부 정책에 따라 ISP는 시간당 사전 정의된 연결 및 메시지 수를 수락합니다. 이러한 변수는 IP 및 전송 도메인의 평판에 따라 ISP 시스템에서 자동으로 수정할 수 있습니다. Adobe Campaign은 제공 플랫폼을 통해 ISP에서 150개 이상의 특정 규칙을 관리하며, 다른 도메인에 대한 하나의 일반 규칙을 관리합니다.

최대 연결 수는 MTA에서 사용하는 공개 IP 주소 수에만 의존하지 않습니다.

예를 들어, MX 규칙에서 5개의 연결을 허용했고 2개의 공개 IP를 구성한 경우 이 도메인에 동시에 열 수 있는 연결이 10개를 초과할 수 없다고 생각할 수 있습니다. 이는 사실이 아닙니다. 실제로 최대 연결 수는 MTA 공개 IP 중 하나와 클라이언트의 MTA의 공개 IP가 결합된 경로와 경로를 나타냅니다.

아래 예에서 사용자는 두 개의 공개 IP 주소를 구성했으며 도메인은 yahoo.com입니다.

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

yahoo.com의 MX 기록에 따르면 yahoo.com은 3개의 메일 교환기를 가지고 있다고 합니다. 피어 메일 교환기를 연결하려면 MTA가 DNS에서 IP 주소를 요청합니다.

```
user:~ user$ host -t a mta5.am0.yahoodns.net
                mta5.am0.yahoodns.net has address 98.136.216.26
                mta5.am0.yahoodns.net has address 98.136.217.202
                mta5.am0.yahoodns.net has address 98.138.112.38
                mta5.am0.yahoodns.net has address 66.196.118.37
                mta5.am0.yahoodns.net has address 63.250.192.46
                mta5.am0.yahoodns.net has address 66.196.118.240
                mta5.am0.yahoodns.net has address 98.136.217.203
                mta5.am0.yahoodns.net has address 98.138.112.35
```

이 레코드의 경우 사용자는 8개의 피어 IP 주소에 연결할 수 있습니다. 2개의 공개 IP 주소가 있으므로 yahoo.com 메일 서버에 연결하기 위해 8 * 2 = 16개의 조합을 제공합니다. 이러한 각 조합을 경로라고 합니다.

두 번째 MX 레코드는 다음과 같이 나타납니다.

```
user:~ user$ host -t a mta6.am0.yahoodns.net
                mta6.am0.yahoodns.net has address 98.138.112.38
                mta6.am0.yahoodns.net has address 98.136.216.26
                mta6.am0.yahoodns.net has address 63.250.192.46
                mta6.am0.yahoodns.net has address 66.196.118.35
                mta6.am0.yahoodns.net has address 98.136.217.203
                mta6.am0.yahoodns.net has address 98.138.112.32
                mta6.am0.yahoodns.net has address 98.138.112.37
                mta6.am0.yahoodns.net has address 66.196.118.33
```

이 8개의 IP 주소 중 4개가 mta5(98.136.216.26, 98.138.112.38, 63.250.192.46 및 98.136.217.203)에서 이미 사용되고 있습니다. 이 레코드를 사용하면 4개의 새 IP 주소를 사용할 수 있습니다. 세 번째 MX 레코드도 마찬가지입니다.

총 16개의 원격 IP 주소가 있습니다. 2개의 로컬 공개 IP와 결합하여 yahoo.com 메일 서버에 연결할 수 있는 32개의 경로가 있습니다.

>[!NOTE]
>
>2개의 MX 레코드가 동일한 IP 주소를 참조하고 있는 경우 이 IP는 1개의 경로로 계산되며 2가 아닙니다.

다음은 MX 규칙 사용에 대한 몇 가지 예입니다.

![](assets/s_ncs_examples_mx_rules.png)

아래 예에서, 사용자는 특정 도메인에 대해 시간당 10,000개의 메시지 제한이 있지만 MTA 처리량 용량은 이 제한보다 높습니다.

이 경우 트래픽은 12시간 동안 5분으로 나누며 실제 제한은 기간당 833개의 메시지입니다.

이러한 메시지는 최대한 빨리 배달됩니다.

![](assets/s_ncs_traffic_shaping.png)

### MX 관리 구성 {#configuring-mx-management}

MX에 대해 준수해야 하는 규칙은 트리 **[!UICONTROL MX management]** 노드의 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** 문서에 정의되어 있습니다.

노드에 **[!UICONTROL MX management]** 문서가 없으면 수동으로 만들 수 있습니다. 이렇게 하려면:

1. 새 메일 규칙 세트를 만듭니다.
1. 모드를 **[!UICONTROL MX management]** 선택합니다.

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. **필드에 defaultMXRules** **[!UICONTROL Internal name]** 를 입력합니다.

변경 사항을 고려하려면 통계 서버를 다시 시작해야 합니다.

통계 서버를 다시 시작하지 않고 구성을 다시 로드하려면 서버를 호스팅하는 컴퓨터에서 다음 명령을 사용합니다. `nlserver stat -reload`

>[!NOTE]
>
>이 명령줄은 서버를 다시 **시작하는**&#x200B;것이 좋습니다. 따라서 다시 시작하기 전에 수집된 통계가 유실되는 것을 방지하고 MX 규칙에 정의된 할당량에 따라 사용할 수 있는 최고점을 방지합니다.

### MX 규칙 구성 {#configuring-mx-rules}

MX 규칙에 연결된 모든 도메인이 **[!UICONTROL MX management]** 문서에 나열됩니다.

이러한 규칙은 순서대로 적용됩니다.대상 MX와 호환되는 MX 마스크의 첫 번째 규칙이 적용됩니다.

각 규칙에 사용할 수 있는 매개 변수는 다음과 같습니다.

* **[!UICONTROL MX mask]**:규칙이 적용되는 도메인. 각 규칙은 MX의 주소 마스크를 정의합니다. 따라서 이 마스크와 이름이 일치하는 모든 MX를 사용할 수 있습니다. 마스크에는 &quot;*&quot; 및 &quot;?&quot;가 포함될 수 있습니다. 일반 문자.

   예를 들어, 다음 주소가 있습니다.

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com
   는 다음 마스크와 호환됩니다.

   * *.yahoo.com
   * ?.mx.yahoo.com
   예를 들어 이메일 주소 foobar@gmail.com의 경우 도메인은 gmail.com이고 MX 레코드는 다음과 같습니다.

   ```
   gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
   ```

   이 경우 MX 규칙이 `*.google.com` 사용됩니다. 보시다시피 MX 규칙 마스크가 메일에 있는 도메인과 반드시 일치하지 않습니다. gmail.com 이메일 주소에 적용되는 MX 규칙은 마스크가 있는 규칙이 `*.google.com`됩니다.

* **[!UICONTROL Range of identifiers]**:이 옵션을 사용하면 규칙이 적용되는 식별자(publicID)의 범위를 표시할 수 있습니다. 다음을 지정할 수 있습니다.

   * 숫자:규칙은 이 publicId에만 적용됩니다.
   * 숫자 범위(**number1-number2**):이 규칙은 이 두 숫자 사이의 모든 publicIds에 적용됩니다.
   >[!NOTE]
   >
   >필드가 비어 있으면 규칙은 모든 식별자에 적용됩니다.

   공용 ID는 하나 또는 여러 MTA에서 사용되는 공개 IP의 내부 식별자입니다. 이러한 ID는 **config-instance.xml** 파일의 MTA 서버에서 정의됩니다.

   ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**:이 MX 규칙의 속성 범위를 정의합니다. 이 확인란을 선택하면 모든 매개 변수가 인스턴스에서 사용 가능한 모든 IP에서 공유됩니다. 이 확인란을 선택하지 않으면 MX 규칙이 각 IP에 대해 정의됩니다. 최대 메시지 수에 사용 가능한 IP 수를 곱합니다.
* **[!UICONTROL Maximum number of connections]**:보낸 사람의 도메인에 대한 동시 연결의 최대 수입니다.
* **[!UICONTROL Maximum number of messages]**:연결 시 전송할 수 있는 최대 메시지 수입니다. 메시지가 이 수를 초과하면 연결이 닫히고 새 메시지가 열립니다.
* **[!UICONTROL Messages per hour]**:보낸 사람의 도메인으로 1시간 내에 보낼 수 있는 최대 메시지 수입니다.
* **[!UICONTROL Connection time out]**:도메인에 연결하기 위한 시간 임계값.

   >[!NOTE]
   >
   >Windows에서는 사용자의 Windows 버전에 따라 이 임계값 전에 **시간 초과를** 발행할 수 있습니다.

* **[!UICONTROL Timeout Data]**:메시지 내용을 보낸 후 최대 대기 시간(SMTP 프로토콜의 DATA 섹션)
* **[!UICONTROL Timeout]**:SMTP 서버와 다른 교환의 최대 대기 시간
* **[!UICONTROL TLS]**:이메일 제공을 암호화할 수 있는 TLS 프로토콜을 선택적으로 활성화할 수 있습니다. 각 MX 마스크에 대해 다음 옵션을 사용할 수 있습니다.

   * **[!UICONTROL Default configuration]**:적용되는 serverConf.xml 구성 파일에 지정된 일반 구성입니다.

      >[!CAUTION]
      >
      >기본 구성을 수정하지 않는 것이 좋습니다.

   * **[!UICONTROL Disabled]** :메시지는 암호화 없이 체계적으로 전송됩니다.
   * **[!UICONTROL Opportunistic]** :수신 서버(SMTP)가 TLS 프로토콜을 생성할 수 있는 경우 메시지 배달이 암호화됩니다.

구성 예:

![](assets/s_ncs_install_mx_mgt_rule_details.png)

### 이메일 포맷 관리 {#managing-email-formats}

보낸 메시지의 형식을 정의하여 각 받는 사람 주소의 도메인에 따라 표시되는 컨텐츠가 자동으로 조정되도록 할 수 있습니다.

이렇게 하려면 **[!UICONTROL Management of email formats]** > **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** 에 있는 문서로 이동합니다 **[!UICONTROL Mail rule sets]**.

이 문서에는 Adobe Campaign에서 관리하는 일본어 형식에 해당하는 사전 정의된 모든 도메인의 목록이 포함되어 있습니다. 자세한 내용은 [이 문서를](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles)참조하십시오.

![](assets/mail_rule_sets.png)

MIME **구조** (Multipurpose Internet Mail Extensions) 매개 변수를 사용하면 다른 메일 클라이언트로 보낼 메시지 구조를 정의할 수 있습니다. 다음 세 가지 옵션을 사용할 수 있습니다.

* **멀티파트**:메시지는 텍스트 또는 HTML 형식으로 전송됩니다. HTML 형식이 허용되지 않으면 메시지는 텍스트 형식으로 계속 표시될 수 있습니다.

   기본적으로 다중 부분 구조는 **다중 부분/대체**&#x200B;구조이지만 이미지가 메시지에 추가되면 자동으로 **다중 부분/관련성이** 됩니다. 특정 제공업체는 기본적으로 **다중 부분/관련** 형식을 예상하므로 **[!UICONTROL Force multipart/related]** 이 옵션을 사용하면 이미지가 연결되어 있지 않더라도 이 형식이 적용됩니다.

* **HTML**:HTML 전용 메시지가 전송됩니다. HTML 형식이 허용되지 않으면 메시지가 표시되지 않습니다.
* **텍스트**:텍스트 전용 형식의 메시지가 전송됩니다. 텍스트 형식 메시지의 장점은 크기가 작기 때문입니다.

이 **[!UICONTROL Image inclusion]** 옵션이 활성화되어 있으면 이메일 본문에 직접 표시됩니다. 이미지가 업로드되고 URL 링크가 해당 컨텐츠로 대체됩니다.

이 옵션은 특히 장식 메일 **, 데코어 메일**&#x200B;또는 데코레이션 메일에 **대한** 일본 시장에서 **사용됩니다**. 자세한 내용은 [이 문서를](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles)참조하십시오.

>[!CAUTION]
>
>이메일에 이미지를 삽입하면 크기가 크게 증가합니다.

## 배달 서버 구성 {#delivery-server-configuration}

### 클럭 동기화 {#clock-synchronization}

Adobe Campaign 플랫폼(데이터베이스 포함)을 구성하는 모든 서버의 클럭은 동기화되어야 하며 시스템은 동일한 시간대로 설정되어야 합니다.

### 통계 서버의 좌표 {#coordinates-of-the-statistics-server}

통계 서버의 주소는 **mta에 제공해야 합니다**.

구성의 **mta** 요소의 statServerAddress **** 속성을 사용하여 사용할 포트의 주소와 번호를 지정할 수 있습니다.

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

동일한 컴퓨터에서 통계 서버를 사용하려면 **localhost** 값이 있는 컴퓨터 이름을 하나 이상 입력해야 합니다.

```
 <mta statServerAddress="localhost">
```

>[!CAUTION]
>
>이 필드를 채우지 않으면 **mta** 가 시작되지 않습니다.

### 사용할 IP 주소 목록 {#list-of-ip-addresses-to-use}

트래픽 관리와 관련된 구성은 구성 파일의 **mta/child/smtp** 요소에 있습니다.

각 **IPAfrity** 요소에 대해 컴퓨터에 사용할 수 있는 IP 주소를 선언해야 합니다.

예:

```
<IPAffinity localDomain="<domain>" name="default">
  <IP address="192.168.0.11" publicId="1" weight="5"/>
  <IP address="192.168.0.12" heloHost="revdns1.campaign.com" publicId="2" weight="5"/>
  <IP address="192.168.0.13" publicId="3" weight="1"/>
</IPAffinity>
```

매개 변수는 다음과 같습니다.

* **주소**:이것은 사용할 MTA 호스트 시스템의 IP 주소입니다.
* **heloHost**:이 식별자는 SMTP 서버에서 볼 수 있는 IP 주소를 나타냅니다.

* **publicId**:이 정보는 NAT 라우터 뒤에 있는 여러 Adobe Campaign **태그가** IP 주소를 공유할 때 유용합니다. 통계 서버는 이 식별자를 사용하여 이 시작점과 대상 서버 사이의 연결을 기억하고 통계를 전송합니다.
* **두께**:주소의 사용 상대 빈도를 정의할 수 있습니다. 기본적으로 모든 주소의 가중치는 1입니다.

>[!NOTE]
>
>serverConf.xml 파일에서 하나의 IP가 고유 식별자(public_id)가 있는 단일 도움말 호스트에 해당하는지 확인해야 합니다. 여러 도움말 호스트에 매핑할 수 없으므로 배달 제한 문제가 발생할 수 있습니다.

앞의 예에서 일반적인 조건에서 주소는 다음과 같이 배포됩니다.

    * &quot;1&quot;: 5 / (5+5+1) = 45%
    * &quot;2&quot;: 5 / (5+5+1) = 45%
    * &quot;3&quot;: 1 / (5+5+1) = 10%

예를 들어, 지정된 MX에 첫 번째 주소를 사용할 수 없는 경우 다음과 같이 메시지가 전송됩니다.

    * &quot;2&quot;: 5 / (5+1) = 83%
    * &quot;3&quot;: 1 / (5+1) = 17%

* **includeDomain**:특정 도메인에 속하는 이메일에 대해 이 IP 주소를 예약할 수 있습니다. 하나 이상의 와일드카드(&#39;*&#39;)를 포함할 수 있는 마스크 목록입니다. 속성을 지정하지 않으면 모든 도메인이 이 IP 주소를 사용할 수 있습니다.

   예: **includeDomain=&quot;wanadoo.com,orange.com,yahoo.*&quot;**

* **excludeDomain**:이 IP 주소의 도메인 목록을 제외합니다. 이 필터는 **includeDomains 필터 다음에** 적용됩니다.

   ![](assets/s_ncs_install_mta_ips.png)

## 이메일 전송 최적화 {#email-sending-optimization}

Adobe Campaign의 내부 아키텍처는 **이메일** 제공을 최적화하기 위한 구성에 영향을 줍니다. 다음은 배송 개선에 대한 몇 가지 팁입니다.

### maxWaitingMessages 매개 변수 조정 {#adjust-the-maxwaitingmessages-parameter}

maxWaitingMessages **매개 변수는** 해당 필드가 미리 준비하는 최대 메시지 수를 **나타냅니다**. 메시지는 전송되거나 포기한 경우에만 이 목록에서 삭제됩니다.

이 매개 변수는 메시지를 도메인별로 정렬하지 않는 경우 매우 중요하며 특히 중요합니다.

maxWorkingSetMb **(256** ) 임계값에 도달하면 배달 서버가 메시지 전송을 중지합니다. 작업이 다시 시작될 때까지 성능이 **크게** 감소합니다. 이 문제를 방지하려면 maxWorkingSetMb **매개 변수의 임계값을 늘리거나** maxWaitingMessages **매개 변수의 임계값을 줄일 수** 있습니다.

maxWorkingSetMb **** 매개 변수는 최대 메시지 수에 평균 메시지 크기를 곱하고 결과에 2.5를 곱하여 경험적으로 계산됩니다.예를 들어 메시지의 평균 크기가 50kB이고 **maxWaitingMessages 매개 변수가** 1,000이면 사용된 메모리의 평균 크기는 125MB입니다.

### 일치 항목 수 조정 {#adjust-the-number-of-mtachild}

하위 수는 시스템의 프로세서 수를 초과할 수 없습니다(약). 1000 세션). 8개를 넘지 않는 것이 **좋습니다**. 그런 다음 **자식** (maxMsgPerChild ****)당 메시지 수를 늘려 충분한 수명을 제공할 수 있습니다.
