---
title: 사이트에 태그 삽입
seo-title: 사이트에 태그 삽입
description: 사이트에 태그 삽입
seo-description: null
page-status-flag: never-activated
uuid: e5e4a431-2093-4d5a-acd2-0040b6ce3519
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 57988b00-62cc-43d3-a2eb-bfed5bff7dc1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 912507f25c5bc3c1ca7121b0df8182176900f4c0

---


# 사이트에 태그 삽입{#inserting-tags-in-your-site}

## 간단한 방법 {#simple-method}

이 메서드는 추적할 웹 페이지의 HTML 소스 코드에 HTML **`<img>`** 태그를 삽입하여 리디렉션 서버로 HTTP 호출을 전송하는 것으로 구성됩니다.

>[!CAUTION]
>
>이 방법은 웹 브라우저가 보낸 쿠키를 사용하여 받는 사람을 식별하며, 100% 신뢰할 수 없습니다.

**예**:

```
<img height='0' width='0' alt='' src='https://localhost/r/12343?tagid=home'
```

삽입된 태그가 리디렉션 서버에 연결됩니다.

![](assets/d_ncs_integration_webtracking_structure2.png)

콘솔에서 추적할 페이지를 정의할 때 샘플 웹 추적 태그를 생성하여 웹 페이지의 소스 코드에 복사하여 붙여 넣을 수 있습니다.

그러나 TRANSACTION-type 태그를 사용할 때는 트랜잭션 정보(금액, 항목 수) 및 확장 스키마로 정의된 정보를 삽입하려면 JavaScript를 사용하여 샘플 태그를 수정해야 합니다.

### 태그 정적 삽입 {#static-insertion-of-tags}

정적 태그 삽입을 수행하려면 콘솔에서 생성하거나 수동으로 구성한 태그를 복사하여 웹 페이지의 소스에 붙여넣으면 됩니다.

**예**:양식을 표시하는 페이지에 웹 추적 태그 삽입

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

확인 페이지에 TRANSACTION-type 웹 추적 태그 삽입(&quot;amount.md&quot;)

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

### 다이내믹한 웹 추적 태그 생성 {#dynamic-generation-of-web-tracking-tags}

웹 페이지가 동적으로 생성되면 페이지 생성 시 웹 추적 태그를 추가할 수 있습니다.

**예**:JSP에 웹 추적이 추가되었습니다.

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

리디렉션 서버로 전송된 정보를 제어하려면 페이지 생성 언어를 사용하여 HTTP 쿼리를 직접 동기식으로 수행하는 것이 가장 안정적인 방법입니다.

구성하는 URL은 웹 추적 태그에 정의된 구문 규칙을 따라야 [합니다.정의](../../configuration/using/web-tracking-tag--definition.md).

![](assets/d_ncs_integration_webtracking_structure3.png)

>[!NOTE]
>
>리디렉션 및 웹 추적은 쿠키를 사용하며, 동기식 HTTP 호출을 수행하는 웹 서버가 리디렉션 서버와 동일한 도메인에 있어야 합니다. 다양한 HTTP 교환은 &#39;id&#39;, &#39;uuid&#39; 및 &#39;uuid230&#39; 쿠키를 전달해야 합니다.

**예**:계정 번호를 사용한 수신자 인증을 사용하여 Java의 동적 생성

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

