---
solution: Campaign Classic
product: campaign
title: 요소 및 속성
description: 요소 및 속성
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 9%

---


# `<compute-string>` 요소  {#compute-string--element}

## 콘텐츠 모델 {#content-model-1}

compute-string:==EMPTY

## 속성 {#attributes-1}

@exr

## 부모 {#parents-1}

`<element>`

## 하위 {#children-1}

없음

## 설명 {#description-1}

`<compute-string>` 요소를 사용하면 XTK 표현식을 기반으로 문자열을 생성하여 여러 값을 기반으로 인터페이스에 &quot;기본 제공&quot; 레이블을 표시할 수 있습니다.

## {#use-and-context-of-use-1} 사용 및 컨텍스트

`<compute-string>`이 정의되지 않은 경우 `<compute-string>` 요소는 스키마의 기본 키 값으로 기본적으로 입력됩니다.

## 특성 설명 {#attribute-description-1}

* **expr(문자열)**:XTK 및/또는 Xpath 표현식

## 예제 {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

수신자에 대해 계산된 문자열의 결과:&quot;John Doe (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
