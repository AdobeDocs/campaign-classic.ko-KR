---
product: campaign
title: Campaign으로 MX 서버 사용
description: MX 서버가 Adobe Campaign Classic에서 작동하는 방식을 알아봅니다.
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 1%

---

# Campaign으로 MX 서버 사용 {#using-mx-servers}

![](../../assets/v7-only.svg)

MX 서버가 Adobe Campaign Classic에서 작동하는 방식을 알아봅니다.

## MX 서버 {#mx-servers}

### MX 서버란 무엇입니까?

MX 레코드(메일 교환기 레코드)는 도메인을 대신하여 전자 메일 메시지를 수락하는 메일 서버를 지정하는 DNS(도메인 이름 시스템)의 리소스 레코드 유형입니다.

### MX 서버는 어떻게 작동합니까?

전자 메일을 보낼 때 소프트웨어 서버는 수신자 도메인 서버와 연결을 설정합니다. 두 서버 간의 통신에서 SMTP 언어를 사용하고 도메인은 둘 이상의 MX 서버를 가질 수 있습니다. 이 도메인에 대한 연결은 우선 순위가 가장 높은(가장 작은 그림)부터 시작되고 다른 서버는 &quot;백업&quot; 서버라고 합니다. 연결 프로토콜은 준수해야 합니다.

### MX 서버는 Adobe Campaign과 어떻게 작동합니까?

접속 프로토콜에서는 서버 편입 및 독점 방지를 위해 규칙을 준수해야 한다. 가장 중요한 것은 다음과 같습니다.

* **허용되는 최대 연결 수**: 이 번호가 존중되면 IP가에 차단 목록 없고 추가 연결로 인해 이메일이 거부되지 않습니다.
* **최대 메시지** 수: 연결 중에 보낼 수 있는 메시지 수를 정의해야 합니다. 이 번호가 정의되지 않으면 서버는 가능한 한 많이 전송합니다. 이렇게 되면 ISP가 분기로 식별하여에 차단 목록 추가됩니다.
* **시간당 메시지**: 평판과 일치하도록 Adobe Campaign은 IP가 시간당 전송할 수 있는 이메일 수를 제어합니다. 이 시스템은 이메일 거부 또는에 대해 사용자를 차단 목록 보호합니다.

## 인바운드 전자 메일

### Inbounce 이메일이란 무엇입니까?

Adobe Campaign이 서버 통신 중에 오류를 처리하는 데 사용하는 프로세스입니다.

### 인바운드 전자 메일은 어떻게 작동합니까?

오류 주소는 ISP에서 다시 보낸 바운스를 처리합니다. 프로세스는 다양한 SMTP 오류 코드를 분석하고 RegEx 표준에 따라 올바른 작업을 적용합니다.

예를 들어, 이메일 주소에는 ISP가 보낸 피드백 &quot;550 사용자 알 수 없음&quot;이 있습니다. 이 오류 코드는 Adobe Campaign 오류 주소(반환 경로 주소)에 의해 처리됩니다. 그러면 이 오류가 RegEx 표준과 비교되고 올바른 규칙이 적용됩니다. 이메일은 *하드 바운스*(유형과 일치), *사용자 알 수 없음*(이유와 일치)으로 간주되며 시스템에 첫 번째 루프가 발생한 후 격리됩니다.

### Adobe Campaign은 어떻게 관리합니까?

Adobe Campaign은 오류 유형과 이유 간의 일치로 이 프로세스를 관리합니다.

* **[!UICONTROL User Unknown]**: 문법적으로 올바르지만 존재하지 않는 주소입니다. 이 오류는 하드 바운스로 분류되고 첫 번째 오류 내에서 격리됩니다.
* **[!UICONTROL Mailbox full]**: 최대 용량에 도달한 사서함입니다. 이 오류는 사용자가 이 사서함을 더 이상 사용하지 않고 있음을 나타낼 수도 있습니다. 이 오류는 소프트 바운스로 분류되고, 세 번째 오류 내에 격리되고, 30일 후에 격리에서 제거됩니다.
* **[!UICONTROL Inactive User]**: 지난 6개월 동안 비활성 사용자로 인해 ISP에서 사서함을 비활성화했습니다. 이 오류는 소프트 바운스로 분류되고 세 번째 오류 내에서 격리됩니다.
* **[!UICONTROL Invalid domain]**: 전자 메일 주소의 도메인이 없습니다. 이 오류는 소프트 바운스로 분류되고 세 번째 오류 내에서 격리됩니다.
* **[!UICONTROL Refused]**: ISP가 사용자에게 이메일을 배달하지 않기로 했습니다. 이 오류는 소프트 바운스로 분류되며 오류가 이메일 주소에 연결되어 있지 않지만 IP 또는 도메인 평판에 연결되어 있으므로 격리에 푸시되지 않습니다.

>[!NOTE]
>
>게재 실패 유형 및 이유에 대한 자세한 내용은 이 [섹션](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)을 참조하십시오.

## 게재 가능성 인스턴스

MX 규칙 및 인바운드 규칙의 일별 업데이트는 이러한 규칙의 게재 가능성 인스턴스 소유자에게 연결된 클라이언트 인스턴스의 특정 워크플로우에서 관리합니다.

이 일별 업데이트는 투명도 프로세스를 통해 인스턴스를 최신 상태로 유지하려는 모든 클라이언트에 대해 실행됩니다.

MX 규칙에는 주로 램프 업 프로세스 중에 사용되는 6가지 서로 다른 수준의 처리량이 있습니다.

![](assets/mx-rules-throughput.png)

사용자 지정 모드는 자체 MX 규칙을 설정하려는 고급 클라이언트를 위한 것입니다. 사용자 지정 모드가 활성화되면 동기화가 꺼질 때 클라이언트가 게재 기능 인스턴스에 의해 업데이트되지 않습니다.

## 바운스 예

* **사용자 알 수 없음** (하드 바운스): 550 5.1.1.. 알 수 없는 {mx003} 사용자입니다.
* **사서함 가득 참** (소프트 바운스): 550 5.2.2 사용자 할당량이 초과됨
* **비활성 사서함** (소프트 바운스): 550 5.7.1 : 받는 사람 주소 거부: 비활성 MailBox, 6개월 이상 채우지 않음
* **도메인이 잘못되었습니다** (소프트 바운스). &#39;ourdan.com&#39;에 대한 DNS 쿼리가 실패했습니다.
* **거절됨** (소프트 바운스): 인바운드 전자 메일 바운스(규칙 &#39;Feedback_loop_Hotmail&#39;이 바운스와 일치함)
* **연결할 수 없음** (소프트 바운스): 421 4.16.55  [TS01]  x.x.x의 메시지는 과도한 사용자 불만 때문에 일시적으로 지연되었습니다

**관련 항목:**
* [MX 구성](../../installation/using/email-deliverability.md#mx-configuration)
* [기술 전자 메일 구성](../../installation/using/email-deliverability.md)
* [게재 실패 이해](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic - 기술 Recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/product-specific-resources/campaign/acc-technical-recommendations.html)
