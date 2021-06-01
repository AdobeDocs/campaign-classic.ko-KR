---
product: campaign
title: 요소 및 속성
description: 요소 및 속성
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 1%

---

# srcschema 요소 {#srcschema--element}

## 컨텐츠 모델 {#content-model-14}

srcSchema:==(attribute | createdBy | 데이터 | 요소 | 열거형 | 도움말 | 인터페이스 | 메서드 | modifiedBy)

## 속성 {#attributes-14}

created (datetime), createdBy-id(long), desc(string), entitySchema(string), extendedSchema(string), img(문자열), implement(string), label(string), labelSingular(string), lastModified(datetime), library(boolean), mappingType(string), modifiedBy-id(long), name(string), namespace(string), useRecycleBin(boolean), view(boolean), xtkschema(string))

## 부모 {#parents-14}

없음

## 하위 {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

## 설명 {#description-14}

`<srcschema>`은 스키마의 루트 요소입니다. 스키마 정의에 대한 입력 지점입니다.

## 사용 컨텍스트 {#use-and-context-of-use-9} 사용

스키마 프레젠테이션은 [스키마 참조 정보](../../../configuration/using/about-schema-reference.md) 및 [스키마 구조](../../../configuration/using/schema-structure.md)에서 사용할 수 있습니다.

## 특성 설명 {#attribute-description-14}

* **만든 날짜(datetime)**:이 속성은 스키마 생성 날짜 및 시간에 대한 정보를 제공합니다. 날짜 시간 양식이 있습니다. 표시되는 값은 서버에서 가져옵니다. 시간은 UTC 형식으로 표시됩니다.
* **createdBy-id(긴)**:는 스키마를 만든 연산자의 식별자입니다.
* **desc(문자열)**:스키마 설명
* **entitySchema(문자열)**:구문 및 승인을 기반으로 하는 기본 스키마(기본적으로 Adobe Campaign의 경우):xtk:srcSchema). 현재 스키마를 저장하면 Adobe Campaign이 @xtkschema 특성에 선언된 스키마로 문법을 승인합니다.
* **extendedSchema(문자열)**:는 현재 스키마 확장이 기반으로 하는 기본 스키마 이름을 받습니다. 양식은 &quot;namespace:name&quot;입니다.
* **img(문자열)**:스키마에 연결된 아이콘(스키마 만들기 마법사에서 정의할 수 있음).
* **레이블(문자열)**:스키마 레이블입니다.
* **labelSingular(문자열)**:인터페이스에 표시할 레이블(단일).
* **lastModified(datetime)**:이 속성은 마지막 수정 날짜 및 시간에 대한 정보를 제공합니다. 날짜 시간 양식이 있습니다. 표시되는 값은 서버에서 가져옵니다. 시간은 UTC 형식으로 표시됩니다.
* **라이브러리(부울)**:스키마가 엔티티가 아니라 라이브러리로 사용됩니다. 따라서 &quot;@ref&quot; 및 &quot;@template&quot; 특성 덕분에 다른 스키마에서 이 스키마를 참조할 수 있습니다.
* **mappingType(문자열)**:

   * &quot;sql&quot;:데이터베이스 매핑
   * &quot;textFile&quot;:텍스트 파일 매핑
   * &quot;xmlFile&quot;:XML 형식 텍스트 파일 매핑
   * &quot;binaryFile&quot;:이진 파일 매핑

* **modifiedBy-id(긴)**:스키마를 변경한 연산자의 식별자와 일치합니다.
* **name(문자열)**:고유한 스키마 이름입니다.
* **namespace(문자열)**:스키마의 네임스페이스(기본값:nms, xtk, nl). 프로젝트에 대한 새 스키마를 만들 때는 전용 네임스페이스를 사용하는 것이 좋습니다.
* **useRecycleBin(부울)**:애플리케이션에서 휴지통 기능을 활성화합니다. 삭제된 레코드는 최종 삭제 전에 휴지통으로 배치됩니다. 이 함수는 &quot;배달&quot; 모드에서만 사용할 수 있습니다.
* **보기(부울)**:활성화되면(@view=&quot;true&quot;) 스키마가 보기로 사용됩니다. 데이터베이스 구조 업데이트 마법사는 스키마를 고려하지 않습니다. 이 옵션은 주로 외부 테이블을 참조하는 데 사용됩니다.
* **xtschema(문자열)**:스키마 문법을 정의하는 스키마의 이름입니다(기본적으로 xtk:srcSchema).

## 예제 {#examples-11}

`<srcschema>` 기본 제공 스키마 &quot;nms:delivery&quot; 요소

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
