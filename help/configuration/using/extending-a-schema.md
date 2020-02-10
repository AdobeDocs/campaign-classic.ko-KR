---
title: 스키마 확장
seo-title: 스키마 확장
description: 스키마 확장
seo-description: null
page-status-flag: never-activated
uuid: 1767b9de-1d72-4ece-aeec-87f83862d81c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 1c9af980-4e6b-44dc-af61-dd284863ec7d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# 스키마 확장{#extending-a-schema}

>[!CAUTION]
>
>일부 내장 스키마는 확장되지 않아야 합니다.주로 다음 설정이 정의된 설정입니다.\
>**dataSource=&quot;file&quot;** 및 **mappingType=&quot;xmlFile&quot;**.\
>다음 스키마는 확장할 수 없습니다. **xtk:entityBackupNew**, **xtk:entityBackup**, **xtk:entity** xtk, xkk **xk, xsrck:xkKK:** jkk, **nkkXKK,********************************************nl:nl모니터링:nl달력 사용자 추적・nms:AgentRulesTracking, Xxtk:Builder, xtk:connectionsXtk:connectionsXtk, xtk dbInit, Xtk:xtkListFuncFuncFusionFusion:tfusionFusion을 해결합니다.jst**, **xtk:navtk:query**, **xtk:queryDef**, xtk:queryResource **, xtk:resource**********************, xtk:xtk, xtk, xkk, xkk, xkk, xk, xk, xkk, xkk, 문자열.
>이 목록은 완전하지 않습니다.

기존 스키마를 확장하는 방법에는 두 가지가 있습니다.

1. 소스 스키마를 직접 수정합니다.
1. 이름이 같지만 네임스페이스가 다른 스키마를 만드는 중입니다. 이점은 원본 스키마를 수정할 필요 없이 표를 확장할 수 있다는 것입니다.

   스키마의 루트 요소에는 확장될 스키마 **이름의** extendedSchema 특성이 포함되어야 합니다.

   확장 스키마에는 자체 스키마가 없습니다.소스 스키마에서 생성된 스키마가 확장 스키마의 필드로 채워집니다.

   >[!CAUTION]
   >
   >응용 프로그램의 내장 스키마를 수정할 수 없으며 스키마 확장 메커니즘을 수정할 수 없습니다. 그렇지 않으면, 수정된 스키마가 향후 애플리케이션 업그레이드 시 업데이트되지 않습니다. 이로 인해 Adobe Campaign을 사용할 때 오류가 발생할 수 있습니다.

   **예**:nms: **recipient** 스키마의 확장입니다.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   nms: **recipient** 확장 스키마는 확장 스키마에서 채워진 필드로 채워집니다.

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   스키마의 루트 요소에 **따라** Schemas 속성은 확장 스키마에 대한 종속성을 참조합니다.

   필드의 **containsTo** 속성이 선언된 스키마를 채웁니다.

>[!CAUTION]
>
>수정 사항을 고려하려면 스키마를 다시 생성해야 합니다. 자세한 내용은 스키마 [재생성](../../configuration/using/regenerating-schemas.md) 섹션을 참조하십시오.\
>수정 내용이 데이터베이스 구조에 영향을 주는 경우 업데이트를 실행해야 합니다. 자세한 내용은 데이터베이스 구조 [업데이트](../../configuration/using/updating-the-database-structure.md) 섹션을 참조하십시오.

