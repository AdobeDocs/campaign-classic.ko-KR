---
product: campaign
title: 스키마 요소 및 속성 - 키필드 요소
description: keyfield 요소
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 4%

---

# keyfield 요소 {#keyfield--element}

![](../../../assets/v7-only.svg)

## 콘텐츠 모델 {#content-model-9}

keyfield:==EMPTY

## 속성 {#attributes-9}

* @xlink(MNTOKEN)
* @xpath(MNTOKEN)

## 상위 {#parents-9}

`<key>`  ,  `<dbindex />`

## 하위 {#children-9}

없음

## 설명 {#description-9}

이 요소는 인덱스 또는 키에 통합할 필드를 정의합니다.

## 속성 설명 {#attribute-description-9}

* **xlink(MNTOKEN)**: 관계 테이블(N-N 링크)에 대한 조인에 정의된 외래 키를 자동으로 참조할 수 있습니다.
* **xpath(MNTOKEN)**: 의 인덱스 또는 키 정의 `<attribute>`  요소를 생성하지 않습니다. 이 속성은 키 또는 인덱스를 정의하는 스키마 속성에 대한 경로를 정의하는 Xpath를 수신합니다.

## 예제 {#examples-}

&quot;@name&quot;에 Xpath가 있는 인덱스에서 &quot;sName&quot; 필드 선택:

```
<keyfield xpath="@name"/>
```
