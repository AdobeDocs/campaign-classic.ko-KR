---
product: campaign
title: 데이터베이스 구조 업데이트
description: 데이터베이스 구조 업데이트
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 8%

---

# 데이터베이스 구조 업데이트{#updating-the-database-structure}

![](../../assets/v7-only.svg)

스키마에 대한 수정 사항을 적용하려면 데이터베이스 업데이트 마법사를 시작합니다. 을 통해 이 마법사에 액세스할 수 있습니다. **[!UICONTROL Tools > Advanced > Update database structure]** . 데이터베이스의 물리적 구조가 논리적 설명과 일치하는지 확인하고 SQL 업데이트 스크립트를 실행합니다.

![](assets/d_ncs_integration_schema_update.png)

데이터베이스의 모듈은 자동으로 채워지고 활성화됩니다.

![](assets/d_ncs_integration_schema_update_select.png)

다음 **[!UICONTROL Add stored procedures]** 및 **[!UICONTROL Import initialization data]** 옵션을 사용하여 초기 SQL 스크립트 및 데이터베이스를 만들 때 실행되는 데이터 패키지를 시작합니다.

외부 데이터 패키지에서 데이터 세트를 가져올 수 있습니다. 이렇게 하려면 을(를) 선택합니다. **[!UICONTROL Import a package]** 패키지의 XML 파일을 입력합니다.

다음 단계에 따라 데이터베이스 업데이트 SQL 스크립트를 봅니다.

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>이는 편집 필드에 있으며 SQL 코드를 삭제하거나 추가하기 위해 수정할 수 있습니다.

그런 다음 데이터베이스 업데이트를 시작합니다.

![](assets/d_ncs_integration_schema_update3.png)
