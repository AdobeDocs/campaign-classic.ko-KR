---
title: 차단 목록 데이터베이스
seo-title: 차단 목록 데이터베이스
description: 차단 목록 데이터베이스
seo-description: null
page-status-flag: never-activated
uuid: 8a4a69f9-87d5-4044-bc55-76cdcb2e7800
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: eede254d-2b25-46ed-b10f-fa1d54780a75
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 3%

---


# 차단 목록 데이터베이스{#blocklisting-databases}

일부 조직은 스파이더가 사용한다고 알려진 IP 주소와 도메인의 데이터베이스를 유지 관리합니다. 이러한 사이트를 상담하면 특정 메시지가 스팸으로 거부된 이유를 이해하는 데 유용합니다. 일반적으로 이러한 목록에 잘못 추가된 주소의 제거를 요청할 수 있습니다.

이러한 데이터베이스를 RBL(실시간 블랙홀 목록)이라고 하며 DNS 메커니즘을 통해 이러한 데이터베이스를 확인합니다. 세 가지 유형의 RBL이 있습니다.

* IP 주소별:는 스팸을 보내거나 스팸을 전송할 가능성이 있는 IP 주소를 나열합니다.
* 보낸 사람 도메인:스팸 전송 또는 잘못 구성된 보낸 사람 도메인(바운스 메일 주소의 전체 도메인)을 나열합니다.
* 웹 도메인별:스팸 컨텐츠에 포함된 링크 및 이미지의 URL에 있는 도메인(등록자와 등록된 상위 수준 도메인)을 나열합니다. Adobe Campaign에서 고려할 도메인은 일반적으로 추적에 사용되는 주소입니다.

다음은 가장 널리 사용되는 RBL의 목록입니다. 보다 포괄적인 목록은 https://www.dnsstuff.com/을 [참조하십시오](https://tools.dnsstuff.com/).

* **스팜하우스**

   https://www.spamhaus.org/을 [참조하십시오.](https://www.spamhaus.org/)

   데이터베이스가 더 중요합니다. 이 목록에 분류되는 것은 일반적으로 심각한 상황이다. 이러한 경우 즉시 조치를 취하고 상업용 서비스, 전달 능력 및 Adobe Campaign 지원을 경고해야 합니다.

* **SpamCop**

   https://www.spamcop.net/을 [참조하십시오.](https://www.spamcop.net/)

   그것은 가장 유명한 데이터베이스 중 하나이다. 이 목록에 IP 주소 중 하나가 있는 경우, 일반적으로 SpamCop 사용자가 메시지를 스팸으로 선언했거나 메시지를 SpamHoneycop에 전송했음을 의미합니다.

* **URIBL**

   https://www.uribl.com/을 [참조하십시오.](https://www.uribl.com/)

   이 목록은 스팸으로 선언된 메시지에 정기적으로 나타나는 도메인을 식별합니다. 도메인이 이 목록에 표시되면 배달 기능에 큰 영향을 줄 수 있습니다. 배달 서비스와 Adobe Campaign 지원 서비스에 즉시 알려 주십시오.

* **SURBL**

   http://www.surbl.org/을 [참조하십시오.](http://www.surbl.org/)

   SURBL은 스팸에 정기적으로 나타나는 웹 사이트를 식별합니다. 도메인이 이 목록에 표시되면 배달 기능에 큰 영향을 줄 수 있습니다. 배달 서비스와 Adobe Campaign 지원 서비스에 즉시 알려 주십시오.

* **iX Manitu**

   이 목록은 독일에서 널리 사용되는 IP 목록입니다. https://www.heise.de/ix/nixspam/을 [참조하십시오.](https://www.heise.de/ix/nixspam/)

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->