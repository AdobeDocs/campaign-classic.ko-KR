---
solution: Campaign Classic
product: campaign
title: 데이터 스키마
description: 데이터 스키마
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 2%

---


# 데이터 스키마{#data-schemas}

다음은 Adobe Campaign에서 데이터 스키마 사용에 관한 몇 가지 일반적인 원칙입니다.

Adobe Campaign에서 데이터 스키마 만들기 및 구성에 대한 자세한 내용은 [이 섹션](../../configuration/using/about-schema-edition.md)을 참조하십시오.

## 스키마 구조 {#schema-structure}

스키마 이름 및 해당 네임스페이스를 채우려면 데이터 스키마의 XML 문서에 **`<srcschema>`** 루트 요소(**name** 및 **namespace** 특성 포함)가 있어야 합니다.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

스키마의 진입점은 기본 요소입니다. 스키마와 동일한 이름을 가지며 루트 요소의 자식이어야 하므로 쉽게 식별할 수 있습니다. 컨텐츠에 대한 설명은 이 요소로 시작합니다.

콘텐츠 관리 스키마에서 기본 요소는 다음 행으로 표시됩니다.

```
<element name="book" template="ncm:content" xmlChildren="true">
```

기본 요소에 입력한 **템플릿** 특성을 사용하면 일반 속성이 있는 스키마를 이름, 만든 날짜, 작성자, 연결된 문자열 등의 모든 콘텐츠 정의로 확장할 수 있습니다.

이러한 속성은 **ncm:content** 스키마에 설명되어 있습니다.

>[!NOTE]
>
>**xmlChildren** 특성이 있으면 기본 요소를 통해 입력된 데이터 구조가 내용 인스턴스의 XML 문서에 저장되었음을 나타냅니다.

>[!CAUTION]
>
>새 스키마를 만들거나 스키마 확장 중에 전체 스키마에 대해 동일한 기본 키 시퀀스 값(@pkSequence)을 유지해야 합니다.

## 데이터 유형 {#data-types}

다음 유형이 채워진 콘텐츠 관리 스키마의 예를 참조하십시오.

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

다양한 속성을 사용하여 데이터 스키마의 **`<element>`** 및 **`<attribute>`** 요소를 보강할 수 있습니다.

컨텐츠 관리에 사용되는 기본 속성은 다음과 같습니다.

* **레이블**:간단한 설명,
* **desc**:자세한 설명,
* **기본값**:콘텐츠 생성 시 기본값을 반환하는 표현식
* **userEnum**:이 필드를 통해 입력한 값을 저장하고 표시하는 무료 열거형입니다.
* **열거형**:가능한 값 목록을 미리 알 때 사용되는 열거형을 수정했습니다.

속성이 채워진 예제 스키마는 다음과 같습니다.

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

이 예에서 **`<chapter>`** 및 **`<page>`** 요소는 컬렉션 요소입니다. 따라서 **언바운드** 특성을 다음 요소의 정의에 추가해야 합니다.

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>**ordered=&quot;true&quot;** 특성이 있으므로 삽입된 컬렉션 요소를 주문할 수 있습니다.

## {#element-referencing}을(를) 참조하는 요소

요소 참조는 컨텐츠 스키마에서 많이 사용됩니다. 이 변수를 사용하면 **`<element>`** 요소의 정의를 계승하여 동일한 구조의 다른 요소에서 참조할 수 있습니다.

참조할 요소의 **ref** 속성은 참조 요소의 경로(XPath)로 완료해야 합니다.

**예**:예제 스키마의  **** 요소와 동일한 구조를 갖는  **`<chapter>`** 부록 섹션 추가

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

## 문자열 {#compute-string} 계산

**계산 문자열**&#x200B;은 컨텐트 인스턴스를 나타내는 문자열을 만드는 데 사용되는 XPath 표현식입니다.

다음은 해당 **계산 문자열**&#x200B;이 있는 예제 스키마입니다.

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
>**이름** 편집 컨트롤을 사용하면 이름 및 네임스페이스로 구성된 스키마 키를 입력할 수 있습니다. 스키마 루트 요소의 **name** 및 **namespace** 속성은 스키마의 XML 편집 필드에서 자동으로 업데이트됩니다.
