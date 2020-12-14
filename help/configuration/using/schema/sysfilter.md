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
source-wordcount: '43'
ht-degree: 18%

---


# sysfilter 요소 {#sysfilter--element}

## 컨텐트 모델 {#content-model-15}

sysFilter:==condition

## 특성 {#attributes-15}

없음

## 부모 {#parents-15}

`<element>`

## 하위 {#children-15}

`<condition>`

## 설명 {#description-15}

이 요소를 사용하면 필터를 정의할 수 있습니다.

## 특성 설명 {#attribute-description-15}

이 요소에는 속성이 없습니다.

## 예제 {#examples-12}

@name 속성에 조건이 있는 필터 정의:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
