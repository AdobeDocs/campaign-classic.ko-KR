---
product: campaign
title: 새 필드 마법사
description: 새 필드 마법사
feature: Schema Extension
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 4%

---

# 새 필드 마법사{#new-field-wizard}

![](../../assets/v7-only.svg)

을 통해 액세스할 수 있는 마법사 **[!UICONTROL Tools > Advanced > Add new fields]** 데이터베이스의 테이블에 하나 이상의 필드를 추가할 수 있습니다.

마법사를 검증하면 확장할 테이블의 확장 스키마가 업데이트되고 SQL 스크립트가 실행되어 데이터베이스의 물리적 구조를 수정합니다.

이 도우미에서는 데이터 스키마의 구조를 알지 않고도 필드를 빠르게 추가할 수 있는 이점이 있습니다.

주요 단점은 확장할 데이터 및 속성의 제한입니다.

마법사 화면에는 다음 단계가 포함됩니다.

1. 첫 번째 페이지에서는 확장할 스키마의 이름과 수정 사항을 저장할 확장 스키마의 네임스페이스를 입력할 수 있습니다.

   ![](assets/d_ncs_integration_schema_addfield.png)

1. 다음 페이지에서는 추가할 필드의 속성을 입력할 수 있습니다.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. 변경 사항을 확인하려면 **[!UICONTROL Finish]** 버튼을 클릭합니다.

이 예제에서 &quot;cus:recipient&quot;라고 하는 확장 파일이 자동으로 만들어지고 해당 SQL 스크립트가 실행됩니다.

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>기본적으로 추가된 필드는 속성으로 선언됩니다 **사용자** (값 &quot;true&quot;가 있는 경우) 이렇게 하면 &quot;treeEdit&quot; 형식 컨트롤을 사용하여 확장 스키마의 입력 형식으로 필드를 표시하고 편집할 수 있습니다(입력 양식 참조).
