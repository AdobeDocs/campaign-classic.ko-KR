---
product: campaign
title: 콘텐츠 편집 모범 사례
description: 콘텐츠 편집 모범 사례
audience: web
content-type: reference
topic-tags: editing-html-content
exl-id: c1eccb48-59bf-412f-9c18-9cda2a022096
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 6%

---

# 콘텐츠 편집 모범 사례{#content-editing-best-practices}

![](../../assets/common.svg)

편집기의 최적 작업을 수행하려면 다음 지침을 준수하는 것이 좋습니다.

* 전 **HTML 페이지 템플릿 가져오기** Adobe Campaign에서 다양한 브라우저에서 템플릿이 열리고 올바르게 표시되는지 확인하십시오.
* HTML 페이지에 **JavaScript 스크립트**&#x200B;로 설정되면 실행되어야 합니다 **오류 없음** 편집기의 외부에서.
* 템플릿을 작성할 때 태그에 **&#39;type&#39;** 속성을 추가하는 것이 좋습니다. `<input>` 이 정보는 편집기에서 처리되고 사용자가 웹 애플리케이션을 구성할 때 데이터베이스의 필드를 양식 필드에 연결하는 데 도움이 됩니다.

   템플릿의 HTML 코드 예제:

   ```
   <input id="email" type="email" name="email"/>
   ```

   다음 **&#39;type&#39;** 속성은 인터페이스에 다음 형식으로 표시됩니다.

   ![](assets/dce_sidebar_inputtypechanges.png)

   &#39;type&#39; 속성의 공식 목록을 사용할 수 있습니다 [이 웹 사이트](https://www.w3schools.com/tags/att_input_type.asp).

* DCE를 사용하여 최종 페이지를 시뮬레이션하는 단계:

   ![](assets/dce_enchainement.png)

* 하나만 있는지 확인하십시오 `<body> </body>` 참조하십시오.
* CSS 또는 JS 파일이 업로드되면 .zip 파일에 포함된 이미지가 업로드되지 않습니다. 따라서 CSS에 있는 이러한 이미지에 대한 참조는 업데이트되지 않습니다.

## 컨텐츠 편집기에서 지원하는 형식 {#content-editor-supported-formats}

디지털 콘텐츠 편집기는 HTML 형식을 지원합니다. 로 전환할 수 있습니다. **소스** 언제든지 모드 설정

디지털 콘텐츠 편집기의 가져오기 기능은 다음과 같이 지원되는 형식을 사용하여 작동합니다.

* CSS: .zip 파일에 있는 이미지는 가져올 수 없습니다. CSS에서 이러한 이미지에 대한 참조는 업데이트되지 않습니다.
* JS: .zip 파일에 있는 이미지는 가져올 수 없습니다. JS에서 이러한 이미지에 대한 참조는 업데이트되지 않습니다.
* Iframe: 연결된 페이지는 가져올 수 없습니다.
* 랜딩 페이지 및 웹 앱: if **양식** 태그가 없으면 경고가 표시됩니다. A `<form> </form>` 항상 메시지 본문에 있어야 합니다.

디지털 콘텐츠 편집기는 다음과 같은 지원되는 코드 페이지에서도 작동합니다.

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
>HTML 코드 페이지는 메타 태그(HTML 4 또는 HTML 5)나 BOM에서 정의해야 합니다. 사용 가능한 코드 페이지가 없으면 파일을 latin1로 엽니다.

## 컨텐츠 상태 HTML {#html-content-statuses}

편집기의 상단 섹션에는 컨텐츠 상태와 관련된 메시지가 표시됩니다. 메시지의 색상 코드는 다음과 같습니다.

* **회색 메시지**: 정보 메시지입니다. 편집기에서 작업을 수행할 필요가 없습니다.
* **파란색 메시지**: 편집 중인 컨텐츠와 관련된 정보 메시지.
* **노란색 메시지**: 사용자를 대신하여 조치가 필요한 경고 또는 오류 메시지.

### 웹 응용 프로그램을 편집할 때의 메시지 목록 {#list-of-messages-when-editing-a-web-application}

* HTML 컨텐츠가 작동합니다.
* 웹 응용 프로그램이 게시되지 않았으므로 온라인으로 액세스할 수 없습니다.
* 웹 응용 프로그램이 온라인 상태입니다. 변경 내용을 적용하려면 다시 게시하십시오.
* 페이지 컨텐츠가 작동하지 않습니다. 여기에는 HTML 양식(`<form>`)
* 구성할 입력 영역 또는 단추가 없습니다.
* 다음 페이지로 전환하려면 &#39;다음 페이지&#39; 작업을 현재 페이지의 단추나 링크에 연결해야 합니다.

### 게재를 편집할 때 메시지 목록 {#list-of-messages-when-editing-a-delivery}

* 게재 컨텐츠가 작동합니다
* 구성할 필드나 개인화 블록이 없습니다.
* 게재 콘텐츠가 준비되었습니다. 분석을 다시 실행하여 변경 사항을 적용하십시오.
* 게재를 보낼 준비가 되었습니다.
