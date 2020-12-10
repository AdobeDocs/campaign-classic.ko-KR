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
source-wordcount: '42'
ht-degree: 19%

---


# `<sysfilter>` 요소  {#sysfilter--element}

## 콘텐츠 모델 {#content-model-15}

sysFilter:==condition

## 속성 {#attributes-15}

없음

## 부모 {#parents-15}

`<element>`

## 하위 {#children-15}

`<condition>`

## 설명 {#description-15}

이 요소를 사용하면 필터를 정의할 수 있습니다.

## 특성 설명 {#attribute-description-15}

이 요소에는 특성이 없습니다.

## 예제 {#examples-12}

@name 속성에 조건이 있는 필터 정의:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
