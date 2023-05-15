---
product: campaign
title: Campaign에서 데이터 스키마 사용
description: Campaign에서 데이터 스키마를 사용하는 방법 알아보기
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Data Model
exl-id: 3e28bfee-0321-40f4-9ef6-1bdb5b25041b
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 1%

---

# Campaign에서 데이터 스키마 사용{#data-schemas}



다음은 Adobe Campaign의 데이터 스키마 사용에 대한 몇 가지 일반적인 원칙입니다.

Adobe Campaign에서 데이터 스키마 만들기 및 구성에 대한 자세한 내용은 다음을 참조하십시오 [이 섹션](../../configuration/using/about-schema-edition.md).

## 스키마 구조 {#schema-structure}

데이터 스키마의 XML 문서에는 **`<srcschema>`** 루트 요소가 있는 요소 **이름** 및 **namespace** 스키마 이름 및 해당 네임스페이스를 채울 속성입니다.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

스키마의 시작 지점은 기본 요소입니다. 스키마와 동일한 이름을 가지며 루트 요소의 자식이어야 하므로 쉽게 식별할 수 있습니다. 컨텐츠의 설명은 이 요소로 시작됩니다.

콘텐츠 관리 스키마에서 기본 요소는 다음 행으로 표시됩니다.

```
<element name="book" template="ncm:content" xmlChildren="true">
```

다음 **템플릿** 기본 요소에 입력된 속성을 사용하여 일반 속성으로 스키마를 이름, 생성 날짜, 작성자, 관련 문자열 등의 모든 컨텐츠 정의로 확장할 수 있습니다.

이러한 속성은 **ncm:content** 스키마.

>[!NOTE]
>
>의 존재 **xmlChildren** 속성은 기본 요소를 통해 입력한 데이터 구조가 콘텐츠 인스턴스의 XML 문서에 저장됨을 나타냅니다.

>[!CAUTION]
>
>새 스키마를 만들거나 스키마 확장 중에 전체 스키마에 대해 동일한 기본 키 시퀀스 값(@pkSequence)을 유지해야 합니다.

## 데이터 유형 {#data-types}

다음은 유형이 채워진 컨텐츠 관리 스키마의 예입니다.

```
<srcSchema name="book" namespace="cus">
  <element name="book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string"/>
    <attribute name="date" type="date"/>
    <attribute name="language" type="string"/>
    <element name="chapter">
      <attribute name="name" type="string"/>
      <element name="page" type="string>
        <attribute name="number" type="short"/>
      </element>
    </element>
  </element>
</element>
```

## 속성 {#properties}

다양한 속성을 사용하여 **`<element>`** 및 **`<attribute>`** 데이터 스키마 요소입니다.

컨텐츠 관리에 사용되는 기본 속성은 다음과 같습니다.

* **레이블**: 간단한 설명,
* **desc**: 긴 설명
* **기본**: 콘텐츠 생성 시 기본값을 반환하는 표현식
* **userEnum**: 이 필드를 통해 입력한 값을 저장하고 표시하기 위한 자유 열거형
* **enum**: 가능한 값 목록을 미리 알 때 사용되는 열거형을 수정했습니다.

다음은 속성이 채워진 예제 스키마입니다.

```
<srcSchema name="book" namespace="cus">
  <enumeration name="language" basetype="string" default="eng">    
    <value name="fra" label="French"/>    
    <value name="eng" label="English"/>   
  </enumeration>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter">
      <attribute name="name" type="string" label="Name" desc="Name of chapter"/>
      <element name="page" type="string" label="Page" desc="Page content">
        <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
      </element>
    </element>
  </element>
</srcSchema>
```

## 컬렉션 요소 {#collection-elements}

컬렉션은 동일한 이름과 동일한 계층 수준을 갖는 요소 목록입니다.

이 예제에서는 **`<chapter>`** 및 **`<page>`** 요소는 수집 요소입니다. 다음 **언바운드** 따라서 속성을 이러한 요소의 정의에 추가해야 합니다.

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>의 존재 **ordered=&quot;true&quot;** 속성을 사용하면 삽입된 컬렉션 요소의 순서를 지정할 수 있습니다.

## 요소 참조 {#element-referencing}

요소 참조는 컨텐츠 스키마에서 많이 사용됩니다. 이 옵션을 통해 의 정의를 계승할 수 있습니다 **`<element>`** 동일한 구조의 다른 요소에서 참조할 수 있도록 요소를 제공합니다.

다음 **ref** 참조할 요소의 특성은 참조 요소의 경로(XPath)로 완료해야 합니다.

**예**: 추가 **부록** 구조와 동일한 구조를 갖는 섹션 **`<chapter>`** 예제 스키마의 요소입니다.

```
<srcSchema name="book" namespace="cus">
  <element name="section">
    <attribute name="name" type="string" label="Name" desc="Name"/>
    <element name="page" type="string" label="Page" desc="Content of page">
      <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
    </element>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter" ref="section"/>
    <element name="appendix" label="Appendix" ref="section"/>
  </element>
</srcSchema>
```

장 구조가 기본 요소 외부에 이름이 &quot;section&quot;인 요소로 이동합니다. 장과 섹션은 &quot;section&quot; 요소를 참조합니다.

## 계산 문자열 {#compute-string}

A **계산 문자열** 는 컨텐츠 인스턴스를 나타내는 문자열을 구성하는 데 사용되는 XPath 표현식입니다.

다음은 이 스키마와 함께 제공되는 예제 스키마입니다 **계산 문자열**:

```
<srcSchema name="book" namespace="cus">
  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    ...
  </element>
</srcSchema>
```

## 스키마 편집 {#editing-schemas}

편집 필드에서는 소스 스키마의 XML 내용을 입력할 수 있습니다.

![](assets/d_ncs_integration_schema_edition.png)

소스 스키마가 저장되면 확장 스키마 생성이 자동으로 시작됩니다.

>[!NOTE]
>
>다음 **이름** edit control을 사용하면 이름과 네임스페이스로 구성된 스키마 키를 입력할 수 있습니다. 다음 **이름** 및 **namespace** 스키마 루트 요소의 특성은 스키마의 XML 편집 필드에서 자동으로 업데이트됩니다.
