---
product: campaign
title: 스키마 구조
description: 스키마 구조
feature: Custom Resources
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 2%

---

# 스키마 구조{#schema-structure}

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

데이터 스키마의 XML 문서에는 **`<srcschema>`** 루트 요소 **이름** 및 **네임스페이스** 속성을 사용하여 스키마 이름과 해당 네임스페이스를 채웁니다.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

다음 XML 콘텐츠를 사용하여 데이터 스키마의 구조를 보여 드리겠습니다.

```
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

해당 데이터 스키마 포함:

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

스키마의 시작점은 주 요소입니다. 스키마와 이름이 같기 때문에 식별하기 쉽고 루트 요소의 하위 항목이어야 합니다. 콘텐츠에 대한 설명은 이 요소에서 시작됩니다.

이 예제에서 기본 요소는 다음 줄로 표시됩니다.

```
<element name="recipient">
```

요소 **`<attribute>`** 및 **`<element>`** 기본 요소 다음에 오는 를 사용하면 XML 구조에서 데이터 항목의 위치와 이름을 정의할 수 있습니다.

샘플 스키마에서는 다음과 같습니다.

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

다음 규칙을 준수해야 합니다.

* 각 **`<element>`** 및 **`<attribute>`** 은(는) 다음을 통해 이름으로 식별되어야 합니다. **이름** 특성.

  >[!IMPORTANT]
  >
  >요소의 이름은 간결해야 하며, 가급적 영어로 작성해야 하고, XML 이름 지정 규칙에 따라 승인된 문자만 포함해야 합니다.

* 전용 **`<element>`** 요소는 다음을 포함할 수 있습니다. **`<attribute>`** 요소 및 **`<element>`** 요소를 XML 구조로 만듭니다.
* An **`<attribute>`** 요소는 다음 내에서 고유한 이름을 가져야 합니다. **`<element>`**.
* 사용 **`<elements>`** 여러 줄 데이터 문자열에서 를 사용하는 것이 좋습니다.

## 데이터 유형 {#data-types}

데이터 유형은 다음을 통해 입력됩니다. **유형** 의 속성 **`<attribute>`** 및 **`<element>`** 요소.

자세한 목록은 의 설명에서 사용할 수 있습니다. [`<attribute>` 요소](../../configuration/using/schema/attribute.md) 및 [`<element>` 요소](../../configuration/using/schema/element.md)).

이 속성이 채워지지 않으면 **문자열** 요소에 자식 요소가 포함되지 않은 경우 는 기본 데이터 형식입니다. 이 경우 요소를 계층적으로 구성하는 데만 사용됩니다(**`<location>`** 요소(예)를 참조하십시오.

스키마에서 지원되는 데이터 유형은 다음과 같습니다.

* **문자열**: 문자열. 예: 이름, 마을 등

  크기는 다음을 통해 지정할 수 있습니다 **length** attribute(선택 사항, 기본값 &quot;255&quot;).

* **부울**: 부울 필드. 가능한 값의 예: true/false, 0/1, yes/no 등.
* **바이트**, **짧음**, **길게**: 정수(1바이트, 2바이트, 4바이트). 예: 나이, 계정 번호, 포인트 수 등
* **더블**: 배정밀도 부동 소수점 숫자 예: 가격, 요금 등
* **날짜**, **datetime**: 날짜 및 날짜 + 시간입니다. 예: 생년월일, 구매일 등
* **다테티메노츠**: 시간대 데이터가 없는 날짜 + 시간입니다.
* **timespan**: 기간. 예: 연공서열.
* **메모**: 긴 텍스트 필드(여러 줄). 예: 설명, 주석 등
* **uuid**: GUID를 지원하는 &quot;uniqueidentifier&quot; 필드(Microsoft SQL Server에서만 지원됨).

  >[!NOTE]
  >
  >포함 **uuid** Microsoft SQL Server가 아닌 다른 엔진의 필드에서는 &quot;newuuid()&quot; 함수를 추가하고 기본값으로 완료해야 합니다.

다음은 입력한 유형이 포함된 예제 스키마입니다.

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

아래 표에는 다른 데이터베이스 관리 시스템에 대해 Adobe Campaign에서 생성한 데이터 유형에 대한 매핑이 나와 있습니다.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PostgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> <strong>MS SQL</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 문자열<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2(유니코드의 경우 NVARCHAR2)<br /> </td> 
   <td> VARCHAR(유니코드의 경우 NVARCHAR)<br /> </td> 
  </tr> 
  <tr> 
   <td> 부울<br /> </td> 
   <td> 스말린트<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 바이트<br /> </td> 
   <td> 스말린트<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 짧음<br /> </td> 
   <td> 스말린트<br /> </td> 
   <td> NUMBER(5)<br /> </td> 
   <td> 스말린트<br /> </td> 
  </tr> 
  <tr> 
   <td> 더블<br /> </td> 
   <td> 배정밀도<br /> </td> 
   <td> 부동<br /> </td> 
   <td> 부동<br /> </td> 
  </tr> 
  <tr> 
   <td> 길게<br /> </td> 
   <td> 정수<br /> </td> 
   <td> NUMBER(10)<br /> </td> 
   <td> INT<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NUMBER(20)<br /> </td> 
   <td> BIGINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 날짜<br /> </td> 
   <td> 날짜<br /> </td> 
   <td> 날짜<br /> </td> 
   <td> 날짜/시간<br /> </td> 
  </tr> 
  <tr> 
   <td> 시간<br /> </td> 
   <td> 시간<br /> </td> 
   <td> 부동<br /> </td> 
   <td> 부동<br /> </td> 
  </tr> 
  <tr> 
   <td> 날짜/시간<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> 날짜<br /> </td> 
   <td> MS SQL &lt; 2008: 날짜/시간<br /> MS SQL &gt;= 2012: DATETIMEOFFSET<br /> </td> 
  </tr> 
  <tr> 
   <td> 다테티메노츠<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> 날짜<br /> </td> 
   <td> MS SQL &lt; 2008: 날짜/시간<br /> MS SQL &gt;= 2012: DATETIME2<br /> </td> 
  </tr> 
  <tr> 
   <td> Timespan<br /> </td> 
   <td> 배정밀도<br /> </td> 
   <td> 부동<br /> </td> 
   <td> 부동<br /> </td> 
  </tr> 
  <tr> 
   <td> 메모<br /> </td> 
   <td> 텍스트<br /> </td> 
   <td> CLOB(유니코드인 경우 NCLOB)<br /> </td> 
   <td> 텍스트(유니코드의 경우 NTEXT)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> 이미지<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 속성 {#properties}

다음 **`<elements>`** 및 **`<attributes>`** 데이터 스키마의 요소를 다양한 속성으로 보강할 수 있습니다. 현재 요소를 설명하기 위해 레이블을 채울 수 있습니다.

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

  설명은 Adobe Campaign 클라이언트 콘솔 주 창의 상태 표시줄에 있는 입력 양식에서 볼 수 있습니다.

  >[!NOTE]
  >
  >설명은 인스턴스의 현재 언어와 연결됩니다.

  **예제**:

  ```
  <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
  ```

### 기본값 {#default-values}

다음 **기본값** 속성을 사용하면 콘텐츠 생성 시 기본값을 반환하는 표현식을 정의할 수 있습니다.

값은 XPath 언어를 준수하는 표현식이어야 합니다. 자세한 내용은 다음을 참조하십시오. [XPath를 사용하여 참조](../../configuration/using/schema-structure.md#referencing-with-xpath).

**예제**:

* 현재 날짜: **default=&quot;GetDate()&quot;**
* 카운터: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

  이 예제에서 기본값은 문자열의 연결을 사용하여 생성되며 **카운터 값** 무료 카운터 이름이 있는 함수. 반환되는 숫자는 삽입 시마다 하나씩 증가합니다.

  >[!NOTE]
  >
  >Adobe Campaign 클라이언트 콘솔에서 **[!UICONTROL Administration>Counters]** 노드는 카운터를 관리하는 데 사용됩니다.

필드에 기본값을 연결하려면 `<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>` : 엔티티를 생성할 때 필드를 기본값으로 미리 채울 수 있습니다. 이 값은 기본 SQL 값이 아닙니다.

`<sqldefault>` : 필드를 생성할 때 추가 값을 가질 수 있도록 해줍니다. 이 값은 SQL 결과로 나타납니다. 스키마 업데이트 중에는 새 레코드만 이 값의 영향을 받습니다.

### 열거형 {#enumerations}

#### 자유 열거형 {#free-enumeration}

다음 **userEnum** 속성을 사용하면 이 필드를 통해 입력한 값을 기억하고 표시하는 자유 열거형을 정의할 수 있습니다. 구문은 다음과 같습니다.

**userEnum=&quot;열거형 이름&quot;**

열거형에 지정한 이름은 자유롭게 선택하고 다른 필드와 공유할 수 있습니다.

다음 값은 입력 양식의 드롭다운 목록에 표시됩니다.

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>Adobe Campaign 클라이언트 콘솔에서 **[!UICONTROL Administration > Enumerations]** 노드는 열거형을 관리하는 데 사용됩니다.

#### 열거형 설정 {#set-enumeration}

다음 **enum** 속성을 사용하면 가능한 값 목록을 미리 알 때 사용되는 고정 열거형을 정의할 수 있습니다.

다음 **enum** 특성은 기본 요소 외부의 스키마에 채워진 열거형 클래스의 정의를 나타냅니다.

열거형을 사용하면 일반 입력 필드에 값을 입력하는 대신 드롭다운 목록에서 값을 선택할 수 있습니다.

![](assets/d_ncs_integration_schema_enum.png)

데이터 스키마의 열거 선언 예:

```
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

열거형은 를 통해 기본 요소 외부에 선언됩니다. **`<enumeration>`** 요소를 생성하지 않습니다.

열거형 속성은 다음과 같습니다.

* **baseType**: 값과 연관된 데이터의 유형,
* **레이블**: 열거형에 대한 설명,
* **이름**: 열거형의 이름,
* **기본값**: 열거형의 기본값

열거형 값은 **`<value>`** 다음 속성을 가진 요소:

* **이름**: 내부에 저장된 값의 이름,
* **레이블**: 그래픽 인터페이스를 통해 표시되는 레이블.

#### 드베넘 열거 {#dbenum-enumeration}

* 다음 **드베넘** 속성을 사용하면 속성과 유사한 속성을 가진 열거형을 정의할 수 있습니다. **enum** 속성.

  그러나 **이름** 속성은 값을 내부적으로 저장하지 않으며, 관련 테이블을 스키마를 수정하지 않고 확장할 수 있는 코드를 저장합니다.

  값은 다음을 통해 정의됩니다. **[!UICONTROL Administration>Enumerations]** 노드.

  예를 들어 이 열거형은 캠페인의 특성을 지정하는 데 사용됩니다.

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

컬렉션은 이름이 같고 계층 수준이 같은 요소의 목록입니다.

다음 **바인딩되지 않음** attribute에 &quot;true&quot; 값을 지정하면 컬렉션 요소를 채울 수 있습니다.

**예**: 의 정의 **`<group>`** 스키마의 컬렉션 요소입니다.

```
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

XML 콘텐츠 투영 시:

```
<group label="Group1"/>
<group label="Group2"/>
```

## XPath를 사용하여 참조 {#referencing-with-xpath}

XPath 언어는 Adobe Campaign에서 데이터 스키마에 속하는 요소나 특성을 참조하는 데 사용됩니다.

XPath는 XML 문서의 트리에서 노드를 찾을 수 있는 구문입니다.

요소는 이름으로 지정되고, 속성은 &quot;@&quot; 문자 앞에 오는 이름으로 지정됩니다.

**예제**:

* **@email**: 이메일을 선택하고,
* **위치/@city**: 아래에서 &quot;city&quot; 속성을 선택합니다. **`<location>`** 요소
* **../@email**: 현재 요소의 상위 요소에서 이메일 주소를 선택합니다
* **그룹`[1]/@label`**: 첫 번째 요소의 하위 요소인 &quot;label&quot; 속성을 선택합니다 **`<group>`** 수집 요소
* **그룹`[@label='test1']`**: 의 하위 항목인 &quot;label&quot; 속성을 선택합니다. **`<group>`** 요소를 반환하고 값 &quot;test1&quot;을 포함합니다.

>[!NOTE]
>
>경로가 하위 요소를 교차하면 추가 제약 조건이 추가됩니다. 이 경우 대괄호 사이에 다음 표현식을 배치해야 합니다.
>
>* **위치/@city** 은(는) 유효하지 않습니다. 다음을 사용하십시오. **`[location/@city]`**
>* **`[@email]`** 및 **@email** 등가물
>

다음 산술 연산과 같은 복잡한 표현식을 정의할 수도 있습니다.

* **@gender+1**: 의 콘텐츠에 1을 추가합니다. **성별** 속성,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: 괄호 사이에 생성 날짜에 추가된 이메일 주소 값을 사용하여 문자열을 구성합니다(문자열 유형의 경우 상수를 따옴표로 묶음).

이 언어의 잠재력을 강화하기 위해 표현식에 높은 수준의 함수가 추가되었습니다.

Adobe Campaign 클라이언트 콘솔에서 표현식 편집기를 통해 사용 가능한 함수 목록에 액세스할 수 있습니다.

![](assets/d_ncs_integration_schema_function.png)

**예제**:

* **GetDate()**: 현재 날짜를 반환합니다.
* **Year(@created)**: &quot;created&quot; 속성에 포함된 날짜의 연도를 반환합니다.
* **GetEmailDomain(@email)**: 이메일 주소의 도메인을 반환합니다.

## 계산 문자열을 통해 문자열 빌드 {#building-a-string-via-the-compute-string}

A **계산 문자열** 는 스키마와 연결된 테이블의 레코드를 나타내는 문자열을 구성하는 데 사용되는 XPath 표현식입니다. **계산 문자열** 는 주로 그래픽 인터페이스에서 선택한 레코드의 레이블을 표시하는 데 사용됩니다.

다음 **계산 문자열** 다음을 통해 정의됨 **`<compute-string>`** 요소는 데이터 스키마의 main 요소 아래에 있습니다. An **expr** 속성에는 표시를 계산하는 XPath 식이 포함되어 있습니다.

**예**: 수신자 테이블의 계산 문자열.

```
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

수신자에 대해 계산된 문자열의 결과: **Doe John(john.doe@aol.com)**

>[!NOTE]
>
>스키마에 계산 문자열이 포함되지 않으면 계산 문자열은 기본적으로 스키마의 기본 키 값으로 채워집니다.
