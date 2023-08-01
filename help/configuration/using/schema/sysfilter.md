---
product: campaign
title: 요소 및 속성 - sysfilter 요소
description: 요소 및 속성
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '45'
ht-degree: 17%

---

# sysfilter 요소 {#sysfilter--element}

![](../../../assets/v7-only.svg)

## 콘텐츠 모델 {#content-model-15}

sysFilter:==condition

## 속성 {#attributes-15}

없음

## 상위 {#parents-15}

`<element>`

## 하위 {#children-15}

`<condition>`

## 설명 {#description-15}

이 요소를 사용하여 필터를 정의할 수 있습니다.

## 속성 설명 {#attribute-description-15}

이 요소에는 속성이 없습니다.

## 예제 {#examples-12}

@name 속성에 조건이 있는 필터의 정의:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
