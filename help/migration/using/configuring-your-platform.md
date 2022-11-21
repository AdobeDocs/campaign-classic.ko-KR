---
product: campaign
title: 구성 조정
description: Campaign v7로 마이그레이션하기 전후에 구성을 조정하는 방법을 알아봅니다
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 2594e4943ba24ae65d1fc005da589dc674aa2b0f
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 2%

---

# 구성 조정{#configuring-your-platform}

![](../../assets/v7-only.svg)

Adobe Campaign v7의 특정 주요 변경 사항에는 특정 구성이 필요합니다. 마이그레이션 전이나 후에 이러한 구성이 필요할 수 있습니다.

마이그레이션 중에 **NmsRecipient** 테이블이 스키마 정의에서 다시 작성됩니다. Adobe Campaign 외부에 있는 이 테이블의 SQL 구조에 대한 모든 변경 사항은 손실됩니다.

확인할 요소의 예:

* 열(또는 인덱스)을 **NmsRecipient** 그러나 스키마에 자세히 설명되어 있지 않으므로 저장되지 않습니다.
* 다음 **테이블스페이스** 속성은 기본적으로 해당 값을 되돌립니다(즉, 배포 마법사에 정의된 값).
* 에 참조 보기를 추가한 경우 **NmsRecipient** 표, 마이그레이션하기 전에 삭제해야 합니다.


## 마이그레이션 전 {#before-the-migration}

Adobe Campaign v7로 마이그레이션할 때 다음 요소를 구성해야 합니다. 시작하기 전에 이러한 요소를 해결해야 합니다 **postupgrade**.

<!--

  * Timezones

  During a migration from a v5.11 platform, you must specify the timezone to use during the postupgrade.

  If you wish to use the "multi timezone" mode, refer to [this section](../../migration/using/general-configurations.md#time-zones).

  If you use Oracle as a database, check that the Oracle timezone files have properly been synched between the application server and the database server. [Learn more](../../migration/using/general-configurations.md#oracle)

* Security zones

  For security reasons, the Adobe Campaign platform is no longer accessible by default: you must configure the security zones, which requires collecting the user IP addresses before the migration. [Learn more](../../migration/using/general-configurations.md#security)

* Syntax

  Some Javascript code may no longer accepted in the v7 version, due to the use of a new interpreter. [Learn more](../../migration/using/general-configurations.md#javascript).

  Similarly, a new syntax is introduced in Adobe Campaign v7 to replace the SQLData based syntax. If you use code elements with this syntax, you must adapt them. [Learn more](../../migration/using/general-configurations.md#sqldata)

  -->

* 암호

   를 구성해야 합니다 **관리** 및 **내부** 암호. [자세히 알아보기](../../migration/using/before-starting-migration.md#user-passwords)

<!--
* Tree structure

  If migrating from a v5.11 platform, you must reorganize the tree structure folders according to Adobe Campaign v6 norms. [Learn more](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).

-->

<!--

* Interaction

  If you are migrating from Campaign v6.02 and using the  **Interaction** module, you must delete all 6.02 schema references that no longer exist in v7. [Learn more](../../migration/using/general-configurations.md#interaction)

-->

## 마이그레이션 후 {#after-the-migration}

실행 후 **postupgrade**, 다음 요소를 확인하고 구성합니다.

* 미러 페이지

   미러 페이지 개인화 블록이 v6.x에서 변경되었습니다. 이 새 버전은 이러한 페이지에 액세스할 때 보안을 개선합니다.

   메시지에서 v5 개인화 블록을 사용한 경우 미러 페이지 표시가 실패합니다. Adobe은 메시지에 미러 페이지를 삽입할 때 새로운 개인화 블록을 사용할 것을 권장합니다.

   그러나 임시 해결 방법으로서(미러 페이지가 아직 라이브 상태일 때) 옵션을 변경하여 이 문제를 방지하려면 이전 개인화 블록으로 돌아갈 수 있습니다 **[!UICONTROL XtkAcceptOldPasswords]** 다음으로 설정 **[!UICONTROL 1]**. 이렇게 해도 새 v6.x 개인화 블록의 사용에는 영향을 주지 않습니다.

* 구문

   구문과 관련된 오류가 발생하면 업그레이드 후 일시적으로 를 활성화해야 합니다 **allowSQLInjection** 옵션 **serverConf.xml** 파일, 이렇게 하면 코드를 다시 작성할 수 있습니다. 코드가 적용되면 보안을 다시 활성화해야 합니다.

* 충돌

   마이그레이션은 업그레이드 후 수행되며 충돌이 보고서, 양식 또는 웹 애플리케이션에 표시될 수 있습니다. 콘솔에서 이러한 충돌을 해결할 수 있습니다.

* Tomcat

   설치 폴더를 사용자 지정한 경우 마이그레이션 후 올바르게 업데이트되었는지 확인합니다.

* 보고서

   모든 기본 제공 보고서는 현재 v6.x 렌더링 엔진을 사용합니다. 보고서에 JavaScript 코드를 추가한 경우 일부 요소가 영향을 받을 수 있습니다.

* 웹 애플리케이션

   업그레이드 후 식별된 웹 응용 프로그램에 연결하는 데 문제가 있으면 **allowUserPassword** 및 **sessionTokenOnly** 옵션 **serverConf.xml** 파일. 보안 문제를 방지하려면 문제가 해결된 후 이 두 옵션을 다시 활성화해야 합니다.

   웹 응용 프로그램의 유형과 구성에 따라 해당 응용 프로그램이 제대로 작동하도록 추가 조작을 수행해야 합니다.

<!--
  If migrating from a v5.11 platform, additional configurations must be carried out. [Learn more](../../migration/using/general-configurations.md#specific-configurations-in-v5-11.md)

* Security zones

  Before starting the server, you must configure the security zones. [Learn more](../../installation/using/security-zones.md) and [see here](../../migration/using/general-configurations.md#security)

-->

<!--

* Workflows

  If migrating from a v5.11 platform, you must check the workflows folder. [Learn more](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

-->

<!--

* Tracking

  If migrating from a v5.11 platform, you must configure the tracking mode. [Learn more](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

-->

* 상호 작용

   만약 **상호 작용**, 마이그레이션 후에는 모든 매개 변수를 조정해야 합니다.

<!--

* Dashboards

  If a client error appears, you have to either update your dashboards with the new Adobe Campaign v7 code, or manually copy the following files from the v6.02 instance to the v7 instance:

  ```
  v6.02 files and spaces:
  /usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
  /usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
  v6.1 files and spaces:
  /usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
  /usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
  ```

-->

<!--

## Specific configurations from a v5.11 to v7{#specific-configurations-in-v5-11}

![](../../assets/v7-only.svg)

This section details the additional configuration required when migrating from v5.11. You should also configure the settings detailed in the [General configurations](../../migration/using/general-configurations.md) section.

### Web applications {#web-applications-v5}

The following warning will be displayed automatically during migration:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Some components of web applications, for instance the various formula fields, have @id attributes. These are used in the XML code of web applications and are no longer generated in the same way. They are not visible in the interface and you must not normally use them. However, in some cases, @id attributes may have been used to personalize the rendering of web applications, for instance via a stylesheet or using JavaScript code.

During migration, you **must** check the log file path specified in the warning:

* **The file is not empty**: it contains warnings which concern inconsistencies recorded before migration and which still exist. This can be JavaScript code in a web application which references a non-existent ID. Each error must be checked and corrected.
* **The file is empty**: this means that Adobe Campaign has not detected any issues.

Whether the file is empty or not, you must check that these IDs are not used for configuration elsewhere (and adapt configuration if this is the case).

### Workflows {#workflows}

Since the name of the Adobe Campaign installation directory has changed, some workflows may not work after the migration. If a workflow references the nl5 directory in one of its activities, this will raise an error. Replace this reference with **build**. You can run an SQL query to identify these workflows (PostgreSQL example):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

### MySQL {#mysql}

>[!CAUTION]
>
>MySQL is only supported in v7 as the main database engine when migrating from version 6.02 or 5.11 using this engine.

MySQL does not manage timezones by default. To enable timezone management, run the following command:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>For more information, refer to the [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) page.

If modifications have been made to the database structure, during configuration for example (creating specific indexes, creating SQL views, etc.), certain precautions should be taken when migrating. Indeed, certain modifications can be generated from incompatibilities with the migration procedure. For example, creating SQL views containing **Timestamp** fields are not compatible with the **usetimestamptz** option. We therefore advise you to follow the recommendations below:

1. Before starting the migration, back up the database.
1. Delete SQL changes.
1. Perform the postupgrade
    >[!NOTE]
    >
    >You must follow the migration steps presented in [this section](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md).
1. Reintegrate SQL changes.

In this example, a **NmcTrackingLogMessages** view had been created and this has a **Timestamp** field named **tslog**. In this case, the migration procedure fails and the following error message appears:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

To make sure the postupgrade works, you must delete the view before the migration and re-create it after the migration while adapting it to the TIMESTAMP WITH TIMEZONE mode.

### Tracking {#tracking}

The tracking formula has been modified. When migrating, the old formula (v5) is replaced by the new one (v7). If you use a personalized formula in Adobe Campaign v5, this configuration has to be adapted in Adobe Campaign v7 (**NmsTracking_ClickFormula** and **NmsTracking_OpenFormula** options).

Web tracking management has also been modified. Once migration to v7 has been carried out, you must start the deployment wizard to finish configuring the web tracking.

  ![](assets/migration_web_tracking.png)

Three modes are available:

* **Session web tracking**: If the **[!UICONTROL Leads]** package has not been installed, this option is selected by default. This option is the most ideal in terms of performance and it allows you to limit the size of the tracking logs.
* **Permanent Web tracking**
* **Anonymous Web Tracking**: If the **[!UICONTROL Leads]** package is installed, this option is selected by default. It is the most resource-consuming option. As above, the **sSourceId** column must be indexed (in the tracking table and the **CrmIncomingLead** table).

>[!NOTE]
>
>For more information on these three modes, refer to [this section](../../configuration/using/about-web-tracking.md).

### Adobe Campaign v7 tree structure {#campaign-vseven-tree-structure}

During migration, the tree structure is automatically reorganized based on the v7 standards. The new folders are added, the obsolete folders are deleted, and their content is placed in the "To move" folder. All items in this folder must be checked after the migration, and the consultant has to decide to either keep it or delete each one. Items to be kept then have to be moved to the right place.

An option has been added for disabling the automatic migration of the navigation tree. This operation is now manual. Obsolete folders are not deleted and new folders are not added. This option should only be used if the out-of-the-box v5 navigation tree has undergone too many changes. Add the option to the console, before migrating, in the **[!UICONTROL Administration > Options]** node:

* Internal name: NlMigration_KeepFolderStructure
* Data type: Integer
* Value (text): 1

If you use this option, after migration you will have to delete obsolete folders, add the new folders and run all necessary checks.

**List of new folders**:

The following folders need to be added after the migration:

| Internal name | Label | Condition |
|---|---|---|
| nmsAutoObjects | Objects created automatically | - |
| nmsCampaignAdmin | Campaign management | - |
| nmsCampaignMgt | Campaign management | - |
| nmsCampaignRes | Campaign management | - |
| nmsModels | Templates | - |
| nmsOnlineRes | Online | - |
| nmsProduction | Production | - |
| nmsProfilProcess | Processes | - |
| xtkDashboard | Dashboards | - |
| xtkPlatformAdmin | Platform | - |
| nmsLocalOrgUnit | Organizational units | - |
| nmsMRM | MRM | MRM installed |
| nmsOperations | Campaigns | Campaign installed |

**List of obsolete folders**:

The obsolete folders to be deleted after the migration are as follows:

>[!NOTE]
>
>The entire content of the obsolete folders must be checked, and for each item the consultant decides whether to keep or delete it. The items to be kept must be moved to the appropriate place.

| Internal name | Label | Condition |
|---|---|---|
| nmsAdministration | Administration | - |
| nmsDeliveryMgt | Campaign execution | - |
| ncmContent | Content management | Content Manager installed |
| ncmForm | Input form | Content Manager installed |
| ncmImage | Images | Content Manager installed |
| ncmJavascript | JavaScript codes | Content Manager installed |
| ncmJst | JavaScript templates | Content Manager installed |
| ncmParameters | Configuration | Content Manager installed |
| ncmSrcSchema | Data schemas | Content Manager installed |
| ncmStylesheet | XSL style files | Content Manager installed |
| nmsAdminPlan | Administration | Campaign installed |
| nmsResourcePlan | Resources | Campaign installed |
| nmsResourcesModels | Templates | Campaign installed |
| nmsRootPlan | Campaign management | Campaign installed |
| nmsOperator | Marketing operators | MRM installed |


## Specific configurations from v6.02 to v7{#specific-configurations-in-v6-02}

![](../../assets/v7-only.svg)

The following section details the additional configuration required when migrating from v6.02. You should also configure the settings detailed in [this page](../../migration/using/general-configurations.md).

### Web applications {#web-applications-v6}

If you are migrating from v6.02, error logs regarding overview-type web applications may appear. Error message examples:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

These web applications used SQLData and are not compatible with v7, due to heightened security. These errors will lead to a migration failure.

If you didn't use these web applications, run the following cleanup script and rerun the postupgrade:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

If you have modified these web applications and would like to continue using them in v7, you must activate the **allowSQLInjection** option in your different security zones and re-start the postupgrade. Refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section for more on this.

### Message Center {#message-center}

After a Message Center control instance migration, you must republish the transactional message templates for them to work.

In v7, the names of transactional message templates on execution instances have changed. They are currently prefixed by the operator name that corresponds to the control instance on which they are created, for example **control1_template1_rt** (where **control1** is the name of the operator). If you have a significant volume of templates, we recommend deleting old templates on control instances.

-->