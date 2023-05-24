---
product: campaign
title: 스키마 요소 및 속성 - 요소 요소
description: 요소 요소
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '2014'
ht-degree: 0%

---

# 요소 요소 {#element--element}

![](../../../assets/v7-only.svg)

## 콘텐츠 모델 {#content-model-4}

element:==(attribute | 계산 문자열 | dbindex | 기본값 | 요소 | 도움말 | 참가 | 키 | sysFilter | translatedDefault)

## 속성 {#attributes-4}

_operation (string), advanced (부울), aggregate (문자열), applicableIf (문자열), autopk (부울), assetsTo (문자열), convDate (문자열), dataPolicy (문자열), dataSource (문자열), dbEnum (문자열), defOnDuplicate (부울), default (문자열), desc (문자열), displayAsField (부울), doesNotSupportDiff (부울), edit (문자열), emptyKeyValue (문자열), enum (문자열), enumImage (문자열), expand (문자열), externalJoin (부울), feature (문자열), featureDate (부울), filterPath (문자열), folderLink) , folderModel(string), folderProcess(string), fullLoad(부울), hierarchical(부울), hierarchicalPath(문자열), img(문자열), inout(문자열), integrity(문자열), label(문자열), labelSingular(문자열), length(문자열), localizable(부울), name(MNTOKEN), noDbIndex(부울), noKey(부울), ordered(부울), overflowtable(부울), pkSequence(문자열), pkgStatus(문자열), ref(문자열), required(부울), revAdvanced(부울), revCardinality(문자열), revDesc(문자열), revIntegrity(문자열) link (string), revTarget (string), revVisibleIf (string), sql (부울), sqlname (문자열), sqltable (문자열), tableSpace (문자열), tableSpaceIndex (문자열), target (MNTOKEN), template (문자열), temporaryTable (부울), translatedDefault (문자열), translatedExpr (문자열), type (MNTOKEN), unbound (부울), user (부울), userEnum (문자열), visibleIf (문자열), xml (부울), xmlChildren (부울)

## 상위 {#parents-4}

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

다음 네 가지 유형이 있습니다 `<element>`  Adobe Campaign 요소:

* 루트 `<element>`  : 스키마와 일치하는 SQL 테이블의 이름을 정의합니다.
* 구조 `<element>`  : 다음 그룹을 정의합니다.  `<element>`   또는   `<attribute>`    요소.
* 링크 `<element>`  : 링크를 정의합니다. 이 요소에는 &quot;@type=link&quot; 속성이 포함되어야 합니다.
* XML `<element>`  : 텍스트 유형 &quot;mData&quot; 필드를 정의합니다. 이 요소에는 &quot;@type=xml&quot; 특성이 포함되어야 합니다.

## 속성 설명 {#attribute-description-4}

* **작업(문자열)(_o)**: 데이터베이스에 쓰는 유형을 정의합니다.

   이 속성은 기본 제공 스키마를 확장할 때 주로 사용됩니다.

   액세스 가능한 값은 다음과 같습니다.

   * &quot;none&quot;: 조정만 가능합니다. 즉, Adobe Campaign은 요소가 존재하지 않는 경우 해당 요소를 업데이트하거나 오류를 생성하지 않고 요소를 복구합니다.
   * &quot;insertOrUpdate&quot;: 삽입을 사용하여 업데이트합니다. 즉, Adobe Campaign이 요소를 업데이트하거나 존재하지 않는 경우 만듭니다.
   * &quot;insert&quot;: 삽입. 즉, Adobe Campaign은 요소의 존재 여부를 확인하지 않고 요소를 삽입합니다.
   * &quot;update&quot;: update. 즉, Adobe Campaign이 요소를 업데이트하거나 존재하지 않는 경우 오류를 생성합니다.
   * &quot;delete&quot;: 삭제. 즉, Adobe Campaign에서 요소를 복구하고 삭제합니다.

* **advanced(부울)**: 이 옵션이 활성화되면(@advanced=&quot;true&quot;) 양식에서 목록을 구성하는 데 액세스할 수 있는 사용 가능한 필드 목록에서 속성을 숨길 수 있습니다.
* **집계(문자열)**: 의 정의를 복사할 수 있도록 해줍니다. `<element>`  다른 스키마를 통해. 이 속성은 &quot;namespace:name&quot; 형식의 스키마 선언을 받습니다.
* **applicableIf (문자열)**: 인덱스를 적용하는 조건. 이 속성은 XTK 식을 받습니다.
* **autopk (부울)**: 이 옵션이 활성화되면(autopk=&quot;true&quot;) 고유 키가 자동으로 정의됩니다. 이 옵션은 스키마의 기본 요소에서만 사용할 수 있습니다. 경고: Adobe Campaign은 생성된 키가 고유하다는 것만 보장합니다. 키 값이 연속적이고 점진적으로 변환되는 것은 보장되지 않습니다.
* **dataPolicy(문자열)**: SQL 필드에 허용되는 값에 대한 승인 제약 조건을 지정할 수 있습니다. 이 속성의 값은 다음과 같습니다.

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
* **기본값(문자열)**: 요소 동작(함수 호출, 기본값)을 정의할 수 있습니다. 이 속성은 XTK 식을 받습니다.
* **desc(문자열)**: 요소에 대한 설명을 삽입할 수 있습니다. 이 설명은 인터페이스의 상태 표시줄에 표시됩니다.
* **displayAsField(부울)**: 이 속성이 활성화된 경우 &quot;link&quot; 유형 `<element>`  스키마의 트리 보기(&quot;구조&quot; 탭)에 필드로 표시됩니다. 이렇게 하면 링크를 로컬 필드로 표시하고 쿼리 중에 해당 동작을 변경할 수 있습니다. 쿼리의 SELECT에서 요소를 찾으면 링크 대상의 값이 사용됩니다. 요소가 쿼리의 WHERE에 있으면 링크의 기본 키가 사용됩니다.
* **편집(문자열)**: 이 속성은 스키마에 연결된 양식에서 사용될 입력 유형을 지정합니다.
* **enum(문자열)**: 필드에 연결된 열거형의 이름을 받습니다. 열거형은 동일한 스키마에 삽입하거나 원격 스키마에 삽입할 수 있습니다.
* **expr (문자열)**: 이 속성은 테이블에 저장된 정의가 없는 계산된 필드를 정의합니다. Xpath 또는 XTK(문자열) 표현식을 받습니다.
* **externalJoin(부울)**: &quot;link&quot; 유형 요소의 외부 조인
* **기능(문자열)**: 특성 필드 정의: 이러한 필드는 기존 테이블에서 데이터를 확장하는 데 사용되지만 별도 테이블에는 저장소가 제공됩니다. 허용되는 값은 다음과 같습니다.

   * &quot;shared&quot;: 컨텐츠는 데이터 유형별로 공유 테이블에 저장됩니다
   * &quot;전용&quot;: 컨텐츠가 전용 테이블에 저장됩니다.

   SQL 특성 테이블은 특성 유형에 따라 자동으로 작성됩니다.

   * 전용: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 공유: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   특성 필드에는 특성에서 단일 값이 인증되는 단순 필드와 여러 값을 포함할 수 있는 컬렉션 요소에 특성이 연결되는 다중 선택 필드의 두 가지 유형이 있습니다.

   스키마에 특성이 정의된 경우 이 스키마에는 단일 필드를 기반으로 하는 기본 키가 있어야 합니다(복합 키는 승인되지 않음).

* **featureDate (부울)**: &quot;@feature&quot; 특성 필드에 연결된 속성입니다. 값이 &quot;true&quot;이면 값이 마지막으로 업데이트된 시기를 알 수 있습니다.
* **filterPath (문자열)**: 이 속성은 Xpath를 수신하며 필드에 필터를 정의할 수 있도록 합니다.
* **folderLink (string)**: 이 속성은 엔티티가 포함된 파일을 복구할 수 있는 링크의 이름을 받습니다.
* **folderModel (string)**: 엔티티 저장소를 활성화하는 폴더 유형을 정의합니다. 이 속성은 &quot;@folderLink&quot;가 있는 경우에만 정의됩니다.
* **folderProcess (string)**: 엔티티 모델 인스턴스가 저장되는 링크를 정의합니다. 이 속성은 &quot;@folderLink&quot;가 있는 경우에만 정의됩니다.
* **fullLoad (부울)**: 이 속성은 양식에서 필드를 선택하는 동안 테이블의 모든 레코드를 강제로 표시합니다.
* **img (문자열)**: 요소에 연결된 이미지의 경로를 받습니다. 이 속성의 값은 &quot;namespace:image name&quot; 유형입니다. 예: img=&quot;cus:myImage.jpg&quot;. 물리적으로 응용 프로그램 서버로 이미지를 가져와야 합니다.
* **무결성(문자열)**: 대상 테이블에 대한 소스 테이블 발생에 대한 참조 무결성.

   액세스 가능한 값은 다음과 같습니다.

   * &quot;define&quot;: Adobe Campaign은 링크를 통해 참조되는 엔티티를 삭제하지 않습니다
   * &quot;보통&quot;: 소스 발생 항목을 삭제하면 대상 발생 시 링크의 키가 초기화됩니다(기본 모드). 이 유형의 무결성은 모든 외래 키를 초기화합니다.
   * &quot;own&quot;: 소스 발생 항목을 삭제하면 대상 발생 항목의 삭제가 트리거됩니다.
   * &quot;owncopy&quot;: &quot;own&quot;(삭제 시)과 유사하거나 발생 항목을 중복(복제 시)합니다.
   * &quot;neutral&quot;: 아무 작업도 하지 않음

* **레이블(문자열)**: 요소 레이블입니다.
* **labelSingular(문자열)**: 인터페이스의 일부 부분에서 사용되는 요소의 레이블(단일 형식).
* **length (문자열)**: 최대 &quot;문자열&quot; 유형 SQL 필드의 값에 대해 승인된 문자 수입니다.
* **현지화 가능(부울)**: 활성화되면 이 속성은 수집 툴에게 번역(내부 사용)을 위해 &quot;@label&quot; 속성 값을 복구하도록 알려줍니다.
* **이름(MNTOKEN)**: 테이블 이름과 일치하는 요소의 내부 이름입니다. &quot;@name&quot; 속성 값은 짧아야 하며, 영어여야 하고, XML에 연결된 이름 지정 제약 조건을 준수해야 합니다.

   스키마가 데이터베이스에 기록되면 Adobe Campaign에서 필드 이름에 접두사가 자동으로 추가됩니다.

   * &quot;i&quot;: &#39;정수&#39; 유형의 접두사입니다.
   * &quot;d&quot;: &#39;double&#39; 유형의 접두사입니다.
   * &quot;s&quot;: 문자열 유형의 접두사입니다.
   * &quot;ts&quot;: &#39;날짜&#39; 유형의 접두사입니다.

   테이블 이름을 자동 방식으로 정의하려면 기본 스키마 요소의 정의에 &quot;@sqltable&quot; 속성을 사용해야 합니다.

* **noDbIndex(부울)**: 요소가 색인화되지 않도록 지정할 수 있습니다.
* **ordered (부울)**: 속성이 활성화(ordered=&quot;true&quot;)되면 Adobe Campaign은 XML 컬렉션 요소에 요소 선언 시퀀스를 유지합니다.
* **pkSequence(문자열)**: 자동 증분 키 계산에 사용할 시퀀스의 이름을 받습니다. 이 속성은 자동 증분 키가 스키마의 루트 요소에 정의된 경우에만 사용할 수 있습니다.
* **pkgStatus(문자열)**: 패키지를 내보내는 동안 값이 이 속성 값의 함수로 고려됩니다.

   * &quot;always&quot;: 요소가 항상 존재합니다.
   * &quot;never&quot;: 요소가 존재하지 않습니다.
   * &quot;default (또는 nothing)&quot;: 기본 요소가 아니거나 내부 필드가 아니며 다른 인스턴스와 호환되지 않는 경우 요소를 내보냅니다

* **참조(문자열)**: 이 속성은 여러 스키마에서 공유하는 >element> 요소에 대한 참조를 정의합니다(정의 팩토링). 정의가 현재 스키마에 복사되지 않습니다.
* **필수(부울)**: 이 속성이 활성화된 경우(@required=&quot;true&quot;) 인터페이스에서 필드가 강조 표시됩니다. 필드의 레이블은 양식에서 빨간색으로 표시됩니다.
* **revAdvanced(부울)**: 활성화되면 이 속성은 반대편 링크가 &quot;고급&quot; 링크임을 지정합니다.
* **revCardinality(문자열)**: 이 속성은 두 테이블 간의 링크 카디널리티를 정의합니다. 링크 유형에 사용됩니다. `<element>`.

   가능한 값:

   * &quot;단일&quot; : 단순 1-1 유형 링크
   * &quot;unbound&quot;: 1-N 유형 컬렉션 링크

   링크를 만드는 동안 특성이 지정되지 않으면 기본적으로 카디널리티는 1-N이 됩니다.

* **revDesc (문자열)**: 이 속성은 반대편 링크에 연결된 설명을 수신합니다.
* **revExternalJoin(부울)**: 활성화되면 반대편 링크에 외부 조인을 강제 적용할 수 있습니다.
* **revIntegrity (문자열)**: 이 속성은 대상 스키마의 무결성을 정의합니다. &quot;@integrity&quot; 속성과 동일한 값이 승인됩니다. 기본적으로 Adobe Campaign은 이 속성에 &quot;normal&quot; 값을 제공합니다.
* **revLabel(문자열)**: 반대 링크의 레이블입니다.
* **revLink (문자열)**: 반대 링크의 이름입니다. 값이 &quot;인 경우&#x200B;_없음_&quot;. 대상 스키마에 반대 링크가 만들어지지 않습니다.
* **revTarget (문자열)**: 반대 링크의 대상.
* **sql(부울)**: 이 속성이 활성화된 경우(@sql=&quot;true&quot;) 요소에 xml=&quot;true&quot; 속성이 있더라도 SQL 요소를 강제로 저장합니다.
* **sqlname(문자열)**: 테이블을 만드는 동안 필드의 이름. &quot;@sqlname&quot;을 지정하지 않으면 기본적으로 &quot;@name&quot; 속성 값이 사용됩니다. 테이블에 스키마를 쓸 때 필드 유형에 따라 접두사가 자동으로 추가됩니다.
* **sqltable(문자열)**: 스키마의 기본 요소에 대해 이 속성은 기본적으로 생성된 SQL 테이블의 이름을 오버로드합니다. &quot;@sqltable&quot;을 지정하지 않으면 기본 이름이 namespace(첫 번째 글자 대문자), SrcSchema &quot;@name&quot; 값이 차례로 옵니다.
* **tableSpace(문자열)**: 이 속성을 사용하면 테이블에 대한 테이블스페이스를 저장하는 새 데이터를 지정할 수 있습니다(루트에서 유효) `<element>`).
* **tableSpaceIndex(문자열)**: 이 속성을 사용하면 테이블에 대한 새 인덱스 저장 영역 테이블스페이스를 지정할 수 있습니다(루트에서 유효) `<element>`).
* **대상(MNTOKEN)**: 테이블 간에 링크를 만들 때 대상 스키마의 이름을 받습니다. 이 속성은 &quot;link&quot; 유형 요소에만 활성화됩니다.
* **템플릿(문자열)**: 이 속성은 다음에 대한 참조를 정의합니다 `<element>` 여러 스키마에서 공유하는 요소입니다. 이 정의는 현재 스키마에 자동으로 복사됩니다.
* **translatedDefault (문자열)**: &quot;@default&quot; 속성이 발견되면 &quot;@translatedDefault&quot;를 사용하여 @default에 정의된 표현식과 일치하도록 표현식을 재정의하고 번역 도구로 수집할 수 있습니다(내부 사용).
* **translatedExpr (문자열)**: &quot;@expr&quot; 속성이 발견되면 &quot;@translatedExpr&quot; 속성을 사용하여 &quot;@expr&quot;에 정의된 표현식과 일치하는 표현식을 재정의할 수 있으며, 이는 번역 도구로 수집됩니다(내부 사용).
* **유형(MNTOKEN)**: 요소에 저장되는 데이터의 유형을 정의합니다.

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

* **바인딩되지 않음(부울)**: 속성이 활성화된 경우(unbound=&quot;true&quot;) 링크는 1-N 카디널리티에 대한 컬렉션 요소로 선언됩니다.
* **userEnum(문자열)**: &quot;열린&quot; 열거형의 내부 이름을 받습니다. 열거형 값은 인터페이스에서 사용자가 정의할 수 있습니다.
* **xml (부울)**: 이 옵션이 활성화되면 요소에 정의된 모든 값이 TEXT type &quot;mData&quot; 필드의 XML에 저장됩니다. 즉, 이러한 필드에는 필터링이나 정렬이 수행되지 않습니다.
* **xmlChildren(부울)**: 각 하위 항목에 대해 스토리지를 강제 적용합니다( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
