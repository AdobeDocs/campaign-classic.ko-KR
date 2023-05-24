---
product: campaign
title: 승인
description: 승인
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Approvals
exl-id: 7ff5da71-ef82-48a2-a608-06a4ca188bb9
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# 승인{#approval}



An **승인** 작업에는 연산자의 참여가 필요합니다. 운영자에게 작업이 할당되며 이메일 메시지 또는 콘솔을 통해 연결된 웹 페이지를 사용하여 이메일로 응답할 수 있습니다.

## 작업 할당 {#task-assignment}

기본적으로 승인은 운영자 그룹에 할당됩니다. 이 그룹은 역할을 나타냅니다(예: &#39;뉴스레터 콘텐츠 그룹&#39; 또는 &#39;뉴스레터 타겟팅 그룹&#39;). 그룹의 각 연산자는 응답할 수 있지만 첫 번째 응답만 고려합니다(여러 승인이 있는 경우 제외).

필요한 경우 단일 연산자 또는 필터로 정의된 연산자 세트에 승인 작업을 할당할 수 있습니다.

* 단일 연산자를 선택하려면 **[!UICONTROL Operator]** 의 값 **[!UICONTROL Assignment type]** 필드를 작성하고 드롭다운 목록에서 관련 연산자를 선택합니다. **[!UICONTROL Assignee]** 필드.

   ![](assets/s_advuser_validation_box_assign.png)

   >[!CAUTION]
   >
   >선택한 운영자만 작업을 승인할 수 있습니다.

* 승인 연산자를 필터링할 쿼리를 정의할 수 있습니다. 이렇게 하려면 **[!UICONTROL Filter]** 의 값 **[!UICONTROL Assignment type]** 필드를 클릭하고 **[!UICONTROL Advanced parameters...]** 다음 예와 같이 필터링 조건을 정의하는 링크:

   ![](assets/s_advuser_validation_box_filter.png)

1회 승인 시 운영자 선택에 해당하는 전환이 활성화되고 작업이 종료됨: 다른 운영자는 회신할 수 없음.

여러 승인이 있는 경우 각 연산자의 선택에 해당하는 전환이 활성화됩니다. 그룹의 모든 운영자가 회신하거나 작업이 만료되면 작업이 완료됩니다.

이 활동은 처리를 차단하지 않으며 워크플로는 회신을 기다리는 동안 다른 작업을 수행할 수 있습니다.

운영자는 콘솔에서 해당 운영자에게 할당된 작업을 승인할 수 있습니다. 관리자 권한이 있는 운영자는 운영자에게 할당된 작업을 보고 삭제할 수 있지만 회신할 수는 없습니다.

활동의 제목 또는 메시지 본문을 수정해도 현재 작업에는 영향을 주지 않지만, 가능한 선택 항목을 수정하면 현재 작업에 직접 영향을 미칩니다. 현재 작업은 자동으로 새 선택 항목 목록을 상속합니다.

**승인** 유형 작업은 다음에서 액세스할 수 있습니다. **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** 노드: 운영자는 이 보기를 통해 승인 양식에 직접 액세스할 수 있습니다.

![](assets/s_advuser_validation_from_console.png)

## 속성 {#properties}

사용자 지정 변수는 검토자에게 보내는 메시지에 사용할 수 있습니다. 메시지 제목이나 본문에 삽입할 수 있습니다.

![](assets/edit_validation.png)

이 **[!UICONTROL Title]** 필드에는 메시지의 제목이 포함됩니다. 보낸 이메일 메시지의 제목입니다. 제목과 메시지 본문은 JavaScript 템플릿이므로 워크플로우의 컨텍스트에 따라 계산된 값을 포함할 수 있습니다.

편집기의 하단 섹션에서는 가능한 답변 목록을 정의할 수 있습니다. 각 답변에 해당하는 전환이 있습니다. 이름은 내부 식별자이고 레이블은 선택 항목 목록에 표시되는 텍스트입니다.

다음을 클릭합니다. **[!UICONTROL Advanced parameters...]** 운영자에게 알리는 데 사용할 게재 템플릿을 선택하는 링크입니다. 기본 템플릿(내부 이름 &#39;notifyAssignee&#39;)은 제목과 메시지를 가져오고 답변에 사용된 웹 페이지에 링크를 추가합니다.

메시지 레이아웃을 개인화하기 위해 이 템플릿을 수정할 수 있지만 복사본을 만드는 것이 좋습니다. 알림이 올바르게 작동하려면 타겟팅 메커니즘(외부 파일, 타겟 매핑)이 필요하므로 수정해서는 안 됩니다.

승인 예를에 나와 있습니다. [승인 정의](defining-approvals.md).

## 출력 매개 변수 {#output-parameters}

* **[!UICONTROL response]**

   응답 관련 댓글

* **[!UICONTROL responseOperator]**

   응답한 연산자의 식별자입니다. 이 필드는 숫자이지만 **[!UICONTROL String]** 필드.
