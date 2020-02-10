---
title: 컨텐츠 편집기 인터페이스
seo-title: 컨텐츠 편집기 인터페이스
description: 컨텐츠 편집기 인터페이스
seo-description: null
page-status-flag: never-activated
uuid: b108ea74-ae2c-4e47-bee8-12070927ba89
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
dc-title: </strong> and
discoiquuid: 20c64d31-c2ed-4bc9-9f0e-46f2e0c08c88
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 컨텐츠 편집기 인터페이스{#content-editor-interface}

## 편집 창 {#editing-window}

DCE 편집 창은 세 개의 서로 다른 섹션으로 분류됩니다. 이러한 기능을 사용하면 컨텐츠의 상태를 보고, 수정하고, 확인할 수 있습니다.

![](assets/dce_decoupe_window_nb.png)

1. 상단 **섹션은** 사용자에게 보내는 메시지의 표시 영역입니다. 이러한 메시지는 웹 애플리케이션 상태 또는 작성 중인 전달의 상태와 컨텐츠와 관련된 경고 및 오류 메시지를 나타냅니다. 자세한 내용은 HTML [컨텐츠 상태를](#html-content-statuses)참조하십시오.
1. 창 **왼쪽에** 있는 섹션은 컨텐츠 편집 영역입니다. 이 영역에서 사용자는 팝업 도구 모음을 사용하여 컨텐츠와 직접 상호 작용할 수 있습니다.이미지에 링크 삽입, 글꼴 변경, 필드 삭제 등 자세한 내용은 양식 [편집을](../../web/using/editing-content.md#editing-forms)참조하십시오.
1. 창 **오른쪽의** 섹션은 컨트롤 패널 영역입니다. 이 영역은 편집기에 대한 다양한 옵션, 특히 페이지 머리글 및 블록의 일반 옵션 구성과 관련된 옵션을 그룹화합니다.테두리를 추가하고, 데이터베이스 필드를 입력 영역에 연결하고, 웹 페이지 속성에 액세스하는 등의 작업을 수행합니다. 자세한 내용은 전역 옵션 및 [컨텐츠](#global-options) 편집 [섹션을](../../web/using/editing-content.md) 참조하십시오.

## 전역 옵션 {#global-options}

편집기의 오른쪽 상단 섹션에서는 현재 작성 중인 컨텐츠를 제어할 수 있는 글로벌 옵션에 액세스할 수 있습니다.

![](assets/dce_global_options.png)

4개의 아이콘이 있습니다.

![](assets/dce_icons_sidebar.png)

* 표시/ **숨기기 블록** 아이콘을 사용하면 HTML 태그에 해당하는 컨텐츠 블록 주위에 파란색 프레임을 표시할 `<div>` 수 있습니다.

* 다른 **컨텐츠** 선택 아이콘을 사용하면 템플릿(기존 템플릿 또는 기본 템플릿)에서 새 컨텐츠를 로드할 수 있습니다.

   ![](assets/dce_popup_templatechoice.png)

   >[!CAUTION]
   >
   >선택한 컨텐츠가 현재 컨텐츠를 대체합니다.

* 템플릿으로 **저장** 아이콘을 사용하면 현재 컨텐츠를 템플릿으로 저장할 수 있습니다. 템플릿의 레이블과 내부 이름을 입력해야 합니다. 템플릿은 **[!UICONTROL Resources > Templates > Content templates]** 노드에 저장됩니다.

   ![](assets/dce_popup_savetemplate.png)

   저장한 템플릿은 사용할 수 있으며 새 컨텐츠를 만들 때 선택할 수 있습니다.

   ![](assets/dce_create_fromtemplate.png)

* 페이지 **속성** 아이콘을 사용하면 HTML 페이지 맨 위에서 컨텐츠 정보를 선택할 수 있습니다.

   ![](assets/dce_popup_headerhtml.png)

   >[!NOTE]
   >
   >이 정보는 페이지의 **`<title>`** 및 **`<meta>`** HTML 태그에 해당합니다.
   >
   >키워드는 쉼표로 구분해야 합니다.

## 블록 옵션 {#block-options}

편집자 오른쪽의 섹션은 컨텐츠에 따라 작업할 수 있는 기본 옵션을 그룹화합니다. 이러한 옵션을 표시하려면 블록을 선택해야 합니다.이러한 옵션의 특성은 선택한 블록에 따라 달라집니다.

![](assets/dce_right_section.png)

다음 작업을 수행할 수 있습니다.

* 하나 또는 여러 블록에 대한 표시를 결정합니다. 가시성 조건 [정의를](../../web/using/editing-content.md#defining-a-visibility-condition)참조하십시오.
* 테두리 및 프레임을 정의합니다. 테두리 및 [배경](../../web/using/editing-content.md#adding-a-border-and-background)추가를 참조하십시오.
* 이미지 속성(크기, 캡션)을 정의합니다. 이미지 [속성](../../web/using/editing-content.md#editing-image-properties)편집을 참조하십시오.
* 데이터베이스를 양식 요소(입력 영역, 확인란)에 연결하려면 [양식의](../../web/using/editing-content.md#changing-the-data-properties-for-a-form)데이터 속성 변경을 참조하십시오.
* 양식의 일부를 필수로 지정하려면 양식의 [데이터 속성 변경을 참조하십시오](../../web/using/editing-content.md#changing-the-data-properties-for-a-form).
* 단추에 대한 작업을 정의합니다. 단추에 [작업 추가를 참조하십시오](../../web/using/editing-content.md#adding-an-action-to-a-button).

## 컨텐츠 툴바 {#content-toolbar}

도구 모음은 선택한 블록에 따라 다른 기능을 제공하는 DCE 인터페이스의 **팝업 요소입니다** .

>[!CAUTION]
>
>특정 도구 모음 함수를 사용하면 HTML 내용의 형식을 지정할 수 있습니다. 그러나 페이지에 CSS 스타일 시트가 포함되어 있는 경우 스타일 시트의 **지침은** 도구 모음으로 지정된 명령보다 **우선할** 수 있습니다.

