---
solution: Campaign Classic
product: campaign
title: 외부 데이터베이스 액세스
description: 외부 데이터베이스 액세스
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 3%

---


# 데이터 스키마 만들기 {#creating-the-data-schema}

외부 데이터베이스에 스키마를 생성하려면

1. 데이터 스키마 목록 **[!UICONTROL New]** 위의 단추를 클릭하고 선택합니다 **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. 스키마에 대한 이름 및 설명을 입력하고 데이터베이스에 연결할 외부 계정을 선택합니다. 이렇게 하면 외부 베이스에서 사용할 수 있는 테이블 목록에 액세스할 수 있습니다. 수집할 데이터가 포함된 테이블을 선택합니다.

   ![](assets/wf_new_schema_select_table_fda.png)

1. 을 **[!UICONTROL OK]** 클릭하여 확인합니다. Adobe Campaign은 선택한 테이블의 구조를 자동으로 감지하고 논리 스키마를 생성합니다. Adobe Campaign은 링크를 생성하지 않습니다.

1. 만들기를 **[!UICONTROL Save]** 확인하려면 클릭합니다.

   >[!CAUTION]
   >
   >Snowflake을 사용하는 경우 기본 키는 필수입니다.

   ![](assets/wf_new_schema_generate_fda.png)

테이블을 매핑하면(표준 또는 FDA 매핑) 인덱스가 자동으로 생성됩니다.
