---
solution: Campaign Classic
product: campaign
title: 게재 제어
description: 전달 제어 워크플로우 활동에 대한 자세한 내용
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%

---


# 게재 제어{#delivery-control}

**배달 컨트롤** 유형 작업을 사용하면 배달을 시작, 일시 중지 또는 중지할 수 있습니다.

변환에 지정된 배달, 명시적으로 선택한 배달 또는 스크립트로 계산된 배달일 수 있습니다. 자세한 내용은 [배달](../../workflow/using/delivery.md)을 참조하십시오.

![](assets/edit_diffusion_act.png)

**[!UICONTROL Start]**&#x200B;을 선택하면 활동이 배달을 시작하는 데 필요한 모든 단계를 수행합니다(대상 계산, 컨텐츠 준비, 배달). 이러한 단계 중 일부가 이전 워크플로우 활동에 의해 이미 수행된 경우 다시 수행되지 않습니다. 예를 들어 대상 추정이 이미 **[!UICONTROL Delivery]** 유형 활동([배달](../../workflow/using/delivery.md) 참조)에 의해 수행된 경우, **[!UICONTROL Act on the delivery]** 활동은 나머지 단계(컨텐츠 준비 및 전달)를 시작합니다.

다음 옵션을 사용할 수 있습니다.

* **[!UICONTROL Generate an outbound transition]**

   실행이 끝날 때 활성화될 아웃바운드 전환을 만듭니다. 아웃바운드 게재의 대상을 검색할지 여부를 선택할 수 있습니다.

* **[!UICONTROL Processing errors]**

   [처리 오류](../../workflow/using/monitoring-workflow-execution.md#processing-errors)를 참조하십시오.

## 입력 매개 변수 {#input-parameters}

* deliveryId

배달 식별자(선택한 작업이 **[!UICONTROL Specified in the transition]**&#x200B;인 경우).
