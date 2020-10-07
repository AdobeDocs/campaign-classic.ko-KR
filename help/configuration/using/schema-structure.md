---
title: 스키마 구조
seo-title: 스키마 구조
description: 스키마 구조
seo-description: null
page-status-flag: never-activated
uuid: 9be70907-6154-4890-91e8-fd0fac30ab05
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: b5c8faf7-d0ae-4d95-b7fe-6ef9674a33d2
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1566'
ht-degree: 1%

---


# 스키마 구조{#schema-structure}

의 기본 구조는 `<srcschema>` 다음과 같습니다.

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

스키마 이름 **`<srcschema>`** 및 해당 네임스페이스를 채우려면 데이터 스키마의 XML 문서에 **이름** 및 **네임스페이스** 특성이 있는 루트 요소를포함해야 합니다.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

다음 XML 내용을 사용하여 데이터 스키마의 구조를 설명하겠습니다.

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

스키마의 진입점은 기본요소입니다. 스키마와 동일한 이름을 가지며 루트 요소의 자식이어야 하므로 쉽게 식별할 수 있습니다. 컨텐츠의 설명은 이 요소로 시작합니다.

이 예에서 주 요소는 다음 줄로 표시됩니다.

```
<element name="recipient">
```

기본 요소 **`<attribute>`** 를 **`<element>`** 따르는 요소와 이름을 XML 구조에서 정의할 수 있습니다.

샘플 스키마에서는 다음과 같습니다.

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

다음 규칙이 따라야 합니다.

* 각 **`<element>`** 과 **`<attribute>`** 는 이름 속성을 통해 이름으로 식별되어야 **합니다** .

   >[!IMPORTANT]
   >
   >요소의 이름은 간결해야 하며, 특히 영어로 작성되어야 하며 XML 명명 규칙에 따라 권한이 있는 문자만 포함해야 합니다.

* XML **`<element>`** 구조에는 **`<attribute>`** 요소 및 **`<element>`** 요소만 포함할 수 있습니다.
* 요소 **`<attribute>`** 의 이름은 고유해야 합니다 **`<element>`**.
* 여러 줄 데이터 문자열 **`<elements>`** 에서 사용하는 것이 좋습니다.

## 데이터 유형 {#data-types}

데이터 유형은 **및** 요소의 **`<attribute>`** type **`<element>`** 속성을 통해입력됩니다.

자세한 목록은 요소 [`<attribute>` 및](../../configuration/using/elements-and-attributes.md#attribute--element) 요소 [`<element>`](../../configuration/using/elements-and-attributes.md#element--element)설명에 있습니다.

이 속성을 채우지 않으면 **문자열이** 기본 데이터 유형입니다. 단, 요소에 하위 요소가 포함되어 있지 않습니다. 그럴 경우 계층적 요소(예: 요소)를 구조화하는&#x200B;**`<location>`** 데에만 사용됩니다.

스키마에서 지원되는 데이터 유형은 다음과 같습니다.

* **문자열**:문자열. 예:이름, 마을 등.

   크기는 **length** 속성을 통해 지정할 수 있습니다(선택 사항, 기본값 &quot;255&quot;).

* **boolean**:부울 필드. 가능한 값의 예:true/false, 0/1, 예/아니요 등
* **byte**, **short**, **long**:정수(1바이트, 2바이트, 4바이트). 예:연령, 계정 번호, 포인트 수 등
* **double**:배정밀도 부동 소수점 숫자 예:가격, 요금 등
* **date**, **datetime**:날짜 및 날짜 + 시간. 예:생년월일, 구매 날짜 등
* **datetimenotz**:날짜 + 시간대 데이터 없음
* **timespan**:기간. 예:상사.
* **메모**:긴 텍스트 필드(여러 줄). 예:설명, 주석 등
* **uuid**:GUID를 지원하는 &quot;uniqueidentifier&quot; 필드(Microsoft SQL Server에서만 지원됨)

   >[!NOTE]
   >
   >Microsoft SQL Server 이외의 엔진에 **uuid** 필드를 포함하려면 &quot;newuuid()&quot; 함수를 추가하고 기본값으로 완료해야 합니다.

입력한 유형이 있는 예제 스키마는 다음과 같습니다.

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

아래 표에는 다른 데이터베이스 관리 시스템에 대해 Adobe Campaign이 생성한 데이터 유형에 대한 매핑이 나열되어 있습니다.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> <strong>Teradata</strong><br /> </td> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> <strong>MS SQL</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 문자열<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2(유니코드의 경우 NVARCHAR2)<br /> </td> 
   <td> VARCHAR(유니코드 경우 VARCHAR 문자 집합 유니코드)<br /> </td> 
   <td> VARCHAR<br /> </td> 
   <td> VARCHAR(유니코드의 경우 NVARCHAR)<br /> </td> 
  </tr> 
  <tr> 
   <td> 부울<br /> </td> 
   <td> SMALINT<br /> </td> 
   <td> 번호(3)<br /> </td> 
   <td> 숫자(3)<br /> </td> 
   <td> SMALINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 바이트<br /> </td> 
   <td> SMALINT<br /> </td> 
   <td> 번호(3)<br /> </td> 
   <td> 숫자(3)<br /> </td> 
   <td> SMALINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Short<br /> </td> 
   <td> SMALINT<br /> </td> 
   <td> 번호(5)<br /> </td> 
   <td> SMALINT<br /> </td> 
   <td> SMALINT<br /> </td> 
   <td> SMALINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 더블<br /> </td> 
   <td> 배정밀도<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> DOUBLE<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Long<br /> </td> 
   <td> 정수<br /> </td> 
   <td> NUMBER(10)<br /> </td> 
   <td> 정수<br /> </td> 
   <td> 정수<br /> </td> 
   <td> INT<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> 번호(20)<br /> </td> 
   <td> 숫자(20)<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> BIGINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 날짜<br /> </td> 
   <td> DATE<br /> </td> 
   <td> DATE<br /> </td> 
   <td> 타임스탬프<br /> </td> 
   <td> DATE<br /> </td> 
   <td> DATETIME<br /> </td> 
  </tr> 
  <tr> 
   <td> Time<br /> </td> 
   <td> TIME<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> TIME<br /> </td> 
   <td> TIME<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> 날짜/시간<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATE<br /> </td> 
   <td> 타임스탬프<br /> </td> 
   <td> 타임스탬프<br /> </td> 
   <td> MS SQL &lt; 2008:DATETIME<br /> MS SQL &gt;= 2012:DATETIMEOFFSET<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATE<br /> </td> 
   <td> 타임스탬프<br /> </td> 
   <td> 타임스탬프<br /> </td> 
   <td> MS SQL &lt; 2008:DATETIME<br /> MS SQL &gt;= 2012:DATETIME2<br /> </td> 
  </tr> 
  <tr> 
   <td> Timespan<br /> </td> 
   <td> 배정밀도<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> DOUBLE<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Memo<br /> </td> 
   <td> TEXT<br /> </td> 
   <td> CLOB(유니코드의 경우 NCLB)<br /> </td> 
   <td> CLOB(유니코드 경우 CLOB 문자 집합 유니코드)<br /> </td> 
   <td> CLOB(6M)<br /> </td> 
   <td> 텍스트(유니코드 경우 NTEXT)<br /> </td> 
  </tr> 
  <tr> 
   <td> 물방울<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB(4M)<br /> </td> 
   <td> IMAGE<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 속성 {#properties}

데이터 스키마 **`<elements>`** 의 및 **`<attributes>`** 요소는 다양한 속성을 사용하여 농축될 수 있습니다. 현재 요소를 설명하기 위해 레이블을 채울 수 있습니다.

### 레이블 및 설명 {#labels-and-descriptions}

* label **속성을 사용하여** 간단한 설명을 입력할 수 있습니다.

   >[!NOTE]
   >
   >레이블은 인스턴스의 현재 언어와 연결됩니다.

   **예제**:

   ```
   <attribute name="email" type="string" length="80" label="Email"/>
   ```

   레이블은 Adobe Campaign 클라이언트 콘솔 입력 양식에서 볼 수 있습니다.

   ![](assets/d_ncs_integration_schema_label.png)

* desc **속성을** 사용하면 긴 설명을 입력할 수 있습니다.

   설명은 Adobe Campaign 클라이언트 콘솔 주 창의 상태 표시줄에 있는 입력 양식에서 볼 수 있습니다.

   >[!NOTE]
   >
   >설명은 인스턴스의 현재 언어와 연결됩니다.

   **예제**:

   ```
   <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
   ```

### 기본값 {#default-values}

기본 **** 속성을 사용하면 컨텐츠 생성 시 기본값을 반환하는 표현식을 정의할 수 있습니다.

값은 XPath 언어와 호환되는 표현식이어야 합니다. 자세한 내용은 XPath로 [참조를 참조하십시오](../../configuration/using/schema-structure.md#referencing-with-xpath).

**예제**:

* 현재 날짜: **default=&quot;GetDate()&quot;**
* 카운터: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

   이 예제에서 기본값은 문자열의 연결과 무료 카운터 이름으로 **CounterValue** 함수를 호출하는 방법으로 구성됩니다. 반환되는 번호는 각 삽입에서 1씩 증가합니다.

   >[!NOTE]
   >
   >Adobe Campaign 클라이언트 콘솔에서는 **[!UICONTROL Administration>Counters]** 노드를 사용하여 카운터를 관리합니다.

기본값을 필드에 연결하려면 `<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>` :개체를 만들 때 기본값으로 필드를 미리 채울 수 있습니다. 이 값은 기본 SQL 값이 아닙니다.

`<sqldefault>` :필드를 만들 때 값을 추가할 수 있습니다. 이 값은 SQL 결과로 나타납니다. 스키마 업데이트 중에 새 레코드만 이 값에 영향을 받습니다.

### 열거형 {#enumerations}

#### 무료 열거형 {#free-enumeration}

userEnum **** 속성을 사용하면 이 필드를 통해 입력한 값을 암기하고 표시하는 자유 열거형을 정의할 수 있습니다. 구문은 다음과 같습니다.

**userEnum=&quot;열거형 이름&quot;**

열거에 지정된 이름은 자유롭게 선택하고 다른 필드와 공유할 수 있습니다.

이러한 값은 입력 양식의 드롭다운 목록에 표시됩니다.

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>Adobe Campaign 클라이언트 콘솔에서 **[!UICONTROL Administration > Enumerations]** 노드가 열거형을 관리하는 데 사용됩니다.

#### 열거형 설정 {#set-enumeration}

enum **속성을** 사용하면 가능한 값 목록을 미리 알고 있을 때 사용되는 고정 열거형을 정의할 수 있습니다.

enum **** 특성이 기본 요소 외부에 있는 스키마에 채워진 열거형 클래스의 정의를 참조합니다.

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

열거형은 요소를 통해 기본 요소 외부에 **`<enumeration>`** 선언됩니다.

열거형 속성은 다음과 같습니다.

* **baseType**:값과 연결된 데이터 유형,
* **레이블**:열거에 대한 설명,
* **이름**:열거형의 이름,
* **기본값**:열거형의 기본값.

열거형 값은 다음 특성을 가진 **`<value>`** 요소에서 선언됩니다.

* **이름**:내부적으로 저장된 값의 이름,
* **레이블**:그래픽 인터페이스를 통해 표시되는 레이블입니다.

#### dbenum 열거형 {#dbenum-enumeration}

* dbenum **** 속성을 사용하면 속성이 enum **** 속성과 유사한 열거형을 정의할 수 있습니다.

   하지만 **name** 속성은 값을 내부적으로 저장하지 않고, 이 속성에는 스키마를 수정하지 않고 관련 테이블을 확장할 수 있는 코드가 저장됩니다.

   값은 노드를 통해 **[!UICONTROL Administration>Enumerations]** 정의됩니다.

   이 열거형은 예를 들어 캠페인의 특성을 지정하는 데 사용됩니다.

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

컬렉션은 동일한 이름과 동일한 계층 수준의 요소 목록입니다.

값 &quot;true&quot;로 **언바운드** 속성을 사용하면 컬렉션 요소를 채울 수 있습니다.

**예**:스키마에 있는 컬렉션 **`<group>`** 요소의 정의입니다.

```
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

XML 컨텐츠 투영:

```
<group label="Group1"/>
<group label="Group2"/>
```

## XPath와 참조 {#referencing-with-xpath}

XPath 언어는 데이터 스키마에 속하는 요소나 속성을 참조하기 위해 Adobe Campaign에서 사용됩니다.

XPath는 XML 문서의 트리에서 노드를 찾을 수 있는 구문입니다.

요소는 이름으로 지정되며 속성은 문자 앞에 &quot;@&quot;가 붙은 이름으로 지정됩니다.

**예제**:

* **@email**:이메일을 선택하고
* **location/@city**:요소 아래의 &quot;city&quot; 속성을 **`<location>`** 선택합니다.
* **../@email**:현재 요소의 상위 요소에서 이메일 주소를 선택합니다.
* **그룹`[1]/@label`**:첫 번째 **`<group>`** 컬렉션 요소의 하위 항목인 &quot;label&quot; 속성을 선택합니다.
* **그룹`[@label='test1']`**:요소의 하위 요소이고 값 &quot;test1&quot;을 포함하는 &quot;label&quot; 속성을 **`<group>`** 선택합니다.

>[!NOTE]
>
>경로가 하위 요소를 교차할 때 추가 제한이 추가됩니다. 이 경우 다음 표현식을 대괄호 사이에 배치해야 합니다.
>
>* **location/@city** is not valid;사용 **`[location/@city]`**
>* **`[@email]`** 및 **@email** 은 동일합니다.

>



다음 산술 연산과 같이 복잡한 표현식을 정의할 수도 있습니다.

* **@gender+1**:gender 속성 컨텐츠에 1을 **추가합니다** .
* **@email + &#39;(&#39;+@created+&#39;)**:괄호 사이에 작성 날짜에 추가된 전자 메일 주소 값을 가져와 문자열을 생성합니다(문자열 유형에 대해서는 따옴표로 상수를 넣습니다).

이 언어의 가능성을 높이기 위해 고급 기능이 표현식에 추가되었습니다.

Adobe Campaign 클라이언트 콘솔의 모든 표현식 편집기를 통해 사용 가능한 함수 목록에 액세스할 수 있습니다.

![](assets/d_ncs_integration_schema_function.png)

**예제**:

* **GetDate()**:현재 날짜를 반환합니다.
* **연도(@created)**:&quot;created&quot; 속성에 포함된 날짜의 연도를 반환합니다.
* **GetEmailDomain(@email)**:전자 메일 주소의 도메인을 반환합니다.

## 계산 문자열을 통해 문자열 작성 {#building-a-string-via-the-compute-string}

계산 문자열 **은** 스키마와 연관된 테이블의 레코드를 나타내는 문자열을 구성하는 데 사용되는 XPath 식입니다. **계산 문자열은** 주로 선택한 레코드의 레이블을 표시하는 그래픽 인터페이스에서 사용됩니다.

계산 **문자열은** 데이터 스키마의 기본 요소 아래의 **`<compute-string>`** 요소를 통해 정의됩니다. expr **속성에는** 표시를 계산하는 XPath 식이 포함됩니다.

**예**:받는 사람 테이블의 계산 문자열.

```
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

받는 사람에 대한 계산된 문자열 결과: **Doe John(john.doe@aol.com)**

>[!NOTE]
>
>스키마에 컴퓨팅 문자열이 포함되어 있지 않으면 기본적으로 스키마의 기본 키 값으로 컴퓨팅 문자열이 채워집니다.

