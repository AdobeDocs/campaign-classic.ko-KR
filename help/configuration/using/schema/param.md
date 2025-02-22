---
product: campaign
title: 스키마 요소 및 속성 - 매개 변수 요소
description: 매개 변수 요소
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 9%

---

# 매개 변수 요소 {#param--element}


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

이 요소를 사용하여 SOAP 메서드 호출을 위한 매개 변수를 정의할 수 있습니다.

## 속성 설명 {#attribute-description-12}

* **desc(문자열)**: `<param>` 요소와 관련된 설명입니다.
* **inout(문자열)**: 이 특성은 매개 변수가 SOAP 호출의 입력(in) 또는 출력(out)에 있는지 여부를 정의합니다. 이 속성을 지정하지 않으면 기본 매개 변수가 입력됩니다(&quot;@inout=in&quot;).
* **레이블(문자열)**: `<param>` 레이블
* **localizable(문자열)**: 활성화되면 이 특성은 컬렉션 도구에 변환을 위해 &quot;@label&quot; 특성의 값을 복구하도록 알려줍니다(내부 사용).
* **이름(MNTOKEN)**: `<param>`의 내부 이름
* **type(문자열)**: 이 특성은 `<param>` 요소의 유형을 정의합니다.

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
   * 날짜
   * DOMDocument
   * DOMELEMENT
   * 중복
   * enum
   * 부동
   * html
   * int64
   * 링크
   * 길게
   * 메모
   * MNTOKEN
   * 백분율
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
