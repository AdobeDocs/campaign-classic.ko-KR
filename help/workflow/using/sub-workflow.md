---
product: campaign
title: 하위 워크플로
description: 하위 워크플로우 활동에 대해 자세히 알아보기
feature: Workflows
exl-id: bc64ca11-2c50-4896-b6c6-ae42c0315924
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 1%

---

# 하위 워크플로{#sub-workflow}



**[!UICONTROL Sub-workflow]** 활동을 사용하면 다른 워크플로우 실행을 트리거하고 결과를 복구할 수 있습니다. 이 활동을 사용하면 간소화된 인터페이스를 사용하면서도 복잡한 워크플로우를 사용할 수 있습니다.

단일 워크플로우에서 여러 하위 워크플로우를 호출할 수 있습니다. 하위 워크플로우는 동기적으로 실행됩니다.

아래 예에서 기본 워크플로우는 점프를 사용하여 하위 워크플로를 호출하는 것입니다. 점프 형식 그래픽 개체에 대한 자세한 내용은 [이 섹션](jump-start-point-and-end-point.md)을 참조하세요.

1. 다른 워크플로우에서 하위 워크플로우로 사용할 워크플로우를 만듭니다.
1. 워크플로우 시작 부분에 우선 순위가 1인 **[!UICONTROL Jump (end point)]** 활동을 삽입합니다. &quot;끝점&quot; 유형 점프가 여러 개 있는 경우 Adobe Campaign에서 가장 낮은 숫자의 &quot;끝점&quot; 점프를 사용합니다.
1. 워크플로우 끝에 우선 순위가 2인 **[!UICONTROL Jump (start point)]** 활동을 삽입합니다. &quot;시작 지점&quot; 유형 점프가 여러 개 있는 경우 Adobe Campaign에서 가장 높은 숫자의 &quot;시작 지점&quot; 점프를 사용합니다.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >하위 워크플로우 활동이 여러 개의 **[!UICONTROL Jump]** 활동이 있는 워크플로우를 참조하는 경우, 하위 워크플로우는 가장 낮은 숫자의 &quot;끝점&quot; 유형 점프와 가장 높은 숫자의 &quot;시작점&quot; 유형 점프 사이에서 실행됩니다.
   >
   >하위 워크플로우를 올바르게 실행하려면 숫자가 가장 낮은 &quot;끝점&quot; 유형 점프만 있고 숫자가 가장 높은 &quot;시작점&quot; 유형 점프만 있어야 합니다.

1. 이 &quot;하위 워크플로우&quot;를 완료하고 저장합니다.
1. 기본 워크플로우를 만듭니다.
1. **[!UICONTROL Sub-workflow]** 활동을 삽입하고 엽니다.
1. **[!UICONTROL Workflow template]** 드롭다운 목록에서 사용할 워크플로를 선택합니다.

   ![](assets/subworkflow_selection.png)

1. 구성 스크립트를 추가하여 참조된 워크플로우를 변경할 수도 있습니다.
1. **[!UICONTROL Ok]**&#x200B;을(를) 클릭합니다. 선택한 워크플로우에서 **[!UICONTROL Jump (start point)]** 활동의 레이블을 사용하는 아웃바운드 전환을 자동으로 만듭니다.

   ![](assets/subworkflow_outbound.png)

1. 워크플로우를 실행합니다.

일단 실행되면 하위 워크플로로 호출된 워크플로가 **[!UICONTROL Being edited]** 상태로 유지되는데, 이것은 다음을 의미합니다.

* 전환을 마우스 오른쪽 버튼으로 클릭하여 대상을 표시할 수 없습니다.
* 중간 모집단 수를 표시할 수 없습니다.
* 하위 워크플로우 로그는 기본 워크플로우에 표시됩니다.

  ![](assets/subworkflow_logs.png)

>[!NOTE]
>
>하위 워크플로우에서 오류가 발생하면 기본 워크플로우가 일시 중지되고 하위 워크플로우의 복사본이 만들어집니다.

## 입력 매개 변수(선택 사항) {#input-parameters--optional-}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수로 정의된 대상을 지정해야 합니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 세트는 쿼리의 타겟팅된 모집단을 식별합니다. **[!UICONTROL tableName]**&#x200B;은(는) 대상 식별자를 기록하는 테이블의 이름이고, **[!UICONTROL schema]**&#x200B;은(는) 모집단의 스키마(일반적으로 nms:recipient)이며, **[!UICONTROL recCount]**&#x200B;은(는) 테이블의 요소 수입니다.

* targetSchema: 이 값은 작업 테이블의 스키마입니다. 이 매개 변수는 **[!UICONTROL tableName]** 및 **[!UICONTROL schema]**&#x200B;이(가) 있는 모든 전환에 유효합니다.
