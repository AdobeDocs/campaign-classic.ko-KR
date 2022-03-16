---
product: campaign
title: 스키마 요소 및 속성 - 조건 요소
description: 조건 요소
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 3%

---

# 조건 요소 {#condition--element}

![](../../../assets/v7-only.svg)

## 컨텐츠 모델 {#content-model-2}

condition:==EMPTY

## 속성 {#attributes-2}

* @boolOperator (string)
* @enabledIf (string)
* @expr (string)

## 부모 {#parents-2}

`<sysfilter>`

## 하위 {#children-2}

없음

## 설명 {#description-2}

이 요소를 사용하면 필터링 조건을 정의할 수 있습니다.

## 사용 및 사용 컨텍스트 {#use-and-context-of-use-2}

1개 `<sysfiler>`  요소에는 여러 필터링 조건이 포함될 수 있습니다.

## 속성 설명 {#attribute-description-2}

* **boolOperator(문자열)**: 여러 개 `<conditions>` 동일한 내에서 정의됩니다  `<sysfilter>` 요소를 사용하면 이 특성을 사용하여 결합할 수 있습니다. 기본적으로 논리 링크는 다음 사이 입니다 `<condition>` 요소는 &quot;AND&quot;입니다. &quot;@boolOperator&quot; 속성을 사용하면 &quot;OR&quot;와 &quot;AND&quot; 유형 링크를 결합할 수 있습니다.
* **enabledIf (문자열)**: 조건 활성화 테스트.
* **expr(문자열)**: XTK 표현식입니다.

## 예제 {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
