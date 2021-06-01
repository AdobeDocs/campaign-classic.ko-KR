---
product: campaign
title: 포크
description: 포크 워크플로우 활동에 대해 자세히 알아보십시오
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 1%

---

# 포크{#fork}

**[!UICONTROL Fork]** 활동을 사용하면 동일한 워크플로우 내에서 독립적으로 여러 활동을 수행할 수 있도록 여러 아웃바운드 전환을 만들 수 있습니다.

예를 들어 쿼리 뒤에 활동을 사용하여 두 작업을 동시에 수행할 수 있습니다.

* 쿼리 결과를 대상에 저장합니다.
* 여러 게재를 보내려면 결과에 대해 세분화를 실행합니다.

컨텐츠 작성 및 게재 전송 자동화의 컨텍스트에서 활동을 사용하여 타겟 계산 및 컨텐츠 생성을 동시에 시작할 수도 있습니다. 전용 사용 사례는 [이 섹션](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)에서 사용할 수 있습니다.

>[!IMPORTANT]
>
>**[!UICONTROL Fork]** 활동 **이(가) 동시에 실행되지 않는 아웃바운드 전환은** 이 동작은 워크플로우의 성능에 영향을 줄 수 있습니다. 여러 활동을 독립적으로 실행해야 하는 경우 이 활동을 사용하여 나머지 워크플로우를 실행하기 전에 나중에 함께 결합합니다.

**[!UICONTROL Fork]** 활동을 구성하려면 아웃바운드 전환의 번호와 레이블을 정의합니다.

![](assets/s_user_segmentation_fork.png)

그런 다음 각 아웃바운드 전환을 구성한 다음 필요한 경우 [AND-join](../../workflow/using/and-join.md) 활동을 사용하여 두 전환을 함께 조인할 수 있습니다. 이렇게 하면 나머지 워크플로우는 **[!UICONTROL Fork]** 활동의 아웃바운드 전환이 완료된 다음에만 실행됩니다.
