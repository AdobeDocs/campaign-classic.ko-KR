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
source-git-commit: ed5390b4f620c3cddaf9b856f3354dc5f06f4d98

---


# 개인 정보 및 권장 사항{#privacy-and-recommendations}

## 개인 정보 및 동의 정보 {#about-privacy-and-consent}

Adobe Campaign은 개인 정보를 비롯한 매우 많은 양의 데이터를 수집 및 처리하기 위한 강력한 도구입니다. Adobe는 Adobe Campaign의 모든 사용자가 법률(DPA, CAN-SPAM, European Directive on Privacy and Electronic Communications, European GDPR 등)을 준수하고, 개인 정보를 책임감 있고 윤리적으로 사용하고, 요청되지 않은 이메일, 푸시 알림 및 SMS 메시지(&quot;스팸&quot;)를 발송하지 않도록 권장하고 있습니다. Adobe는 고객 라이프타임 가치 및 충성도 향상을 위한 허가 마케팅의 원칙을 강력하게 신뢰하며, 따라서 Adobe Campaign을 사용하여 요청되지 않은 메시지를 전송하는 것을 엄격히 금지합니다.

자세한 내용은 Adobe Experience [Cloud 개인 정보를](https://www.adobe.com/privacy/marketing-cloud.html)참조하십시오.

Adobe Campaign은 Adobe 서비스를 사용할 때 GDPR 준수를 지원하는 툴 및 기능, 모범 사례 등을 제공합니다. 이 [문서를](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/ACC_GDPR.html)참조하십시오.

보안 및 개인 정보 [확인 목록을](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html) 통해 보안 및 개인 정보 보호에 대한 주요 요소를 확인할 수 있습니다.

## 쿠키 및 추적 기능 {#cookies-and-tracking-capabilities}

추적 기능 덕분에 Adobe Campaign을 사용하면 웹 사이트에서 게재 받는 사람의 검색 결과를 추적할 수 있습니다. 이를 위해 Adobe Campaign은 세션 쿠키와 영구 쿠키를 사용합니다.

&quot;개인 정보 및 전자 통신&quot; 및 GDPR(유럽 개인 정보 보호 규정)에 대한 2009/136/CE는 기업이 쿠키를 설치하기 전에 웹 사이트 사용자의 동의를 요구한다는 지침을 명시합니다. 쿠키의 설치를 승인하기 위한 확인란이 포함된 권한 요청(예: 페이지 위로 올라오기)을 통해 사이트가 웹 추적 툴을 갖추고 있음을 사용자에게 알리거나, 쿠키가 첫번째로 방문한 페이지의 상단에 배너를 추가하는 등의 작업을 수행해야 합니다. 팝업 창은 브라우저에 의해 종종 차단되므로 사용하지 않아야 합니다.

사용자 추적 관리의 구성은 옵트아웃 배너가 있는 웹 애플리케이션 및 랜딩 페이지에 사용할 수 있습니다. 이 [페이지를](../../web/using/web-application-tracking-opt-out.md)참조하십시오.

Adobe Campaign에서는 두 가지 유형의 쿠키를 사용합니다.

1. 세션 쿠키(nlid):여기에는 연락처로 전송된 이메일의 식별자(broadlogId)와 메시지 템플릿의 식별자(deliveryId)가 포함되어 있습니다. Adobe Campaign에서 보낸 이메일에 포함된 URL을 클릭하면 방문자가 추가되며, 이를 통해 웹에서 해당 행동을 추적할 수 있습니다. 브라우저를 닫으면 이 세션 쿠키가 자동으로 지워집니다. 연락처는 브라우저가 쿠키를 거부하도록 구성할 수 있습니다.
1. 영구 쿠키(uuid230):웹 사이트를 방문할 때 Adobe Campaign과 상호 작용하는 사용자를 식별할 수 있습니다. Adobe Campaign에서 마케팅 캠페인 동안 클릭 수와 전송 비율에 대한 예상 수를 계산하는 데 사용됩니다. 연락처가 이메일을 클릭하고, Adobe Campaign에서 양식을 채우거나, 인바운드 상호 작용 엔진에 대한 호출 중에 입력할 때 배치됩니다. 사용자는 브라우저를 삭제하거나 거부하도록 구성할 수 있습니다.

## 데이터베이스 무결성 {#database-integrity}

Adobe Campaign에는 다양한 기능이 포함되어 있습니다. 따라서 복잡한 데이터베이스 구조를 사용합니다. 데이터베이스에는 많은 테이블, 필드, 링크 및 인덱스가 포함되어 있습니다. 인터페이스에 특정 중간 테이블이 표시되지 않습니다. 소프트웨어는 특정 링크, 필드 및 색인을 자동으로 생성, 삭제 또는 수정합니다. Adobe Campaign 인터페이스(그래픽 인터페이스, 가져오기 프로그램, 서버 모듈, 웹 모듈, 배달 서버, 필드 추가, 데이터베이스 확장 등)만 해당 데이터베이스의 무결성을 유지하면서 데이터베이스의 컨텐츠를 수정할 수 있습니다.

**이 소프트웨어**&#x200B;이외의 다른 도구를 사용하여 데이터베이스 내용 또는 구조를 수정하지 마십시오. 이러한 수정은 데이터베이스를 손상시킬 가능성이 높으므로 다음과 같은 결과가 발생합니다.실수로 링크 수정 또는 손실, 고스트 레코드 또는 링크 작성, 심각한 오류 메시지 등, Adobe Campaign에서 제공한 보증 및 기술 지원 계약을 무효화하고 있습니다.

Adobe Campaign 시스템에서 모든 데이터는 데이터베이스에 저장됩니다. 전체 Adobe Campaign 시스템의 올바른 작동 여부는 다음 데이터의 가용성에 따라 달라집니다.구독, 관리 및 구독 취소, 관리 화면, 전달 큐, 전달 최적화 메커니즘 등을 위한 웹 모듈

## Apache Tomcat {#apache-tomcat}

Adobe Campaign에는 Apache Software Foundation( https://www.apache.org/)에서 개발한 Apache Tomcat [가](https://www.apache.org/)포함되어 있습니다.
