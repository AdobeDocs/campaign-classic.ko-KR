---
product: campaign
title: 요소 및 속성
description: 요소 및 속성
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 8%

---

# 계산 문자열 요소 {#compute-string--element}

## 컨텐츠 모델 {#content-model-1}

계산 문자열:==EMPTY

## 속성 {#attributes-1}

@expr

## 부모 {#parents-1}

`<element>`

## 하위 {#children-1}

없음

## 설명 {#description-1}

`<compute-string>` 요소를 사용하면 XTK 표현식을 기반으로 문자열을 생성하여 여러 값을 기반으로 인터페이스에 &quot;built&quot; 레이블을 표시할 수 있습니다.

## 사용 컨텍스트 {#use-and-context-of-use-1} 사용

`<compute-string>` 이 정의되지 않으면 기본적으로 `<compute-string>` 요소가 스키마에 있는 기본 키 값으로 입력됩니다.

## 특성 설명 {#attribute-description-1}

* **expr(문자열)**:XTK 및/또는 Xpath 표현식

## 예제 {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

수신자에 대해 계산된 문자열 결과:&quot;John Doe (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
