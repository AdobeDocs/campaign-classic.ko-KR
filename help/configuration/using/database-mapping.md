---
product: campaign
title: 데이터베이스 매핑
description: 데이터베이스 매핑
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 3%

---

# 데이터베이스 매핑{#database-mapping}

설명된 샘플 스키마의 SQL 매핑 [이 페이지에서](schema-structure.md) 는 다음 XML 문서를 생성합니다.

```sql
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

스키마의 루트 요소가 (으)로 변경됨 **`<srcschema>`** 끝 **`<schema>`**.

다른 유형의 문서는 소스 스키마에서 자동으로 생성되며 스키마라고 합니다.

SQL 이름은 요소 이름과 유형에 따라 자동으로 결정됩니다.

SQL 이름 지정 규칙은 다음과 같습니다.

* **표**: 스키마 네임스페이스 및 이름 연결

  이 예제에서 표의 이름은 스키마의 기본 요소를 통해 **sqltable** 특성:

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* **필드**: 유형에 따라 정의된 접두사가 앞에 오는 요소의 이름: 정수는 &#39;i&#39;, 복수는 &#39;d&#39;, 문자열은 &#39;s&#39;, 날짜는 &#39;ts&#39; 등.

  필드 이름은 **sqlname** 입력된 각 속성에 대한 속성 **`<attribute>`** 및 **`<element>`**:

  ```sql
  <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
  ```

>[!NOTE]
>
>소스 스키마에서 SQL 이름을 오버로드할 수 있습니다. 이렇게 하려면 관련 요소에서 &quot;sqltable&quot; 또는 &quot;sqlname&quot; 특성을 채웁니다.

확장 스키마에서 생성된 테이블을 생성하는 SQL 스크립트는 다음과 같습니다.

```sql
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

SQL 필드 제약 조건은 다음과 같습니다.

* 숫자 및 날짜 필드에 null 값이 없음
* 숫자 필드는 0으로 초기화됩니다.

## XML 필드 {#xml-fields}

기본적으로 모두  **`<attribute>`** 및 **`<element>`** -typed 요소는 데이터 스키마 테이블의 SQL 필드에 매핑됩니다. 그러나 SQL 대신 XML로 이 필드를 참조할 수 있습니다. 즉, 모든 XML 필드의 값이 들어 있는 테이블의 메모 필드(&quot;mData&quot;)에 데이터가 저장됩니다. 이러한 데이터의 저장소는 스키마 구조를 관찰하는 XML 문서입니다.

XML에서 필드를 채우려면 다음을 추가해야 합니다. **xml** 관련 요소에 &quot;true&quot; 값이 있는 특성.

**예**: 다음은 XML 필드 사용의 두 가지 예입니다.

* 여러 줄 주석 필드:

  ```sql
  <element name="comment" xml="true" type="memo" label="Comment"/>
  ```

* HTML 형식의 데이터 설명:

  ```sql
  <element name="description" xml="true" type="html" label="Description"/>
  ```

  html 유형을 사용하면 HTML 콘텐츠를 CDATA 태그에 저장하고 Adobe Campaign 클라이언트 인터페이스에 특수 HTML 편집 검사를 표시할 수 있습니다.

데이터베이스의 실제 구조를 수정하지 않고 새 필드를 추가하려면 XML 필드를 사용합니다. 또 다른 장점은 리소스(SQL 필드에 할당된 크기, 테이블당 필드 수 제한 등)를 적게 사용한다는 것입니다. 그러나 XML 필드는 인덱싱하거나 필터링할 수 없습니다.

## 인덱싱된 필드 {#indexed-fields}

인덱스를 사용하면 애플리케이션에서 사용되는 SQL 쿼리의 성능을 최적화할 수 있습니다.

인덱스는 데이터 스키마의 기본 요소에서 선언됩니다.

```sql
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

색인은 다음 규칙을 따릅니다.

* 인덱스는 테이블에서 하나 이상의 필드를 참조할 수 있습니다
* 다음의 경우 색인은 모든 필드에서 고유할 수 있습니다(중복 방지). **고유** attribute에 &quot;true&quot; 값이 포함됨
* 인덱스의 SQL 이름은 테이블의 SQL 이름과 인덱스의 이름에서 결정됩니다

>[!NOTE]
>
>* 표준으로 색인은 스키마의 기본 요소에서 선언된 첫 번째 요소입니다.
>
>* 인덱스는 테이블 매핑(표준 또는 FDA) 중에 자동으로 만들어집니다.

**예**:

* 이메일 주소 및 구/군/시에 색인 추가:

  ```sql
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

  ```sql
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

## 자세히 알아보기

자세한 내용은 다음 링크를 참조하십시오.

* [스키마 시작하기](about-schema-reference.md)
* [스키마 구조](schema-structure.md)
* [키 관리](database-keys.md)
* [링크 관리](database-links.md)
* [Campaign 데이터 모델](about-data-model.md)