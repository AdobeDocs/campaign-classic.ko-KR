---
product: campaign
title: 요소 및 속성 - 계산 문자열 요소
description: 계산 문자열 요소
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 5%

---

# 계산 문자열 요소 {#compute-string--element}

![](../../../assets/v7-only.svg)

## 콘텐츠 모델 {#content-model-1}

compute-string:==EMPTY

## 속성 {#attributes-1}

@expr

## 상위 {#parents-1}

`<element>`

## 하위 {#children-1}

없음

## 설명 {#description-1}

다음 `<compute-string>` 요소를 사용하면 XTK 표현식을 기반으로 문자열을 생성하여 여러 값을 기반으로 인터페이스에 &quot;빌드된&quot; 레이블을 표시할 수 있습니다.

## 사용 및 사용 컨텍스트 {#use-and-context-of-use-1}

없는 경우 `<compute-string>` 가 정의된 횟수, `<compute-string>` 요소는 기본적으로 스키마의 기본 키 값과 함께 입력됩니다.

## 속성 설명 {#attribute-description-1}

* **expr (문자열)**: XTK 및/또는 Xpath 식

## 예제 {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

수신자에 대해 계산된 문자열 결과: &quot;John Doe(john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
