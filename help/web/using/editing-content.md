---
title: 컨텐츠 편집
seo-title: 컨텐츠 편집
description: 컨텐츠 편집
seo-description: null
page-status-flag: never-activated
uuid: 2f51e848-1820-4bec-a0ea-63c9ddff05e0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: da66d640-8504-4dc7-bc4e-1c0ac1d37c37
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 컨텐츠 편집{#editing-content}

## 가시성 조건 정의 {#defining-a-visibility-condition}

웹 페이지 요소에 가시성 조건을 지정할 수 있습니다.이 요소는 조건이 존중되는 경우에만 표시됩니다.

가시성 조건을 추가하려면 블록을 선택하고 표현식 편집기를 사용하여 **[!UICONTROL Visibility condition]** 필드에 조건을 입력합니다.

![](assets/dce_add_condition.png)

>[!NOTE]
>
>고급 표현식 편집이 [이 페이지에](../../platform/using/defining-filter-conditions.md#list-of-functions)표시됩니다.

![](assets/dce_popup_visibilitycondition.png)

이러한 조건은 XTK 식 구문을 사용합니다(예: ctx. **recipient).@email != &quot;&quot;** &quot; 또는 **ctx.recipient.@status=&quot;0&quot;**). 기본적으로 모든 필드가 표시됩니다.

>[!NOTE]
>
>드롭다운 메뉴와 같이 보이지 않는 동적 블록은 편집할 수 없습니다.

## 테두리 및 배경 추가 {#adding-a-border-and-background}

선택한 블록에 **테두리를** 추가할 수 있습니다. 테두리는 다음 세 가지 옵션을 사용하여 정의됩니다.스타일, 크기 및 색상.

![](assets/dce_popup_border.png)

색상 차트에서 색상을 선택하여 **배경색을** 정의할 수도 있습니다.

![](assets/dce_popup_background.png)

## 양식 편집 {#editing-forms}

### 양식의 데이터 속성 변경 {#changing-the-data-properties-for-a-form}

데이터베이스 필드를 입력 영역, 라디오 단추 또는 확인란 유형 블록과 연결할 수 있습니다.

![](assets/dce_sidebar_field.png)

>[!NOTE]
>
>기본 필드는 웹 응용 프로그램 저장소 스키마의 필드입니다.

필드 **** 입력 영역을 사용하면 양식 필드에 연결할 데이터베이스 필드를 선택할 수 있습니다.

기본적으로 제공되는 필드는 **nms:recipient** 테이블에 있는 필드입니다.

![](assets/dce_field_selection.png)

필수 **필드** 옵션을 사용하면 사용자가 필드를 채운 경우에만 페이지의 승인을 승인할 수 있습니다. 필수 필드를 채우지 않으면 오류 메시지가 나타납니다.

라디오 단추 및 확인란의 경우 **추가 구성이 필요합니다**.

실제로 사용된 템플릿에 기본적으로 값이 포함되어 있지 않으면 편집기에서 작성해야 합니다.

이렇게 하려면:

* 아이콘을 **[!UICONTROL Edit]** 클릭합니다.

   ![](assets/dce_sidebar_options.png)

* 선택한 필드에 항목 목록 값(선택한 필드로 정의)을 **[!UICONTROL Value]** 입력합니다.

   ![](assets/dce_sidebar_completeoptionradio.png)

### 양식 필드 수정 {#modifying-form-fields}

라디오 단추, 입력 영역, 드롭다운 목록 등의 양식 필드 도구 모음에서 수정할 수 있습니다.

즉, 다음을 수행할 수 있습니다.

* 양식 필드가 포함된 블록을 **[!UICONTROL Delete]** 아이콘을 사용하여 삭제합니다.
* 아이콘을 사용하여 새 블록을 만들어 선택한 필드를 **[!UICONTROL Duplicate]** 복제합니다.
* 아이콘을 사용하여 데이터베이스 필드를 양식 영역에 연결하려면 **[!UICONTROL Form data]** 창을 **[!UICONTROL Edit]** 편집합니다.

   ![](assets/dce_toolbar_formblock_edition.png)

## 단추에 동작 추가 {#adding-an-action-to-a-button}

사용자가 단추를 클릭하면 연결된 동작을 정의할 수 있습니다. 이렇게 하려면 드롭다운 목록에서 수행할 작업을 선택합니다.

![](assets/dce_sidebar_button.png)

사용 가능한 작업은 다음과 같습니다.

* **[!UICONTROL Refresh]** :현재 페이지를 새로 고칩니다.
* **[!UICONTROL Next page]** :웹 애플리케이션에서 다음 페이지로 연결되는 링크를 만듭니다.
* **[!UICONTROL Previous page]** :웹 응용 프로그램에서 이전 페이지에 대한 링크를 만듭니다.

>[!NOTE]
>
>이 **[!UICONTROL None]** 값을 사용하면 단추를 활성화할 수 없습니다.

해당 필드의 단추에 연결된 레이블을 수정할 수 있습니다.

## 링크 추가 {#adding-a-link}

링크를 페이지 요소에 삽입할 수 있습니다.이미지, 단어, 단어 그룹, 텍스트 블록 등

이렇게 하려면 요소를 선택한 다음 팝업 메뉴에서 첫 번째 아이콘을 사용합니다.

![](assets/dce_insertlink_icon.png)

이 아이콘을 사용하면 사용 가능한 모든 유형의 링크에 액세스할 수 있습니다.

![](assets/dce_insertlink_menu.png)

개인화 블록과 필드는 텍스트 문자 블록에만 삽입할 수 있습니다.

>[!NOTE]
>
>각 유형의 링크에 대해 열기 모드를 구성할 수 있습니다.타겟 드롭다운 목록에서 타겟 **창을** 선택합니다. 이 값은 HTML **`<target>`** 태그에 해당합니다.
>
>사용 가능한 **타겟** 목록은 다음과 같습니다.

>* 기타(IFrame)
>* 위쪽 창(_top)
* 상위 창(_parent)
* 새 창(_Blank)
* 현재 창(_self)
* 기본 브라우저 동작



### URL에 대한 링크 {#link-to-a-url}

외부 **URL에 연결** 옵션을 사용하면 소스 컨텐츠의 URL을 열 수 있습니다.

![](assets/dce_toolbar_imgblock_externallink.png)

URL 필드에 문제의 링크 주소를 **입력합니다** . URL 필드는 다음과 같이 입력해야 합니다.https://www.myURL.com ****.

### 웹 애플리케이션에 대한 링크 {#link-to-a-web-application}

웹 **애플리케이션에** 대한 링크 옵션을 사용하면 Adobe Campaign 웹 애플리케이션에 액세스할 수 있습니다.

![](assets/dce_toolbar_imgblock_appweb.png)

해당 필드에서 웹 애플리케이션을 선택합니다.

제안된 웹 애플리케이션의 목록은 **[!UICONTROL Resources > Online > Web Applications]** 노드에서 사용 가능한 애플리케이션에 해당합니다.

### 작업에 대한 링크 {#link-to-an-action}

작업 **옵션을 정의하는** 링크를 사용하면 소스 요소를 클릭할 때 작업을 구성할 수 있습니다.

![](assets/dce_toolbar_imgblock_action.png)

>[!NOTE]
사용 가능한 작업은 단추에 [작업](#adding-an-action-to-a-button) 추가 섹션에서 자세히 설명합니다.

### 링크 삭제 {#delete-a-link}

링크가 삽입되면 도구 모음에는 두 개의 새 아이콘이 표시됩니다.링크를 **편집하고** 만든 링크와 **상호 작용할 수 있도록 링크를** 끊습니다.

* **[!UICONTROL Edit link]** 링크의 모든 매개 변수가 포함된 창을 표시할 수 있습니다.
* **[!UICONTROL Break the link]** 확인 후 링크 및 모든 관련 매개 변수를 삭제할 수 있습니다.

>[!NOTE]
링크를 삭제해도 컨텐츠는 그대로 유지됩니다.

## 글꼴 속성 변경 {#changing-font-attributes}

텍스트 요소를 선택하면 글꼴 속성(스타일, 형식)을 수정할 수 있습니다.

![](assets/dce_toolbar_txt.png)

사용 가능한 옵션은 다음과 같습니다.

* **확대된 글꼴** 아이콘:선택한 텍스트의 크기를 늘립니다(추가 `<span style="font size:">`).
* **글꼴** 아이콘 축소:선택한 텍스트 크기 축소(추가 `<span style="font size:">`)
* **굵게** 아이콘:선택한 텍스트를 굵게 표시( `<strong> </strong>` 태그로 텍스트 감싸기)
* **기울임체** 아이콘:선택한 텍스트를 기울임꼴로 만들기( `<em> </em>` 태그로 텍스트 감싸기)
* **밑줄** 아이콘:선택한 텍스트에 밑줄 표시( `<span style="text-decoration: underline;">` 태그로 텍스트 감싸기)
* **왼쪽** 정렬 아이콘:선택한 블록의 왼쪽에 텍스트를 정렬합니다(add style=&quot;text-align:left;&quot;)
* **가운데** 아이콘:선택한 블록의 텍스트 가운데 맞춤(스타일 추가=&quot;text-align:center;&quot;)
* **오른쪽** 정렬 아이콘:선택한 블록의 오른쪽에 텍스트를 정렬합니다(add style=&quot;text-align:right;&quot;
* **배경색** 아이콘을 변경합니다.선택한 블록의 배경색을 변경할 수 있습니다(style=&quot;background-color:rgba(170, 86, 255, 0.87)
* **텍스트 색상** 아이콘 변경:선택한 블록의 텍스트 색상을 변경하거나 선택한 텍스트만 변경할 수 있습니다(`<span style="color: #CODE">`).

>[!NOTE]
* **삭제** 아이콘:블록과 모든 해당 컨텐츠를 삭제합니다.

* **복제** 아이콘:블록과 관련된 모든 스타일과 함께 블록을 복제합니다.


## 이미지 및 애니메이션 관리 {#managing-images-and-animations}

디지털 컨텐츠 편집기를 사용하면 브라우저와 호환되는 **모든 유형의 이미지를** 작업할 수 있습니다.

DCE와 호환하려면 **&quot;Flash&quot; 유형 애니메이션을** HTML 페이지에 다음과 같이 삽입해야 합니다.

```
<object type="application/x-shockwave-flash" data="https://www.mydomain.com/flash/your_animation.swf" width="200" height="400">
 <param name="movie" value="https://www.mydomain.com/flash/your_animation.swf" />
 <param name="quality" value="high" />
 <param name="play" value="true"/>
 <param name="loop" value="true"/> 
</object>
```

>[!CAUTION]
HTML 페이지의 **스크립트** 태그로 외부 파일을 호출해서는 안 됩니다. 이러한 파일은 Adobe Campaign 서버로 가져오지 않습니다.

### 이미지 추가/삭제/복제 {#adding---deleting---duplicating-an-image}

이미지를 삽입하려면 이미지 유형 블록을 선택하고 이미지 **아이콘을 클릭합니다** .

![](assets/dce_insert_image.png)

로컬에 저장된 이미지 파일을 선택합니다.

![](assets/dce_popup_imgupload.png)

삭제 **아이콘은** 이미지를 포함하는 ![]() 태그를 삭제합니다.

[ **복제** ] 아이콘은 ![]() 태그와 해당 컨텐츠를 복제합니다.

>[!CAUTION]
이미지를 복제하면 새 이미지와 관련된 식별자가 삭제됩니다.

### 이미지 속성 편집 {#editing-image-properties}

이미지가 포함된 블록을 선택하면 다음 속성에 액세스합니다.

* **캡션을** 사용하면 이미지에 연결된 캡션을 정의할 수 있습니다( **대체** HTML 속성에 해당합니다).
* **크기를** 사용하면 이미지 크기를 픽셀 단위로 지정할 수 있습니다.

   ![](assets/dce_popup_imgsize.png)

## 개인화 콘텐츠 추가 {#adding-personalization-content}

### 개인화 필드 삽입 {#inserting-a-personalization-field}

삽입 **아이콘에 대한 개인화 필드** 옵션을 사용하면 받는 사람 이름과 같은 데이터베이스 필드를 컨텐츠에 추가할 수 있습니다. 이 옵션은 텍스트 문자 블록에만 사용할 수 있습니다.

![](assets/dce_toolbar_textblock_persofield.png)

기본적으로 제공되는 필드는 **[!UICONTROL Recipient]** 표에서 가져옵니다. 필요한 경우 웹 응용 프로그램 속성을 편집하여 다른 표를 선택합니다.

필드 이름이 편집기에 나타나고 노란색으로 강조 표시됩니다. 개인화가 생성되면(예: 랜딩 페이지를 미리 볼 때) 타깃팅된 수신자의 프로필로 바뀝니다.

개인화 필드 삽입 [섹션에](../../web/using/creating-a-landing-page.md#inserting-a-personalization-field) 예가 나와 있습니다.

### 개인화 블록 삽입 {#inserting-a-personalization-block}

개인화 **블록** 옵션을 사용하면 콘텐츠에 동적 및 개인화된 블록을 삽입할 수 있습니다. 예를 들어 로고나 인사말 메시지를 추가할 수 있습니다. 텍스트 문자 블록에는 사용할 수 없습니다.

![](assets/dce_toolbar_textblock_persoblock.png)

개인화 블록 이름이 삽입되면 편집기에 노란색으로 강조 표시됩니다. 개인화가 생성되면 수신자 프로필에 자동으로 적용됩니다.

내장된 개인화 블록과 맞춤형 개인화 블록을 정의하는 방법에 대한 자세한 내용은 [이 페이지를](../../delivery/using/personalization-blocks.md)참조하십시오.
