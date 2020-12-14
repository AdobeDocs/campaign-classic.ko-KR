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
source-wordcount: '205'
ht-degree: 3%

---


# 메서드 요소 {#method--element}

## 컨텐트 모델 {#content-model-10}

메서드:==( help | 매개 변수)

## 특성 {#attributes-10}

* @_operation (문자열)
* @access (문자열)
* @const (boolean)
* @hidden (boolean)
* @label (문자열)
* @library (문자열)
* @name (MNTOKEN)
* @pkonly (boolean)
* @static (boolean)

## 부모 {#parents-10}

`<methods>`  ,  `<interface />`

## 하위 {#children-10}

* `<help>`
* `<parameters>`

## 설명 {#description-10}

이 요소를 사용하면 SOAP 메서드를 정의할 수 있습니다.

## 사용 및 사용 상황{#use-and-context-of-use-7}

SOAP 메서드를 사용하면 응용 프로그램 프로세스를 사용할 수 있습니다.

&quot;@library&quot;은 새 메서드(기본적으로 제공되지 않음)를 선언하는 데 필요합니다.네임스페이스와 라이브러리에 사용되는 이름은 선언이 있는 스키마의 이름 및 네임스페이스와 독립적입니다.

## 특성 설명 {#attribute-description-10}

* **액세스(문자열)**:이 속성은 메서드 사용에 대한 액세스 제어를 정의합니다. 이 속성이 없으면 식별은 필수입니다. 사용 가능한 값은 다음과 같습니다.&#39;anonymous&#39;, &#39;admin&#39; 및 &#39;sql&#39;.
* **const (boolean)**:이 속성이 활성화되면 선언된 메서드에서 엔티티가
* **label (string)**:메서드의 레이블입니다.
* **라이브러리(문자열)**:이 메서드는 응용 프로그램이 고유하지 않습니다. 이 속성은 메서드 정의가 있는 메서드 라이브러리 값을 사용합니다(nms:mylibrary.js).
* **이름(MNTOKEN)**:고유한 메서드 이름.
* **정적(부울)**:이 속성을 활성화하면 이 메서드는 자치적인 것으로 간주되므로 호출될 때 메서드에 모든 매개 변수를 지정해야 합니다.

## 예제 {#examples-7}

&quot;구독&quot;의 정의:

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
