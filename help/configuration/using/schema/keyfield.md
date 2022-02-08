---
product: campaign
title: 스키마 요소 및 속성
description: keyfield 요소
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 2%

---

# keyfield 요소 {#keyfield--element}

![](../../../assets/v7-only.svg)

## 컨텐츠 모델 {#content-model-9}

keyfield:==EMPTY

## 속성 {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## 부모 {#parents-9}

`<key>`  ,  `<dbindex />`

## 하위 {#children-9}

없음

## 설명 {#description-9}

이 요소는 인덱스 또는 키에 통합할 필드를 정의합니다.

## 속성 설명 {#attribute-description-9}

* **xlink(MNTOKEN)**: 관계식 테이블(N-N 링크)에 대해 조인에 정의된 외래 키를 자동으로 참조할 수 있도록 해줍니다.
* **xpath(MNTOKEN)**: 인덱스 또는 키 정의 `<attribute>`  요소를 생성하지 않습니다. 이 속성은 키 또는 인덱스를 정의하는 스키마 속성의 경로를 정의하는 Xpath를 수신합니다.

## 예제 {#examples-}

&quot;@name&quot;에 Xpath가 있는 인덱스의 &quot;sName&quot; 필드 선택:

```
<keyfield xpath="@name"/>
```
