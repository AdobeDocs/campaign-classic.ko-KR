---
product: campaign
title: 집계 업데이트
description: 업데이트 집계 워크플로우 활동에 대해 자세히 알아보십시오
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 4%

---

# 집계 업데이트{#update-aggregate}

![](../../assets/common.svg)

집계는 보고를 위해 큐브 수준에서 정의됩니다. 합계를 구성할 때 **[!UICONTROL Workflow]** 탭을 사용할 수 있습니다.

큐브와 Adobe Campaign에서 합계를 사용하는 방법에 대한 자세한 내용은 전용 [섹션](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates)을 참조하십시오.

**[!UICONTROL Update aggregate]** 활동을 사용하면 적용할 업데이트 모드를 선택할 수 있습니다. 전체 또는 일부.

기본적으로 각 계산 중에 전체 업데이트가 수행됩니다. 부분 업데이트를 활성화하려면 관련 옵션을 선택하고 업데이트 조건을 정의합니다.

![](assets/s_advuser_cube_agregate_05.png)

**우수 사례**: 활동 **[!UICONTROL Scheduler]** 을 사용하여 계산 업데이트 빈도를 지정할 수 있습니다.

![](assets/s_advuser_cube_agregate_04.png)
