---
product: campaign
title: 추적 URL 감지
description: URL 추적을 위한 권장 패턴에 대해 자세히 알아보기
feature: Monitoring
role: User, Developer, Data Engineer
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# 추적 URL 감지

## 불검출의 예

`<%= getURL("http://mynewsletter.com") %>` 은 을 작동하고 이메일을 통해 수신자에게 웹 페이지의 실제 콘텐츠를 전송합니다. 하지만 어떤 링크도 추적되지 않습니다. MTA가 실행되기 때문입니다 `"<%=getURL(..."` 보내기 전 각 이메일에 대해. 수신자마다 다를 수 있으므로 Adobe Campaign은 추적을 위한 URL을 알고 태그 ID를 할당할 수 없습니다.

다운로드할 페이지가 모든 수신자에게 동일한 경우 가장 좋은 방법은 다음을 수행하는 것입니다.

`<%@ include url="http://mynewsletter.com" %>`

이 경우 페이지는 분석 중에 추적 감지 전에 다운로드됩니다. 이를 통해 Adobe Campaign은 링크를 검색하고, 태그 ID를 할당하고, 추적할 수 있습니다.

## 권장 패턴

처리 후 `<%@` 지침에서 추적할 URL의 구문은 다음과 같습니다. `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>다른 모든 패턴은 Adobe에서 지원되지 않으므로 잠재적인 보안 공백을 방지하기 위해 피해야 합니다.

## 비보안 패턴

콘텐츠에 개인화된 링크를 추가할 때 잠재적인 보안 차이를 방지하기 위해 항상 URL의 호스트 이름 부분에 개인화를 두지 마십시오. [이 페이지](../../installation/using/privacy.md#url-personalization)에서 자세히 알아보십시오.

예를 들어 `<a href="http://<%=myURL%>">` 구문은 다음과 같습니다 **안전하지 않음** 피해야 합니다.

* 이 구문을 사용하면 Adobe Campaign에서 생성한 링크에 하나 이상의 매개 변수가 포함된 경우 보안 문제가 발생할 수 있습니다.
* Tidy가 일부 링크를 잘못 패치할 수 있으며 임의로 발생할 수 있습니다. 일반적인 증상은 이메일 증명에는 표시되지만 미리보기에는 표시되지 않는 HTML 부분입니다.
* URL을 이스케이프 처리하는 것은 문제가 있습니다. URL의 일부 문자로 인해 문제가 발생할 수 있습니다.
* 리디렉션 URL의 매개 변수와 충돌하는 ID라는 매개 변수를 사용할 수 없습니다.
* Adobe Campaign이 &quot;myURL&quot;의 가능한 모든 값을 무의미하게 추적하므로 추적의 관심은 게재 통계로 제한됩니다.
