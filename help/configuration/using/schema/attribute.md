---
product: campaign
title: 요소 및 속성 - 속성 요소
description: 요소 및 속성
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '1555'
ht-degree: 1%

---

# 속성 요소 {#attribute--element}

![](../../../assets/v7-only.svg)

## 콘텐츠 모델 {#content-model}

attribute:==help

## 속성 {#attributes}

_operation (string), advanced (부울), applicableIf (문자열), autoIncrement (부울), includesTo (문자열), dataPolicy (문자열), dbEnum (문자열), defOnDuplicate (부울), default (문자열), desc (문자열), edit (문자열), enum (문자열), expr (문자열), feature (문자열), featureDate (부울), img (문자열), inout (문자열), label (문자열), length (문자열), localizable (부울), name (MNTOKEN), notNull (부울), pkgStatus (문자열), ref (문자열), required (부울), sql (부울), sqlDefault (문자열), sqlname (문자열), sqltable (문자열) , translatedDefault (문자열), translatedExpr (문자열), type (MNTOKEN), user (부울), userEnum (문자열), visibleIf (문자열), xml (부울)

## 상위 {#parents}

`<element>`

## 하위 {#children}

`<help>`

## 설명 {#description}

`<attribute>` 요소를 사용하여 데이터베이스의 필드를 정의할 수 있습니다.

## 사용 및 사용 컨텍스트 {#use-and-context-of-use}

`<attribute>` 요소를 선언해야 합니다. `<element>` 요소를 생성하지 않습니다.

시퀀스 `<attribute>` 요소는 `<srcschema>` 는 데이터베이스의 필드 만들기 순서에 영향을 주지 않습니다. 생성 순서는 알파벳순입니다.

## 속성 설명 {#attribute-description}

* **작업(문자열)(_o)**: 데이터베이스에 쓰는 유형을 정의합니다.

   이 속성은 기본 제공 스키마를 확장할 때 주로 사용됩니다.

   액세스 가능한 값은 다음과 같습니다.

   * &quot;none&quot;: 조정만 가능합니다. 즉, Adobe Campaign은 요소가 존재하지 않는 경우 해당 요소를 업데이트하거나 오류를 생성하지 않고 요소를 복구합니다.
   * &quot;insertOrUpdate&quot;: 삽입을 사용하여 업데이트합니다. 즉, Adobe Campaign이 요소를 업데이트하거나 존재하지 않는 경우 만듭니다.
   * &quot;insert&quot;: 삽입. 즉, Adobe Campaign은 요소의 존재 여부를 확인하지 않고 요소를 삽입합니다.
   * &quot;update&quot;: update. 즉, Adobe Campaign이 요소를 업데이트하거나 존재하지 않는 경우 오류를 생성합니다.
   * &quot;delete&quot;: 삭제. 즉, Adobe Campaign에서 요소를 복구하고 삭제합니다.

* **advanced(부울)**: 이 옵션이 활성화되면(@advanced=&quot;true&quot;) 양식에서 목록을 구성하는 데 액세스할 수 있는 사용 가능한 필드 목록에서 속성을 숨길 수 있습니다.
* **applicableIf (문자열)**: 이 속성을 사용하면 필드를 선택 사항으로 만들 수 있습니다. 다음 `<attribute>` 제약 조건을 준수할 때 데이터베이스를 업데이트할 때 요소가 고려됩니다. &quot;applicableIf&quot;는 XTK 표현식을 받습니다.
* **autoIncrement(부울)**: 이 옵션이 활성화되면 필드가 카운터가 됩니다. 이렇게 하면 값(대부분 ID)을 증가시킬 수 있습니다. (외부 사용)
* **속함(문자열)**: 필드를 공유하는 테이블의 이름과 네임스페이스를 가져와 속성이 선언된 스키마를 채웁니다. (다음에만 사용됨) `<schema>`).
* **dataPolicy(문자열)**: SQL 또는 XML 필드에 허용되는 값에 대한 승인 제약 조건을 지정할 수 있습니다. 이 속성의 값은 다음과 같습니다.

   * &quot;none&quot;: 값 없음
   * &quot;smartCase&quot;: 첫 글자 대문자
   * &quot;lowerCase&quot;: 모든 lower case
   * &quot;upperCase&quot;: 모든 upper case
   * &quot;email&quot;: 이메일 주소
   * &quot;phone&quot;: 전화 번호
   * &quot;identifier&quot;: 식별자 이름
   * &quot;resIdentifier&quot;: 파일 이름

* **dbEnum(문자열)**: &quot;폐쇄형&quot; 열거형의 내부 이름을 받습니다. 열거형 값은 `<srcschema>`.
* **defOnDuplicate(부울)**: 이 속성이 활성화되면 레코드가 복제될 때 기본값(@default에 정의됨)이 레코드에 자동으로 다시 적용됩니다.
* **기본값(문자열)**: 기본 필드의 값(함수 호출, 기본값)을 정의할 수 있습니다. 이 속성은 XTK 식을 받습니다.
* **desc(문자열)**: 속성에 대한 설명을 삽입할 수 있습니다. 이 설명은 인터페이스의 상태 표시줄에 표시됩니다.
* **편집(문자열)**: 이 속성은 스키마에 연결된 양식에서 사용될 입력 유형을 지정합니다.
* **enum(문자열)**: 필드에 연결된 열거형의 이름을 받습니다. 열거형은 동일한 스키마에 삽입하거나 원격 스키마에 삽입할 수 있습니다.
* **expr (문자열)**: 필드 사전 계산 표현식을 정의합니다. 이 속성은 Xpath 또는 XTK 식을 받습니다.
* **기능(문자열)**: 특성 필드 정의: 이러한 필드는 기존 테이블에서 데이터를 확장하는 데 사용되지만 별도 테이블에는 저장소가 제공됩니다. 허용되는 값은 다음과 같습니다.

   * &quot;shared&quot;: 컨텐츠는 데이터 유형별로 공유 테이블에 저장됩니다
   * &quot;전용&quot;: 컨텐츠가 전용 테이블에 저장됩니다.

   SQL 특성 테이블은 특성 유형에 따라 자동으로 작성됩니다.

   * 전용: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 공유: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   특성 필드에는 단일 값이 특성에 대해 인증되는 단순 oà¹ 필드와 특성이 여러 값을 포함할 수 있는 컬렉션 요소에 연결되는 oà¹ 다중 선택 필드의 두 가지 유형이 있습니다.

   스키마에 특성이 정의된 경우 이 스키마에는 단일 필드를 기반으로 하는 기본 키가 있어야 합니다(복합 키는 승인되지 않음).

* **featureDate (부울)**: &quot;@feature&quot; 특성 필드에 연결된 속성입니다. 값이 &quot;true&quot;이면 값이 마지막으로 업데이트된 시기를 알 수 있습니다.
* **img (문자열)**: 필드(네임스페이스 + 이미지 이름)에 연결된 이미지의 경로를 정의할 수 있습니다(예: img=&quot;cus:mypicture.jpg&quot;). 물리적으로 응용 프로그램 서버로 이미지를 가져와야 합니다.
* **레이블(문자열)**: 필드에 연결된 레이블로, 주로 인터페이스의 사용자에게 연결됩니다. 이름 지정 제한을 방지할 수 있습니다.
* **length (문자열)**: 최대 &quot;문자열&quot; 유형 SQL 필드의 값에 대한 문자 수입니다. &quot;@length&quot; 속성을 지정하지 않으면 Adobe Campaign에서 255자에 대한 필드를 자동으로 만듭니다.
* **현지화 가능(부울)**: 활성화되면 이 속성은 수집 툴에게 번역(내부 사용)을 위해 &quot;@label&quot; 속성 값을 복구하도록 알려줍니다.
* **이름(MNTOKEN)**: 테이블의 필드 이름과 일치하는 속성의 이름입니다. &quot;@name&quot; 속성의 값은 짧아야 하며, 영어가 가급적이면 XML 이름 지정 제한을 준수해야 합니다.

   스키마가 데이터베이스에 기록되면 Adobe Campaign에서 필드 이름에 접두사가 자동으로 추가됩니다.

   * &quot;i&quot;: &#39;정수&#39; 유형의 접두사입니다.
   * &quot;d&quot;: &#39;double&#39; 유형의 접두사입니다.
   * &quot;s&quot;: 문자열 유형의 접두사입니다.
   * &quot;ts&quot;: &#39;날짜&#39; 유형의 접두사입니다.

   테이블에서 필드의 이름을 완전히 정의하려면 속성을 정의할 때 &quot;@sqlname&quot; 옵션을 사용합니다.

* **notNull(부울)**: 데이터베이스의 NULL 레코드 관리와 관련된 Adobe Campaign의 동작을 재정의할 수 있습니다. 기본적으로 숫자 필드는 null이 아니며 문자열 및 날짜 유형 필드는 null일 수 있습니다.
* **pkgStatus(문자열)**: 패키지를 내보내는 동안 &quot;@pkgStatus&quot;의 값에 따라 값이 고려됩니다.

   * &quot;always&quot;: 항상 표시
   * &quot;절대 안 함&quot;: 절대 없음
   * &quot;default (또는 nothing)&quot;: 기본값이거나 다른 인스턴스와 호환되지 않는 내부 필드가 아닌 경우를 제외하고 값을 내보냅니다.

* **참조(문자열)**: 이 속성은 다음에 대한 참조를 정의합니다 `<attribute>` 여러 스키마에서 공유하는 요소(정의 팩토링). 정의가 현재 스키마에 복사되지 않습니다.
* **필수(부울)**: 이 속성이 활성화된 경우(@required=&quot;true&quot;) 인터페이스에서 필드가 강조 표시됩니다. 필드의 레이블은 양식에서 빨간색으로 표시됩니다.
* **sql(부울)**: 이 속성이 활성화되면(@sql=&quot;true&quot;), 속성이 포함된 요소에 xml=&quot;true&quot; 속성이 있더라도 SQL 속성을 강제로 저장합니다.
* **sqlDefault(문자열)**: 이 속성을 사용하면 @notNull 속성이 활성화된 경우 데이터베이스 업데이트를 위해 고려되는 기본값을 정의할 수 있습니다. 속성을 만든 후 이 속성을 추가하면 새 레코드에 대해서도 스키마 동작이 변경되지 않습니다. 스키마를 변경하고 새 레코드의 값을 업데이트하려면 속성을 삭제하고 다시 만들어야 합니다.
* **sqlname(문자열)**: 테이블을 만드는 동안 필드의 수입니다. @sqlname을 지정하지 않으면 기본적으로 &quot;@name&quot; 속성 값이 사용됩니다. 스키마가 데이터베이스에 작성되면 필드 유형에 따라 접두사가 자동으로 추가됩니다.
* **템플릿(문자열)**: 이 속성은 다음에 대한 참조를 정의합니다 `<attribute>` 여러 스키마에서 공유하는 요소입니다. 이 정의는 현재 스키마에 자동으로 복사됩니다.
* **translatedDefault (문자열)**: &quot;@default&quot; 속성이 발견되면 &quot;@translatedDefault&quot;를 사용하여 @default에 정의된 표현식과 일치하도록 표현식을 재정의하고 번역 도구로 수집할 수 있습니다(내부 사용).
* **translatedExpr (문자열)**: &quot;@expr&quot; 속성이 있는 경우 &quot;@translatedExpr&quot; 속성을 사용하면 표현식을 번역 도구에서 수집할 @expr에 정의된 것과 일치하도록 재정의할 수 있습니다(내부 사용).
* **유형(MNTOKEN)**: 필드 유형.

   필드 유형은 일반적입니다. 설치된 데이터베이스 유형에 따라 Adobe Campaign은 구조를 업데이트하는 동안 정의된 유형을 설치된 데이터베이스와 관련된 값으로 변경합니다.

   사용 가능한 유형 목록:

   * 모든
   * bin
   * blob
   * 부울
   * 바이트
   * C데이터
   * datetime
   * datetimetz
   * 다테티메노츠
   * date
   * 더블
   * enum
   * 부동
   * html
   * int64
   * 링크
   * 길게
   * 메모
   * MNTOKEN
   * percent
   * primarykey
   * 짧음
   * 문자열
   * 시간
   * timespan
   * uuid

   &quot;@type&quot; 속성을 비워 두면 Adobe Campaign은 기본적으로 길이가 100인 문자열(STRING)을 필드에 연결합니다.

   필드가 STRING 유형이고 &quot;@sqlname&quot; 특성이 있어 필드 이름을 지정하지 않으면 데이터베이스의 필드 이름 앞에 자동으로 &#39;s&#39;가 붙습니다. 이 운영 모드는 정수 (i), DOUBLE (d) 및 DATES (ts) 유형 필드와 유사합니다.

* **userEnum(문자열)**: &quot;열린&quot; 열거형의 내부 이름을 받습니다. 열거형의 값은 인터페이스에서 사용자가 정의할 수 있습니다.
* **visibleIf (문자열)**: 속성을 표시하거나 숨길 조건을 XTK 식 형식으로 정의합니다.

   >[!IMPORTANT]
   >
   >속성은 숨겨져 있지만 데이터는 계속 액세스할 수 있습니다.

* **xml (부울)**: 이 옵션이 활성화된 경우 필드의 값에 연결된 SQL 필드가 없습니다. Adobe Campaign은 레코드 스토리지용 텍스트 유형 &quot;mData&quot; 필드를 만듭니다. 즉, 이러한 필드에는 필터링이나 정렬이 없습니다.

### 예제 {#examples}

데이터베이스에 값이 저장된 열거형 값의 예:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>     
```

&quot;@datapolicy&quot;가 있는 XML 필드 선언:

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

&quot;@applicableIf&quot;을 사용하는 예: &quot;contains&quot; 속성은 국가 수가 20개보다 큰 경우에만 만들어집니다.

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

&quot;공유&quot; 유형의 &quot;@feature&quot;가 있는 예:

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

&quot;전용&quot; 유형의 &quot;@feature&quot;가 있는 예:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
