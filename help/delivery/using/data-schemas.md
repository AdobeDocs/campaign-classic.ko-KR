---
title: 데이터 스키마
seo-title: 데이터 스키마
description: 데이터 스키마
seo-description: null
page-status-flag: never-activated
uuid: 3327a38c-e44d-4581-a67b-bb60c1604a5f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: aeaa9475-3715-40a4-8864-29d126883272
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 데이터 스키마{#data-schemas}

다음은 Adobe Campaign에서 데이터 스키마 사용과 관련된 몇 가지 일반적인 원칙입니다.

Adobe Campaign에서 데이터 스키마 만들기 및 구성에 대한 자세한 내용은 [이 섹션을](../../configuration/using/about-schema-edition.md)참조하십시오.

## 스키마 구조 {#schema-structure}

스키마 이름과 네임스페이스를 채우려면 데이터 스키마의 XML 문서에 **`<srcschema>`** 이름 **및** 네임스페이스 **특성이 있는** 루트 요소가 있어야 합니다.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

스키마의 진입점은 기본 요소입니다. 스키마와 이름이 동일하며 루트 요소의 자식이어야 하므로 쉽게 식별할 수 있습니다. 컨텐트에 대한 설명은 이 요소로 시작합니다.

컨텐츠 관리 스키마에서 기본 요소는 다음 줄로 표시됩니다.

```
<element name="book" template="ncm:content" xmlChildren="true">
```

기본 요소에 입력된 **템플릿** 속성을 사용하면 일반 속성이 있는 스키마를 이름, 생성 날짜, 작성자, 연결된 문자열 등과 같은 모든 컨텐츠 정의로 확장할 수 있습니다.

이러한 속성은 **ncm:content** 스키마에 설명되어 있습니다.

>[!NOTE]
>
>xmlChildren **특성이** 있으면 기본 요소를 통해 입력된 데이터 구조가 컨텐츠 인스턴스의 XML 문서에 저장됨을 나타냅니다.

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

다양한 속성을 사용하여 데이터 스키마의 **`<element>`** 및 **`<attribute>`** 요소를 강화할 수 있습니다.

컨텐츠 관리에 사용되는 기본 속성은 다음과 같습니다.

* **레이블**:간략한 설명,
* **desc**:자세한 설명,
* **기본값**:표현식 컨텐츠 생성 시 기본값 반환,
* **userEnum**:이 필드를 통해 입력한 값을 저장하고 표시하는 무료 열거형
* **enum**:가능한 값 목록을 미리 알 때 사용되는 열거형을 수정했습니다.

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

컬렉션은 동일한 이름과 동일한 계층 수준의 요소 목록입니다.

이 예에서는 **`<chapter>`** 및 **`<page>`** 요소가 수집 요소입니다. 따라서 **언바운드** 속성은 다음 요소의 정의에 추가해야 합니다.

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>ordered=&quot; **true&quot;** 속성이 있으면 삽입된 컬렉션 요소를 주문할 수 있습니다.

## 참조 요소 {#element-referencing}

요소 참조는 컨텐츠 스키마에서 많이 사용됩니다. 이 기능을 사용하면 **`<element>`** 요소의 정의를 계승하여 동일한 구조를 가진 다른 요소에서 참조할 수 있습니다.

참조할 요소의 **ref** 속성은 참조 요소의 경로(XPath)와 함께 완료해야 합니다.

**예**:예제 **스키마의** 요소와 동일한 구조를 갖는 부록 섹션 추가 **`<chapter>`** .

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

장 구조는 기본 요소 외부에 이름이 &quot;section&quot;인 요소로 이동합니다. 장과 섹션은 &quot;section&quot; 요소를 참조합니다.

## 문자열 계산 {#compute-string}

컴퓨팅 **문자열은** 컨텐츠 인스턴스를 나타내는 문자열을 구성하는 데 사용되는 XPath 표현식입니다.

다음은 Compute 문자열이 있는 예제 **스키마입니다**.

```
<srcSchema name="book" namespace="cus">
  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    ...
  </element>
</srcSchema>
```

## 스키마 편집 {#editing-schemas}

편집 필드에서 소스 스키마의 XML 내용을 입력할 수 있습니다.

![](assets/d_ncs_integration_schema_edition.png)

소스 스키마가 저장되면 확장 스키마 생성이 자동으로 시작됩니다.

>[!NOTE]
>
>이름 **편집** 컨트롤을 사용하면 이름 및 네임스페이스로 구성된 스키마 키를 입력할 수 있습니다. 스키마 루트 요소의 **이름** 및 **네임스페이스** 속성은 스키마의 XML 편집 필드에서 자동으로 업데이트됩니다.
