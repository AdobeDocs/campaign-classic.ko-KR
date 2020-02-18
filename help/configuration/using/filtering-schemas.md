---
title: 스키마 필터링
seo-title: 스키마 필터링
description: 스키마 필터링
seo-description: null
page-status-flag: never-activated
uuid: 04a90785-3084-42fd-85af-77bc28687579
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 64d4c5b8-db0b-4287-8d30-4bf09878a401
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 스키마 필터링{#filtering-schemas}

## 시스템 필터 {#system-filters}

권한에 따라 특정 사용자에 대한 스키마 액세스를 필터링할 수 있습니다. 시스템 필터를 사용하면 readAccess 및 writeAccess 매개 변수를 사용하여 스키마에 자세히 설명된 엔티티의 읽기 및 쓰기 권한을 관리할 **수** **** 있습니다.

>[!NOTE]
>
>이 제한은 기술 지식이 없는 사용자에게만 적용됩니다.관련 권한이 있거나 워크플로우를 사용하는 기술 사용자는 데이터를 검색하고 업데이트할 수 있습니다.

* **readAccess**:스키마 데이터에 대한 읽기 전용 액세스 권한을 제공합니다.

   **경고** - 연결된 모든 테이블은 동일한 제한으로 설정해야 합니다. 이 구성은 성능에 영향을 줄 수 있습니다.

* **writeAccess**:스키마 데이터에 대한 쓰기 액세스를 제공합니다.

이러한 필터는 스키마의 기본 **요소** 수준에서 입력되며, 다음 예에서 보듯이 액세스를 제한하기 위해 형식을 지정할 수 있습니다.

* 쓰기 권한 제한

   여기에서 필터는 ADMINISTRATION 권한 없이 연산자에 대한 WRITE 권한을 허용하지 않는 데 사용됩니다. 즉, 관리자만 이 스키마에서 설명하는 개체에 대한 쓰기 권한을 갖습니다.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* 읽기 및 쓰기 권한 제한:

   여기에서 필터는 모든 연산자에 대해 스키마에 대한 읽기 및 쓰기 권한을 모두 허용하지 않는 데 사용됩니다. &quot;$(loginId)&quot; 표현식으로 표현되는 **내부** 계정만!= 0&quot;에 이러한 권한이 있습니다.

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   조건을 정의하는 데 사용되는 **expr** 속성 값은 TRUE 또는 FALSE입니다.

>[!NOTE]
>
>필터를 지정하지 않으면 모든 연산자가 스키마에 대한 읽기 및 쓰기 권한을 갖게 됩니다.

## 내장된 스키마 보호 {#protecting-built-in-schemas}

기본적으로 내장 스키마는 관리 권한이 있는 연산자에 대한 WRITE 권한을 통해서만 액세스할 수 있습니다.

* ncm:게시
* nl:모니터링
* nms:일정
* xtk:builder
* xtk:연결
* xtk:dbInit
* xtk:entityBackup새로운 기능
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:양식
* xtk:funcList
* xtk:fusion
* xtk:이미지
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:스키마
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:문자열
* xtk:xslt

>[!IMPORTANT]
>
>xtk:sessionInfo **스키마에 대한** READ 및 WRITE 권한은 Adobe Campaign 인스턴스의 내부 계정에서만 액세스할 수 있습니다.

## 내장 스키마의 시스템 필터 수정 {#modifying-system-filters-of-built-in-schemas}

이전 버전과의 호환성 문제로 인해 기본적으로 보호되는 기본 스키마의 시스템 필터를 수정할 수 있습니다.

>[!NOTE]
>
>그러나 최적의 보안을 보장하도록 기본 매개 변수를 수정하지 않는 것이 좋습니다.

1. 관련 스키마의 확장을 만들거나 기존 확장을 엽니다.
1. 기본 **`<sysfilter name="<filter name>" _operation="delete"/>`** 요소에 자식 요소를 추가하여 원본 스키마에서 동일한 필터 응용 프로그램을 삭제합니다.
1. 원하는 경우 시스템 필터에 [설명된 대로 새 필터를 추가할 수](#system-filters)있습니다.

