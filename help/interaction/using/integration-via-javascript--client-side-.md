---
title: JavaScript를 통한 통합(클라이언트측)
seo-title: JavaScript를 통한 통합(클라이언트측)
description: JavaScript를 통한 통합(클라이언트측)
seo-description: null
page-status-flag: never-activated
uuid: 19cafecd-cf13-458a-857e-0a45c346f4ed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 7453d768-31eb-4372-aae3-27527cd5c79b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# JavaScript를 통한 통합(클라이언트측){#integration-via-javascript-client-side}

웹 페이지에서 상호 작용 엔진을 호출하려면 JavaScript 코드에 대한 호출을 페이지에 직접 삽입합니다. 이 호출은 타깃팅된

    요소.

JavaScript 통합 방법을 사용하는 것이 좋습니다.

URL을 호출하는 스크립트는 다음과 같습니다.

```
<script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=" type="text/javascript"></script>
```

&quot;**env**&quot; 매개 변수는 익명의 상호 작용을 위한 라이브 환경의 내부 이름을 받습니다.

오퍼를 발표하려면 Adobe Campaign에서 환경과 오퍼 공간을 만든 다음 HTML 페이지를 구성해야 합니다.

다음 사용 사례에서는 JavaScript를 통해 오퍼를 통합하는 가능한 옵션에 대해 자세히 설명합니다.

## HTML 모드 {#html-mode}

### 익명의 오퍼 제시 {#presenting-an-anonymous-offer}

1. **상호 작용 엔진 준비**

   Adobe Campaign 인터페이스를 열고 익명 환경을 준비합니다.

   익명 환경에 연결된 오퍼 공간을 만듭니다.

   오퍼 공간과 연결된 오퍼 및 표현을 만듭니다.

1. **HTML 페이지의 컨텐츠**

   HTML 페이지에는

   만든 오퍼 공간의 내부 이름(&quot;i_internal name space&quot;)의 값을 갖는 @id 속성을 갖는 요소입니다. 오퍼가 상호 작용에 의해 이 요소에 삽입됩니다.

   예제에서 @id 속성은 &quot;i_SPC12&quot; 값을 받습니다. 여기서 &quot;SPC12&quot;는 이전에 만든 오퍼 공간의 내부 이름입니다.

   ```
   <div id="i_SPC12"></div>
   ```

   이 예에서는 스크립트 호출을 위한 URL이 다음과 같습니다(&quot;OE3&quot;은 라이브 환경의 내부 이름입니다).

   ```
   <script id="interactionProposalScript" src="https://instance.adobe.org:8080/nl/interactionProposal.js?env=OE3" type="text/javascript"></script>
   ```

   >[!CAUTION]
   >
   >태그가 직접 닫히지 `<script>` 않아야 합니다.

   이 정적 호출은 상호 작용 엔진에 필요한 모든 매개 변수를 포함하는 동적 호출을 자동으로 생성합니다.

   이 동작을 사용하면 동일한 페이지에서 여러 오퍼 공간을 사용하여 엔진에 대한 단일 호출로 관리할 수 있습니다.

1. **HTML 페이지의 결과**

   오퍼 표현의 컨텐츠는 상호 작용 엔진에서 HTML 페이지로 반환됩니다.

   ```
   <div id="banner_header">
     <div id="i_SPC12">
       <table>
         <tbody>
           <tr>
             <td><h3>Fly to Japan!</h3></td>
           </tr>
           <tr>
             <td><img width="150px" src="https://instance.adobe.org/res/Track/874fdaf72ddc256b2d8260bb8ec3a104.jpg"></td>
             <td>
               <p>Discover Japan for 2 weeks at an unbelievable price!!</p>
               <p><b>2345 Dollars - All inclusive</b></p>
             </td>
           </tr>
         </tbody>
       </table>
     </div>
     <script src="https://instance.adobe.org:8080/nl/interactionProposal.js?env=OE3" id="interactionProposalScript" type="text/javascript"></script>
   </div>
   ```

### 식별된 오퍼 제시 {#presenting-an-identified-offer}

식별된 연락처에 오퍼를 제공하기 위해 프로세스는 여기에 설명된 프로세스와 유사합니다.익명의 [제안](#presenting-an-anonymous-offer). 웹 페이지의 내용에서 엔진에 대한 호출 동안 연락처를 식별하는 다음 스크립트를 추가해야 합니다.

```
<script type="text/javascript">
  interactionTarget = <contact_identifier>;
</script>
```

1. 웹 페이지에서 호출할 오퍼 공간으로 이동하여 을 클릭하고 하나 이상의 식별 키를 **[!UICONTROL Advanced parameters]** 추가합니다.

   ![](assets/interaction_htmlmode_001.png)

   이 예에서 ID 키는 이메일과 수신자 이름을 모두 기반으로 하므로 합성됩니다.

1. 웹 페이지가 표시되는 동안 스크립트 평가를 통해 수신자 ID를 오퍼 엔진에 전달할 수 있습니다. ID가 합성된 경우 키는 고급 설정에 사용된 것과 동일한 시퀀스에 표시되고|.

   다음 예에서는 연락처가 웹 사이트에 로그인되어 이메일 및 이름 덕분에 인터랙션 엔진 호출 중에 인식되었습니다.

   ```
   <script type="text/javascript">
     interactionTarget = myEmail|myName;
   </script>
   ```

### HTML 렌더링 함수 사용 {#using-an-html-rendering-function}

HTML 오퍼 표현을 자동으로 생성하려면 렌더링 함수를 사용할 수 있습니다.

1. 오퍼 공간으로 이동하고 **[!UICONTROL Edit functions]** 링크를 클릭합니다.
1. 을 **[!UICONTROL Overload the HTML rendering function]**&#x200B;선택합니다.
1. 탭으로 **[!UICONTROL HTML rendering]** 이동하여 오퍼 공간에서 오퍼 컨텐츠에 대해 정의된 필드와 일치하는 변수를 삽입합니다.

   ![](assets/interaction_htmlmode_002.png)

   이 예에서 오퍼는 웹 페이지의 배너 형식으로 표시되며 클릭 가능한 이미지와 오퍼 컨텐츠에 정의된 필드와 일치하는 제목으로 구성됩니다.

## XML 모드 {#xml-mode}

### 오퍼 제시 {#presenting-an-offer}

상호 작용을 통해 오퍼 엔진을 호출하는 HTML 페이지로 XML 노드를 반환할 수 있습니다. 이 XML 노드는 고객 측에서 개발할 수 있도록 함수로 처리할 수 있습니다.

상호 작용 엔진에 대한 호출은 다음과 같습니다.

```
<script type="text/javascript" id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=&cb="></script>
```

&quot;**env**&quot; 매개 변수는 라이브 환경의 내부 이름을 받습니다.

&quot;**cb**&quot; 매개 변수는 (콜백) 제안을 포함하는 엔진에서 반환되는 XML 노드를 읽는 함수의 이름을 받습니다. 이 매개 변수는 선택 사항입니다.

&quot;**t**&quot; 매개 변수는 식별된 상호 작용에 대해서만 대상의 값을 받습니다. 이 매개 변수는 interactionTarget **변수와 함께 전달할 수도 있습니다** . 이 매개 변수는 선택 사항입니다.

&quot;**c**&quot; 매개 변수는 카테고리의 내부 이름 목록을 받습니다. 이 매개 변수는 선택 사항입니다.

&quot;**th**&quot; 매개 변수는 테마 목록을 받습니다. 이 매개 변수는 선택 사항입니다.

&quot;**gctx**&quot; 매개 변수는 전체 페이지에 대한 호출 데이터 전역(컨텍스트)을 받습니다. 이 매개 변수는 선택 사항입니다.

반환된 XML 노드는 다음과 같습니다.

```
<propositions>
 <proposition id="" offer-id="" weight="" rank="" space="" div=""> //proposition identifiers
   ...XML content defined in Adobe Campaign...
 </proposition>
 ...
</propositions>
```

다음 사용 사례에서는 Adobe Campaign에서 수행하는 구성에 대해 자세히 설명한 다음 HTML 페이지에서 엔진에 대한 호출 결과를 표시합니다.

1. **환경 및 오퍼 공간 만들기**

   환경 만들기에 대한 자세한 내용은 라이브/ [디자인 환경을](../../interaction/using/live-design-environments.md)참조하십시오.

   오퍼 공간 만들기에 대한 자세한 내용은 오퍼 공간 [만들기를 참조하십시오](../../interaction/using/creating-offer-spaces.md).

1. **오퍼 스키마를 확장하여 새 필드 추가**

   이 스키마는 다음 필드를 정의합니다.제목 번호 2 및 가격

   예제의 스키마 이름은 **cus:offer입니다.**

   ```
   <srcSchema _cs="Marketing offers (cus)" created="2013-01-18 17:14:20.762Z" createdBy-id="0"
              desc="" entitySchema="xtk:srcSchema" extendedSchema="nms:offer" img="nms:offer.png"
              label="Marketing offers" labelSingular="Marketing offers" lastModified="2013-01-18 15:20:18.373Z"
              mappingType="sql" md5="F14A7AA009AE1FCE31B0611E72866AC3" modifiedBy-id="0"
              name="offer" namespace="cus" xtkschema="xtk:srcSchema">
     <createdBy _cs="Administrator (admin)"/>
     <modifiedBy _cs="Administrator (admin)"/>
     <element img="nms:offer.png" label="Marketing offers" labelSingular="Marketing offer"
              name="offer">
       <element label="Content" name="view">
         <element label="Price" name="price" type="long" xml="true"/>
         <element label="Title 2" name="title2" type="string" xml="true"/>
   
         <element advanced="true" desc="Price calculation script." label="Script price"
                  name="price_jst" type="CDATA" xml="true"/>
         <element advanced="true" desc="Title calculation script." label="Script title"
                  name="title2_jst" type="CDATA" xml="true"/>
       </element>
     </element>
   </srcSchema>
   ```

   >[!CAUTION]
   >
   >각 요소를 두 번 정의해야 합니다. CDATA(&quot;_jst&quot;) 유형 요소에는 개인화 필드가 포함될 수 있습니다.
   >
   >데이터베이스 구조를 업데이트하는 것을 잊지 마십시오. For more on this, refer to [this section](../../configuration/using/updating-the-database-structure.md).

   >[!NOTE]
   >
   >오퍼 스키마를 확장하여 일괄 처리 모드와 단일 모드 및 모든 형식(텍스트, HTML 및 XML)으로 새 필드를 추가할 수 있습니다.

1. **오퍼 공식을 확장하여 새 필드를 편집하고 기존 필드를 수정합니다.**

   오퍼( **nsm)** 입력 양식을 편집합니다.

   &quot;보기&quot; 섹션에서 다음 컨텐츠가 포함된 두 개의 새 필드를 삽입합니다.

   ```
   <input label="Title 2" margin-right="5" prebuildSubForm="false" type="subFormLink"
                        xpath="title2_jst">
                   <form label="Edit title 2" name="editForm" nothingToSave="true">
                     <input nolabel="true" toolbarAlign="horizontal" type="jstEdit"
                            xpath="." xpathInsert="/ignored/customizeTitle2">
                       <container>
                         <input menuId="viewMenuBuilder" options="inbound" type="customizeBtn"
                                xpath="/ignored/customizeTitle2"/>
                       </container>
                     </input>
                   </form>
                 </input>
                 <input nolabel="true" type="edit" xpath="title2_jst"/>
   
                 <input label="Price" margin-right="5" prebuildSubForm="false" type="subFormLink"
                        xpath="price_jst">
                   <form label="Edit price" name="editForm" nothingToSave="true">
                     <input nolabel="true" toolbarAlign="horizontal" type="jstEdit"
                            xpath="." xpathInsert="/ignored/customizePrice">
                       <container>
                         <input menuId="viewMenuBuilder" options="inbound" type="customizeBtn"
                                xpath="/ignored/customizePrice"/>
                       </container>
                     </input>
                   </form>
                 </input>
                 <input colspan="2" label="Prix" nolabel="true" type="number" xpath="price_jst"/>
   ```

   대상 URL 필드에 주석을 답니다.

   ![](assets/interaction_xmlmode_form_001.png)

   >[!CAUTION]
   >
   >( `<input>`) 양식의 필드는 생성된 스키마에 정의된 CDATA 유형 요소를 가리켜야 합니다.

   오퍼 표현 양식의 렌더링은 다음과 같습니다.

   ![](assets/interaction_xmlmode_form.png)

   및 **[!UICONTROL Title 2]** 필드가 **[!UICONTROL Price]** 추가되었으며 **[!UICONTROL Destination URL]** 필드가 더 이상 표시되지 않습니다.

1. **오퍼 만들기**

   오퍼 만들기에 대한 자세한 내용은 오퍼 [만들기를](../../interaction/using/creating-an-offer.md)참조하십시오.

   다음 사용 사례에서는 오퍼가 다음과 같이 입력됩니다.

   ![](assets/interaction_xmlmode_offer.png)

1. 오퍼를 승인하거나 다른 사람이 승인하도록 한 다음, 연결된 라이브 환경에서 사용할 수 있도록 마지막 단계에서 만든 오퍼 공간에서 활성화하십시오.
1. **엔진 호출 및 HTML 페이지 결과**

   HTML 페이지의 상호 작용 엔진에 대한 호출은 다음과 같습니다.

   ```
   <script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=OE7&cb=alert" type="text/javascript">
   ```

   &quot;**env**&quot; 매개 변수의 값은 라이브 환경의 내부 이름입니다.

   &quot;**cb**&quot; 매개 변수의 값은 엔진에서 반환한 XML 노드를 해석해야 하는 함수의 이름입니다. 이 예제에서 호출된 up 함수는 모달 창(alert() 함수)을 엽니다.

   상호 작용 엔진에서 반환되는 XML 노드는 다음과 같습니다.

   ```
   <propositions>
    <proposition id="a28002" offer-id="10322005" weight="1" rank="1" space="SPC14" div="i_SPC14">
     <xmlOfferView>
      <title>Travel to Russia</title>
      <price>3456</price>
      <description>Discover this vacation package!INCLUDES 10 nights. FEATURES buffet breakfast daily. BONUS 5th night free.</description>
      <image>
       <path>https://myinstance.com/res/Track/ae1d2113ed732d58a3beb441084e5960.jpg</path>
       <alt>Travel to Russia</alt>
      </image>
     </xmlOfferView>
    </proposition>
   </propositions>
   ```

### 렌더링 함수 사용 {#using-a-rendering-function-}

XML 렌더링 기능을 사용하여 오퍼 프레젠테이션을 만들 수 있습니다. 이 함수는 엔진에 대한 호출 중에 HTML 페이지로 반환되는 XML 노드를 수정합니다.

1. 오퍼 공간으로 이동하고 **[!UICONTROL Edit functions]** 링크를 클릭합니다.
1. 을 **[!UICONTROL Overload the XML rendering function]**&#x200B;선택합니다.
1. 탭으로 이동하여 원하는 함수를 삽입합니다. **[!UICONTROL XML rendering]**

   함수는 다음과 같이 표시될 수 있습니다.

   ```
   function (proposition) {
     delete proposition.@id;
     proposition.@newAttribute = "newValue";
   } 
   ```

![](assets/interaction_xmlmode_001.png)

