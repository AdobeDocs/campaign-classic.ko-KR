---
solution: Campaign Classic
product: campaign
title: 결합
description: 조합 워크플로우 활동에 대한 자세한 내용
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---


# 결합{#union}

유니온은 단일 타겟에서 여러 인바운드 활동의 결과를 그룹화합니다. 수신한 모든 결과가 있는 대상이 생성됩니다.그러므로 조합이 실행되려면 모든 이전 활동을 마쳐야 한다.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>조합 활동 구성 및 사용에 대한 자세한 내용은 [여러 대상 결합(조합)](../../workflow/using/targeting-data.md#combining-several-targets--union-)을 참조하십시오.

## 조합 예 {#union-example}

다음 예제에서는 목록을 업데이트하기 위해 두 쿼리의 결과가 결합되었습니다. 두 쿼리는 수신자를 대상으로 합니다. 따라서 결과는 같은 표에 기반을 두고 있습니다.

1. 2개의 쿼리 바로 뒤에 **[!UICONTROL Union]** -type 활동을 삽입한 다음 목록의 업데이트 유형 활동 앞에 입력합니다.
1. 레이블을 입력할 수 있습니다.
1. 이 예에서는 쿼리에서 발생한 모집단에 일관된 데이터가 포함되므로 **[!UICONTROL Keys only]** 조정 방법을 선택합니다.
1. 쿼리에 대한 추가 데이터를 추가한 경우 공유된 데이터만 유지할지 결정할 수 있습니다.
1. 최종 모집단 크기를 제한하려면 **[!UICONTROL Limit size of generated population]** 상자를 선택합니다.

   최대 받는 사람 수를 입력하고 모집단에서 우선순위가 높은 쿼리를 선택하여 이 최종 숫자를 지정합니다.

1. 조합 활동을 승인한 다음 목록 업데이트 활동을 구성합니다([목록 업데이트](../../workflow/using/list-update.md) 참조).
1. 워크플로우를 시작합니다. 결과 수가 표시되고 목록 업데이트 활동에 정의된 목록이 생성되거나 업데이트됩니다. 이 목록에는 쿼리 모두에 대한 수신자 세트나, 해당되는 경우 이전 단계에서 정의한 번호가 포함되어 있습니다.

   ![](assets/union_example.png)

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수로 정의된 대상을 지정해야 합니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 3개의 값 집합은 결합으로 인한 대상을 식별합니다. **[!UICONTROL tableName]** 는 대상 식별자를 기록하는 테이블의 이름이며, 채우기 **[!UICONTROL schema]** 의 스키마(일반적으로 nms:recipient) **[!UICONTROL recCount]** 이며 표의 요소 수입니다.
