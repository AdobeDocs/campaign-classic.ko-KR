---
solution: Campaign Classic
product: campaign
title: 스키마 특성
description: 스키마 특성
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---


# 스키마 특성{#schema-characteristics}

기존 테이블을 참조하는 스키마의 특성은 다음과 같습니다.

* Adobe Campaign은 기존 테이블과 상대적인 SQL 객체를 수정해서는 안 됩니다.
* 표 및 열 이름은 명시적으로 지정해야 합니다.
* 인덱스를 선언해야 합니다.

>[!IMPORTANT]
>
>쓸모 없는 경우에도 표준 수신자 테이블의 필드를 삭제하지 마십시오. 이로 인해 Adobe Campaign 데이터베이스에 동작 오류가 발생할 수 있습니다.

## 보기 특성 {#the-view-attribute}

소스 스키마는 **srcSchema** 루트 요소에 대해 **view** 특성을 허용합니다. 사용자 정의 테이블에서 Adobe Campaign을 조작할 때 사용해야 합니다. **view=&quot;true&quot;** 특성은 데이터베이스 구조 업데이트 마법사에 이 스키마를 무시하도록 지시합니다. 따라서 응용 프로그램은 테이블, 해당 열 및 인덱스를 해당 스키마와 동기화할 수 없습니다.

이 특성이 **true**&#x200B;로 설정되면 스키마는 이 테이블의 데이터에 액세스하기 위해 SQL 쿼리를 생성하는 데만 사용됩니다.

## 표 및 열 이름 {#names-of-tables-and-columns}

테이블 업데이트 마법사로 테이블을 생성하면 각 스키마 및 속성의 이름에 따라 테이블 및 열 이름이 자동으로 생성됩니다. 다음 속성을 입력하여 SQL 이름을 사용하도록 할 수 있습니다.

* **스키마** 의 주 요소 내에서 sqltableewithin을 사용하여 테이블을 지정하려면
* **각** 특성 내의 sqlnamewithin을 사용하여 열을 지정합니다.

**예제**:

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

이 예제에서 테이블 및 열의 이름이 명시적으로 지정되지 않은 경우 응용 프로그램은 테이블에 대해 **lastName** 및 **firstName** 등을 사용했을 것입니다.****

스키마에서 기존 테이블의 열 일부만을 채울 수 있습니다. 채워지지 않은 열은 사용자가 액세스할 수 없습니다.

## 인덱싱된 필드 {#indexed-fields}

클라이언트 콘솔에서 목록의 레코드를 정렬할 때 인덱스 필드를 정렬하면 더 나은 성능을 얻을 수 있습니다. 스키마에서 인덱스를 선언하면 콘솔은 아래와 같이 열 레이블 왼쪽에 있는 정렬 순서 화살표 아래에 빨간색 선으로 인덱스 필드를 표시합니다.

![](assets/s_ncs_integration_mapping_index.png)

스키마에서 색인은 다음과 같이 정의됩니다.

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

이 때문에 사용자 정의 테이블의 기존 인덱스를 일치하는 스키마에서 선언해야 합니다.

인덱스는 소스 스키마의 각 키 및 링크 선언에 대해 암시적으로 선언됩니다. 인덱스 선언은 **noDbIndex=&quot;true&quot;** 특성을 지정하여 수행할 수 없습니다.

**예제**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```

