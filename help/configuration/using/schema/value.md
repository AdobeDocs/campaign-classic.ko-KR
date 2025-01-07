---
product: campaign
title: 요소 및 속성 - 값 요소
description: 요소 및 속성
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 2%

---

# 값 요소 {#value--element}


## 콘텐츠 모델 {#content-model-16}

value:==help

## 속성 {#attributes-16}

* @applicableIf(문자열)
* @desc(문자열)
* @enabledIf(문자열)
* @img(문자열)
* @label(문자열)
* @name(문자열)
* @value(문자열)

## 상위 {#parents-16}

`<enumeration>`

## 하위 {#children-16}

`<help>`

## 설명 {#description-16}

이 요소를 사용하면 열거형에 저장된 값을 정의할 수 있습니다.

## 속성 설명 {#attribute-description-16}

* **적용할 수 있는 경우(문자열)**: 이 특성을 사용하면 열거형 값을 선택 사항으로 만들 수 있습니다. XTK 표현식을 받습니다.
* **desc(문자열)**: 열거형 값에 대한 설명입니다.
* **enabledIf (문자열)**: 열거형 값을 활성화하는 조건입니다.
* **img(문자열)**: &quot;namespace:image_name&quot; 양식의 열거형에 연결된 이미지입니다. 응용 프로그램 서버로 이미지를 가져와야 합니다.
* **label(문자열)**: 열거형 값의 레이블입니다.
* **이름(문자열)**: 열거형 값의 내부 이름입니다.
* **값(문자열)**: 열거형 값의 값입니다. 값의 형식은 열거형의 형식을 기반으로 정의됩니다. 열거형이 문자열 형식이면 문자열 형식 값만 포함할 수 있습니다.

## 예제 {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
