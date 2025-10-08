---
product: campaign
title: 캠페인 게재 설정 구성
description: Campaign 게재 설정을 구성하는 방법 알아보기
feature: Installation, Channel Configuration
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: 28279c6ec0eab7f914cf6107cd1ec1cebd05113d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 5%

---

# 게재 설정 구성 {#delivery-settings}



**serverConf.xml** 폴더에 게재 매개 변수를 구성해야 합니다.

* **DNS 구성**: **`<dnsconfig>`**&#x200B;부터 MTA 모듈에서 만든 MX 형식 DNS 쿼리에 응답하는 데 사용되는 DNS 서버의 배달 도메인과 IP 주소(또는 호스트)를 지정합니다.

  >[!NOTE]
  >
  >**nameServers** 매개 변수는 Windows에서 설치하는 데 필수적입니다. Linux에서 설치하는 경우 비워 두어야 합니다.

  ```
  <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
  ```

필요에 따라 다음과 같은 구성을 수행할 수도 있습니다. [SMTP 릴레이](#smtp-relay)를 구성하고, [MTA 하위 프로세스 수를 조정](#mta-child-processes), [아웃바운드 SMTP 트래픽 관리](#managing-outbound-smtp-traffic-with-affinities).

## SMTP 릴레이 {#smtp-relay}

MTA 모듈은 SMTP 브로드캐스트(포트 25)에 대한 기본 메일 전송 에이전트 역할을 합니다.

그러나 보안 정책에서 요구하는 경우 중계 서버로 대체할 수 있습니다. 이 경우, 글로벌 스루풋은 (중계 서버 스루풋이 Adobe Campaign 스루풋보다 열등한 경우에 한하여) 중계 스루풋이 될 것이다.

이 경우 이러한 매개 변수는 **`<relay>`** 섹션에서 SMTP 서버를 구성하여 설정합니다. 메일을 전송하는 데 사용되는 SMTP 서버의 IP 주소(또는 호스트) 및 관련 포트(기본적으로 25)를 지정해야 합니다.

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>이 작동 모드는 릴레이 서버 고유의 성능(지연, 대역폭 등)으로 인해 처리량을 크게 줄일 수 있으므로 게재에 심각한 제한을 의미합니다. 또한 동기 게재 오류(SMTP 트래픽 분석으로 검색됨)를 검증하는 용량이 제한되며 릴레이 서버를 사용할 수 없는 경우 전송할 수 없습니다.

## MTA 하위 프로세스 {#mta-child-processes}

서버의 CPU 성능과 사용 가능한 네트워크 리소스에 따라 브로드캐스트 성능을 최적화하기 위해 하위 프로세스(기본적으로 maxSpareServers 2) 수를 제어할 수 있습니다. 이 구성은 각 개별 컴퓨터에 있는 MTA 구성의 **`<master>`** 섹션에서 이루어집니다.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

[전자 메일 전송 최적화](../../installation/using/email-deliverability.md#email-sending-optimization)도 참조하세요.

## 관심도를 포함한 아웃바운드 SMTP 트래픽 관리 {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>선호도 구성은 한 서버에서 다른 서버로 일관되어야 합니다. 구성 변경 사항은 MTA를 실행하는 모든 애플리케이션 서버에서 복제되어야 하므로 선호도 구성을 위해 Adobe에 문의하는 것이 좋습니다.

IP 주소를 사용하여 선호도를 통해 아웃바운드 SMTP 트래픽을 개선할 수 있습니다.

그렇게 하려면 다음 단계를 적용합니다.

1. **`<ipaffinity>`** serverConf.xml **파일의** 섹션에 선호도를 입력하십시오.

   하나의 관심도에 여러 가지 이름이 있을 수 있습니다. 이름을 구분하려면 **;** 문자를 사용하십시오.

   예:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   관련 매개 변수를 보려면 **serverConf.xml** 파일을 참조하십시오.

1. 드롭다운 목록에서 선호도 선택을 활성화하려면 **IPAffinity** 열거형에 선호도 이름을 추가해야 합니다.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >**Adobe Campaign v8(콘솔) 설명서**&#x200B;에서 [열거형으로 작업](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}하는 방법에 대해 자세히 알아보세요.


   그런 다음 유형화에 대해 아래에 표시된 대로 사용할 선호도를 선택할 수 있습니다.

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >[게재 서버 구성](../../installation/using/email-deliverability.md#delivery-server-configuration)도 참조할 수 있습니다.

**관련 항목**
* [기술 이메일 구성](email-deliverability.md)
* [Campaign으로 MX 서버 사용](using-mx-servers.md)
* [이메일 BCC 구성](email-archiving.md)
