---
product: campaign
title: 게재 제어
description: 게재 제어 워크플로우 활동에 대해 자세히 알아보십시오
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%

---

# 게재 제어{#delivery-control}

**배달 컨트롤** 유형 작업을 사용하면 게재를 시작, 일시 중지 또는 중지할 수 있습니다.

이 값은 전환에 지정된 게재, 명시적으로 선택한 게재 또는 스크립트로 계산된 게재일 수 있습니다. 자세한 내용은 [배달](../../workflow/using/delivery.md)을 참조하십시오.

![](assets/edit_diffusion_act.png)

**[!UICONTROL Start]**&#x200B;을 선택하면 활동이 게재를 시작하는 데 필요한 모든 단계(대상 계산, 콘텐츠 준비, 게재)를 수행합니다. 이러한 단계 중 일부가 이전 워크플로우 활동에서 이미 수행된 경우 다시 수행하지 않습니다. 예를 들어 대상 추정이 이미 **[!UICONTROL Delivery]** 유형 활동([배달](../../workflow/using/delivery.md) 참조)에 의해 수행된 경우 **[!UICONTROL Act on the delivery]** 활동이 나머지 단계(컨텐츠 준비 및 전달)를 시작합니다.

다음 옵션을 사용할 수 있습니다.

* **[!UICONTROL Generate an outbound transition]**

   실행 종료 시 활성화되는 아웃바운드 전환을 만듭니다. 아웃바운드 게재의 대상을 검색할지 여부를 선택할 수 있습니다.

* **[!UICONTROL Processing errors]**

   [처리 오류](../../workflow/using/monitoring-workflow-execution.md#processing-errors)를 참조하십시오.

## 입력 매개 변수 {#input-parameters}

* deliveryId

배달 식별자입니다. 선택한 작업이 **[!UICONTROL Specified in the transition]**&#x200B;인 경우
