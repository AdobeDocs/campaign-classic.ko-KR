---
solution: Campaign Classic
product: campaign
title: 캠페인 게재 설정 구성
description: 캠페인 게재 설정을 구성하는 방법에 대해 알아봅니다.
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 1%

---

# 배달 설정 구성 {#delivery-settings}

배달 매개 변수는 **serverConf.xml** 폴더에 구성해야 합니다.

* **DNS 구성**:MTA 모듈에서 MX 유형 DNS 쿼리에 응답하는 데 사용되는 DNS 서버의 배달 도메인 및 IP 주소(또는 호스트)를  **`<dnsconfig>`** 계속 지정합니다.

   >[!NOTE]
   >
   >**nameServers** 매개 변수는 Windows에서 설치하는 데 반드시 필요합니다. Linux에서 설치하려면 비워 두어야 합니다.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

필요에 따라 다음 구성을 수행할 수도 있습니다.[SMTP 릴레이](#smtp-relay)를 구성하고 [MTA 하위 프로세스](#mta-child-processes), [아웃바운드 SMTP 트래픽 관리](#managing-outbound-smtp-traffic-with-affinities) 수를 조정합니다.

## SMTP 릴레이 {#smtp-relay}

MTA 모듈은 SMTP 브로드캐스트(포트 25)에 대한 기본 메일 전송 에이전트 역할을 합니다.

그러나 보안 정책에 필요한 경우 릴레이 서버로 바꿀 수 있습니다. 이 경우, 글로벌 처리량은 릴레이 처리량이 됩니다(릴레이 서버 처리량이 Adobe Campaign 처리량보다 낮음).

이 경우 이러한 매개 변수는 **`<relay>`** 섹션에서 SMTP 서버를 구성하여 설정합니다. 메일 및 관련 포트(기본적으로 25개)를 전송하는 데 사용되는 SMTP 서버의 IP 주소(또는 호스트)를 지정해야 합니다.

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>이 운영 모드는 릴레이 서버 내부 성능(지연, 반밴드..)으로 인해 처리량을 크게 줄일 수 있으므로 배달 시 심각한 제한 사항을 의미합니다. 또한, SMTP 트래픽을 분석하여 감지된 동기 배달 오류를 평가할 수 있는 능력이 제한되며 릴레이 서버를 사용할 수 없을 경우 전송을 수행할 수 없습니다.

## MTA 하위 프로세스 {#mta-child-processes}

서버의 CPU 성능 및 사용 가능한 네트워크 리소스에 따라 브로드캐스트 성능을 최적화하기 위해 하위 프로세스(기본적으로 maxSpareServers) 수를 제어할 수 있습니다. 이 구성은 각 개별 컴퓨터에서 MTA 구성의 **`<master>`** 섹션에서 수행합니다.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

또한 [이메일 전송 최적화](../../installation/using/email-deliverability.md#email-sending-optimization)를 참조하십시오.

## {#managing-outbound-smtp-traffic-with-affinities} 친화성이 있는 아웃바운드 SMTP 트래픽 관리

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

**관련 항목**
* [기술 이메일 구성](email-deliverability.md)
* [Campaign에서 MX 서버 사용](using-mx-servers.md)
* [이메일 BCC 구성](email-archiving.md)
