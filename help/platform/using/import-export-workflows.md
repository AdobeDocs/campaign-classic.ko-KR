---
product: campaign
title: 워크플로우를 사용하여 데이터 가져오기 및 내보내기
description: Campaign에서 워크플로우를 사용하여 데이터를 가져오고 내보내는 방법 알아보기
feature: Data Management, Workflows
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 266ecd49-7101-4ff1-941f-1f9b39b44955
source-git-commit: 4fb262c616276f785f97b42bec22c150afc6e5c8
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# 워크플로우를 사용하여 데이터 가져오기 및 내보내기 {#import-export-workflows}



## 데이터 수집 {#collecting-data-workflows}

워크플로우는 일부 가져오기 프로세스를 자동화하는 유용한 방법이 될 수 있습니다. 로컬 파일에서 데이터를 가져오든 SFTP에서 데이터를 가져오든 간에 워크플로우를 사용하여 데이터 관리 절차를 표준화할 수 있습니다.

>[!NOTE]
>
>워크플로우를 사용하여 데이터를 가져오고 내보내는 방법에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/audience/add-profiles/import-profiles){target=_blank}를 참조하세요.


<!--
### Use data from a list: Read list {#using-data-from-a-list--read-list}

The data sent in a workflow can come from lists whereby the data has been prepared and structured beforehand.

This list may have been directly created in Adobe Campaign or imported by the **[!UICONTROL Import a list]** option. For more on this option, refer to this [page](../../platform/using/about-generic-imports-exports.md).

For more on using the read list activity in a workflow, refer to [this page](../../workflow/using/read-list.md).

### Load data from a file {#loading-data-from-a-file}

The data processed in a workflow can be extracted from a structured file so that it can be imported into Adobe Campaign.

A description of the loading data activity can be found in the [Data loading (file)](../../workflow/using/data-loading-file.md) section.

Example of structured file to import:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

Once data has been collected you can use it in your workflows, for example to enrich a delivery or update the database. For more on this, refer to [this page](../../workflow/using/how-to-use-workflow-data.md).

## Export data {#exporting-data-via-a-workflow}

Workflows can be a useful way to automate some of your export processes or to export precise sets of data after using some of the available data management activities available to transform your data.

Export operations are performed using a **[!UICONTROL Data extraction (file) activity]**. For more on how to configure and use the activity, refer to [this page](../../workflow/using/extraction-file.md).
-->