---
solution: Campaign Classic
product: campaign
title: 추적 URL 감지
description: URL을 추적하는 권장 패턴에 대해 자세히 알아보십시오.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---


# 추적 URL 감지

## 비 감지 예

`<%= getURL("http://mynewsletter.com") %>` 작업하고 이메일을 통해 웹 페이지의 실제 컨텐츠를 수신자에게 보냅니다. 하지만 어떤 링크도 추적되지 않습니다. 이러한 이유는 MTA가 보내기 전에 각 이메일에 대해 `"<%=getURL(..."`을(를) 실행하기 때문입니다. 각 수신자에 대해 다를 수 있으므로 Adobe Campaign은 추적할 URL을 알지 못하고 태그 ID를 할당할 수 없습니다.

다운로드할 페이지가 모든 수신자에게 동일한 경우 다음을 수행하는 것이 좋습니다.

`<%@ include url="http://mynewsletter.com" %>`

이 경우 추적 감지 전에 분석 중에 페이지가 다운로드됩니다. 이를 통해 Adobe Campaign은 링크를 검색하고 태그 ID를 할당하며 링크를 추적할 수 있습니다.

## 권장 패턴

`<%@` 지침을 처리한 후 추적할 URL의 구문은 다음과 같습니다.`<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>다른 모든 패턴은 Adobe에서 지원되지 않으므로 잠재적인 보안 격차를 방지해야 합니다.

## http://&lt;%=myURL%> 패턴에 대한 경고

`<a href="http://<%=myURL%>">` 구문은 안전하지 않으므로 다음과 같은 이유로 권장되지 않습니다.

* Clean은 임의로 발생할 수 있는 일부 링크를 잘못 패치할 수 있습니다. 일반적인 증상은 이메일 교정쇄에는 표시되지만 미리 보기에서는 표시되지 않는 HTML입니다.
* URL을 이스케이프하는 데 문제가 있고 URL의 일부 문자로 인해 문제가 발생할 수 있습니다.
* 리디렉션 URL에서 매개 변수와 충돌하는 ID라는 매개 변수는 사용할 수 없습니다.
* 그러면 Adobe Campaign이 &quot;myURL&quot;의 모든 가능한 값을 다르게 추적하므로, 추적의 관심사는 전달에 대한 통계로 제한됩니다.

자세한 내용은 [이 페이지](https://helpx.adobe.com/campaign/kb/acc-security.html#privacy)를 참조하십시오.

