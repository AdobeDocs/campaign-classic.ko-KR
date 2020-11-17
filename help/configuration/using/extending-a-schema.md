---
title: 스키마 확장
description: 스키마 확장 방법 살펴보기
page-status-flag: never-activated
uuid: 1767b9de-1d72-4ece-aeec-87f83862d81c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 1c9af980-4e6b-44dc-af61-dd284863ec7d
translation-type: tm+mt
source-git-commit: 30eaabba8962c518c734cc4e9ad27065cfe9d467
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 5%

---


# 스키마 확장{#extending-a-schema}

>[!IMPORTANT]
>
>일부 내장 스키마는 확장될 수 없습니다.주로 다음 설정이 정의된 설정입니다.\
>**dataSource=&quot;file&quot;** and **mappingType=&quot;xmlFile&quot;**.\
>다음 스키마는 확장할 수 없습니다. **xtk:BackupNew**, **xtk:entityBackupOriginal**, xtk xtk, xtkOriginal **xtk, xxxkk** xxxkkxsrc, srcsrc, nknkrxncm **************************************************publishing ms nlCalendar trackingnms:userTownersAgentBuilderPublick:builderxk:connections,xxtk initxtk listjeckjecfxtkjeckkFusion을 다시 시작하고 있습니다.jst**, **xtk:navtree**, **xtk:query** xk:queryxk:resource **menu**********************, xtk-schema, xtk scalscript, xxxk, xxk context, xxxk 컨텍스트, xxtxk, xtk, xfXFxtk,XF.
>이 목록은 완전하지 않다.

기존 스키마를 확장하는 방법에는 두 가지가 있습니다.

1. 소스 스키마를 직접 수정합니다.
1. 이름이 같지만 네임스페이스가 다른 스키마를 만드는 중입니다. 원본 스키마를 수정할 필요 없이 테이블을 확장할 수 있다는 장점이 있습니다.

   스키마의 루트 요소에는 확장될 스키마 이름의 **extendedSchema** 특성이 포함되어야 합니다.

   확장 스키마에 고유한 스키마가 없습니다.소스 스키마에서 생성된 스키마가 확장 스키마의 필드로 채워집니다.

   >[!IMPORTANT]
   >
   >응용 프로그램의 내장 스키마를 수정할 수 없으며 스키마 확장 메커니즘을 수정할 수 없습니다. 그렇지 않으면 응용 프로그램을 나중에 업그레이드할 때 수정된 스키마가 업데이트되지 않습니다. 이것은 Adobe Campaign을 사용하는 데 잘못된 기능을 초래할 수 있다.

   **예**:nms:recipient **스키마의** 확장입니다.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   nms: **recipient** extended 스키마는 확장 스키마에 채워진 필드로 채워집니다.

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   스키마의 루트 요소에 대한 **dependingSchemas** 속성은 확장 스키마에 대한 종속성을 참조합니다.

   필드 **의** categoryTo 속성은 선언할 스키마에서 채워집니다.

>[!IMPORTANT]
>
>수정 사항을 고려하려면 스키마를 재생성해야 합니다. For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.\
>수정 내용이 데이터베이스 구조에 영향을 주는 경우 업데이트를 실행해야 합니다. 자세한 내용은 [데이터베이스 구조 업데이트](../../configuration/using/updating-the-database-structure.md) 섹션을 참조하십시오.

