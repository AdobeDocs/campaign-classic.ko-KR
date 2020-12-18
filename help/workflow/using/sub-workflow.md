---
solution: Campaign Classic
product: campaign
title: 하위 워크플로우
description: 하위 워크플로우 활동에 대한 자세한 내용
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---


# 하위 워크플로우{#sub-workflow}

**[!UICONTROL Sub-workflow]** 활동을 사용하면 다른 워크플로우의 실행을 트리거하고 결과를 복구할 수 있습니다. 이 활동을 통해 간결한 인터페이스를 사용하면서 복잡한 워크플로우를 사용할 수 있습니다.

단일 워크플로우에서 여러 하위 워크플로우를 호출할 수 있습니다. 하위 워크플로우는 동기식으로 실행됩니다.

아래 예에서 기본 워크플로우는 이동을 사용하여 하위 워크플로우를 호출하는 것입니다. 점프 유형 그래픽 개체에 대한 자세한 내용은 [이 섹션](../../workflow/using/jump--start-point-and-end-point-.md)을 참조하십시오.

1. 다른 워크플로우에서 하위 워크플로우로 사용할 워크플로우를 만듭니다.
1. 워크플로우 시작 부분에 우선 순위가 1인 **[!UICONTROL Jump (end point)]** 활동을 삽입합니다. &quot;끝점&quot; 문자 이동이 여러 개인 경우 Adobe Campaign에서는 &quot;끝점&quot; 이동을 가장 낮은 숫자로 사용합니다.
1. 워크플로가 끝날 때 우선 순위가 2인 **[!UICONTROL Jump (start point)]** 활동을 삽입합니다. &quot;시작점&quot; 문자 이동이 여러 개인 경우 Adobe Campaign에서는 &quot;시작점&quot; 이동을 가장 높은 숫자로 사용합니다.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >하위 워크플로우 활동이 여러 **[!UICONTROL Jump]** 활동이 있는 워크플로우를 참조하는 경우 하위 워크플로우는 가장 낮은 수의 &quot;끝점&quot; 유형 점프 및 가장 높은 수의 &quot;시작점&quot; 유형 이동 사이에 실행됩니다.
   >
   >하위 워크플로를 올바르게 실행하려면 가장 낮은 번호로 한 개의 &quot;끝점&quot; 유형만 이동하고 가장 높은 숫자로 한 개의 &quot;시작점&quot; 유형만 이동해야 합니다.

1. 이 &quot;하위 워크플로우&quot;를 완료하고 저장합니다.
1. 기본 워크플로우를 만듭니다.
1. **[!UICONTROL Sub-workflow]** 활동을 삽입하고 엽니다.
1. **[!UICONTROL Workflow template]** 드롭다운 목록에서 사용할 워크플로우를 선택합니다.

   ![](assets/subworkflow_selection.png)

1. 구성 스크립트를 추가하여 참조된 작업 흐름을 변경할 수도 있습니다.
1. **[!UICONTROL Ok]**&#x200B;을(를) 클릭합니다. 그러면 선택한 워크플로우에서 **[!UICONTROL Jump (start point)]** 활동의 레이블을 사용하여 아웃바운드 전환이 자동으로 생성됩니다.

   ![](assets/subworkflow_outbound.png)

1. 워크플로우를 실행합니다.

하위 워크플로우로 호출된 워크플로우가 실행되면 **[!UICONTROL Being edited]** 상태로 유지되며, 이것은 다음을 의미합니다.

* 전환을 마우스 오른쪽 단추로 클릭하여 대상을 표시할 수 없습니다.
* 중간 모집단의 수를 표시할 수 없습니다.
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

이 세 값 집합은 쿼리를 기준으로 타게팅된 모집단을 식별합니다. **[!UICONTROL tableName]** 는 대상 식별자를 기록하는 테이블의 이름이며, 채우기 **[!UICONTROL schema]** 의 스키마(일반적으로 nms:recipient) **[!UICONTROL recCount]** 이며 표의 요소 수입니다.

* targetSchema:이 값은 작업 테이블의 스키마입니다. 이 매개 변수는 **[!UICONTROL tableName]** 및 **[!UICONTROL schema]**&#x200B;이(가) 있는 모든 전환에서 유효합니다.
