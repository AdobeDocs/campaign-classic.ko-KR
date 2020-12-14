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
source-wordcount: '2012'
ht-degree: 0%

---


# 요소 {#element--element}

## 컨텐트 모델 {#content-model-4}

요소:==(특성 | compute-string | dbindex | 기본값 | 요소 | 도움말 | 가입 | 키 | sysFilter | translatedDefault)

## 특성 {#attributes-4}

_operation(문자열), 고급(부울), 집계(문자열), 적용 가능한If(문자열), 자동(부울), convTo(문자열), convDate(문자열), dataPolicy(문자열), dataSource(문자열), dbEnum(문자열), defOnDuplicate(부울), 기본(문자열), displayAsField(문자열) boolean), doesNotSupportDiff(부울 값), 편집(문자열), 빈 키 값(문자열), 열거형(문자열), enumImage(문자열), expandSchemaTarget(문자열), externalJoin(문자열), externalJoin(부울), 기능(문자열), featureDate (문자열), filterLink(문자열), folderModel(문자열), folderProcess(문자열), fullLoad(부울 값), 계층적(부울 값), imgPath(문자열), inout(문자열), 무결성(문자열), 레이블(문자열), labelSingular(문자열), 길이(문자열), 지역화 가능(부울), 이름(MNTOKEN), noDbIndex(boolean), noNoNo키(부울), 순서가 지정된(부울), 오버플로우 테이블(부울), pkSequence(문자열), pkStatus(문자열), 참조(문자열), 필수(부울), revAdvanced(부울), revCardinality(문자열), revExternalJoin(boolean), revIntegrity(문자열), revLink (문자열), revTarget(문자열), revVisibleIf (문자열), sql(부울 값), sqlname(문자열), sqltable(문자열), tableSpace(문자열), tableSpaceIndex(문자열), 대상(MNTOKEN), 템플릿(문자열), translatedDefault(문자열), translatedExpr(문자열), type MNTOKEN), 언바운드(부울), 사용자(부울), userEnum(문자열), visibleIf (문자열), xml(부울), xmlChildren(boolean)

## 부모 {#parents-4}

`<srcschema>`

`<element>`

## 하위 {#children-4}

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

## 설명 {#description-4}

Adobe Campaign에는 4가지 유형의 `<element>` 요소가 있습니다.

* 루트 `<element>` :스키마와 일치하는 SQL 테이블의 이름을 정의합니다.
* 구조 `<element>` :`<element>` 그룹을 정의합니다.   or   `<attribute>`    요소를 참조하십시오.
* 링크 `<element>` :링크를 정의합니다. 이 요소에는 &quot;@type=link&quot; 속성이 포함되어야 합니다.
* XML `<element>` :텍스트 유형 &quot;mData&quot; 필드를 정의합니다. 이 요소에는 &quot;@type=xml&quot; 특성이 포함되어야 합니다.

## 특성 설명 {#attribute-description-4}

* **_operation(문자열)**:데이터베이스의 쓰기 유형을 정의합니다.

   이 속성은 기본적으로 기본 스키마를 확장할 때 사용됩니다.

   액세스 가능한 값은 다음과 같습니다.

   * &quot;없음&quot;:화해만. 즉, Adobe Campaign은 요소를 업데이트하지 않고 복구하거나 오류가 없는 경우 오류를 생성합니다.
   * &quot;insertOrUpdate&quot;:삽입으로 업데이트합니다. 즉, Adobe Campaign은 요소를 업데이트하거나 존재하지 않을 경우 요소를 만듭니다.
   * &quot;삽입&quot;:삽입. 즉, Adobe Campaign은 요소의 존재 여부를 확인하지 않고 요소를 삽입합니다.
   * &quot;업데이트&quot;:업데이트를 참조하십시오. 즉, Adobe Campaign은 요소를 업데이트하거나 존재하지 않을 경우 오류를 생성합니다.
   * &quot;삭제&quot;:삭제할 수 있습니다. 즉, Adobe Campaign은 요소를 복구 및 삭제합니다.

* **고급(부울)**:이 옵션이 활성화되면(@advanced=&quot;true&quot;) 양식에서 목록을 구성하기 위해 액세스할 수 있는 사용 가능한 필드 목록에서 속성을 숨길 수 있습니다.
* **집계(문자열)**:다른 스키마를  `<element>`  통해 정의를 복사할 수 있습니다. 이 속성은 &quot;namespace:name&quot; 형식의 스키마 선언을 받습니다.
* **applicableIf (string)**:인덱스를 적용하는 조건. 이 속성은 XTK 표현식을 받습니다.
* **자동(부울)**:이 옵션이 활성화된 경우(autk=&quot;true&quot;) 고유 키가 자동으로 정의됩니다. 이 옵션은 스키마의 주 요소에만 사용할 수 있습니다. 경고, Adobe Campaign은 생성된 키가 고유해야 합니다. 키 값이 연속적이고 증가한다는 것은 보장되지 않습니다.
* **dataPolicy(문자열)**:SQL 필드에 허용되는 값에 대한 승인 제한을 지정할 수 있습니다. 이 속성의 값은 다음과 같습니다.

   * &quot;없음&quot;:값 없음
   * &quot;smartCase&quot;:첫 글자 대문자 대문자
   * &quot;lowerCase&quot;:소문자
   * &quot;upperCase&quot;:모든 대문자
   * &quot;이메일&quot;:이메일 주소
   * &quot;phone&quot;:전화 번호
   * &quot;식별자&quot;:식별자 이름
   * &quot;resIdentifier&quot;:파일 이름

* **dbEnum(문자열)**:는 &quot;closed&quot; 열거형의 내부 이름을 받습니다. 열거형 값은 `<srcschema>`에 정의해야 합니다.
* **defOnDuplicate(부울)**:이 속성이 활성화되면 레코드가 중복되면(@default에 정의) 기본값이 자동으로 레코드에 다시 적용됩니다.
* **기본값(문자열)**:요소 비헤이비어를 정의할 수 있습니다(함수 호출, 기본값). 이 속성은 XTK 표현식을 받습니다.
* **desc(문자열)**:요소의 설명을 삽입할 수 있습니다. 이 설명은 인터페이스의 상태 표시줄에 표시됩니다.
* **displayAsField(부울)**:이 속성이 활성화되면 &quot;링크&quot; 유형이 스키마의 트리 보기에 필드로  `<element>`  표시됩니다(&quot;구조&quot; 탭). 이렇게 하면 링크를 로컬 필드로 표시하고 쿼리 도중 링크를 변경할 수 있습니다. 쿼리의 SELECT에 요소가 있으면 링크 대상의 값이 사용됩니다. 쿼리의 WHERE에 요소가 있으면 링크의 기본 키가 사용됩니다.
* **편집(문자열)**:이 속성은 스키마에 연결된 양식에 사용할 입력 유형을 지정합니다.
* **enum(문자열)**:은 필드에 연결된 열거형의 이름을 받습니다. 열거형은 동일한 스키마나 원격 스키마에 삽입할 수 있습니다.
* **expr(문자열)**:이 속성은 테이블에 정의가 저장되지 않는 계산된 필드를 정의합니다. Xpath 또는 XTK(문자열) 표현식을 수신합니다.
* **externalJoin(부울)**:&quot;링크&quot; 유형 요소의 외부 조인.
* **feature (string)**:특성 필드를 정의합니다.이러한 필드는 기존 테이블에서 데이터를 확장하지만 부록 테이블의 저장과 함께 사용됩니다. 허용된 값은 다음과 같습니다.

   * &quot;공유&quot;:내용은 데이터 유형별로 공유 테이블에 저장됩니다
   * &quot;전용&quot;:컨텐츠는 전용 테이블에 저장됩니다.

   SQL 특성 테이블은 특성 유형에 따라 자동으로 만들어집니다.

   * 전용:`Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 공유:`Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   두 가지 유형의 특성 필드가 있습니다.특성에 대해 단일 값이 인증되는 단순 필드와 여러 값이 포함될 수 있는 컬렉션 요소에 특성이 연결되어 있는 객관식 필드.

   스키마에서 특성이 정의되면 이 스키마에는 단일 필드를 기반으로 하는 기본 키가 있어야 합니다(복합 키는 인증되지 않음).

* **featureDate (boolean)**:&quot;@feature&quot; 특성 필드에 연결된 속성입니다. 값이 &quot;true&quot;이면 값이 마지막으로 업데이트된 시기를 알 수 있습니다.
* **filterPath(문자열)**:이 속성은 Xpath를 수신하고 필드에 필터를 정의할 수 있도록 해줍니다.
* **folderLink(문자열)**:이 속성은 엔티티가 포함된 파일을 복구할 수 있는 링크의 이름을 받습니다.
* **folderModel(문자열)**:엔티티 저장소를 사용할 수 있는 폴더 유형을 정의합니다. 이 속성은 &quot;@folderLink&quot;이 있는 경우에만 정의됩니다.
* **folderProcess(문자열)**:엔티티 모델 인스턴스가 저장되는 링크를 정의합니다. 이 속성은 &quot;@folderLink&quot;이 있는 경우에만 정의됩니다.
* **fullLoad(부울)**:이 속성은 폼에서 필드를 선택하는 동안 테이블의 모든 레코드를 강제로 표시합니다.
* **img (string)**:는 요소에 연결된 이미지의 경로를 받습니다. 이 속성의 값은 &quot;namespace:image name&quot; 유형입니다. 예:img=&quot;cus:myImage.jpg&quot; 물리적으로 이미지를 응용 프로그램 서버로 가져와야 합니다.
* **integrity (string)**:대상 테이블을 향한 소스 테이블 항목의 참조 무결성

   액세스 가능한 값은 다음과 같습니다.

   * &quot;정의&quot;:Adobe Campaign은 링크를 통해 참조되는 경우 엔티티를 삭제하지 않습니다.
   * &quot;보통&quot;:소스 발생을 삭제하면 대상 발생 시 링크의 키가 초기화됩니다(기본 모드). 이 무결성 유형은 모든 외래 키가 초기화됩니다
   * &quot;소유&quot;:소스 항목 삭제는 대상 항목의 삭제를 트리거합니다.
   * &quot;owncopy&quot;:&quot;소유&quot;(삭제의 경우) 또는 중복 항목(중복의 경우)과 유사
   * &quot;중립&quot;:아무 작업도 하지 않음

* **label (string)**:요소 레이블을 지정합니다.
* **labelSingular(문자열)**:인터페이스의 일부 부분에 사용되는 요소의 label(singular form).
* **length(문자열)**:max. &quot;string&quot; 유형의 SQL 필드에 대해 권한이 부여된 문자 수입니다.
* **localizable(boolean)**:활성화되면 이 속성은 번역(내부 사용)을 위해 &quot;@label&quot; 속성의 값을 복구하도록 컬렉션 도구에 지시합니다.
* **이름(MNTOKEN)**:테이블 이름과 일치하는 요소의 내부 이름입니다. &quot;@name&quot; 속성의 값은 짧아야 하며, 영어로만 사용할 수 있으며, XML에 연결된 이름 지정 제한을 준수해야 합니다.

   스키마가 데이터베이스에 기록되면 접두사가 Adobe Campaign에 의해 필드 이름에 자동으로 추가됩니다.

   * &quot;i&quot;:접두어를 사용합니다.
   * &quot;d&quot;:접두어가 &#39;double&#39; 유형입니다.
   * &quot;s&quot;:접두사를 사용합니다.
   * &quot;ts&quot;:&#39;date&#39; 유형의 접두어입니다.

   표 이름을 자율적인 방식으로 정의하려면 주 스키마 요소의 정의에 &quot;@sqltable&quot; 속성을 사용해야 합니다.

* **noDbIndex(부울)**:요소를 인덱싱하지 않도록 지정할 수 있습니다.
* **ordered(boolean)**:속성이 활성화되면(ordered=&quot;true&quot;) Adobe Campaign은 요소 선언 시퀀스를 XML 컬렉션 요소에 유지합니다.
* **pkSequence(문자열)**:는 자동 증분 키를 계산하는 데 사용할 시퀀스의 이름을 받습니다. 이 속성은 스키마의 루트 요소에 자동 증분 키가 정의된 경우에만 사용할 수 있습니다.
* **pkgStatus(문자열)**:패키지 내보내기 동안 값은 이 속성의 값 함수로 고려됩니다.

   * &quot;항상&quot;:요소는 항상 있습니다.
   * &quot;never&quot;:요소가 절대 존재하지 않습니다.
   * &quot;기본값(또는 없음)&quot;:요소가 기본 요소이거나 내부 필드가 아니며 다른 인스턴스와 호환되지 않는 경우를 제외하고 요소를 내보냅니다

* **ref(문자열)**:이 속성은 여러 스키마가 공유하는 >element> 요소에 대한 참조를 정의합니다(정의 팩토링). 정의가 현재 스키마에 복사되지 않습니다.
* **필수(부울)**:이 속성이 활성화되면(@required=&quot;true&quot;) 인터페이스에 필드가 강조 표시됩니다. 필드의 레이블은 빨간색으로 표시됩니다.
* **revAdvanced(부울)**:이 속성을 활성화하면 반대 링크가 &quot;고급&quot; 링크임을 지정합니다.
* **revCardinality(문자열)**:이 속성은 두 테이블 간의 링크의 기수를 정의합니다. &quot;링크&quot; 유형 `<element>`에 사용됩니다.

   가능한 값은 다음과 같습니다.

   * &quot;단일&quot; :간단한 1-1 유형 링크
   * &quot;언바운드&quot;:1-N 유형 컬렉션 링크

   기본적으로 링크를 만드는 동안 속성이 지정되지 않으면 기수는 1-N이 됩니다.

* **revDesc(문자열)**:이 속성은 반대 링크에 연결된 설명을 받습니다.
* **revExternalJoin(부울)**:이 속성을 활성화하면 반대 링크에서 외부 조인을 강제 적용할 수 있습니다.
* **revIntegrity(문자열)**:이 속성은 대상 스키마의 무결성을 정의합니다. &quot;@integrity&quot; 속성과 동일한 값이 인증됩니다. 기본적으로 Adobe Campaign은 이 속성에 &quot;normal&quot; 값을 제공합니다.
* **revLabel(문자열)**:반대 링크의 레이블.
* **revLink(문자열)**:반대 링크의 이름. 값이 &quot;_NONE_&quot;인 경우 대상 스키마에 반대 링크가 만들어지지 않습니다.
* **revTarget(문자열)**:의 대상이 됩니다.
* **sql(부울)**:이 속성이 활성화되면(@sql=&quot;true&quot;) 요소에 xml=&quot;true&quot; 속성이 있더라도 SQL 요소의 스토리지가 강제로 지정됩니다.
* **sqlname(문자열)**:테이블을 만드는 동안 필드의 이름입니다. &quot;@sqlname&quot;이 지정되지 않은 경우 기본적으로 &quot;@name&quot; 속성의 값이 사용됩니다. 스키마를 표에 쓸 때, 접두사는 필드 유형에 따라 자동으로 추가됩니다.
* **sqltable(문자열)**:스키마의 주 요소에 대해 이 속성은 기본적으로 생성된 SQL 테이블의 이름을 오버로드합니다. &quot;@sqltable&quot;이 지정되지 않은 경우 기본 이름은 다음과 같이 구조화됩니다.namespace(첫 번째 문자 대문자) 뒤에 SrcSchema &quot;@name&quot; 값이 옵니다.
* **tableSpace(문자열)**:이 속성을 사용하면 테이블에 대해 테이블스페이스를 저장하는 새 데이터를 지정할 수  `<element>`있습니다(루트에서 유효).
* **tableSpaceIndex(문자열)**:이 속성을 사용하면 테이블에 대한 새 인덱스 저장 영역 테이블스페이스를 지정할 수 있습니다(루트에서 유효).  `<element>`
* **target(MNTOKEN)**:는 테이블 간 링크를 만들 때 대상 스키마의 이름을 받습니다. 이 속성은 &quot;링크&quot; 유형 요소에만 활성화됩니다.
* **템플릿(문자열)**:이 속성은 여러 스키마가 공유하는  `<element>` 요소에 대한 참조를 정의합니다. 정의가 현재 스키마에 자동으로 복사됩니다.
* **translatedDefault(문자열)**:&quot;@default&quot; 속성이 발견되면 &quot;@translatedDefault&quot;을 사용하여 평행 이동 도구(내부 사용)로 수집될 @default에 정의된 표현식과 일치하도록 표현식을 재정의할 수 있습니다.
* **translatedExpr(문자열)**:&quot;@expr&quot; 속성이 있는 경우 &quot;@translatedExpr&quot; 속성을 사용하여 &quot;@expr&quot;에 정의된 표현식과 일치하는 표현식을 재정의할 수 있으며 이 표현식은 번역 도구(내부 사용)에 의해 수집됩니다.
* **유형(MNTOKEN)**:요소에 저장된 데이터의 유형을 정의합니다.

   사용 가능한 유형 목록:

   * 임의
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

* **언바운드(부울)**:속성이 활성화되면(unbound=&quot;true&quot;) 링크가 1-N 기수에 대한 컬렉션 요소로 선언됩니다.
* **userEnum(문자열)**:는 &quot;open&quot; 열거형의 내부 이름을 받습니다. 열거형 값은 인터페이스에서 사용자가 정의할 수 있습니다.
* **xml(부울)**:이 옵션을 활성화하면 요소에 정의된 모든 값이 텍스트 유형 &quot;mData&quot; 필드에 XML에 저장됩니다. 즉, 이러한 필드를 필터링하거나 정렬하지 않습니다.
* **xmlChildren(boolean)**:각 하위(  `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
