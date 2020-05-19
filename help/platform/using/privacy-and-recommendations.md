---
title: 개인 정보 및 권장 사항
seo-title: 개인 정보 및 권장 사항
description: 개인 정보 및 권장 사항
seo-description: null
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be148d7cd55097b9014d2f4d3b095c65a5ca8c54
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---


# 개인 정보 및 권장 사항{#privacy-and-recommendations}

## 개인 정보 및 동의 {#about-privacy-and-consent}

Adobe Campaign은 개인 정보를 비롯한 매우 많은 양의 데이터를 수집하고 처리하기 위한 강력한 툴입니다. Adobe는 Adobe Campaign의 모든 사용자가 입법(DPA, CAN-SPAM, 개인 정보 및 전자 통신에 대한 유럽 지문, 유럽 GDPR, CCPA 등)을 준수하고, 책임감 있고 윤리적인 개인 정보를 사용하며, 요청되지 않은 이메일, 푸시 알림 및 SMS 메시지(&quot;스팸&quot;)를 보내지 않도록 권장하고 있습니다. Adobe는 고객 라이프타임 가치 및 충성도 향상을 위한 허가 마케팅의 원칙을 강력하게 믿고 있으며, 따라서 Adobe Campaign을 사용해서 불필요한 메시지를 전송하는 것을 엄격히 금합니다.

자세한 내용은 [Adobe Experience Cloud 개인 정보를 참조하십시오](https://www.adobe.com/privacy/marketing-cloud.html).

보안 및 개인 정보 보호 체크리스트를 통해 보안 및 개인 정보 [](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html) 관련 사항을 확인하는 데 시간을 할애할 수 있습니다.

## 개인 정보 관리 {#privacy-management}

Adobe Campaign은 개인 정보 보호 규정(GDPR, CPA 등)을 준수하는 데 도움이 되는 다양한 툴을 제공합니다.

GDPR(General Data Protection Regulation)은 데이터 보호 요구 사항을 통합하고 현대화한 유럽 연합의 개인 정보 보호법입니다. GDPR은 EU에 있는 데이터 주체의 데이터를 보유하고 있는 Adobe Campaign 고객에게 적용됩니다.

CPA(California Consumer Privacy Act)는 캘리포니아 거주자들에게 개인 정보에 대한 새로운 권리를 제공하고 캘리포니아에서 사업을 수행하는 특정 업체에 데이터 보호 책임을 부과합니다.

동의 관리, 데이터 유지 설정 및 권한 관리 외에도 데이터 프로세서로서의 Adobe의 역할에 따라 특정 개인 정보 보호 요청에 대해 데이터 컨트롤러로서의 준비를 용이하게 하는 추가 기능을 제공합니다.

이 문서 [에서](https://helpx.adobe.com/campaign/kb/acc-privacy.html)Adobe Campaign을 사용하여 다양한 개인 정보 보호 키 기능을 관리하는 방법을 알아봅니다. 액세스 권한, 잊혀질 권리, 동의, 데이터 유지 및 사용자 역할. 또한 Adobe 솔루션을 사용할 때 개인 정보 보호 규정을 준수하는 모범 사례를 찾을 수 있습니다.

## 쿠키 및 추적 기능 {#cookies-and-tracking-capabilities}

Adobe Campaign의 추적 기능 덕분에 웹 사이트에서 배달 받는 사람의 검색을 추적할 수 있습니다. 이를 위해 Adobe Campaign은 세션 쿠키와 영구 쿠키를 사용합니다.

유럽 2009/136/CE &quot;개인 정보 및 전자 통신&quot; 및 유럽 개인 정보 보호 규정(GDPR)은 회사가 쿠키를 설치하기 전에 웹 사이트 사용자의 동의를 필요로 한다고 명시합니다. 쿠키의 설치를 승인하는 확인란이 포함된 권한 부여 요청(예: 페이지 위로 올라오기)을 통해 사이트가 웹 추적 도구를 갖추고 있음을 사용자에게 알리거나, 첫 번째 페이지가 시작되는 등의 페이지에 배너를 추가해야 합니다. 팝업 창은 브라우저에 의해 종종 차단되므로 사용하지 않아야 합니다.

사용자 추적 관리의 구성은 옵트아웃 배너가 있는 웹 응용 프로그램 및 랜딩 페이지에 사용할 수 있습니다. 이 [페이지를 참조하십시오](../../web/using/web-application-tracking-opt-out.md).

Adobe Campaign에서는 두 가지 유형의 쿠키를 사용합니다.

1. 세션 쿠키(nlid): 여기에는 연락처로 보낸 이메일의 식별자(broadlogId)와 메시지 템플릿의 식별자(deliveryId)가 포함됩니다. 이 URL은 연락처가 Adobe Campaign이 보낸 이메일에 포함된 URL을 클릭할 때 추가되며, 이를 통해 웹에서의 동작을 추적할 수 있습니다. 브라우저를 닫으면 이 세션 쿠키가 자동으로 지워집니다. 연락처는 브라우저가 쿠키를 거부하도록 구성할 수 있습니다.
1. 영구 쿠키(uuid230): 웹 사이트를 방문할 때 Adobe Campaign과 상호 작용하는 사용자를 식별할 수 있습니다. Adobe Campaign에서 마케팅 캠페인 동안 클릭 수와 전송 속도 예상 횟수를 계산하는 데 사용됩니다. 연락처가 이메일을 클릭하거나, Adobe Campaign에서 양식을 채우거나, 인바운드 상호 작용 엔진에 대한 호출 중에 삽입됩니다. 사용자는 브라우저를 삭제하거나 거부하도록 구성할 수 있습니다.

## 데이터베이스 무결성 {#database-integrity}

Adobe Campaign에는 다양한 기능이 포함되어 있습니다. 따라서 복잡한 데이터베이스 구조를 사용합니다. 데이터베이스에는 많은 테이블, 필드, 링크 및 인덱스가 포함되어 있습니다. 인터페이스에 특정 중간 테이블이 표시되지 않습니다. 특정 링크, 필드 및 색인을 자동으로 생성, 삭제 또는 수정합니다. Adobe Campaign 인터페이스(그래픽 인터페이스, 가져오기 프로그램, 서버 모듈, 웹 모듈, 전달 서버, 필드 추가, 데이터베이스 확장 등)만 데이터베이스의 무결성을 유지하면서 데이터베이스의 내용을 수정할 수 있습니다.

**이 소프트웨어 이외의 다른 도구를 사용하여 데이터베이스 내용 또는 구조를 수정하지 마십시오**. 이러한 수정은 데이터베이스를 손상시켜 다음과 같은 결과가 발생할 수 있습니다. 실수로 링크 수정 또는 손실, 고스트 레코드 또는 링크 작성, 심각한 오류 메시지 등, Adobe Campaign에서 제공한 보증 및 기술 지원 계약이 무효화됩니다.

Adobe Campaign 시스템에서 모든 데이터는 데이터베이스에 저장됩니다. 전체 Adobe Campaign 시스템의 적절한 작동 여부는 다음 데이터에 따라 달라집니다. 구독, 관리 및 구독 취소, 관리 스크린, 전달 큐, 전달 최적화 메커니즘 등을 위한 웹 모듈

## Apache Tomcat {#apache-tomcat}

Adobe Campaign에는 Apache Software Foundation( https://www.apache.org/)에서 개발한 Apache Tomcat이 [포함되어](https://www.apache.org/)있습니다.
