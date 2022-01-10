---
product: campaign
title: 구성 조정
description: Campaign v7로 마이그레이션하기 전후에 구성을 조정하는 방법을 알아봅니다
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 327f220d6700242308ef3738a38cc95b970e3f46
workflow-type: tm+mt
source-wordcount: '1980'
ht-degree: 3%

---

# 구성 조정{#configuring-your-platform}

![](../../assets/v7-only.svg)

Adobe Campaign v7의 특정 주요 변경 사항에는 특정 구성이 필요합니다. 마이그레이션 전이나 후에 이러한 구성이 필요할 수 있습니다.

Campaign v5 또는 v6에서 마이그레이션할 때 Adobe Campaign v7에서 수행할 세부 구성은 [이 페이지](general-configurations.md).


마이그레이션 중에 **NmsRecipient** 테이블이 스키마 정의에서 다시 작성됩니다. Adobe Campaign 외부에 있는 이 테이블의 SQL 구조에 대한 모든 변경 사항은 손실됩니다.

확인할 요소의 예:

* 열(또는 인덱스)을 **NmsRecipient** 그러나 스키마에 자세히 설명되어 있지 않으므로 저장되지 않습니다.
* 다음 **테이블스페이스** 속성은 기본적으로 해당 값을 되돌립니다(즉, 배포 마법사에 정의된 값).
* 에 참조 보기를 추가한 경우 **NmsRecipient** 표, 마이그레이션하기 전에 삭제해야 합니다.


## 마이그레이션 전 {#before-the-migration}

Adobe Campaign v7로 마이그레이션할 때 다음 요소를 구성해야 합니다. 시작하기 전에 이러한 요소를 해결해야 합니다 **postupgrade**.

* 시간대

   v5.11 플랫폼에서 마이그레이션하는 동안 업그레이드 후 사용할 시간대를 지정해야 합니다.

   다중 시간대 모드를 사용하려면 다음을 참조하십시오 [이 섹션](../../migration/using/general-configurations.md#time-zones).

   oracle을 데이터베이스로 사용하는 경우 Oracle 시간대 파일이 애플리케이션 서버와 데이터베이스 서버 간에 제대로 동기화되었는지 확인합니다. [자세히 알아보기](../../migration/using/general-configurations.md#oracle)

* 보안 영역

   보안상의 이유로 기본적으로 Adobe Campaign 플랫폼에 더 이상 액세스할 수 없습니다. 마이그레이션 전에 사용자 IP 주소를 수집해야 하는 보안 영역을 구성해야 합니다. [자세히 알아보기](../../migration/using/general-configurations.md#security)

* 구문

   새 인터프리터를 사용하기 때문에 일부 Javascript 코드가 v7 버전에서 더 이상 허용되지 않을 수 있습니다. [자세히 알아보기](../../migration/using/general-configurations.md#javascript)

   마찬가지로 SQLData 기반 구문을 대체하기 위해 Adobe Campaign v7에 새로운 구문이 도입되었습니다. 이 구문과 함께 코드 요소를 사용하는 경우 이를 조정해야 합니다. [자세히 알아보기](../../migration/using/general-configurations.md#sqldata)

* 암호

   를 구성해야 합니다 **관리** 및 **내부** 암호. [자세히 알아보기](../../migration/using/before-starting-migration.md#user-passwords)

* 트리 구조

   v5.11 플랫폼에서 마이그레이션하는 경우 Adobe Campaign v6 규칙에 따라 트리 구조 폴더를 재구성해야 합니다. [자세히 알아보기](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* 상호 작용

   Campaign v6.02에서 마이그레이션하고  **상호 작용** 모듈, v7에 더 이상 존재하지 않는 6.02 스키마 참조를 모두 삭제해야 합니다. [자세히 알아보기](../../migration/using/general-configurations.md#interaction)

## 마이그레이션 후 {#after-the-migration}

실행 후 **postupgrade**, 다음 요소를 확인하고 구성합니다.

* 미러 페이지

   미러 페이지 개인화 블록이 v6.x에서 변경되었습니다. 이 새 버전은 이러한 페이지에 액세스할 때 보안을 개선합니다.

   메시지에서 v5 개인화 블록을 사용한 경우 미러 페이지 표시가 실패합니다. Adobe은 메시지에 미러 페이지를 삽입할 때 새로운 개인화 블록을 사용할 것을 권장합니다.

   그러나 임시 해결 방법으로서(미러 페이지가 아직 라이브 상태일 때) 옵션을 변경하여 이 문제를 방지하려면 이전 개인화 블록으로 돌아갈 수 있습니다 **[!UICONTROL XtkAcceptOldPasswords]** 다음으로 설정 **[!UICONTROL 1]**. 이렇게 해도 새 v6.x 개인화 블록의 사용에는 영향을 주지 않습니다.

* 구문

   구문과 관련된 오류가 발생하면 업그레이드 후 일시적으로 를 활성화해야 합니다 **allowSQLInjection** 옵션 **serverConf.xml** 파일, 이렇게 하면 코드를 다시 작성할 수 있습니다. 코드가 적용되면 보안을 다시 활성화해야 합니다. [자세히 알아보기](../../migration/using/general-configurations.md#sqldata)

* 충돌

   마이그레이션은 업그레이드 후 수행되며 충돌이 보고서, 양식 또는 웹 애플리케이션에 표시될 수 있습니다. 콘솔에서 이러한 충돌을 해결할 수 있습니다. [자세히 알아보기](../../migration/using/general-configurations.md#conflicts)

* Tomcat

   설치 폴더를 사용자 지정한 경우 마이그레이션 후 올바르게 업데이트되었는지 확인합니다. [자세히 알아보기](../../migration/using/general-configurations.md#tomcat)

* 보고서

   모든 기본 제공 보고서는 현재 v6.x 렌더링 엔진을 사용합니다. 보고서에 JavaScript 코드를 추가한 경우 일부 요소가 영향을 받을 수 있습니다. [자세히 알아보기](../../migration/using/general-configurations.md#reports)

* 웹 애플리케이션

   업그레이드 후 식별된 웹 응용 프로그램에 연결하는 데 문제가 있으면 **allowUserPassword** 및 **sessionTokenOnly** 옵션 **serverConf.xml** 파일. 보안 문제를 방지하려면 문제가 해결된 후 이 두 옵션을 다시 활성화해야 합니다. [자세히 알아보기](../../migration/using/general-configurations.md#identified-web-applications)

   웹 응용 프로그램의 유형과 구성에 따라 해당 응용 프로그램이 제대로 작동하도록 추가 조작을 수행해야 합니다. [자세히 알아보기](../../migration/using/general-configurations.md#web-applications)

   v5.11 플랫폼에서 마이그레이션하는 경우 추가 구성을 수행해야 합니다. [자세히 알아보기](../../migration/using/general-configurations.md#specific-configurations-in-v5-11.md)

* 보안 영역

   서버를 시작하기 전에 보안 영역을 구성해야 합니다. [추가 정보](../../installation/using/security-zones.md) 및 [여기에서 확인하십시오.](../../migration/using/general-configurations.md#security)

* 워크플로우

   v5.11 플랫폼에서 마이그레이션하는 경우 워크플로우 폴더를 확인해야 합니다. [자세히 알아보기](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* 추적

   v5.11 플랫폼에서 마이그레이션하는 경우 추적 모드를 구성해야 합니다. [자세히 알아보기](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* 상호 작용

   만약 **상호 작용**, 마이그레이션 후에는 모든 매개 변수를 조정해야 합니다. [자세히 알아보기](../../migration/using/general-configurations.md#interaction)

* 대시보드

   클라이언트 오류가 표시되면 대시보드를 새 Adobe Campaign v7 코드로 업데이트하거나 v6.02 인스턴스에서 v7 인스턴스로 다음 파일을 수동으로 복사해야 합니다.

   ```
   v6.02 files and spaces:
   /usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
   /usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
   v6.1 files and spaces:
   /usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
   /usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
   ```


## v5.11에서 v7로 특정 구성{#specific-configurations-in-v5-11}

![](../../assets/v7-only.svg)

이 섹션에서는 v5.11에서 마이그레이션할 때 필요한 추가 구성에 대해 자세히 설명합니다. 또한 [일반 구성](../../migration/using/general-configurations.md) 섹션을 참조하십시오.

### 웹 애플리케이션 {#web-applications-v5}

마이그레이션 중에 다음 경고가 자동으로 표시됩니다.

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

웹 응용 프로그램의 일부 구성 요소(예: 다양한 공식 필드)에는 @id 속성이 있습니다. 이러한 파일은 웹 응용 프로그램의 XML 코드에서 사용되며 더 이상 동일한 방식으로 생성되지 않습니다. 인터페이스에는 표시되지 않으며 일반적으로 사용해서는 안 됩니다. 그러나 경우에 따라 @id 속성을 사용하여 스타일시트를 통해 또는 JavaScript 코드를 사용하여 웹 응용 프로그램의 렌더링을 개인화할 수 있습니다.

마이그레이션 중에 **반드시** 경고에 지정된 로그 파일 경로를 확인합니다.

* **파일이 비어 있지 않습니다**: 여기에는 마이그레이션 전에 기록된 불일치가 발생하고 여전히 존재하는 경고가 포함되어 있습니다. 존재하지 않는 ID를 참조하는 웹 애플리케이션에서 JavaScript 코드일 수 있습니다. 각 오류를 확인하고 수정해야 합니다.
* **파일이 비어 있습니다.**: 즉, Adobe Campaign에서 문제를 감지하지 못했습니다.

파일이 비어 있는지 여부에 관계없이, 이러한 ID가 다른 곳에서 구성에 사용되지 않는지 확인해야 합니다(이 경우 구성을 조정).

### 워크플로우 {#workflows}

Adobe Campaign 설치 디렉토리의 이름이 변경되었으므로 마이그레이션 후 일부 워크플로우가 작동하지 않을 수 있습니다. 워크플로우가 활동 중 하나에서 nl5 디렉토리를 참조하는 경우 오류가 발생합니다. 이 참조를 다음으로 바꾸기 **빌드**. SQL 쿼리를 실행하여 이러한 워크플로우를 식별할 수 있습니다(PostgreSQL 예).

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

### MySQL {#mysql}

>[!CAUTION]
>
>MySQL은 이 엔진을 사용하여 버전 6.02 또는 5.11에서 마이그레이션할 때 v7에서만 기본 데이터베이스 엔진으로 지원됩니다.

MySQL은 기본적으로 시간대를 관리하지 않습니다. 시간대 관리를 사용하려면 다음 명령을 실행하십시오.

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>자세한 내용은 [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) 페이지.

데이터베이스 구조를 수정한 경우(예: 특정 인덱스를 만들고 SQL 보기 만들기 등) 구성 중에 마이그레이션할 때 특정 주의 사항이 수행되어야 합니다. 실제로, 마이그레이션 절차와의 호환되지 않으므로 특정 수정 사항을 생성할 수 있습니다. 예를 들어 **Timestamp** 필드가 **usetimestamptz** 선택 사항입니다. 따라서 아래 권장 사항을 따르는 것이 좋습니다.

1. 마이그레이션을 시작하기 전에 데이터베이스를 백업합니다.
1. SQL 변경 내용을 삭제합니다.
1. 업그레이드 후 수행
   >[!NOTE]
   >
   >에 제시된 마이그레이션 단계를 따라야 합니다. [이 섹션](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md).
1. SQL 변경 사항을 다시 통합합니다.

이 예제에서는 **NmcTrackingLogMessages** 보기가 생성되었으며 **Timestamp** 이름이 지정된 필드 **tslog**. 이 경우 마이그레이션 절차가 실패하고 다음 오류 메시지가 표시됩니다.

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

업그레이드 후 작업이 작동하는지 확인하려면 마이그레이션 전에 보기를 삭제하고 마이그레이션 후 TIMESTAMP WITH TIMEZONE 모드에 적용하는 동안 해당 보기를 다시 만들어야 합니다.

### 추적 {#tracking}

추적 공식이 수정되었습니다. 마이그레이션할 때 이전 공식(v5)은 새 공식(v7)로 대체됩니다. Adobe Campaign v5에서 개인화된 공식을 사용하는 경우 이 구성을 Adobe Campaign v7에서 수정해야 합니다(**NmsTracking_ClickFormula** 및 **NmsTracking_OpenFormula** 옵션).

웹 추적 관리도 수정되었습니다. v7로의 마이그레이션이 수행되면 배포 마법사를 시작하여 웹 추적 구성을 완료해야 합니다.

![](assets/migration_web_tracking.png)

다음 세 가지 모드를 사용할 수 있습니다.

* **세션 웹 추적**: 만약 **[!UICONTROL Leads]** 패키지가 설치되지 않았습니다. 이 옵션은 기본적으로 선택됩니다. 이 옵션은 성능 측면에서 가장 이상적입니다. 이 옵션을 사용하면 추적 로그 크기를 제한할 수 있습니다.
* **영구 웹 추적**
* **익명 웹 추적**: 만약 **[!UICONTROL Leads]** 패키지가 설치되면 기본적으로 이 옵션이 선택됩니다. 리소스를 가장 많이 사용하는 옵션입니다. 위와 같이, **sSourceId** 열은 인덱싱되어야 합니다(추적 테이블 및 **CrmIncomingLead** 테이블).

>[!NOTE]
>
>이러한 세 가지 모드에 대한 자세한 내용은 [이 섹션](../../configuration/using/about-web-tracking.md).

### Adobe Campaign v7 트리 구조 {#campaign-vseven-tree-structure}

마이그레이션 중에 트리 구조가 v7 표준에 따라 자동으로 재구성됩니다. 새 폴더가 추가되고, 오래된 폴더가 삭제되고, 해당 컨텐츠가 &quot;이동&quot; 폴더에 배치됩니다. 마이그레이션 후 이 폴더의 모든 항목을 확인해야 하며 컨설턴트는 이를 보관하거나 각 항목을 삭제하도록 결정해야 합니다. 보관해야 할 품목들은 적당한 곳으로 이동해야 한다.

탐색 트리의 자동 마이그레이션을 비활성화하는 옵션이 추가되었습니다. 이제 이 작업은 수동 작업입니다. 오래된 폴더는 삭제되지 않으며 새 폴더는 추가되지 않습니다. 이 옵션은 기본 제공 v5 탐색 트리가 너무 많은 변경 사항을 거친 경우에만 사용해야 합니다. 마이그레이션하기 전에 콘솔에서 옵션을 추가합니다. **[!UICONTROL Administration > Options]** 노드:

* 내부 이름: NlMigration_KeepFolderStructure
* 데이터 유형: 정수
* 값(텍스트): 1

이 옵션을 사용하는 경우 마이그레이션 후 오래된 폴더를 삭제하고 새 폴더를 추가하고 필요한 모든 검사를 실행해야 합니다.

**새 폴더 목록**:

마이그레이션 후 다음 폴더를 추가해야 합니다.

| 내부 이름 | 레이블 | 조건 |
|---|---|---|
| nmsAutoObjects | 자동으로 생성된 개체 | - |
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
| nmsOperations | 캠페인 | 캠페인 설치 |

**오래된 폴더 목록**:

마이그레이션 후 삭제할 오래된 폴더는 다음과 같습니다.

>[!NOTE]
>
>오래된 폴더의 전체 컨텐츠를 확인해야 하며, 각 항목에 대해 컨설턴트가 보관 또는 삭제 여부를 결정합니다. 보관할 항목은 적절한 위치로 이동해야 합니다.

| 내부 이름 | 레이블 | 조건 |
|---|---|---|
| nmsAdministration | 관리 | - |
| nmsDeliveryMgt | 캠페인 실행 | - |
| ncmContent | 콘텐츠 관리 | Content Manager가 설치됨 |
| ncmForm | 입력 양식 | Content Manager가 설치됨 |
| ncmImage | 이미지 | Content Manager가 설치됨 |
| ncmJavascript | JavaScript 코드 | Content Manager가 설치됨 |
| ncmJst | JavaScript 템플릿 | Content Manager가 설치됨 |
| ncmParameters | 구성 | Content Manager가 설치됨 |
| ncmSrcSchema | 데이터 스키마 | Content Manager가 설치됨 |
| ncmStylesheet | XSL 스타일 파일 | Content Manager가 설치됨 |
| nmsAdminPlan | 관리 | 캠페인 설치 |
| nmsResourcePlan | 리소스 | 캠페인 설치 |
| nmsResourcesModels | 템플릿 | 캠페인 설치 |
| nmsRootPlan | 캠페인 관리 | 캠페인 설치 |
| nmsOperator | 마케팅 운영자 | MRM이 설치됨 |


## v6.02에서 v7로 특정 구성{#specific-configurations-in-v6-02}

![](../../assets/v7-only.svg)

다음 섹션에서는 v6.02에서 마이그레이션할 때 필요한 추가 구성에 대해 자세히 설명합니다. 또한 [이 페이지](../../migration/using/general-configurations.md).

### 웹 애플리케이션 {#web-applications-v6}

v6.02에서 마이그레이션하는 경우 개요 유형 웹 응용 프로그램에 대한 오류 로그가 표시될 수 있습니다. 오류 메시지 예:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

이러한 웹 응용 프로그램은 SQLData를 사용하며 보안이 강화되어 v7와 호환되지 않습니다. 이러한 오류로 인해 마이그레이션 오류가 발생합니다.

이러한 웹 응용 프로그램을 사용하지 않은 경우 다음 정리 스크립트를 실행하고 업그레이드 후 를 다시 실행하십시오.

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

이러한 웹 응용 프로그램을 수정한 후 v7에서 계속 사용하려면 **allowSQLInjection** 다른 보안 영역에서 옵션을 선택하고 업그레이드 후 다시 시작합니다. 자세한 내용은 [SQLData](../../migration/using/general-configurations.md#sqldata) 섹션에 자세히 설명되어 있습니다.

### 메시지 센터 {#message-center}

메시지 센터 제어 인스턴스 마이그레이션 후 이를 수행하려면 트랜잭션 메시지 템플릿을 다시 게시해야 합니다.

v7에서 실행 인스턴스의 트랜잭션 메시지 템플릿 이름이 변경되었습니다. 이 매개 변수에는 현재 생성된 컨트롤 인스턴스에 해당하는 연산자 이름이 접두사로 추가됩니다 **control1_template1_rt** (다음과 같은 경우) **control1** 은 연산자의 이름입니다. 대량의 템플릿이 있는 경우 제어 인스턴스에서 이전 템플릿을 삭제하는 것이 좋습니다.