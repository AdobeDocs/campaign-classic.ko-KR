---
product: campaign
title: 하위 워크플로우
description: 하위 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: bc64ca11-2c50-4896-b6c6-ae42c0315924
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# 하위 워크플로우{#sub-workflow}



다음 **[!UICONTROL Sub-workflow]** 활동을 사용하면 다른 워크플로우의 실행을 트리거하고 결과를 복구할 수 있습니다. 이 활동을 사용하면 간소화된 인터페이스를 사용하면서도 복잡한 워크플로우를 사용할 수 있습니다.

단일 워크플로우에서 여러 하위 워크플로우를 호출할 수 있습니다. 하위 워크플로우는 동기적으로 실행됩니다.

아래 예에서 기본 워크플로우는 점프를 사용하여 하위 워크플로를 호출하는 것입니다. 점프 유형 그래픽 객체에 대한 자세한 내용은 [이 섹션](jump--start-point-and-end-point-.md).

1. 다른 워크플로우에서 하위 워크플로우로 사용할 워크플로우를 만듭니다.
1. 삽입 **[!UICONTROL Jump (end point)]** 워크플로우 시작 시 우선순위가 1인 활동. &quot;끝점&quot; 유형 점프가 여러 개 있는 경우 Adobe Campaign에서 가장 낮은 숫자의 &quot;끝점&quot; 점프를 사용합니다.
1. 삽입 **[!UICONTROL Jump (start point)]** 워크플로우 종료 시 우선순위가 2인 활동. &quot;시작 지점&quot; 유형 점프가 여러 개 있는 경우 Adobe Campaign에서 가장 높은 숫자의 &quot;시작 지점&quot; 점프를 사용합니다.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >하위 워크플로우 활동이 여러 개의 워크플로우를 참조하는 경우 **[!UICONTROL Jump]** 활동에서 하위 워크플로는 숫자가 가장 낮은 &quot;끝점&quot; 유형 점프와 숫자가 가장 높은 &quot;시작점&quot; 유형 점프 사이에서 실행됩니다.
   >
   >하위 워크플로우를 올바르게 실행하려면 숫자가 가장 낮은 &quot;끝점&quot; 유형 점프만 있고 숫자가 가장 높은 &quot;시작점&quot; 유형 점프만 있어야 합니다.

1. 이 &quot;하위 워크플로우&quot;를 완료하고 저장합니다.
1. 기본 워크플로우를 만듭니다.
1. 삽입 **[!UICONTROL Sub-workflow]** 활동을 수행하고 엽니다.
1. 에서 사용할 워크플로를 선택합니다. **[!UICONTROL Workflow template]** 드롭다운 목록입니다.

   ![](assets/subworkflow_selection.png)

1. 구성 스크립트를 추가하여 참조된 워크플로우를 변경할 수도 있습니다.
1. **[!UICONTROL Ok]**&#x200B;을(를) 클릭합니다. 이 옵션을 선택하면 레이블이 인 아웃바운드 전환이 자동으로 만들어집니다. **[!UICONTROL Jump (start point)]** 선택한 워크플로우의 활동입니다.

   ![](assets/subworkflow_outbound.png)

1. 워크플로우를 실행합니다.

실행되면 하위 워크플로우로 호출된 워크플로우가에 유지됩니다. **[!UICONTROL Being edited]** 상태, 즉

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

이 세 값 세트는 쿼리의 타겟팅된 모집단을 식별합니다. **[!UICONTROL tableName]** 는 대상 식별자를 기록하는 테이블의 이름입니다. **[!UICONTROL schema]** 모집단의 스키마(일반적으로 nms:recipient)이며, **[!UICONTROL recCount]** 는 테이블에 있는 요소의 수입니다.

* targetSchema: 이 값은 작업 테이블의 스키마입니다. 이 매개 변수는 다음과 같은 모든 전환에 유효합니다. **[!UICONTROL tableName]** 및 **[!UICONTROL schema]**.
