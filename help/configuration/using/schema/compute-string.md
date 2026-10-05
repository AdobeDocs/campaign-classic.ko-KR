---
product: campaign
title: 요소 및 속성 - 계산 문자열 요소
description: 계산 문자열 요소
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
TQID: 'https://experienceleague.adobe.com/vLSA9oDdBg-0sElc6QlusY-YviNyRU8Fq6yXRrFrN1g'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 5%
---
# 계산 문자열 요소 {#compute-string--element}


## 콘텐츠 모델 {#content-model-1}

compute-string:==EMPTY

## 속성 {#attributes-1}

@expr

## 상위 {#parents-1}

`<element>`

## 하위 {#children-1}

없음

## 설명 {#description-1}

`<compute-string>` 요소를 사용하면 XTK 식을 기반으로 문자열을 생성하여 여러 값을 기반으로 인터페이스에 &quot;빌드된&quot; 레이블을 표시할 수 있습니다.

## 사용 및 사용 컨텍스트 {#use-and-context-of-use-1}

`<compute-string>`이(가) 정의되지 않으면 기본적으로 스키마에 기본 키 값으로 `<compute-string>` 요소가 입력됩니다.

## 속성 설명 {#attribute-description-1}

* **expr(문자열)**: XTK 및/또는 Xpath 식

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
