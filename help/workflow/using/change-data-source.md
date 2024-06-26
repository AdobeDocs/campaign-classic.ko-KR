---
title: 데이터 소스 변경
description: 데이터 소스 변경 활동에 대해 자세히 알아보기
feature: Workflows, Data Management, Federated Data Access
exl-id: d7bf9d62-6f9e-415f-8160-446210f6392e
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---

# 데이터 소스 변경 {#change-data-source}

>[!NOTE]
>
> 다음 **[!UICONTROL Change data source]** 활동은 다음에서만 사용할 수 있습니다. **[!UICONTROL Access to external data (Federated Data Access)]** 패키지. Adobe Campaign Classic 기본 제공 패키지에 대한 자세한 내용은 다음을 참조하십시오. [페이지](../../installation/using/installing-campaign-standard-packages.md).

다음 **[!UICONTROL Change data source]** 활동을 사용하면 워크플로우의 데이터 소스를 변경할 수 있습니다 **[!UICONTROL Working table]**. 이렇게 하면 FDA, FFDA 및 로컬 데이터베이스와 같은 다양한 데이터 소스에서 데이터를 보다 유연하게 관리할 수 있습니다.

다음 **[!UICONTROL Working table]** Adobe Campaign Classic 워크플로우에서 데이터를 처리하고 워크플로우 활동과 데이터를 공유할 수 있습니다.
기본적으로 **[!UICONTROL Working table]** 는 쿼리하는 데이터의 소스와 동일한 데이터베이스에 생성됩니다.

예를 들어 **[!UICONTROL Profiles]** 클라우드 데이터베이스에 저장된 테이블에는 **[!UICONTROL Working table]** 동일한 클라우드 데이터베이스에서.
이를 변경하려면 다음을 추가할 수 있습니다. **[!UICONTROL Change Data Source]** 활동에 대해 다른 데이터 소스 선택 **[!UICONTROL Working table]**.

를 사용할 때는 **[!UICONTROL Change Data Source]** 활동을 계속하려면 클라우드 데이터베이스로 다시 전환해야 합니다.

을(를) 사용하려면 **[!UICONTROL Change Data Source]** 활동:

1. 워크플로우를 만듭니다.

1. 을(를) 사용하여 타겟팅된 수신자 쿼리 **[!UICONTROL Query]** 활동.

   에 대한 자세한 내용은 **[!UICONTROL Query]** 활동. 다음을 참조하십시오. [페이지](../../workflow/using/query.md#creating-a-query).

1. 다음에서 **[!UICONTROL Targeting]** 탭, 추가 **[!UICONTROL Change data source]** 활동.

   ![](assets/change-data-source.png)

1. 을(를) 두 번 클릭합니다. **[!UICONTROL Change data source]** 선택할 활동 **[!UICONTROL Default data source]**.

   그러면 쿼리 결과가 포함된 작업 테이블이 기본 PostgreSQL 데이터베이스로 이동됩니다.

   ![](assets/change-data-source_2.png)

1. 다음에서 **[!UICONTROL Actions]** 탭, 드래그 앤 드롭 **[!UICONTROL JavaScript code]** 작업 테이블에서 단일 작업을 수행하는 활동.

   에 대한 자세한 내용은 **[!UICONTROL JavaScript code]** 활동( )은 [JavaScript 코드 및 고급 JavaScript 코드](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) 페이지를 가리키도록 업데이트하는 중입니다.

1. 다른 항목 추가 **[!UICONTROL Change data source]** 활동을 클라우드 데이터베이스로 다시 전환합니다.

1. 활동을 두 번 클릭하고 다음을 선택합니다. **[!UICONTROL Active FDA external account]** 그런 다음 해당 **[!UICONTROL External database]** 외부 계정입니다.

   ![](assets/change-data-source_3.png)

1. 이제 워크플로우를 시작할 수 있습니다.
