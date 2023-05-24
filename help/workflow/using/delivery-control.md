---
product: campaign
title: 게재 제어
description: 게재 제어 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%

---

# 게재 제어{#delivery-control}



A **게재 제어**-type 작업을 사용하여 게재를 시작, 일시 중지 또는 중지할 수 있습니다.

전환에 지정된 게재, 명시적으로 선택한 게재 또는 스크립트로 계산된 게재가 될 수 있습니다. 자세한 내용은 다음을 참조하십시오. [게재](delivery.md).

![](assets/edit_diffusion_act.png)

다음을 선택하는 경우 **[!UICONTROL Start]**, 활동은 게재를 시작하는 데 필요한 모든 단계(대상 계산, 콘텐츠 준비, 게재)를 수행합니다. 이전 워크플로우 활동에서 이러한 단계 중 일부를 이미 수행한 경우에는 다시 수행되지 않습니다. 예를 들어 대상 추정이 이미 다음에 의해 수행된 경우: **[!UICONTROL Delivery]** 유형 활동( 참조) [게재](delivery.md)), **[!UICONTROL Act on the delivery]** 활동은 나머지 단계(콘텐츠 준비 및 게재)를 시작합니다.

다음 옵션을 사용할 수 있습니다.

* **[!UICONTROL Generate an outbound transition]**

   실행 종료 시 활성화될 아웃바운드 전환을 만듭니다. 아웃바운드 게재의 타겟을 검색할지 여부를 선택할 수 있습니다.

* **[!UICONTROL Processing errors]**

   을(를) 참조하십시오 [처리 오류](monitoring-workflow-execution.md#processing-errors).

## 입력 매개 변수 {#input-parameters}

* deliveryId

게재 식별자(선택한 작업이 **[!UICONTROL Specified in the transition]**.
