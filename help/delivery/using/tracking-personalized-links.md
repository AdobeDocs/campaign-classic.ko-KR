---
product: campaign
title: 개인화된 링크 추적 시작
description: Campaign Classic에서 개인화하고 추적을 지원할 수 있는 이메일에 링크를 작성하는 방법을 알아봅니다.
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---

# 개인화된 링크 추적 시작 {#tracking-personalized-links}

![](../../assets/common.svg)

개인화가 포함된 이메일 콘텐츠의 링크에는 특정 구문을 추적해야 합니다.

이메일 콘텐츠(HTML 또는 텍스트)에서 JavaScript를 사용하면 두 가지 제한 사항을 사용하여 다이내믹 콘텐츠를 생성하고 수신자에게 보낼 수 있습니다.

* 스크립트는 데이터베이스에 직접 액세스할 수 없습니다(SQL 함수 및 API 함수를 사용할 수 없음).
* Adobe Campaign에서 링크를 추적할 수 있도록 URL을 감지할 수 있어야 합니다. [자세히 알아보기](detecting-tracking-urls.md)

특정 사전 처리 지침을 추가하여 URL을 스크립팅하고 추적할 수 있습니다. [자세히 알아보기](pre-processing-instructions.md)

추적 감지를 위해 Adobe Campaign은 [Clean](http://www.html-tidy.org/)을 포함하여 HTML 소스를 분석하고 패턴을 감지합니다. 컨텐츠를 개별적으로 추적할 수 있도록 컨텐츠의 모든 URL을 나열합니다. Adobe Campaign은 Clean을 다시 사용하여 URL(`http://myurl.com`)을 Adobe Campaign 리디렉션 서버를 가리키는 URL로 바꿉니다.

예를 들어 초기 컨텐츠에서 `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` 은(는) 한 특정 수신자에 대해 다음과 같이 대체됩니다. `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

위치:

* h는 HTML 컨텐츠를 의미합니다(텍스트 컨텐츠의 경우 &quot;t&quot;).
* 617791은 메시지 ID / broadLog ID(16진수)입니다.
* 71ffa3는 NmsDelivery ID(16진수)입니다.
* 71ffa8은 NmsTrackingUrl ID(16진수)입니다.
* p1, p2 등은 URL에서 대체할 모든 매개 변수입니다.
