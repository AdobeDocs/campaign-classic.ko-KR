---
title: 외부 데이터베이스 액세스
seo-title: 외부 데이터베이스 액세스
description: 외부 데이터베이스 액세스
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c86af066045c1c35b51624de8565af21746354c1
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---


# 추가 옵션 {#additional-options}

<!--

## HTTP relay to a remote instance {#http-relay-to-a-remote-instance}

You can access external databases configured in remote instances using the HTTP protocol.

>[!NOTE]
>
>Not all SQL data types are supported by this feature. Blob data types are not supported at all. It is possible that other data types may not work depending on the targeted database (Timestamp on Microsoft SQL Server, for example). Please contact Adobe support for more information.

This simplifies transferring and synchronizing data between two instances. It also enables you to sidestep any tunneling between an instance and a remote database as well as the installation of the client layers to access this database. The destination instance can be a hosted instance.

>[!CAUTION]
>
>This option is only for facilitating data replication flows (ETL).   
>
>For example, it allows a cloud-hosted instance to have direct access to the data in an "on-premise" hosted database. However, it is not intended to allow targeting to be carried on an "on-premise" hosted database directly from the cloud.

To do this, you must configure the external accounts of the two instances so that the local instance can communicate with the remote instance using the HTTP protocol:

* Local instance: select the new **[!UICONTROL HTTP relay to a remote database]** connection type.

  In case of bulk load data transfer, also specify the buffer size. Select the compression option if you want to reduce the size of the transferred data.

  The **[!UICONTROL Data source]** must be defined with the following syntax: "nms:extAccount : `<internal_name_of_the_external_account>`"

  ![](assets/fda_over_http_1.png)

  >[!NOTE]
  >
  >We recommend that you use an HTTPS connection.

* Remote instance: in the FDA external account of the database accessed via the HTTP relay, check the Target of an **[!UICONTROL 'HTTP relay to a remote database' account option]**.

  ![](assets/fda_over_http_2.png)

The following example shows the new possible operating mode:

![](assets/schema_fda_over_http_2.png)

>[!CAUTION]
>
>The default database of the remote instance must be accessed via an external account as well.

This operating method avoids that the cleanup workflow of each instance deletes the work tables of the databases that use the instance as relay.

Thus, in the previous example, the cleanup workflow of the remote instance will not perform any action on the red FDA database as it is used by the local instance.

-->

## 임시 스키마를 직접 생성 {#directly-creating-temporary-schemas}

FDA 외부 데이터베이스에 대한 여러 액세스를 관리하려는 경우 새 옵션을 사용하면 외부 계정을 구성할 때 작업 스키마를 직접 만들 수 있습니다.

>[!NOTE]
>
>이 옵션은 PostgreSQL에서만 작동합니다.

![](assets/fda_work_table.png)

## 외부 데이터로 이메일 개인화 최적화 {#optimizing-email-personalization-with-external-data}

빌드 8740에서 이 옵션 **[!UICONTROL Prepare the personalization data with a workflow]** 은 이제 배달 속성의 **[!UICONTROL Analysis]** 탭에서 사용할 수 있습니다.

배달 분석 중에 이 옵션을 사용하면 FDA에 연결된 테이블의 데이터를 포함하여, 대상에 연결된 모든 데이터를 임시 테이블에 저장하는 워크플로우를 자동으로 생성하고 실행합니다.

이 옵션을 선택하면 개인화 실행을 위한 성능이 크게 향상될 수 있습니다.

## 워크플로우에서 외부 데이터베이스의 데이터 사용 {#using-data-from-an-external-database-in-a-workflow}

여러 Adobe Campaign 워크플로우 활동에서 외부 데이터베이스에 저장된 데이터를 사용할 수 있습니다.

### 외부 데이터 필터링 {#filtering-on-external-data}

쿼리 활동을 통해 외부 데이터를 추가하고 정의된 필터 구성에서 사용할 수 있습니다.

For more on this, refer to the [Query](../../workflow/using/targeting-data.md#selecting-data) section.

### 하위 세트 만들기 {#creating-sub-sets}

분할 활동을 통해 하위 세트를 만들 수 있습니다. 외부 데이터를 사용하여 사용할 필터링 기준을 정의할 수 있습니다.

For more on this, refer to the [Split](../../workflow/using/split.md) section.

### 외부 데이터베이스 로드 중 {#loading-external-database}

데이터 로드(RDBMS)에서 외부 데이터를 사용할 수 있습니다. 이 활동은 [데이터 로드](../../workflow/using/data-loading--rdbms-.md) 섹션에 표시됩니다.

### 정보 및 링크 추가 {#adding-information-and-links}

데이터 연계 강화 기능을 사용하면 워크플로우의 작업 테이블에 데이터를 추가할 수 있을 뿐만 아니라 외부 테이블에 대한 링크를 추가할 수 있습니다. 따라서 외부 데이터베이스의 데이터를 활용할 수 있습니다. 이 활동은 [데이터 연계 강화](../../workflow/using/enrichment.md) 섹션에 제공됩니다.
<!--

## Cloud Messaging - FDA synchronization {#cloud-messaging---fda-synchronization}

When the Cloud Messaging server and the Marketing server have not been synchronized for a long period, the volume of missing broadlogs on the Marketing server can be significant. To optimize broadlog synchronization via the FDA, the **NmsMidSourcing_LogsPeriodHour** option has been added. This allows a maximum period (expressed in hours) to be specified as to limit the number of broadlogs recovered every time the synchronization workflow is executed.

The option is to be added in the console, in the **[!UICONTROL Administration > Options]** node.

>[!CAUTION]
>
>This option must **only** be used for synchronizing a significant volume of broadlogs via the FDA.

>[!NOTE]
>
>The option is only taken into account if a last recovery date exists (**NmsMidSourcing_LastBroadLog_&#42;** option).

## Message Center - Read access on the XtkFolder table {#message-center---read-access-on-the-xtkfolder-table}

From build 8141 and above, manual action is necessary if Message Center uses the FDA as an archiving mode.

You need to grant read access on the XtKFolder table to the user linked with the external FDA account.

For a PostgreSQL database for example, the command is as follows:

```
GRANT SELECT ON XtkFolder TO DBUSER;
```

This user must have read access to the following tables:

* NmsBroadLogRtEvent
* NmsBroadLogBatchEvent
* NmsTrackingLogRtEvent
* NmsTrackingLogBatchEvent
* NmsRtEvent
* NmsBatchEvent
* NmsBroadLogMsg
* NmsTrackingUrl
* NmsDelivery
* NmsWebTrackingLog

>[!NOTE]
>
>This modification deletes the "Permission denied for relation xtkfolder" error message.

If the working schema selected in the external FDA account is not the out-of-the-box Neolane account, then this modification to the access rights is not necessary.

-->

