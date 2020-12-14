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
source-wordcount: '93'
ht-degree: 8%

---


# 조건 요소 {#condition--element}

## 컨텐트 모델 {#content-model-2}

조건:==EMPTY

## 특성 {#attributes-2}

* @boolOperator (문자열)
* @enabledIf (문자열)
* @expr (문자열)

## 부모 {#parents-2}

`<sysfilter>`

## 하위 {#children-2}

없음

## 설명 {#description-2}

이 요소를 사용하면 필터링 조건을 정의할 수 있습니다.

## 사용 및 사용 상황{#use-and-context-of-use-2}

하나의 `<sysfiler>` 요소에는 여러 필터링 조건이 포함될 수 있습니다.

## 특성 설명 {#attribute-description-2}

* **boolOperator(문자열)**:여러  `<conditions>` 요소가 동일한   `<sysfilter>` 요소 내에 정의된 경우 이 속성을 사용하여 여러 요소를 결합할 수 있습니다. 기본적으로 논리 링크는 `<condition>` 요소 사이의 &quot;AND&quot;입니다. &quot;@boolOperator&quot; 속성을 사용하여 &quot;OR&quot; 및 &quot;AND&quot; 유형 링크를 결합할 수 있습니다.
* **enabledIf (string)**:조건 활성화 테스트.
* **expr(문자열)**:XTK 표현식입니다.

## 예제 {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
