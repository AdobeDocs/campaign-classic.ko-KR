---
solution: Campaign Classic
product: campaign
title: 스키마 확장
description: 스키마 확장 방법 알아보기
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 5%

---


# 스키마 확장{#extending-a-schema}

>[!IMPORTANT]
>
>일부 내장 스키마는 확장되지 않아야 합니다.주로 다음 설정이 정의된 설정입니다.\
>**dataSource=&quot;file&quot;** 및  **mappingType=&quot;xmlFile&quot;**.\
>다음 스키마는 확장할 수 없습니다.**xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, &lt;a8:src **, &lt;a 10/>ncm:publishing**, **nl:monitoring**, **nms:calendar**, **nms:remoteTracking**, **nms:user에이전트 규칙**, **xtk:builder**, **xtk:connections**, **xtk:dbInit**, **xtk:func&lt;a222** xtk:fusion **,** xtk:jst **,** xtk:navtree **,** xtk:queryDef **,** xtk:resourceMenu **,** xtk:schema 39/>, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings**********
>이 목록은 완전하지 않다.

기존 스키마를 확장하는 방법에는 두 가지가 있습니다.

1. 소스 스키마를 직접 수정합니다.
1. 이름이 같지만 네임스페이스가 다른 다른 스키마를 만드는 중입니다. 원본 스키마를 수정할 필요 없이 테이블을 확장할 수 있다는 장점이 있습니다.

   스키마의 루트 요소에는 확장될 스키마 이름의 **extendedSchema** 특성이 포함되어야 합니다.

   확장 스키마에 고유한 스키마가 없습니다.소스 스키마에서 생성된 스키마가 확장 스키마의 필드로 채워집니다.

   >[!IMPORTANT]
   >
   >응용 프로그램의 내장 스키마를 수정할 수 없으며 스키마 확장 메커니즘을 수정할 수 없습니다. 그렇지 않으면 나중에 애플리케이션을 업그레이드할 때 수정된 스키마가 업데이트되지 않습니다. 이 경우 Adobe Campaign을 사용할 때 잘못된 기능을 초래할 수 있습니다.

   **예**:nms: **recipientschema의** 확장입니다.

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

   스키마의 루트 요소에 있는 **deadminedSchemas** 특성이 확장 스키마에 대한 종속성을 참조합니다.

   필드의 **containsTo** 특성이 선언된 스키마를 채웁니다.

>[!IMPORTANT]
>
>수정 사항을 고려하려면 스키마를 다시 생성해야 합니다. 자세한 내용은 [스키마 다시 생성](../../configuration/using/regenerating-schemas.md) 섹션을 참조하십시오.\
>수정 내용이 데이터베이스 구조에 영향을 주는 경우 업데이트를 실행해야 합니다. 자세한 내용은 [데이터베이스 구조 업데이트](../../configuration/using/updating-the-database-structure.md) 섹션을 참조하십시오.

