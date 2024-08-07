---
product: campaign
title: 콘텐츠 편집
description: 콘텐츠 편집
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: 968430d6-b1dd-47f8-8b31-39aaa18bc05c
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1227'
ht-degree: 0%

---

# 콘텐츠 편집{#editing-content}



## 가시성 조건 정의 {#defining-a-visibility-condition}

웹 페이지 요소에 가시성 조건을 지정할 수 있습니다. 이 요소는 조건이 준수되는 경우에만 표시됩니다.

가시성 조건을 추가하려면 블록을 선택하고 표현식 편집기를 사용하여 **[!UICONTROL Visibility condition]** 필드에 조건을 입력합니다.

![](assets/dce_add_condition.png)

>[!NOTE]
>
>고급 표현식 편집이 [이 페이지](../../platform/using/defining-filter-conditions.md#list-of-functions)에 표시됩니다.

![](assets/dce_popup_visibilitycondition.png)

이러한 조건은 XTK 식 구문(예: **ctx.recipient)을 채택합니다.@email!= &quot;&quot;** 또는 **ctx.recipient.@status==&quot;0&quot;**). 기본적으로 모든 필드가 표시됩니다.

>[!NOTE]
>
>드롭다운 메뉴와 같이 표시되지 않는 동적 블록은 편집할 수 없습니다.

## 테두리 및 배경 추가 {#adding-a-border-and-background}

선택한 블록에 **border**&#x200B;을(를) 추가할 수 있습니다. 테두리는 스타일, 크기 및 색상의 세 가지 옵션을 사용하여 정의됩니다.

![](assets/dce_popup_border.png)

색상 차트에서 색상을 선택하여 **배경색**&#x200B;을 정의할 수도 있습니다.

![](assets/dce_popup_background.png)

## 양식 편집 {#editing-forms}

### 양식에 대한 데이터 속성 변경 {#changing-the-data-properties-for-a-form}

데이터베이스 필드를 입력 영역, 라디오 버튼 또는 체크박스 유형 블록과 연결할 수 있습니다.

![](assets/dce_sidebar_field.png)

>[!NOTE]
>
>기본 필드는 웹 애플리케이션 스토리지 스키마의 필드입니다.

**필드** 입력 영역을 사용하면 양식 필드에 연결할 데이터베이스 필드를 선택할 수 있습니다.

기본적으로 제공되는 필드는 **nms:recipient** 테이블에 있는 필드입니다.

![](assets/dce_field_selection.png)

**필수 필드** 옵션을 사용하면 사용자가 해당 필드를 입력한 경우에만 페이지의 승인을 승인하도록 할 수 있습니다. 필수 필드를 입력하지 않으면 오류 메시지가 표시됩니다.

라디오 단추와 확인란의 경우 **추가 구성이 필요합니다**.

실제로, 사용된 템플릿에 기본적으로 값이 포함되어 있지 않으면 편집기에서 값을 완료해야 합니다.

방법은 다음과 같습니다.

* **[!UICONTROL Edit]** 아이콘을 클릭합니다.

  ![](assets/dce_sidebar_options.png)

* **[!UICONTROL Value]** 필드에 항목별 목록 값(선택한 필드로 정의됨)을 입력하십시오.

  ![](assets/dce_sidebar_completeoptionradio.png)

### 양식 필드 수정 {#modifying-form-fields}

라디오 단추, 입력 영역, 드롭다운 목록 등과 같은 양식 필드. 도구 모음에서 수정할 수 있습니다.

이는 다음을 수행할 수 있음을 의미합니다.

* **[!UICONTROL Delete]** 아이콘을 사용하여 양식 필드가 포함된 블록을 삭제합니다.
* **[!UICONTROL Duplicate]** 아이콘을 사용하여 새 블록을 만들어 선택한 필드를 복제합니다.
* **[!UICONTROL Form data]** 창을 편집하여 **[!UICONTROL Edit]** 아이콘을 사용하여 데이터베이스 필드를 양식 영역에 연결합니다.

  ![](assets/dce_toolbar_formblock_edition.png)

## 단추에 작업 추가 {#adding-an-action-to-a-button}

사용자가 버튼을 클릭하면 관련 작업을 정의할 수 있습니다. 이렇게 하려면 드롭다운 목록에서 수행할 작업을 선택합니다.

![](assets/dce_sidebar_button.png)

사용 가능한 작업은 다음과 같습니다.

* **[!UICONTROL Refresh]** : 현재 페이지를 새로 고칩니다.
* **[!UICONTROL Next page]** : 웹 응용 프로그램의 다음 페이지에 대한 링크를 만듭니다.
* **[!UICONTROL Previous page]** : 웹 응용 프로그램의 이전 페이지에 대한 링크를 만듭니다.

>[!NOTE]
>
>**[!UICONTROL None]** 값을 사용하면 단추를 활성화할 수 없습니다.

해당 필드의 단추에 연결된 레이블을 수정할 수 있습니다.

## 링크 추가 {#adding-a-link}

이미지, 단어, 단어 그룹, 텍스트 블록 등의 모든 페이지 요소에 링크를 삽입할 수 있습니다.

이렇게 하려면 요소를 선택한 다음 팝업 메뉴에서 첫 번째 아이콘을 사용합니다.

![](assets/dce_insertlink_icon.png)

이 아이콘을 사용하면 사용 가능한 모든 유형의 링크에 액세스할 수 있습니다.

![](assets/dce_insertlink_menu.png)

개인화 블록 및 필드는 텍스트 유형 블록에만 삽입할 수 있습니다.

>[!NOTE]
>
>각 링크 유형에 대해 열기 모드를 구성할 수 있습니다. **Target** 드롭다운 목록에서 대상 창을 선택하십시오. 이 값은 **`<target>`** HTML 태그에 해당합니다.
>
>사용 가능한 **대상** 목록은 다음과 같습니다.
>
>* 기타(IFrame)
>* 위쪽 창(_top)
>* 상위 창(_parent)
>* 새 창(_blank)
>* 현재 창(_self)
>* 기본 브라우저 동작
>

### URL에 연결 {#link-to-a-url}

**외부 URL에 연결** 옵션을 사용하면 소스 콘텐츠에서 모든 URL을 열 수 있습니다.

![](assets/dce_toolbar_imgblock_externallink.png)

**URL** 필드에 해당 링크 주소를 입력합니다. URL 필드는 **https://www.myURL.com**(으)로 입력해야 합니다.

### 웹 애플리케이션에 대한 링크 {#link-to-a-web-application}

**웹 응용 프로그램에 연결** 옵션을 사용하면 Adobe Campaign 웹 응용 프로그램에 액세스할 수 있습니다.

![](assets/dce_toolbar_imgblock_appweb.png)

해당 필드에서 웹 애플리케이션을 선택합니다.

제안된 웹 응용 프로그램 목록은 **[!UICONTROL Resources > Online > Web Applications]** 노드에서 사용 가능한 응용 프로그램에 해당합니다.

### 작업에 대한 링크 {#link-to-an-action}

동작을 정의하는 **링크** 옵션을 사용하면 소스 요소를 클릭할 때 동작을 구성할 수 있습니다.

![](assets/dce_toolbar_imgblock_action.png)

>[!NOTE]
>
>사용 가능한 작업은 [단추에 작업 추가](#adding-an-action-to-a-button) 섹션에 자세히 설명되어 있습니다.

### 링크 삭제 {#delete-a-link}

링크가 삽입되면 도구 모음에 만든 링크와 상호 작용할 수 있는 두 개의 새 아이콘(**링크 편집** 및 **링크 끊기**)이 제공됩니다.

* **[!UICONTROL Edit link]**&#x200B;을(를) 사용하면 링크의 모든 매개 변수를 포함하는 창을 표시할 수 있습니다.
* **[!UICONTROL Break the link]**&#x200B;을(를) 사용하면 확인 후 링크 및 모든 관련 매개 변수를 삭제할 수 있습니다.

>[!NOTE]
>
>링크가 삭제되더라도 컨텐츠는 계속 유지됩니다.

## 글꼴 속성 변경 {#changing-font-attributes}

텍스트 요소를 선택하면 글꼴 특성(스타일, 형식)을 수정할 수 있습니다.

![](assets/dce_toolbar_txt.png)

사용 가능한 옵션은 다음과 같습니다.

* **글꼴 확대** 아이콘: 선택한 텍스트의 크기를 늘립니다(`<span style="font size:">` 추가).
* **글꼴 줄이기** 아이콘: 선택한 텍스트의 크기를 줄입니다(`<span style="font size:">` 추가).
* **굵게** 아이콘: 선택한 텍스트를 굵게 만듭니다(`<strong> </strong>` 태그로 텍스트 줄바꿈).
* **기울임꼴** 아이콘: 선택한 텍스트를 기울임꼴(텍스트를 `<em> </em>` 태그로 줄바꿈)
* **밑줄** 아이콘: 선택한 텍스트에 밑줄을 긋습니다(`<span style="text-decoration: underline;">` 태그로 텍스트 줄바꿈).
* **왼쪽 정렬** 아이콘: 선택한 블록의 왼쪽으로 텍스트를 정렬합니다(style=&quot;text-align: left;&quot;).
* **Center** 아이콘: 선택한 블록의 텍스트를 가운데로 정렬합니다(style=&quot;text-align: center;&quot;).
* **오른쪽 정렬** 아이콘: 선택한 블록의 오른쪽으로 텍스트를 정렬합니다(style=&quot;text-align: right;&quot;).
* **배경색 변경** 아이콘: 선택한 블록의 배경색을 변경할 수 있습니다(style=&quot;background-color 추가: rgba(170, 86, 255, 0.87)).
* **텍스트 색상 변경** 아이콘: 선택한 블록의 텍스트 색상을 변경하거나 선택한 텍스트만 변경할 수 있습니다(`<span style="color: #CODE">`).

>[!NOTE]
>
>* **삭제** 아이콘: 블록 및 해당 콘텐츠를 모두 삭제합니다.
>
>* **복제** 아이콘: 블록과 관련된 모든 스타일을 복제합니다.

## 이미지 및 애니메이션 관리 {#managing-images-and-animations}

디지털 콘텐츠 편집기를 사용하면 브라우저와 호환되는 **모든 유형의 이미지**&#x200B;에서 작업할 수 있습니다.

>[!CAUTION]
>
>HTML 페이지의 **script** 태그에서 외부 파일을 호출해서는 안 됩니다. 이러한 파일은 Adobe Campaign 서버로 가져오지 않습니다.

### 이미지 추가/삭제/복제 {#adding---deleting---duplicating-an-image}

이미지를 삽입하려면 이미지 유형 블록을 선택하고 **이미지** 아이콘을 클릭합니다.

![](assets/dce_insert_image.png)

로컬에 저장된 이미지 파일을 선택하십시오.

![](assets/dce_popup_imgupload.png)

**삭제** 아이콘은 이미지가 포함된 태그를 삭제합니다.

**복제** 아이콘은 태그와 해당 콘텐츠를 복제합니다.

>[!CAUTION]
>
>이미지를 복제하면 새 이미지와 관련된 식별자가 삭제됩니다.

### 이미지 속성 편집 {#editing-image-properties}

이미지가 포함된 블록을 선택하면 다음 속성에 액세스합니다.

* **캡션**&#x200B;을 사용하면 이미지에 연결된 캡션을 정의할 수 있습니다(**alt** HTML 특성에 해당).
* **Dimension**&#x200B;을(를) 사용하면 이미지 크기를 픽셀 단위로 지정할 수 있습니다.

  ![](assets/dce_popup_imgsize.png)

## 개인화 콘텐츠 추가 {#adding-personalization-content}

### 개인화 필드 삽입 {#inserting-a-personalization-field}

삽입 아이콘에 대한 **Personalization 필드** 옵션을 사용하면 수신자 이름과 같은 데이터베이스 필드를 콘텐츠에 추가할 수 있습니다. 이 옵션은 텍스트 유형 블록에만 사용할 수 있습니다.

![](assets/dce_toolbar_textblock_persofield.png)

기본적으로 제공된 필드는 **[!UICONTROL Recipient]** 테이블에서 가져옵니다. 필요한 경우 웹 응용 프로그램 속성을 편집하여 다른 테이블을 선택합니다.

필드 이름이 편집기에 나타나고 노란색으로 강조 표시됩니다. 개인화가 생성되면(예: 랜딩 페이지를 미리 볼 때) 타겟팅된 수신자의 프로필로 대체됩니다.

예제는 [개인화 필드 삽입](creating-a-landing-page.md#inserting-a-personalization-field) 섹션에 나와 있습니다.

### 개인화 블록 삽입 {#inserting-a-personalization-block}

**Personalization 블록** 옵션을 사용하면 동적이고 개인화된 블록을 콘텐츠에 삽입할 수 있습니다. 예를 들어 로고 또는 인사말 메시지를 추가할 수 있습니다. 텍스트 유형 블록에는 사용할 수 없습니다.

![](assets/dce_toolbar_textblock_persoblock.png)

삽입되면 개인화 블록 이름이 편집기에 노란색으로 강조 표시됩니다. 개인화가 생성되면 수신자 프로필에 자동으로 조정됩니다.

기본 제공 개인화 블록과 사용자 지정 개인화 블록을 정의하는 방법에 대한 자세한 내용은 [이 페이지](../../delivery/using/personalization-blocks.md)를 참조하세요.
