---
solution: Campaign Classic
product: campaign
title: 워크플로우를 사용하여 데이터 가져오기 및 내보내기
description: Campaign Classic의 워크플로우를 사용하여 데이터를 가져오고 내보내는 방법을 살펴봅니다.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 3%

---


# 워크플로우 {#import-export-workflows}을(를) 사용하여 데이터 가져오기 및 내보내기

## 데이터 수집 중 {#collecting-data-workflows}

워크플로우는 일부 가져오기 프로세스를 자동화하는 유용한 방법입니다. 로컬 파일 또는 SFTP에서 데이터를 가져오더라도 워크플로우를 사용하여 데이터 관리 절차를 표준화할 수 있습니다.

### 목록의 데이터 사용:목록 읽기 {#using-data-from-a-list--read-list}

워크플로우에서 전송된 데이터는 데이터가 미리 준비하고 구조화된 목록에서 가져올 수 있습니다.

이 목록은 Adobe Campaign에서 직접 만들거나 **[!UICONTROL Import a list]** 옵션으로 가져올 수 있습니다. 이 옵션에 대한 자세한 내용은 이 [페이지](../../platform/using/about-generic-imports-exports.md)를 참조하십시오.

워크플로우에서 목록 읽기 활동 사용에 대한 자세한 내용은 [이 페이지](../../workflow/using/read-list.md)를 참조하십시오.

### {#loading-data-from-a-file} 파일에서 데이터 로드

워크플로우에서 처리된 데이터를 구조화된 파일에서 추출하여 Adobe Campaign으로 가져올 수 있습니다.

로드 데이터 활동에 대한 설명은 [데이터 로드(파일)](../../workflow/using/data-loading--file-.md) 섹션에서 찾을 수 있습니다.

가져올 구조화된 파일의 예:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

데이터가 수집되면 워크플로우에서 사용할 수 있습니다. 예를 들어, 배달을 강화하거나 데이터베이스를 업데이트할 수 있습니다. 자세한 정보는 이 [페이지](../../workflow/using/how-to-use-workflow-data.md)를 참조하십시오.

## 데이터 내보내기 {#exporting-data-via-a-workflow}

워크플로우는 데이터를 변형하는 데 사용할 수 있는 데이터 관리 활동 중 일부를 사용한 후 내보내기 프로세스를 자동화하거나 정확한 데이터 세트를 내보내는 유용한 방법입니다.

내보내기 작업은 **[!UICONTROL Data extraction (file) activity]**&#x200B;을(를) 사용하여 수행됩니다. 활동을 구성하고 사용하는 방법에 대한 자세한 내용은 [이 페이지](../../workflow/using/extraction--file-.md)를 참조하십시오.
