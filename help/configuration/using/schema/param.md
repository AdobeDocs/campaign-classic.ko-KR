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
source-wordcount: '175'
ht-degree: 6%

---


# param 요소 {#param--element}

## 컨텐트 모델 {#content-model-12}

param:==help

## 특성 {#attributes-12}

* @_operation (문자열)
* @desc (문자열)
* @enum (문자열)
* @inout (문자열)
* @label (문자열)
* @localizable (문자열)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (문자열)

## 부모 {#parents-12}

`<parameters>`

## 하위 {#children-12}

`<help>`

## 설명 {#description-12}

이 요소를 사용하면 SOAP 메서드를 호출할 매개 변수를 정의할 수 있습니다.

## 특성 설명 {#attribute-description-12}

* **desc(문자열)**:요소에 관련된  `<param>` 설명입니다.
* **inout(문자열)**:이 속성은 매개 변수가 SOAP 호출의 입력(in) 또는 출력(out)에 있는지 여부를 정의합니다. 이 속성을 지정하지 않으면 기본 매개 변수는 입력(&quot;@inout=in&quot;)입니다.
* **label (string)**: `<param>` label
* **localizable(문자열)**:활성화되면 이 속성은 번역(내부 사용)을 위해 &quot;@label&quot; 속성의 값을 복구하도록 컬렉션 도구에 지시합니다.
* **이름(MNTOKEN)**:내부 이름  `<param>`
* **type(string)**:이 속성은 요소의 유형을  `<param>` 정의합니다.

   사용 가능한 유형 목록:

   * 임의
   * bin
   * 물방울
   * boolean
   * byte
   * CDATA
   * datetime
   * datetimez
   * datetimenotz
   * date
   * DOMDocument
   * 돔 요소
   * 이중
   * enum
   * float
   * html
   * int64
   * link
   * long
   * 메모
   * MNTOKEN
   * 퍼센트
   * 기본 키
   * short
   * 문자열
   * 시간
   * timpan
   * uuid

## 예제 {#examples-9}

문자 문자열 유형의 &quot;serviceName&quot; 인바운드 설정의 정의:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
