---
title: 데이터 소스 변경
description: 데이터 소스 변경 활동에 대해 자세히 알아보기
feature: Workflows, Data Management, Federated Data Access
hide: true
hidefromtoc: true
exl-id: d7bf9d62-6f9e-415f-8160-446210f6392e
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---

# 데이터 소스 변경 {#change-data-source}

>[!NOTE]
>
> **[!UICONTROL Change data source]** 활동은 **[!UICONTROL Access to external data (Federated Data Access)]** 패키지만 사용할 수 있습니다. Adobe Campaign Classic 기본 제공 패키지에 대한 자세한 내용은 이 [페이지](../../installation/using/installing-campaign-standard-packages.md)를 참조하세요.

**[!UICONTROL Change data source]** 활동을 사용하면 **[!UICONTROL Working table]** 워크플로우의 데이터 원본을 변경할 수 있습니다. 이렇게 하면 FDA, FFDA 및 로컬 데이터베이스와 같은 다양한 데이터 소스에서 데이터를 보다 유연하게 관리할 수 있습니다.

**[!UICONTROL Working table]**&#x200B;을(를) 사용하면 Adobe Campaign Classic 워크플로우에서 데이터를 처리하고 워크플로우 활동과 데이터를 공유할 수 있습니다.
기본적으로 **[!UICONTROL Working table]**&#x200B;은(는) 쿼리하는 데이터의 원본과 동일한 데이터베이스에 만들어집니다.

예를 들어 클라우드 데이터베이스에 저장된 **[!UICONTROL Profiles]** 테이블을 쿼리할 때 동일한 클라우드 데이터베이스에 **[!UICONTROL Working table]**&#x200B;을(를) 만듭니다.
이를 변경하려면 **[!UICONTROL Change Data Source]** 활동을 추가하여 **[!UICONTROL Working table]**&#x200B;의 다른 데이터 원본을 선택할 수 있습니다.

**[!UICONTROL Change Data Source]** 활동을 사용하는 경우 워크플로우 실행을 계속하려면 클라우드 데이터베이스로 다시 전환해야 합니다.

**[!UICONTROL Change Data Source]** 활동을 사용하려면:

1. 워크플로우를 만듭니다.

1. **[!UICONTROL Query]** 활동을 사용하여 타깃팅된 수신자를 쿼리합니다.

   **[!UICONTROL Query]** 활동에 대한 자세한 내용은 이 [페이지](../../workflow/using/query.md#creating-a-query)를 참조하세요.

1. **[!UICONTROL Targeting]** 탭에서 **[!UICONTROL Change data source]** 활동을 추가합니다.

   ![](assets/change-data-source.png)

1. **[!UICONTROL Change data source]** 활동을 두 번 클릭하여 **[!UICONTROL Default data source]**&#x200B;을(를) 선택합니다.

   그러면 쿼리 결과가 포함된 작업 테이블이 기본 PostgreSQL 데이터베이스로 이동됩니다.

   ![](assets/change-data-source_2.png)

1. **[!UICONTROL Actions]** 탭에서 **[!UICONTROL JavaScript code]** 활동을 끌어다 놓아 작업 테이블에서 단일 작업을 수행합니다.

   **[!UICONTROL JavaScript code]** 활동에 대한 자세한 내용은 [JavaScript 코드 및 고급 JavaScript 코드](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) 페이지를 참조하세요.

1. 클라우드 데이터베이스로 다시 전환하려면 다른 **[!UICONTROL Change data source]** 활동을 추가하십시오.

1. 활동을 두 번 클릭하고 **[!UICONTROL Active FDA external account]**&#x200B;을(를) 선택한 다음 해당 **[!UICONTROL External database]** 외부 계정을 선택합니다.

   ![](assets/change-data-source_3.png)

1. 이제 워크플로우를 시작할 수 있습니다.
