---
product: campaign
title: 데이터 스키마의 키 관리
description: 데이터 스키마의 키 관리 이해
feature: Configuration, Instance Settings
role: Developer
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
TQID: 'https://experienceleague.adobe.com/dErbfzRabMls-5x1S3eRZO94Kqcz9LRh3PaUhVD5zAU'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 1%
---
# 스키마의 키 관리 {#management-of-keys}

데이터 스키마와 연결된 각 테이블에는 테이블의 레코드를 식별하기 위한 하나 이상의 키가 있어야 합니다. 이 페이지에서는 Campaign Classic v7 테이블에 사용되는 자동 증분 키에 대해 설명합니다.

Campaign v7에서 v8로 전환하는 과정의 일부로 Campaign Classic 설명서 세트가 간소화 및 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다. 키 관리에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-keys){target=_blank}를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-keys){target=_blank}

## 자동 증분 키 {#auto-incremental-key}

대부분의 Adobe Campaign 테이블의 기본 키는 데이터베이스 엔진에서 자동으로 생성된 32비트 정수(Long)입니다. 키 값의 계산은 전체 데이터베이스에서 고유한 숫자를 생성하는 시퀀스(기본적으로 **XtkNewId** SQL 함수)에 따라 달라집니다. 키의 내용은 레코드 삽입 시 자동으로 입력됩니다.

증분 키의 장점은 테이블 간의 조인에 수정할 수 없는 기술 키를 제공한다는 것입니다. 또한 이 키는 2바이트 정수를 사용하므로 메모리를 많이 차지하지 않습니다.

소스 스키마에서 **pkSequence** 특성과 함께 사용할 시퀀스의 이름을 지정할 수 있습니다. 이 특성이 원본 스키마에 지정되어 있지 않으면 **XtkNewId** 기본 시퀀스가 사용됩니다. 가장 많은 레코드가 포함된 테이블이므로 응용 프로그램에서 **nms:broadLog** 및 **nms:trackingLog** 스키마(**NmsBroadLogId** 및 **NmsTrackingLogId**)에 대해 전용 시퀀스를 사용합니다.

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
* [링크 관리](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"}(Campaign v8 설명서)
* [Campaign 데이터 모델](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/datamodel){target="_blank"}(Campaign v8 설명서)
