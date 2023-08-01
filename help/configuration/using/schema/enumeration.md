---
product: campaign
title: 스키마 요소 및 속성 - 열거형 요소
description: 열거형 요소
feature: Schema Extension
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 6%

---

# 열거형 요소 {#enumeration--element}

![](../../../assets/v7-only.svg)

## 콘텐츠 모델 {#content-model-5}

열거형:==(도움말| 값)

## 속성 {#attributes-5}

* @basetype(문자열)
* @default(문자열)
* @desc(문자열)
* @label(문자열)
* @name(문자열)
* @template(문자열)

## 상위 {#parents-5}

`<srcschema>`

## 하위 {#children-5}

* `<help>`
* `<value>`

## 설명 {#description-5}

이 요소를 사용하면 값 열거형을 정의할 수 있습니다. 열거형은에 정의된 스키마에 속하지만 다른 스키마를 통해 액세스할 수 있습니다.

## 사용 및 사용 컨텍스트 {#use-and-context-of-use-4}

열거형은 기본 요소가 정의되기 전에 스키마의 시작 부분에서 정의됩니다.

## 속성 설명 {#attribute-description-5}

* **기본 유형(문자열)**: 열거형에 저장된 값의 유형입니다.

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

* **기본값(문자열)**: 기본값. 기본값은 열거에 정의된 값 중 하나일 수도 있습니다.
* **desc(문자열)**: 열거형 설명.
* **레이블(문자열)**: 열거형 레이블입니다.
* **이름(문자열)**: 열거형의 내부 이름입니다.
* **템플릿(문자열)**: 이 속성은 다음에 대한 참조를 정의합니다 `<enumeration>` 여러 스키마에서 공유하는 요소입니다. 이 정의는 현재 스키마에 자동으로 복사됩니다.

## 예제 {#examples-4}

데이터베이스에 값이 저장된 열거형 값의 예:

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
