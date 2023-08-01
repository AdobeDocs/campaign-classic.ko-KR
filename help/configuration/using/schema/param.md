---
product: campaign
title: 스키마 요소 및 속성 - 매개 변수 요소
description: 매개 변수 요소
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 7%

---

# 매개 변수 요소 {#param--element}

![](../../../assets/v7-only.svg)

## 콘텐츠 모델 {#content-model-12}

param:==help

## 속성 {#attributes-12}

* @_operation(문자열)
* @desc(문자열)
* @enum(문자열)
* @inout(문자열)
* @label(문자열)
* @localizable(문자열)
* @name(MNTOKEN)
* @namespace(MNTOKEN)
* @type(문자열)

## 상위 {#parents-12}

`<parameters>`

## 하위 {#children-12}

`<help>`

## 설명 {#description-12}

이 요소를 사용하면 SOAP 메서드를 호출하기 위한 매개 변수를 정의할 수 있습니다.

## 속성 설명 {#attribute-description-12}

* **desc(문자열)**: 다음과 관련된 설명 `<param>` 요소를 생성하지 않습니다.
* **inout(문자열)**: 이 속성은 매개 변수가 SOAP 호출의 입력(in) 또는 출력(out)에 있는지 여부를 정의합니다. 이 속성을 지정하지 않으면 기본 매개 변수가 입력됩니다(&quot;@inout=in&quot;).
* **레이블(문자열)**: `<param>` 레이블
* **현지화 가능(문자열)**: 활성화되면 이 속성은 수집 툴에게 번역(내부 사용)을 위해 &quot;@label&quot; 속성 값을 복구하도록 알려줍니다.
* **이름(MNTOKEN)**: 의 내부 이름 `<param>`
* **유형(문자열)**: 이 속성은 의 유형을 정의합니다. `<param>` 요소

  사용 가능한 유형 목록:

   * 모든
   * bin
   * blob
   * 부울
   * 바이트
   * C데이터
   * datetime
   * datetimetz
   * 다테티메노츠
   * date
   * DOMDocument
   * DOMELEMENT
   * 더블
   * enum
   * 부동
   * html
   * int64
   * 링크
   * 길게
   * 메모
   * MNTOKEN
   * percent
   * primarykey
   * 짧음
   * 문자열
   * 시간
   * timespan
   * uuid

## 예제 {#examples-9}

문자열 유형의 &quot;serviceName&quot; 인바운드 설정 정의:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
