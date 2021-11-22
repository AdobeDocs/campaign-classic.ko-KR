---
product: campaign
title: Campaign 게재 설정 구성
description: Campaign 게재 설정을 구성하는 방법 알아보기
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 5%

---

# 게재 설정 구성 {#delivery-settings}

![](../../assets/v7-only.svg)

게재 매개 변수는 **serverConf.xml** 폴더를 입력합니다.

* **DNS 구성**: mta 모듈에서 MX 형식 DNS 쿼리에 응답하는 데 사용되는 DNS 서버의 게재 도메인 및 IP 주소(또는 호스트)를 지정합니다. **`<dnsconfig>`** 계속

   >[!NOTE]
   >
   >다음 **nameServers** 매개 변수는 Windows에서 설치하는 데 필수입니다. Linux에서 설치하려면 비워 두어야 합니다.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

요구 사항과 설정에 따라 다음 구성을 수행할 수도 있습니다. 구성 [SMTP 릴레이](#smtp-relay), 개수의 조정 [MTA 하위 프로세스](#mta-child-processes), [아웃바운드 SMTP 트래픽 관리](#managing-outbound-smtp-traffic-with-affinities).

## SMTP 릴레이 {#smtp-relay}

MTA 모듈은 SMTP 브로드캐스트(포트 25)의 기본 메일 전송 에이전트 역할을 합니다.

그러나 보안 정책에 필요한 경우 중계 서버로 바꿀 수 있습니다. 이 경우 글로벌 처리량은 릴레이 1이 됩니다(릴레이 서버 처리량이 Adobe Campaign 처리량보다 낮음).

이 경우 이러한 매개 변수는 **`<relay>`** 섹션을 참조하십시오. 메일을 전송하는 데 사용되는 SMTP 서버의 IP 주소(또는 호스트)와 관련 포트(기본적으로 25)를 지정해야 합니다.

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>이 운영 모드는 릴레이 서버 고유의 성능(지연, 대역폭...)으로 인해 처리량을 크게 줄일 수 있으므로 전송 시 심각한 제한 사항을 의미합니다. 또한, 동기 배달 오류(SMTP 트래픽 분석으로 검색됨)의 자격을 제한하며 릴레이 서버를 사용할 수 없는 경우에는 전송을 수행할 수 없습니다.

## MTA 하위 프로세스 {#mta-child-processes}

서버의 CPU 성능과 사용 가능한 네트워크 리소스에 따라 브로드캐스트 성능을 최적화하기 위해 하위 프로세스 수(기본적으로 maxSpareServer 2)를 제어할 수 있습니다. 이 구성은 **`<master>`** 각 개별 컴퓨터에서 MTA 구성의 섹션을 참조하십시오.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

또한 [이메일 전송 최적화](../../installation/using/email-deliverability.md#email-sending-optimization).

## 관심사가 있는 아웃바운드 SMTP 트래픽 관리 {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>선호도 구성은 한 서버에서 다른 서버로 일관되어야 합니다. 구성 변경 사항은 MTA를 실행하는 모든 애플리케이션 서버에서 복제되어야 하므로 선호도 구성을 위해 Adobe에 문의하는 것이 좋습니다.

IP 주소가 있는 관심사를 통해 아웃바운드 SMTP 트래픽을 개선할 수 있습니다.

그렇게 하려면 다음 단계를 적용합니다.

1. 에 관심사를 입력합니다. **`<ipaffinity>`** 섹션 **serverConf.xml** 파일.

   친화성 하나는 여러 다른 이름을 가질 수 있습니다. 구분하려면 **;** 문자.

   예제:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   관련 매개 변수를 보려면 **serverConf.xml** 파일.

1. 드롭다운 목록에서 친화성 선택을 활성화하려면 관련성 이름을 **IPAffness** 열거형.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >열거형은 다음에 자세히 설명되어 있습니다. [이 문서](../../platform/using/managing-enumerations.md).

   그런 다음 유형화에 대해 아래에 표시된 대로 사용할 친화성을 선택할 수 있습니다.

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >다음을 의미할 수도 있습니다 [게재 서버 구성](../../installation/using/email-deliverability.md#delivery-server-configuration).

**관련 항목**
* [기술 이메일 구성](email-deliverability.md)
* [Campaign으로 MX 서버 사용](using-mx-servers.md)
* [이메일 BCC 구성](email-archiving.md)
