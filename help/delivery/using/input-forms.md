---
product: campaign
title: 입력 양식
description: Campaign에서 입력 양식을 사용하는 방법 알아보기
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Data Management
exl-id: 8ec52c96-44a2-4544-93b6-9ba251510682
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 2%

---

# 입력 양식{#input-forms}



다음은 Adobe Campaign의 입력 양식 사용에 관한 몇 가지 일반 원칙입니다.

Forms은에 자세히 설명되어 있습니다. [이 섹션](../../configuration/using/identifying-a-form.md).

## 양식 구조 {#form-structure}

입력 양식의 XML 문서에는 **`<form>`** 루트 요소 **이름** 및 **네임스페이스** 속성을 사용하여 각각 양식 이름과 해당 네임스페이스를 채웁니다.

```xml
<form name="form_name" namespace="name_space">
…
</form>
```

기본적으로 양식은 이름과 네임스페이스가 동일한 데이터 스키마와 연결됩니다. 양식을 다른 이름과 연결하려면 **entity-schema** 속성 **`<form>`** 요소를 생성하지 않습니다.

입력 양식의 구조를 설명하기 위해 예제 스키마 &quot;cus:book&quot;을 기반으로 인터페이스를 설명합니다.

![](assets/d_ncs_content_form1.png)

다음은 해당 입력 양식입니다.

```xml
<form name="book" namespace="cus" type="contentForm">
  <input xpath="@name"/>
  <input xpath="@date"/>
  <input xpath="@language"/>
</form>
```

편집 요소에 대한 설명은 **`<form>`** 루트 요소입니다.

편집 컨트롤은 다음에 입력됩니다. **`<input>`** 요소가 **xpath** 스키마에 있는 필드의 경로를 포함하는 속성입니다.

**XPath 구문에 대한 알림 메시지:**

XPath 언어는 Adobe Campaign에서 데이터 스키마에 속하는 요소나 특성을 참조하는 데 사용됩니다.

XPath는 XML 문서의 트리에서 노드를 찾을 수 있는 구문입니다.

요소는 이름으로 지정되고, 속성은 &quot;@&quot; 문자 앞에 오는 이름으로 지정됩니다.

예제:

* **@date**: 이름이 &quot;date&quot;인 속성을 선택합니다.
* **챕터/@title**: 아래에서 &quot;title&quot; 속성을 선택합니다. `<chapter>` 요소
* **../@date**: 현재 요소의 상위 요소에서 날짜를 선택합니다

편집 컨트롤은 해당 데이터 유형에 자동으로 적응하고 스키마에 정의된 레이블을 사용합니다.

기본적으로 각 필드는 한 줄에 표시되며, 데이터 유형에 따라 사용 가능한 모든 공간을 차지합니다.

>[!CAUTION]
>
>입력 양식은 다음을 참조해야 합니다. **type=&quot;contentForm&quot;** 속성 **`<form>`** 요소를 사용하여 컨텐츠를 입력하는 데 필요한 프레임을 자동으로 추가합니다.

## 양식화 {#formatting}

서로 상대적인 컨트롤의 배열은 HTML 테이블에 사용된 배열과 비슷하며, 컨트롤을 여러 열로 나누거나, 요소를 교차시키거나, 사용 가능한 공간 위치를 지정할 수 있습니다. 그러나 형식을 지정하면 비율의 분포만 인증된다는 점을 유념하십시오. 객체에 대해 고정된 치수를 지정할 수 없습니다.

이 작업에 대한 자세한 정보는 [이 섹션](../../configuration/using/form-structure.md#formatting)을 참조하십시오.

## 목록 유형 컨트롤 {#list-type-controls}

컬렉션 요소를 편집하려면 목록 형식 컨트롤을 사용해야 합니다.

### 열 목록 {#column-list}

이 컨트롤에는 추가 및 삭제 단추가 포함된 도구 모음이 있는 편집 가능한 열 목록이 표시됩니다.

![](assets/d_ncs_content_form4.png)

```xml
<input xpath="chapter" type="list">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

목록 컨트롤에는 **type=&quot;list&quot;** 속성 및 목록의 경로는 컬렉션 요소를 참조해야 합니다.

열은 자식에 의해 선언됩니다 **`<input>`** 목록에 있는 요소입니다.

>[!NOTE]
>
>다음과 같은 경우 위쪽 및 아래쪽 정렬 화살표가 자동으로 추가됩니다. **ordered=&quot;true&quot;** 데이터 스키마의 컬렉션 요소에 대해 특성이 완료되었습니다.

기본적으로 도구 모음 단추는 세로로 정렬되어 있습니다. 또한 가로로 정렬할 수도 있습니다.

![](assets/d_ncs_content_form5.png)

```xml
<input nolabel="true" toolbarCaption="List of chapters" type="list" xpath="chapter">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

다음 **toolbarCaption** 속성은 도구 모음을 강제로 가로 정렬하고 목록 위에 제목을 채웁니다.

>[!NOTE]
>
>컬렉션 요소 레이블이 컨트롤 왼쪽에 표시되지 않도록 하려면 **nolabel=&quot;true&quot;** 특성.

#### 목록 확대 {#zoom-in-a-list}

목록 데이터의 삽입 및 편집은 별도의 편집 양식으로 수행할 수 있다.

목록 내에서 양식 편집은 다음과 같은 경우에 사용됩니다.

* 편리한 정보 입력을 위해,
* 다중 라인 컨트롤의 존재,
* 목록의 열에는 기본 필드만 있으며 폼에는 컬렉션 요소의 모든 필드가 표시됩니다.

![](assets/d_ncs_content_form7.png)

```xml
<input nolabel="true" toolbarCaption="List of chapters" type="list" xpath="chapter" zoom="true" zoomOnAdd="true">
  <input xpath="@name"/>
  <input xpath="@number"/>

  <form colcount="2" label="Editing a chapter">
    <input xpath="@name"/>
    <input xpath="@number"/>
    <input colspan="2" xpath="page"/>
  </form>
</input>
```

편집 양식의 정의는 다음을 통해 지정됩니다. **`<form>`** 요소를 추가합니다. 이 구조는 입력 양식의 구조와 동일합니다.

A **[!UICONTROL Detail]** 다음 경우에 단추가 자동으로 추가됩니다. **zoom=&quot;true&quot;** 목록 정의에 속성이 입력됩니다. 이렇게 하면 선택한 행에서 편집 양식을 열 수 있습니다.

>[!NOTE]
>
>추가 **zoomOnAdd=&quot;true&quot;** 속성은 목록의 요소를 삽입할 때 편집 양식을 호출하도록 강제합니다.

### 탭 목록 {#tab-list}

이 목록에는 컬렉션 요소의 편집 기능이 탭 형태로 표시됩니다.

![](assets/d_ncs_content_form6.png)

```xml
<container toolbarCaption="List of chapters" type="notebooklist" xpath="chapter" xpath-label="@name">
  <container colcount="2">
    <input xpath="@name"/>
    <input xpath="@number"/>
    <input colspan="2" xpath="page"/>
  </container>
</container>
```

목록 컨트롤에는 **type=&quot;notebooklist&quot;** 속성 및 목록의 경로는 컬렉션 요소를 참조해야 합니다.

탭의 제목에는 다음을 통해 입력한 데이터의 값이 포함됩니다. **xpath-label** 특성.

편집 컨트롤은 아래에 선언해야 합니다. **`<container>`** list 컨트롤의 자식 요소입니다.

도구 모음 단추를 사용하여 목록 요소를 추가하거나 삭제합니다.

>[!NOTE]
>
>왼쪽 및 오른쪽 정렬 화살표는 **ordered=&quot;true&quot;** 속성은 데이터 스키마의 컬렉션 요소에 대해 채워집니다.

## 컨테이너 {#containers}

컨테이너를 사용하여 컨트롤 집합을 그룹화할 수 있습니다. 이러한 속성은 다음을 통해 존재합니다. **`<container>`** 요소를 생성하지 않습니다. 이 컨트롤은 이미 여러 열의 컨트롤 서식을 지정하는 데 사용되었으며 탭 목록의 컨트롤에도 사용되었습니다.

컨테이너 및 입력 양식에서 컨테이너를 사용하는 방법에 대한 자세한 내용은 [이 섹션](../../configuration/using/form-structure.md#containers).

## 양식 편집 {#editing-forms}

편집 영역을 사용하면 입력 양식의 XML 내용을 입력할 수 있습니다.

![](assets/d_ncs_content_form12.png)

다음 **[!UICONTROL Preview]** 탭에서는 입력 양식을 볼 수 있습니다.

![](assets/d_ncs_content_form13.png)

자세한 내용 [양식 편집](../../configuration/using/editing-forms.md) 및 [양식 구조](../../configuration/using/form-structure.md).
