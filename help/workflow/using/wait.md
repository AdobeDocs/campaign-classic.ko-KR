---
product: campaign
title: 대기
description: 대기 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# 대기{#wait}



A **대기** 활동은 몇 초에서 몇 개월 사이의 시간 지연 후 전환을 활성화합니다. 대기 작업이 다른 작업의 실행을 차단하지 않습니다. 워크플로우는 이 작업이 보류 중인 동안 작업을 동시에 실행할 수 있습니다.

아래 예와 같이 편집기를 사용하여 레이블을 입력하고 대기 시간을 입력할 수 있습니다.

![](assets/edit_wait.png)

에서 **[!UICONTROL Duration]** 필드에서 값을 선택한 단위로 표시할 수 있습니다. (연산자의 지역 설정에 따라):

* 지역 설정을 지정하지 않은 경우: **s** - 초 **m** - 분 **h** 몇 시간 동안 **d** 며칠 동안 **y** 수년 동안 승인 시 값은 자동으로 가장 읽기 쉬운 단위로 변환됩니다.

   기본 단위는 일(**d**).

* 반면에 예를 들어 지역 설정이 &#39;Français&#39;로 설정된 경우: **s** - 초 **mn** - 분 **h** 몇 시간 동안 **j** 며칠 동안 **m** 몇 달 동안 **a** 수년 동안 승인 시 위의 예와 같이 값이 자동으로 가장 읽기 쉬운 단위로 변환됩니다 **90년대** 으로 변환되었습니다. **1mn 30s**.

   기본 단위는 일(**d**).
