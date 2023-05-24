---
product: campaign
title: SOAP 메서드 구현
description: SOAP 메서드 구현
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 4%

---

# SOAP 메서드 구현{#implementing-soap-methods}



## 소개 {#introduction}

JavaScript에서는 SOAP 메서드를 만들 수 있습니다. 이 함수는 응용 프로그램 프로세스를 활성화하므로 양식에서 JSP 및 해당 호출을 방지할 수 있습니다.

이러한 SOAP 메서드는 애플리케이션에서 기본적으로 정의된 것과 동일한 방식으로 동작합니다. 정적, 키만 및 const 속성과 동일한 속성이 지원됩니다.

## 메서드 라이브러리 정의 {#defining-a-method-library}

메서드 라이브러리를 만들려면 다음 두 단계가 필요합니다.

* SOAP 메서드 선언,
* JavaScript의 정의(또는 구현)입니다.

### 선언 {#declaration}

먼저 스키마에서 메서드를 선언합니다. 스키마를 만들고 편집하는 방법에 대한 자세한 내용은 [이 섹션](../../configuration/using/about-schema-edition.md)).

이 선언은 기본 메서드의 선언과 유사하지만, 정의가 있는 메서드 라이브러리의 이름을 지정하는 &#39;library&#39; 특성을 추가해야 합니다.

이 이름은 &#39;JavaScript 코드&#39; 유형 엔터티의 이름(네임스페이스 포함)과 일치합니다.

예제:

testLog(msg) 메서드는 nms:recipient 확장에서 선언됩니다.

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>라이브러리에 사용되는 네임스페이스 및 이름은 선언이 있는 네임스페이스 및 스키마 이름과 독립적입니다.

### 정의 {#definition}

SOAP 메서드는 라이브러리를 나타내는 스크립트로 그룹화된 JavaScript 함수 형식으로 구현됩니다.

>[!NOTE]
>
>메서드 라이브러리는 여러 스키마에 대한 함수를 그룹화하거나 그 반대로 한 스키마의 함수를 별도의 라이브러리에서 정의할 수 있습니다.

스크립트에는 초기 라이브러리 로드 중에 실행할 코드가 포함될 수 있습니다.

**1. 이름**

함수 이름은 다음 형식을 준수해야 합니다.

```
 <schema-namespace>_<schema-name>_<method-name>
```

예제:

다음 JavaScript 함수는 위에 설명된 메서드의 구현입니다. &#39;cus:test&#39; 이름을 사용하여 &#39;JavaScript 코드&#39; 유형 엔터티에 정의되어야 합니다.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. 서명**

함수의 시그니처에는 선언의 각 &#39;in&#39; 또는 &#39;inout&#39; 매개 변수에 대한 인수가 포함되어야 합니다.

특정 사례:

* **비정적 메서드**: 함수는 &#39;xml&#39;(E4X) 유형 개체의 형태로 전달된 XML 엔티티와 일치하는 추가 인수를 먼저 포함해야 합니다.
* **&quot;key only&quot; 유형 메서드**: 함수는 문자열 형태로 전달된 키와 일치하면서 추가 인수를 먼저 포함해야 합니다.

**3. 반환된 값**

이 함수는 각 &#39;out&#39; 또는 &#39;inout&#39; 형식 매개 변수에 대한 값을 반환해야 합니다. 특정 사례: 메서드가 &#39;static&#39;, &#39;key only&#39; 또는 &#39;const&#39; 속성 없이 선언되는 경우 첫 번째 반환되는 값이 수정된 엔티티와 일치해야 합니다. 새 개체를 반환하거나 수정된 첫 번째 매개 변수를 반환할 수 있습니다.

예제:

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

여러 값을 반환할 때는 표에 표시해야 합니다.

예제:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```
