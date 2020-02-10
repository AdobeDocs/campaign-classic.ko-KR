---
title: 데이터 로드(RDBMS)
seo-title: 데이터 로드(RDBMS)
description: 데이터 로드(RDBMS)
seo-description: null
page-status-flag: never-activated
uuid: d5ec30f2-398a-4b16-9232-924437da146a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: a128caac-5740-4dac-b14d-1d2fcef3cc69
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 데이터 로드(RDBMS){#data-loading-rdbms}

이 **[!UICONTROL Data loading (RDBMS)]** 활동을 사용하면 이 외부 데이터베이스에 직접 액세스하고 타깃팅에 필요한 데이터만 수집할 수 있습니다.

성능 향상을 위해 쿼리 활동(외부 데이터베이스의 데이터를 사용할 수 있는 경우)을 사용하는 것이 좋습니다. 자세한 내용은 외부 데이터베이스 [액세스(FDA)를](../../workflow/using/accessing-an-external-database--fda-.md)참조하십시오.

작업은 다음과 같습니다.

1. 목록에서 데이터 소스를 선택하고 추출할 데이터가 포함된 테이블의 이름을 입력합니다.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   해당 필드에 입력한 테이블의 이름은 외부 데이터베이스에서 데이터를 수집하는 템플릿으로 사용됩니다. 워크플로우에 의해 처리된 테이블의 이름은 데이터 로드 활동의 인바운드 전환으로 계산하거나 전달할 수 있습니다. 사용할 테이블을 선택하려면 을 클릭합니다 **[!UICONTROL Advanced..]**. 링크를 클릭하고 **[!UICONTROL Specified in the transition]** 또는 **[!UICONTROL Explicit]** 옵션을 선택합니다.

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. 링크를 클릭하여 데이터베이스에 수집할 데이터를 선택합니다. **[!UICONTROL Select the columns to extract...]**

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. 이 데이터에 대한 필터를 정의할 수 있습니다. 이렇게 하려면 **[!UICONTROL Edit query....]** 링크를 클릭합니다.

   이와 같이 수집된 데이터는 워크플로우의 라이프 사이클 동안 사용할 수 있습니다.

