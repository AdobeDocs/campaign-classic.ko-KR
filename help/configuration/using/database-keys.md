---
product: campaign
title: 데이터 스키마의 키 관리
description: 데이터 스키마의 키 관리 이해
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
source-git-commit: f03e72d4ecd17446264adf74603aefca95f99d41
workflow-type: tm+mt
source-wordcount: '604'
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

키를 스키마에서 처음 채울 때 또는 가 포함된 경우 &#39;기본 키&#39;라고 합니다 `internal` 속성이 &quot;true&quot;로 설정되어 있습니다.


키에는 다음 규칙이 적용됩니다.

* 키는 테이블에서 하나 이상의 필드를 참조할 수 있습니다
* 고유 인덱스는 각 키 정의에 대해 암시적으로 선언됩니다. 를 설정하여 키에 인덱스를 만들 수 없습니다. `noDbIndex` 속성을 &quot;true&quot;로 설정합니다.

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

대부분의 Adobe Campaign 테이블의 기본 키는 데이터베이스 엔진에서 자동으로 생성된 32비트 정수(Long)입니다. 키 값의 계산은 시퀀스에 따라 다릅니다(기본적으로 **XtkNewId** SQL 함수)를 사용하여 전체 데이터베이스에서 고유한 숫자를 생성합니다. 키의 내용은 레코드 삽입 시 자동으로 입력됩니다.

증분 키의 장점은 테이블 간의 조인에 수정할 수 없는 기술 키를 제공한다는 것입니다. 또한 이 키는 2바이트 정수를 사용하므로 메모리를 많이 차지하지 않습니다.

소스 스키마에서 와 함께 사용할 시퀀스의 이름을 지정할 수 있습니다 **pkSequence** 특성. 소스 스키마에 이 속성이 지정되지 않으면 **XtkNewId** 기본 시퀀스가 사용됩니다. 응용 프로그램은 다음에 대한 전용 시퀀스를 사용합니다. **nms:broadLog** 및 **nms:trackingLog** 스키마 (**NmsBroadLogId** 및 **NmsTrackingLogId** 각각) - 가장 많은 레코드를 포함하는 테이블이기 때문입니다.

ACC 18.10에서, **XtkNewId** 기본 스키마에서 시퀀스의 기본값이 더 이상 아닙니다. 이제 전용 시퀀스로 스키마를 빌드하거나 기존 스키마를 확장할 수 있습니다.

>[!IMPORTANT]
>
>새 스키마를 생성하거나 스키마 확장 중에 전체 스키마에 대해 동일한 기본 키 시퀀스 값(@pkSequence)을 유지해야 합니다.

Adobe Campaign 스키마에서 참조된 시퀀스(**NmsTrackingLogId** 예를 들어 )는 매개 변수의 ID 수를 쉼표로 구분하여 반환하는 SQL 함수와 연결되어야 합니다. 이 함수를 호출해야 합니다. **GetNew** XXX **Id**, 여기서 **XXX** 는 시퀀스의 이름입니다(**GetNewNmsTrackingLogIds** 예). 보기 **postgres-nms.sql**, **mssql-nms.sql** 또는 **oracle-nms.sql** 에서 응용 프로그램과 함께 제공된 파일 **datakit/nms/eng/sql/** 각 데이터베이스 엔진에 대한 &#39;NmsTrackingLogId&#39; 시퀀스 작성의 예를 복구하기 위한 디렉터리입니다.

고유 키를 선언하려면 **autopk** 속성(값 &quot;true&quot; 사용)이 데이터 스키마의 기본 요소에 있습니다.

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

