---
product: campaign
title: 스키마 필터링
description: 스키마 필터링
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# 스키마 필터링{#filtering-schemas}

![](../../assets/v7-only.svg)

## 시스템 필터 {#system-filters}

사용 권한에 따라 특정 사용자에 대한 스키마 액세스를 필터링할 수 있습니다. 시스템 필터를 사용하면 **readAccess** 및 **writeAccess** 매개 변수를 사용하여 스키마에 자세히 나와 있는 엔터티의 읽기 및 쓰기 권한을 관리할 수 있습니다.

>[!NOTE]
>
>이 제한 사항은 기술 전문가가 아닌 사용자만 적용됩니다. 관련 권한이 있거나 워크플로우를 사용하는 기술 사용자는 데이터를 검색하고 업데이트할 수 있습니다.

* **readAccess**: 스키마 데이터에 대한 읽기 전용 액세스 권한을 제공합니다.

   **경고**  - 연결된 모든 테이블은 동일한 제한을 사용하여 설정해야 합니다. 이 구성은 성능에 영향을 줄 수 있습니다.

* **writeAccess**: 스키마 데이터에 대한 쓰기 액세스를 제공합니다.

이러한 필터는 스키마의 기본 **요소** 수준에서 입력되며, 다음 예와 같이 액세스를 제한하려면 형식을 지정할 수 있습니다.

* 쓰기 권한 제한

   여기서는 ADMINISTRATION 권한 없이 연산자에 대해 스키마에 대한 WRITE 권한을 허용하지 않는 데 필터를 사용합니다. 즉, 관리자만 이 스키마에서 설명하는 엔터티에 대한 쓰기 권한이 있습니다.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* 읽기 및 쓰기 권한 제한:

   여기서는 모든 연산자에 대해 스키마에 대한 읽기 및 쓰기 권한을 모두 허용하지 않는 데 필터를 사용합니다. &quot;$(loginId)&quot; 식으로 표시되는 **internal** 계정만 표시합니다.= 0&quot;에는 이러한 권한이 있습니다.

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   조건을 정의하는 데 사용되는 가능한 **expr** 속성 값은 TRUE 또는 FALSE입니다.

>[!NOTE]
>
>필터를 지정하지 않으면 모든 연산자는 스키마에 대한 읽기 및 쓰기 권한을 갖습니다.

## Protect 기본 제공 스키마 {#protecting-built-in-schemas}

기본적으로 내장 스키마에는 ADMINISTRATION 권한이 있는 연산자에 대한 WRITE 권한만 있으면 액세스할 수 있습니다.

* ncm:게시
* nl:모니터링
* nms:달력
* xtk:builder
* xtk:연결
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
>**xtk:sessionInfo** 스키마에 대한 읽기 및 쓰기 권한은 Adobe Campaign 인스턴스의 내부 계정에서만 액세스할 수 있습니다.

## 기본 제공 스키마의 시스템 필터 수정 {#modifying-system-filters-of-built-in-schemas}

이전 버전과의 호환성 문제로 인해 기본적으로 보호되는 기본 제공 스키마의 시스템 필터를 수정할 수 있습니다.

>[!NOTE]
>
>그러나 Adobe은 최적의 보안을 위해 기본 매개 변수를 수정하지 않는 것을 권장합니다.

1. 관련 스키마에 대한 확장을 만들거나 기존 확장을 엽니다.
1. 기본 요소에 하위 요소 **`<sysfilter name="<filter name>" _operation="delete"/>`**&#x200B;을 추가하여 원본 스키마에서 동일한 필터 적용을 삭제합니다.
1. 원한다면 [시스템 필터](#system-filters)에 자세히 설명된 대로 새 필터를 추가할 수 있습니다.
