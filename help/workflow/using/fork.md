---
solution: Campaign Classic
product: campaign
title: 포크
description: 포크 워크플로우 활동에 대한 자세한 내용
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 3eecc16442a11849c12819cf83392f60c5b82a13
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# 포크{#fork}

**[!UICONTROL Fork]** 활동을 사용하면 동일한 워크플로우 내에서 여러 활동을 독립적으로 수행하기 위해 여러 개의 아웃바운드 전환을 만들 수 있습니다.

예를 들어 쿼리 다음에 활동을 사용하여 두 개의 작업을 동시에 수행할 수 있습니다.

* 쿼리 결과를 대상에 저장,
* 여러 배달을 전송하려면 결과에 따라 세그먼테이션을 실행합니다.

대상 계산 및 컨텐츠 생성을 동시에 실행하기 위해 컨텐츠 생성 및 전달 전송 자동화의 컨텍스트에서 활동을 사용할 수도 있습니다. 전용 사용 사례는 [이 섹션](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)에서 사용할 수 있습니다.

>[!WARNING]
>
>포크 활동 후에 추가된 아웃바운드 전환은 동시에 실행되지 않습니다.
>
>따라서 워크플로우의 성능을 향상시키기 위해 활동을 사용하지 말고, 여러 활동을 독립적으로 실행하고 나머지 워크플로우를 실행하기 전에 나중에 함께 참여하려면 합니다.

활동을 구성하려면 활동을 연 다음 원하는 아웃바운드 전환의 번호와 레이블을 정의합니다.

![](assets/s_user_segmentation_fork.png)

그런 다음 각 아웃바운드 전환을 구성한 다음 필요한 경우 [AND-join](../../workflow/using/and-join.md) 활동을 사용하여 두 전환을 함께 연결할 수 있습니다. 이렇게 하면 나머지 워크플로우는 **[!UICONTROL Fork]** 활동의 아웃바운드 전환이 완료된 후에만 실행됩니다.
