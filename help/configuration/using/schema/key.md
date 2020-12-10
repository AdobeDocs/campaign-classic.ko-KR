---
solution: Campaign Classic
product: campaign
title: 요소 및 속성
description: 요소 및 속성
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 2%

---


# `<key>` 요소  {#key--element}

## 콘텐츠 모델 {#content-model-8}

key:==keyfield

## 속성 {#attributes-8}

* @allowEmptyPart(boolean)
* @applicableIf(문자열)
* @internal (boolean)
* @label(문자열)
* @name(MNTOKEN)
* @noDbIndex(부울)

## 부모 {#parents-8}

`<element>`

## 하위 {#children-8}

`<keyfield>`

## 설명 {#description-8}

이 요소를 사용하면 테이블에서 레코드를 식별하는 키를 정의할 수 있습니다.

테이블에 키가 하나 이상 있어야 합니다.

## {#use-and-context-of-use-6} 사용 및 컨텍스트

일반적으로 키는 스키마와 인덱스의 기본 요소 뒤에 선언됩니다.

키에 여러 필드(예: 몇 개의 `<keyfield>` 하위)가 포함되어 있는 경우는 키를 합성이라고 합니다. 기본 키를 정의하는 데 복합 키를 사용하지 마십시오.

스키마의 기본 요소에 &quot;@autopk=true&quot; 특성이 포함된 경우 기본 키는 고유합니다. 스키마당 기본 키는 하나만 가질 수 있습니다.

처음 1000개의 식별자는 예약되어 있으므로 키에 대해 값 범위를 정의해야 하는 경우 1000부터 시작합니다.

## 특성 설명 {#attribute-description-8}

* **allowEmptyPart(부울)**:복합 키의 경우 이 속성이 활성화되면 해당 키 중 하나 이상이 비어 있지 않으면 해당 키가 유효한 것으로 간주됩니다. 이 경우 빈 개념 값은 &quot;0&quot;(부울 또는 모든 유형의 숫자 데이터에 대해)입니다. 기본적으로 복합 키를 구성하는 모든 키를 입력해야 합니다.
* **applicableIf (string)**:이 속성을 사용하면 키를 선택 사항으로 만들 수 있습니다. 키 정의를 적용할 조건에 따라 조건을 정의합니다. 이 속성은 XTK 표현식을 받습니다.
* **내부(부울)**:활성화되면 이 속성을 통해 Adobe Campaign이 키가 기본 키임을 알 수 있습니다.
* **label (string)**:키의 레이블입니다.
* **이름(MNTOKEN)**:키의 내부 이름입니다.
* **noDbIndex(부울)**:활성화되면(noDbIndex=&quot;true&quot;) 키와 일치하는 필드가 인덱싱되지 않습니다.

## 예제 {#examples-------}

&quot;@expr&quot; 또는 &quot;alias&quot; 필드를 비워 둘 수 있는 복합 키의 선언입니다.

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

`<srcschema>`에 있는 STRING 유형의 &quot;Name&quot; 필드에 있는 기본 키 선언 및 일치하는 SQL 쿼리:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
