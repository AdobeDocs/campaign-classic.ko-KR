---
product: campaign
title: 요소 및 속성 - sysfilter 요소
description: 요소 및 속성
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
TQID: 'https://experienceleague.adobe.com/hjsD-JSGBPnwyj1IsLDo-tUy-63apy0-6kT9vngaaQk'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '45'
ht-degree: 17%
---
# sysfilter 요소 {#sysfilter--element}


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
