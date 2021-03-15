---
solution: Campaign Classic
product: campaign
title: 개인화된 링크 추적 시작
description: Campaign Classic에서 개인화할 수 있는 이메일에 링크를 작성하고 추적을 지원하는 방법을 알아봅니다.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 768fe62db4efd1217c22973c7e5dc31097d67bae
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 6%

---


# 개인화된 링크 추적 시작 {#tracking-personalized-links}

개인화가 포함된 이메일 컨텐츠의 링크는 특정 구문을 추적해야 합니다.

이메일 컨텐츠(HTML 또는 텍스트)에서 JavaScript를 사용하면 2가지 제한 사항과 함께 동적 컨텐츠를 생성하고 수신자에게 전송할 수 있습니다.

* 스크립트가 데이터베이스에 직접 액세스할 수 없습니다(SQL 함수 및 API 함수를 사용할 수 없음).
* Adobe Campaign은 링크를 추적할 수 있도록 URL을 감지할 수 있어야 합니다. [자세히 알아보기](detecting-tracking-urls.md)

이러한 URL에 [특정 사전 처리 지침](pre-processing-instructions.md)을 추가할 수 있습니다.

사전 처리 지침을 따릅니다.

추적 감지를 위해 Adobe Campaign은 [Dilt](http://www.html-tidy.org/)을 포함하여 HTML 소스를 파싱하고 패턴을 검색합니다. 컨텐츠의 모든 URL이 나열되므로 개별적으로 추적할 수 있습니다. Adobe Campaign에서는 다시 [정리]를 사용하여 URL(`http://myurl.com`)을 Adobe Campaign 리디렉션 서버를 가리키는 URL로 바꿉니다.

예를 들어 초기 컨텐츠에서:`http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>`은(는) 특정 받는 사람을 위해 다음과 같이 대체됩니다.`http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

위치:

* &quot;h&quot;는 HTML 컨텐츠를 의미하며 텍스트 컨텐츠의 경우 &quot;t&quot;를 의미합니다.
* 617791은 메시지 ID / broadLog ID(16진수)입니다.
* 71ffa3는 NmsDelivery ID(16진수)입니다.
* 71ffa8은 NmsTrackingUrl ID(16진수)입니다.
* p1, p2 등은 URL에서 대체할 모든 매개 변수입니다.
