---
title: 결합
seo-title: 결합
description: 결합
seo-description: null
page-status-flag: never-activated
uuid: 987e106e-c414-4db4-a93e-96e43dc04370
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 573021ad-1efb-4156-af6d-417737ce745a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 결합{#union}

합집합은 단일 타겟에서 여러 인바운드 활동의 결과를 그룹화합니다. 수신한 모든 결과가 있는 대상이 생성됩니다.그러므로 모든 이전 활동은 노조가 시행되도록 완성되어야 한다.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>조합 활동 구성 및 사용에 대한 자세한 내용은 여러 대상 [결합(조합)을](../../workflow/using/targeting-data.md#combining-several-targets--union-)참조하십시오.

## 조합 예 {#union-example}

다음 예에서는 목록을 업데이트하기 위해 두 쿼리의 결과가 결합되었습니다. 두 쿼리는 수신자를 대상으로 합니다. 따라서 결과는 같은 표를 기반으로 합니다.

1. 두 개의 쿼리 바로 뒤에 **[!UICONTROL Union]** -type 활동을 삽입하고 목록의 업데이트 유형 활동 앞에 추가한 다음 엽니다.
1. 레이블을 입력할 수 있습니다.
1. 이 예에서는 쿼리의 결과 모집단(consistent data)이 포함되어 있으므로 조정 방법을 선택합니다. **[!UICONTROL Keys only]**
1. 쿼리에 대한 추가 데이터를 추가한 경우 공유된 데이터만 유지하도록 결정할 수 있습니다.
1. 최종 모집단 크기를 제한하려면 **[!UICONTROL Limit size of generated population]** 상자를 선택합니다.

   최대 받는 사람 수를 입력하고 모집단 우선순위가 높은 쿼리를 선택하여 이 최종 숫자를 지정합니다.

1. 조합 활동을 승인한 다음 목록 업데이트 활동을 구성합니다(목록 [업데이트](../../workflow/using/list-update.md)참조).
1. 워크플로우를 시작합니다. 결과 수가 표시되고 목록 업데이트 활동에 정의된 목록이 작성되거나 업데이트됩니다. 이 목록에는 쿼리 모두에 대한 수신자 집합 또는 해당되는 경우 이전 단계에서 정의한 번호가 포함되어 있습니다.

   ![](assets/union_example.png)

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수에 의해 정의된 대상을 지정해야 합니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 개의 값 집합은 결합으로 인한 대상을 식별합니다. **[!UICONTROL tableName]** 는 대상 식별자를 기록하는 테이블의 이름이며 **[!UICONTROL schema]** 모집단(일반적으로 nms:recipient)의 스키마이며 **[!UICONTROL recCount]** 표의 요소 수입니다.
