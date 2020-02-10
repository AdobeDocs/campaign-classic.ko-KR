---
title: 요소 및 속성
seo-title: 요소 및 속성
description: 요소 및 속성
seo-description: null
page-status-flag: never-activated
uuid: 72b0128a-a453-4646-93e5-b399914abb76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5e24d94a-f9c1-4642-a881-dfc4b5492f14
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f9b3508fee3b441752648258b1bc9d5d2b919791

---


# 요소 및 속성 {#elements-and-attributes}

스키마를 편집할 때 소스 스키마(xtk:srcSchema)를 기반으로 하는 승인 시스템을 사용할 수 있습니다. &quot;데이터베이스 구조 업데이트...&quot;를 사용하여 데이터베이스를 업데이트할 때 일부 오류가 발견될 수도 있습니다. 마법사로

기본적으로 Adobe Campaign 스키마에서 모든 부울 유형 속성은 &quot;false&quot;입니다. 활성화하려면 스키마에서 속성을 지정하고 값을 &quot;true&quot;로 설정해야 합니다.

## `<attribute>` 요소 {#attribute--element}

### 콘텐츠 모델 {#content-model}

attribute:==help

### 속성 {#attributes}

_operation (string), advanced (boolean), applicableIf (string), autoIncrement (boolean), consistentTo (string), dbEnum (string), defOnDuplicate (boolean), default (string), edit (string), exr (string), feature (string), featureDate (boolean)) , img (문자열), inout (문자열), 레이블(문자열), 길이(문자열), 현지화 가능(부울), 이름(MNTOKEN), notNull(부울), pkgStatus(문자열), 참조(문자열), 필수(부울), sqlDefault(문자열), sqlname(문자열), sqltable(문자열), 대상(MNTOKEN), 템플릿 ), translatedDefault (string), translatedExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (boolean)

### 부모 {#parents}

`<element>`

### 어린이 {#children}

`<help>`

### 설명 {#description}

`<attribute>` 요소를 사용하면 데이터베이스에 필드를 정의할 수 있습니다.

### 사용 및 사용 컨텍스트 {#use-and-context-of-use}

`<attribute>` 요소는 `<element>` 요소에서 선언되어야 합니다.

요소에 정의된 `<attribute>` 요소가 데이터베이스의 필드 생성 시퀀스에는 `<srcschema>` 영향을 주지 않습니다. 제작 시퀀스는 알파벳 순으로 표시됩니다.

### 속성 설명 {#attribute-description}

* **_operation(문자열)**:데이터베이스에 쓰는 유형을 정의합니다.

   이 속성은 기본적으로 기본 스키마를 확장할 때 사용됩니다.

   액세스 가능한 값은 다음과 같습니다.

   * &quot;none&quot;:화해만. 즉, Adobe Campaign이 요소를 업데이트하지 않고 복구하거나 오류가 없는 경우 오류가 생성됩니다.
   * &quot;insertOrUpdate&quot;:업데이트를 삽입하여 사용할 수 있습니다. 즉, Adobe Campaign은 요소를 업데이트하거나 요소가 없을 경우 만듭니다.
   * &quot;삽입&quot;:삽입. 즉, Adobe Campaign은 요소의 존재 여부를 확인하지 않고 요소를 삽입합니다.
   * &quot;업데이트&quot;:업데이트. 즉, Adobe Campaign이 요소를 업데이트하거나 요소가 없을 경우 오류를 생성합니다.
   * &quot;삭제&quot;:삭제. 즉, Adobe Campaign이 요소를 복구 및 삭제합니다.

* **고급(부울)**:이 옵션이 활성화되면(@advanced=&quot;true&quot;) 양식에서 목록을 구성하기 위해 액세스할 수 있는 사용 가능한 필드 목록에서 속성을 숨길 수 있습니다.
* **applableIf (string)**:이 속성을 사용하면 필드를 선택 사항으로 만들 수 있습니다. 제약 조건을 준수하면 데이터베이스를 업데이트할 때 `<attribute>` 요소가 고려됩니다. &quot;applableIf&quot;는 XTK 표현식을 받습니다.
* **autoIncrement(부울)**:이 옵션을 활성화하면 필드가 카운터가 됩니다. 이를 통해 값(대부분 ID)을 늘릴 수 있습니다. (외부 사용)
* **containsTo(문자열)**:필드를 공유하는 테이블의 이름과 네임스페이스를 가져와서 속성이 선언되는 스키마를 채웁니다. (a에서만 사용됨). `<schema>`
* **dataPolicy(문자열)**:sql 또는 XML 필드에 허용되는 값에 대한 승인 제한을 지정할 수 있습니다. 이 속성의 값은 다음과 같습니다.

   * &quot;none&quot;:값 없음
   * &quot;smartCase&quot;:첫 글자 대문자
   * &quot;lowerCase&quot;:소문자
   * &quot;대문자&quot;:모든 대문자
   * &quot;이메일&quot;:이메일 주소
   * &quot;phone&quot;:전화 번호
   * &quot;identifier&quot;:식별자 이름
   * &quot;resIdentifier&quot;:파일 이름

* **dbEnum(문자열)**:는 &quot;닫힘&quot; 열거형의 내부 이름을 받습니다. 열거형 값은 에서 정의해야 합니다 `<srcschema>`.
* **defOnDuplicate(부울)**:이 속성을 활성화하면 레코드가 복제되면(@default에 정의됨) 기본값이 자동으로 레코드에 다시 적용됩니다.
* **기본값(문자열)**:기본 필드의 값을 정의할 수 있습니다(함수 호출, 기본값). 이 속성은 XTK 표현식을 받습니다.
* **desc (string)**:속성 설명을 삽입할 수 있습니다. 이 설명은 인터페이스의 상태 표시줄에 표시됩니다.
* **edit (string)**:이 속성은 스키마에 연결된 양식에서 사용할 입력 유형을 지정합니다.
* **enum(문자열)**:는 필드에 연결된 열거형의 이름을 받습니다. 열거를 동일한 스키마나 원격 스키마에 삽입할 수 있습니다.
* **expr(문자열)**:필드 사전 계산 표현식을 정의합니다. 이 속성은 Xpath 또는 XTK 표현식을 받습니다.
* **feature (string)**:특성 필드를 정의합니다.이러한 필드는 기존 테이블의 데이터를 확장하지만 부록 테이블의 저장과 함께 사용됩니다. 허용된 값은 다음과 같습니다.

   * &quot;공유&quot;:컨텐츠는 데이터 유형별로 공유 테이블에 저장됩니다
   * &quot;전용&quot;:컨텐츠는 전용 테이블에 저장됩니다.
   SQL 특성 테이블은 특성 유형에 따라 자동으로 만들어집니다.

   * 전용: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 공유: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`
   두 가지 유형의 특성 필드가 있습니다.하나의 값이 특성에 대해 인증되는 간단한 초점 필드와 여러 값이 포함될 수 있는 컬렉션 요소와 연결된 다중 선택 필드 중 하나를 선택합니다.

   스키마에서 특성이 정의되면 이 스키마에는 단일 필드를 기반으로 하는 기본 키가 있어야 합니다(복합 키는 인증되지 않음).

* **featureDate(부울)**:특성 &quot;@feature&quot; 특성 필드에 연결되어 있습니다. 값이 &quot;true&quot;이면 값이 마지막으로 업데이트된 시기를 알 수 있습니다.
* **img(문자열)**:필드에 연결된 이미지의 경로를 정의할 수 있습니다(네임스페이스 + 이미지 이름)(예:img=&quot;cus:mypicture.jpg&quot;). 실제로 이미지를 애플리케이션 서버로 가져와야 합니다.
* **label(문자열)**:레이블은 필드에 연결되어 있으며, 대부분 인터페이스에서 사용자에게 지정됩니다. 이를 통해 이름 지정 제한을 피할 수 있습니다.
* **length(문자열)**:max. &quot;string&quot; 유형의 SQL 필드에 대한 문자 수입니다. &quot;@length&quot; 속성을 지정하지 않으면 Adobe Campaign은 255자 필드를 자동으로 만듭니다.
* **지역화 가능(부울)**:활성화되면 이 속성은 번역(내부 사용)에 대한 &quot;@label&quot; 속성의 값을 복구하도록 컬렉션 도구에 지시합니다.
* **이름(MNTOKEN)**:테이블의 필드 이름과 일치하는 속성의 이름입니다. &quot;@name&quot; 속성의 값은 짧아야 하며, 특히 영어로 되어 있어야 하며, XML 이름 지정 제한을 준수해야 합니다.

   스키마가 데이터베이스에 작성되면 접두사는 Adobe Campaign에 의해 필드 이름에 자동으로 추가됩니다.

   * &quot;i&quot;:접두사를 사용합니다.
   * &quot;d&quot;:접두사를 사용합니다.
   * &quot;s&quot;:접두사를 사용합니다.
   * &quot;ts&quot;:접두사를 사용합니다.
   테이블에서 필드의 이름을 완전히 정의하려면 속성을 정의할 때 &quot;@sqlname&quot; 옵션을 사용합니다.

* **notNull(부울)**:데이터베이스의 NULL 레코드 관리와 관련된 Adobe Campaign의 동작을 재정의할 수 있습니다. 기본적으로 숫자 필드는 null이 아니며 문자열 및 날짜 유형 필드는 null일 수 있습니다.
* **pkgStatus(문자열)**:패키지 내보내기 동안 값은 &quot;@pkgStatus&quot;의 값에 따라 고려됩니다.

   * &quot;always&quot;:항상 표시
   * &quot;never&quot;:존재하지 않음
   * &quot;default (or nothing)&quot;:값이 기본값이거나 다른 인스턴스와 호환되지 않는 내부 필드가 아닌 경우를 제외하고 값이 내보내집니다.

* **ref(문자열)**:이 속성은 여러 스키마가 공유하는 `<attribute>` 요소에 대한 참조를 정의합니다(정의 팩토링). 정의가 현재 스키마로 복사되지 않습니다.
* **필수(부울)**:이 속성이 활성화되면(@required=&quot;true&quot;) 필드가 인터페이스에서 강조 표시됩니다. 필드의 레이블은 양식에 빨간색으로 표시됩니다.
* **sql(부울)**:이 특성이 활성화된 경우(@sql=&quot;true&quot;) 특성이 포함된 요소에 xml=&quot;true&quot; 속성이 있는 경우에도 SQL 속성의 저장소를 강제로 수행합니다.
* **sqlDefault(문자열)**:이 속성을 사용하면 @notNull 특성이 활성화된 경우 데이터베이스를 업데이트하는 데 고려되는 기본값을 정의할 수 있습니다. 속성 생성 후 이 속성을 추가하면 새 레코드에 대해서도 스키마 동작이 변경되지 않습니다. 스키마를 변경하고 새 레코드에 대한 값을 업데이트하려면 속성을 삭제하고 다시 만들어야 합니다.
* **sqlname(문자열)**:을 클릭합니다. @sqlname이 지정되지 않은 경우 기본적으로 &quot;@name&quot; 속성의 값이 사용됩니다. 데이터베이스에 스키마를 작성할 때 필드의 유형에 따라 접두사가 자동으로 추가됩니다.
* **템플릿(문자열)**:이 속성은 여러 스키마로 공유된 `<attribute>` 요소에 대한 참조를 정의합니다. 정의가 현재 스키마에 자동으로 복사됩니다.
* **translatedDefault(문자열)**:&quot;@default&quot; 속성이 있으면 &quot;@translatedDefault&quot;를 사용하여 번역 도구(내부 사용)로 수집하기 위해 @default에 정의된 표현식과 일치하도록 표현식을 재정의할 수 있습니다.
* **translatedExpr(문자열)**:&quot;@expr&quot; 특성이 있는 경우 &quot;@translatedExpr&quot; 속성을 사용하면 번역 도구(내부 사용)에 의해 수집될 @expr에 정의된 표현식과 일치하도록 표현식을 재정의할 수 있습니다.
* **유형(MNTOKEN)**:필드 유형.

   필드 유형은 일반적입니다. 설치된 데이터베이스 유형에 따라 Adobe Campaign은 정의된 유형을 구조 업데이트 동안 설치된 데이터베이스 특정 값으로 변경합니다.

   사용 가능한 유형 목록:

   * 임의
   * bin
   * blob
   * boolean
   * byte
   * CDATA
   * datetime
   * datetimez
   * datetimenotz
   * date
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * 메모
   * MNTOKEN
   * 퍼센트
   * 기본 키
   * short
   * 문자열
   * time
   * 시간 대응
   * uuid
   &quot;@type&quot; 속성이 비어 있는 경우 Adobe Campaign은 길이가 100인 문자열(STRING)을 필드에 기본적으로 연결합니다.

   필드가 STRING 유형이고 필드 이름이 &quot;@sqlname&quot; 특성이 있는 경우 데이터베이스의 필드 이름 앞에 &#39;s&#39;가 자동으로 표시됩니다. 이 운영 모드는 INTEGER(i), DOUBLE(d) 및 DATES(ts) 유형 필드와 유사합니다.

* **userEnum(문자열)**:는 &quot;open&quot; 열거형의 내부 이름을 받습니다. 열거형의 값은 인터페이스에서 사용자가 정의할 수 있습니다.
* **visibleIf(문자열)**:xtk 표현식 형식으로 조건을 정의하여 속성을 표시하거나 숨깁니다.

   >[!CAUTION]
   >
   >이 속성은 숨겨지지만 해당 데이터에 여전히 액세스할 수 있습니다.

* **xml(부울)**:이 옵션을 활성화하면 필드의 값에 연결된 SQL 필드가 없습니다. Adobe Campaign은 레코드 저장을 위한 텍스트 유형 &quot;mData&quot; 필드를 만듭니다. 즉, 이러한 필드를 필터링하거나 정렬하지 않습니다.

### 예 {#examples}

값이 데이터베이스에 저장되는 열거형 값의 예:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>     
```

&quot;@databolicy&quot;가 있는 XML 필드 선언:

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

&quot;@applicableIf&quot;의 예:&quot;contains&quot; 속성은 국가 수가 20개 이상인 경우에만 생성됩니다.

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

&quot;shared&quot; 유형의 &quot;@feature&quot;가 있는 예:

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

&quot;dedicated&quot; 유형의 &quot;@feature&quot;의 예:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```

## `<compute-string>` 요소 {#compute-string--element}

### 콘텐츠 모델 {#content-model-1}

compute-string:==EMPTY

### 속성 {#attributes-1}

@expr

### 부모 {#parents-1}

`<element>`

### 어린이 {#children-1}

없음

### 설명 {#description-1}

이 `<compute-string>` 요소를 사용하면 XTK 표현식을 기반으로 문자열을 생성하여 여러 값을 기반으로 인터페이스에 &quot;내장&quot; 레이블을 표시할 수 있습니다.

### 사용 및 사용 컨텍스트 {#use-and-context-of-use-1}

정의되지 `<compute-string>` 않으면 `<compute-string>` 기본적으로 스키마에 있는 기본 키 값으로 요소가 입력됩니다.

### 속성 설명 {#attribute-description-1}

* **expr(문자열)**:XTK 및/또는 Xpath 표현식

### 예 {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

수신자에 대해 계산된 문자열의 결과:&quot;John Doe(john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```

## `<condition>` 요소 {#condition--element}

### 콘텐츠 모델 {#content-model-2}

조건:==EMPTY

### 속성 {#attributes-2}

* @boolOperator(문자열)
* @enabledIf(문자열)
* @expr(문자열)

### 부모 {#parents-2}

`<sysfilter>`

### 어린이 {#children-2}

없음

### 설명 {#description-2}

이 요소를 사용하면 필터링 조건을 정의할 수 있습니다.

### 사용 및 사용 컨텍스트 {#use-and-context-of-use-2}

한 `<sysfiler>` 요소에는 여러 필터링 조건이 포함될 수 있습니다.

### 속성 설명 {#attribute-description-2}

* **boolOperator(문자열)**:여러 `<conditions>` 요소가 동일한 `<sysfilter>` 요소 내에 정의된 경우 이 속성을 사용하여 여러 요소를 결합할 수 있습니다. 기본적으로 논리 링크는 &quot;AND&quot; `<condition>` 입니다. &quot;@boolOperator&quot; 특성을 사용하여 &quot;OR&quot; 및 &quot;AND&quot; 유형 링크를 결합할 수 있습니다.
* **enabledIf(문자열)**:조건 활성화 테스트.
* **expr(문자열)**:XTK 표현식입니다.

### 예 {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```

## `<dbindex>` 요소 {#dbindex--element}

### 콘텐츠 모델 {#content-model-3}

dbindex:==keyfield

### 속성 {#attributes-3}

* @_operation(문자열)
* @applicableIf(문자열)
* @label(문자열)
* @name(MNTOKEN)
* @unique(부울)

### 부모 {#parents-3}

`<element>`

### 어린이 {#children-3}

`<keyfield>`

### 설명 {#description-3}

이 요소를 사용하면 테이블에 연결된 인덱스를 정의할 수 있습니다.

### 사용 및 사용 컨텍스트 {#use-and-context-of-use-3}

여러 개의 색인을 정의할 수 있습니다. 하나의 인덱스는 표의 필드를 하나 이상 참조할 수 있습니다. 일반적으로 인덱스 선언은 기본 스키마 요소의 정의를 따릅니다.

요소에 정의된 `<keyfield>` 요소의 순서는 매우 `<dbindex>` 중요합니다. 첫 번째 `<keyfield>` 항목은 쿼리가 주로 기반으로 하는 인덱스 기준이어야 합니다.

데이터베이스의 인덱스 이름은 테이블 이름과 인덱스 이름을 연결하여 계산됩니다. 예:인덱스 생성 쿼리 중 인덱스 필드의 테이블 이름 &quot;Sample&quot;, 네임스페이스 &quot;Cus&quot;, 인덱스 이름 &quot;MyIndex&quot;-> 이름:&quot;CusSample_myIndex&quot;.

### 속성 설명 {#attribute-description-3}

* **_operation(문자열)**:데이터베이스에 쓰는 유형을 정의합니다.

   이 속성은 기본적으로 기본 스키마를 확장할 때 사용됩니다.

   액세스 가능한 값은 다음과 같습니다.

   * &quot;none&quot;:화해만. 즉, Adobe Campaign이 요소를 업데이트하지 않고 복구하거나 오류가 없는 경우 오류가 생성됩니다.
   * &quot;insertOrUpdate&quot;:업데이트를 삽입하여 사용할 수 있습니다. 즉, Adobe Campaign은 요소를 업데이트하거나 요소가 없을 경우 만듭니다.
   * &quot;삽입&quot;:삽입. 즉, Adobe Campaign은 요소의 존재 여부를 확인하지 않고 요소를 삽입합니다.
   * &quot;업데이트&quot;:업데이트. 즉, Adobe Campaign이 요소를 업데이트하거나 요소가 없을 경우 오류를 생성합니다.
   * &quot;삭제&quot;:삭제. 즉, Adobe Campaign이 요소를 복구 및 삭제합니다.

* **applableIf (string)**:인덱스를 고려하는 조건 - XTK 표현식을 받습니다.
* **label(문자열)**:색인 레이블.
* **이름(MNTOKEN)**:고유 색인 이름.
* **고유(부울)**:이 옵션을 활성화하면(@unique=&quot;true&quot;) 속성이 필드 전체에서 인덱스의 고유성을 보장합니다.

### 예 {#examples-3}

&quot;id&quot; 필드에 색인 만들기 (요소의 &quot;@unique&quot; 특성은 데이터베이스(쿼리)에서 인덱스를 만들 때 &quot;UNIQUE&quot; SQL 키 단어의 추가를 `<dbindex>` 트리거합니다.)

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

&quot;@mail&quot; 및 &quot;@phoneNumber&quot; 필드에 복합 인덱스 만들기:

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

## `<element>` 요소 {#element--element}

### 콘텐츠 모델 {#content-model-4}

element:==(attribute| compute-string| dbindex| 기본값| 요소| 도움말| 가입| 키| sysFilter| translatedDefault)

### 속성 {#attributes-4}

_operation (string), advanced (boolean), aggregate (string), applicableIf (string), autopk (boolean), convTo (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), desc (string), displayAsField), displayAsField) boolean), doesNotSupportDiff(부울 값), 편집(문자열), emptyKeyValue(문자열), enumImage(문자열), expandSchemaTarget (문자열), expand(문자열), externalJoin (부울), featureDate (부울), filterPath (문자열), folderLink (문자열), folderModel(문자열), folderProcess(문자열), fullLoad(부울 값), 계층적(부울 값), 계층적Path(문자열), inout(문자열), 무결성(문자열), 레이블(문자열), labelSingular(문자열), 길이(문자열), 지역화 가능(부울), 이름(MNTOKEN), noDbIndex (부울), noNoOut key (boolean), ordered (boolean), overflowtable(boolean), pkSequence (string), pkStatus (string), ref(string), revAdvanced(boolean), revCardinality (string), revDesc (boolean), revExternalJoin (string), revLabel (string), revLink) (문자열), revTarget(문자열), revVisibleIf (문자열), sql(부울), sqlname(문자열), sqltable(문자열), tableSpace(문자열), tableSpace(문자열), target(MNTOKEN), 템플릿(문자열), 임시 테이블(부울), translatedDefault(문자열), translatedExpr(문자열), type MNTOKEN), 언바운드(부울), 사용자(부울), userEnum(문자열), visibleIf(문자열), xml(부울), xmlChildren(부울)

### 부모 {#parents-4}

`<srcschema>`

`<element>`

### 어린이 {#children-4}

* `<attribute>`
* `<compute-string>`
* `<dbindex>`
* `<default>`
* `<element>`
* `<help>`
* `<join>`
* `<key>`
* `<sysfilter>`
* `<translateddefault>`

### 설명 {#description-4}

Adobe Campaign에는 다음 네 가지 유형의 `<element>` 요소가 있습니다.

* 루트 `<element>` :스키마와 일치하는 SQL 테이블의 이름을 정의합니다.
* 구조 `<element>` :은 `<element>` 또는 `<attribute>` 요소 그룹을 정의합니다.
* 링크 `<element>` :링크를 정의합니다. 이 요소에는 &quot;@type=link&quot; 특성이 포함되어야 합니다.
* XML `<element>` :텍스트 유형 &quot;mData&quot; 필드를 정의합니다. 이 요소에는 &quot;@type=xml&quot; 특성이 포함되어야 합니다.

### 속성 설명 {#attribute-description-4}

* **_operation(문자열)**:데이터베이스에 쓰는 유형을 정의합니다.

   이 속성은 기본적으로 기본 스키마를 확장할 때 사용됩니다.

   액세스 가능한 값은 다음과 같습니다.

   * &quot;none&quot;:화해만. 즉, Adobe Campaign이 요소를 업데이트하지 않고 복구하거나 오류가 없는 경우 오류가 생성됩니다.
   * &quot;insertOrUpdate&quot;:업데이트를 삽입하여 사용할 수 있습니다. 즉, Adobe Campaign은 요소를 업데이트하거나 요소가 없을 경우 만듭니다.
   * &quot;삽입&quot;:삽입. 즉, Adobe Campaign은 요소의 존재 여부를 확인하지 않고 요소를 삽입합니다.
   * &quot;업데이트&quot;:업데이트. 즉, Adobe Campaign이 요소를 업데이트하거나 요소가 없을 경우 오류를 생성합니다.
   * &quot;삭제&quot;:삭제. 즉, Adobe Campaign이 요소를 복구 및 삭제합니다.

* **고급(부울)**:이 옵션이 활성화되면(@advanced=&quot;true&quot;) 양식에서 목록을 구성하기 위해 액세스할 수 있는 사용 가능한 필드 목록에서 속성을 숨길 수 있습니다.
* **aggregate (string)**:다른 스키마를 `<element>` 통해 의 정의를 복사할 수 있습니다. 이 속성은 &quot;namespace:name&quot; 형식의 스키마 선언을 받습니다.
* **applableIf (string)**:조건을 참조하십시오. 이 속성은 XTK 표현식을 받습니다.
* **자동(부울)**:이 옵션이 활성화되면(autopk=&quot;true&quot;) 고유 키가 자동으로 정의됩니다. 이 옵션은 스키마의 기본 요소에만 사용할 수 있습니다. 경고, Adobe Campaign은 생성된 키가 고유함을 보장만 합니다. 키 값이 연속되거나 증가한다는 것은 보장되지 않습니다.
* **dataPolicy(문자열)**:sql 필드에 허용되는 값에 대한 승인 제약 조건을 지정할 수 있습니다. 이 속성의 값은 다음과 같습니다.

   * &quot;none&quot;:값 없음
   * &quot;smartCase&quot;:첫 글자 대문자
   * &quot;lowerCase&quot;:소문자
   * &quot;대문자&quot;:모든 대문자
   * &quot;이메일&quot;:이메일 주소
   * &quot;phone&quot;:전화 번호
   * &quot;identifier&quot;:식별자 이름
   * &quot;resIdentifier&quot;:파일 이름

* **dbEnum(문자열)**:는 &quot;닫힘&quot; 열거형의 내부 이름을 받습니다. 열거형 값은 에서 정의해야 합니다 `<srcschema>`.
* **defOnDuplicate(부울)**:이 속성을 활성화하면 레코드가 복제되면(@default에 정의됨) 기본값이 자동으로 레코드에 다시 적용됩니다.
* **기본값(문자열)**:요소 비헤이비어를 정의할 수 있습니다(함수 호출, 기본값). 이 속성은 XTK 표현식을 받습니다.
* **desc (string)**:요소의 설명을 삽입할 수 있습니다. 이 설명은 인터페이스의 상태 표시줄에 표시됩니다.
* **displayAsField(부울)**:이 속성이 활성화되면 &quot;링크&quot; 유형이 스키마의 트리 보기에 필드로 `<element>` 표시됩니다(&quot;구조&quot; 탭). 이렇게 하면 링크를 로컬 필드로 표시하고 쿼리 중에 동작을 변경할 수 있습니다. 쿼리의 SELECT에 요소가 있으면 링크 대상의 값이 사용됩니다. 쿼리의 WHERE에 요소가 있으면 링크의 기본 키가 사용됩니다.
* **edit (string)**:이 속성은 스키마에 연결된 양식에서 사용할 입력 유형을 지정합니다.
* **enum(문자열)**:는 필드에 연결된 열거형의 이름을 받습니다. 열거를 동일한 스키마나 원격 스키마에 삽입할 수 있습니다.
* **expr(문자열)**:이 속성은 테이블에 정의가 저장되지 않는 계산된 필드를 정의합니다. Xpath 또는 XTK(문자열) 표현식을 받습니다.
* **externalJoin(부울)**:&quot;링크&quot; 유형 요소의 외부 조인.
* **feature (string)**:특성 필드를 정의합니다.이러한 필드는 기존 테이블의 데이터를 확장하지만 부록 테이블의 저장과 함께 사용됩니다. 허용된 값은 다음과 같습니다.

   * &quot;공유&quot;:컨텐츠는 데이터 유형별로 공유 테이블에 저장됩니다
   * &quot;전용&quot;:컨텐츠는 전용 테이블에 저장됩니다.
   SQL 특성 테이블은 특성 유형에 따라 자동으로 만들어집니다.

   * 전용: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 공유: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`
   두 가지 유형의 특성 필드가 있습니다.특성에 대해 단일 값이 인증되는 단순 필드와 여러 선택 필드(특성이 여러 값이 포함될 수 있는 컬렉션 요소에 링크됨)

   스키마에서 특성이 정의되면 이 스키마에는 단일 필드를 기반으로 하는 기본 키가 있어야 합니다(복합 키는 인증되지 않음).

* **featureDate(부울)**:특성 &quot;@feature&quot; 특성 필드에 연결되어 있습니다. 값이 &quot;true&quot;이면 값이 마지막으로 업데이트된 시기를 알 수 있습니다.
* **filterPath(문자열)**:이 속성을 사용하면 Xpath를 수신하고 필드에 필터를 정의할 수 있습니다.
* **folderLink(문자열)**:이 속성은 엔티티가 포함된 파일을 복구할 수 있는 링크의 이름을 받습니다.
* **folderModel(문자열)**:엔티티 저장소를 사용할 수 있는 폴더 유형을 정의합니다. 이 속성은 &quot;@folderLink&quot;가 있는 경우에만 정의됩니다.
* **folderProcess(문자열)**:엔티티 모델 인스턴스가 저장되는 링크를 정의합니다. 이 속성은 &quot;@folderLink&quot;가 있는 경우에만 정의됩니다.
* **fullLoad(부울)**:이 속성은 양식에서 필드를 선택하는 동안 테이블에 있는 모든 레코드를 강제로 표시합니다.
* **img(문자열)**:는 요소에 연결된 이미지의 경로를 받습니다. 이 특성의 값은 &quot;namespace:image name&quot; 유형입니다. 예:img=&quot;cus:myImage.jpg&quot; 실제로 이미지를 애플리케이션 서버로 가져와야 합니다.
* **integrity (string)**:대상 테이블에 대한 소스 테이블 발생에 대한 참조 무결성

   액세스 가능한 값은 다음과 같습니다.

   * &quot;정의&quot;:Adobe Campaign은 링크를 통해 참조되는 경우 엔티티를 삭제하지 않습니다
   * &quot;normal&quot;:소스 발생을 삭제하면 대상 발생 시 링크의 키가 초기화됩니다(기본 모드). 이 유형의 무결성은 모든 외래 키를 초기화합니다
   * &quot;소유&quot;:소스 항목 삭제는 타겟 항목의 삭제를 트리거합니다.
   * &quot;owncopy&quot;:&quot;소유&quot;(삭제 시) 또는 중복 발생(중복의 경우)과 유사
   * &quot;중립&quot;:아무것도 하지 않음

* **label(문자열)**:요소 레이블입니다.
* **labelSingular(문자열)**:인터페이스의 일부 부분에 사용되는 요소의 레이블(단일 양식)입니다.
* **length(문자열)**:max. &quot;문자열&quot; 유형의 SQL 필드에 대해 권한이 부여된 문자 수입니다.
* **지역화 가능(부울)**:활성화되면 이 속성은 번역(내부 사용)에 대한 &quot;@label&quot; 속성의 값을 복구하도록 컬렉션 도구에 지시합니다.
* **이름(MNTOKEN)**:테이블의 이름과 일치하는 요소의 내부 이름입니다. &quot;@name&quot; 속성의 값은 짧아야 하며, 특히 영어로 되어 있어야 하며, XML에 연결된 이름 지정 제한을 준수해야 합니다.

   스키마가 데이터베이스에 작성되면 접두사는 Adobe Campaign에 의해 필드 이름에 자동으로 추가됩니다.

   * &quot;i&quot;:접두사를 사용합니다.
   * &quot;d&quot;:접두사를 사용합니다.
   * &quot;s&quot;:접두사를 사용합니다.
   * &quot;ts&quot;:접두사를 사용합니다.
   테이블 이름을 자율적으로 정의하려면 기본 스키마 요소의 정의에 &quot;@sqltable&quot; 속성을 사용해야 합니다.

* **noDbIndex(부울)**:요소를 인덱싱하지 않도록 지정할 수 있습니다.
* **ordered(부울)**:속성이 활성화되면(ordered=&quot;true&quot;) Adobe Campaign은 요소 선언 시퀀스를 XML 컬렉션 요소에 유지합니다.
* **pkSequence(문자열)**:는 자동 증분 키를 계산하는 데 사용할 시퀀스의 이름을 받습니다. 이 속성은 자동 증분 키가 스키마의 루트 요소에 정의된 경우에만 사용할 수 있습니다.
* **pkgStatus(문자열)**:패키지 내보내기 동안 값은 이 속성의 값으로 고려됩니다.

   * &quot;always&quot;:요소는 항상 존재합니다.
   * &quot;never&quot;:요소는 절대 존재하지 않습니다.
   * &quot;default (or nothing)&quot;:요소가 기본 요소이거나 내부 필드가 아니며 다른 인스턴스와 호환하지 않는 한 요소가 내보내집니다.

* **ref(문자열)**:이 속성은 여러 스키마가 공유하는 >element> 요소에 대한 참조를 정의합니다(정의 팩토링). 정의가 현재 스키마로 복사되지 않습니다.
* **필수(부울)**:이 속성이 활성화되면(@required=&quot;true&quot;) 필드가 인터페이스에서 강조 표시됩니다. 필드의 레이블은 양식에 빨간색으로 표시됩니다.
* **revAdvanced(부울)**:이 속성을 활성화하면 반대 링크가 &quot;고급&quot; 링크임을 지정합니다.
* **revCardinality(문자열)**:이 속성은 두 테이블 간의 링크의 카디널리티를 정의합니다. &quot;링크&quot; 유형에 사용됩니다 `<element>`.

   가능한 값은 다음과 같습니다.

   * &quot;single&quot; :간단한 1-1 유형 링크
   * &quot;언바운드&quot;:1-N 유형 컬렉션 링크
   기본적으로 링크를 만드는 동안 속성이 지정되지 않으면 카디널리티는 1-N이 됩니다.

* **revDesc(문자열)**:이 속성은 반대쪽 링크에 연결된 설명을 받습니다.
* **revExternalJoin(부울)**:이 속성을 활성화하면 반대 링크에 대해 외부 조인을 강제 적용할 수 있습니다.
* **revIntegrity(문자열)**:이 속성은 대상 스키마에 대한 무결성을 정의합니다. &quot;@integrity&quot; 속성과 동일한 값이 인증되었습니다. 기본적으로 Adobe Campaign은 이 속성에 &quot;일반&quot; 값을 제공합니다.
* **revLabel(문자열)**:레이블(반대쪽 링크)입니다.
* **revLink(문자열)**:상대 링크의 이름입니다. 값이 &quot;NONE&quot;_인_&#x200B;경우 대상 스키마에서 반대 링크가 만들어지지 않습니다.
* **revTarget(문자열)**:의 대상이 됩니다.
* **sql(부울)**:이 특성이 활성화된 경우(@sql=&quot;true&quot;) 요소에 xml=&quot;true&quot; 속성이 있더라도 SQL 요소의 저장소를 강제로 유지합니다.
* **sqlname(문자열)**:테이블을 만드는 동안 필드의 이름입니다. &quot;@sqlname&quot;을(를) 지정하지 않으면 기본적으로 &quot;@name&quot; 속성의 값이 사용됩니다. 스키마를 표에 쓸 때 접두사는 필드 유형에 따라 자동으로 추가됩니다.
* **sqltable(문자열)**:스키마의 기본 요소에 대해 이 속성은 기본적으로 생성된 SQL 테이블의 이름을 오버로드합니다. &quot;@sqltable&quot;을 지정하지 않으면 기본 이름이 다음과 같이 구조화됩니다.namespace(첫 번째 문자 대문자) 뒤에 SrcSchema &quot;@name&quot;의 값이 옵니다.
* **tableSpace(문자열)**:이 속성을 사용하면 테이블에 대해 테이블스페이스를 저장하는 새 데이터를 지정할 수 있습니다(루트에서 유효). `<element>`
* **tableSpaceIndex(문자열)**:이 속성을 사용하면 테이블에 대한 새 인덱스 저장 영역 테이블스페이스를 지정할 수 있습니다(루트에서 유효). `<element>`
* **target(MNTOKEN)**:는 테이블 간 링크를 만들 때 대상 스키마의 이름을 받습니다. 이 속성은 &quot;링크&quot; 유형 요소에만 활성화됩니다.
* **템플릿(문자열)**:이 속성은 여러 스키마로 공유된 `<element>` 요소에 대한 참조를 정의합니다. 정의가 현재 스키마에 자동으로 복사됩니다.
* **translatedDefault(문자열)**:&quot;@default&quot; 속성이 있으면 &quot;@translatedDefault&quot;를 사용하여 번역 도구(내부 사용)로 수집하기 위해 @default에 정의된 표현식과 일치하도록 표현식을 재정의할 수 있습니다.
* **translatedExpr(문자열)**:&quot;@expr&quot; 특성이 있는 경우 &quot;@translatedExpr&quot; 특성을 사용하면 &quot;@expr&quot;에 정의된 표현식과 일치하는 표현식을 재정의할 수 있으며, 이 특성은 번역 도구(내부 사용)에 의해 수집됩니다.
* **유형(MNTOKEN)**:요소에 저장된 데이터의 유형을 정의합니다.

   사용 가능한 유형 목록:

   * 임의
   * bin
   * blob
   * boolean
   * byte
   * CDATA
   * datetime
   * datetimez
   * datetimenotz
   * date
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * 메모
   * MNTOKEN
   * 퍼센트
   * 기본 키
   * short
   * 문자열
   * time
   * 시간 대응
   * uuid

* **언바운드(부울)**:속성이 활성화되면(언바운드=&quot;true&quot;) 링크가 1-N 기수에 대한 컬렉션 요소로 선언됩니다.
* **userEnum(문자열)**:는 &quot;open&quot; 열거형의 내부 이름을 받습니다. 열거형 값은 인터페이스에서 사용자가 정의할 수 있습니다.
* **xml(부울)**:이 옵션을 활성화하면 요소에 정의된 모든 값이 XML에 저장됩니다(텍스트 유형 &quot;mData&quot; 필드). 즉, 이러한 필드를 필터링하거나 정렬하지 않습니다.
* **xmlChildren(부울)**:각 자식( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`

## `<enumeration>` 요소 {#enumeration--element}

### 콘텐츠 모델 {#content-model-5}

열거형:==(help| value)

### 속성 {#attributes-5}

* @basetype(문자열)
* @default(문자열)
* @desc(문자열)
* @label(문자열)
* @name(문자열)
* @template(문자열)

### 부모 {#parents-5}

`<srcschema>`

### 어린이 {#children-5}

* `<help>`
* `<value>`

### 설명 {#description-5}

이 요소를 사용하면 값 열거형을 정의할 수 있습니다. 열거형은 정의된 스키마에 속하지만 다른 스키마를 통해 액세스할 수 있습니다.

### 사용 및 사용 컨텍스트 {#use-and-context-of-use-4}

열거형은 스키마 시작 시(기본 요소가 정의되기 전에) 정의됩니다.

### 속성 설명 {#attribute-description-5}

* **basetype(문자열)**:열거형에 저장된 값의 유형입니다.

   사용 가능한 유형 목록:

   * 임의
   * bin
   * blob
   * boolean
   * byte
   * CDATA
   * datetime
   * datetimez
   * datetimenotz
   * date
   * DOMDocument
   * 돔
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * 메모
   * MNTOKEN
   * 퍼센트
   * 기본 키
   * short
   * 문자열
   * time
   * 시간 대응
   * uuid

* **기본값(문자열)**:기본값. 기본값은 열거형에 정의된 값 중 하나일 수도 있습니다.
* **desc (string)**:열거형 설명.
* **label(문자열)**:열거형 레이블입니다.
* **name(문자열)**:열거형의 내부 이름입니다.
* **템플릿(문자열)**:이 속성은 여러 스키마로 공유된 `<enumeration>` 요소에 대한 참조를 정의합니다. 정의가 현재 스키마에 자동으로 복사됩니다.

### 예 {#examples-4}

값이 데이터베이스에 저장되는 열거형 값의 예:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

기본값이 있는 열거형의 정의:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```

## `<help>` 요소 {#help--element}

### 콘텐츠 모델 {#content-model-6}

help:==EMPTY

### 속성 {#attributes-6}

없음

### 부모 {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

### 어린이 {#children-6}

없음

### 설명 {#description-6}

이 요소를 사용하면 `<element>` 또는 `<attribute>` 요소를 설명할 수 있습니다. 텍스트만 포함할 수 있으며 데이터베이스의 XML에 저장됩니다.

### 속성 설명 {#attribute-description-6}

이 요소에는 특성이 없습니다.

### 예 {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```

## `<join>` 요소 {#join--element}

### 콘텐츠 모델 {#content-model-7}

join:==EMPTY

### 속성 {#attributes-7}

* @dstFilterExpr(문자열)
* @xpath-dst (문자열)
* @xpath-src(문자열)

### 부모 {#parents-7}

`<element>`

### 어린이 {#children-7}

없음

### 설명 {#description-7}

SQL 테이블 간 조인을 만드는 필드를 정의할 수 있습니다.

### 사용 및 사용 컨텍스트 {#use-and-context-of-use-5}

요소는 상위 `<join>` `<element>` 요소가 &#39;link&#39; 유형인 경우에만 사용할 수 있습니다. 즉, 부모 요소에는 &quot;@type=link&quot; 속성이 선언되어 있어야 합니다.

원격 테이블의 이름과 네임스페이스를 `<join>` 요소에 지정할 필요는 없습니다. 상위에 지정해야 합니다 `<element>`.

규칙별로, 링크는 스키마 끝에 정의됩니다.

링크 유형 요소가 정의될 때 `<join>` 요소가 지정되지 않으면 링크가 두 테이블의 기본 키에 자동으로 배치됩니다.

### 속성 설명 {#attribute-description-7}

* **dstFilterExpr(문자열)**:이 속성을 사용하면 원격 테이블에서 적격한 값의 수를 제한할 수 있습니다.
* **xpath-dst(문자열)**:이 속성은 Xpath(@name 특성의 원격 테이블)를 받습니다.
* **xpath-src(문자열)**:이 속성은 현재 스키마에서 Xpath(@name 속성)를 받습니다.

### 예 {#examples-6}

현재 테이블의 &#39;email&#39; 필드와 원격 테이블의 &quot;@compagny-id&quot; 필드 간의 링크:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

&#39;EN&#39; 값이 포함되어야 하는 &quot;@country&quot; 필드의 내용을 기반으로 &quot;cus:Country&quot; 테이블 쪽으로 필터링된 링크:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```

## `<key>` 요소 {#key--element}

### 콘텐츠 모델 {#content-model-8}

key:==keyfield

### 속성 {#attributes-8}

* @allowEmptyPart(부울)
* @applicableIf(문자열)
* @internal (boolean)
* @label(문자열)
* @name(MNTOKEN)
* @noDbIndex(부울)

### 부모 {#parents-8}

`<element>`

### 어린이 {#children-8}

`<keyfield>`

### 설명 {#description-8}

이 요소를 사용하면 테이블에서 레코드를 식별하는 키를 정의할 수 있습니다.

테이블에 키가 하나 이상 있어야 합니다.

### 사용 및 사용 컨텍스트 {#use-and-context-of-use-6}

일반적으로 키는 스키마와 인덱스의 기본 요소 뒤에 선언됩니다.

키는 여러 필드(예: 여러 `<keyfield>` 하위)를 포함하는 경우 합성이라고 합니다. 기본 키를 정의하는 데 복합 키를 사용하지 마십시오.

스키마의 기본 요소에 &quot;@autopk=true&quot; 특성이 포함된 경우 기본 키는 고유합니다. 스키마당 기본 키는 하나만 가질 수 있습니다.

처음 1000개의 식별자는 예약되어 있으므로 키에 대해 값 범위를 정의해야 하는 경우 1000부터 시작합니다.

### 속성 설명 {#attribute-description-8}

* **allowEmptyPart(부울)**:복합 키의 경우 이 속성이 활성화되면 키 중 하나 이상이 비어 있지 않으면 해당 키가 유효한 것으로 간주됩니다. 이 경우 빈 개념 값은 &quot;0&quot;(부울 값 또는 모든 유형의 숫자 데이터)입니다. 기본적으로 복합 키를 구성하는 모든 키를 입력해야 합니다.
* **applableIf (string)**:이 속성을 사용하면 키를 선택 사항으로 만들 수 있습니다. 키 정의가 적용되는 조건에 따라 조건을 정의합니다. 이 속성은 XTK 표현식을 받습니다.
* **내부(부울)**:활성화되면 이 속성을 사용하여 Adobe Campaign이 키가 기본 키임을 알 수 있습니다.
* **label(문자열)**:레이블입니다.
* **이름(MNTOKEN)**:키의 내부 이름입니다.
* **noDbIndex(부울)**:활성화되면(noDbIndex=&quot;true&quot;) 키와 일치하는 필드가 인덱싱되지 않습니다.

### 예 {#examples-------}

&quot;@expr&quot; 또는 &quot;alias&quot; 필드를 비워 둘 수 있는 복합 키의 선언입니다.

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

STRING 유형의 &quot;이름&quot; 필드에 있는 기본 키 선언 및 일치하는 SQL `<srcschema>` 쿼리:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```

## `<keyfield>` 요소 {#keyfield--element}

### 콘텐츠 모델 {#content-model-9}

keyfield:==EMPTY

### 속성 {#attributes-9}

* @xlink(MNTOKEN)
* @xpath(MNTOKEN)

### 부모 {#parents-9}

`<key>`  ,  `<dbindex />`

### 어린이 {#children-9}

없음

### 설명 {#description-9}

이 요소는 색인 또는 키에 통합할 필드를 정의합니다.

### 속성 설명 {#attribute-description-9}

* **xlink(MNTOKEN)**:관계식 테이블(N-N 링크)에 대해 조인에 정의된 외래 키를 자동으로 참조할 수 있도록 해줍니다.
* **xpath(MNTOKEN)**:인덱스나 `<attribute>` 요소의 키 정의입니다. 이 속성은 키 또는 인덱스를 정의하는 스키마 속성의 경로를 정의하는 Xpath를 받습니다.

### 예 {#examples-}

&quot;@name&quot;에 Xpath가 있는 인덱스의 &quot;sName&quot; 필드 선택:

```
<keyfield xpath="@name"/>
```

## `<method>` 요소 {#method--element}

### 콘텐츠 모델 {#content-model-10}

메서드:==( help| 매개 변수)

### 속성 {#attributes-10}

* @_operation(문자열)
* @access(문자열)
* @const (boolean)
* @hidden(부울)
* @label(문자열)
* @library(문자열)
* @name(MNTOKEN)
* @pkonly(부울)
* @static(부울)

### 부모 {#parents-10}

`<methods>`  ,  `<interface />`

### 어린이 {#children-10}

* `<help>`
* `<parameters>`

### 설명 {#description-10}

이 요소를 사용하면 SOAP 메서드를 정의할 수 있습니다.

### 사용 및 사용 컨텍스트 {#use-and-context-of-use-7}

SOAP 메서드는 애플리케이션 프로세스를 활성화합니다.

&quot;@library&quot;는 새 메서드(비기본)를 선언하는 데 필요합니다.네임스페이스와 라이브러리에 사용되는 이름은 선언이 있는 스키마의 이름 및 네임스페이스와 독립적입니다.

### 속성 설명 {#attribute-description-10}

* **access(문자열)**:이 속성은 메서드를 사용하기 위한 액세스 제어를 정의합니다. 이 속성이 없는 경우 식별은 필수입니다. 사용 가능한 값은 다음과 같습니다.&#39;anonymous&#39;, &#39;admin&#39; 및 &#39;sql&#39;
* **const (boolean)**:활성화되면 이 속성은 선언된 메서드가
* **label(문자열)**:레이블입니다.
* **library(문자열)**:이 메서드는 응용 프로그램이 고유하지 않습니다. 이 속성은 메서드 정의가 있는 메서드 라이브러리 값을 가져옵니다(nms:mylibrary.js).
* **이름(MNTOKEN)**:고유한 메서드 이름.
* **정적(부울)**:이 속성이 활성화되면 이 메서드는 자치적으로 간주되며, 호출될 때 메서드에 모든 매개 변수를 지정해야 합니다.

### 예 {#examples-7}

기본 &quot;구독&quot;의 정의:

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

## `<methods>` 요소 {#methods--element}

### 콘텐츠 모델 {#content-model-11}

메서드:==method

### 속성 {#attributes-11}

없음

### 부모 {#parents-11}

`<srcschema>`

### 어린이 {#children-11}

메서드

### 설명 {#description-11}

이 요소를 사용하면 `<method>` 요소를 정의할 수 있습니다. 메서드를 선언하려면 필수입니다.

### 속성 설명 {#attribute-description-11}

이 요소에는 특성이 없습니다.

### 예 {#examples-8}

```
<methods async="true"
...// definition of one or more <method
</methods>
```

## `<param>` 요소 {#param--element}

### 콘텐츠 모델 {#content-model-12}

param:==help

### 속성 {#attributes-12}

* @_operation(문자열)
* @desc(문자열)
* @enum(문자열)
* @inout(문자열)
* @label(문자열)
* @localizable(문자열)
* @name(MNTOKEN)
* @namespace(MNTOKEN)
* @type(문자열)

### 부모 {#parents-12}

`<parameters>`

### 어린이 {#children-12}

`<help>`

### 설명 {#description-12}

이 요소를 사용하면 SOAP 메서드 호출에 대한 매개 변수를 정의할 수 있습니다.

### 속성 설명 {#attribute-description-12}

* **desc (string)**:요소에 관련된 `<param>` 설명입니다.
* **inout(문자열)**:이 속성은 매개 변수가 SOAP 호출의 입력(in) 또는 출력(출력)에 있는지 여부를 정의합니다. 이 속성을 지정하지 않으면 기본 매개 변수는 입력(&quot;@inout=in&quot;)입니다.
* **label(문자열)**: `<param>` 레이블
* **localized(문자열)**:활성화되면 이 속성은 번역(내부 사용)에 대한 &quot;@label&quot; 속성의 값을 복구하도록 컬렉션 도구에 지시합니다.
* **이름(MNTOKEN)**:내부 이름 `<param>`
* **type(문자열)**:이 속성은 `<param>` 요소의 유형을 정의합니다.

   사용 가능한 유형 목록:

   * 임의
   * bin
   * blob
   * boolean
   * byte
   * CDATA
   * datetime
   * datetimez
   * datetimenotz
   * date
   * DOMDocument
   * 돔
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * 메모
   * MNTOKEN
   * 퍼센트
   * 기본 키
   * short
   * 문자열
   * time
   * 시간 대응
   * uuid

### 예 {#examples-9}

문자 문자열 유형의 &quot;serviceName&quot; 인바운드 설정의 정의:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```

## `<parameters>` 요소 {#parameters--element}

### 콘텐츠 모델 {#content-model-13}

매개 변수:==param

### 속성 {#attributes-13}

없음

### 부모 {#parents-13}

`<method>`

### 어린이 {#children-13}

`<param>`

### 설명 {#description-13}

이 요소는 `<parameter>` 요소 그룹을 정의합니다.

### 사용 및 사용 컨텍스트 {#use-and-context-of-use-8}

이 요소는 요소의 단일 `<param>` 하위 요소에도 필수적입니다 `<method>` .

### 속성 설명 {#attribute-description-13}

없음

### 예 {#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```

## `<srcschema>` 요소 {#srcschema--element}

### 콘텐츠 모델 {#content-model-14}

srcSchema:==(attribute)| createdBy| 데이터| 요소| 열거| 도움말| 인터페이스| 메서드| modifiedBy)

### 속성 {#attributes-14}

created(datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (string), img (string), implements (string), label (string), labelSingular(string), lastModified (datetime), mappingType (string), modifiedBy-id (long), name (string), namespace), string), useRecycleBin(부울), 보기(부울), xtkschema(문자열)

### 부모 {#parents-14}

없음

### 어린이 {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

### 설명 {#description-14}

이 `<srcschema>` 는 스키마의 루트 요소입니다. 스키마 정의에 대한 입력 점입니다.

### 사용 및 사용 컨텍스트 {#use-and-context-of-use-9}

스키마 프레젠테이션은 스키마 참조 [및 스키마](../../configuration/using/about-schema-reference.md) 구조에 [대해 사용할](../../configuration/using/schema-structure.md)수 있습니다.

### 속성 설명 {#attribute-description-14}

* **created(datetime)**:이 속성은 스키마 생성 날짜 및 시간에 대한 정보를 제공합니다. &quot;날짜 시간&quot; 양식이 있습니다. 표시되는 값은 서버에서 가져옵니다. 시간은 UTC 형식으로 표시됩니다.
* **createdBy-id (long)**:는 스키마를 만든 연산자의 식별자입니다.
* **desc (string)**:스키마 설명
* **entitySchema(문자열)**:구문과 승인이 기반으로 하는 기본 스키마(기본적으로 Adobe Campaign에 대해):xtk:srcSchema). 현재 스키마를 저장할 때 Adobe Campaign은 @xtkschema 속성에 선언된 스키마와 함께 해당 문법을 승인합니다.
* **extendedSchema(문자열)**:는 현재 스키마 확장이 기반으로 하는 기본 스키마 이름을 받습니다. 양식은 &quot;namespace:name&quot;입니다.
* **img(문자열)**:스키마에 연결된 아이콘(스키마 생성 마법사에서 정의할 수 있음).
* **label(문자열)**:스키마 레이블입니다.
* **labelSingular(문자열)**:label (singular) for display in the interface.
* **lastModified(datetime)**:이 속성은 마지막 수정 날짜 및 시간에 대한 정보를 제공합니다. &quot;날짜 시간&quot; 양식이 있습니다. 표시되는 값은 서버에서 가져옵니다. 시간은 UTC 형식으로 표시됩니다.
* **라이브러리(부울)**:스키마를 엔티티가 아닌 라이브러리로 사용하는 경우 따라서 &quot;@ref&quot; 및 &quot;@template&quot; 특성 덕분에 다른 스키마에서 이 스키마를 참조할 수 있습니다.
* **mappingType(문자열)**:

   * &quot;sql&quot;:데이터베이스 매핑
   * &quot;textFile&quot;:텍스트 파일 매핑
   * &quot;xmlFile&quot;:XML 형식 텍스트 파일 매핑
   * &quot;binaryFile&quot;:이진 파일 매핑

* **modifiedBy-id (long)**:스키마를 변경한 연산자의 식별자와 일치합니다.
* **name(문자열)**:고유한 스키마 이름입니다.
* **namespace(문자열)**:스키마의 네임스페이스(기본값:nms, xtk, nl). 프로젝트에 대한 새 스키마를 만들 때는 전용 네임스페이스를 사용하는 것이 좋습니다.
* **useRecycleBin(부울)**:애플리케이션에서 휴지통 기능을 활성화합니다. 삭제된 레코드는 최종 삭제 전에 휴지통에 보관됩니다. 이 함수는 &quot;배달&quot; 모드에서만 사용할 수 있습니다.
* **보기(부울)**:활성화된 경우(@view=&quot;true&quot;) 스키마는 뷰로 사용됩니다. 데이터베이스 구조 업데이트 마법사는 스키마를 고려하지 않습니다. 이 옵션은 주로 외부 테이블을 참조하는 데 사용됩니다.
* **xtkschema(문자열)**:스키마 문법을 정의하는 스키마의 이름입니다(기본적으로 xtk:srcSchema).

### 예 {#examples-11}

`<srcschema>` box 스키마 밖에서 &quot;nms:delivery&quot;의 요소

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```

## `<sysfilter>` 요소 {#sysfilter--element}

### 콘텐츠 모델 {#content-model-15}

sysFilter:==condition

### 속성 {#attributes-15}

없음

### 부모 {#parents-15}

`<element>`

### 어린이 {#children-15}

`<condition>`

### 설명 {#description-15}

이 요소를 사용하면 필터를 정의할 수 있습니다.

### 속성 설명 {#attribute-description-15}

이 요소에는 특성이 없습니다.

### 예 {#examples-12}

@name 속성에 조건이 있는 필터의 정의:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```

## `<value>` 요소 {#value--element}

### 콘텐츠 모델 {#content-model-16}

value:==help

### 속성 {#attributes-16}

* @applicableIf(문자열)
* @desc(문자열)
* @enabledIf(문자열)
* @img(문자열)
* @label(문자열)
* @name(문자열)
* @value(문자열)

### 부모 {#parents-16}

`<enumeration>`

### 어린이 {#children-16}

`<help>`

### 설명 {#description-16}

이 요소를 사용하면 열거형에 저장된 값을 정의할 수 있습니다.

### 속성 설명 {#attribute-description-16}

* **applableIf (string)**:이 속성을 사용하면 열거형 값을 선택 사항으로 만들 수 있습니다. XTK 표현식을 받습니다.
* **desc (string)**:열거형 값에 대한 설명입니다.
* **enabledIf(문자열)**:열거형 값 활성화에 대한 조건입니다.
* **img(문자열)**:image linked to the enumeration in the &quot;namespace:image_name&quot; form. 이미지를 응용 프로그램 서버로 가져와야 합니다.
* **label(문자열)**:enumeration 값의 레이블입니다.
* **name(문자열)**:열거형 값의 내부 이름입니다.
* **값(문자열)**:열거형 값의 값입니다. 값의 유형은 열거형 유형에 따라 정의됩니다. 열거형이 문자 문자열 유형인 경우 문자 문자열 유형 값만 포함할 수 있습니다.

### 예 {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
