---
product: campaign
title: 요소 및 속성
description: 요소 및 속성
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 3%

---

# 조인 요소 {#join--element}

![](../../../assets/v7-only.svg)

## 컨텐츠 모델 {#content-model-7}

join:==EMPTY

## 속성 {#attributes-7}

* @dstFilterExpr (string)
* @xpath-dst (string)
* @xpath-src (string)

## 부모 {#parents-7}

`<element>`

## 하위 {#children-7}

없음

## 설명 {#description-7}

SQL 테이블 간에 조인을 만드는 필드를 정의할 수 있습니다.

## 사용 및 사용 컨텍스트 {#use-and-context-of-use-5}

`<join>` 요소는 상위 `<element>` 요소가 &#39;link&#39; 유형인 경우에만 사용할 수 있습니다. 즉, 상위 요소에는 &quot;@type=link&quot; 속성이 선언되어야 합니다.

`<join>` 요소에서 원격 테이블의 이름과 네임스페이스를 지정할 필요가 없습니다. 상위 `<element>`에 지정해야 합니다.

규칙에 따라 링크는 스키마 끝에 정의됩니다.

링크 유형 요소가 정의될 때 `<join>` 요소가 지정되지 않으면 링크가 두 테이블의 기본 키에 자동으로 배치됩니다.

## 속성 설명 {#attribute-description-7}

* **dstFilterExpr(문자열)**: 이 속성을 사용하면 원격 테이블에서 적합한 값의 수를 제한할 수 있습니다.
* **xpath-dst(문자열)**: 이 속성은 Xpath(원격 테이블의 @name 특성)를 수신합니다.
* **xpath-src(문자열)**: 이 속성은 Xpath(현재 스키마의 @name 특성)를 수신합니다.

## 예제 {#examples-6}

현재 테이블의 &#39;전자 메일&#39; 필드와 원격 테이블의 &quot;@compagny-id&quot; 필드 사이에 연결:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

&#39;EN&#39; 값을 포함해야 하는 &quot;@country&quot; 필드의 컨텐츠를 기반으로 &quot;cus:Country&quot; 테이블을 향해 필터링된 링크:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
