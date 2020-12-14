---
solution: Campaign Classic
product: campaign
title: 요소 및 속성
description: 요소 및 속성
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 3%

---


# 조인 요소 {#join--element}

## 컨텐트 모델 {#content-model-7}

join:==EMPTY

## 특성 {#attributes-7}

* @dstFilterExpr (문자열)
* @xpath-dst (문자열)
* @xpath-src (문자열)

## 부모 {#parents-7}

`<element>`

## 하위 {#children-7}

없음

## 설명 {#description-7}

SQL 테이블 간 조인을 만드는 필드를 정의할 수 있습니다.

## 사용 및 사용 상황{#use-and-context-of-use-5}

`<join>` 요소는 부모 `<element>` 요소가 &#39;link&#39; 유형인 경우에만 사용할 수 있습니다. 즉, 상위 요소에 &quot;@type=link&quot; 속성이 선언되어야 합니다.

`<join>` 요소에서 원격 테이블의 이름 및 네임스페이스를 지정할 필요가 없습니다. 부모 `<element>`에 지정해야 합니다.

규칙으로, 링크는 스키마 끝에 정의됩니다.

링크 유형 요소가 정의될 때 `<join>` 요소가 지정되지 않으면 두 테이블의 기본 키에 링크가 자동으로 배치됩니다.

## 특성 설명 {#attribute-description-7}

* **dstFilterExpr(문자열)**:이 속성을 사용하면 원격 테이블의 적격한 값 수를 제한할 수 있습니다.
* **xpath-dst(문자열)**:이 속성은 Xpath(원격 테이블의 @name 속성)를 받습니다.
* **xpath-src(문자열)**:이 속성은 현재 스키마의 Xpath(@name 특성)를 받습니다.

## 예제 {#examples-6}

현재 테이블의 &#39;email&#39; 필드와 원격 테이블의 &quot;@compagny-id&quot; 필드 사이의 링크:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

&#39;EN&#39; 값이 포함되어야 하는 &quot;@country&quot; 필드의 내용을 기반으로 &quot;cus:Country&quot; 테이블을 향해 필터링된 링크:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
