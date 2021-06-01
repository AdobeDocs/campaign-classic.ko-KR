---
product: campaign
title: 요소 및 속성
description: 요소 및 속성
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 5%

---

# 열거형 요소 {#enumeration--element}

## 컨텐츠 모델 {#content-model-5}

열거형:==(도움말| 값)

## 속성 {#attributes-5}

* @basetype (string)
* @default (string)
* @desc (string)
* @label (string)
* @name (string)
* @template (string)

## 부모 {#parents-5}

`<srcschema>`

## 하위 {#children-5}

* `<help>`
* `<value>`

## 설명 {#description-5}

이 요소를 사용하면 값 열거형을 정의할 수 있습니다. 열거형은 정의된 스키마에 속하지만 다른 스키마를 통해 액세스할 수 있습니다.

## 사용 컨텍스트 {#use-and-context-of-use-4} 사용

열거형은 스키마 시작 시(기본 요소가 정의되기 전에) 정의됩니다.

## 특성 설명 {#attribute-description-5}

* **basetype(문자열)**:열거형에 저장된 값의 유형입니다.

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

* **기본값(문자열)**:기본값. 기본값은 열거형에 정의된 값 중 하나일 수도 있습니다.
* **desc(문자열)**:열거형 설명.
* **레이블(문자열)**:열거형 레이블.
* **name(문자열)**:열거형의 내부 이름입니다.
* **템플릿(문자열)**:이 속성은 여러 스키마에서 공유되는  `<enumeration>` 요소에 대한 참조를 정의합니다. 정의가 현재 스키마에 자동으로 복사됩니다.

## 예제 {#examples-4}

값이 데이터베이스에 저장된 열거형 값의 예:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

기본값이 있는 열거형의 정의:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
