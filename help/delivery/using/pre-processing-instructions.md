---
product: campaign
title: 추적된 URL에 대한 전처리 지침
description: 이메일의 URL을 스크립팅하고 계속 추적하는 데 사용하는 전처리 지침에 대해 자세히 알아보십시오
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Monitoring
role: User, Data Engineer, Developer
exl-id: 9d3f5c74-377a-4e24-81e5-bb605f69cf8a
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 2%

---

# 전처리 지침 {#pre-processing-instructions}

게재 콘텐츠의 특정 구문을 사용하여 지침을 추가하고 추적된 이메일의 URL을 스크립팅할 수 있습니다. &lt;%@ 지침은 JavaScript가 아닙니다. 이 구문은 Adobe Campaign에만 적용됩니다.

게재 콘텐츠 컨텍스트에서만 적용됩니다. 이메일 URL을 스크립팅하고 계속 추적할 수 있는 유일한 방법입니다(URL 매개 변수 제외). 추적할 링크를 탐지하기 전에 게재 분석 중에 적용된 자동 복사/붙여넣기로 볼 수 있습니다.

지침에는 세 가지 유형이 있습니다.

* **[!DNL include]**: 주로 옵션, 개인화 블록, 외부 파일 또는 페이지의 일부 코드를 팩터링합니다. [자세히 알아보기](#include)
* **[!DNL value]**: 게재 필드, 게재 변수 및 게재에 로드된 사용자 지정 개체에 대한 액세스 권한을 부여합니다. [자세히 알아보기](#value)
* **[!DNL foreach]**: 사용자 지정 개체로 로드된 배열을 루프합니다. [자세히 알아보기](#foreach)

게재 마법사에서 직접 테스트할 수 있습니다. 이러한 속성은 콘텐츠 미리 보기에서, 그리고 URL 목록을 보기 위해 추적 단추를 클릭할 때 적용됩니다.

## [!DNL include] {#include}

다음은 가장 일반적으로 사용되는 예입니다.

* 미러 페이지 링크 포함:

  ```
  <%@ include view="MirrorPage" %>  
  ```

* 미러 페이지 URL:

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

  게재 마법사의 개인화 버튼을 사용하여 올바른 구문을 가져옵니다.

## [!DNL value] {#value}

이 지침은 모든 수신자에 대해 일정한 게재 매개 변수에 대한 액세스를 제공합니다.

구문:

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

위치:

* **[!DNL object]**: 개체 이름(예: 게재, 공급자 등)입니다.
객체는 다음과 같을 수 있습니다.
   * **[!DNL delivery]**: 현재 게재용 (아래 하위 섹션에서 세부 정보 및 제한 사항 참조).
   * **[!DNL provider]**: 현재 게재 공급자/라우팅(nms:externalAccount)용
   * 추가 스크립트 객체: 다음을 통해 컨텍스트에 객체가 로드되는 경우 **속성** > **개인화** > **실행 컨텍스트에 개체 추가**.
   * foreach 루프의 항목: 참조 [Foreach](#foreach) 아래 섹션.
* **[!DNL xpath]**: 필드의 xpath
* **[!DNL index]** (선택 사항): **[!DNL object]** 는 배열의 항목 인덱스인 배열(추가 스크립트 객체의 경우)입니다(0에서 시작).

### [!DNL delivery] 오브젝트 {#delivery-object}

이메일 개인화의 경우 게재 오브젝트는 다음 두 가지 방법으로 액세스할 수 있습니다.

* JavaScript 사용:

  ```
  <%= delivery.myField %>`.
  ```

  JavaScript에서는 사용자 지정 필드 게재가 지원되지 않습니다. MTA는 기본 제공 게재 스키마에만 액세스할 수 있으므로 미리 보기에서는 작동하지만 MTA에서는 작동하지 않습니다.

* 전처리 사용:

  ```
  <%@ value object="delivery"
  ```


**주의**

중간 소싱을 통해 전송된 게재에 대해 다음 지침을 사용하는 경우, 사용자 정의 필드 **@myCustomField** 마케팅 및 중간 소싱 플랫폼 모두에서 nms:delivery 스키마에 추가되어야 합니다.

```
<%@ value object="delivery" xpath="@myCustomField" %>
```

게재 매개 변수/변수의 경우 다음 구문(게재 개체 사용)을 사용하십시오.

```
<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>
```

### [!DNL value] Javascript 섹션에서 {#value-in-javascript}

Javascript 섹션에서 &lt;%@ 값 사용을 허용하려면 두 개의 특수 개체가 &lt;% 및 %>(으)로 대체됩니다.

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

이 명령을 사용하면 게재에 로드된 개체 배열에서 반복을 사용하여 개체와 관련된 개별 링크를 추적할 수 있습니다.

구문:

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>
```

위치:

* **[!DNL object]**: 시작할 오브젝트의 이름(일반적으로 추가 스크립트 오브젝트)이지만 게재가 될 수 있습니다.
* **[!DNL xpath]** (선택 사항): 반복할 컬렉션의 xpath입니다. 기본값은 &quot;.&quot;입니다. 즉, 개체는 반복할 배열입니다.
* **[!DNL index]** (선택 사항): xpath가 &quot;.&quot;가 아닌 경우 그리고 개체는 배열 자체이며, 개체의 항목 인덱스입니다(0에서 시작).
* **[!DNL item]** (선택 사항): foreach 루프 내에서 &lt;%@ 값으로 액세스할 수 있는 새 개체의 이름입니다. 스키마에 링크 이름이 있는 기본값.

예제:

게재 속성/개인화에서 문서 배열 및 수신자와 문서 간의 관계 테이블을 로드합니다.

이러한 문서에 대한 링크를 표시하는 것은 다음과 같이 Javascript를 사용하여 간단히 수행할 수 있습니다.

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

해당 솔루션을 사용하면 모든 문서에 대한 링크를 구분 없이 추적할 수 있습니다. 수신자가 문서 링크를 클릭했음을 알 수 있지만, 어떤 문서에 대해 알 수는 없습니다.

해결 방법은 다음과 같습니다.

1. 게재의 추가 스크립트 배열에 가능한 모든 문서를 미리 로드합니다. - articleList[] - 이것은 가능한 유한한 수의 물품이 있어야 한다는 것을 의미합니다.
1. 콘텐츠의 시작 부분에 JavaScript 함수를 작성합니다.

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

1. 함수를 호출하여 문서를 표시합니다.

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```
