---
solution: Campaign Classic
product: campaign
title: 요소 및 속성
description: 요소 및 속성
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '1552'
ht-degree: 0%

---


# `<attribute>` 요소  {#attribute--element}

## 콘텐츠 모델 {#content-model}

attribute:==help

## 속성 {#attributes}

_operation (string), advanced (boolean), applableIf (string), autoIncrement(boolean), consistentTo (string), dataPolicy (string), defOnDuplicate (string), default (string), desc (string), edit (string), exr (string), featureDate (boolean) , img (문자열), inout (문자열), 레이블(문자열), 길이(문자열), 지역화가능(부울 값), 이름(MNTOKEN), notNull(부울), pkgStatus(문자열), 참조(문자열), 필수(부울), sqlDefault(문자열), sqlname(문자열), sqltable(문자열), target(MNTOKEN), 템플릿), translatedDefault(문자열), translatedExpr(문자열), type(MNTOKEN), user(boolean), userEnum(string), visibleIf (string), xml(boolean)

## 부모 {#parents}

`<element>`

## 하위 {#children}

`<help>`

## 설명 {#description}

`<attribute>` 요소를 사용하면 데이터베이스에서 필드를 정의할 수 있습니다.

## {#use-and-context-of-use} 사용 및 컨텍스트

`<attribute>` 요소는  `<element>` 요소로 선언해야 합니다.

`<attribute>` 요소가 `<srcschema>`에 정의된 시퀀스는 데이터베이스의 필드 생성 시퀀스에 영향을 주지 않습니다. 작성 시퀀스는 알파벳 순으로 표시됩니다.

## 특성 설명 {#attribute-description}

* **_operation(문자열)**:데이터베이스의 쓰기 유형을 정의합니다.

   이 속성은 기본적으로 기본 스키마를 확장할 때 사용됩니다.

   액세스 가능한 값은 다음과 같습니다.

   * &quot;none&quot;:혼자서. 즉, Adobe Campaign은 요소를 업데이트하지 않고 복구하거나 오류가 없는 경우 오류를 발생시킵니다.
   * &quot;insertOrUpdate&quot;:업데이트를 삽입하여 사용하십시오. 즉, Adobe Campaign이 요소를 업데이트하거나 존재하지 않을 경우 요소를 만듭니다.
   * &quot;삽입&quot;:삽입. 이것은 Adobe Campaign이 요소의 존재 여부를 확인하지 않고 요소를 삽입한다는 것을 의미합니다.
   * &quot;업데이트&quot;:업데이트. 즉, Adobe Campaign에서 요소를 업데이트하거나 존재하지 않을 경우 오류를 생성합니다.
   * &quot;삭제&quot;:삭제. 이는 Adobe Campaign이 요소를 복구하고 삭제할 것임을 의미합니다.

* **고급(부울)**:이 옵션을 활성화하면(@advanced=&quot;true&quot;) 양식에서 목록을 구성하기 위해 액세스할 수 있는 사용 가능한 필드 목록에서 속성을 숨길 수 있습니다.
* **applicableIf (string)**:이 속성을 사용하면 필드를 선택 사항으로 만들 수 있습니다. 제약 조건을 준수하면 데이터베이스를 업데이트할 때 `<attribute>` 요소를 고려합니다. &quot;applableIf&quot;는 XTK 표현식을 받습니다.
* **autoIncrement(부울)**:이 옵션을 활성화하면 필드가 카운터가 됩니다. 이를 통해 값(대부분 ID)을 늘릴 수 있습니다. (외부 사용)
* **containsTo (string)**:필드를 공유하는 테이블의 이름과 네임스페이스를 가져와서 속성이 선언되는 스키마를 채웁니다. ( `<schema>`에서만 사용됨)
* **dataPolicy(문자열)**:SQL 또는 XML 필드에 허용되는 값에 대한 승인 제한을 지정할 수 있습니다. 이 속성의 값은 다음과 같습니다.

   * &quot;none&quot;:값 없음
   * &quot;smartCase&quot;:첫 글자 대문자
   * &quot;lowerCase&quot;:소문자
   * &quot;upperCase&quot;:모든 대문자
   * &quot;이메일&quot;:이메일 주소
   * &quot;phone&quot;:전화 번호
   * &quot;identifier&quot;:식별자 이름
   * &quot;resIdentifier&quot;:파일 이름

* **dbEnum(문자열)**:는 &quot;closed&quot; 열거형의 내부 이름을 받습니다. 열거형 값은 `<srcschema>`에 정의해야 합니다.
* **defOnDuplicate(부울)**:이 속성을 활성화하면 레코드가 중복되면(@default에 정의됨) 기본값이 자동으로 레코드에 다시 적용됩니다.
* **default(string)**:기본 필드의 값을 정의할 수 있습니다(함수 호출, 기본값). 이 속성은 XTK 표현식을 받습니다.
* **desc(문자열)**:속성 설명을 삽입할 수 있습니다. 이 설명은 인터페이스의 상태 표시줄에 표시됩니다.
* **edit (string)**:이 속성은 스키마에 연결된 양식에서 사용할 입력 유형을 지정합니다.
* **enum(문자열)**:은 필드에 연결된 열거형의 이름을 받습니다. 열거를 동일한 스키마나 원격 스키마에 삽입할 수 있습니다.
* **expr(문자열)**:필드 사전 계산 표현식을 정의합니다. 이 속성은 Xpath 또는 XTK 표현식을 받습니다.
* **feature (string)**:특성 필드를 정의합니다.이러한 필드는 기존 테이블의 데이터를 확장하지만 부록 테이블의 저장과 함께 사용됩니다. 허용된 값은 다음과 같습니다.

   * &quot;공유&quot;:컨텐츠는 데이터 유형별로 공유 테이블에 저장됩니다
   * &quot;전용&quot;:컨텐츠는 전용 테이블에 저장됩니다.

   SQL 특성 테이블은 특성 유형에 따라 자동으로 만들어집니다.

   * 전용:`Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 공유:`Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   두 가지 유형의 특성 필드가 있습니다.특성이 여러 값이 포함될 수 있는 컬렉션 요소에 연결된 경우 단일 값이 특성에 대해 허가된 단순 다중 선택 필드 및 다중 선택 필드 다중 선택 필드

   스키마에서 특성이 정의되면 이 스키마에는 단일 필드를 기반으로 하는 기본 키가 있어야 합니다(복합 키는 인증되지 않음).

* **featureDate(부울 값)**:특성 &quot;@feature&quot; 특성 필드에 연결되어 있습니다. 값이 &quot;true&quot;이면 값이 마지막으로 업데이트된 시기를 알 수 있습니다.
* **img(문자열)**:필드에 연결된 이미지의 경로를 정의할 수 있습니다(네임스페이스 + 이미지 이름)(예:img=&quot;cus:mypicture.jpg&quot;). 실제 이미지는 애플리케이션 서버로 가져와야 합니다.
* **label (string)**:필드에 연결된 레이블로, 대부분 인터페이스에서 사용자에게 지정됨. 이를 통해 이름 지정 제한을 방지할 수 있습니다.
* **length(문자열)**:max. &quot;문자열&quot; 유형 SQL 필드의 값에 대한 문자 수입니다. &quot;@length&quot; 속성을 지정하지 않으면 Adobe Campaign은 255자 필드를 자동으로 만듭니다.
* **localable(boolean)**:활성화되면 이 속성은 번역(내부 사용)을 위해 &quot;@label&quot; 속성의 값을 복구하도록 컬렉션 도구에 지시합니다.
* **이름(MNTOKEN)**:테이블의 필드 이름과 일치하는 속성의 이름입니다. &quot;@name&quot; 특성 값은 짧아야 하며, 특히 영어로 되어야 하며 XML 이름 지정 제한을 준수해야 합니다.

   스키마가 데이터베이스에 작성되면, 접두사는 Adobe Campaign에 의해 필드 이름에 자동으로 추가됩니다.

   * &quot;i&quot;:접두사를 사용합니다.
   * &quot;d&quot;:접두사를 사용합니다.
   * &quot;s&quot;:접두사를 사용합니다.
   * &quot;ts&quot;:접두사를 사용합니다.

   테이블의 필드 이름을 완전히 정의하려면 속성을 정의할 때 &quot;@sqlname&quot; 옵션을 사용합니다.

* **notNull(부울)**:데이터베이스의 NULL 레코드 관리와 관련된 Adobe Campaign 동작을 재정의할 수 있습니다. 기본적으로 숫자 필드는 null이 아니며 문자열 및 날짜 유형 필드는 null일 수 있습니다.
* **pkgStatus(문자열)**:패키지 내보내기 동안 값은 &quot;@pkgStatus&quot;의 값에 따라 고려됩니다.

   * &quot;always&quot;:항상
   * &quot;never&quot;:존재하지 않음
   * &quot;default (or nothing)&quot;:값이 기본값이거나 다른 인스턴스와 호환되지 않는 내부 필드가 아닌 경우를 제외하고 내보내집니다.

* **ref(문자열)**:이 속성은 여러 스키마가 공유하는  `<attribute>` 요소에 대한 참조를 정의합니다(정의 팩토링). 정의가 현재 스키마에 복사되지 않습니다.
* **필수(부울 값)**:이 속성이 활성화되면(@required=&quot;true&quot;) 인터페이스에 필드가 강조 표시됩니다. 필드의 레이블은 빨간색으로 표시됩니다.
* **sql(부울)**:이 특성이 활성화된 경우(@sql=&quot;true&quot;), 특성이 포함된 요소에 xml=&quot;true&quot; 속성이 있는 경우에도 SQL 속성의 저장소를 강제로 유지합니다.
* **sqlDefault(문자열)**:이 속성을 사용하면 @notNull 특성이 활성화된 경우 데이터베이스를 업데이트하는 데 고려되는 기본값을 정의할 수 있습니다. 속성 생성 후 이 속성을 추가하면 새 레코드에 대해서도 스키마 동작이 변경되지 않습니다. 스키마를 변경하고 새 레코드의 값을 업데이트하려면 속성을 삭제하고 다시 만들어야 합니다.
* **sqlname(문자열)**:을 클릭합니다. @sqlname이 지정되지 않은 경우 기본적으로 &quot;@name&quot; 속성의 값이 사용됩니다. 데이터베이스에 스키마를 작성할 때 접두사는 필드 유형에 따라 자동으로 추가됩니다.
* **템플릿(문자열)**:이 속성은 여러 스키마가 공유하는  `<attribute>` 요소에 대한 참조를 정의합니다. 정의가 현재 스키마에 자동으로 복사됩니다.
* **translatedDefault(문자열)**:&quot;@default&quot; 특성이 있는 경우, &quot;@translatedDefault&quot;를 사용하면 번역 도구(내부 사용)에서 수집할 @default에 정의된 표현식과 일치하도록 표현식을 재정의할 수 있습니다.
* **translatedExpr(문자열)**:&quot;@expr&quot; 특성이 있는 경우, &quot;@translatedExpr&quot; 속성을 사용하면 번역 도구(내부 사용)에서 수집할 표현식을 @expr에 정의된 표현식과 일치하도록 재정의할 수 있습니다.
* **유형(MNTOKEN)**:필드 유형.

   필드 유형은 일반적입니다. 설치된 데이터베이스 유형에 따라, Adobe Campaign은 정의된 유형을 구조 업데이트 중에 설치된 데이터베이스 고유의 값으로 변경합니다.

   사용 가능한 유형 목록:

   * ANY
   * bin
   * 물방울
   * boolean
   * byte
   * CDATA
   * datetime
   * datetimez
   * datetimenotz
   * date
   * 이중
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
   * 시간
   * timpan
   * uuid

   &quot;@type&quot; 특성이 비어 있는 경우, 기본적으로 길이가 100인 문자열(STRING)을 필드에 연결합니다.

   필드가 STRING 유형이고 필드 이름이 &quot;@sqlname&quot; 특성이 있는 경우 데이터베이스의 필드 이름 앞에 &#39;s&#39;가 자동으로 표시됩니다. 이 운영 모드는 INTEGER(i), DOUBLE(d) 및 DATES(ts) 유형 필드와 유사합니다.

* **userEnum(문자열)**:은 &quot;open&quot; 열거형의 내부 이름을 받습니다. 열거형 값은 인터페이스에서 사용자가 정의할 수 있습니다.
* **visibleIf (string)**:속성을 표시하거나 숨길 조건을 XTK 표현식 형태로 정의합니다.

   >[!IMPORTANT]
   >
   >속성은 숨겨지지만 해당 데이터는 여전히 액세스할 수 있습니다.

* **xml(부울)**:이 옵션을 활성화하면 필드 값에 연결된 SQL 필드가 없습니다. Adobe Campaign은 레코드 저장을 위한 텍스트 유형 &quot;mData&quot; 필드를 만듭니다. 즉, 이러한 필드를 필터링하거나 정렬하지 않습니다.

### 예제 {#examples}

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

예: &quot;@applicableIf&quot;&quot;contains&quot; 속성은 국가 수가 20개 이상인 경우에만 생성됩니다.

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

&quot;shared&quot; 유형의 &quot;@feature&quot;가 있는 예:

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

&quot;dedicated&quot; 유형의 &quot;@feature&quot;가 있는 예:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
