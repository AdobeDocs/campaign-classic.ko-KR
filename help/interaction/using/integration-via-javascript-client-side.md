---
product: campaign
title: JavaScript를 통한 통합(클라이언트측)
description: JavaScript를 통한 통합(클라이언트측)
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a9842e59-120c-4a35-abdf-6540a0bbdd6d
source-git-commit: 349c3dfd936527e50d7d3e03aa3408b395502da0
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 2%

---

# JavaScript를 통한 통합(클라이언트측){#integration-via-javascript-client-side}



웹 페이지에서 상호 작용 엔진을 호출하려면 JavaScript 코드에 대한 호출을 페이지에 직접 삽입합니다. 이 호출은 타깃팅된 오퍼의 콘텐츠를 반환합니다

요소를 생성하지 않습니다.

Adobe은 JavaScript 통합 방법을 사용하는 것을 권장합니다.

URL을 호출하는 스크립트는 다음과 같습니다.

```
<script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=" type="text/javascript"></script>
```

&quot;**env**&quot; 매개 변수는 익명 상호 작용 전용 라이브 환경의 내부 이름을 받습니다.

오퍼를 표시하려면 Adobe Campaign에서 환경 및 오퍼 공간을 만든 다음 HTML 페이지를 구성해야 합니다.

다음 사용 사례에서는 JavaScript을 통해 오퍼를 통합할 수 있는 옵션을 자세히 설명합니다.

## HTML 모드 {#html-mode}

### 익명 오퍼 표시 {#presenting-an-anonymous-offer}

1. **상호 작용 엔진을 준비하는 중**

   Adobe Campaign 인터페이스를 열고 익명 환경을 준비합니다.

   익명 환경에 연결된 오퍼 공간을 만듭니다.

   오퍼 및 오퍼 공간에 연결된 오퍼 표현을 만듭니다.

1. **HTML 페이지의 콘텐츠**

   HTML 페이지에는

   작성된 오퍼 공간(&quot;i_internal name space&quot;)의 내부 이름 값이 있는 @id 속성이 있는 요소입니다. 오퍼가 여기에 삽입됩니다.
상호 작용에 의한 요소입니다.

   이 예에서 @id 속성은 &quot;i_SPC12&quot; 값을 수신하며, 여기서 &quot;SPC12&quot;는 이전에 만든 오퍼 공간의 내부 이름입니다.

   ```
   <div id="i_SPC12"></div>
   ```

   이 예에서 스크립트를 호출하는 URL은 다음과 같습니다(&quot;OE3&quot;는 라이브 환경의 내부 이름입니다).

   ```
   <script id="interactionProposalScript" src="https://instance.adobe.org:8080/nl/interactionProposal.js?env=OE3" type="text/javascript"></script>
   ```

   >[!IMPORTANT]
   >
   >`<script>` 태그는 자동으로 닫으면 안 됩니다.

   이 정적 호출은 상호 작용 엔진에 필요한 모든 매개 변수를 포함하는 동적 호출을 자동으로 생성합니다.

   이 비헤이비어를 사용하면 엔진에 대한 단일 호출로 관리할 수 있도록 동일한 페이지에서 여러 오퍼 공간을 사용할 수 있습니다.

1. **HTML 페이지의 결과**

   오퍼 표현의 콘텐츠가 상호 작용 엔진에 의해 HTML 페이지로 반환됩니다.

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

### 식별된 오퍼 표시 {#presenting-an-identified-offer}

식별된 연락처에 오퍼를 제공하기 위한 프로세스는 [익명 오퍼 제공](#presenting-an-anonymous-offer)과 유사합니다. 웹 페이지의 콘텐츠에서 엔진 호출 중에 연락처를 식별하는 다음 스크립트를 추가해야 합니다.

```
<script type="text/javascript">
  interactionTarget = <contact_identifier>;
</script>
```

1. 웹 페이지에서 호출할 오퍼 공간으로 이동하여 **[!UICONTROL Advanced parameters]**&#x200B;을(를) 클릭하고 ID 키를 하나 이상 추가합니다.

   ![](assets/interaction_htmlmode_001.png)

   이 예제에서 식별 키는 이메일과 수신자 이름을 기반으로 하므로 합성 키입니다.

1. 웹 페이지가 표시되는 동안 스크립트 평가를 사용하여 수신자 ID를 오퍼 엔진에 전달할 수 있습니다. ID가 합성인 경우, 키는 고급 설정에 사용된 것과 동일한 순서로 표시되며, |.

   다음 예에서는 연락처가 웹 사이트에 로그온했으며, 전자 메일과 이름 덕분에 상호 작용 엔진에 대한 호출 중에 인식되었습니다.

   ```
   <script type="text/javascript">
     interactionTarget = myEmail|myName;
   </script>
   ```

### HTML 렌더링 기능 사용 {#using-an-html-rendering-function}

HTML 오퍼 표현을 자동으로 생성하려면 렌더링 함수를 사용할 수 있습니다.

1. 오퍼 공간으로 이동하여 **[!UICONTROL Edit functions]** 링크를 클릭합니다.
1. **[!UICONTROL Overload the HTML rendering function]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL HTML rendering]** 탭으로 이동하여 오퍼 콘텐츠에 대해 정의된 필드와 일치하는 변수를 오퍼 공간에 삽입합니다.

   ![](assets/interaction_htmlmode_002.png)

   이 예제에서 오퍼는 웹 페이지에 배너 형태로 표시되며 클릭 가능한 이미지와 오퍼 콘텐츠에 정의된 필드와 일치하는 제목으로 구성됩니다.

## XML 모드 {#xml-mode}

### 오퍼 표시 {#presenting-an-offer}

상호 작용을 사용하면 오퍼 엔진을 호출하는 HTML 페이지로 XML 노드를 반환할 수 있습니다. 이 XML 노드는 고객 측에서 개발해야 하는 함수에 의해 처리될 수 있습니다.

상호 작용 엔진에 대한 호출은 다음과 같습니다.

```
<script type="text/javascript" id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=&cb="></script>
```

&quot;**env**&quot; 매개 변수는 라이브 환경의 내부 이름을 받습니다.

&quot;**cb**&quot; 매개 변수는 (콜백) 제안을 포함하는 엔진에서 반환된 XML 노드를 읽을 함수의 이름을 받습니다. 이 매개 변수는 선택 사항입니다.

&quot;**t**&quot; 매개 변수는 식별된 상호 작용에 대해서만 대상 값을 받습니다. 이 매개 변수는 **interactionTarget** 변수와 함께 전달할 수도 있습니다. 이 매개 변수는 선택 사항입니다.

&quot;**c**&quot; 매개 변수는 범주의 내부 이름 목록을 받습니다. 이 매개 변수는 선택 사항입니다.

&quot;**th**&quot; 매개 변수는 테마 목록을 받습니다. 이 매개 변수는 선택 사항입니다.

&quot;**gctx**&quot; 매개 변수는 전체 페이지에 대한 호출 데이터 전역(컨텍스트)을 수신합니다. 이 매개 변수는 선택 사항입니다.

반환된 XML 노드는 다음과 같습니다.

```
<propositions>
 <proposition id="" offer-id="" weight="" rank="" space="" div=""> //proposition identifiers
   ...XML content defined in Adobe Campaign...
 </proposition>
 ...
</propositions>
```

다음 사용 사례에서는 XML 모드를 활성화하기 위해 Adobe Campaign에서 수행하는 구성에 대해 자세히 설명한 다음 HTML 페이지에 엔진 호출 결과를 표시합니다.

1. **환경 및 오퍼 공간 만들기**

   환경 만들기에 대한 자세한 내용은 [라이브/디자인 환경](../../interaction/using/live-design-environments.md)을 참조하세요.

   오퍼 공간을 만드는 방법에 대한 자세한 내용은 [오퍼 공간 만들기](../../interaction/using/creating-offer-spaces.md)를 참조하세요.

1. **오퍼 스키마를 확장하여 새 필드 추가**

   이 스키마는 제목 번호 2 및 가격 필드를 정의합니다.

   예제의 스키마 이름은 **cus:offer**&#x200B;입니다.

   ```
   <srcSchema _cs="Marketing offers (cus)" created="2 AAAA-MM-DD HH:MM:SS.762Z" createdBy-id="0"
              desc="" entitySchema="xtk:srcSchema" extendedSchema="nms:offer" img="nms:offer.png"
              label="Marketing offers" labelSingular="Marketing offers" lastModified="AAAA-MM-DD HH:MM:SS.373Z"
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

   >[!IMPORTANT]
   >
   >각 요소를 두 번 정의해야 합니다. CDATA(&quot;_jst&quot;) 유형 요소에는 개인화 필드가 포함될 수 있습니다.
   >
   >데이터베이스 구조를 업데이트하는 것을 잊지 마십시오. 이 작업에 대한 자세한 정보는 [이 섹션](../../configuration/using/updating-the-database-structure.md)을 참조하십시오.

   >[!NOTE]
   >
   >오퍼 스키마를 확장하여 배치 및 단일 모드와 모든 형식(텍스트, HTML 및 XML)의 새 필드를 추가할 수 있습니다.

1. **오퍼 수식을 확장하여 새 필드를 편집하고 기존 필드를 수정합니다**

   **오퍼(nsm)** 입력 양식을 편집합니다.

   &quot;보기&quot; 섹션에 다음 콘텐츠가 있는 두 개의 새 필드를 삽입합니다.

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

   대상 URL 필드를 주석 처리합니다.

   ![](assets/interaction_xmlmode_form_001.png)

   >[!IMPORTANT]
   >
   >( `<input>`) 양식의 필드는 만들어진 스키마에 정의된 CDATA 형식 요소를 가리켜야 합니다.

   오퍼 표시 양식의 렌더링은 다음과 같습니다.

   ![](assets/interaction_xmlmode_form.png)

   **[!UICONTROL Title 2]** 및 **[!UICONTROL Price]** 필드가 추가되었으며 **[!UICONTROL Destination URL]** 필드가 더 이상 표시되지 않습니다.

1. **오퍼 만들기**

   오퍼 만들기에 대한 자세한 내용은 [오퍼 만들기](../../interaction/using/creating-an-offer.md)를 참조하세요.

   다음 사용 사례에서는 오퍼를 다음과 같이 입력합니다.

   ![](assets/interaction_xmlmode_offer.png)

1. 오퍼를 승인하거나 다른 사람이 승인하도록 한 다음, 연결된 라이브 환경에서 사용할 수 있도록 마지막 단계에서 만든 오퍼 공간에서 활성화합니다.
1. **HTML 페이지의 엔진 호출 및 결과**

   HTML 페이지의 상호 작용 엔진에 대한 호출은 다음과 같습니다.

   ```
   <script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=OE7&cb=alert" type="text/javascript">
   ```

   &quot;**env**&quot; 매개 변수의 값은 라이브 환경의 내부 이름입니다.

   &quot;**cb**&quot; 매개 변수의 값은 엔진에서 반환된 XML 노드를 해석해야 하는 함수의 이름입니다. 이 예에서 호출된 up 함수는 모달 창(alert() 함수)을 엽니다.

   상호 작용 엔진에서 반환된 XML 노드는 다음과 같습니다.

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

XML 렌더링 함수를 사용하여 오퍼 프레젠테이션을 만들 수 있습니다. 이 함수는 엔진을 호출하는 동안 HTML 페이지로 반환되는 XML 노드를 수정합니다.

1. 오퍼 공간으로 이동하여 **[!UICONTROL Edit functions]** 링크를 클릭합니다.
1. **[!UICONTROL Overload the XML rendering function]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL XML rendering]** 탭으로 이동하여 원하는 함수를 삽입합니다.

   함수는 다음과 같이 표시될 수 있습니다.

   ```
   function (proposition) {
     delete proposition.@id;
     proposition.@newAttribute = "newValue";
   } 
   ```

![](assets/interaction_xmlmode_001.png)
