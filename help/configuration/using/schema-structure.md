---
product: campaign
title: 스키마 구조
description: 스키마 구조
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
source-git-commit: 1bb1365ce5a4eb89447c5d736a42cd470c7f3bba
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 1%

---

# 스키마 구조{#schema-structure}

![](../../assets/v7-only.svg)

의 기본 구조 `<srcschema>` 는 다음과 같습니다.

```
<srcSchema>
    <enumeration>
        ...          //definition of enumerations
    </enumeration>
   
    <element>         //definition of the root <element>    (mandatory)

        <compute-string/>  //definition of a compute-string
        <dbindex>
            ...        //definition of indexes
        </dbindex>
        <key>
            ...        //definition of keys
        </key>
        <sysFilter>
            ...           //definition of filters
        </sysFilter>
        <attribute>
            ...             //definition of fields
        </attribute>
    
            <element>           //definition of sub-<element> 
                  <attribute>           //(collection, links or XML)
                  ...                         //and additional fields
                  </attribute>
                ...
            </element>
      
    </element> 

        <methods>                 //definition of SOAP methods
            <method>
                ...
            </method>
            ...
    </methods>  
          
</srcSchema>
```

데이터 스키마의 XML 문서에는 **`<srcschema>`** 루트 요소가 있는 요소 **이름** 및 **namespace** 스키마 이름 및 해당 네임스페이스를 채울 속성입니다.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

다음 XML 컨텐츠를 사용하여 데이터 스키마의 구조를 설명하겠습니다.

```
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

해당 데이터 스키마 사용:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email"/>
    <attribute name="created"/>
    <attribute name="gender"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

## 설명 {#description}

스키마의 시작 지점은 기본 요소입니다. 스키마와 동일한 이름을 가지며 루트 요소의 자식이어야 하므로 쉽게 식별할 수 있습니다. 컨텐츠의 설명은 이 요소로 시작됩니다.

이 예제에서 기본 요소는 다음 행으로 표시됩니다.

```
<element name="recipient">
```

요소 **`<attribute>`** 및 **`<element>`** 기본 요소 다음에 나오는 기본 요소를 사용하여 XML 구조에서 데이터 항목의 위치 및 이름을 정의할 수 있습니다.

샘플 스키마에서는 다음과 같습니다.

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

다음 규칙에 부합해야 합니다.

* 각 **`<element>`** 및 **`<attribute>`** 는 **이름** 속성을 사용합니다.

   >[!IMPORTANT]
   >
   >요소의 이름은 간결해야 하며, 바람직하게는 영어로 작성되어야 하며 XML 이름 지정 규칙에 따라 인증된 문자만 포함해야 합니다.

* 전용 **`<element>`** 요소를 포함할 수 있습니다. **`<attribute>`** 요소 및 **`<element>`** XML 구조의 요소
* An **`<attribute>`** 요소에는 **`<element>`**.
* 의 사용 **`<elements>`** 여러 줄 데이터 문자열에서 를 사용하는 것이 좋습니다.

## 데이터 유형 {#data-types}

데이터 유형은 **유형** 의 속성 **`<attribute>`** 및 **`<element>`** 요소를 생성하지 않습니다.

자세한 목록은 [`<attribute>` 요소](../../configuration/using/schema/attribute.md) 그리고 [`<element>` 요소](../../configuration/using/schema/element.md)).

이 속성을 채우지 않으면, **string** 요소에 하위 요소가 포함되지 않은 경우 는 기본 데이터 유형입니다. 그럴 경우 계층 구조를 구성하는 데만 사용됩니다(**`<location>`** 요소를 생성하지 않습니다.

스키마에서 지원되는 데이터 유형은 다음과 같습니다.

* **string**: 문자열. 예: 이름, 도시 등

   크기는 를 통해 지정할 수 있습니다 **length** 속성(선택 사항, 기본값 &quot;255&quot;).

* **부울**: 부울 필드. 가능한 값의 예: true/false, 0/1, 예/아니요 등
* **byte**, **short**, **장기간**: 정수(1바이트, 2바이트, 4바이트). 예: 연령, 계좌 번호, 포인트 수 등
* **이중**: 배정밀도 부동 소수점 번호 예: 가격, 비율 등
* **날짜**, **datetime**: 날짜 및 날짜 + 시간. 예: 생년월일, 구매 날짜 등
* **datetimeenotz**: 날짜 + 시간(시간대 데이터 없음)
* **시간 간격**: 지속 시간. 예: 연수.
* **메모**: 긴 텍스트 필드(여러 줄). 예: 설명, 설명 등
* **uuid**: GUID를 지원하는 &quot;uniqueidentifier&quot; 필드(Microsoft SQL Server에서만 지원됨)입니다.

   >[!NOTE]
   >
   >를 포함하려면 다음을 수행하십시오 **uuid** Microsoft SQL Server 이외의 엔진의 필드에 &quot;newuuid()&quot; 함수를 추가하고 해당 기본값으로 완료해야 합니다.

입력한 유형을 사용하는 예제 스키마는 다음과 같습니다.

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email" type="string" length="80"/>
    <attribute name="created" type="datetime"/>
    <attribute name="gender" type="byte"/>
    <element name="location">
      <attribute name="city" type="string" length="50"/>
   </element>
  </element>
</srcSchema>
```

### Adobe Campaign/DBMS 데이터 유형 매핑 {#mapping-the-types-of-adobe-campaign-dbms-data}

아래 표에는 다른 데이터베이스 관리 시스템에 대해 Adobe Campaign에서 생성한 데이터 유형에 대한 매핑이 나열되어 있습니다.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>PostgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> <strong>MS SQL</strong><br /> </td> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 문자열<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2(유니코드 경우 NVARCHAR2)<br /> </td> 
   <td> VARCHAR(유니코드 경우 VARCHAR 문자 집합 유니코드)<br /> </td> 
   <td> VARCHAR<br /> </td> 
   <td> VARCHAR(유니코드 경우 NVARCHAR)<br /> </td> 
  </tr> 
  <tr> 
   <td> 부울<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> 숫자(3)<br /> </td> 
   <td> 숫자(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 바이트<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> 숫자(3)<br /> </td> 
   <td> 숫자(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Short<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> 숫자(5)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> SMALLINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 더블<br /> </td> 
   <td> 이중 정밀도<br /> </td> 
   <td> 부동<br /> </td> 
   <td> 부동<br /> </td> 
   <td> 이중<br /> </td> 
   <td> 부동<br /> </td> 
  </tr> 
  <tr> 
   <td> Long<br /> </td> 
   <td> 정수<br /> </td> 
   <td> 숫자(10)<br /> </td> 
   <td> 정수<br /> </td> 
   <td> 정수<br /> </td> 
   <td> INT<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> 숫자(20)<br /> </td> 
   <td> 숫자(20)<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> BIGINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 날짜<br /> </td> 
   <td> 날짜<br /> </td> 
   <td> 날짜<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> 날짜<br /> </td> 
   <td> DATETIME<br /> </td> 
  </tr> 
  <tr> 
   <td> 시간<br /> </td> 
   <td> 시간<br /> </td> 
   <td> 부동<br /> </td> 
   <td> 시간<br /> </td> 
   <td> 시간<br /> </td> 
   <td> 부동<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetime<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> 날짜<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIMEOFFSET<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> 날짜<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIME2<br /> </td> 
  </tr> 
  <tr> 
   <td> 타임판<br /> </td> 
   <td> 이중 정밀도<br /> </td> 
   <td> 부동<br /> </td> 
   <td> 부동<br /> </td> 
   <td> 이중<br /> </td> 
   <td> 부동<br /> </td> 
  </tr> 
  <tr> 
   <td> 메모<br /> </td> 
   <td> 텍스트<br /> </td> 
   <td> CLOB(유니코드 경우 NCLOB)<br /> </td> 
   <td> CLOB(유니코드 경우 CLOB 문자 집합 유니코드)<br /> </td> 
   <td> CLOB(6M)<br /> </td> 
   <td> 텍스트(유니코드 경우 NTEXT)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB(4M)<br /> </td> 
   <td> 이미지<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 속성 {#properties}

다음 **`<elements>`** 및 **`<attributes>`** 데이터 스키마의 요소는 다양한 속성으로 보강할 수 있습니다. 현재 요소를 설명하기 위해 레이블을 채울 수 있습니다.

### 레이블 및 설명 {#labels-and-descriptions}

* 다음 **레이블** 속성을 사용하면 간단한 설명을 입력할 수 있습니다.

   >[!NOTE]
   >
   >레이블은 인스턴스의 현재 언어와 연결됩니다.

   **예제**:

   ```
   <attribute name="email" type="string" length="80" label="Email"/>
   ```

   레이블은 Adobe Campaign 클라이언트 콘솔 입력 양식에서 볼 수 있습니다.

   ![](assets/d_ncs_integration_schema_label.png)

* 다음 **desc** 속성을 사용하면 긴 설명을 입력할 수 있습니다.

   설명은 Adobe Campaign 클라이언트 콘솔 기본 창의 상태 표시줄에 있는 입력 양식에서 볼 수 있습니다.

   >[!NOTE]
   >
   >설명은 인스턴스의 현재 언어와 연결됩니다.

   **예제**:

   ```
   <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
   ```

### 기본값 {#default-values}

다음 **기본** 속성을 사용하면 콘텐츠 작성 시 기본값을 반환하는 표현식을 정의할 수 있습니다.

값은 XPath 언어와 호환되는 표현식이어야 합니다. 자세한 내용은 [XPath를 사용한 참조](../../configuration/using/schema-structure.md#referencing-with-xpath).

**예제**:

* 현재 날짜: **default=&quot;GetDate()&quot;**
* 카운터: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

   이 예에서 기본값은 문자열의 연결을 사용하여 생성되고 **카운터 값** 자유 카운터 이름을 사용하는 함수입니다. 반환된 숫자는 삽입할 때마다 1씩 증가합니다.

   >[!NOTE]
   >
   >Adobe Campaign 클라이언트 콘솔에서 **[!UICONTROL Administration>Counters]** 노드를 사용하여 카운터를 관리합니다.

기본값을 필드에 연결하려면 `<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>` : 엔티티를 만들 때 기본값으로 필드를 미리 채울 수 있습니다. 값은 기본 SQL 값이 아닙니다.

`<sqldefault>` : 필드를 만들 때 값을 추가할 수 있습니다. 이 값은 SQL 결과로 나타납니다. 스키마 업데이트 중에는 새 레코드만 이 값의 영향을 받습니다.

### 열거형 {#enumerations}

#### 자유 열거형 {#free-enumeration}

다음 **userEnum** 속성을 사용하면 이 필드를 통해 입력한 값을 암기하고 표시할 자유 열거형을 정의할 수 있습니다. 구문은 다음과 같습니다.

**userEnum=&quot;열거형 이름&quot;**

열거에 지정된 이름을 자유롭게 선택하고 다른 필드와 공유할 수 있습니다.

이러한 값은 입력 양식의 드롭다운 목록에 표시됩니다.

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>Adobe Campaign 클라이언트 콘솔에서 **[!UICONTROL Administration > Enumerations]** 노드는 열거형을 관리하는 데 사용됩니다.

#### 열거형 설정 {#set-enumeration}

다음 **enum** 속성을 사용하면 가능한 값 목록을 미리 알 때 사용되는 고정 열거형을 정의할 수 있습니다.

다음 **enum** 특성은 기본 요소 외부에 있는 스키마에 채워진 열거형 클래스의 정의를 나타냅니다.

열거형을 사용하면 일반 입력 필드에 값을 입력하는 대신 드롭다운 목록에서 값을 선택할 수 있습니다.

![](assets/d_ncs_integration_schema_enum.png)

데이터 스키마의 열거형 선언의 예:

```
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

열거형은 를 통해 기본 요소 외부에 선언됩니다 **`<enumeration>`** 요소를 생성하지 않습니다.

열거형 속성은 다음과 같습니다.

* **baseType**: 값과 연관된 데이터 유형,
* **레이블**: 열거형에 대한 설명,
* **이름**: 열거형의 이름,
* **기본**: 열거형의 기본값입니다.

열거형 값은 **`<value>`** 다음 속성을 갖는 요소:

* **이름**: 내부적으로 저장된 값의 이름,
* **레이블**: 그래픽 인터페이스를 통해 표시되는 레이블입니다.

#### dbenum 열거형 {#dbenum-enumeration}

* 다음 **디베늄** 속성을 사용하면 다음과 유사한 속성을 갖는 열거형을 정의할 수 있습니다 **enum** 속성을 사용합니다.

   하지만, **이름** 속성은 값을 내부적으로 저장하지 않고 스키마를 수정하지 않고 관련 테이블을 확장할 수 있는 코드를 저장합니다.

   값은 **[!UICONTROL Administration>Enumerations]** 노드 아래에 있어야 합니다.

   이 열거형은 캠페인의 특성을 지정하는 데 사용됩니다(예: ).

   ![](assets/d_ncs_configuration_schema_dbenum.png)

### 예제 {#example}

다음은 속성이 채워진 예제 스키마입니다.

```
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="male" value="1"/>   
    <value name="female" label="female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
    <attribute name="created" type="datetime" label="Date of creation" default="GetDate()"/>
    <attribute name="gender" type="byte" label="gender" enum="gender"/>
    <element name="location" label="Location">
      <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
   </element>
  </element>
</srcSchema>
```

## 컬렉션 {#collections}

컬렉션은 동일한 이름과 동일한 계층 수준을 갖는 요소 목록입니다.

다음 **언바운드** 속성이 &quot;true&quot; 값으로 설정되어 있으면 수집 요소를 채울 수 있습니다.

**예**: 의 정의 **`<group>`** 스키마의 컬렉션 요소.

```
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

XML 컨텐츠의 투영 사용:

```
<group label="Group1"/>
<group label="Group2"/>
```

## XPath를 사용한 참조 {#referencing-with-xpath}

XPath 언어는 Adobe Campaign에서 데이터 스키마에 속하는 요소나 속성을 참조하는 데 사용됩니다.

XPath는 XML 문서의 트리에서 노드를 찾을 수 있는 구문입니다.

요소는 이름으로 지정되며, 특성은 문자 앞에 &quot;@&quot; 가 있는 이름으로 지정됩니다.

**예제**:

* **@email**: 이메일을 선택하고
* **위치/@city**: 에서 &quot;city&quot; 속성을 선택합니다. **`<location>`** 요소
* **../@email**: 현재 요소의 상위 요소에서 전자 메일 주소를 선택합니다.
* **그룹`[1]/@label`**: 첫 번째 항목의 하위인 &quot;label&quot; 속성을 선택합니다 **`<group>`** 컬렉션 요소
* **그룹`[@label='test1']`**: 의 하위인 &quot;label&quot; 속성을 선택합니다 **`<group>`** 요소 및 &quot;test1&quot; 값 포함

>[!NOTE]
>
>경로가 하위 요소를 교차하면 추가 제한이 추가됩니다. 이 경우 대괄호 사이에 다음 표현식을 배치해야 합니다.
>
>* **위치/@city** 는 유효하지 않습니다. 다음 사용 **`[location/@city]`**
>* **`[@email]`** 및 **@email** 동일함
>


다음 산술 연산과 같이 복잡한 표현식을 정의할 수도 있습니다.

* **@gender+1**: 의 콘텐츠에 1을 추가합니다. **성별** attribute,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: 괄호 사이에 만든 날짜에 추가된 전자 메일 주소의 값을 가져와서 문자열을 구성합니다(문자열 유형의 경우 따옴표로 상수 입력).

이 언어의 가능성을 높이기 위해 표현식에 높은 수준의 기능이 추가되었습니다.

Adobe Campaign 클라이언트 콘솔의 모든 표현식 편집기를 통해 사용 가능한 함수 목록에 액세스할 수 있습니다.

![](assets/d_ncs_integration_schema_function.png)

**예제**:

* **GetDate()**: 현재 날짜 반환
* **Year(@created)**: 생성된 속성에 포함된 날짜의 연도를 반환합니다.
* **GetEmailDomain(@email)**: 이메일 주소의 도메인을 반환합니다.

## 계산 문자열을 통해 문자열 작성 {#building-a-string-via-the-compute-string}

A **계산 문자열** 는 스키마와 연결된 테이블의 레코드를 나타내는 문자열을 구성하는 데 사용되는 XPath 표현식입니다. **계산 문자열** 주로 그래픽 인터페이스에서 선택한 레코드의 레이블을 표시하는 데 사용됩니다.

다음 **계산 문자열** 는 **`<compute-string>`** 데이터 스키마의 기본 요소 아래에 있는 요소. An **expr** 특성에 XPath 식이 포함되어 있어 표시를 계산합니다.

**예**: 수신자 테이블의 계산 문자열.

```
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

수신자에 대한 계산된 문자열 결과: **Doe John (john.doe@aol.com)**

>[!NOTE]
>
>스키마에 계산 문자열이 없으면 계산 문자열이 기본적으로 스키마의 기본 키 값으로 채워집니다.
