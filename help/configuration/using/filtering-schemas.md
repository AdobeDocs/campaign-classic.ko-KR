---
product: campaign
title: 스키마 필터링
description: 스키마 필터링
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# 스키마 필터링{#filtering-schemas}

## 시스템 필터 {#system-filters}

권한에 따라 특정 사용자에 대한 스키마 액세스를 필터링할 수 있습니다. 시스템 필터를 사용하면 스키마에 설명된 엔티티의 읽기 및 쓰기 권한을 관리할 수 있습니다. **readAccess** 및 **writeAccess** 매개 변수.

>[!NOTE]
>
>이 제한은 기술 사용자가 아닌 사용자에게만 적용됩니다. 관련 권한이 있거나 워크플로우를 사용하는 기술 사용자는 데이터를 검색하고 업데이트할 수 있습니다.

* **readAccess**: 스키마 데이터에 대한 읽기 전용 액세스를 제공합니다.

   **경고** - 연결된 모든 테이블은 동일한 제한으로 설정해야 합니다. 이 구성은 성능에 영향을 줄 수 있습니다.

* **writeAccess**: 스키마 데이터에 대한 쓰기 액세스 권한을 제공합니다.

이 필터는 메인에 입력됩니다 **요소** 다음 예제에 표시된 대로 스키마 및 스키마 수준을 형성하여 액세스를 제한할 수 있습니다.

* 쓰기 권한 제한

   여기서 필터는 ADMINISTRATION 권한이 없는 연산자에 대해 스키마에 대한 WRITE 권한을 허용하지 않는 데 사용됩니다. 즉, 관리자만 이 스키마에서 설명한 엔티티에 대한 쓰기 권한을 갖습니다.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* 읽기 및 쓰기 권한 제한:

   여기서 필터는 모든 연산자에 대해 스키마에 대한 읽기 및 쓰기 권한을 모두 허용하지 않는 데 사용됩니다. 만 **내부** 계정, 표현식 &quot;$(loginId)!=0&quot;에는 이러한 권한이 있습니다.

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   가능 **expr** 조건을 정의하는 데 사용되는 속성 값은 TRUE 또는 FALSE입니다.

>[!NOTE]
>
>필터를 지정하지 않으면 모든 연산자는 스키마에 대한 읽기 및 쓰기 권한을 갖게 됩니다.

## Protect 기본 스키마 {#protecting-built-in-schemas}

기본적으로 기본 제공 스키마는 관리 권한이 있는 연산자에 대한 쓰기 권한으로만 액세스할 수 있습니다.

* ncm:게시
* nl:monitoring
* nms:calendar
* xtk:builder
* xtk:connections
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusion
* xtk:image
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:strings
* xtk:xslt

>[!IMPORTANT]
>
>읽기 및 쓰기 권한 **xtk:sessionInfo** 스키마는 Adobe Campaign 인스턴스의 내부 계정에서만 액세스할 수 있습니다.

## 기본 제공 스키마의 시스템 필터 수정 {#modifying-system-filters-of-built-in-schemas}

이전 버전과의 호환성 문제로 인해 기본적으로 보호되는 기본 제공 스키마의 시스템 필터를 수정할 수 있습니다.

>[!NOTE]
>
>Adobe 그러나 최적의 보안을 보장하기 위해 기본 매개 변수를 수정하지 않는 것이 좋습니다.

1. 관련 스키마에 대한 확장을 만들거나 기존 확장을 엽니다.
1. 하위 요소 추가 **`<sysfilter name="<filter name>" _operation="delete"/>`** 원본 스키마에서 필터 적용을 삭제하는 기본 요소입니다.
1. 원하는 경우 다음에 자세히 설명된 대로 새 필터를 추가할 수 있습니다. [시스템 필터](#system-filters).
