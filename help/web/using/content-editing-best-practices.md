---
title: 컨텐츠 편집 우수 사례
seo-title: 컨텐츠 편집 우수 사례
description: 컨텐츠 편집 우수 사례
seo-description: null
page-status-flag: never-activated
uuid: badc6806-b474-4cad-94a3-003a50271281
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 3ad38469-8e22-4bfc-8029-5d360f76d6bb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# 컨텐츠 편집 우수 사례{#content-editing-best-practices}

편집기의 최적 작업을 위해 다음 지침을 준수하는 것이 좋습니다.

* Adobe Campaign에서 HTML 페이지 템플릿을 **** 가져오기 전에 템플릿이 열려 있고 다양한 브라우저에서 올바르게 표시되는지 확인하십시오.
* HTML 페이지에 JavaScript **스크립트가**&#x200B;있는 경우 편집기 외부에서 오류 **** 없이 실행해야 합니다.
* 템플릿을 작성할 때는 **태그에** &#39;type&#39; `<input>` 속성을 추가하는 것이 좋습니다. 이 정보는 편집자가 처리하며 웹 응용 프로그램을 구성할 때 데이터베이스의 필드를 양식 필드에 연결하는 데 도움이 됩니다.

   템플릿의 HTML 코드 예:

   ```
   <input id="email" type="email" name="email"/>
   ```

   The **&#39;type&#39;** attribute is visible in the interface in the following form:

   ![](assets/dce_sidebar_inputtypechanges.png)

   &#39;유형&#39; 속성의 공식 목록은 이 [웹 사이트에서](https://www.w3schools.com/tags/att_input_type.asp)사용할 수 있습니다.

* DCE 파섹

   ![](assets/dce_enchainement.png)

* 페이지에 하나만 `<body> </body>` 있어야 합니다.
* CSS 또는 JS 파일이 업로드되면 .zip 파일에 포함된 이미지가 업로드되지 않습니다. 따라서 CSS에 있는 이러한 이미지에 대한 참조는 업데이트되지 않습니다.

## 컨텐츠 편집기 지원 포맷 {#content-editor-supported-formats}

디지털 컨텐츠 편집기는 HTML 형식을 지원합니다.언제든지 **소스** 모드로 전환할 수 있습니다.

디지털 컨텐츠 편집기의 가져오기 기능은 다음과 같이 지원되는 형식을 사용합니다.

* CSS:.zip 파일에 있는 이미지는 가져올 수 없습니다. CSS에서 이러한 이미지에 대한 참조는 업데이트되지 않습니다.
* JS:.zip 파일에 있는 이미지는 가져올 수 없습니다. JS에서 이러한 이미지에 대한 참조는 업데이트되지 않습니다.
* Iframe:연결된 페이지는 가져올 수 없습니다.
* 랜딩 페이지 및 웹 앱:양식 **태그가** 없으면 경고가 표시됩니다. 메시지 본문에 항상 `<form> </form>` 있어야 합니다.

디지털 컨텐츠 편집기는 다음 지원되는 코드 페이지에서도 작동합니다.

* iso-8859-1
* iso-8859-2
* utf-7
* utf-8(BOM 사용 시 권장)
* iso-8859-15
* us-ascii
* shift jis
* iso-2022-jp
* big-5
* euc-kr
* utf-16

>[!NOTE]
>
>HTML 코드 페이지는 메타 태그(HTML 4 또는 HTML 5) 또는 BOM에서 정의해야 합니다. 사용할 수 있는 코드 페이지가 없으면 파일을 latin1로 엽니다.

## HTML 컨텐츠 상태 {#html-content-statuses}

편집기의 상단 섹션에는 컨텐츠 상태와 관련된 메시지가 표시됩니다. 메시지의 색상 코드는 다음과 같습니다.

* **회색 메시지**:정보 메시지, 편집기에서 수행할 작업이 없습니다.
* **파란색 메시지**:편집 중인 컨텐츠와 관련된 정보 메시지입니다.
* **노란색 메시지**:사용자를 대신하여 작업이 필요한 경고 또는 오류 메시지

### 웹 응용 프로그램을 편집할 때의 메시지 목록 {#list-of-messages-when-editing-a-web-application}

* HTML 컨텐츠가 작동합니다.
* 웹 응용 프로그램이 게시되지 않았으므로 온라인으로 액세스할 수 없습니다.
* 웹 응용 프로그램이 온라인 상태입니다. 변경 내용을 적용하려면 다시 게시하십시오.
* 페이지 컨텐츠가 작동하지 않습니다. 여기에는 HTML 양식(`<form>`)이 포함되어야 합니다.
* 구성할 입력 영역 또는 단추가 없습니다.
* 다음 페이지로 전환하려면 현재 페이지의 단추나 링크에 &#39;다음 페이지&#39; 동작을 연결해야 합니다.

### 배달 편집 시 메시지 목록 {#list-of-messages-when-editing-a-delivery}

* 게재 컨텐츠의 기능
* 구성할 필드나 개인화 블록이 없습니다.
* 게재 컨텐츠가 준비되었습니다. 분석을 다시 실행하여 변경 사항을 적용하십시오.
* 배송을 받을 준비가 되었습니다.

