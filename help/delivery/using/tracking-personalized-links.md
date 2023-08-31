---
product: campaign
title: 개인화된 링크 추적 시작
description: Campaign에서 개인화되고 추적을 지원하는 이메일에 링크를 작성하는 방법을 알아봅니다
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Personalization
role: User
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 7%

---

# 개인화된 링크 추적 시작 {#tracking-personalized-links}

개인화가 포함된 이메일 콘텐츠의 링크는 추적할 특정 구문이 필요합니다.

이메일 콘텐츠(HTML 또는 텍스트)에서 JavaScript를 사용하면 두 가지 제한 사항을 포함하여 다이내믹 콘텐츠를 생성하여 수신자에게 보낼 수 있습니다.

* 스크립트는 데이터베이스에 직접 액세스할 수 없습니다(SQL 함수 및 API 함수를 사용할 수 없음).
* 링크를 추적할 수 있도록 Adobe Campaign에서 URL을 감지할 수 있어야 합니다. [자세히 알아보기](detecting-tracking-urls.md)

특정 전처리 명령을 추가하여 URL을 스크립팅하고 추적할 수 있습니다. [자세히 알아보기](pre-processing-instructions.md)

추적 검색을 위해 Adobe Campaign이 임베드됨 [단정해](https://www.html-tidy.org/) HTML 소스를 구문 분석하고 패턴을 감지합니다. 콘텐츠의 모든 URL을 나열하므로 개별적으로 추적할 수 있습니다. Adobe Campaign은 Tidy를 다시 사용하여 URL( )을 바꿉니다.`http://myurl.com`)를 사용하여 Adobe Campaign 리디렉션 서버를 지정합니다.

예를 들어 초기 콘텐츠에서 다음을 수행합니다. `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` 은(는) 특정 수신자 한 명에 대해 다음으로 대체됩니다. `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

위치:

* &quot;h&quot;는 HTML 컨텐츠(또는 텍스트 컨텐츠의 경우 &quot;t&quot;)를 의미합니다.
* 617791은 메시지 ID / broadLog ID (16진수)입니다.
* 71ffa3은 NmsDelivery ID(16진수)입니다.
* 71ffa8은 NmsTrackingUrl ID(16진수)입니다.
* p1, p2 등은 URL에서 대체할 모든 매개 변수입니다.
