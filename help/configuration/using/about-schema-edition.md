---
title: 스키마 버전 정보
seo-title: 스키마 버전 정보
description: 스키마 버전 정보
seo-description: null
page-status-flag: never-activated
uuid: edb4d47d-b507-4d86-9873-ebd5f6acefc6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: d5b08e4e-060c-4185-9dac-af270918e2b9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 스키마 버전 정보{#about-schema-edition}

Adobe Campaign은 데이터 스키마를 사용하여 다음을 수행합니다.

* 응용 프로그램 내의 데이터 객체가 기본 데이터베이스 테이블에 연결되는 방식을 정의합니다.
* Campaign 애플리케이션 내에서 서로 다른 데이터 객체 간의 링크를 정의합니다.
* 각 개체에 포함된 개별 필드를 정의하고 설명합니다.

Campaign 기본 제공 테이블 및 상호 작용에 대한 자세한 내용은 Campaign Classic [데이터 모델을](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)참조하십시오.

## 스키마 확장 또는 만들기 {#extending-or-creating-schemas}

받는 사람 테이블(nms:recipient)과 같은 Campaign의 핵심 데이터 스키마 중 하나에 필드 또는 인덱스 또는 기타 요소를 추가하려면 해당 스키마를 확장해야 합니다. 자세한 내용은 스키마 [확장](../../configuration/using/extending-a-schema.md) 섹션을 참조하십시오.

Adobe Campaign에 기본적으로 존재하지 않는 완전히 새로운 유형의 데이터(예: 계약서 표)를 추가하려면 사용자 지정 스키마를 직접 만들 수 있습니다. 자세한 내용은 데이터 스키마 [섹션을](../../configuration/using/data-schemas.md) 참조하십시오.

![](assets/schemaextension_getting_started_1.png)

작업할 스키마를 확장하거나 만들었으면 XML 컨텐츠 요소를 아래 표시된 순서대로 정의하는 것이 좋습니다.

## 열거형 {#enumerations}

열거형은 스키마의 기본 요소 앞에 먼저 정의됩니다. 이 매개 변수를 사용하면 지정된 필드에 대한 사용자의 선택 사항을 제한하기 위해 목록에 값을 표시할 수 있습니다.

예:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

그런 다음 필드를 정의할 때 다음과 같이 이 열거형을 사용할 수 있습니다.

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>사용자 관리 열거형(일반적으로 **[!UICONTROL Administration]** > 아래 **[!UICONTROL Platform]** )을 사용하여 지정된 필드에 대한 값을 지정할 수도 있습니다. 이러한 열거형은 효과적으로 전역 열거형이며 작업 중인 특정 스키마 외부에서 열거형을 사용할 수 있는 경우 더 나은 선택 사항입니다.

열거형에 대한 자세한 내용은 열거형 및 [요소](../../configuration/using/schema-structure.md#enumerations) 섹션을 참조하십시오 [`<enumeration>`](../../configuration/using/elements-and-attributes.md#enumeration--element) .

## 색인 {#index}

인덱스는 스키마의 기본 요소에서 선언된 첫 번째 요소입니다.

이러한 필드는 고유하거나 그렇지 않을 수 있으며 하나 이상의 필드를 참조할 수 있습니다.

예:

```
<dbindex name="email" unique="true">
  <keyfield xpath="@email"/>
</dbindex>
```

```
<dbindex name="lastNameAndZip">
  <keyfield xpath="@lastName"/>
  <keyfield xpath="location/@zipCode"/>
</dbindex>
```

xpath **속성은** 색인화할 스키마에서 필드를 가리킵니다.

>[!IMPORTANT]
>
>인덱스에서 제공하는 SQL 쿼리 읽기 성능 향상도 레코드 쓰기에 대한 성능 히트와 함께 제공된다는 점을 기억해야 합니다. 따라서 지수는 주의해서 사용해야 한다.

색인에 대한 자세한 내용은 인덱스 [필드](../../configuration/using/database-mapping.md#indexed-fields) 섹션을 참조하십시오.

## 키 {#keys}

모든 테이블에는 키가 하나 이상 있어야 하며, **@autopk=true** 속성을 &quot;true&quot;로 설정하여 스키마의 기본 요소에 자동으로 설정됩니다.

기본 키는 **내부** 속성을 사용하여 정의할 수도 있습니다.

예:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

이 예에서는 **@autok** 속성이 &quot;id&quot;라는 기본 기본 키를 만들도록 하는 대신 자체 &quot;houseinId&quot; 기본 키를 지정합니다.

>[!IMPORTANT]
>
>새 스키마를 만들거나 스키마 확장 중에 전체 스키마에 대해 동일한 기본 키 시퀀스 값(@pkSequence)을 유지해야 합니다.

키에 대한 자세한 내용은 키 [관리](../../configuration/using/database-mapping.md#management-of-keys) 섹션을 참조하십시오.

## 속성(필드) {#attributes--fields-}

속성을 사용하면 데이터 개체를 구성하는 필드를 정의할 수 있습니다. 스키마 에디션 도구 모음의 **[!UICONTROL Insert]** 단추를 사용하여 커서가 있는 XML에 빈 속성 템플릿을 놓을 수 있습니다. 자세한 내용은 데이터 스키마 [섹션을](../../configuration/using/data-schemas.md) 참조하십시오.

![](assets/schemaextension_getting_started_2.png)

속성 전체 목록은 [`<attribute>` 요소](../../configuration/using/elements-and-attributes.md#attribute--element) 섹션에서 사용할 수 있습니다. 다음은 보다 일반적으로 사용되는 속성 중 일부입니다.

* **@advanced**
* **@dataPolicy**
* **@default**
* **@desc**
* **@enum**
* **@expr**
* **@label**
* **@length**
* **@name**
* **@notNull**
* **@required**
* **@ref**
* **@xml**
* **@type**

   다른 데이터베이스 관리 시스템에 대해 Adobe Campaign에서 생성된 데이터 유형에 대한 매핑을 나열하는 표를 보려면 Adobe Campaign/DBMS 데이터 [](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) 유형 매핑 섹션을 참조하십시오.

각 속성에 대한 자세한 내용은 속성 [설명](../../configuration/using/elements-and-attributes.md#attribute-description) 섹션을 참조하십시오.

### 예 {#examples}

기본값 정의 예:

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

필수로 표시된 필드의 템플릿으로 공통 속성을 사용하는 예:

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

계산된 필드의 예: **@advanced** 속성을 사용하여 숨김

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

SQL 필드에 저장되고 **@dataPolicy 특성이 있는 XML 필드의** 예입니다.

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>대부분의 속성은 데이터베이스의 물리적 필드에 1-1 카디널리티에 따라 연결되어 있지만 XML 필드나 계산된 필드의 경우에는 그렇지 않습니다.\
>XML 필드는 표의 메모 필드(&quot;mData&quot;)에 저장됩니다.\
>그러나 계산된 필드는 쿼리가 시작될 때마다 동적으로 만들어지므로 응용 프로그램 레이어에만 존재합니다.

## 링크 {#links}

링크는 스키마의 기본 요소에 있는 마지막 요소 중 일부입니다. 이 매개 변수는 인스턴스의 서로 다른 모든 스키마가 서로 어떻게 연관되어 있는지 정의합니다.

링크가 연결된 테이블의 **외래 키가** 포함된 스키마에서 링크가 선언됩니다.

다음과 같은 세 가지 유형의 카디널리티가 있습니다.1-1, 1-N 및 N-N기본적으로 사용되는 1-N 유형입니다.

### 예 {#examples-1}

수신자 테이블(기본 스키마)과 사용자 지정 트랜잭션 테이블 간의 1-N 링크의 예:

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

사용자 지정 스키마 &quot;Car&quot;(&quot;cus&quot; 네임스페이스)와 받는 사람 테이블 간의 1-1 링크의 예:

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

받는 사람 테이블과 기본 키가 아닌 이메일 주소를 기반으로 한 주소 테이블 간의 외부 조인의 예:

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

여기서 &quot;xpath-dst&quot;는 대상 스키마의 기본 키에 해당하고 &quot;xpath-src&quot;는 소스 스키마의 외래 키에 해당합니다.

## 감사 추적 {#audit-trail}

스키마 하단에 포함할 유용한 요소 중 하나는 추적 요소(감사 추적)입니다.

아래 예를 사용하여 작성 날짜, 데이터를 만든 사용자, 날짜 및 테이블의 모든 데이터에 대한 마지막 수정 내용 작성자와 관련된 필드를 포함할 수 있습니다.

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## 데이터베이스 구조 업데이트 {#updating-the-database-structure}

변경 사항이 완료되고 저장되면 SQL 구조에 영향을 줄 수 있는 변경 사항을 데이터베이스에 적용해야 합니다. 이렇게 하려면 데이터베이스 업데이트 마법사를 사용합니다.

![](assets/schemaextension_getting_started_3.png)

자세한 내용은 데이터베이스 구조 [업데이트](../../configuration/using/updating-the-database-structure.md) 섹션을 참조하십시오.

>[!NOTE]
>
>수정 사항이 데이터베이스 구조에 영향을 주지 않으면 스키마를 다시 생성해야 합니다. 이렇게 하려면 업데이트할 스키마를 선택하고 마우스 오른쪽 단추를 클릭한 다음 을 선택합니다 **[!UICONTROL Actions > Regenerate selected schemas...]** . 자세한 내용은 스키마 [재생성](../../configuration/using/regenerating-schemas.md) 섹션을 참조하십시오.

