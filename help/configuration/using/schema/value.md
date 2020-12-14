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
source-wordcount: '147'
ht-degree: 5%

---


# 값 요소 {#value--element}

## 컨텐트 모델 {#content-model-16}

value:==help

## 특성 {#attributes-16}

* @applicableIf (문자열)
* @desc (문자열)
* @enabledIf (문자열)
* @img (문자열)
* @label (문자열)
* @name (문자열)
* @value (문자열)

## 부모 {#parents-16}

`<enumeration>`

## 하위 {#children-16}

`<help>`

## 설명 {#description-16}

이 요소를 사용하면 열거형에 저장된 값을 정의할 수 있습니다.

## 특성 설명 {#attribute-description-16}

* **applicableIf (string)**:이 속성을 사용하면 열거형 값을 선택 사항으로 만들 수 있습니다. XTK 표현식을 수신합니다.
* **desc(문자열)**:열거형 값에 대한 설명입니다.
* **enabledIf (string)**:열거형 값 활성화에 대한 조건입니다.
* **img (string)**:&quot;namespace:image_name&quot; 양식의 열거에 연결된 이미지입니다. 이미지를 응용 프로그램 서버로 가져와야 합니다.
* **label (string)**:열거형 값의 레이블입니다.
* **이름(문자열)**:열거형 값의 내부 이름입니다.
* **값(문자열)**:열거형 값의 값입니다. 값의 유형은 열거형 유형에 따라 정의됩니다. 열거가 문자 문자열 유형인 경우 문자 문자열 유형 값만 포함할 수 있습니다.

## 예제 {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
