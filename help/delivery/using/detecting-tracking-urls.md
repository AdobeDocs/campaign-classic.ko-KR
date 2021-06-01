---
product: campaign
title: 추적 URL 감지
description: URL을 추적하는 권장 패턴에 대해 자세히 알아보십시오
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# 추적 URL 감지

## 비검출 예

`<%= getURL("http://mynewsletter.com") %>` 은(는) 이메일을 통해 웹 페이지의 실제 콘텐츠를 수신자에게 보냅니다. 하지만 어떤 링크도 추적되지 않습니다. 그 이유는 MTA가 보내기 전에 각 이메일에 대해 `"<%=getURL(..."`을 실행하기 때문입니다. 수신자마다 다를 수 있으므로 Adobe Campaign은 추적에 대한 URL을 알 수 없으며 태그 ID를 할당할 수 없습니다.

다운로드할 페이지가 모든 수신자에 대해 동일한 경우 모범 사례는 다음과 같습니다.

`<%@ include url="http://mynewsletter.com" %>`

이 경우 페이지는 추적 감지 전에 분석 중에 다운로드됩니다. 이를 통해 Adobe Campaign에서 링크를 검색하고, 태그 ID를 할당하고, 추적할 수 있습니다.

## 권장 패턴

`<%@` 지침을 처리한 후 추적할 URL에는 다음 구문이 있습니다.`<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>다른 모든 패턴은 Adobe에서 지원되지 않으므로 잠재적인 보안 격차를 방지해야 합니다.

## 비보안 패턴

컨텐츠에 개인화된 링크를 추가할 때는 잠재적인 보안 격차를 방지하기 위해 항상 URL의 호스트 이름 부분에 개인화를 사용하지 마십시오. [이 페이지](../../installation/using/privacy.md#url-personalization)에서 자세히 알아보십시오.

예를 들어 `<a href="http://<%=myURL%>">` 구문은 **안전하지 않으므로 사용하지 않아야 합니다.**

* Adobe Campaign에서 생성한 링크에 하나 이상의 매개 변수가 포함되어 있으면 이 구문을 사용하면 보안 문제가 발생할 수 있습니다.
* Clean은 임의로 발생할 수 있는 일부 링크를 잘못 패치할 수 있습니다. 일반적인 증상은 이메일 증명에는 표시되지만 미리 보기에서는 표시되지 않는 HTML입니다.
* URL을 이스케이프하는 것이 문제가 되고, URL의 일부 문자가 있으면 문제가 발생할 수 있습니다.
* 리디렉션 URL에서 매개 변수와 충돌하는 ID라는 매개 변수를 사용할 수 없습니다.
* Adobe Campaign은 &quot;myURL&quot;이라는 가능한 모든 값을 다르게 추적하므로 추적의 관심사는 게재 통계로 제한됩니다.
