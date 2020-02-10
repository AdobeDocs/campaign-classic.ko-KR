---
title: 새 필드 마법사
seo-title: 새 필드 마법사
description: 새 필드 마법사
seo-description: null
page-status-flag: never-activated
uuid: 2c8d35db-042a-47cf-a7a6-3bb63bf40d94
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6da65fb5-18a1-41a0-96d8-588e383f944b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 새 필드 마법사{#new-field-wizard}

을 통해 액세스할 수 있는 마법사를 **[!UICONTROL Tools > Advanced > Add new fields]** 사용하면 데이터베이스의 테이블에 하나 이상의 필드를 추가할 수 있습니다.

마법사의 유효성을 검사하면 확장할 테이블의 확장 스키마가 업데이트되고 SQL 스크립트를 실행하여 데이터베이스의 물리적 구조를 수정합니다.

이 도우미는 데이터 스키마의 구조를 모르더라도 필드를 신속하게 추가할 수 있습니다.

주된 단점은 확장할 데이터와 속성의 제한입니다.

마법사 화면에는 다음 단계가 포함됩니다.

1. 첫 번째 페이지에서는 확장할 스키마의 이름과 수정 내용을 저장할 확장 스키마의 네임스페이스를 입력할 수 있습니다.

   ![](assets/d_ncs_integration_schema_addfield.png)

1. 다음 페이지에서 추가할 필드의 속성을 입력할 수 있습니다.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. 변경 사항을 확인하려면 **[!UICONTROL Finish]** 단추를 클릭합니다.

예제에서 &quot;cus:recipient&quot;라는 확장 파일이 자동으로 생성되며 해당 SQL 스크립트가 실행됩니다.

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>기본적으로 추가된 필드는 속성 **사용자로** 선언됩니다(값 &quot;true&quot;). 이렇게 하면 &quot;treeEdit&quot; 형식 컨트롤을 사용하여 확장 스키마의 입력 형식으로 필드를 표시하고 편집할 수 있습니다(입력 양식 참조).

