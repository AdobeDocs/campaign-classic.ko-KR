---
product: campaign
title: 스키마 요소 및 속성
description: 매개 변수 요소
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 2%

---

# 매개 변수 요소 {#param--element}

![](../../../assets/v7-only.svg)

## 컨텐츠 모델 {#content-model-12}

param:==help

## 속성 {#attributes-12}

* @_operation (string)
* @desc (string)
* @enum (string)
* @inout (string)
* @label (string)
* @localizable (string)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (string)

## 부모 {#parents-12}

`<parameters>`

## 하위 {#children-12}

`<help>`

## 설명 {#description-12}

이 요소를 사용하면 SOAP 메서드 호출을 위한 매개 변수를 정의할 수 있습니다.

## 속성 설명 {#attribute-description-12}

* **desc(문자열)**: 과 관련된 설명 `<param>` 요소를 생성하지 않습니다.
* **inout(문자열)**: 이 속성은 매개 변수가 SOAP 호출의 입력(in) 또는 출력(출력)에 있는지 여부를 정의합니다. 이 속성을 지정하지 않으면 기본 매개 변수가 입력됩니다(&quot;@inout=in&quot;).
* **레이블(문자열)**: `<param>` 레이블
* **지역화 가능(문자열)**: 활성화되면 이 속성은 번역을 위한 &quot;@label&quot; 속성 값을 복구하도록 수집 도구에 알려줍니다(내부 사용).
* **name(MNTOKEN)**: 의 내부 이름 `<param>`
* **유형(문자열)**: 이 속성은 `<param>` 요소

   사용 가능한 유형 목록:

   * 임의
   * bin
   * blob
   * 부울
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimeenotz
   * 날짜
   * DOMDocument
   * 돔 요소
   * 이중
   * enum
   * float
   * html
   * int64
   * 링크
   * 장기간
   * 메모
   * MNTOKEN
   * 퍼센트
   * primarykey
   * short
   * string
   * 시간
   * 시간 간격
   * uuid

## 예제 {#examples-9}

문자열 유형의 &quot;serviceName&quot; 인바운드 설정에 대한 정의:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
