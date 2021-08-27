---
product: campaign
title: 외부 데이터베이스 액세스
description: 외부 데이터베이스 액세스
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 9%

---

# 데이터 스키마 만들기 {#creating-the-data-schema}

![](../../assets/v7-only.svg)

외부 데이터베이스에 스키마를 생성하려면 다음을 수행합니다.

1. 데이터 스키마 목록 위에 있는 **[!UICONTROL New]** 단추를 클릭하고 **[!UICONTROL Access external data]** 을 선택합니다.

   ![](assets/wf_new_schema_fda.png)

1. 스키마에 대한 이름과 설명을 입력하고 데이터베이스에 연결할 외부 계정을 선택합니다. 이렇게 하면 외부 베이스에서 사용할 수 있는 테이블 목록에 액세스할 수 있습니다. 수집할 데이터가 포함된 테이블을 선택합니다.

   ![](assets/wf_new_schema_select_table_fda.png)

1. **[!UICONTROL OK]** 을 클릭하여 확인합니다. Adobe Campaign은 선택한 테이블의 구조를 자동으로 감지하고 논리 스키마를 생성합니다. Adobe Campaign은 링크를 생성하지 않습니다.

1. **[!UICONTROL Save]** 을 클릭하여 만들기를 확인합니다.

   >[!CAUTION]
   >
   >Snowflake을 사용할 경우 기본 키는 필수입니다.

   ![](assets/wf_new_schema_generate_fda.png)

테이블을 매핑(표준 또는 FDA 매핑)할 때 인덱스가 자동으로 만들어집니다.
