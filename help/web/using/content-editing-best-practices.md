---
title: 콘텐츠 편집 모범 사례
seo-title: 콘텐츠 편집 모범 사례
description: 콘텐츠 편집 모범 사례
seo-description: null
page-status-flag: never-activated
uuid: badc6806-b474-4cad-94a3-003a50271281
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 3ad38469-8e22-4bfc-8029-5d360f76d6bb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 7%

---


# 콘텐츠 편집 모범 사례{#content-editing-best-practices}

편집기의 최적 작업을 위해 다음 지침을 준수하는 것이 좋습니다.

* Before **importing an HTML page template** in Adobe Campaign, please make sure the template opens and displays correctly in the various browsers.
* If the HTML page contains **JavaScript scripts**, they need to execute **without errors** outside of the editor.
* 템플릿을 작성할 때 태그에 **&#39;type&#39;** 속성을 추가하는 것이 좋습니다. `<input>` 이 정보는 편집자가 처리하고 웹 응용 프로그램을 구성할 때 데이터베이스 필드를 양식 필드에 연결하는 데 도움이 됩니다.

   템플릿의 HTML 코드 예제:

   ```
   <input id="email" type="email" name="email"/>
   ```

   인터페이스 **에 &#39;type&#39;** 속성이 표시됩니다.

   ![](assets/dce_sidebar_inputtypechanges.png)

   &#39;type&#39; 속성의 공식 목록은 이 웹 사이트 [에서 사용할 수 있습니다](https://www.w3schools.com/tags/att_input_type.asp).

* DCE를 사용하여 종료 페이지를 시뮬레이션하는 단계:

   ![](assets/dce_enchainement.png)

* 페이지에 하나만 `<body> </body>` 있는지 확인합니다.
* CSS 또는 JS 파일이 업로드되면 .zip 파일에 포함된 이미지가 업로드되지 않습니다. 따라서 CSS에 있는 이러한 이미지에 대한 참조는 업데이트되지 않습니다.

## 컨텐츠 편집기 지원 형식 {#content-editor-supported-formats}

디지털 콘텐츠 편집기는 HTML 형식을 지원합니다.언제든지 **소스** 모드로 전환할 수 있습니다.

디지털 컨텐츠 편집기의 가져오기 기능은 다음과 같이 지원되는 형식을 사용합니다.

* CSS:.zip 파일에 있는 이미지는 가져올 수 없습니다. CSS에서 이러한 이미지에 대한 참조는 업데이트되지 않습니다.
* JS:.zip 파일에 있는 이미지는 가져올 수 없습니다. JS에서 이러한 이미지에 대한 참조는 업데이트되지 않습니다.
* Iframe:연결된 페이지는 가져올 수 없습니다.
* 랜딩 페이지 및 웹 앱:양식 **** 태그가 없으면 경고가 표시됩니다. 메시지 본문에 항상 있어야 `<form> </form>` 합니다.

디지털 컨텐츠 편집기는 다음과 같은 지원되는 코드 페이지에서도 작동합니다.

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

* **회색 메시지**:정보 메시지, 편집기에서 수행할 작업은 없습니다.
* **파란색 메시지**:편집되는 컨텐츠와 관련된 정보 메시지입니다.
* **노란색 메시지**:사용자를 대신하여 작업이 필요한 경고 또는 오류 메시지

### 웹 응용 프로그램을 편집할 때의 메시지 목록 {#list-of-messages-when-editing-a-web-application}

* HTML 컨텐츠가 작동합니다.
* 웹 응용 프로그램이 게시되지 않았으므로 온라인으로 액세스할 수 없습니다.
* 웹 응용 프로그램이 온라인 상태입니다. 변경 사항을 적용하려면 다시 게시하십시오.
* 페이지 컨텐츠가 작동하지 않습니다. 여기에는 HTML 양식(`<form>`)이 포함되어야 합니다.
* 구성할 입력 영역 또는 단추가 없습니다.
* 다음 페이지로 전환을 활성화하려면 &#39;다음 페이지&#39; 작업을 현재 페이지의 단추나 링크에 연결해야 합니다.

### 배달 편집 시 메시지 목록 {#list-of-messages-when-editing-a-delivery}

* 전달 컨텐츠의 기능
* 구성할 필드나 개인화 블록이 없습니다.
* 배달 컨텐츠가 준비되었습니다. 분석을 다시 실행하여 변경 사항을 적용하십시오.
* 배달을 보낼 준비가 되었습니다.

