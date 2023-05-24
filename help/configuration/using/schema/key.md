---
product: campaign
title: 스키마 요소 및 속성 - 키 요소
description: 주요 요소
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 1%

---

# 주요 요소 {#key--element}

![](../../../assets/v7-only.svg)

## 콘텐츠 모델 {#content-model-8}

key:==keyfield

## 속성 {#attributes-8}

* @allowEmptyPart(부울)
* @applicableIf(문자열)
* @internal(부울)
* @label(문자열)
* @name(MNTOKEN)
* @noDbIndex(부울)

## 상위 {#parents-8}

`<element>`

## 하위 {#children-8}

`<keyfield>`

## 설명 {#description-8}

이 요소를 사용하여 테이블에서 레코드를 식별하는 키를 정의할 수 있습니다.

테이블에는 하나 이상의 키가 있어야 합니다.

## 사용 및 사용 컨텍스트 {#use-and-context-of-use-6}

일반적으로 키는 스키마의 기본 요소와 인덱스 뒤에 선언됩니다.

키가 여러 필드(예: 여러 필드)를 포함하는 경우 복합 키라고 합니다 `<keyfield>` 하위). 복합 키를 사용하여 기본 키를 정의하지 마십시오.

스키마의 주 요소에 &quot;@autopk=true&quot; 속성이 포함된 경우 기본 키는 고유합니다. 스키마당 기본 키는 하나만 가질 수 있습니다.

처음 1000개의 식별자가 예약되어 있으므로 키에 대해 값 범위를 정의해야 하는 경우 1000부터 시작합니다.

## 속성 설명 {#attribute-description-8}

* **allowEmptyPart(부울)**: 복합 키의 경우 이 속성이 활성화되면 해당 키 중 하나 이상이 비어 있지 않으면 해당 키가 유효한 것으로 간주됩니다. 이 경우 빈 개념 값은 &quot;0&quot;(부울 또는 모든 숫자 데이터 유형의 경우)입니다. 기본적으로 복합 키를 구성하는 모든 키를 입력해야 합니다.
* **applicableIf (문자열)**: 이 속성을 사용하면 키를 선택 사항으로 만들 수 있습니다. 키 정의가 적용될 조건을 정의합니다. 이 속성은 XTK 식을 받습니다.
* **내부(부울)**: 활성화되면 이 속성은 Adobe Campaign에게 키가 기본임을 알려줍니다.
* **레이블(문자열)**: 키의 레이블입니다.
* **이름(MNTOKEN)**: 키의 내부 이름입니다.
* **noDbIndex(부울)**: 활성화된 경우(noDbIndex=&quot;true&quot;) 키와 일치하는 필드가 인덱싱되지 않습니다.

## 예제 {#examples-------}

&quot;@expr&quot; 또는 &quot;별칭&quot; 필드를 비워둘 수 있는 복합 키 선언:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

에서 STRING 형식의 &quot;이름&quot; 필드에 기본 키를 선언합니다. `<srcschema>`  일치하는 SQL 쿼리:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
