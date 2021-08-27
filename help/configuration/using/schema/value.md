---
product: campaign
title: 요소 및 속성
description: 요소 및 속성
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 5%

---

# 값 요소 {#value--element}

![](../../../assets/v7-only.svg)

## 컨텐츠 모델 {#content-model-16}

값:==도움말

## 속성 {#attributes-16}

* @applicableIf (string)
* @desc (string)
* @enabledIf (string)
* @img (string)
* @label (string)
* @name (string)
* @value (string)

## 부모 {#parents-16}

`<enumeration>`

## 하위 {#children-16}

`<help>`

## 설명 {#description-16}

이 요소를 사용하면 열거형에 저장된 값을 정의할 수 있습니다.

## 속성 설명 {#attribute-description-16}

* **적용 가능한 경우(문자열)**: 이 속성을 사용하면 열거형 값을 선택 사항으로 만들 수 있습니다. XTK 표현식을 수신합니다.
* **desc(문자열)**: 열거형 값에 대한 설명입니다.
* **enabledIf (문자열)**: 열거형 값을 활성화하기 위한 조건입니다.
* **img(문자열)**: &quot;namespace:image_name&quot; 양식의 열거형에 연결된 이미지입니다. 이미지를 애플리케이션 서버로 가져와야 합니다.
* **레이블(문자열)**: 열거형 값의 레이블입니다.
* **name(문자열)**: 열거형 값의 내부 이름입니다.
* **값(문자열)**: 열거형 값의 값입니다. 값의 유형은 열거형의 유형에 따라 정의됩니다. 열거형이 문자열 유형인 경우 문자열 유형 값만 포함할 수 있습니다.

## 예제 {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
