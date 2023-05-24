---
product: campaign
title: 집계 업데이트
description: 업데이트 집계 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 3%

---

# 집계 업데이트{#update-aggregate}



집계는 보고 목적으로 큐브 수준에서 정의됩니다. A **[!UICONTROL Workflow]** 합계를 구성할 때 탭을 사용할 수 있습니다.

집계는 대량의 데이터를 조작할 때 유용합니다. 전용 워크플로우 상자에 정의된 설정을 기반으로 가장 최근에 수집한 데이터를 지표에 통합하기 위해 자동으로 업데이트됩니다

합계는 각 큐브의 관련 탭에 정의됩니다.

![](assets/s_advuser_cube_agregate_01.png)


다음 **[!UICONTROL Update aggregate]** 활동을 사용하면 적용할 업데이트 모드(전체 또는 일부)를 선택할 수 있습니다.

기본적으로 각 계산 중에 전체 업데이트가 수행됩니다. 부분 업데이트를 활성화하려면 관련 옵션을 선택하고 업데이트 조건을 정의합니다.

![](assets/s_advuser_cube_agregate_05.png)

**모범 사례**: a **[!UICONTROL Scheduler]** 활동을 사용하여 계산 업데이트 빈도를 지정할 수 있습니다.

![](assets/s_advuser_cube_agregate_04.png)
