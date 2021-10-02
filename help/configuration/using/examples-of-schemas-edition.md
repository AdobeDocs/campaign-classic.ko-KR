---
product: campaign
title: 스키마 편집 사례
description: 스키마 편집 사례
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: b7ee70e0-89c6-4cd3-8116-2f073d4a2f2f
source-git-commit: 8b970705f0da6a9e09de9fadb3e1a8c5f4814f9f
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 2%

---

# 스키마 편집 사례{#examples-of-schemas-edition}

![](../../assets/v7-only.svg)

## 표 확장 {#extending-a-table}

**nms:recipient** 스키마 수신자 테이블을 확장하려면 다음 절차를 적용합니다.

1. 다음 데이터를 사용하여 확장 스키마(**cus:extension**)를 만듭니다.

   ```
   <srcSchema mappingType="sql" name="extension" namespace="cus" xtkschema="xtk:srcSchema" extendedSchema="nms:recipient">  
     <enumeration basetype="string" default="area1" name="area">    
       <value label="Zone 1" name="area1"/>    
       <value label="Zone 2" name="area2"/>  
     </enumeration>  
   
     <element name="extension">    
       <dbindex name="area">      
         <keyfield xpath="location/@area"/>    
       </dbindex>      
   
       <attribute label="Loyalty code" name="fidelity" type="long"/>    
       <element name="location">      
         <attribute name="area" label="Purchasing zone" type="string" length="50" enum="area"/>    
       </element>  </element>  
   </srcSchema>
   ```

   이 예제에서 인덱싱된 필드(**fidelity**)가 추가되고, **위치** 요소(**nms:recipient** 스키마에 이미 존재함)가 열거된 필드(**영역**)로 보완됩니다.

   >[!IMPORTANT]
   >
   >확장 스키마를 참조하려면 **extendedSchema** 특성을 추가해야 합니다.

1. 확장 스키마가 **nms:recipient** 스키마이고 추가 데이터가 있는지 확인합니다.

   ```
   <schema dependingSchemas="cus:extension" mappingType="sql" name="recipient" namespace="nms" xtkschema="xtk:schema">
     ...
     <enumeration basetype="string" default="area1" name="area">    
       <value label="Zone 1" name="area1"/>    
       <value label="Zone 2" name="area2"/>  
     </enumeration>
     ...
     <element autopk="true" name="recipient" sqltable="NmsRecipient"> 
       <dbindex name="area">      
         <keyfield xpath="location/@area"/>    
       </dbindex>
   
       ...
       <attribute belongsTo="cus:extension" label="Loyalty code" name="fidelity" sqlname="iFidelity" type="long"/>
       <element name="location">
         ...
         <attribute enum="area" label="Purchasing zone" length="50" name="area" sqlname="sArea" type="string"/>
       </element>
       ...
     </element>
   </schema>
   ```

   데이터베이스 업데이트 마법사에서 생성된 SQL 스크립트는 다음과 같습니다.

   ```
   ALTER TABLE NmsRecipient ADD iFidelity INTEGER;
   UPDATE NmsRecipient SET iFidelity = 0;
   ALTER TABLE NmsRecipient ALTER COLUMN iFidelity SET NOT NULL;ALTER TABLE NmsRecipient ALTER COLUMN iFidelity SET Default 0;
   ALTER TABLE NmsRecipient ADD sArea VARCHAR(50); 
   CREATE INDEX NmsRecipient_area ON NmsRecipient(sArea);
   ```

## 연결된 컬렉션 테이블 {#linked-collection-table}

이 섹션에서는 카디널리티 1-N을 사용하여 수신자 테이블에 연결된 주문 테이블을 만드는 방법을 설명합니다.

테이블 원본 스키마 순서 지정:

```
<srcSchema label="Order" name="order" namespace="cus" xtkschema="xtk:srcSchema">  
  <element autopk="true" name="order">    
    <compute-string expr="@number" + '(' + ToString(@date) + ')'/>    
    
    <attribute label="Number" length="128" name="number" type="string"/>    
    <attribute desc="Order date" label="Date" name="date" type="datetime" default="GetDate()"/>    
    <attribute desc="order total" label="Total" name="total" type="double"/>    
    <element label="Recipient" name="recipient" revDesc="Orders associated with this recipient" revIntegrity="own" revLabel="Orders" target="nms:recipient" type="link"/>  
  </element>
</srcSchema>
```

수신자 테이블에 대한 링크의 조인에서 사용할 자동 생성된 기본 키를 만들려면 테이블 유형이 **자동**&#x200B;입니다.

생성된 스키마:

```
<schema label="Order" mappingType="sql" name="order" namespace="cus" xtkschema="xtk:schema">  
  <element autopk="true" label="Order" name="order" sqltable="CusOrder">    
    <compute-string expr="ToString(@date) + ' - ' + @number"/>    

    <dbindex name="id" unique="true">      
      <keyfield xpath="@id"/>    
    </dbindex>    

    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>    

    <dbindex name="recipientId">      
      <keyfield xpath="@recipient-id"/>    
    </dbindex>    

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iOrderId" type="long"/>    
    <attribute label="Number" length="128" name="number" sqlname="sNumber" type="string"/>    
    <attribute desc="Order date" label="Date" name="date" sqlname="tsDate" type="datetime"/>    
    <attribute desc="order total" label="Total" name="total" sqlname="Total" type="double"/>    
    <element label="Recipient" name="recipient" revLink="order" target="nms:recipient" type="link">      
      <join xpath-dst="@id" xpath-src="@recipient-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Recipient' link ('id' field)" name="recipient-id" sqlname="iRecipientId" type="long"/>  
   </element>
</schema>
```

테이블 작성 SQL 스크립트는 다음과 같습니다.

```
CREATE TABLE CusOrder(dTotal DOUBLE PRECISION NOT NULL Default 0, iOrderId INTEGER NOT NULL Default 0, iRecipientId INTEGER NOT NULL Default 0, sNumber VARCHAR(128), tsDate TIMESTAMP Default NULL);
CREATE UNIQUE INDEX CusOrder_id ON CusOrder(iOrderId);
CREATE INDEX CusOrder_recipientId ON CusOrder(iRecipientId);  
INSERT INTO CusOrder (iOrderId) VALUES (0); 
```

>[!NOTE]
>
>스크립트 끝에 SQL 명령 INSERT INTO를 사용하면 외부 조인을 시뮬레이션하기 위해 0으로 설정된 식별자 레코드를 삽입할 수 있습니다.

## 확장 테이블 {#extension-table}

확장 테이블을 사용하면 연결된 카디널리티 1-1의 테이블에서 기존 테이블의 내용을 확장할 수 있습니다.

확장 테이블의 목적은 테이블에서 지원되는 필드 수에 대한 제한을 방지하거나, 필요할 때 소비되는 데이터가 차지하는 공간을 최적화하는 것입니다.

확장 테이블 스키마 만들기(**cus:feature**):

```
<srcSchema mappingType="sql" name="feature" namespace="cus" xtkschema="xtk:srcSchema">  
  <element autopk="true" name="feature">    
    <attribute label="Children" name="children" type="byte"/>    
    <attribute label="Single" name="single" type="boolean"/>    
    <attribute label="Spouse first name" length="100" name="spouseFirstName" type="string"/>  
  </element>
</srcSchema>
```

수신자 테이블에 확장 스키마를 만들어 카디널리티 1-1 링크를 추가합니다.

```
<srcSchema extendedSchema="nms:recipient" label="Recipient" mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:srcSchema">  
  <element name="recipient">    
    <element desc="Features" integrity="own" label="Features" name="feature" revCardinality="single" revLink="recipient" target="cus:feature" type="link"/> 
  </element>
</srcSchema>
```

>[!NOTE]
>
>수신자 테이블과 확장 테이블 간의 링크의 정의는 외래 키를 포함하는 스키마에서 채워야 합니다.

확장 테이블을 만들기 위한 SQL 스크립트는 다음과 같습니다.

```
CREATE TABLE CusFeature(  iChildren NUMERIC(3) NOT NULL Default 0, iFeatureId INTEGER NOT NULL Default 0, iSingle NUMERIC(3) NOT NULL Default 0, sSpouseFirstName VARCHAR(100));
CREATE UNIQUE INDEX CusFeature_id ON CusFeature(iFeatureId);  
INSERT INTO CusFeature (iFeatureId) VALUES (0); 
```

받는 사람 테이블 SQL 업데이트 스크립트는 다음과 같습니다.

```
ALTER TABLE NmsRecipient ADD iFeatureId INTEGER;
UPDATE NmsRecipient SET iFeatureId = 0;
ALTER TABLE NmsRecipient ALTER COLUMN iFeatureId SET NOT NULL;
ALTER TABLE NmsRecipient ALTER COLUMN iFeatureId SET Default 0;
CREATE INDEX NmsRecipient_featureId ON NmsRecipient(iFeatureId);
```

## 오버플로 테이블 {#overflow-table}

오버플로 테이블은 확장 테이블(카디널리티 1-1)이지만, 확장할 테이블에 대한 링크의 선언이 오버플로 테이블의 스키마에서 채워집니다.

오버플로 테이블에는 확장할 테이블의 외래 키가 포함되어 있습니다. 따라서 확장할 테이블은 수정되지 않습니다. 두 테이블 간의 관계는 확장할 테이블의 기본 키 값입니다.

오버플로 테이블 스키마 만들기(**cus:overflow**):

```
<srcSchema label="Overflow" name="overflow" namespace="cus" xtkschema="xtk:srcSchema">  
  <element name="overflow">    
    <key internal="true" name="id">      
      <keyfield xlink="recipient"/>    
    </key>    

    <attribute label="Children" name="children" type="byte"/>    
    <attribute label="Single" name="single" type="boolean"/>    
    <attribute label="Spouse first name" length="100" name="spouseFirstName" type="string"/>  
    <element label="Customer" name="recipient" revCardinality="single" revIntegrity="own" revExternalJoin="true" target="nms:recipient" type="link"/>  
  </element>  
</srcSchema>
```

>[!NOTE]
>
>오버플로 테이블의 기본 키는 확장할 테이블에 대한 링크입니다(이 예제에서는 &quot;nms:recipient&quot; 스키마).

테이블 작성 SQL 스크립트는 다음과 같습니다.

```
CREATE TABLE CusOverflow(iChildren NUMERIC(3) NOT NULL Default 0, iRecipientId INTEGER NOT NULL Default 0, iSingle NUMERIC(3) NOT NULL Default 0, sSpouseFirstName VARCHAR(100));
CREATE UNIQUE INDEX CusOverflow2_id ON CusOverflow2(iRecipientId);  
```

## 관계 테이블 {#relationship-table}

관계 테이블을 사용하면 두 테이블을 카디널리티 N-N과 연결할 수 있습니다. 이 표에는 연결할 테이블의 외래 키만 포함되어 있습니다.

그룹(**nms:group**)과 수신자(**nms:recipient**) 간의 관계 테이블의 예.

관계 테이블의 소스 스키마:

```
<srcSchema name="rcpGrpRel" namespace="cus">
  <element name="rcpGrpRel">
    <key internal="true" name="id">      
      <keyfield xlink="rcpGroup"/>      
      <keyfield xlink="recipient"/>    
    </key>

    <element integrity="neutral" label="Recipient" name="recipient" revDesc="Groups to which this recipient belongs" revIntegrity="own" revLabel="Groups" target="nms:recipient" type="link"/>    
    <element integrity="neutral" label="Group" name="rcpGroup" revDesc="Recipients in the group" revIntegrity="own" revLabel="Recipients" revLink="rcpGrpRel" target="nms:group" type="link"/>
  </element>
</srcSchema>
```

생성된 스키마는 다음과 같습니다.

```
<schema mappingType="sql" name="rcpGrpRel" namespace="cus" xtkschema="xtk:schema">  
  <element name="rcpGrpRel" sqltable="CusRcpGrpRel">    
    <compute-string expr="ToString([@rcpGroup-id]) + ',' + ToString([@recipient-id])"/>    
    <dbindex name="id" unique="true">      
      <keyfield xpath="@rcpGroup-id"/>      
      <keyfield xpath="@recipient-id"/>    
    </dbindex>    

    <key internal="true" name="id">      
      <keyfield xpath="@rcpGroup-id"/>      
      <keyfield xpath="@recipient-id"/>    
    </key>    

    <dbindex name="rcpGroupId">      
      <keyfield xpath="@rcpGroup-id"/>    
    </dbindex>    
    <dbindex name="recipientId">      
      <keyfield xpath="@recipient-id"/>    
    </dbindex>    

    <element integrity="neutral" label="Recipient" name="recipient" revLink="rcpGrpRel" target="nms:recipient" type="link">      
      <join xpath-dst="@id" xpath-src="@recipient-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Recipient' link ('id' field)" name="recipient-id" sqlname="iRecipientId" type="long"/>    

    <element integrity="neutral" label="Group" name="rcpGroup" revLink="rcpGrpRel" target="nms:group" type="link">      
      <join xpath-dst="@id" xpath-src="@rcpGroup-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Group' link ('id' field)" name="rcpGroup-id" sqlname="iRcpGroupId" type="long"/>  
  </element>
</schema>
```

테이블 작성 SQL 스크립트는 다음과 같습니다.

```
CREATE TABLE CusRcpGrpRel( iRcpGroupId INTEGER NOT NULL Default 0, iRecipientId INTEGER NOT NULL Default 0);
CREATE UNIQUE INDEX CusRcpGrpRel_id ON CusRcpGrpRel(iRcpGroupId, iRecipientId);
CREATE INDEX CusRcpGrpRel_recipientId ON CusRcpGrpRel(iRecipientId);
```

## 사용 사례: 기존 참조 테이블에 필드 연결 {#uc-link}

이 사용 사례에서는 기존 참조 테이블을 기본 제공 Adobe Campaign 열거형 메커니즘(열거형, userEnum 또는 dbEnum)의 대체 요소로 사용하는 방법을 보여 줍니다.

기존 참조 테이블을 스키마에서 열거형으로 사용할 수도 있습니다. 이 작업은 테이블과 참조 테이블 간의 링크를 만들고 **displayAsField=&quot;true&quot;** 속성을 추가하여 수행할 수 있습니다.

이 예에서 참조 테이블에는 은행 이름과 식별자 목록이 들어 있습니다.

```
<srcSchema entitySchema="xtk:srcSchema" img="cus:bank16x16.png" label="Bank" mappingType="sql" name="bank" namespace="cus"
xtkschema="xtk:srcSchema">
    <element img="cus:bank16x16.png" label="Banks" name="bank">
        <compute-string expr="@name"/>
        <key name="id">
            <keyfield xpath="@id"/>
        </key>
        <attribute label="Bank Id" name="id" type="short"/>
        <attribute label="Name" length="64" name="name" type="string"/>
     </element> 
</srcSchema>
```

이 참조 테이블을 사용하는 테이블에서 링크를 정의하고 **displayAsField=&quot;true&quot;** 속성을 추가합니다.

```
<element displayAsField="true" label="Bank" name="bank" target="cus:bank" type="link" noDbIndex="true"/>
```

사용자 인터페이스에 링크가 표시되지 않고 필드가 표시됩니다. 사용자가 해당 필드를 선택하면 참조 테이블에서 값을 선택하거나 자동 완료 기능을 사용할 수 있습니다.

![](assets/schema-edition-ex.png)

* 자동 완료되도록 하려면 참조 테이블에서 계산 문자열을 정의해야 합니다.

* Adobe Campaign이 링크의 소스 테이블에 저장된 값에 인덱스를 만들지 않도록 링크 정의에 **noDbIndex=&quot;true&quot;** 속성을 추가합니다.

## 관련 항목

* [열거형 작업](../../platform/using/managing-enumerations.md)

* [Campaign 스키마 시작](../../configuration/using/about-schema-edition.md)

* [데이터베이스 구조 업데이트](../../configuration/using/updating-the-database-structure.md)
