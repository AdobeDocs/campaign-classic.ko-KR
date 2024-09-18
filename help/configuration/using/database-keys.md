---
product: campaign
title: 데이터 스키마의 키 관리
description: 데이터 스키마의 키 관리 이해
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
source-git-commit: 517b85f5d7691acc2522bf4541f07c34c60c7fbf
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 1%

---

# 스키마의 키 관리 {#management-of-keys}

데이터 스키마와 연결된 각 테이블에는 테이블의 레코드를 식별하기 위한 하나 이상의 키가 있어야 합니다.

데이터 스키마의 주 요소에서 키가 선언됩니다.

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

스키마에서 처음 채울 때 또는 &quot;true&quot;로 설정된 `internal` 특성이 포함된 경우 키를 &#39;기본 키&#39;라고 합니다.

키에는 다음 규칙이 적용됩니다.

* 키는 테이블에서 하나 이상의 필드를 참조할 수 있습니다
* 고유 인덱스는 각 키 정의에 대해 암시적으로 선언됩니다. `noDbIndex` 특성을 &quot;true&quot;로 설정하여 키에 인덱스를 만들 수 없습니다.

>[!NOTE]
>
>* 표준으로 키는 인덱스가 정의된 후 스키마의 기본 요소에서 선언되는 요소입니다.
>
>* 테이블 매핑(표준 또는 FDA) 중에 키가 생성되면 Adobe Campaign은 고유한 색인을 찾습니다.

**예**:

* 이메일 주소 및 구/군/시에 키 추가:

  ```sql
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

  ```sql
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

  ```sql
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

  ```sql
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

## 자동 증분 키 {#auto-incremental-key}

대부분의 Adobe Campaign 테이블의 기본 키는 데이터베이스 엔진에서 자동으로 생성된 32비트 정수(Long)입니다. 키 값의 계산은 전체 데이터베이스에서 고유한 숫자를 생성하는 시퀀스(기본적으로 **XtkNewId** SQL 함수)에 따라 달라집니다. 키의 내용은 레코드 삽입 시 자동으로 입력됩니다.

증분 키의 장점은 테이블 간의 조인에 수정할 수 없는 기술 키를 제공한다는 것입니다. 또한 이 키는 2바이트 정수를 사용하므로 메모리를 많이 차지하지 않습니다.

소스 스키마에서 **pkSequence** 특성과 함께 사용할 시퀀스의 이름을 지정할 수 있습니다. 이 특성이 원본 스키마에 지정되어 있지 않으면 **XtkNewId** 기본 시퀀스가 사용됩니다. **nms:broadLog** 및 **nms:trackingLog** 스키마(**NmsBroadLogId** 및 **NmsTrackingLogId**)에 대해 전용 시퀀스를 사용합니다. 이 스키마는 가장 많은 레코드를 포함하는 테이블이기 때문입니다.

ACC 18.10에서 **XtkNewId**&#x200B;은(는) 기본 제공 스키마에서 시퀀스에 대한 기본값이 아닙니다. 이제 전용 시퀀스로 스키마를 빌드하거나 기존 스키마를 확장할 수 있습니다.

>[!IMPORTANT]
>
>새 스키마를 생성하거나 스키마 확장 중에 전체 스키마에 대해 동일한 기본 키 시퀀스 값(@pkSequence)을 유지해야 합니다.

Adobe Campaign 스키마에서 참조된 시퀀스(예: **NmsTrackingLogId**)는 매개 변수의 ID 수를 쉼표로 구분하여 반환하는 SQL 함수와 연결되어야 합니다. 이 함수를 **GetNew** XXX **Ids**&#x200B;이라고 해야 합니다. 여기서 **XXX**&#x200B;은(는) 시퀀스 이름입니다(예: **GetNewNmsTrackingLogIds**). **datakit/nms/eng/sql/** 디렉터리에서 응용 프로그램과 함께 제공된 **postgres-nms.sql**, **mssql-nms.sql** 또는 **oracle-nms.sql** 파일을 확인하여 각 데이터베이스 엔진에 대한 &#39;NmsTrackingLogId&#39; 시퀀스 생성의 예를 복구하십시오.

고유 키를 선언하려면 데이터 스키마의 기본 요소에서 **autopk** 특성(&quot;true&quot; 값 포함)을 채웁니다.

**예**:

소스 스키마에서 증분 키 선언:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

생성된 스키마:

```sql
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


## 자세히 알아보기

자세한 내용은 다음 링크를 참조하십시오.

* [스키마 시작하기](about-schema-reference.md)
* [스키마 구조](schema-structure.md)
* [데이터베이스 매핑](database-mapping.md)
* [링크 관리](database-links.md)
* [Campaign 데이터 모델](about-data-model.md)
