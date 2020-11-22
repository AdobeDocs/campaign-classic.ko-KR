---
solution: Campaign Classic
product: campaign
title: v5.11의 특정 구성
description: v5.11의 특정 구성
audience: migration
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 3%

---


# v5.11의 특정 구성{#specific-configurations-in-v5-11}

이 섹션에서는 v5.11에서 마이그레이션할 때 필요한 추가 구성에 대해 자세히 설명합니다. [일반 구성](../../migration/using/general-configurations.md) 섹션에 설명된 설정도 구성해야 합니다.

## 웹 애플리케이션 {#web-applications}

마이그레이션 중에 다음 경고가 자동으로 표시됩니다.

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side javascript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

웹 응용 프로그램의 일부 구성 요소(예: 다양한 공식 필드)에는 @id 속성이 있습니다. 웹 애플리케이션의 XML 코드에서 사용되며 더 이상 동일한 방식으로 생성되지 않습니다. 인터페이스에서는 표시되지 않으며 일반적으로 사용하지 않아야 합니다. 그러나 경우에 따라, 스타일시트 또는 JavaScript 코드를 사용하여 웹 애플리케이션의 렌더링을 개인화하는 데 @id 속성이 사용되었을 수 있습니다.

마이그레이션하는 동안에는 경고에 지정된 로그 파일 경로를 **확인해야** 합니다.

* **파일이 비어 있지 않습니다**.여기에는 마이그레이션 전에 기록된 불일치와 여전히 존재하는 경고가 포함됩니다. 존재하지 않는 ID를 참조하는 웹 응용 프로그램의 JavaScript 코드일 수 있습니다. 각 오류를 확인하고 수정해야 합니다.
* **파일이 비어 있습니다**.adobe campaign이 전혀 문제를 발견하지 못했다는 뜻이다.

파일이 비어 있는지 여부에 관계없이 이러한 ID가 다른 곳에서 구성에 사용되지 않는지 확인해야 합니다(이 경우 구성을 조정합니다.).

## 워크플로우 {#workflows}

Adobe Campaign 설치 디렉터리 이름이 변경되었으므로 마이그레이션 후 일부 워크플로가 작동하지 않을 수 있습니다. 워크플로가 해당 활동 중 하나에서 nl5 디렉토리를 참조하면 오류가 발생합니다. 이 참조를 **빌드로 대체합니다**. SQL 쿼리를 실행하여 이러한 워크플로우를 식별할 수 있습니다(PostgreSQL 예).

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

## 사용자 친화성 {#user-friendliness}

Adobe Campaign v5.11 홈 페이지는 더 이상 사용할 수 없습니다.

권장되지는 않지만, 특정 인터페이스를 Adobe Campaign v5.11에서 유지하려면 특정 솔루션이 있습니다. 자세한 내용은 Adobe에 문의하십시오.

## MySQL {#mysql}

>[!IMPORTANT]
>
>MySQL은 이 엔진을 사용하여 버전 6.02 또는 5.11에서 마이그레이션할 때 v7에서만 기본 데이터베이스 엔진으로 지원됩니다.

MySQL은 기본적으로 시간대를 관리하지 않습니다. 시간대 관리를 활성화하려면 다음 명령을 실행합니다.

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>자세한 내용은 https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html [페이지를](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) 참조하십시오.

데이터베이스 구조를 수정한 경우(예: 특정 인덱스 생성, SQL 뷰 생성 등) 마이그레이션 시 특정 예방 조치를 취해야 합니다. 실제로 마이그레이션 절차와의 비호환성에서 특정 수정 사항을 생성할 수 있습니다. 예를 들어 타임스탬프 필드가 포함된 SQL **보기** 만들기는 usetimestamptz **옵션과 호환되지** 않습니다. 따라서 아래의 권장 사항을 따를 것을 권장합니다.

1. 마이그레이션을 시작하기 전에 데이터베이스를 백업합니다.
1. SQL 변경 사항을 삭제합니다.
1. Adobe Campaign 7 [마이그레이션 사전 요구 사항 섹션에 설명된 절차에 따라 업그레이드 후](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) 를 수행합니다.
   >[!NOTE]
   >
   >Adobe Campaign 7 [마이그레이션 사전 요구 사항 섹션에 설명된 마이그레이션 단계를](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) 수행해야 합니다.
1. SQL 변경 사항을 다시 통합합니다.

이 예에서 **NmcTrackingLogMessages** 보기가 생성되었으며 여기에 **tslog라는** 타임스탬프 **필드가**&#x200B;있습니다. 이 경우 마이그레이션 절차가 실패하고 다음 오류 메시지가 나타납니다.

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

업그레이드 후 작업이 작동하는지 확인하려면 마이그레이션 전에 보기를 삭제하고 마이그레이션 후 다시 만든 후 TIMESTAMP WITH TIMEZONE 모드로 변경해야 합니다.

## 추적 {#tracking}

추적 공식이 수정되었습니다. 마이그레이션 시 이전 공식(v5)이 새 공식(v7)으로 대체됩니다. Adobe Campaign v5에서 개인화된 공식을 사용하는 경우, 이 구성은 Adobe Campaign v7(**NmsTracking_ClickFormula** 및 **NmsTracking_OpenFormula** 옵션)에서 수정해야 합니다.

웹 추적 관리도 수정되었습니다. v7으로의 마이그레이션이 수행되면 웹 추적 구성을 완료하려면 배포 마법사를 시작해야 합니다.

![](assets/migration_web_tracking.png)

다음 세 가지 모드를 사용할 수 있습니다.

* **세션 웹 추적**:패키지가 설치되어 있지 않은 경우 **[!UICONTROL Leads]** 기본적으로 이 옵션이 선택되어 있습니다. 이 옵션은 성능 면에서 가장 이상적인 옵션이므로 추적 로그의 크기를 제한할 수 있습니다.
* **영구 웹 추적**
* **익명 웹 추적**:패키지가 설치되어 있는 **[!UICONTROL Leads]** 경우 기본적으로 이 옵션이 선택되어 있습니다. 리소스를 많이 사용하는 옵션입니다. 위와 같이 sSourceId **열** 은 인덱싱되어야 합니다(추적 테이블 및 **CrmIncomingLead** 테이블).

>[!NOTE]
>
>이러한 세 가지 모드에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../configuration/using/about-web-tracking.md).

## Adobe Campaign v7 트리 구조 {#campaign-vseven-tree-structure}

마이그레이션 중에 트리 구조가 v7 표준에 따라 자동으로 재구성됩니다. 새 폴더가 추가되고, 오래된 폴더가 삭제되며, 해당 컨텐츠는 &quot;이동&quot; 폴더에 배치됩니다. 마이그레이션 후 이 폴더의 모든 항목을 확인해야 하며 컨설턴트는 이 항목을 보관하거나 각 항목을 삭제하기로 결정해야 합니다. 보관해야 할 물건들은 올바른 장소로 이동해야 한다.

탐색 트리의 자동 마이그레이션을 비활성화하기 위한 옵션이 추가되었습니다. 이제 이 작업은 수동입니다. 오래된 폴더는 삭제되지 않고 새 폴더가 추가되지 않습니다. 이 옵션은 기본 v5 탐색 트리가 너무 많은 변경을 거친 경우에만 사용해야 합니다. 노드에서 마이그레이션하기 전에 콘솔에 옵션을 **[!UICONTROL Administration > Options]** 추가합니다.

* 내부 이름:NlMigration_KeepFolderStructure
* 데이터 유형:정수
* 값(텍스트):1

이 옵션을 사용하는 경우 마이그레이션 후 오래된 폴더를 삭제하고 새 폴더를 추가하고 필요한 모든 검사를 실행해야 합니다.

**새 폴더 목록**:

마이그레이션 후 다음 폴더를 추가해야 합니다.

| 내부 이름 | 레이블 | 조건 |
|---|---|---|
| nmsAutoObjects | 자동으로 생성되는 개체 | - |
| nmsCampaignAdmin | 캠페인 관리 | - |
| nmsCampaignMgt | 캠페인 관리 | - |
| nmsCampaignRes | 캠페인 관리 | - |
| nmsModels | 템플릿 | - |
| nmsOnlineRes | 온라인 | - |
| nmsProduction | 프로덕션 | - |
| nmsProfileProcess | 프로세스 | - |
| xtkDashboard | 대시보드 | - |
| xtkPlatformAdmin | 플랫폼 | - |
| nmsLocalOrgUnit | 조직 단위 | - |
| nmsMRM | MRM | MRM이 설치됨 |
| nmsOperations | 캠페인 | 캠페인 설치됨 |

**오래된 폴더**&#x200B;목록:

마이그레이션 후 삭제할 오래된 폴더는 다음과 같습니다.

>[!NOTE]
>
>오래된 폴더의 전체 컨텐츠를 확인해야 하며, 각 항목에 대해 컨설턴트가 보관할지 또는 삭제할지를 결정합니다. 보관해야 할 항목들은 적절한 장소로 이동해야 한다.

| 내부 이름 | 레이블 | 조건 |
|---|---|---|
| nmsAdministration | 관리 | - |
| nmsDeliveryMgt | 캠페인 실행 | - |
| ncmContent | 콘텐츠 관리 | Content Manager 설치 |
| ncmForm | 입력 양식 | Content Manager 설치 |
| ncmImage | 이미지 | Content Manager 설치 |
| ncmJavascript | JavaScript 코드 | Content Manager 설치 |
| ncmJst | JavaScript 템플릿 | Content Manager 설치 |
| ncmParameters | 구성 | Content Manager 설치 |
| ncmSrcSchema | 데이터 스키마 | Content Manager 설치 |
| ncmStylesheet | XSL 스타일 파일 | Content Manager 설치 |
| nmsAdminPlan | 관리 | 캠페인 설치됨 |
| nmsResourcePlan | 리소스 | 캠페인 설치됨 |
| nmsResourcesModels | 템플릿 | 캠페인 설치됨 |
| nmsRootPlan | 캠페인 관리 | 캠페인 설치됨 |
| nmsOperator | 마케팅 운영자 | MRM이 설치됨 |

