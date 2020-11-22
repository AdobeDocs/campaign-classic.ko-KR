---
solution: Campaign Classic
product: campaign
title: SOAP 메서드 구현
description: SOAP 메서드 구현
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 4%

---


# SOAP 메서드 구현{#implementing-soap-methods}

## 소개 {#introduction}

JavaScript에서 SOAP 메서드를 만들 수 있습니다. 이 기능은 응용 프로그램 프로세스를 단순화하므로 JSP와 양식의 호출을 개발할 수 없습니다.

이러한 SOAP 메서드는 응용 프로그램에서 기본적으로 정의된 메서드와 같은 방식으로 작동합니다. 동일한 속성이 지원됩니다.정적, 키 전용 및 const.

## 메서드 라이브러리 정의 {#defining-a-method-library}

메서드 라이브러리를 만드는 과정에는 두 가지 단계가 포함됩니다.

* SOAP 메서드 선언,
* JavaScript의 정의(또는 구현)입니다.

### 선언 {#declaration}

스키마를 사용하여 메서드를 선언합니다(스키마를 만들고 편집하는 방법에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../configuration/using/about-schema-edition.md)).

이 선언이 기본 메서드와 비슷하지만 정의가 있는 메서드 라이브러리의 이름을 지정하는 &#39;library&#39; 특성을 추가해야 합니다.

이 이름은 &#39;JavaScript 코드&#39; 형식 엔티티의 이름(네임스페이스와 일치)과 일치합니다.

예제:

testLog(msg) 메서드는 nms:recipient 확장명으로 선언됩니다.

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>네임스페이스와 라이브러리에 사용되는 이름은 선언이 있는 네임스페이스 및 스키마 이름과 독립적입니다.

### 정의 {#definition}

SOAP 메서드는 라이브러리를 나타내는 스크립트로 그룹화된 JavaScript 함수 형태로 구현됩니다.

>[!NOTE]
>
>메서드 라이브러리는 다양한 스키마에 대한 함수를 그룹화하거나 그 반대의 경우 하나의 스키마의 함수를 별도의 라이브러리에서 정의할 수 있습니다.

스크립트에는 초기 라이브러리를 로드하는 동안 실행할 코드가 포함될 수 있습니다.

**1. 이름**

함수의 이름은 다음 형식을 따라야 합니다.

```
 <schema-namespace>_<schema-name>_<method-name>
```

예제:

다음 JavaScript 함수는 위에서 설명한 방법을 구현한 것입니다. &#39;cus:test&#39; 이름을 사용하여 &#39;JavaScript 코드&#39; 유형 엔티티에서 정의됩니다.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. 서명**

함수의 서명에 선언의 각 &#39;in&#39; 또는 &#39;inout&#39; 매개 변수에 대한 인수가 포함되어야 합니다.

특정 사례:

* **비정적 메서드**:함수에는 &#39;xml&#39;(E4X) 형식 개체의 형태로 전달된 XML 엔티티와 함께 사용할 때 먼저 추가 인수가 포함되어야 합니다.
* **&quot;key only&quot; 유형 메서드**:함수는 먼저 문자 문자열 형태로 전달된 키와 함께 추가 인수를 포함해야 합니다.

**3. 반환된 값**

함수는 각 &#39;out&#39; 또는 &#39;inout&#39; 형식 매개 변수에 대한 값을 반환해야 합니다. 특정 사례:&#39;static&#39;, &#39;key only&#39; 또는 &#39;const&#39; 특성 없이 메서드가 선언된 경우, 처음 반환된 값은 수정된 엔터티와 일치해야 합니다. 새 개체를 반환하거나 첫 번째 수정된 매개 변수를 반환할 수 있습니다.

예제:

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

여러 값을 반환해야 할 경우 테이블에 표시되어야 합니다.

예제:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```

