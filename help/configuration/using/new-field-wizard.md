---
product: campaign
title: 새 필드 도우미
description: 새 필드 도우미
feature: Schema Extension
role: Developer
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
TQID: https://experienceleague.adobe.com/dr6UMSb0vKU7Fne9uso4IYSJLHSyNqDQHX5V-r-qhcE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 200
ht-degree: 4%

---

# 새 필드 도우미{#new-field-wizard}


**[!UICONTROL Tools > Advanced > Add new fields]**&#x200B;을(를) 통해 액세스할 수 있는 도우미를 사용하여 데이터베이스의 테이블에 하나 이상의 필드를 추가할 수 있습니다.

길잡이의 유효성을 검사하면 확장할 테이블의 확장 스키마가 업데이트되고 SQL 스크립트가 시작되어 데이터베이스의 물리적 구조가 수정됩니다.

이 도우미는 데이터 스키마의 구조를 알 필요 없이 필드를 빠르게 추가할 수 있는 장점이 있습니다.

주요 단점은 자료 및 확장해야 할 특성의 한계이다.

길잡이 화면에는 다음 단계가 포함됩니다.

1. 첫 번째 페이지에서는 확장할 스키마의 이름과 수정 사항이 저장될 확장 스키마의 네임스페이스를 입력할 수 있습니다.

   ![](assets/d_ncs_integration_schema_addfield.png)

1. 다음 페이지에서는 추가할 필드의 속성을 입력할 수 있습니다.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. 변경 내용을 확인하려면 **[!UICONTROL Finish]** 단추를 클릭하십시오.

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
>기본적으로 추가된 필드는 속성 **user**(값 &quot;true&quot; 사용)으로 선언됩니다. 이렇게 하면 &quot;treeEdit&quot; 유형의 컨트롤을 사용하여 확장 스키마의 입력 양식에서 필드를 표시하고 편집할 수 있습니다(입력 양식 참조).
