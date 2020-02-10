---
title: 데이터베이스 구조 업데이트
seo-title: 데이터베이스 구조 업데이트
description: 데이터베이스 구조 업데이트
seo-description: null
page-status-flag: never-activated
uuid: 084dcc7b-f890-4dff-a322-c9a8f1d614b8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: b82ae459-30b5-4a1c-91cc-5c7b8f128333
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 데이터베이스 구조 업데이트{#updating-the-database-structure}

스키마를 수정하려면 데이터베이스 업데이트 마법사를 시작합니다. 이 마법사는 을 통해 액세스할 수 **[!UICONTROL Tools > Advanced > Update database structure]** 있습니다. 데이터베이스의 물리적 구조가 논리적 설명과 일치하는지 확인하고 SQL 업데이트 스크립트를 실행합니다.

![](assets/d_ncs_integration_schema_update.png)

데이터베이스의 모듈은 자동으로 채워지고 활성화됩니다.

![](assets/d_ncs_integration_schema_update_select.png)

및 **[!UICONTROL Add stored procedures]** **[!UICONTROL Import initialization data]** 옵션은 초기 SQL 스크립트 및 데이터베이스를 만들 때 실행되는 데이터 패키지를 실행하는 데 사용됩니다.

외부 데이터 패키지에서 데이터 세트를 가져올 수 있습니다. 이렇게 하려면 패키지의 XML 파일을 선택하고 **[!UICONTROL Import a package]** 입력합니다.

다음 단계에 따라 데이터베이스 업데이트 SQL 스크립트를 봅니다.

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>편집 필드에 있으며 SQL 코드를 삭제하거나 추가하기 위해 수정할 수 있습니다.

그런 다음 데이터베이스 업데이트를 시작합니다.

![](assets/d_ncs_integration_schema_update3.png)

