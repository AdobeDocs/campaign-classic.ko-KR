---
product: campaign
title: 요소 및 속성
description: dbindex 요소
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 1%

---

# dbindex 요소 {#dbindex--element}

![](../../../assets/v7-only.svg)

## 컨텐츠 모델 {#content-model-3}

dbindex:==keyfield

## 속성 {#attributes-3}

* @_operation (string)
* @applicableIf (string)
* @label (string)
* @name (MNTOKEN)
* @unique (부울)

## 부모 {#parents-3}

`<element>`

## 하위 {#children-3}

`<keyfield>`

## 설명 {#description-3}

이 요소를 사용하면 테이블에 연결된 인덱스를 정의할 수 있습니다.

## 사용 및 사용 컨텍스트 {#use-and-context-of-use-3}

여러 인덱스를 정의할 수 있습니다. 하나의 색인이 테이블의 필드를 하나 이상 참조할 수 있습니다. 인덱스 선언은 일반적으로 기본 스키마 요소의 정의를 따릅니다.

주문 `<keyfield>` 에 정의된 요소 `<dbindex>` 는 매우 중요합니다. 첫 번째 `<keyfield>` 은 주로 쿼리를 기반으로 하는 인덱싱 기준이어야 합니다.

데이터베이스의 인덱스 이름은 테이블의 이름과 인덱스 이름을 연결하여 계산됩니다. 예: 인덱스를 만드는 동안 인덱스 필드의 테이블 이름 &quot;Sample&quot;, 네임스페이스 &quot;Cus&quot;, 인덱스 이름 &quot;MyIndex&quot;-> 이름: &quot;CusSample_myIndex&quot;.

## 속성 설명 {#attribute-description-3}

* **_operation(문자열)**: 데이터베이스의 쓰기 유형을 정의합니다.

   이 속성은 주로 기본 스키마를 확장할 때 사용됩니다.

   액세스 가능한 값은 다음과 같습니다.

   * &quot;none&quot;: 화해만. 즉, Adobe Campaign은 요소를 업데이트하지 않고 요소를 복구하거나 존재하지 않을 경우 오류를 생성합니다.
   * &quot;insertOrUpdate&quot;: 삽입으로 업데이트합니다. 즉, Adobe Campaign은 요소가 없으면 요소를 업데이트하거나 만듭니다.
   * &quot;insert&quot;: 삽입 광고. 즉, Adobe Campaign이 요소 존재 여부를 확인하지 않고 요소를 삽입합니다.
   * &quot;update&quot;: 업데이트합니다. 즉, Adobe Campaign이 요소를 업데이트하거나 요소가 없는 경우 오류를 생성합니다.
   * &quot;delete&quot;: 삭제 즉, Adobe Campaign이 요소를 복구 및 삭제합니다.

* **적용 가능한 경우(문자열)**: 색인을 고려하기 위한 조건 - XTK 표현식을 수신합니다.
* **레이블(문자열)**: 인덱스 레이블입니다.
* **name(MNTOKEN)**: 고유 인덱스 이름입니다.
* **고유(부울)**: 이 옵션이 활성화되면(@unique=&quot;true&quot;) 속성이 해당 필드 전체에서 인덱스의 고유성을 보장합니다.

## 예제 {#examples-3}

&quot;id&quot; 필드에 인덱스를 만듭니다. (@unique&quot; 속성 `<dbindex>` 요소는 데이터베이스(쿼리)에서 인덱스를 만들 때 &quot;UNIQUE&quot; SQL 키 단어의 추가를 트리거합니다.

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

&quot;@mail&quot; 및 &quot;@phoneNumber&quot; 필드에 복합 인덱스 생성:

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
