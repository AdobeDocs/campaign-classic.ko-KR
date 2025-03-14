---
product: campaign
title: 스키마 확장
description: 스키마를 확장하는 방법 알아보기
role: Data Engineer, Developer
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 4%

---

# 스키마 확장{#extending-a-schema}

>[!IMPORTANT]
>
>일부 기본 제공 스키마는 확장해서는 안 됩니다. 주로 다음 설정이 정의된 스키마입니다.\
>**dataSource=&quot;file&quot;** 및 **mappingType=&quot;xmlFile&quot;**.\
>**xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl:monitoring**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules**, **xtk:builder**, **xtk:connections**, **xtk:dbInit**, **xtk:funcList**, **xtk:fusion**, **xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings**.
>이 목록은 완전하지 않습니다.

기존 스키마를 확장하는 방법에는 두 가지가 있습니다.

1. 소스 스키마를 직접 수정하는 중입니다.
1. 이름은 같지만 네임스페이스가 다른 다른 스키마를 만듭니다. 원래 스키마를 수정할 필요 없이 테이블을 확장할 수 있다는 이점이 있습니다.

   스키마의 루트 요소는 확장될 스키마 이름의 **extendedSchema** 특성을 해당 값으로 포함해야 합니다.

   확장 스키마에는 자체 스키마가 없습니다. 소스 스키마에서 생성된 스키마는 확장 스키마의 필드로 채워집니다.

   >[!IMPORTANT]
   >
   >애플리케이션의 기본 제공 스키마를 수정할 수 없고 스키마 확장 메커니즘을 수정할 수 없습니다. 그렇지 않으면 수정된 스키마는 나중에 애플리케이션을 업그레이드할 때 업데이트되지 않습니다. 이로 인해 Adobe Campaign 사용 시 오작동이 발생할 수 있습니다.

   **예**: **nms:recipient** 스키마의 확장입니다.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   **nms:recipient** 확장 스키마가 확장 스키마에 채워진 필드로 채워집니다.

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   스키마의 루트 요소에 있는 **dependingSchemas** 특성이 확장 스키마에 대한 종속성을 참조합니다.

   필드의 **assetsTo** 특성은 선언된 스키마를 채웁니다.

>[!IMPORTANT]
>
>수정 사항을 고려하려면 스키마를 재생성해야 합니다. 자세한 정보는 이 [페이지](../../configuration/using/regenerating-schemas.md)를 참조하십시오.\
>수정 사항이 데이터베이스 구조에 영향을 주는 경우 업데이트를 실행해야 합니다. 자세한 정보는 이 [페이지](../../configuration/using/updating-the-database-structure.md)를 참조하십시오.
