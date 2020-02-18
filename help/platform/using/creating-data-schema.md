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
source-git-commit: 9a26ec7ed1c8463270ac9f97079f49e00d5b258e

---


# 데이터 스키마 만들기 {#creating-the-data-schema}

외부 데이터베이스에 스키마를 생성하려면 다음을 수행합니다.

1. 데이터 스키마 목록 위의 **[!UICONTROL New]** 단추를 클릭하고 **[!UICONTROL Access external data]**&#x200B;선택합니다.

   ![](assets/wf_new_schema_fda.png)

1. 스키마에 대한 이름과 설명을 입력하고 데이터베이스에 대한 연결을 활성화할 외부 계정을 선택합니다. 이렇게 하면 외부 베이스에서 사용할 수 있는 테이블 목록에 액세스할 수 있습니다. 수집할 데이터가 포함된 테이블을 선택합니다.

   ![](assets/wf_new_schema_select_table_fda.png)

1. 을 **[!UICONTROL OK]** 클릭하여 확인합니다. Adobe Campaign은 선택한 테이블의 구조를 자동으로 감지하고 논리 스키마를 생성합니다. Adobe Campaign은 링크를 생성하지 않습니다.

1. 만들기를 **[!UICONTROL Save]** 확인하려면 클릭합니다.

   >[!CAUTION]
   >
   >Snowflake를 사용할 경우, 주요 키는 필수입니다.

   ![](assets/wf_new_schema_generate_fda.png)

표를 매핑하면(표준 또는 FDA 매핑) 인덱스가 자동으로 생성됩니다.
