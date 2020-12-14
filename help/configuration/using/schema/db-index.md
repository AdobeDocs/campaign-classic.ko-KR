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
source-wordcount: '338'
ht-degree: 2%

---


# dbindex 요소 {#dbindex--element}

## 컨텐트 모델 {#content-model-3}

dbindex:==keyfield

## 특성 {#attributes-3}

* @_operation (문자열)
* @applicableIf (문자열)
* @label (문자열)
* @name (MNTOKEN)
* @unique (boolean)

## 부모 {#parents-3}

`<element>`

## 하위 {#children-3}

`<keyfield>`

## 설명 {#description-3}

이 요소를 사용하면 테이블에 연결된 인덱스를 정의할 수 있습니다.

## 사용 및 사용 상황{#use-and-context-of-use-3}

여러 색인을 정의할 수 있습니다. 하나의 색인은 테이블의 필드를 하나 이상 참조할 수 있습니다. 일반적으로 인덱스 선언은 기본 스키마 요소의 정의를 따릅니다.

`<dbindex>`에 정의된 `<keyfield>` 요소의 순서는 매우 중요합니다. 첫 번째 `<keyfield>`은 쿼리가 주로 기반으로 하는 인덱스 기준이어야 합니다.

데이터베이스의 인덱스 이름은 테이블 이름과 인덱스 이름을 연결하여 계산됩니다. 예:인덱스 생성 쿼리 중 인덱스 필드의 테이블 이름 &quot;Sample&quot;, 네임스페이스 &quot;Cus&quot;, 인덱스 이름 &quot;MyIndex&quot;-> 이름:&quot;CusSample_myIndex&quot;.

## 특성 설명 {#attribute-description-3}

* **_operation(문자열)**:데이터베이스의 쓰기 유형을 정의합니다.

   이 속성은 기본적으로 기본 스키마를 확장할 때 사용됩니다.

   액세스 가능한 값은 다음과 같습니다.

   * &quot;없음&quot;:화해만. 즉, Adobe Campaign은 요소를 업데이트하지 않고 복구하거나 오류가 없는 경우 오류를 생성합니다.
   * &quot;insertOrUpdate&quot;:삽입으로 업데이트합니다. 즉, Adobe Campaign은 요소를 업데이트하거나 존재하지 않을 경우 요소를 만듭니다.
   * &quot;삽입&quot;:삽입. 즉, Adobe Campaign은 요소의 존재 여부를 확인하지 않고 요소를 삽입합니다.
   * &quot;업데이트&quot;:업데이트를 참조하십시오. 즉, Adobe Campaign은 요소를 업데이트하거나 존재하지 않을 경우 오류를 생성합니다.
   * &quot;삭제&quot;:삭제할 수 있습니다. 즉, Adobe Campaign은 요소를 복구 및 삭제합니다.

* **applicableIf (string)**:인덱스를 고려하기 위한 조건 - XTK 표현식을 받습니다.
* **label (string)**:색인 레이블.
* **이름(MNTOKEN)**:고유 색인 이름.
* **고유(부울)**:이 옵션이 활성화되면(@unique=&quot;true&quot;) 속성은 해당 필드 전체에서 색인의 고유성을 보장합니다.

## 예제 {#examples-3}

&quot;id&quot; 필드에 색인을 만듭니다. (데이터베이스(쿼리)에서 인덱스를 만들 때 `<dbindex>` 요소의 &quot;@unique&quot; 속성은 &quot;UNIQUE&quot; SQL 키 단어의 추가를 트리거합니다.)

```
<element label="Sample" name="Sample">
  <dbindex name="myIndex" label="My index on the ID field" unique="true" applicableIf="HasPackage('nms:social')">
      <keyfield xpath="@id"/>
  </dbindex>
    <attribute name="id" type="long"/>
</element>          
```

```
ALTER TABLE CusSample ADD iSampleId INTEGER;
UPDATE CusSample SET iSampleId = 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET Default 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET NOT NULL; 
CREATE UNIQUE INDEX CusSample_myIndex ON CusSample(iSampleId);
```

&quot;@mail&quot; 및 &quot;@phoneNumber&quot; 필드에 합성 인덱스 만들기:

```
<element label="NewSchemaUser" name="NewSchemaUser">
  <dbindex name="myIndex" label="My composite index">
         <keyfield xpath="@email"/>
         <keyfield xpath="@phone"/>
  </dbindex>
  
  <attribute name="email" type="string"/>
  <attribute name="phone" type="string"/>
</element>      
```

```
CREATE INDEX DocNewSchemaUser_myIndex ON DocNewSchemaUser(sEmail, sPhone);
```
