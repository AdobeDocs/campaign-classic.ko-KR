---
product: campaign
title: 워크플로우를 사용하여 데이터 가져오기 및 내보내기
description: Campaign에서 워크플로우를 사용하여 데이터를 가져오고 내보내는 방법 알아보기
feature: Data Management, Workflows
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 266ecd49-7101-4ff1-941f-1f9b39b44955
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 5%

---

# 워크플로우를 사용하여 데이터 가져오기 및 내보내기 {#import-export-workflows}



## 데이터 수집 {#collecting-data-workflows}

워크플로우는 일부 가져오기 프로세스를 자동화하는 유용한 방법이 될 수 있습니다. 로컬 파일에서 데이터를 가져오든 SFTP에서 데이터를 가져오든 간에 워크플로우를 사용하여 데이터 관리 절차를 표준화할 수 있습니다.

### 목록의 데이터 사용: 목록 읽기 {#using-data-from-a-list--read-list}

워크플로우에서 전송된 데이터는 미리 데이터를 준비하고 구조화한 목록에서 가져올 수 있습니다.

이 목록은 Adobe Campaign에서 직접 만들었거나 **[!UICONTROL Import a list]** 옵션을 선택합니다. 이 옵션에 대한 자세한 내용은 다음을 참조하십시오. [페이지](../../platform/using/about-generic-imports-exports.md).

워크플로우에서 목록 읽기 활동 사용에 대한 자세한 내용은 을 참조하십시오. [이 페이지](../../workflow/using/read-list.md).

### 파일에서 데이터 로드 {#loading-data-from-a-file}

워크플로우에서 처리된 데이터는 Adobe Campaign으로 가져올 수 있도록 구조화된 파일에서 추출할 수 있습니다.

데이터 로드 활동에 대한 설명은 [데이터 로드 중(파일)](../../workflow/using/data-loading--file-.md) 섹션.

가져올 구조화된 파일의 예:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

데이터가 수집되면 워크플로우에서 사용할 수 있습니다. 예를 들어 게재를 보강하거나 데이터베이스를 업데이트할 수 있습니다. 자세한 정보는 이 [페이지](../../workflow/using/how-to-use-workflow-data.md)를 참조하십시오.

## 데이터 내보내기 {#exporting-data-via-a-workflow}

워크플로우는 일부 내보내기 프로세스를 자동화하거나 데이터를 변형하는 데 사용할 수 있는 일부 데이터 관리 활동을 사용한 후 정확한 데이터 세트를 내보내는 유용한 방법이 될 수 있습니다.

내보내기 작업은 **[!UICONTROL Data extraction (file) activity]**. 활동을 구성하고 사용하는 방법에 대한 자세한 내용은 을 참조하십시오. [이 페이지](../../workflow/using/extraction--file-.md).
