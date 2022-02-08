---
product: campaign
title: 스키마 요소 및 속성
description: 요소 요소
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '2012'
ht-degree: 0%

---

# 요소 요소 {#element--element}

![](../../../assets/v7-only.svg)

## 컨텐츠 모델 {#content-model-4}

요소:==(속성) | 계산 문자열 | dbindex | 기본값 | 요소 | 도움말 | 가입 | 키 | sysFilter | translatedDefault)

## 속성 {#attributes-4}

_operation(문자열), 고급(부울), 집계(문자열), 적용 가능한 경우(문자열), autok(부울), convTo(문자열), convDate(문자열), dataSource(문자열), dataSource(문자열), dbEnum(문자열), defOnDuplicate(문자열), 기본값(문자열), desc(문자열), displayAsField(부울), 편집(문자열), 비어 있는 KeyValue(문자열), 확장(스키마 문자열), 확장(문자열) Target(문자열), expr(문자열), externalJoin(부울), 기능(문자열), featureDate(부울), filterPath(문자열), folderLink(문자열), folderModel(문자열), folderProcess(문자열), fullLoad(부울), hierarchicalPath(문자열), inout(문자열), integrity(문자열), label(문자열), labelSingular(문자열), length(부울), name(부울), name(MNDB), index(noIndex), Index(index) 키(부울), 순차(부울), 오버플로우테이블(부울), pkSequence(문자열), pkStatus(문자열), ref(문자열), 필수(부울), revAdvanced(부울), revCardinality(문자열), revExternalJoin(문자열), revIntegrity(문자열), revLink(문자열), revTarget(문자열), revVisibleIf(문자열), sql(부울), sqlname(테이블 문자열), 테이블 문자열), string SpaceIndex(문자열), target(MNTOKEN), 템플릿(문자열), 임시 테이블(부울), translatedDefault(문자열), translatedExpr(문자열), 유형(MNTOKEN), 언바운드(부울), 사용자(부울), userEnum(문자열), visibleIf(문자열), xml(부울), xmlChildren(부울)

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

네 가지 유형이 있습니다 `<element>`  Adobe Campaign의 요소:

* 루트 `<element>`  : 는 스키마와 일치하는 SQL 테이블의 이름을 정의합니다.
* 구조 `<element>`  : 그룹 정의  `<element>`   또는   `<attribute>`    요소를 생성하지 않습니다.
* 링크 `<element>`  : 링크를 정의합니다. 이 요소에는 &quot;@type=link&quot; 속성이 포함되어야 합니다.
* XML `<element>`  : 텍스트 유형 &quot;mData&quot; 필드를 정의합니다. 이 요소에는 &quot;@type=xml&quot; 특성이 포함되어야 합니다.

## 속성 설명 {#attribute-description-4}

* **_operation(문자열)**: 데이터베이스의 쓰기 유형을 정의합니다.

   이 속성은 주로 기본 스키마를 확장할 때 사용됩니다.

   액세스 가능한 값은 다음과 같습니다.

   * &quot;none&quot;: 화해만. 즉, Adobe Campaign은 요소를 업데이트하지 않고 요소를 복구하거나 존재하지 않을 경우 오류를 생성합니다.
   * &quot;insertOrUpdate&quot;: 삽입으로 업데이트합니다. 즉, Adobe Campaign은 요소가 없으면 요소를 업데이트하거나 만듭니다.
   * &quot;insert&quot;: 삽입 광고. 즉, Adobe Campaign이 요소 존재 여부를 확인하지 않고 요소를 삽입합니다.
   * &quot;update&quot;: 업데이트합니다. 즉, Adobe Campaign이 요소를 업데이트하거나 요소가 없는 경우 오류를 생성합니다.
   * &quot;delete&quot;: 삭제 즉, Adobe Campaign이 요소를 복구 및 삭제합니다.

* **고급(부울)**: 이 옵션이 활성화되면(@advanced=&quot;true&quot;) 양식의 목록을 구성하기 위해 액세스할 수 있는 사용 가능한 필드 목록에서 속성을 숨길 수 있습니다.
* **집계(문자열)**: 의 정의를 복사할 수 있습니다 `<element>`  다른 스키마 사용. 이 속성은 &quot;namespace:name&quot; 형식으로 스키마 선언을 수신합니다.
* **적용 가능한 경우(문자열)**: 인덱스를 적용하는 조건. 이 속성은 XTK 표현식을 수신합니다.
* **autok(부울)**: 이 옵션이 활성화되면(autok=&quot;true&quot;) 고유 키가 자동으로 정의됩니다. 이 옵션은 스키마의 기본 요소에서만 사용할 수 있습니다. 경고: Adobe Campaign에서는 생성된 키가 고유한지 만 보장합니다. 키 값이 연속적이고 증가하는지 보장되지 않습니다.
* **dataPolicy(문자열)**: sql 필드에 허용되는 값에 대한 승인 제약 조건을 지정할 수 있습니다. 이 속성의 값은 다음과 같습니다.

   * &quot;none&quot;: 값 없음
   * &quot;smartCase&quot;: 첫 글자 대문자
   * &quot;lowerCase&quot;: 모든 하위 케이스
   * &quot;upperCase&quot;: 모든 상위 사례
   * &quot;email&quot;: 이메일 주소
   * &quot;phone&quot;: 전화 번호
   * &quot;identifier&quot;: 식별자 이름
   * &quot;resIdentifier&quot;: 파일 이름

* **dbEnum(문자열)**: &quot;closed&quot; 열거형의 내부 이름을 받습니다. 열거형 값은 `<srcschema>`.
* **defOnDuplicate(부울)**: 이 속성을 활성화하면 레코드가 복제되면 기본값(@default에 정의됨)이 레코드에 자동으로 다시 적용됩니다.
* **기본값(문자열)**: 요소 동작(함수 호출, 기본값)을 정의할 수 있습니다. 이 속성은 XTK 표현식을 수신합니다.
* **desc(문자열)**: 요소에 대한 설명을 삽입할 수 있습니다. 이 설명은 인터페이스의 상태 표시줄에 표시됩니다.
* **displayAsField(부울)**: 이 속성이 활성화되면 &quot;링크&quot; 유형이 사용됩니다 `<element>`  스키마(&quot;구조&quot; 탭)의 트리 보기에 필드로 표시됩니다. 이렇게 하면 링크를 로컬 필드로 표시하고 쿼리 중에 동작을 변경할 수 있습니다. 쿼리의 SELECT에 요소가 있으면 링크 대상의 값이 사용됩니다. 쿼리의 WHERE에 요소가 있으면 링크의 기본 키가 사용됩니다.
* **편집(문자열)**: 이 속성은 스키마에 연결된 양식에 사용할 입력 유형을 지정합니다.
* **enum(문자열)**: 필드에 연결된 열거형의 이름을 받습니다. 열거형은 동일한 스키마에 삽입하거나 원격 스키마에 삽입할 수 있습니다.
* **expr(문자열)**: 이 속성은 테이블에 정의가 저장되지 않는 계산된 필드를 정의합니다. Xpath 또는 XTK (문자열) 표현식을 수신합니다.
* **externalJoin(부울)**: 링크 유형 요소의 외부 조인
* **기능(문자열)**: 특성 필드를 정의합니다. 이 필드는 기존 테이블의 데이터를 확장하는 데 사용되지만 부록 테이블의 저장과 함께 사용됩니다. 허용되는 값은 다음과 같습니다.

   * &quot;shared&quot;: 컨텐츠는 데이터 유형별로 공유 테이블에 저장됩니다
   * &quot;dedicated&quot;: 컨텐츠는 전용 테이블에 저장됩니다

   SQL 특성 테이블은 특성 유형에 따라 자동으로 작성됩니다.

   * 전용: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 공유: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   다음과 같은 두 가지 유형의 특성 필드가 있습니다. 특성에 대해 단일 값을 허용하는 단순 필드 및 여러 값을 포함할 수 있는 컬렉션 요소와 연결된 다중 선택 필드.

   스키마에 특성이 정의된 경우 이 스키마에는 단일 필드를 기반으로 하는 기본 키가 있어야 합니다(복합 키가 승인되지 않음).

* **featureDate(부울)**: &quot;@feature&quot; 특성 필드에 연결된 속성입니다. 값이 &quot;true&quot;이면 값이 마지막으로 업데이트된 시기를 알 수 있습니다.
* **filterPath(문자열)**: 이 속성은 Xpath를 수신하고 필드에 필터를 정의할 수 있도록 해줍니다.
* **folderLink (문자열)**: 이 속성은 엔티티가 포함된 파일을 복구할 수 있는 링크의 이름을 받습니다.
* **folderModel(문자열)**: 엔티티 저장소를 사용할 수 있는 폴더 유형을 정의합니다. 이 속성은 &quot;@folderLink&quot;이 있는 경우에만 정의됩니다.
* **folderProcess(문자열)**: 엔티티 모델 인스턴스가 저장되는 링크를 정의합니다. 이 속성은 &quot;@folderLink&quot;이 있는 경우에만 정의됩니다.
* **fullLoad(부울)**: 이 속성을 사용하면 양식에서 필드를 선택할 때 테이블의 모든 레코드가 표시됩니다.
* **img(문자열)**: 는 요소에 연결된 이미지의 경로를 수신합니다. 이 특성의 값은 &quot;namespace:image name&quot; 형식입니다. 예: img=&quot;cus:myImage.jpg&quot;. 실제로 이미지를 애플리케이션 서버로 가져와야 합니다.
* **무결성(문자열)**: 대상 테이블에 대한 소스 테이블의 발생 참조 무결성

   액세스 가능한 값은 다음과 같습니다.

   * &quot;define&quot;: 링크를 통해 참조되는 경우에는 Adobe Campaign에서 엔티티를 삭제하지 않습니다
   * &quot;normal&quot;: 소스 항목을 삭제하면 대상 발생 시 링크의 키가 초기화됩니다(기본 모드). 이 유형의 무결성은 모든 외래 키를 초기화합니다
   * &quot;own&quot;: 소스 발생 삭제를 수행하면 대상 발생 항목이 삭제됩니다
   * &quot;downcopy&quot;: &quot;소유&quot;(삭제의 경우)와 유사하거나 중복 발생(중복의 경우)합니다.
   * &quot;neutral&quot;: 아무 작업도 하지 않음

* **레이블(문자열)**: 요소 레이블입니다.
* **labelSingular(문자열)**: 인터페이스의 일부 부분에 사용되는 요소의 레이블(단일 형식)입니다.
* **length (문자열)**: 최대. 문자열 유형 SQL 필드의 값에 대해 권한이 부여된 문자 수입니다.
* **지역화 가능(부울)**: 활성화되면 이 속성은 번역을 위한 &quot;@label&quot; 속성 값을 복구하도록 수집 도구에 알려줍니다(내부 사용).
* **name(MNTOKEN)**: 테이블의 이름과 일치하는 요소의 내부 이름입니다. &quot;@name&quot; 속성 값은 짧아야 하며, 바람직하게는 영어로 입력해야 하며 XML에 연결된 이름 지정 제약 조건을 준수해야 합니다.

   스키마를 데이터베이스에 기록하면 접두사가 Adobe Campaign에 의해 필드 이름에 자동으로 추가됩니다.

   * &quot;i&quot;: &#39;integer&#39; 형식의 접두사입니다.
   * &quot;d&quot;: &#39;double&#39; 형식의 접두사입니다.
   * &quot;s&quot;: 접두사로 문자 문자열 유형을 사용합니다.
   * &quot;ts&quot;: &#39;date&#39; 유형의 접두사입니다.

   자율적인 방식으로 테이블의 이름을 정의하려면 기본 스키마 요소의 정의에 &quot;@sqltable&quot; 속성을 사용해야 합니다.

* **noDbIndex(부울)**: 요소가 인덱싱되지 않도록 지정할 수 있습니다.
* **순서 지정(부울)**: 특성이 활성화되어 있으면(ordered=&quot;true&quot;) Adobe Campaign은 요소 선언 시퀀스를 XML 수집 요소에 유지합니다.
* **pkSequence(문자열)**: 자동 증분 키 계산에 사용할 시퀀스의 이름을 받습니다. 이 속성은 스키마의 루트 요소에 자동 증분 키가 정의된 경우에만 사용할 수 있습니다.
* **pkgStatus (string)**: 패키지를 내보내는 동안 값이 이 속성 값의 함수로 고려됩니다.

   * &quot;always&quot;: 요소는 항상 있습니다
   * &quot;never&quot;: 요소가 존재하지 않습니다
   * &quot;default(또는 nothing)&quot;: 요소가 기본 요소이거나 내부 필드가 아니며 다른 인스턴스와 호환되지 않는 경우 요소를 내보냅니다

* **ref(문자열)**: 이 속성은 여러 스키마에서 공유되는 >element> 요소에 대한 참조를 정의합니다(정의 팩터링). 정의가 현재 스키마에 복사되지 않습니다.
* **필수(부울)**: 이 속성이 활성화된 경우(@required=&quot;true&quot;) 인터페이스에 필드가 강조 표시됩니다. 필드의 레이블은 빨간색으로 표시됩니다.
* **revAdvanced(부울)**: 활성화되면 이 속성은 상대 링크가 &quot;고급&quot; 링크임을 지정합니다.
* **revCardinality(문자열)**: 이 속성은 두 테이블 간의 링크의 카디널리티를 정의합니다. 링크 유형에 사용됩니다 `<element>`.

   가능한 값은 다음과 같습니다.

   * &quot;single&quot; : 단순 1-1 유형 링크
   * &quot;바인딩되지 않음&quot;: 1-N 유형 컬렉션 링크

   기본적으로 링크를 만드는 동안 속성을 지정하지 않으면 카디널리티는 1-N이 됩니다.

* **revDesc(문자열)**: 이 속성은 반대되는 링크에 연결된 설명을 수신합니다.
* **revExternalJoin(부울)**: 이 속성을 활성화하면 반대 링크에 대해 외부 조인을 강제 적용할 수 있습니다.
* **revIntegrity(문자열)**: 이 속성은 대상 스키마에 대한 무결성을 정의합니다. &quot;@integrity&quot; 속성과 동일한 값이 승인됩니다. 기본적으로 Adobe Campaign은 이 속성에 &quot;일반&quot; 값을 제공합니다.
* **revLabel(문자열)**: 반대 링크의 레이블입니다.
* **revLink (문자열)**: 반대 링크의 이름입니다. 값이 &quot;_없음_&quot;. 대상 스키마에 반대 링크가 만들어지지 않습니다.
* **revTarget(문자열)**: 대상이 될 수 있습니다.
* **sql(부울)**: 이 특성이 활성화되면(@sql=&quot;true&quot;) 요소에 xml=&quot;true&quot; 속성이 있더라도 SQL 요소의 저장을 강제 적용합니다.
* **sqlname(문자열)**: 테이블을 만드는 동안 필드의 이름입니다. &quot;@sqlname&quot;을 지정하지 않으면 기본적으로 &quot;@name&quot; 속성의 값이 사용됩니다. 스키마에 스키마를 작성할 때 접두사는 필드 유형에 따라 자동으로 추가됩니다.
* **sqltable(문자열)**: 스키마의 기본 요소에 대해 이 속성은 기본적으로 생성된 SQL 테이블의 이름을 오버로드합니다. &quot;@sqltable&quot;을 지정하지 않으면 기본 이름이 다음과 같이 구조화됩니다. namespace(첫 번째 글자 대문자)에 SrcSchema &quot;@name&quot; 값이 옵니다.
* **tableSpace(문자열)**: 이 속성을 사용하면 테이블에 대해 테이블(루트에 대해 유효)을 저장하는 새 데이터를 지정할 수 있습니다 `<element>`).
* **tableSpaceIndex(문자열)**: 이 속성을 사용하면 테이블에 대한 새 인덱스 저장 영역 테이블스페이스를 지정할 수 있습니다(루트에 있음). `<element>`).
* **target(MNTOKEN)**: 는 테이블 간 링크를 만들 때 대상 스키마의 이름을 받습니다. 이 속성은 &quot;링크&quot; 유형 요소에만 활성화됩니다.
* **템플릿(문자열)**: 이 속성은 `<element>` 여러 스키마에서 공유된 요소입니다. 정의가 현재 스키마에 자동으로 복사됩니다.
* **translatedDefault(문자열)**: &quot;@default&quot; 속성이 발견되면 &quot;@translatedDefault&quot;을 사용하여 @default에 정의된 표현식과 일치하도록 표현식을 재정의하여 번역 도구(내부 사용)에 수집할 수 있습니다.
* **translatedExpr(문자열)**: &quot;@expr&quot; 속성을 찾으면 &quot;@translatedExpr&quot; 속성을 사용하여 &quot;@expr&quot;에 정의된 표현식과 일치하는 표현식을 재정의할 수 있으며, 이러한 표현식은 번역 도구(내부 사용)에 의해 수집됩니다.
* **유형(MNTOKEN)**: 요소에 저장된 데이터의 유형을 정의합니다.

   사용 가능한 유형 목록:

   * 임의
   * bin
   * blob
   * 부울
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimeenotz
   * 날짜
   * 이중
   * enum
   * float
   * html
   * int64
   * 링크
   * 장기간
   * 메모
   * MNTOKEN
   * 퍼센트
   * primarykey
   * short
   * string
   * 시간
   * 시간 간격
   * uuid

* **언바운드(부울)**: 특성이 활성화되면(unbound=&quot;true&quot;) 링크가 1-N 카디널리티에 대한 수집 요소로 선언됩니다.
* **userEnum(문자열)**: &quot;open&quot; 열거형의 내부 이름을 받습니다. 열거형 값은 인터페이스에서 사용자가 정의할 수 있습니다.
* **xml(부울)**: 이 옵션을 활성화하면 요소에 정의된 모든 값이 텍스트 유형 &quot;mData&quot; 필드의 XML에 저장됩니다. 즉, 이러한 필드를 필터링하거나 정렬하지 않습니다.
* **xmlChildren(부울)**: 각 하위 항목에 대한 스토리지 강제 적용 `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
