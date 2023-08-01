---
product: campaign
title: 사이트에 웹 추적 태그 삽입
description: 사이트에 웹 추적 태그를 삽입하는 방법 알아보기
feature: Configuration
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
exl-id: e7fcec75-82fe-45ff-8d45-7d6e95baeb14
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# 사이트에 웹 추적 태그 삽입{#inserting-tags-in-your-site}

## 간단한 방법 {#simple-method}

이 메서드는 를 삽입하여 리디렉션 서버로 HTTP 호출을 보내는 것으로 구성됩니다. **`<img>`** 추적하려는 웹 페이지의 HTML 소스 코드에 있는 HTML 태그입니다.

>[!IMPORTANT]
>
>이 방법은 웹 브라우저에서 보낸 쿠키를 사용하여 수신자를 식별하며 100% 신뢰할 수 없습니다.

**예제**:

```
<img height='0' width='0' alt='' src='https://localhost/r/12343?tagid=home'
```

삽입된 태그는 리디렉션 서버에 연결됩니다.

![](assets/d_ncs_integration_webtracking_structure2.png)

콘솔에서 추적할 페이지를 정의할 때 샘플 웹 추적 태그를 생성하여 웹 페이지의 소스 코드에 복사하여 붙여넣을 수 있습니다.

그러나 TRANSACTION 유형 태그를 사용하는 경우, 트랜잭션 정보(금액, 항목 수)와 확장 스키마에 의해 정의된 정보를 삽입하려면 JavaScript를 사용하여 샘플 태그를 수정해야 합니다.

### 태그의 정적 삽입 {#static-insertion-of-tags}

정적 태그 삽입을 수행하려면 콘솔에서 생성했거나 수동으로 구성한 태그를 복사하여 웹 페이지의 소스에 붙여넣으면 됩니다.

**예**: 양식을 표시하는 페이지에 웹 추적 태그 삽입

```
<html>
  <...>
  <body>
  <script>
      document.write("<img height='0' width='0' alt='' src='https://localhost/r/" + Math.random().toString() + "?tagid=home'>");
    </script>
    <noscript>
     <img height='0' width='0' alt='' src='https://localhost/r/?tagid=home'>
    </noscript>
    <h1>My site</h1>
    <form action="http://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

확인 페이지(&quot;amount.md&quot;)에 트랜잭션 유형 웹 추적 태그 삽입.

```
<html>
  <body>
    <script>
      function getURLparam(name) 
      {
        var m = location.search.match new RegExp("[?&]" + name + "=([^&]+)"));
        return m ? unescape(m[1]) : "";
      }
 
       var params = "https://localhost/r/" + Math.random().toString() + "?tagid=amount&amount="
                      +getURLparam("amount")+"&article="+getURLparam("quantity");
       document.write("<img height='0' width='0' src='"+params+"'/>");
    </script>

    <h1>Approval confirmation</h1>
  </body>
</html>
```

### 웹 추적 태그의 동적 생성 {#dynamic-generation-of-web-tracking-tags}

웹 페이지가 동적으로 생성되면 페이지 생성 시 웹 추적 태그를 추가할 수 있습니다.

**예**: 웹 추적이 JSP에 추가되었습니다.

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <img height='0' width='0' alt='' src='https://localhost/r/<%=new Random().nextInt()%>?tagid=home'>
    <h1>My site</h1>
    <form action="https://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <%  
      String strParams = new Random().nextInt() + "?tagid=amount";
      strParams += "&amount="+request.getParameter("amount");
      strParams += "&article="+request.getParameter("quantity");
    %>
    <img height='0' width='0' alt=''
     src='http://localhost/r/<%=strParams%>'>
    <h1>Approval confirmation</h1>
    </body>
</html>
```

## 최적 방법 {#optimum-method-}

리디렉션 서버로 전송되는 정보를 제어하려는 경우 페이지 생성 언어를 사용하여 HTTP 쿼리를 동기적으로 직접 수행하는 것이 가장 안정적인 방법입니다.

생성하는 URL은에 정의된 구문 규칙을 준수해야 합니다. [웹 추적 태그: 정의](../../configuration/using/web-tracking-tag--definition.md).

![](assets/d_ncs_integration_webtracking_structure3.png)

>[!NOTE]
>
>리디렉션 및 웹 추적은 쿠키를 사용하며, 동기 HTTP 호출을 수행하는 웹 서버가 리디렉션 서버와 동일한 도메인에 있는 것이 중요합니다. 다양한 HTTP 교환은 &#39;id&#39;, &#39;uuid&#39; 및 &#39;uuid230&#39; 쿠키를 전달해야 합니다.

**예**: 계정 번호를 사용한 수신자 인증을 사용하는 Java의 동적 생성.

```
[...]
  // Recipient account, amount and articles
  String strAccount = request.getParameter("account");
  String strAmount = request.getParameter("amount");
  String strArticle = request.getParameter("article");

  StringBuffer strCookies = new StringBuffer();
  String strSetCookie = null;

  // Get cookies from client request
  Cookie[] cookies = request.getCookies();
  for(int i=0; i< cookies.length; i++ )
  {
    Cookie c = cookies[i];
    String strName = c.getName();
    if( strName.equals("id") || strName.equals("uuid") || strName.equals("uuid230") )
      // Helper function to add cookies in string
      AddCookie(strCookies, c);
  }
  // Now perform a synchronous HTTP request to inform redirection server
  // Add a tagid in auto-discover mode, and a default jobId to use (in hexa)
  StringBuffer strURL = new StringBuffer("https://www.adobe.com/r/a?tagid=cmd_page%7Ct&jobid=27EE");
  if( strAccount != null )
    AddParameter(strURL, "rcpid", "saccount="+strAccount);
  if( strAmount != null )
    AddParameter(strURL, "amount", strAmount);
  if( strArticle != null )
    AddParameter(strURL, "article", strArticle);
  
  URL url = new URL(strURL.toString());
  HttpURLConnection connection = (HttpURLConnection)url.openConnection();
  // Add the client cookies
  if( strCookies.length() > 0 )
    connection.setRequestProperty("Cookie", strCookies.toString());

  int errcode = connection.getResponseCode();

  // Now add the Adobe Campaign cookies if the server returned one :
  if( errcode == 200 )
  {
    strSetCookie = connection.getHeaderField("Set-Cookie");
    if( strSetCookie != null && strSetCookie.length() > 0 )
      response.addHeader("Set-Cookie", strSetCookie);
  }
  [...]
```
