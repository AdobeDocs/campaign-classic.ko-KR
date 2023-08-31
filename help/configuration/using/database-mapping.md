---
product: campaign
title: 데이터베이스 매핑
description: 데이터베이스 매핑
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1981'
ht-degree: 1%

---

# 데이터베이스 매핑{#database-mapping}

예제 스키마의 SQL 매핑은 다음 XML 문서를 제공합니다.

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient email address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

## 설명 {#description}

스키마의 루트 요소가 더 이상 아닙니다. **`<srcschema>`**, 하지만 **`<schema>`**.

이를 통해 소스 스키마에서 자동으로 생성되는 다른 유형의 문서(간단히 스키마라고 함)로 이동합니다. 이 스키마는 Adobe Campaign 애플리케이션에서 사용됩니다.

SQL 이름은 요소 이름과 유형에 따라 자동으로 결정됩니다.

SQL 이름 지정 규칙은 다음과 같습니다.

* 표: 스키마 네임스페이스 및 이름의 연결

  이 예제에서 표의 이름은 스키마의 기본 요소를 통해 **sqltable** 특성:

  ```
  <element name="recipient" sqltable="CusRecipient">
  ```

* 필드: 유형에 따라 정의된 접두사가 앞에 오는 요소의 이름(정수는 &#39;i&#39;, double은 &#39;d&#39;, 문자열은 &#39;s&#39;, 날짜는 &#39;ts&#39; 등)

  필드 이름은 **sqlname** 입력된 각 속성에 대한 속성 **`<attribute>`** 및 **`<element>`**:

  ```
  <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
  ```

>[!NOTE]
>
>소스 스키마에서 SQL 이름을 오버로드할 수 있습니다. 이렇게 하려면 관련 요소에서 &quot;sqltable&quot; 또는 &quot;sqlname&quot; 특성을 채웁니다.

확장 스키마에서 생성된 테이블을 생성하는 SQL 스크립트는 다음과 같습니다.

```
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

SQL 필드 제약 조건은 다음과 같습니다.

* 숫자 및 날짜 필드에 null 값이 없음,
* 숫자 필드는 0으로 초기화됩니다.

## XML 필드 {#xml-fields}

기본적으로 모든 입력 **`<attribute>`** 및 **`<element>`** 요소는 데이터 스키마 테이블의 SQL 필드에 매핑됩니다. 그러나 SQL 대신 XML로 이 필드를 참조할 수 있습니다. 즉, 모든 XML 필드의 값이 들어 있는 테이블의 메모 필드(&quot;mData&quot;)에 데이터가 저장됩니다. 이러한 데이터의 저장소는 스키마 구조를 관찰하는 XML 문서입니다.

XML에서 필드를 채우려면 다음을 추가해야 합니다. **xml** 관련 요소에 &quot;true&quot; 값이 있는 특성.

**예**: 다음은 XML 필드 사용의 두 가지 예입니다.

* 여러 줄 주석 필드:

  ```
  <element name="comment" xml="true" type="memo" label="Comment"/>
  ```

* HTML 형식의 데이터 설명:

  ```
  <element name="description" xml="true" type="html" label="Description"/>
  ```

  html 유형을 사용하면 HTML 콘텐츠를 CDATA 태그에 저장하고 Adobe Campaign 클라이언트 인터페이스에 특수 HTML 편집 검사를 표시할 수 있습니다.

XML 필드를 사용하면 데이터베이스의 물리적 구조를 수정할 필요 없이 필드를 추가할 수 있습니다. 또 다른 장점은 리소스(SQL 필드에 할당된 크기, 테이블당 필드 수 제한 등)를 적게 사용한다는 것입니다.

XML 필드를 인덱싱하거나 필터링할 수 없는 것이 주요 단점입니다.

## 인덱싱된 필드 {#indexed-fields}

인덱스를 사용하면 애플리케이션에서 사용되는 SQL 쿼리의 성능을 최적화할 수 있습니다.

인덱스는 데이터 스키마의 기본 요소에서 선언됩니다.

```
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

색인은 다음 규칙을 따릅니다.

* 인덱스는 테이블에서 하나 이상의 필드를 참조할 수 있습니다.
* 다음의 경우 색인은 모든 필드에서 고유할 수 있습니다(중복 방지). **고유** attribute에 &quot;true&quot; 값이 포함되어 있습니다.
* 인덱스의 SQL 이름은 테이블의 SQL 이름과 인덱스의 이름에서 결정됩니다.

>[!NOTE]
>
>표준으로 색인은 스키마의 기본 요소에서 선언된 첫 번째 요소입니다.

>[!NOTE]
>
>인덱스는 테이블 매핑(표준 또는 FDA) 중에 자동으로 만들어집니다.

**예제**:

* 이메일 주소 및 구/군/시에 색인 추가:

  ```
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* &quot;id&quot; 이름 필드에 고유 인덱스 추가:

  ```
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

## 키 관리 {#management-of-keys}

테이블에는 테이블에서 레코드를 식별하기 위한 키가 하나 이상 있어야 합니다.

데이터 스키마의 주 요소에서 키가 선언됩니다.

```
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

키는 다음 규칙을 따릅니다.

* 키는 테이블에서 하나 이상의 필드를 참조할 수 있습니다.
* 키를 스키마에서 처음 채우거나 키가 포함된 경우 &#39;기본&#39;(또는 &#39;우선 순위&#39;)이라고 합니다. **내부** 속성이 &quot;true&quot; 값을 갖습니다.
* 고유 인덱스는 각 키 정의에 대해 암시적으로 선언됩니다. 를 추가하여 키의 색인 만들기를 방지할 수 있습니다. **noDbIndex** 속성이 &quot;true&quot; 값을 갖습니다.

>[!NOTE]
>
>표준으로 키는 인덱스가 정의된 후 스키마의 기본 요소에서 선언되는 요소입니다.

>[!NOTE]
>
>테이블 매핑(표준 또는 FDA) 중에 키가 생성되면 Adobe Campaign은 고유한 색인을 찾습니다.

**예제**:

* 이메일 주소 및 구/군/시에 키 추가:

  ```
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </key>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

  생성된 스키마:

  ```
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
     <dbindex name="email" unique="true">      
       <keyfield xpath="@email"/>      
       <keyfield xpath="location/@city"/>    
     </dbindex>    
  
     <key name="email">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="location/@city"/>    
     </key>    
  
     <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
     <element label="Location" name="location">      
       <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
     </element>  
    </element>
  </schema>
  ```

* &quot;id&quot; 이름 필드에 기본 키 또는 내부 키 추가:

  ```
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="id" internal="true">
        <keyfield xpath="@id"/> 
      </key>
  
      <key name="email" noDbIndex="true">
        <keyfield xpath="@email"/> 
      </key>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

  생성된 스키마:

  ```
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
      <key name="email">      
        <keyfield xpath="@email"/>    
      </key>    
  
      <dbindex name="id" unique="true">      
        <keyfield xpath="@id"/>    
      </dbindex>    
  
      <key internal="true" name="id">      
       <keyfield xpath="@id"/>    
      </key>    
  
      <attribute label="Identifier" name="id" sqlname="iRecipientId" type="long"/>    
      <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
    </element>
  </schema>
  ```

### 자동 증분 키 {#auto-incremental-key}

대부분의 Adobe Campaign 테이블의 기본 키는 데이터베이스 엔진에서 자동으로 생성된 32비트 정수(Long)입니다. 키 값의 계산은 시퀀스에 따라 다릅니다(기본적으로 **XtkNewId** SQL 함수)를 사용하여 전체 데이터베이스에서 고유한 숫자를 생성합니다. 키의 내용은 레코드 삽입 시 자동으로 입력됩니다.

증분 키의 장점은 테이블 간의 조인에 수정할 수 없는 기술 키를 제공한다는 것입니다. 또한 이 키는 2바이트 정수를 사용하므로 메모리를 많이 차지하지 않습니다.

소스 스키마에서 와 함께 사용할 시퀀스의 이름을 지정할 수 있습니다 **pkSequence** 특성. 소스 스키마에 이 속성이 지정되지 않으면 **XtkNewId** 기본 시퀀스가 사용됩니다. 응용 프로그램은 다음에 대한 전용 시퀀스를 사용합니다. **nms:broadLog** 및 **nms:trackingLog** 스키마 (**NmsBroadLogId** 및 **NmsTrackingLogId** 각각) - 가장 많은 레코드를 포함하는 테이블이기 때문입니다.

ACC 18.10에서, **XtkNewId** 기본 스키마에서 시퀀스의 기본값이 더 이상 아닙니다. 이제 전용 시퀀스로 스키마를 빌드하거나 기존 스키마를 확장할 수 있습니다.

>[!IMPORTANT]
>
>새 스키마를 생성하거나 스키마 확장 중에 전체 스키마에 대해 동일한 기본 키 시퀀스 값(@pkSequence)을 유지해야 합니다.

>[!NOTE]
>
>Adobe Campaign 스키마에서 참조된 시퀀스(**NmsTrackingLogId** 예를 들어 )는 매개 변수의 ID 수를 쉼표로 구분하여 반환하는 SQL 함수와 연결되어야 합니다. 이 함수를 호출해야 합니다. **GetNew** XXX **Id**, 여기서 **XXX** 는 시퀀스의 이름입니다(**GetNewNmsTrackingLogIds** 예). 보기 **postgres-nms.sql**, **mssql-nms.sql** 또는 **oracle-nms.sql** 에서 응용 프로그램과 함께 제공된 파일 **datakit/nms/eng/sql/** 각 데이터베이스 엔진에 대한 &#39;NmsTrackingLogId&#39; 시퀀스 작성의 예를 복구하기 위한 디렉터리입니다.

고유 키를 선언하려면 **autopk** 속성(값 &quot;true&quot; 사용)이 데이터 스키마의 기본 요소에 있습니다.

**예제**:

소스 스키마에서 증분 키 선언:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

생성된 스키마:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" autopk="true" pkSequence="XtkNewId" sqltable="CusRecipient"> 
    <dbindex name="id" unique="true">
      <keyfield xpath="@id"/>
    </dbindex>

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

키 및 해당 인덱스의 정의 외에 자동 생성된 기본 키를 포함하기 위해 확장 스키마에 &quot;id&quot;라는 숫자 필드가 추가되었습니다.

>[!IMPORTANT]
>
>기본 키가 0으로 설정된 레코드는 테이블 생성 시 자동으로 삽입됩니다. 이 레코드는 볼륨 테이블에 적용되지 않는 외부 조인을 피하는 데 사용됩니다. 기본적으로 모든 외래 키는 값 0으로 초기화되므로 데이터 항목이 채워지지 않은 경우 조인에서 항상 결과가 반환될 수 있습니다.

## 링크: 표 간의 관계 {#links--relation-between-tables}

링크는 한 테이블과 다른 테이블 간의 연관을 설명합니다.

다양한 유형의 연관(&quot;카디널리티&quot;라고 함)은 다음과 같습니다.

* 카디널리티 1-1: 소스 테이블의 발생 항목 하나는 타겟 테이블의 해당 발생 항목을 최대 한 개까지 가질 수 있습니다.
* 카디널리티 1-N: 소스 테이블의 발생 항목 하나는 타겟 테이블의 여러 발생 항목을 가질 수 있지만, 타겟 테이블의 발생 항목 하나는 소스 테이블의 해당 발생 항목을 최대 한 개까지 가질 수 있습니다.
* 카디널리티 N-N: 소스 테이블의 발생 항목 하나는 타겟 테이블의 여러 발생 항목을 가질 수 있으며, 그 반대의 경우도 가능합니다.

인터페이스에서 아이콘 덕분에 서로 다른 유형의 관계를 쉽게 구별할 수 있습니다.

캠페인 테이블/데이터베이스와의 조인 관계의 경우:

* ![](assets/join_with_campaign11.png) : 카디널리티 1-1. 예를 들어 수신자와 현재 주문 간에 적용될 수 있습니다. 수신자는 현재 주문 테이블을 한 번에 하나만 연결할 수 있습니다.
* ![](assets/externaljoin11.png) : 카디널리티 1-1, 외부 조인. 예를 들어 수신자와 해당 국가 간. 수신자는 한 테이블 국가에만 관련될 수 있습니다. 국가 테이블의 내용은 저장되지 않습니다.
* ![](assets/join_with_campaign1n.png) : 카디널리티 1-N. 예를 들어 수신자와 구독 테이블 간 수신자는 구독 테이블의 여러 발생 횟수와 관련될 수 있습니다.

Federated Database Access를 사용하는 조인 관계의 경우

* ![](assets/join_fda_11.png) : 카디널리티 1-1
* ![](assets/join_fda_1m.png) : 카디널리티 1-N

FDA 표에 대한 자세한 내용은 [외부 데이터베이스 액세스](../../installation/using/about-fda.md).

주 요소를 통해 연결된 테이블의 외래 키를 포함하는 스키마에서 링크를 선언해야 합니다.

```
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

링크는 다음 규칙을 따릅니다.

* 링크의 정의는 **링크**-type **`<element>`** 다음 속성을 사용합니다.

   * **이름**: 소스 테이블의 링크 이름,
   * **target**: 대상 스키마 이름,
   * **레이블**: 링크 레이블,
   * **revLink** (선택 사항): 대상 스키마의 역방향 링크 이름(기본적으로 자동으로 추론됨),
   * **무결성** (선택 사항): 소스 테이블의 발생과 대상 테이블의 발생에 대한 참조 무결성. 가능한 값은 다음과 같습니다.

      * **정의**: 대상 발생에서 더 이상 참조하지 않는 경우 소스 발생을 삭제할 수 있습니다.
      * **표준**: 소스 발생 항목을 삭제하면 대상 발생 항목에 대한 링크의 키가 초기화됩니다(기본 모드). 이 유형의 무결성은 모든 외래 키를 초기화합니다.
      * **소유**: 소스 발생 항목을 삭제하면 타겟 발생 항목이 삭제되고,
      * **owncopy**: 와 동일 **소유** (삭제 시) 또는 발생 횟수 중복(중복 시),
      * **중립**: 아무 작업도 하지 않습니다.

   * **revIntegrity** (선택 사항): 대상 스키마의 무결성 (선택 사항, 기본적으로 &quot;보통&quot;),
   * **반대 카디널리티** (선택 사항): 값 &quot;single&quot;을 사용하면 카디널리티가 유형 1-1(기본적으로 1-N)로 채워집니다.
   * **externalJoin** (선택 사항): 외부 조인을 강제 적용합니다
   * **revExternalJoin** (선택 사항): 역방향 링크에 외부 조인을 강제 적용합니다

* 링크는 소스 테이블에서 대상 테이블로 하나 이상의 필드를 참조합니다. 조인을 구성하는 필드( `<join>`  요소)는 대상 스키마의 내부 키를 사용하여 기본적으로 자동으로 추론되므로 채우지 않아도 됩니다.
* 확장 스키마에 있는 링크의 외부 키에 인덱스가 자동으로 추가됩니다.
* 링크는 두 개의 절반 링크로 구성되며, 첫 번째 링크는 소스 스키마에서 선언되고 두 번째 링크는 대상 스키마의 확장 스키마에서 자동으로 만들어집니다.
* 다음 경우에 조인은 외부 조인이 될 수 있습니다. **externalJoin** 값이 &quot;true&quot;인 속성이 추가됩니다(PostgreSQL에서 지원됨).

>[!NOTE]
>
>표준으로 링크는 스키마 끝에 선언된 요소입니다.

### 예제 1 {#example-1}

&quot;cus:company&quot; 스키마 테이블과 1-N 관계:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

생성된 스키마:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>
    ...
    <element label="Company" name="company" revLink="recipient" target="cus:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Company' link (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

링크 정의는 조인을 구성하는 필드, 즉 대상 스키마에 해당 XPath(&quot;@id&quot;)가 있는 기본 키와 스키마에 해당 XPath(&quot;@company-id&quot;)가 있는 외래 키로 보완됩니다.

외래 키는 대상 테이블의 관련 필드와 동일한 특성을 사용하는 요소에 자동으로 추가되며, 다음과 같은 명명 규칙이 적용됩니다. 대상 스키마 이름 뒤에 관련 필드 이름(&quot;회사 ID&quot;)이 표시됩니다.

대상의 확장 스키마(&quot;cus:company&quot;):

```
<schema mappingType="sql" name="company" namespace="cus" xtkschema="xtk:schema">  
  <element name="company" sqltable="CusCompany" autopk="true"> 
    <dbindex name="id" unique="true">     
      <keyfield xpath="@id"/>    
    </dbindex>   
    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>
    ...
    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iCompanyId" type="long"/>
    ...
    <element belongsTo="cus:recipient" integrity="define" label="Contact" name="recipient" revLink="company" target="nms:recipient" type="link" unbound="true">      
      <join xpath-dst="@company-id" xpath-src="@id"/>    
    </element>
  </element>
</schema>
```

다음 매개 변수와 함께 &quot;cus:recipient&quot; 표에 대한 역방향 링크가 추가되었습니다.

* **이름**: 소스 스키마의 이름에서 자동으로 추론됩니다(소스 스키마의 링크 정의에 &quot;revLink&quot; 속성으로 강제 추론될 수 있음).
* **revLink**: 역방향 링크 이름
* **target**: 연결된 스키마의 키(&quot;cus:recipient&quot; 스키마)
* **바인딩되지 않음**: 링크는 1-N 카디널리티에 대한 컬렉션 요소로 선언됩니다(기본값)
* **무결성**: 기본적으로 &quot;define&quot;(소스 스키마의 링크 정의에 &quot;revIntegrity&quot; 속성으로 강제 적용할 수 있음)

### 예제 2 {#example-2}

이 예제에서는 &quot;nms:address&quot; 스키마 테이블에 대한 링크를 선언합니다. 조인은 외부 조인이며 받는 사람의 이메일 주소와 연결된 테이블(&quot;nms:address&quot;)의 &quot;@address&quot; 필드로 명시적으로 채워집니다.

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

### 예제 3 {#example-3}

1-1 &quot;cus:extension&quot; 스키마 테이블과의 관계:

```
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### 예제 4 {#example-4}

폴더 링크(&quot;xtk:folder&quot; 스키마):

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

기본값은 &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot; 함수에 입력된 첫 번째 적격 매개 변수 유형 파일의 식별자를 반환합니다.

### 예제 5 {#example-5}

이 예제에서는 를 사용하는 링크(&quot;company&quot; to &quot;cus:company&quot; schema)에 키를 만들려고 합니다. **xlink** (&quot;email&quot;) 테이블의 속성 및 필드:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <key name="companyEmail"> 
      <keyfield xpath="@email"/>
      <keyfield xlink="company"/>
    </key>
    
    <attribute name="email" type="string" length="80" label="Email" desc="Recipient email"/>
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

생성된 스키마:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>

    <dbindex name="companyEmail" unique="true">
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </dbindex>    

    <key name="companyEmail">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </key>

    <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

&quot;companyEmail&quot; 이름 키의 정의가 &quot;company&quot; 링크의 외래 키로 확장되었습니다. 이 키는 두 필드 모두에서 고유한 색인을 생성합니다.
