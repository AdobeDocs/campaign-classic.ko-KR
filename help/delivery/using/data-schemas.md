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



다음은 Adobe Campaign의 데이터 스키마 사용과 관련된 몇 가지 일반 원칙입니다.

Adobe Campaign에서 데이터 스키마를 만들고 구성하는 방법에 대한 자세한 내용은 다음을 참조하십시오. [이 섹션](../../configuration/using/about-schema-edition.md).

## 스키마 구조 {#schema-structure}

데이터 스키마의 XML 문서에는 **`<srcschema>`** 루트 요소 **이름** 및 **네임스페이스** 속성을 사용하여 스키마 이름과 해당 네임스페이스를 채웁니다.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

스키마의 시작점은 주 요소입니다. 스키마와 이름이 같기 때문에 식별하기 쉽고 루트 요소의 하위 항목이어야 합니다. 콘텐츠에 대한 설명은 이 요소에서 시작됩니다.

콘텐츠 관리 스키마에서 기본 요소는 다음 줄로 표시됩니다.

```
<element name="book" template="ncm:content" xmlChildren="true">
```

다음 **템플릿** main 요소에 입력한 속성을 사용하면 일반 속성이 있는 스키마를 이름, 생성 날짜, 작성자, 관련 문자열 등과 같은 모든 콘텐츠 정의로 확장할 수 있습니다.

이러한 속성은에 설명되어 있습니다. **ncm:content** 스키마.

>[!NOTE]
>
>의 존재 **xmlChild** attribute는 기본 요소를 통해 입력된 데이터 구조가 컨텐츠 인스턴스의 XML 문서에 저장되어 있음을 나타냅니다.

>[!CAUTION]
>
>새 스키마를 생성하거나 스키마 확장 중에 전체 스키마에 대해 동일한 기본 키 시퀀스 값(@pkSequence)을 유지해야 합니다.

## 데이터 유형 {#data-types}

다음은 유형을 채운 컨텐츠 관리 스키마의 예입니다.

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

다양한 속성을 사용하여 다음을 강화할 수 있습니다. **`<element>`** 및 **`<attribute>`** 데이터 스키마의 요소입니다.

콘텐츠 관리에 사용되는 주요 속성은 다음과 같습니다.

* **레이블**: 간단한 설명,
* **desc**: 긴 설명,
* **기본값**: 콘텐츠 생성 시 기본값을 반환하는 표현식
* **userEnum**: 이 필드를 통해 입력된 값을 저장하고 표시하기 위한 무료 열거형,
* **enum**: 가능한 값 목록을 미리 알 때 사용되는 고정된 열거형입니다.

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

컬렉션은 이름이 같고 계층 수준이 같은 요소의 목록입니다.

이 예에서는 **`<chapter>`** 및 **`<page>`** 요소는 컬렉션 요소입니다. 다음 **바인딩되지 않음** 따라서 다음 요소의 정의에 속성을 추가해야 합니다.

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

콘텐츠 스키마에서는 요소 참조가 많이 사용됩니다. 이를 통해 의 정의를 인수분해할 수 있습니다. **`<element>`** 요소를 사용하여 동일한 구조의 다른 요소에서 참조할 수 있습니다.

다음 **참조** 참조할 요소의 특성은 참조 요소의 경로(XPath)로 완료되어야 합니다.

**예**: 의 추가 **부록** 섹션과 구조가 동일한 **`<chapter>`** 예제 스키마의 요소입니다.

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

챕터 구조가 주 요소 외부에 있는 &quot;section&quot;이라는 이름의 요소로 이동합니다. 챕터와 섹션은 &quot;section&quot; 요소를 참조합니다.

## 계산 문자열 {#compute-string}

A **계산 문자열** 는 콘텐츠 인스턴스를 나타내는 문자열을 구성하는 데 사용되는 XPath 표현식입니다.

다음은 와 함께 예제 스키마입니다 **계산 문자열**:

```
<srcSchema name="book" namespace="cus">
  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    ...
  </element>
</srcSchema>
```

## 스키마 편집 {#editing-schemas}

편집 필드를 사용하면 소스 스키마의 XML 콘텐츠를 입력할 수 있습니다.

![](assets/d_ncs_integration_schema_edition.png)

소스 스키마를 저장하면 확장 스키마 생성이 자동으로 실행됩니다.

>[!NOTE]
>
>다음 **이름** 편집 컨트롤을 사용하면 이름과 네임스페이스로 구성된 스키마 키를 입력할 수 있습니다. 다음 **이름** 및 **네임스페이스** 스키마 루트 요소의 속성은 스키마의 XML 편집 필드에서 자동으로 업데이트됩니다.
