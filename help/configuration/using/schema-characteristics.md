---
title: 스키마 특성
seo-title: 스키마 특성
description: 스키마 특성
seo-description: null
page-status-flag: never-activated
uuid: ca8eb7af-ef22-403a-8f04-ece5dc903174
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 441e80e1-0559-41fd-83e8-afdf94279e75
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 스키마 특성{#schema-characteristics}

기존 테이블을 참조하는 스키마의 특성은 다음과 같습니다.

* Adobe Campaign은 기존 테이블과 관련된 SQL 개체를 수정해서는 안 됩니다.
* 테이블 및 열 이름은 명시적으로 지정해야 합니다.
* 인덱스를 선언해야 합니다.

>[!CAUTION]
>
>쓸모없는 경우에도 표준 수신자 테이블의 필드를 삭제하지 마십시오. 이로 인해 Adobe Campaign 데이터베이스에 동작 오류가 발생할 수 있습니다.

## view 속성 {#the-view-attribute}

소스 스키마는 srcSchema **루트 요소에 대한 보기** 속성을 **** 수락합니다. 사용자 지정 테이블에서 Adobe Campaign을 조작할 때 사용해야 합니다. view=&quot; **true&quot;** 속성은 데이터베이스 구조 업데이트 마법사에서 이 스키마를 무시하도록 지시합니다. 따라서 응용 프로그램은 테이블, 해당 열 및 인덱스를 해당 스키마와 동기화할 수 없습니다.

이 속성이 **true로**&#x200B;설정되면 스키마는 이 테이블의 데이터에 액세스하기 위해 SQL 쿼리를 생성하는 데만 사용됩니다.

## 표 및 열 이름 {#names-of-tables-and-columns}

테이블 업데이트 마법사에서 테이블을 생성하면 각 스키마 및 속성의 이름을 기반으로 테이블 및 열 이름이 자동으로 생성됩니다. 그러나 다음 속성을 입력하여 SQL 이름을 강제로 사용할 수 있습니다.

* **스키마의** 기본 요소 내의 sqltable을 사용하여 테이블을 지정합니다.
* **각 특성 내의 sqlname** . 열을 지정합니다.

**예**:

```
<element label="Individual" name="individual" sqltable="individual">
    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key> 
    <attribute name="id" type="long" length="32" />
    <attribute name="lastName" type="string" length="100" sqlname="Last_Name"/>
    <attribute name="firstName" type="string" length="100" sqlname="First_Name"/>
    <attribute name="email" type="string" length="100"/>
    <attribute name="mobile" type="string" length="100"/>
</element>
```

이 예제에서 테이블 및 열 이름이 명시적으로 지정되지 않은 경우 응용 프로그램에서 테이블, **lastName** 및 **열의** **FirstName** 을사용했을수 있습니다.

스키마에서는 기존 테이블의 열 일부만을 채울 수 있습니다. 채워지지 않은 열은 사용자가 액세스할 수 없습니다.

## 인덱스 필드 {#indexed-fields}

클라이언트 콘솔에서 목록의 레코드를 정렬할 때 인덱스 필드를 정렬하면 더 나은 성능을 얻을 수 있습니다. 스키마에서 인덱스를 선언하면 콘솔은 아래와 같이 열 레이블의 왼쪽에 정렬 순서 화살표 아래에 빨간색 선으로 인덱스된 필드를 표시합니다.

![](assets/s_ncs_integration_mapping_index.png)

스키마에서 색인은 다음과 같이 정의됩니다.

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

따라서 일치 스키마에서 사용자 지정 테이블의 기존 인덱스를 선언해야 합니다.

인덱스는 소스 스키마의 각 키 및 링크 선언에 대해 암시적으로 선언됩니다. noDbIndex=&quot; **true&quot;** 속성을 지정하여 인덱스 선언을 수행할 수 없습니다.

**예**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```

