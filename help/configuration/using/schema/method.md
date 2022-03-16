---
product: campaign
title: 스키마 요소 및 속성 - 메서드 요소
description: 메서드 요소
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# 메서드 요소 {#method--element}

![](../../../assets/v7-only.svg)

## 컨텐츠 모델 {#content-model-10}

메서드:==( 도움말 | 매개 변수)

## 속성 {#attributes-10}

* @_operation (string)
* @access (string)
* @const (부울)
* @hidden (부울)
* @label (string)
* @library (string)
* @name (MNTOKEN)
* @pkonly (부울)
* @static (부울)

## 부모 {#parents-10}

`<methods>`  ,  `<interface />`

## 하위 {#children-10}

* `<help>`
* `<parameters>`

## 설명 {#description-10}

이 요소를 사용하면 SOAP 메서드를 정의할 수 있습니다.

## 사용 및 사용 컨텍스트 {#use-and-context-of-use-7}

SOAP 메서드를 사용하면 응용 프로그램 프로세스를 사용할 수 있습니다.

@library은 새 메서드(비기본)를 선언하는 데 필요합니다. 네임스페이스와 라이브러리에 사용되는 이름은 선언이 있는 스키마의 네임스페이스 및 이름과 독립적입니다.

## 속성 설명 {#attribute-description-10}

* **access (string)**: 이 속성은 메서드 사용에 대한 액세스 제어를 정의합니다. 이 속성이 없으면 식별이 필수입니다. 사용 가능한 값은 다음과 같습니다. &#39;anonymous&#39;, &#39;admin&#39; 및 &#39;sql&#39;.
* **const(부울)**: 활성화된 경우 이 속성은 선언된 메서드가 엔터티를 변경함을 의미합니다
* **레이블(문자열)**: 메서드의 레이블입니다.
* **라이브러리(문자열)**: 이 메서드는 응용 프로그램이 고유하지 않습니다. 이 속성은 메서드 정의가 있는 메서드 라이브러리 값을 가져옵니다(nms:mylibrary.js).
* **name(MNTOKEN)**: 고유한 메서드 이름입니다.
* **정적(부울)**: 이 속성을 활성화하면 메서드가 자치적으로 간주되며, 메서드가 호출될 때 모든 매개 변수를 메서드에 지정해야 합니다.

## 예제 {#examples-7}

기본 제공 &quot;Subscribe&quot;에 대한 정의:

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```
