---
product: campaign
title: 스키마 요소 및 속성 - 메서드 요소
description: 메서드 요소
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 1%

---

# 메서드 요소 {#method--element}

![](../../../assets/v7-only.svg)

## 콘텐츠 모델 {#content-model-10}

method:==( help | 매개 변수)

## 속성 {#attributes-10}

* @_operation(문자열)
* @access(문자열)
* @const(부울)
* @hidden(부울)
* @label(문자열)
* @library(문자열)
* @name(MNTOKEN)
* @pkonly(부울)
* @static(부울)

## 상위 {#parents-10}

`<methods>`  ,  `<interface />`

## 하위 {#children-10}

* `<help>`
* `<parameters>`

## 설명 {#description-10}

이 요소를 사용하여 SOAP 메서드를 정의할 수 있습니다.

## 사용 및 사용 컨텍스트 {#use-and-context-of-use-7}

SOAP 메서드는 응용 프로그램 프로세스를 사용합니다.

&quot;@library&quot;는 새 메서드(비기본)를 선언하는 데 필요합니다. 라이브러리에 사용되는 네임스페이스 및 이름은 선언이 있는 스키마의 네임스페이스 및 이름과 독립적입니다.

## 속성 설명 {#attribute-description-10}

* **액세스(문자열)**: 이 속성은 메서드를 사용하기 위한 액세스 제어를 정의합니다. 이 속성이 누락된 경우 식별은 필수입니다. 사용 가능한 값은 &#39;anonymous&#39;, &#39;admin&#39; 및 &#39;sql&#39;입니다.
* **const(부울)**: 활성화된 경우 이 속성은 선언된 메서드가 엔티티를 변경함을 의미합니다
* **레이블(문자열)**: 메서드의 레이블입니다.
* **라이브러리(문자열)**: 이 메서드는 애플리케이션에서 고유하지 않습니다. 이 속성은 메서드 정의가 있는 메서드 라이브러리의 값을 가져옵니다(nms:mylibrary.js).
* **이름(MNTOKEN)**: 고유한 메서드 이름입니다.
* **정적(부울)**: 이 특성이 활성화되어 있으면 메서드가 자율적으로 간주됩니다. 호출될 때 모든 매개 변수를 메서드에 지정해야 합니다.

## 예제 {#examples-7}

즉시 사용 가능한 &quot;구독&quot; 메서드에 대한 정의:

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
