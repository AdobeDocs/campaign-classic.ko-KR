---
solution: Campaign Classic
product: campaign
title: 추적된 URL에 대한 사전 처리 지침
description: 이메일의 URL을 스크립팅하는 데 사용되고 추적되는 사전 처리 지침에 대해 자세히 알아보십시오.
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 9d3f5c74-377a-4e24-81e5-bb605f69cf8a
translation-type: tm+mt
source-git-commit: fdcb96c3c4afed1f36529e658eda26766226c44f
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 1%

---

# 사전 처리 지침 {#pre-processing-instructions}

전달 내용에서 특정 구문을 사용하여 지침을 추가하고 추적된 이메일의 URL을 스크립팅할 수 있습니다. &lt;%@ 지침은 JavaScript가 아닙니다.이 구문은 Adobe Campaign에만 적용됩니다.

배달 컨텐츠 컨텍스트에서만 적용됩니다. URL 매개 변수 외에도 이메일의 URL을 스크립팅하고 계속 추적하는 유일한 방법입니다. 추적할 링크를 감지하기 전에 배달 분석 중에 적용된 자동 복사/붙여넣기로 볼 수 있습니다.

다음 3가지 유형의 지침이 있습니다.

* **[!DNL include]**:주로 옵션, 개인화 블록, 외부 파일 또는 페이지의 일부 코드를 요인 화합니다. [자세히 알아보기](#include)
* **[!DNL value]**:배달에서 로드된 배달, 배달 변수 및 사용자 지정 개체에 대한 액세스 권한을 제공합니다. [자세히 알아보기](#value)
* **[!DNL foreach]**:를 클릭하여 사용자 지정 객체로 로드된 배열을 루프합니다. [자세히 알아보기](#foreach)

전달 마법사에서 직접 테스트할 수 있습니다. 이 URL은 컨텐츠 미리 보기에 적용되고 추적 단추를 클릭하면 URL 목록을 볼 수 있습니다.

## [!DNL include] {#include}

다음은 가장 일반적으로 사용되는 예입니다.

* 미러 페이지 링크 포함:

   ```
   <%@ include view="MirrorPage" %>  
   ```

* 페이지 URL 미러:

   ```
   View as a <a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page.
   ```

* 기본 구독 취소 URL:

   ```
   <%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>
   ```

* 기타 예:

   ```
   <%@ include file='http://www.google.com' %>
   <%@ include file='file:///X:/france/service/test.html' %>
   <%@ include option='NmsServer_URL' %>
   ```

   전달 마법사의 개인화 단추를 사용하여 올바른 구문을 가져옵니다.

## [!DNL value] {#value}

이 명령을 사용하면 모든 받는 사람에게 일정인 전달 매개 변수에 액세스할 수 있습니다.

구문:

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

위치:

* **[!DNL object]**:객체의 이름(예:배달, 공급자 등).
개체는 다음과 같습니다.
   * **[!DNL delivery]**:현재 배달을 참조하십시오(아래 하위 섹션의 세부 사항 및 제한 사항 참조).
   * **[!DNL provider]**:현재 배달 공급자/경로 지정(nms:externalAccount)에 대해 지정합니다.
   * 추가 스크립트 개체:객체를 다음 방법으로 컨텍스트에서 로드한 경우&#x200B;**속성** > **개인화** > **실행 컨텍스트에 개체 추가**.
   * 예측 루프의 항목:아래의 [예측](#foreach) 섹션을 참조하십시오.
* **[!DNL xpath]**:필드의 xpath입니다.
* **[!DNL index]** (선택 사항):배열 **[!DNL object]** 인 경우(추가 스크립트 객체의 경우) 배열의 항목 인덱스(0부터 시작)입니다.

### [!DNL delivery] 개체 {#delivery-object}

이메일 개인화의 경우 다음 두 가지 방법으로 전달 개체에 액세스할 수 있습니다.

* JavaScript 사용:

   ```
   <%= delivery.myField %>`.
   ```

   JavaScript 개체 배달 사용자 정의 필드는 지원되지 않습니다. MTA는 기본 제공 스키마에만 액세스할 수 있으므로 MTA에서는 미리 보기에서 작동하지만 MTA에서는 작동하지 않습니다.

* 사전 처리 사용:

   ```
   <%@ value object="delivery"
   ```


**주의 사항**

mid-sourcing을 통해 전송된 납품에 대해 다음 지침을 사용하는 경우, 사용자 지정 필드 **@myCustomField**&#x200B;을 마케팅 및 중간 소싱 플랫폼 모두에서 nms:delivery 스키마에 추가해야 합니다.

```
<%@ value object="delivery" xpath="@myCustomField" %>
```

배달 매개 변수/변수의 경우 다음 구문을 사용합니다(전달 객체 사용).

```
<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>
```

### [!DNL value] javascript 섹션  {#value-in-javascript}

Javascript 섹션에서 &lt;%@ 값을 사용할 수 있도록 두 개의 특수 개체가 &lt;% 및 %>로 대체됩니다.

```
<%@ value object='startScript' %>
<%@ value object='endScript' %>
```

예제:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## [!DNL foreach] {#foreach}

이 명령을 사용하면 전달에 로드된 객체의 배열에서 반복을 통해 객체와 관련된 개별 링크를 추적할 수 있습니다.

구문:

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>
```

위치:

* **[!DNL object]**:시작할 객체의 이름(일반적으로 추가 스크립트 객체)이지만 배달일 수 있습니다.
* **[!DNL xpath]** (선택 사항):반복할 컬렉션의 xpath입니다. 기본값은 &quot;.&quot;입니다. 즉, 객체가 루프할 배열입니다.
* **[!DNL index]** (선택 사항):xpath가 &quot;&quot;이(가) 아닌 경우 및 개체는 배열 자체이며 객체의 항목 인덱스입니다(0부터 시작).
* **[!DNL item]** (선택 사항):액세스 가능한 새 개체의 이름  &lt;> 스키마에 링크 이름이 있는 기본값입니다.

예제:

게재 속성/개인화에서 수신자와 아티클 간의 아티클 및 관계 테이블을 로드합니다.

이러한 아티클에 대한 링크 표시는 다음과 같이 Javascript를 사용하여 간단하게 수행할 수 있습니다.

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

이 솔루션을 사용하면 모든 문서에 대한 링크가 구별없이 추적됩니다. 받는 사람이 아티클 링크를 클릭했음을 알 수 있지만 어떤 아티클이 있는지 알 수 없습니다.

해결 방법은 다음과 같습니다.

1. 가능한 모든 아티클을 배달의 추가 스크립트 배열에 미리 로드합니다(아티클 목록[]). 이는 가능한 아티클의 수가 한정되어야 함을 의미합니다.
1. 컨텐츠 시작 부분에 JavaScript 함수를 작성합니다.

   ```
   <%@ value object='startScript' %>
   function displayArticle(articleId)
   {
     <%@ foreach object="articleList" item="article" %>
       if( articleId == <% value object="article" xpath="@id" %> ) 
       {
         <%@ value object='endScript' %>
           <a href="http://nl.net?a.jsp?article=<%@ value object="article" xpath="@id" %>">article</a>
         <%@ value object='startScript' %>
       } 
     <%@ end @%>
   }
   <%@ value object='endScript' %>
   ```

1. 함수를 호출하여 아티클을 표시합니다.

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```
