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
source-wordcount: '100'
ht-degree: 8%

---


# `<keyfield>` 요소  {#keyfield--element}

## 콘텐츠 모델 {#content-model-9}

keyfield:==EMPTY

## 속성 {#attributes-9}

* @xlink(MNTOKEN)
* @xpath(MNTOKEN)

## 부모 {#parents-9}

`<key>`  ,  `<dbindex />`

## 하위 {#children-9}

없음

## 설명 {#description-9}

이 요소는 색인 또는 키에 통합할 필드를 정의합니다.

## 특성 설명 {#attribute-description-9}

* **xlink(MNTOKEN)**:관계식 테이블(N-N 링크)에 대해 조인에 정의된 외래 키를 자동으로 참조할 수 있도록 해줍니다.
* **xpath(MNTOKEN)**:요소의 색인 또는 키 정의입니다 `<attribute>`  . 이 속성은 키 또는 인덱스를 정의하는 스키마 속성의 경로를 정의하는 Xpath를 받습니다.

## 예제 {#examples-}

&quot;@name&quot;에 Xpath가 있는 인덱스의 &quot;sName&quot; 필드 선택:

```
<keyfield xpath="@name"/>
```
