---
title: 양식 렌더링
seo-title: 양식 렌더링
description: 양식 렌더링
seo-description: null
page-status-flag: never-activated
uuid: 714ce201-5535-4fde-b388-1605ac54edcb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 669635bd-868b-4550-b075-6294ccb71297
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '989'
ht-degree: 2%

---


# 양식 렌더링{#form-rendering}

## 양식 렌더링 템플릿 선택 {#selecting-the-form-rendering-template}

양식 설정을 사용하면 페이지를 생성하는 데 사용되는 템플릿을 선택할 수 있습니다. 이 항목에 액세스하려면 양식 세부 사항 도구 모음에서 **[!UICONTROL Settings]** 단추를 클릭하고 **[!UICONTROL Rendering]** 탭을 선택합니다. 기본적으로 사용할 수 있는 여러 템플릿(스타일 시트)이 있습니다.

![](assets/s_ncs_admin_survey_rendering_select.png)

편집기의 하단 섹션에서는 선택한 템플릿의 렌더링을 볼 수 있습니다.

확대/축소 기능을 사용하면 선택한 템플릿을 편집할 수 있습니다.

![](assets/s_ncs_admin_survey_render_edit.png)

이러한 템플릿을 수정하거나 재정의할 수 있습니다. 이렇게 하려면 링크를 클릭하고 정보를 **[!UICONTROL Page layout...]** 개인화합니다.

![](assets/s_ncs_admin_survey_render_edit_param.png)

다음을 수행할 수 있습니다.

* 로고로 사용되는 이미지를 변경하고 크기를 조정합니다.
* 또한 사용자가 이 렌더링 템플릿을 선택할 때 미리 보기 이미지에 액세스할 수 있는 경로를 지정합니다.

이 **[!UICONTROL Headers/Footers]** 탭에서는 이 템플릿을 사용하여 각 양식 페이지의 머리글과 바닥글에 표시되는 정보를 변경할 수 있습니다.

![](assets/s_ncs_admin_survey_render_edit_header.png)

및 섹션의 각 줄 **[!UICONTROL Page headers]** 은 HTML **[!UICONTROL Page footers]** 페이지의 행에 해당합니다. Click **[!UICONTROL Add]** to create a new line.

기존 줄을 선택하고 **[!UICONTROL Detail]** 단추를 클릭하여 원하는 대로 변경합니다.

![](assets/s_ncs_admin_survey_render_edit_header_detail.png)

선의 내용을 변경하고 테두리를 추가하고 관련 탭을 통해 글꼴 속성을 변경할 수 있습니다. 이 변경 사항 **[!UICONTROL OK]** 을 확인하려면 을(를) 클릭합니다.

이 필드를 사용하면 페이지 머리글과 바닥글의 요소 위치를 정의할 수 있습니다. **[!UICONTROL Position]**

![](assets/s_ncs_admin_survey_render_edit_header_position.png)

>[!NOTE]
>
>렌더링 템플릿은 **[!UICONTROL Administration > Configuration > Form rendering]** 노드에 저장됩니다.\
>자세한 내용은 양식 렌더링 [사용자 정의를 참조하십시오.](#customizing-form-rendering)

## 양식 렌더링 사용자 정의 {#customizing-form-rendering}

### 요소의 레이아웃 변경 {#changing-the-layout-of-elements}

양식의 각 요소(입력 필드, 이미지, 라디오 단추 등)에 대해 스타일 시트를 오버로드할 수 있습니다.

To do this, use the **[!UICONTROL Advanced]** tab.

![](assets/s_ncs_admin_survey_advanced_tab.png)

다음 속성을 정의할 수 있습니다.

* **[!UICONTROL Label position]**:레이블 [위치 정의를 참조하십시오](../../web/using/defining-web-forms-layout.md#defining-the-position-of-labels).
* **[!UICONTROL Label format]**:단어 감싸기 또는 줄 바꿈 없음,
* **[!UICONTROL Number of cells]** :페이지 [에 필드 위치 지정을 참조하십시오](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).
* **[!UICONTROL Horizontal alignment]** (왼쪽, 오른쪽, 가운데) 및 **[!UICONTROL Vertical alignment]** (높음, 낮음, 가운데),
* **[!UICONTROL Width]** 영역:백분율 또는 em, 포인트 또는 픽셀(기본값)로 표현될 수 있습니다.
* 최대 **[!UICONTROL Length]**:허용되는 최대 문자 수(텍스트, 숫자 및 암호 유형 컨트롤의 경우),
* **[!UICONTROL Lines]**:문자 영역에 대한 **[!UICONTROL Multi-line text]** 줄 수,
* **[!UICONTROL Style inline]**:추가 설정으로 CSS 스타일 시트를 오버로드할 수 있습니다. 이러한 속성은 서로 구분되어 **있습니다.** 아래 예제에 표시된 문자:

   ![](assets/s_ncs_admin_survey_advanced_tab_inline.png)

### 머리글 및 바닥글 정의 {#defining-headers-and-footers}

필드는 루트의 이름이 페이지와 동일한 트리 구조로 정렬됩니다. 이름을 수정하려면 선택하십시오.

창의 제목은 양식 속성 창의 **[!UICONTROL Page]** 탭에 입력해야 합니다. 페이지 머리글과 바닥글에 설정된 컨텐츠를 추가할 수도 있습니다. 이 정보는 모든 페이지에 표시됩니다. 이 컨텐츠는 아래와 같이 **[!UICONTROL Texts]** 탭의 일치 섹션에 입력됩니다.

![](assets/s_ncs_admin_survey_titles_config.png)

### HTML 헤더에 요소 추가 {#adding-elements-to-html-header}

양식 페이지의 HTML 헤더에 삽입할 추가 요소를 입력할 수 있습니다. 이렇게 하려면 관련 페이지의 **[!UICONTROL Header]** 탭에 요소를 입력합니다.

이렇게 하면 페이지의 제목 표시줄에 표시할 아이콘을 참조할 수 있습니다.

![](assets/webform_header_page_tab.png)

## 제어 설정 정의 {#defining-control-settings}

사용자가 양식을 채울 때 형식이나 구성에 따라 특정 필드에 자동으로 검사가 수행됩니다. 특정 필드를 필수 입력(필수 필드 [정의 참조](#defining-mandatory-fields))으로 만들거나 입력한 데이터의 형식을 확인할 수 있습니다(데이터 형식 [확인 참조](#checking-data-format)). 확인은 페이지 승인 중에 수행됩니다(출력 전환을 가능하게 하는 링크나 단추를 클릭하여).

### 필수 필드 정의 {#defining-mandatory-fields}

특정 필드를 필수 필드로 만들려면 필드를 만들 때 이 옵션을 선택합니다.

![](assets/s_ncs_admin_survey_required_field.png)

사용자가 필드에 입력하지 않고 이 페이지를 승인하면 다음 메시지가 표시됩니다.

![](assets/s_ncs_admin_survey_required_default_msg.png)

링크를 클릭하여 이 메시지를 개인화할 수 **[!UICONTROL Personalize this message]** 있습니다.

![](assets/s_ncs_admin_survey_required_custom_msg.png)

사용자가 필드에 입력하지 않고 이 페이지를 승인하면 다음 메시지가 표시됩니다.

![](assets/s_ncs_admin_survey_required_custom_msg2.png)

### 데이터 형식 확인 {#checking-data-format}

데이터베이스의 기존 필드에 값이 저장되어 있는 양식을 확인하는 경우 저장소 필드에 대한 규칙이 적용됩니다.

값이 변수에 저장되어 있는 양식 확인의 경우 승인 규칙은 변수의 형식에 따라 다릅니다.

예를 들어, 아래와 같이 클라이언트 번호를 저장하는 **[!UICONTROL Number]** 검사를 만드는 경우:

![](assets/s_ncs_admin_survey_choose_format.png)

사용자는 양식 필드에 정수를 입력해야 합니다.

## 조건부 표시 필드 정의 {#defining-fields-conditional-display}

사용자가 선택한 값을 기준으로 표시할 페이지의 필드 표시를 구성할 수 있습니다. 이는 한 필드 또는 여러 필드(컨테이너로 그룹화된 경우)에 적용할 수 있습니다.

페이지의 각 요소에 대해 **[!UICONTROL Visibility]** 표시 조건을 정의할 수 있습니다.

![](assets/s_ncs_admin_survey_condition_edit.png)

조건은 데이터베이스 필드 또는 변수의 값과 관련이 있을 수 있습니다.

필드 선택 창에서 다음 데이터 중에서 선택할 수 있습니다.

![](assets/s_ncs_admin_survey_condition_select.png)

* 기본 트리에는 양식 컨텍스트의 매개 변수가 포함되어 있습니다. 기본 매개 변수는 받는 사람의 암호화된 식별자와 일치하는 식별자, 언어 및 원본입니다.

   자세한 정보는 이 [페이지](../../web/using/defining-web-forms-properties.md#form-url-parameters)를 참조하십시오.

* 하위 **[!UICONTROL Recipients]** 트리에는 양식에 삽입되고 데이터베이스에 저장된 입력 필드가 포함되어 있습니다.

   자세한 내용은 데이터베이스에 데이터 [저장을 참조하십시오](../../web/using/web-forms-answers.md#storing-data-in-the-database).

* 하위 **[!UICONTROL Variables]** 트리에는 이 양식에 사용할 수 있는 변수가 포함되어 있습니다. 자세한 내용은 로컬 변수에 [데이터 저장을 참조하십시오](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable).

자세한 내용은 다음 사용 사례를 참조하십시오. [선택한 값에 따라 다른 옵션을 표시합니다](../../web/using/use-cases--web-forms.md#displaying-different-options-depending-on-the-selected-values).

또한 개체를 사용하여 양식 페이지의 표시를 조건화할 수도 **[!UICONTROL Test]** 있습니다. 자세한 정보는 이 [페이지](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)를 참조하십시오.

## 기존 양식에서 요소 가져오기 {#importing-elements-from-an-existing-form}

다른 웹 양식에서 필드나 컨테이너를 가져올 수 있습니다. 이를 통해 주소 블록, 뉴스레터 구독 영역 등과 같이 양식에 삽입되는 재사용 가능한 블록 라이브러리를 만들 수 있습니다.

요소를 양식에 가져오려면 다음 단계를 적용합니다.

1. 하나 이상의 요소를 삽입할 페이지를 편집한 다음 도구 모음 **[!UICONTROL Import an existing block]** 에서 클릭합니다.

   ![](assets/s_ncs_admin_survey_import_block.png)

1. 가져올 필드가 포함된 웹 양식을 선택하고 가져올 컨테이너 및 필드를 선택합니다.

   ![](assets/s_ncs_admin_survey_import_block_selection.png)

   >[!NOTE]
   >
   >소스 양식 이름 오른쪽에 있는 **[!UICONTROL Edit link]** 아이콘을 사용하면 선택한 웹 양식을 볼 수 있습니다.

1. 삽입 **[!UICONTROL Ok]** 을 확인하려면 을(를) 클릭합니다.

   ![](assets/s_ncs_admin_survey_import_block_rendering.png)

