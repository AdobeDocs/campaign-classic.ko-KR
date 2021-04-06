---
solution: Campaign Classic
product: campaign
title: Campaign에서 MX 서버 사용
description: MX 서버가 Adobe Campaign Classic과 작동하는 방법을 알아봅니다.
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
translation-type: tm+mt
source-git-commit: 3b5a6e6f03d9cb26ed372c3df069cbada36756a2
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 0%

---

# 캠페인 {#using-mx-servers}에서 MX 서버 사용

MX 서버가 Adobe Campaign Classic과 작동하는 방법을 알아봅니다.

## MX 서버 {#mx-servers}

### MX 서버란?

MX 레코드(메일 교환기 레코드)는 도메인 대신 이메일 메시지를 수락하는 메일 서버를 지정하는 DNS(도메인 이름 시스템)의 리소스 레코드 유형입니다.

### MX 서버는 어떻게 작동합니까?

이메일을 보내면 소프트웨어 서버가 받는 사람 도메인 서버와 연결을 설정합니다. 두 서버 간의 통신에서 SMTP 언어를 사용하고 도메인은 둘 이상의 MX 서버를 가질 수 있습니다. 이 도메인에 대한 연결은 가장 높은 우선 순위(최소 그림)에서 시작되며 다른 서버를 &quot;백업&quot; 서버라고 합니다. 연결 프로토콜을 반드시 준수해야 합니다.

### MX 서버는 Adobe Campaign과 어떻게 작동합니까?

접속 프로토콜에서는 서버 스팸, 독점 방지를 위해 규칙을 존중해야 한다. 가장 중요한 것은 다음과 같습니다.

* **허용되는 최대 연결 수**:이 번호가 유효하면 IP가에 차단 목록 없고 추가 연결로 인해 이메일이 거부되지 않습니다.
* **최대 메시지** 수:연결 중에 보낼 수 있는 메시지 수를 정의해야 합니다. 이 번호가 정의되지 않은 경우 서버는 가능한 한 많은 수를 전송합니다. 이렇게 하면 ISP에서 스팸으로 식별되고에 차단 목록 추가됩니다.
* **시간당 메시지**:e-신뢰도에 맞게 Adobe Campaign은 IP가 시간당 전송할 수 있는 이메일 수를 제어할 수 있습니다. 이 시스템은 이메일 거부 또는로부터 사용자를 보호할 차단 목록 수 있습니다.

## 이메일 바운스 취소

### Inbounce 이메일은 무엇입니까?

Adobe Campaign이 서버 통신 중에 오류를 처리하는 데 사용하는 프로세스입니다.

### 바운스 전자 메일은 어떻게 작동합니까?

오류 주소는 ISP에서 다시 보낸 바운스를 처리합니다. 프로세스는 다른 SMTP 오류 코드를 분석하고 RegEx 표준에 따라 올바른 작업을 적용합니다.

예를 들어 이메일 주소에는 ISP에서 보낸 &quot;550 사용자 알 수 없음&quot; 피드백이 있습니다. 이 오류 코드는 Adobe Campaign 오류 주소(반환 경로 주소)로 처리됩니다. 그러면 이 오류가 RegEx 표준과 비교되고 올바른 규칙이 적용됩니다. 전자 메일은 *하드 바운스*(유형과 일치), *사용자 알 수 없음*(원인 일치))로 간주되며 첫 번째 루프가 시스템에 도착한 후 격리 상태로 푸시됩니다.

### Adobe Campaign은 어떻게 관리하고 있습니까?

Adobe Campaign은 오류 유형과 원인 간의 일치로 이 프로세스를 관리합니다.

* **[!UICONTROL User Unknown]**:구문적으로 올바르지만 존재하지 않는 주소. 이 오류는 하드 바운스로 분류되고 첫 번째 오류 내에 격리되도록 푸시되었습니다.
* **[!UICONTROL Mailbox full]**:최대 용량에 도달한 사서함. 이 오류는 사용자가 이 사서함을 더 이상 사용하지 않고 있음을 나타낼 수도 있습니다. 이 오류는 소프트 바운스로 분류되고 세 번째 오류 내에 격리되어 30일 후 격리 조치에서 제거됩니다.
* **[!UICONTROL Inactive User]**:지난 6개월 동안 비활성 사용자로 인해 사서함이 ISP에 의해 비활성화되었습니다. 이 오류는 소프트 바운스로 분류되고 세 번째 오류 내에 격리되도록 푸시되었습니다.
* **[!UICONTROL Invalid domain]**:전자 메일 주소의 도메인이 없습니다. 이 오류는 소프트 바운스로 분류되고 세 번째 오류 내에 격리되도록 푸시되었습니다.
* **[!UICONTROL Refused]**:ISP는 사용자에게 이메일을 전달하기를 거부했다. 이 오류는 소프트 바운스로 분류되며, 오류가 이메일 주소에 연결되어 있지 않지만 IP 또는 도메인 평판에 연결되어 있으므로 격리 상태로 푸시되지 않습니다.

>[!NOTE]
>
>배달 실패 유형 및 이유에 대한 자세한 내용은 이 [섹션](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)을 참조하십시오.

## 배달 가능성 인스턴스

MX 규칙 및 바운스 규칙의 일별 업데이트는 이러한 규칙의 제공 가능 인스턴스 소유자에 연결된 클라이언트 인스턴스의 특정 워크플로우에 의해 관리됩니다.

투명도 프로세스를 통해 인스턴스를 최신 상태로 유지하려는 모든 클라이언트에 대해 이 일일 업데이트를 실행하고 있습니다.

MX 규칙에는 6개의 서로 다른 수준의 처리량이 있으며 주로 구현 프로세스 중에 사용됩니다.

![](assets/mx-rules-throughput.png)

사용자 지정 모드는 MX 규칙을 직접 설정하려는 고급 클라이언트를 위한 것입니다. 사용자 지정 모드가 활성화되면 동기화가 꺼질 때 전달 가능 인스턴스에 의해 클라이언트가 업데이트되지 않습니다.

## 바운스 예

* **사용자 알 수 없음** (하드 바운스):550 5.1.1 ...{mx003}을(를) 알 수 없습니다.
* **사서함 전체** (소프트 바운스):사용자 할당량 550 5.2.2 초과
* **비활성 사서함** (소프트 바운스):550 5.7.1 :거부된 수신자 주소:비활성 MailBox, 6개월 이상 채워지지 않음
* **도메인이 잘못됨** (소프트 바운스):&#39;ourdan.com&#39;에 대한 DNS 쿼리가 실패했습니다.
* **거부됨** (소프트 바운스):인바운드 이메일 바운스(규칙 &#39;Feedback_loop_Hotmail&#39;이 바운스와 일치함)
* **연결할 수**  없음(소프트 바운스):421 4.16.55  [TS01] x.x.x의 메시지는 과도한 사용자 불만 때문에 일시적으로 지연됨

**관련 항목:**
* [MX 구성](../../installation/using/email-deliverability.md#mx-configuration)
* [기술 이메일 구성](../../installation/using/email-deliverability.md)
* [배달 오류 이해](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic - 기술 Recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/product-specific-resources/campaign/acc-technical-recommendations.html)
