---
product: campaign
title: "활용 사례: 개요 만들기"
description: "활용 사례: 개요 만들기"
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Apps
exl-id: a1ac3aab-dc81-4533-9207-26d5dc5e1c88
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# 사용 사례: 개요 페이지 만들기{#use-cases-creating-overviews}



다음 예제에서는 개요형 웹 응용 프로그램을 만들어 데이터베이스의 모든 웹 응용 프로그램을 표시합니다. 다음 요소를 구성합니다.

* 폴더의 필터( [폴더에 필터 추가](#adding-a-filter-on-a-folder)),
* 새 웹 응용 프로그램을 만들기 위한 단추( [새 웹 응용 프로그램을 구성하는 단추 추가](#adding-a-button-to-configure-a-new-web-application)),
* 목록의 각 항목에 대한 세부 정보가 표시됩니다(참조: [목록에 세부 사항 추가](#adding-detail-to-a-list)),
* 링크 편집 도구당 하나의 필터(참조) [링크 편집기를 사용하여 필터 만들기](#creating-a-filter-using-a-link-editor)),
* 새로 고침 링크( [새로 고침 링크 만들기](#creating-a-refresh-link)).

![](assets/s_ncs_configuration_webapp_overview.png)

## 단일 페이지 웹 애플리케이션 만들기 {#creating-a-single-page-web-application}

1. 단일 만들기 **[!UICONTROL Page]** 웹 응용 프로그램을 사용하여 아웃바운드 전환 및 다음 페이지로 전환을 비활성화합니다.

   ![](assets/s_ncs_configuration_webapp_create.png)

1. 페이지 제목 변경.

   이 제목은 개요 헤더와 웹 애플리케이션 개요에 표시됩니다.

1. 웹 애플리케이션 속성에서 **[!UICONTROL Single-page Web application]** 템플릿.

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. 를 엽니다. **[!UICONTROL Page]** 웹 응용 프로그램의 활동 및 목록 열기(**[!UICONTROL Static element > List]**).
1. 에서 **[!UICONTROL Data]** 목록의 탭에서 **[!UICONTROL Web applications]** 문서 및 **[!UICONTROL Label]** , **[!UICONTROL Creation date]** 및 **[!UICONTROL Type of application]** 출력 열.
1. 에서 **[!UICONTROL Filter]** 하위 탭에서 아래 표시된 대로 다음 필터를 만들어 웹 응용 프로그램만 표시하고 보기에서 템플릿을 제외합니다.

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. 페이지의 구성 창을 닫고 를 클릭합니다. **[!UICONTROL Preview]**.

   데이터베이스에서 사용할 수 있는 웹 응용 프로그램 목록이 표시됩니다.

   ![](assets/s_ncs_configuration_webapp_preview.png)

## 폴더에 필터 추가 {#adding-a-filter-on-a-folder}

개요에서는 Adobe Campaign 트리의 위치에 따라 데이터에 액세스하도록 선택할 수 있습니다. 폴더의 필터입니다. 다음 프로세스를 적용하여 개요에 추가합니다.

1. 커서를 **[!UICONTROL Page]** 웹 응용 프로그램의 노드 및 **[!UICONTROL Select folder]** 요소(**[!UICONTROL Advanced controls > Select folder]**).
1. 에서 **[!UICONTROL Storage]** 창이 나타나면 **[!UICONTROL Edit variables]** 링크를 클릭합니다.
1. 변수 레이블을 필요에 맞게 변경합니다.
1. 변수 이름을 **폴더** 값.

   >[!NOTE]
   >
   >변수 이름은 폴더에 연결된 요소(즉, 스키마에 정의됨)의 이름과 일치해야 합니다. **폴더** 이 경우 테이블을 참조할 때는 이 이름을 다시 사용해야 합니다.

1. 적용 **[!UICONTROL XML]** 변수를 입력합니다.

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. 을(를) 선택합니다 **[!UICONTROL Refresh page]** 상호 작용

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. 목록에 커서를 놓고 **[!UICONTROL Advanced]** 탭에서 이전에 **[!UICONTROL Folder filter XPath]** 탭의 목록을 표시합니다. 폴더 링크와 관련된 요소의 이름(예: **폴더**.

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >이 단계에서는 웹 응용 프로그램이 응용 프로그램 컨텍스트 내에 있지 않으므로 폴더에서 필터를 테스트할 수 없습니다.

## 새 웹 응용 프로그램을 구성하는 단추 추가 {#adding-a-button-to-configure-a-new-web-application}

1. 커서를 **[!UICONTROL Page]** 요소 및 링크 추가(**[!UICONTROL Static elements > Link]**).
1. 개요 단추에 표시되므로 링크 레이블을 수정합니다.

   이 예제에서 레이블은 **새로 만들기**.

1. URL 필드에 다음 URL을 삽입합니다. **xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**.

   >[!NOTE]
   >
   >**nms:webApp** 웹 응용 프로그램 스키마와 일치합니다.
   >
   >**nms:newWebApp** 새 웹 응용 프로그램 만들기 마법사와 일치합니다.

1. 동일한 창에 URL을 표시하도록 선택합니다.
1. 이미지 필드에 웹 애플리케이션 아이콘을 추가합니다. **/nms/img/webApp.png**.

   이 아이콘은 **[!UICONTROL New]** 버튼을 클릭합니다.

1. Enter 키 **버튼** 에서 **[!UICONTROL Style]** 필드.

   이 스타일은 **[!UICONTROL Single-page Web application]** 이전에 선택한 템플릿입니다.

   ![](assets/s_ncs_configuration_webapp_link.png)

## 목록에 세부 사항 추가 {#adding-detail-to-a-list}

개요에서 목록을 구성할 때 목록의 각 항목에 대한 추가 세부 사항을 표시하도록 선택할 수 있습니다.

1. 이전에 만든 목록 요소에 커서를 놓습니다.
1. 에서 **[!UICONTROL General]** 탭에서 을 선택합니다 **[!UICONTROL Columns and additional detail]** 드롭다운 목록에 표시 모드.

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. 에서 **[!UICONTROL Data]** 탭에서 추가 **[!UICONTROL Primary key]** , **[!UICONTROL Internal name]** 및 **[!UICONTROL Description]** 열을 선택하고 **[!UICONTROL Hidden field]** 선택 사항입니다.

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   이렇게 하면 각 항목의 세부 사항에서만 이 정보가 표시됩니다.

1. 에서 **[!UICONTROL Additional detail]** 탭에서 다음 코드를 추가합니다.

   ```
   <div class="detailBox">
     <div class="actionBox">
       <span class="action"><img src="/xtk/img/fileEdit.png"/><a title="Open" class="linkAction" href="xtk://open/?schema=nms:webApp&form=nms:webApp&pk=
       <%=webApp.id%>">Open...</a></span>
       <% 
       if( webApp.@appType == 1 ) { //survey
       %>
       <span class="action"><img src="/xtk/img/report.png"/><a target="_blank" title="Reports" class="linkAction" href="/xtk/report.jssp?_context=selection&
         _schema=nms:webApp&_selection=<%=webApp.@id%>
         &__sessiontoken=<%=document.controller.getSessionToken()%>">Reports</a></span>
       <% 
       } 
       %>
     </div>
     <div>
       Internal name: <%= webApp.@internalName %>
     </div>
     <%
     if( webApp.desc != "" )
     {
     %>
     <div>
       Description: <%= webApp.desc %>
     </div>
     <% 
     } 
     %>
   </div>
   ```

>[!NOTE]
>
>JavaScript 라이브러리를 서버에서 새로 고치는 데 5분이 소요됩니다. 이 지연을 기다리지 않도록 서버를 다시 시작할 수 있습니다.

## 목록 필터링 및 업데이트 {#filtering-and-updating-the-list}

이 섹션에서는 특정 연산자가 생성한 웹 응용 프로그램의 개요를 표시하는 필터를 만듭니다. 이 필터는 링크 편집기를 사용하여 만듭니다. 연산자를 선택하면 목록을 새로 고쳐 필터를 적용합니다. 새로 고침 링크를 만들어야 합니다.

이러한 두 요소는 개요에서 그래픽으로 그룹화하기 위해 동일한 컨테이너로 그룹화됩니다.

1. 커서를 **[!UICONTROL Page]** 요소를 선택하고 **[!UICONTROL Container > Standard]**.
1. 열 수를 로 설정합니다. **2개**&#x200B;링크 편집기와 링크가 서로 이웃하도록 하는 것입니다.

   ![](assets/s_ncs_configuration_webapp_container.png)

   요소 레이아웃에 대한 자세한 내용은 [이 섹션](about-web-forms.md).

1. 적용 **dottingFilter**.

   이 스타일은 **[!UICONTROL Single-page Web application]** 이전에 선택한 템플릿입니다.

   ![](assets/s_ncs_configuration_webapp_container002.png)

### 링크 편집기를 사용하여 필터 만들기 {#creating-a-filter-using-a-link-editor}

1. 이전 단계에서 만든 컨테이너에 커서를 놓고 를 통해 링크 편집기를 삽입합니다. **[!UICONTROL Advanced controls]** 메뉴 아래의 제품에서 사용할 수 있습니다.
1. 자동으로 열리는 저장 창에서 **[!UICONTROL Variables]** 옵션을 클릭한 다음 **[!UICONTROL Edit variables]** 데이터를 필터링할 XML 변수를 링크하고 만듭니다.

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. 레이블을 수정합니다.

   다음 옆에 표시됩니다. **[!UICONTROL Filter]** 개요 필드.

1. 응용 프로그램 스키마로 연산자 테이블을 선택합니다.

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. 목록 요소에 커서를 놓고 **[!UICONTROL Data > Filter]** 탭:

   * **표현식:** &#39;Created by&#39; 링크의 외부 키
   * **연산자:** 다음과 같음
   * **값:** 변수(변수)
   * **다음과 같은 경우 고려합니다.** &#39;$(var2/@id&#39;!=&quot;

   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>웹 애플리케이션 사용자는 정보에 액세스하려면 해당 Adobe Campaign 권한이 있는 식별된 연산자여야 합니다. 이 유형의 구성은 익명 웹 응용 프로그램에서 작동하지 않습니다.

### 새로 고침 링크 만들기 {#creating-a-refresh-link}

1. 컨테이너에 커서를 놓고 **[!UICONTROL Link]** 사용 **[!UICONTROL Static elements]** 메뉴 아래의 제품에서 사용할 수 있습니다.
1. 레이블을 수정합니다.
1. **[!UICONTROL Refresh data in a list]**&#x200B;을(를) 선택합니다.
1. 앞에서 만든 목록을 추가합니다.

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. 에서 새로 고침 아이콘 추가 **[!UICONTROL Image]** 필드: **/xtk/img/refresh.png**.
1. 정렬 순서 화살표를 사용하여 아래에서 보듯이 웹 애플리케이션의 다양한 요소를 재구성합니다.

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

이제 웹 응용 프로그램이 구성되었습니다. 을(를) 클릭합니다. **[!UICONTROL Preview]** 탭을 클릭하여 미리 봅니다.

![](assets/s_ncs_configuration_webapp_result.png)
