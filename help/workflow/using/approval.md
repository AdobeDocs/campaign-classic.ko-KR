---
title: 승인
seo-title: 승인
description: 승인
seo-description: null
page-status-flag: never-activated
uuid: 49285790-5aa7-4e15-a657-42e4f78be518
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: a0090c78-5873-446d-8d5f-b0f94ff5d373
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 승인{#approval}

승인 **작업은** 연산자의 참여가 필요합니다. 운영자에게 작업이 할당되고 이메일 메시지 또는 콘솔을 통해 연결된 웹 페이지를 사용하여 이메일로 응답할 수 있습니다.

## 작업 할당 {#task-assignment}

기본적으로 승인은 연산자 그룹에 할당됩니다. 이 그룹은 역할을 나타냅니다(예:&#39;뉴스레터 컨텐츠 그룹&#39; 또는 &#39;뉴스레터 타깃팅 그룹&#39;. 그룹의 각 연산자는 응답할 수 있지만 첫 번째 응답만 고려됩니다(여러 승인이 있는 경우는 제외).

필요한 경우 단일 연산자 또는 필터에 정의된 연산자 세트에 승인 작업을 할당할 수 있습니다.

* 단일 연산자를 선택하려면 **[!UICONTROL Operator]** 필드에서 **[!UICONTROL Assignment type]** 값을 선택하고 **[!UICONTROL Assignee]** 필드의 드롭다운 목록에서 관련 연산자를 선택합니다.

   ![](assets/s_advuser_validation_box_assign.png)

   >[!CAUTION]
   >
   >선택한 운영자만 작업을 승인할 수 있습니다.

* 승인 연산자를 필터링하기 위한 쿼리를 정의할 수 있습니다. 이렇게 하려면 다음 예와 같이 **[!UICONTROL Filter]** 필드에서 **[!UICONTROL Assignment type]** 값을 선택하고 **[!UICONTROL Advanced parameters...]** 링크를 클릭하여 필터링 조건을 정의합니다.

   ![](assets/s_advuser_validation_box_filter.png)

단일 승인 시 연산자 선택에 해당하는 전환이 활성화되고 작업이 완료됩니다.다른 연산자는 회신할 수 없습니다.

여러 승인이 있으면 각 연산자의 선택에 따라 전환이 활성화됩니다. 그룹의 모든 연산자가 답글을 남겼거나 작업이 만료되면 작업이 완료됩니다.

이 활동은 처리를 차단하지 않으며, 워크플로우는 응답을 기다리는 동안 다른 작업을 수행할 수 있습니다.

연산자는 콘솔에서 해당 연산자에 할당된 작업을 승인할 수 있습니다. 관리자 권한이 있는 연산자는 연산자에 할당된 작업을 보고 삭제할 수 있지만 응답할 수는 없습니다.

활동의 제목 또는 메시지 본문을 수정하는 것은 현재 작업에 영향을 주지 않지만, 반면에, 가능한 선택 항목을 수정하는 것은 현재 작업에 직접적인 영향을 미치며, 이는 새 선택 항목 목록을 자동으로 상속합니다.

**승인** 유형 작업은 **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** 노드에서 액세스할 수 있습니다.운영자는 이 보기를 통해 승인 양식에 직접 액세스할 수 있습니다.

![](assets/s_advuser_validation_from_console.png)

## 속성 {#properties}

사용자 지정 변수는 검토자에게 보낸 메시지에서 사용할 수 있습니다. 메시지 제목이나 본문에 삽입할 수 있습니다.

![](assets/edit_validation.png)

이 **[!UICONTROL Title]** 필드에는 메시지 제목이 있습니다.전송된 이메일 메시지의 제목입니다. 메시지 본문뿐만 아니라 제목도 JavaScript 템플릿이므로 워크플로우의 컨텍스트에 따라 계산된 값을 포함할 수 있습니다.

편집기의 하단 섹션에서는 가능한 대답 목록을 정의할 수 있습니다. 각 응답에 해당하는 전환이 있습니다. 이름은 내부 식별자이며 레이블은 선택 항목 목록에 표시될 텍스트입니다.

연산자를 알리는 데 사용할 배달 템플릿을 선택하려면 **[!UICONTROL Advanced parameters...]** 링크를 클릭합니다. 기본 템플릿(내부 이름 &#39;notifyAssignee&#39;)은 제목과 메시지를 가져와서 응답하는 데 사용되는 웹 페이지에 링크를 추가합니다.

메시지 레이아웃을 개인화하기 위해 이 템플릿을 수정할 수 있지만 사본을 만드는 것이 좋습니다. 알림이 올바르게 작동하려면 타깃팅 메커니즘(외부 파일, 대상 매핑)을 수정해서는 안 됩니다.

승인 예는 승인 정의에 [나와](../../workflow/using/executing-a-workflow.md#defining-approvals)있습니다.

## 출력 매개 변수 {#output-parameters}

* **[!UICONTROL response]**

   응답과 관련된 댓글

* **[!UICONTROL responseOperator]**

   응답한 연산자의 식별자입니다. 이 필드는 숫자 값이지만 **[!UICONTROL String]** 필드입니다.

