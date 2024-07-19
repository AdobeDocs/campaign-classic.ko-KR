---
product: campaign
title: 스키마 요소 및 속성 - 조건 요소
description: 조건 요소
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 5%

---

# 조건 요소 {#condition--element}

![](../../../assets/v7-only.svg)

## 콘텐츠 모델 {#content-model-2}

condition:==EMPTY

## 속성 {#attributes-2}

* @boolOperator(문자열)
* @enabledIf(문자열)
* @expr(문자열)

## 상위 {#parents-2}

`<sysfilter>`

## 하위 {#children-2}

없음

## 설명 {#description-2}

이 요소를 사용하여 필터링 조건을 정의할 수 있습니다.

## 사용 및 사용 컨텍스트 {#use-and-context-of-use-2}

하나의 `<sysfiler>` 요소에 여러 필터링 조건이 포함될 수 있습니다.

## 속성 설명 {#attribute-description-2}

* **boolOperator(string)**: 동일한 `<sysfilter>` 요소 내에 여러 `<conditions>`이(가) 정의되어 있으면 이 특성을 사용하여 해당 요소를 결합할 수 있습니다. 기본적으로 논리적 링크는 `<condition>`개 요소 사이에 있으며 &quot;AND&quot;입니다. &quot;@boolOperator&quot; 속성을 사용하면 &quot;OR&quot; 및 &quot;AND&quot; 유형 링크를 결합할 수 있습니다.
* **enabledIf (문자열)**: 조건 활성화 테스트입니다.
* **expr(문자열)**: XTK 식입니다.

## 예제 {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
