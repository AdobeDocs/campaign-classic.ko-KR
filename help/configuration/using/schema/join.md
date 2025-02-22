---
product: campaign
title: 스키마 요소 및 속성 - 조인 요소
description: 조인 요소
feature: Schema Extension
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---

# 조인 요소 {#join--element}


## 콘텐츠 모델 {#content-model-7}

join:==EMPTY

## 속성 {#attributes-7}

* @dstFilterExpr(문자열)
* @xpath-dst(문자열)
* @xpath-src(문자열)

## 상위 {#parents-7}

`<element>`

## 하위 {#children-7}

없음

## 설명 {#description-7}

SQL 테이블 간에 조인을 만드는 필드를 정의할 수 있습니다.

## 사용 및 사용 컨텍스트 {#use-and-context-of-use-5}

`<join>` 요소는 부모 `<element>` 요소가 &#39;link&#39; 유형인 경우에만 사용할 수 있습니다. 즉, 상위 요소에는 &quot;@type=link&quot; 특성이 선언되어 있어야 합니다.

`<join>` 요소에 원격 테이블의 이름과 네임스페이스를 지정할 필요는 없습니다. 상위 `<element>`에 지정해야 합니다.

규칙에 따라 스키마의 끝에 링크가 정의됩니다.

링크 유형 요소를 정의할 때 `<join>` 요소를 지정하지 않으면 두 테이블의 기본 키에 링크가 자동으로 배치됩니다.

## 속성 설명 {#attribute-description-7}

* **dstFilterExpr(문자열)**: 이 특성을 사용하면 원격 테이블의 적격 값 수를 제한할 수 있습니다.
* **xpath-dst(문자열)**: 이 특성은 Xpath(원격 테이블의 @name 특성)를 받습니다.
* **xpath-src(문자열)**: 이 특성은 Xpath(현재 스키마의 @name 특성)를 받습니다.

## 예제 {#examples-6}

현재 테이블의 &quot;이메일&quot; 필드와 원격 테이블의 &quot;@compagny-id&quot; 필드 간 링크:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

&#39;EN&#39; 값을 포함해야 하는 &quot;@country&quot; 필드의 콘텐츠를 기반으로 &quot;cus:Country&quot; 테이블로 필터링된 링크:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
