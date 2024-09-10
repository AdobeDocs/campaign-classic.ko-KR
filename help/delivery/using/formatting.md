---
product: campaign
title: 양식화
description: 양식화
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Email Design
role: User, Developer, Data Engineer
exl-id: d9688dc4-20c6-4a9a-990f-465f39b2faa2
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '1451'
ht-degree: 0%

---

# 양식화{#formatting}

## JavaScript 템플릿 {#javascript-templates}

JavaScript 템플릿은 JavaScript 코드가 포함된 HTML 또는 텍스트 문서입니다. 게재 작업의 이메일 콘텐츠와 동일한 방식으로 구성됩니다.

### JavaScript 템플릿 식별 {#identification-of-a-javascript-template}

JavaScript 템플릿은 스키마 및 양식과 마찬가지로 이름 및 네임스페이스로 식별됩니다. 그러나 템플릿 이름에 **.js** 옵션을 추가하는 것이 좋습니다.

### JavaScript 템플릿의 구조 {#structure-of-a-javascript-template}

&quot;cus:book&quot; 스키마를 기반으로 하는 JavaScript HTML 서식 템플릿의 예입니다.

```
<html>
  <body>
    <!-- Title of book -->
    <h1><%= content.@name %></h1>
    <ul>
      <% for each(var chapter in content.chapter) { %>
        <li><%= chapter.@name %></li>
      <% }%>
    </ul>
  </body>
</html>
```

다양한 JavaScript 지시문은 다음 양식으로 표시됩니다.

* 필드 병합: **`<%= <source> %>`** 구문을 사용하여 데이터의 내용을 표시합니다. 여기서 `<source>`은(는) 표시할 데이터의 원본 필드입니다.
* 지침 블록: &lt;% 및 %> 태그 사이에 포함된 일련의 JavaScript 지침을 실행합니다.

**content** 개체는 입력 XML 문서의 주 요소를 나타냅니다.

이 예제에서 다음 줄에는 장부 이름의 내용이 표시됩니다.

```
<h1><%= content.@name %></h1>
```

다음 코드는 `<chapter>` 컬렉션 요소에서 반복합니다.

```
<% for each(var chapter in content.chapter) { %>
  <li><%= chapter.@name %></li>
<% }%>
```

컨텐츠의 속성 및 요소는 JavaScript 객체로 표시되며 소스 문서의 구조를 따릅니다.

**예**:

* **콘텐츠.@name**: 기본 요소의 &quot;name&quot; 특성 값을 검색합니다.
* **콘텐츠.@`['name']`**: **콘텐츠와 동일합니다.@name** 구문
* **content.chapter.length**: `<chapter` 컬렉션 요소의 요소 수를 반환합니다.
* **content.chapter`[0]`.@name**: 첫 번째 `<chapter>` 요소의 이름을 검색합니다.
* **chapter.name()**: `<chapter>` 요소의 이름을 반환합니다.
* **chapter.parent().name()**: `<chapter>`의 부모 요소 이름을 반환합니다.

>[!CAUTION]
>
>&#39;-&#39; 문자는 JavaScript 언어로 예약되어 있으므로 이 문자를 포함하는 모든 특성 또는 요소의 값을 `['<field>']` 구문을 통해 복구해야 합니다.
>
>예: `content.@['offer-id']`.

프로그래밍 언어의 모든 기능 (변수, 루프, 조건부 테스트, 함수 등). )를 사용하여 출력 문서를 구성할 수 있습니다. SOAP API는 출력 문서를 보강하는 데 액세스할 수 있습니다.

예:

* 조건부 테스트:

  ```
  <% if (content.@number == 1 || content.@language == 'en') { %>
  <!-- Content to be displayed if test is true--> 
  <% } %>
  ```

* 함수 호출:

  ```
  <!-- Displays a horizontal bar -->
  ;<% function DisplayHorizontalBar() { %>
    <hr/>
  <% } %> 
  
  <!-- The same function in a block  -->
  <% 
  function DisplayHorizontalBar2()
  {
    document.write('<hr/>');
  }
  %> 
  
  <!-- Returns the value in uppercase -->
  <% 
  function formatName(value)
  { 
    return value.toUpperCase(); 
  }
  %>
  
  <!-- Call functions -->
  <%= DisplayHorizontalBar1() %>
  <%= DisplayHorizontalBar2() %>
  <%= formatName(content.@name) %>
  ```

* 선언 및 변수 호출:

  ```
  <%  var counter = 0; %>
  
  <%= counter += 10 %>
  ```

* 정적 메서드를 사용한 수신자 이름 검색 및 표시:

  ```
  <% var recipient = nms.recipient.get(1246); %>
  <%= recipient.lastName %>
  ```

* 비정적 메서드를 사용한 수신자 이름 복구 및 표시:

  ```
  <% var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr="@id=1246"/>
      </where>
    </queryDef>);
  
    var recipient = query.ExecuteQuery();
  %>
  
  <%= recipient.@lastName %>
  ```

### JavaScript 템플릿 포함 {#including-a-javascript-template}

나중에 사용할 수 있도록 함수 또는 변수 라이브러리를 구성할 수 있습니다. 이렇게 하려면 **eval** 함수와 함께 JavaScript 템플릿을 가져옵니다. 이를 통해 다른 JavaScript 템플릿에서 선언된 추가 기능으로 컨텍스트를 보강할 수 있습니다.

**예**: **common.jsp** 템플릿을 가져오는 중

```
<% eval(xtk.javascript.get("cus:common.js").data);  %>
```

### JavaScript 템플릿 편집 {#editing-a-javascript-template}

편집 영역을 사용하면 JavaScript 템플릿의 콘텐츠를 채울 수 있습니다.

![](assets/d_ncs_content_form16.png)

>[!NOTE]
>
>JavaScript 개체의 초기화를 위해 관련 데이터 모델 스키마를 채워야 합니다.

언제든지 출력 문서의 미리 보기를 생성하려면 내용과 출력 형식(HTML, 텍스트, XML)을 선택한 다음 **[!UICONTROL Generate]** 을 클릭합니다.

![](assets/d_ncs_content_form17.png)

>[!NOTE]
>
>출력 문서를 미리 보기 위해 변경 사항을 저장할 필요는 없습니다.

### JavaScript 템플릿을 만들고 사용하는 방법의 예 {#example-of-how-to-create-and-use-a-javascript-template}

아래에서는 JavaScript 템플릿을 사용하여 다음 콘텐츠 관리를 구현하는 데 필요한 구성을 찾을 수 있습니다.

![](assets/d_ncs_content_sample_1.png)

이 예에는 다음 단계가 포함됩니다.

1. 다음 스키마를 만듭니다(이 경우: **neo:news**).

   ```
   <srcSchema _cs="Invitation (neo)"   entitySchema="xtk:srcSchema" img="xtk:schema.png" label="Invitation" mappingType="sql" name="news" namespace="neo" xtkschema="xtk:srcSchema">
   
     <enumeration basetype="string" default="en" name="language">
       <value label="Français" name="fr" value="fr"/>
       <value label="English" name="gb" value="gb"/>
     </enumeration>
   
     <enumeration basetype="string" name="css">
       <value label="Blue" name="bl" value="blue"/>
       <value label="Orange" name="or" value="orange"/>
     </enumeration>
   
     <element label="Intervenants" name="attendee">
       <key internal="true" name="id">
         <keyfield xpath="@id"/>
       </key>
       <attribute label="Name" name="name" type="string"/>
       <element label="Image" name="image" target="xtk:fileRes" type="link"/>
       <attribute label="Description" name="description" type="string"/>
       <attribute default="Gid()" label="Id" name="id" type="long"/>
     </element>
   
     <element label="Invitation" name="news" template="ncm:content" xmlChildren="true">
   
       <compute-string expr="@name"/>
       <attribute enum="language" label="Language" name="language" type="string"/>
       <attribute enum="css" label="Stylesheet" name="css" type="string"/>
       <attribute label="Title" name="title" type="string"/>
       <element label="Presentation" name="presentation" type="html"/>
       <attribute label="Date" name="date" type="date"/>
       <element label="Attendees list" name="attendeesList" ordered="true" ref="attendee" unbound="true"/>
   
     </element>
   </srcSchema>
   ```

1. 연결된 **[!UICONTROL Content management]** 형식 양식(**neo:news**) 만들기

   ```
   <form _cs="News (neo)" entitySchema="xtk:form"  img="xtk:form.png" label="News"  name="news" namespace="neo" type="contentForm" xtkschema="xtk:form">
   
     <container type="iconbox">
       <container label="Invitation">
         <input xpath="@langue"/>
         <input xpath="@css"/>
         <input xpath="@title"/>
         <input xpath="@date"/>
         <input xpath="presentation"/>
       </container>
   
       <container label="Intervenants">
         <container toolbarCaption="Liste des intervenants" type="notebooklist" xpath="attendeesList" xpath-label="@nom">
           <container>
             <input xpath="@nom"/>
             <input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
               <sysFilter>
                 <condition expr="@isImage = true"/>
               </sysFilter>
             </input>
             <input xpath="@description"/>
           </container>
         </container>
       </container>
     </container>
   
   </form>
   ```

1. HTML 및 텍스트 형식에 대한 메시지 콘텐츠로 JavaScript 템플릿을 만듭니다.

   * 이 예에서 HTML은

     ```
     <html>     
       <head>         
         <title>Newsletter</title>
          <style type="text/css">
           .body {font-family:Verdana, Arial, Helvetica, sans-serif; font-size:10px; color:#514c48; margin-left: auto; margin-right: auto;}
           .body table {width:748; border: solid 1px; cellpadding:0; cellspacing:0"}
          </style>
       </head>     
       <body>
         <p><center><%= mirrorPage %></center></p>
         <center>
           <table>      
            <tr>
             <td>                                                         
               <img src="[LOGO]"/>                                   
             </td>
             <td>
               <h1><%= content.@title %></h1>
             </td>
            </tr>
            <tr>
     
            <td>
             <div >                                    
               <h0><%= hello,</h0>                              
               <p><%= content.presentation %></p>                                          
     
               <h0>Useful information</h0>                              
               <p>                                  
                 <img src="[IMAGE 1]"/>When? <br/><%= formatDate(content.@date, "%2D %Bl %4Y") %> From 10 AM in your bookshop.</p><br/>                                       
               <p>                                  
                 <img src="[IMAGE 2]"/>Who? <br>Meet our favorite authors and illustrators and get a signed copy of their book.</p><br/>                                                         
               <p>                                  
                 <img src="[IMAGE 3]"/>Attendance is free but there is a limited number of seats: sign up now!</p>
           </div>
           </td>
     
             <td>                                                    
              <div style="text-align:left; width:210; height:400px; background:url([IMAGE DE FOND])">
     
                 <h0><%= participant %></h0>
                 <%
                 var i
                 var iLength = content.attendeesList.length()
                 for (i=0; i<iLength; i++)
                 { %>
                 <p>
                   <%= generateImgTag(content.attendeesList[i].@["image-id"]) %>  <%= content.attendeesList[i].@description %>
                 </p>  
                 <% }  
                 %>                              
              </div2>
             </td>
         </tr>
       </table>
     </center>
     </body>    
     </html>
     ```

   * 텍스트의 경우:

     ```
     <%= content.@title %>
     <%= content.presentation %>
     
     *** When? On <%= formatDate(content.@date, "%2D %Bl %4Y") %> From 10 AM in your bookshop.
     
     *** Who? Come and meet our favorite authors and illustrators and get a signed copy of their books. 
     
     *** Attendance is free but there is a limited number of seats: sign up now!
     
     Guests:
     ******************
     <%
     var i
     var iLength = content.attendeesList.length()
     //for (i=(iLength-1); i>-1; i--)
     for( i=0 ; i<iLength ; i++ )
       { %>
       Description <%= i %> : <%= content.attendeesList[i].@description %>
       <% }  
     %>
     ```

1. 이제 두 형식 모두에 사용되는 게시 템플릿을 만듭니다.

   * HTML:

     ![](assets/d_ncs_content_sample_2.png)

   * 텍스트의 경우:

     ![](assets/d_ncs_content_sample_3.png)

1. 그런 다음 게재에서 이 콘텐츠 템플릿을 사용할 수 있습니다.

   자세한 내용은 [콘텐츠 템플릿 사용](using-a-content-template.md)을 참조하세요.

## XSL 스타일시트 {#xsl-stylesheets}

XSLT 언어를 사용하면 XML 문서를 출력 문서로 변경할 수 있습니다. 스타일시트의 출력 방법에 따라 HTML, 일반 텍스트 또는 다른 XML 트리에서 결과 문서를 생성할 수 있습니다.

이 변환은 스타일시트라고 하는 문서에서 XML에 자세히 설명되어 있습니다.

### 스타일시트 식별 {#identifying-a-stylesheet}

스타일시트는 스키마 및 양식과 마찬가지로 이름 및 네임스페이스로 식별됩니다. 그러나 스타일시트 이름에 **.xsl** 확장을 추가하는 것이 좋습니다.

스타일시트의 식별 키는 네임스페이스와 콜론으로 구분된 이름으로 구성된 문자열입니다(예: **cus:book.xsl**).

### 스타일시트 구조 {#structure-of-a-stylesheet}

예제 스키마 &quot;cus:book&quot;을 기반으로 한 HTML 서식 스타일시트의 예:

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>
  <!-- Point of entry of the stylesheet -->
  <xsl:template match="/book">
    <html>
      <body>
        <!-- Book title -->
        <h1><xsl:value-of select="@name"/></h1>
        <lu>
          <!-- List of chapters -->
          <xsl:for-each select="child::chapter">
            <li><xsl:value-of select="@name"/></li>
          </xsl:for-each>
       </lu>
      </body>
    </html>
   </xsl:template>
</xsl:stylesheet>
```

스타일시트는 다음 규칙을 따르는 XML 문서입니다.

* 속성 값은 따옴표 사이에 있습니다.
* 요소에는 여는 표식과 닫는 표식이 있어야 합니다.
* &#39;&lt;&#39; 또는 &#39;&amp;&#39; 문자를 **&#39;&lt;&#39;** 또는 **&#39;&amp;&#39;** 엔터티로 바꾸고,
* 각 XSL 요소는 **xsl** 네임스페이스를 사용해야 합니다.

스타일시트는 XSL 루트 요소 마커 **`<xsl:stylesheet>`**(으)로 시작하고 **`</xsl:stylesheet>`** 마커로 끝나야 합니다. XSL 네임스페이스는 여는 마커에 다음과 같이 정의해야 합니다.

```
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

**`<xsl:output>`** 요소는 생성된 문서의 형식을 지정합니다. 원하는 문자 집합과 출력 형식을 지정합니다.

```
<xsl:output encoding="ISO-8859-1" method="html"/>
```

다음은 출력 문서의 서식을 지정하기 위한 스타일시트의 구성에 대해 설명합니다.

```
<xsl:template match="/book">
  <html>
    <body>
      <!-- Book title -->
      <h1><xsl:value-of select="@name"/></h1>
      <lu>
        <!-- List of chapters -->
        <xsl:for-each select="child::chapter">
          <li><xsl:value-of select="@name"/></li>
        </xsl:for-each>
      </lu>
    </body>
  </html>
</xsl:template>
```

기본적으로 XSLT 프로세서는 입력 XML 문서의 루트 또는 주 노드에 적용되는 **template**&#x200B;을(를) 찾습니다. 출력 문서의 구성은 이 **템플릿**(으)로 시작됩니다.

이 예제에서 HTML 페이지는 책 이름과 챕터 목록을 표시하여 &quot;cus:book&quot; 스키마에서 생성됩니다.

>[!NOTE]
>
>XSLT 언어에 대한 자세한 내용은 XSLT 참조 문서를 참조하십시오.

### HTML/XML 표시 {#displaying-html-xml}

**html** 필드를 표시하려면 **`<xsl:value-of>`** 지시문에서 **disable-output-escaping=&quot;yes&quot;** 옵션을 사용하십시오. 이렇게 하면 문자를 XML 엔티티로 바꾸지 않을 수 있습니다(예: &lt; 를 &lt; 로 바꾸기).

**disable-output-escaping=&quot;yes&quot;** 옵션이 있는 **`<xsl:text>`** 지시문을 사용하면 개인화 필드 또는 조건부 테스트를 위해 JavaScript 태그를 삽입할 수 있습니다.

예:

* &quot;html&quot; 유형 필드의 내용 표시:

  ```
  <xsl:value-of select="summary" disable-output-escaping="yes"/>
  ```

* 개인화 필드 **&lt;%= recipient.email %>** 삽입:

  ```
  <xsl:text disable-output-escaping="yes"><%= recipient.email %></xsl:text>
  ```

* 조건부 테스트 **&lt;% 추가 중(recipient.language == &#39;en&#39;) `{` %>**:

  ```
  <xsl:text disable-output-escaping="yes"><% if (recipient.language == 'en') { %></xsl:text>
  ```

### 스타일시트 포함 {#including-stylesheets}

여러 스타일시트에서 공유할 템플릿 또는 변수 라이브러리를 빌드할 수 있습니다. 위에 제시된 &quot;longMonth&quot; **template**&#x200B;은 나중에 재사용할 수 있도록 스타일시트에서 원격으로 템플릿을 찾을 수 있는 대표적인 장점입니다.

**`<xsl:include>`** 지시문은 문서에 포함할 스타일시트의 이름을 나타냅니다.

**예**: &quot;common.xsl&quot; 스타일 시트를 포함합니다.

```
<? xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:include href="common.xsl"/> 
  <xsl:output encoding="ISO-8859-1" method="jsp" indent="yes"/>
  ...
</xsl:stylesheet>
```

>[!NOTE]
>
>포함할 스타일시트의 참조에 네임스페이스 이름을 입력해서는 안 됩니다. 표준으로 이 스타일시트는 사용자 네임스페이스로 만들어집니다.

### 스타일시트 편집 {#editing-a-stylesheet}

편집 영역을 사용하면 스타일시트의 컨텐트를 채울 수 있습니다.

![](assets/d_ncs_content_form14.png)

언제든지 출력 문서의 미리 보기를 생성하려면 컨텐츠 인스턴스와 형식(HTML, 텍스트, XML)을 선택한 다음 **[!UICONTROL Generate]** 을 클릭합니다.

![](assets/d_ncs_content_form15.png)

>[!NOTE]
>
>출력 문서 미리보기를 보기 위해 스타일시트에 변경 사항을 저장할 필요가 없습니다.

## 이미지 관리 {#image-management}

### 이미지 참조 {#image-referencing}

HTML 출력 문서에 입력된 이미지는 절대 또는 상대 참조로 참조될 수 있습니다.

상대 참조를 사용하면 **NcmResourcesDir** 및 **NcmResourcesDirPreview** 옵션에 이미지가 포함된 서버의 URL을 입력할 수 있습니다. 이러한 옵션에는 Adobe Campaign 클라이언트 콘솔에서 게시 및 미리 볼 이미지 위치가 포함되어 있습니다.

이 두 옵션은 **[!UICONTROL Administration > Platform > Options]** 폴더의 옵션 관리 화면을 통해 액세스할 수 있습니다.

**예**:

* NcmResourcesDir = &quot;https://server/images/&quot;
* NcmResourcesDirPreview = &quot;x:/images/&quot;

스타일시트 처리 중에 입력 XML 문서의 기본 요소에 있는 **_resPath** 특성은 컨텍스트(미리 보기 또는 게시)에 따라 하나 이상의 옵션으로 자동으로 채워집니다.

이미지 배치 옵션을 사용하는 방법과 해당 옵션을 이미지에 사용하는 방법의 예:

```
<img src="<%= content.@_resPath %>/newsletter/image.png"/>
```

>[!NOTE]
>
>이미지가 저장된 서버의 참조(이 예제에서는 &quot;resPath&quot;)를 포함하는 변수를 선언하는 것이 좋습니다.

### 공개 리소스 사용 {#using-public-resources}

배포 마법사에 입력한 인스턴스 설정에 따라 **[!UICONTROL Public resources]**&#x200B;을(를) 사용하여 이미지를 선언하고 서버에 업로드할 수도 있습니다.

그런 다음 콘텐츠에서 이러한 이미지를 호출할 수 있습니다. 이렇게 하려면 컨텐츠 관리 스키마에서 다음 구문을 사용합니다.

```
<element label="Image" name="image" target="xtk:fileRes" type="link"/>
```

양식에서 이미지를 선택하는 필드는 다음 구문을 통해 추가됩니다.

```
<input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
    <sysFilter>
      <condition expr="@isImage = true"/>
    </sysFilter>
  </input>
```

>[!NOTE]
>
>**[!UICONTROL Public resources]** 및 구성 및 사용 방법에 대한 자세한 내용은 [이 섹션](../../installation/using/deploying-an-instance.md#managing-public-resources)을 참조하세요.

## 날짜 표시 {#date-display}

XML 입력 문서에서 날짜는 내부 XML 형식으로 저장됩니다. **`YYYY/MM/DD HH:MM:SS`**(예: `2018/10/01 12:23:30`).

Adobe Campaign에서는 아래에 자세히 설명된 JavaScript 템플릿 및 XSL 스타일시트에 대한 날짜 서식 함수를 제공합니다.

### JavaScript 날짜 서식 {#javascript-date-formatting}

원하는 형식으로 날짜를 표시하기 위해 Adobe Campaign은 날짜의 내용을 입력으로 사용하는 **formatDate** 함수와 다음 구문을 사용하여 출력 형식을 지정하는 문자열을 제공합니다. **%4Y/%2M/%2D %2H%2N%2S**

예:

* 날짜를 **31/10/2018** 형식으로 표시:

  ```
   <%= formatDate(content.@date, "%2D/%2M/%4Y") %>
  ```

* 날짜를 **2018년 7월** 형식으로 표시:

  ```
  <%
   function displayDate(date)
    {
      var aMonth = 
      [ 'January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December' ];
  
      var month = formatDate(content.@date, "%2M")
      var year = formatDate(content.@date, "%4Y")
  
      return aMonth[month-1]+" "+year;
    }
  %>
  
  <%= displayDate(content.@date) %>
  ```

### XSL 날짜 서식 {#xsl-date-formatting}

XSLT 구문에는 표준 날짜 관리 함수가 없습니다. 원하는 형식으로 날짜를 표시하기 위해 Adobe Campaign에서는 외부 함수 **date-format**&#x200B;을(를) 제공합니다. 이 함수는 날짜의 콘텐츠와 다음 구문을 사용하여 출력 형식을 지정하는 문자열을 입력으로 사용합니다. **%4Y/%2M/%2D %2H%2N%2S**

예:

* 날짜를 **01/10/2018** 형식으로 표시하려면:

  ```
  <xsl:value-of select="external:date-format(@date, '%2D/%2M/%4Y')"/>
  ```

* 날짜를 **2018년 7월** 형식으로 표시하려면:

  ```
  <!-- Returns the month in the form of a string with the month number as input -->
  <xsl:template name="longMonth">
    <xsl:param name="monthNumber"/>
  
    <xsl:choose>
      <xsl:when test="$monthNumber = 1">January</xsl:when>
      <xsl:when test="$monthNumber = 2">February</xsl:when>
      <xsl:when test="$monthNumber = 3">March</xsl:when>
      <xsl:when test="$monthNumber = 4">April</xsl:when>
      <xsl:when test="$monthNumber = 5">May</xsl:when>
      <xsl:when test="$monthNumber = 6">June</xsl:when>
      <xsl:when test="$monthNumber = 7">July</xsl:when>
      <xsl:when test="$monthNumber = 8">August</xsl:when>
      <xsl:when test="$monthNumber = 9">September</xsl:when>
      <xsl:when test="$monthNumber = 10">October</xsl:when>
      <xsl:when test="$monthNumber = 11">November</xsl:when>
      <xsl:when test="$monthNumber = 12">December</xsl:when>
    </xsl:choose>
  </xsl:template> 
  
  <!-- Display date -->
  <xsl:call-template name="longMonth">
    <xsl:with-param name="monthNumber">
      <xsl:value-of select="external:date-format(@date, '%2M')"/>
    </xsl:with-param>
  </xsl:call-template>
   <xsl:value-of select="external:date-format(@date, '%4y')"/>
  ```
