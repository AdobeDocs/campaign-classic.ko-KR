---
solution: Campaign Classic
product: campaign
title: 개인 정보 및 동의
description: 개인 정보 및 동의서에 대한 자세한 내용
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '2043'
ht-degree: 73%

---


# 개인 정보 및 동의{#privacy-and-recommendations}

## 일반 권장 사항 {#general-recommendations}

Adobe Campaign은 개인 정보와 중요한 데이터를 포함한 많은 양의 데이터를 수집하고 처리할 수 있는 강력한 데이터 도구입니다. 따라서 개인 정보를 신중하게 관리해야 합니다.

* 항상 개인 정보를 책임감 있고 윤리적으로 사용하십시오.

* 요청하지 않은 이메일, 푸시 알림 및 SMS 메시지(&quot;스팸&quot;)를 보내지 마십시오. Adobe는 고객 생애의 가치 및 충성도를 향상하기 위해 허가 마케팅의 원칙을 강력하게 믿고 있습니다. 따라서 원치 않는 메시지 발송에 Adobe Campaign을 사용하는 것을 엄격히 금하고 있습니다.

[보안 및 개인 정보 보호 체크리스트](https://helpx.adobe.com/kr/campaign/kb/acc-security.html)를 검토하여 보안 및 개인 정보에 대한 주요 요소를 알아보십시오.

### 개인 정보 보호 규정 {#privacy-regulations}

개인 정보를 올바로 처리하고 개인 데이터를 관리하기 위해 운영하는 지역에 적용되는 법규 내에서 작업하십시오. 다음과 같은 규정이 있습니다.
* [GDPR](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en) (European General Data Protection Regulation)
* [DPA](https://www.gov.uk/data-protection) (UK’s implementation of GDPR)
* [개인 정보 및 전자 통신에 관한 유럽 지침](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM Act](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business) (상업용 이메일에 관한 규정 및 요구 사항에 설정된 미국 법)
* [CPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;chapter=&amp;article=) (California Consumer Privacy Act)
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) (Thailand Personal Data Protection Act)
* [LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf) (브라질 일반 데이터 보호법) - 2020년 8월 16일부터 유효

>[!NOTE]
>
>GDPR, CPA, PDPA 및 LGPD가 Adobe Campaign에 적용되는 방법에 대한 자세한 내용은 [이 페이지](../../platform/using/privacy-management.md#privacy-management-regulations)을 참조하십시오.

### Adobe Experience Cloud 개인 정보 보호 {#experience-cloud-privacy}

Adobe Campaign은 Adobe Experience Cloud 솔루션의 일부입니다. Campaign에서 개인 정보를 처리하는 방식은 다음과 같은 Experience Cloud 일반 원칙을 따릅니다.

* **Adobe Experience Cloud 사용 시 수집되는 정보**

   Adobe Experience Cloud 솔루션을 사용하는 회사는 수집할 정보를 선택하고 Adobe Experience Cloud 계정으로 보냅니다. 수집할 수 있는 정보의 유형에는 웹 검색 활동, IP 주소, 모바일 디바이스의 위치 정보, 캠페인 성공률, 장바구니에서 구매 또는 장바구니로 배치된 항목 등이 있습니다.

   >[!NOTE]
   >
   >모든 Adobe 제품에 대해 Campaign은 앱 및 웹 사이트 사용자에 대한 정보를 수집합니다. 자세한 내용은 [Adobe 개인 정보 보호 정책](https://www.adobe.com/privacy/policy.html)을 참조하십시오.

* **Adobe Experience Cloud을 정보를 수집하는 데 사용하는 방법**

   * Adobe Experience Cloud 솔루션은 사용자가 정보를 수집할 수 있도록 쿠키 및 웹 비콘(태그 또는 픽셀로도 알려져 있음)과 같은 유사한 기술을 사용합니다. Adobe Campaign의 쿠키 및 추적 기능에 대한 자세한 내용은 [이 섹션](#tracking-capabilities)을 참조하십시오.
   * 또한 모바일 앱에서 Adobe Experience Cloud 기술을 사용할 수 있습니다. 캠페인과 함께 모바일 게재 전송에 대한 자세한 내용은 [SMS 채널](../../delivery/using/sms-channel.md) 및 [모바일 앱 채널](../../delivery/using/about-mobile-app-channel.md)을 참조하십시오.

* **Adobe Experience Cloud 사용에 대한 사용자의 개인 정보 보호 선택**

   Adobe는 고객에게 다음과 같은 내용을 설명하는 개인 정보 보호 정책을 제공하도록 요구합니다.

   * Adobe Experience Cloud과 관련된 개인 정보 보호 사례
   * 사용자가 Adobe Experience Cloud과 관련하여 자신의 정보를 수집하거나 사용하는 것에 대한 환경 설정을 하는 방법

   >[!NOTE]
   >
   >모든 Adobe 제품에서 Campaign 사용자는 앱 및 웹 사이트를 통해 수집된 정보의 공유를 옵트아웃할 수 있습니다. 자세한 내용은 [Adobe Experience Cloud 사용 정보 FAQ](https://www.adobe.com/privacy/experience-cloud-usage-info-faq.html)를 참조하십시오.

Adobe Experience Cloud 개인 정보 보호에 대한 자세한 내용은 [이 페이지](https://www.adobe.com/privacy/marketing-cloud.html)를 참조하십시오.

## 개인 데이터 및 가상 사용자 {#personal-data}

개인 정보 관리 시 누가 어떤 데이터를 주의 깊게 처리할지를 정의하는 것이 중요합니다.
* **개인 데이터**&#x200B;는 살아있는 개인을 직접 또는 간접적으로 식별할 수 있는 정보입니다.
* **중요한 개인 데이터**&#x200B;는 노동조합 멤버십뿐 아니라 개인의 인종, 정치적 관점, 종교적 신념, 범죄 기록, 유전자 정보, 건강 정보, 성적 선호도, 생체 인식 정보 등과 관련된 정보입니다.

Campaign을 다른 Experience Cloud 솔루션과 통합하면, [Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md), [Audience Manager 또는 사용자 핵심 서비스](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md), [Campaign Standard](../../integrations/using/synchronizing-audiences.md) 또는 [CRM 커넥터](../../platform/using/crm-connectors.md)를 통해 다른 솔루션과 함께 사용할 수 있습니다. 개인 데이터 보호를 위해 추가 관리가 필요합니다.

[기본 규정](#privacy-regulations)은 다음과 같이 데이터를 관리하는 서로 다른 엔터티를 의미합니다.
* **데이터 컨트롤러**&#x200B;는 개인 데이터를 수집, 사용 및 공유하는 방법과 목적을 결정하는 인증 기관입니다.
* **데이터 프로세서**&#x200B;는 데이터 컨트롤러의 지시에 따라 개인 데이터를 수집, 사용 또는 공유하는 개인 또는 주체입니다.
* **데이터 주체**&#x200B;는 개인 데이터를 수집, 사용 또는 공유하며 해당 개인 데이터를 참조해서 직접 또는 간접적으로 식별할 수 있는 살아있는 개인입니다.

따라서 개인 데이터를 수집 및 공유하는 회사는 데이터 컨트롤러이며 클라이언트는 데이터 주체이고 Adobe Campaign은 데이터 프로세서의 역할을 합니다. [개인 정보 보호 요청](#privacy-requests)을 관리할 때와 같이 데이터 주체와의 관계를 처리하는 것은 데이터 컨트롤러로서의 책임입니다.

### 사용 사례 시나리오 {#use-case-scenario}

서로 다른 가상 사용자가 상호 작용하는 방법을 보여주기 위해 높은 수준의 GDPR 고객 경험을 예로 들어보겠습니다.

이 예에서는 항공사가 Adobe Campaign 고객입니다. 이 회사는 **데이터 컨트롤러**&#x200B;이고 항공사의 모든 클라이언트는 **데이터 주체**&#x200B;입니다. 이 특정 경우에서 Laura는 항공사의 고객입니다.

이 예제에서 사용되는 다양한 가상 사용자는 다음과 같습니다.

* **Laura**&#x200B;는 **데이터 주체**&#x200B;입니다. Laura는 항공사로부터 메시지를 받는 수신자입니다. Laura는 정기적인 고객이지만, 어떤 시점에서는 항공사로부터 개인화된 광고나 마케팅 메시지를 받고 싶지 않다고 결정할 수 있습니다. Laura는 항공사의 절차에 따라 정기 고객 번호를 삭제하도록 요구할 겁니다.

* **Anne**&#x200B;는 항공사의 **데이터 컨트롤러**&#x200B;입니다. Laura의 요청을 받고 데이터 주체를 확인하기 위해 요청한 유용한 ID를 검색한 후, Adobe Campaign에서 요청을 제출합니다.

* **Adobe Campaign**&#x200B;은 **데이터 프로세서**&#x200B;입니다.

![](assets/privacy-gdpr-flow.png)

이 사용 사례의 일반적인 흐름은 다음과 같습니다.

1. **데이터 주체**(Laura)는 이메일, 고객 지원 센터 또는 웹 포털을 통해 **데이터 컨트롤러**&#x200B;에게 GDPR 요청을 보냅니다.

1. **데이터 컨트롤러**(Anne)는 인터페이스를 통해서나 API를 사용하여 GDPR 요청을 Campaign으로 푸시합니다.

1. **데이터 프로세서**(Adobe Campaign)이 정보를 수신하면 GDPR 요청에 대해 조치를 취하여 **데이터 컨트롤러**(Anne)에게 응답이나 승인을 보냅니다.

1. 그런 다음 **데이터 컨트롤러**(Anne)가 정보를 검토하고 다시 **데이터 주체**(Laura)로 보냅니다.

## 데이터 획득 {#data-acquisition}

Adobe Campaign을 사용하면 개인 및 중요한 정보를 포함한 데이터를 수집할 수 있습니다. 따라서 수신자로부터 동의를 받고 모니터링하는 것이 중요합니다.

* 항상 수신자가 커뮤니케이션 수신에 동의하도록 합니다. 이를 위해서는 옵트아웃 요청을 최대한 빨리 준수하고 이중 옵트인 프로세스를 통해 동의를 확인하십시오. 자세한 내용은 [이중 옵트인](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in)을(를) 사용하여 구독 양식 만들기를 참조하십시오.
* 사기성 목록을 가져오고 시드 주소를 사용하여 클라이언트 파일이 잘못 사용되고 있는지 확인하십시오. 자세한 내용은 [시드 주소 ](../../delivery/using/about-seed-addresses.md)를 참조하십시오.
* 동의 및 권한 관리를 통해 수신자의 환경 설정을 추적할 수 있을 뿐만 아니라 조직 내에서 누가 어떤 데이터에 액세스할 수 있는지를 관리할 수 있습니다. 자세한 내용은 [이 섹션](#consent)을 참조하십시오.
* 수신자의 개인 정보 보호 요청을 간편하게 지원하고 관리할 수 있습니다. 자세한 내용은 [이 섹션](#privacy-requests)을 참조하십시오.

## 개인 정보 관리 {#privacy-management}

개인 정보 관리는 개인 정보 보호 규정(GDPR, CPA 등)을 준수하는 데 도움이 되는 모든 프로세스 및 도구를 의미합니다. [이 페이지](https://helpx.adobe.com/kr/campaign/kb/campaign-privacy-overview.html)에 대한 개인 정보 관리의 개요를 확인하십시오.

Adobe Campaign은 개인 정보 관리를 위한 다양한 기능을 제공합니다.
* 동의 관리, 데이터 보존 및 사용자 역할. [이 섹션](#consent)을 참조하십시오.
* 개인 정보 보호 요청(액세스 권한 및 잊혀질 권리). [이 섹션](#privacy-requests)을 참조하십시오.
* 개인 정보 판매 옵트아웃 (CCPA-특정). [이 섹션](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa)을 참조하십시오.

Campaign의 주요 개인 정보 보호 기능과 관련된 개인의 예가 [이 섹션](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-faq.html?lang=ko#getting-started)에 나와 있습니다.

### 동의, 보존 및 역할 {#consent}

기본적으로 Adobe Campaign은 다음과 같은 개인 정보에 필수적인 중요한 기능을 제공합니다.

* **동의 관리**: 구독 관리 프로세스를 통해 수신자의 환경 설정을 관리하고 어떤 수신자가 어떤 구독 유형을 옵트인했는지 추적할 수 있습니다. 자세한 내용은 [구독 정보](../../delivery/using/about-services-and-subscriptions.md)를 참조하십시오.
* **데이터 보존**: 모든 기본 제공 표준 로그 테이블에는 사전 설정된 보존 기간이 있으며 일반적으로 데이터 저장소를 6개월 이하로 제한합니다. 워크플로우로 추가 보존 기간을 설정할 수 있습니다. 자세한 내용은 Adobe 컨설턴트나 기술 관리자에게 문의하십시오.
* **권한 관리**: Adobe Campaign은 다양한 사전 설치 또는 사용자 지정 역할을 통해 다양한 캠페인 운영자에게 할당된 권한을 관리할 수 있는 기능을 제공합니다. 이를 통해 회사 내에서 다른 유형의 데이터에 액세스, 수정 또는 내보낼 수 있는 사용자를 관리할 수 있습니다. 자세한 내용은 [액세스 관리 정보](../../platform/using/access-management.md)를 참조하십시오.

이러한 기능과 Adobe Campaign에서 관리하는 방법에 대한 자세한 내용은 [이 섹션](../../platform/using/privacy-management.md#consent-retention-roles)을 참조하십시오.

### 개인 정보 보호 요청 {#privacy-requests}

Adobe Campaign은 특정 개인 정보 보호 요청에 대해 데이터 컨트롤러로서 사용자의 준비를 용이하게 하는 데 도움이 되는 추가 기능을 제공합니다.

* **액세스 권한**&#x200B;은 데이터 주체가 데이터 주체의 확인을 통해 데이터 주체의 개인 데이터가 처리 중인지 여부, 처리 장소 및 그 이유를 알 수 있는 권리입니다.

* **잊혀질 권리**(삭제 요청)는 데이터 주체가 자신의 개인 데이터를 삭제하도록 권한을 부여합니다.

**액세스** 및 **삭제** 요청이 [이 섹션](../../platform/using/privacy-management.md#right-access-forgotten)에 표시됩니다.

이러한 요청을 만드는 구현 단계는 [이 섹션](../../platform/using/privacy-requests.md)에 자세히 설명되어 있습니다.

## 추적 기능 {#tracking-capabilities}

### 쿠키 {#cookies}

Adobe Campaign은 추적 기능 덕분에 세 가지 유형의 쿠키를 사용하여 배달 받는 사람의 탐색을 추적할 수 있습니다.세션 쿠키와 2개의 영구 쿠키.

* **session** 쿠키:**nlid** 쿠키에는 연락처(**broadlogId**)로 보낸 이메일의 ID와 메시지 템플릿의 식별자(**deliveryId**)가 포함되어 있습니다. 이 URL은 연락처가 Adobe Campaign이 보낸 전자 메일에 포함된 URL을 클릭할 때 추가되며, 이를 통해 웹에서 해당 동작을 추적할 수 있습니다. 브라우저를 닫으면 이 세션 쿠키가 자동으로 지워집니다. 연락처는 브라우저가 쿠키를 거부하도록 구성할 수 있습니다.

* 두 개의 **영구** 쿠키:
   * Adobe Experience Cloud 솔루션 간에 **UUID**(Universal Unique IDentitfier) 쿠키가 공유됩니다. 새 값이 생성될 때 클라이언트 브라우저에서 사라질 때까지 한 번 설정됩니다. 이 쿠키를 사용하면 웹 사이트를 방문할 때 Experience Cloud 솔루션과 상호 작용하는 사용자를 식별할 수 있습니다. 랜딩 페이지(알 수 없는 고객 활동을 수신자에게 연결)나 배송을 통해 보관할 수 있습니다. 이 쿠키의 설명은 [이 페이지](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-mc.html?lang=en#ec-cookies)에서 사용할 수 있습니다.
   * **nllastdelid** 쿠키(Campaign Classic 20.3에서 도입)는 사용자가 링크를 클릭한 마지막 배달의 **deliveryId**&#x200B;가 포함된 영구 쿠키입니다. 이 쿠키는 세션 쿠키가 없을 때 사용되는 추적 테이블을 식별하는 데 사용됩니다.

GDPR(General Data Protection Regulation)과 같은 규정에서는 회사가 쿠키를 설치하기 전에 웹 사이트 사용자의 계약을 요구하는 것을 명시합니다.

* 쿠키의 사용을 승인하는 확인란을 사용하여 사이트에 권한 부여 요청(예: 페이지 위로 올라오기)을 통해 웹 추적 도구가 설치되어 있음을 사용자에게 알리거나, 첫 번째 페이지에 있는 배너를 추가하는 등의 작업을 수행해야 합니다.
* 팝업 창은 브라우저에 의해 종종 차단되므로 사용하지 않아야 합니다.

### 메시지 추적 {#message-tracking}

Adobe Campaign을 사용하면 보낸 이메일과 배달 받는 사람의 행동을 추적할 수 있습니다.링크, 구독 취소 등을 열고 자세한 내용은 [메시지 추적 정보](../../delivery/using/about-message-tracking.md)를 참조하십시오.

이렇게 하려면 배달 대시보드의 [추적](../../delivery/using/delivery-dashboard.md#tracking-logs) 탭에서 배달 및 받는 사람 동작의 영향을 측정하기 위해 [추적된 링크](../../delivery/using/how-to-configure-tracked-links.md)를 메시지에 추가합니다. 추적 데이터는 [추적 표시기](../../reporting/using/delivery-reports.md#tracking-indicators) 보고서에서 해석됩니다.

### 웹 추적 {#web-tracking}

또한, 받는 사람이 웹 사이트를 검색하는 방식을 모니터링할 수 있습니다.추적 태그를 삽입하여 웹 애플리케이션 페이지에서 정보를 수집하고 방문을 측정합니다. 자세한 내용은 [웹 응용 프로그램 추적](../../web/using/tracking-a-web-application.md)을 참조하십시오.

웹 추적 구성은 [이 섹션](../../configuration/using/about-web-tracking.md)에 나와 있습니다.

추적을 추가로 관리하기 위해 Adobe Campaign을 사용하면 옵트아웃 배너를 표시하여 행동 추적을 옵트아웃한 최종 사용자의 웹 동작 추적을 중지할 수 있습니다. 자세한 내용은 [웹 응용 프로그램 추적 옵트아웃](../../web/using/web-application-tracking-opt-out.md)을 참조하십시오.
