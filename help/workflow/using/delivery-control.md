---
title: 게재 제어
seo-title: 게재 제어
description: 게재 제어
seo-description: null
page-status-flag: never-activated
uuid: f9cef2d9-a6a5-45bd-8c7a-fabc11879628
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 0b5ee05c-4b96-425a-ab0f-60b930de21bd
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 5%

---


# 게재 제어{#delivery-control}

배달 **제어**&#x200B;유형 작업을 사용하면 배달을 시작, 일시 중지 또는 중지할 수 있습니다.

전환 시 지정된 배달, 명시적으로 선택한 배달 또는 스크립트로 계산된 배달일 수 있습니다. For more on this, refer to [Delivery](../../workflow/using/delivery.md).

![](assets/edit_diffusion_act.png)

선택하는 경우, 활동 **[!UICONTROL Start]**&#x200B;은 배달을 시작하는 데 필요한 모든 단계를 수행합니다(대상 계산, 컨텐츠 준비, 배달). 이러한 단계 중 일부가 이전 워크플로우 활동에 의해 이미 수행된 경우 다시 수행되지 않습니다. 예를 들어, 대상 추정이 이미 **[!UICONTROL Delivery]** 유형 활동( [배달 참조](../../workflow/using/delivery.md))에 의해 수행된 경우 **[!UICONTROL Act on the delivery]** 활동이 나머지 단계(컨텐츠 준비 및 배달)를 시작합니다.

다음 옵션을 사용할 수 있습니다.

* **[!UICONTROL Generate an outbound transition]**

   실행 끝에 활성화될 아웃바운드 전환을 만듭니다. 아웃바운드 게재의 대상을 검색할지 여부를 선택할 수 있습니다.

* **[!UICONTROL Processing errors]**

   처리 [오류를 참조하십시오](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## 입력 매개 변수 {#input-parameters}

* deliveryId

배달 식별자(선택한 작업이 있는 경우) **[!UICONTROL Specified in the transition]**.
