---
title: 결합
description: 조합 워크플로우 활동에 대한 자세한 내용
page-status-flag: never-activated
uuid: 987e106e-c414-4db4-a93e-96e43dc04370
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 573021ad-1efb-4156-af6d-417737ce745a
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---


# 결합{#union}

하나의 대상에 여러 인바운드 활동의 결과를 그룹화합니다. 수신한 모든 결과가 있는 대상이 생성됩니다.그러므로 모든 이전 활동은 반드시 시행되어야 한다.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>조합 활동 구성 및 사용에 대한 자세한 내용은 여러 대상 [결합(결합)을 참조하십시오](../../workflow/using/targeting-data.md#combining-several-targets--union-).

## 조합 예제 {#union-example}

다음 예에서는 목록을 업데이트하기 위해 두 쿼리의 결과가 결합되었습니다. 이 두 쿼리는 수신자를 대상으로 합니다. 따라서 결과는 같은 표에 기반을 두고 있습니다.

1. 두 개의 쿼리 바로 뒤에 - **[!UICONTROL Union]** type 활동을 삽입하고 목록의 업데이트 유형 활동 전에 이를 엽니다.
1. 레이블을 입력할 수 있습니다.
1. 이 예에서는 쿼리의 결과로 생성된 모집단 **[!UICONTROL Keys only]** 에 일관된 데이터가 포함되기 때문에 조정 방법을 선택합니다.
1. 쿼리에 대한 추가 데이터를 추가한 경우 공유되는 데이터만 유지하도록 결정할 수 있습니다.
1. If you wish to limit the size of the final population, check the **[!UICONTROL Limit size of generated population]** box.

   최대 받는 사람 수를 입력하고 모집단에서 우선순위가 높은 쿼리를 선택하여 이 최종 숫자를 지정합니다.

1. 조합 활동을 승인한 다음 목록 업데이트 활동을 구성합니다(목록 업데이트 [참조](../../workflow/using/list-update.md)).
1. 워크플로우를 시작합니다. 결과 수가 표시되고 목록 업데이트 활동에 정의된 목록이 생성되거나 업데이트됩니다. 이 목록에는 쿼리 모두에 대한 수신자 세트나, 해당되는 경우 이전 단계에서 정의된 숫자가 포함되어 있습니다.

   ![](assets/union_example.png)

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수로 정의된 대상을 지정해야 합니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 집합은 결합으로 인한 대상을 식별합니다. **[!UICONTROL tableName]** 는 대상 식별자를 기록하는 테이블 이름 **[!UICONTROL schema]** 으로, 모집단(일반적으로 nms:recipient)의 스키마이며 표의 요소 **[!UICONTROL recCount]** 수입니다.
