---
product: campaign
title: FDA용 데이터 스키마 만들기
description: FDA용 데이터 스키마를 만드는 방법 알아보기
feature: Installation, Instance Settings, Federated Data Access
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# 데이터 스키마 만들기 {#creating-the-data-schema}



외부 데이터베이스에 스키마를 생성하려면 다음을 수행합니다.

1. 데이터 스키마 목록 위에 있는 **[!UICONTROL New]** 단추를 클릭하고 **[!UICONTROL Access external data]**&#x200B;을(를) 선택합니다.

   ![](assets/wf_new_schema_fda.png)

1. 스키마에 대한 **[!UICONTROL Namespace]** 및 **[!UICONTROL Name]**&#x200B;을(를) 입력하고 데이터베이스에 연결할 **[!UICONTROL External account]**&#x200B;을(를) 선택하십시오. 이렇게 하면 외부 기반에서 사용할 수 있는 테이블 목록에 액세스할 수 있습니다.

   ![](assets/wf_new_schema_select_table_fda.png)

1. **[!UICONTROL Table name]** 필드에서 수집할 데이터가 포함된 테이블을 선택합니다.

   Snowflake을 사용하면 데이터베이스 사용자에게 올바른 권한이 부여된 경우 여기에서 보기를 선택할 수 있습니다. 보기를 사용할 때 Adobe Campaign에서 XML 스키마를 자동으로 생성할 수 없으므로 직접 만들어야 합니다. 보기에 대한 자세한 내용은 [Snowflake 설명서](https://docs.snowflake.com/en/user-guide/views-introduction.html)를 참조하세요.

   ![](assets/wf_new_schema_select_table_fda.png)

1. **[!UICONTROL OK]**&#x200B;을(를) 클릭하여 확인합니다. Adobe Campaign은 선택한 테이블의 구조를 자동으로 감지하고 논리 스키마를 생성합니다. Adobe Campaign은 링크를 생성하지 않습니다.

1. **[!UICONTROL Save]**&#x200B;을(를) 클릭하여 만들기를 확인합니다.

   >[!CAUTION]
   >
   >Snowflake을 사용하는 경우 기본 키는 필수입니다.

   ![](assets/wf_new_schema_generate_fda.png)

테이블을 매핑할 때(표준 또는 FDA 매핑) 인덱스가 자동으로 만들어집니다.
