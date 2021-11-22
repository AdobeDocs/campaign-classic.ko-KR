---
product: campaign
title: 로컬 승인
description: 로컬 승인
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 2d9cbfc8-1f99-4b38-8460-77c7c986e9ca
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 1%

---

# 로컬 승인{#local-approval}

![](../../assets/common.svg)

타겟팅 워크플로우에 통합되면, **[!UICONTROL Local approval]** 활동을 통해 게재를 보내기 전에 수신자 승인 프로세스를 설정할 수 있습니다.

![](assets/local_validation_0.png)

>[!CAUTION]
>
>이 활동을 사용하려면 캠페인 옵션인 분산 마케팅 모듈을 구매해야 합니다. 사용권 계약을 확인하십시오.

예 **[!UICONTROL Local approval]** 배포 템플릿을 사용하는 활동은 [로컬 승인 활동 사용](using-the-local-approval-activity.md).

먼저 활동 및 **[!UICONTROL Action to execute]** 필드:

![](assets/local_validation_1.png)

* 을(를) 선택합니다 **[!UICONTROL Target approval notification]** 배달 전에 로컬 감독자에게 알림 이메일을 전송하여 자신에게 할당된 수신자를 승인하도록 요청하는 옵션입니다.

   ![](assets/local_validation_intro_2.png)

* **증분 쿼리**: 쿼리를 수행하고 실행을 계획할 수 있습니다. 자세한 내용은 [증분 쿼리](incremental-query.md) 섹션을 참조하십시오.

   ![](assets/local_validation_intro_3.png)

## Target 승인 알림 {#target-approval-notification}

이 경우 **[!UICONTROL Local approval]** 활동은 업스트림 타깃팅과 게재 사이에 배치됩니다.

![](assets/local_validation_2.png)

대상 승인을 위한 알림의 경우 입력할 필드는 다음과 같습니다.

![](assets/local_validation_3.png)

* **[!UICONTROL Distribution context]**: 선택 **[!UICONTROL Specified in the transition]** 사용 중인 경우 옵션 **[!UICONTROL Split]** 활동을 입력하여 타깃팅된 모집단을 제한합니다. 이 경우 분배 템플릿은 분할 활동에 입력됩니다. 타겟팅된 모집단을 제한하지 않는 경우 **[!UICONTROL Explicit]** 옵션을 선택하고 배포 템플릿을 **[!UICONTROL Data distribution]** 필드.

   데이터 배포 템플릿 만들기에 대한 자세한 내용은 [데이터 배포당 하위 집합 레코드 수 제한](split.md#limiting-the-number-of-subset-records-per-data-distribution).

* **[!UICONTROL Approval management]**

   * 게재 템플릿과 전자 메일 알림에 사용할 제목을 선택합니다. 기본 템플릿을 사용할 수 있습니다. **[!UICONTROL Local approval notification]**. 승인 및 피드백 알림에서 수신자 목록 위에 표시되는 설명을 추가할 수도 있습니다.
   * 을(를) 지정합니다. **[!UICONTROL Approval type]** 승인 기한(승인 시작 날짜부터 또는 기한)에 해당합니다. 이 날짜에서는 워크플로우가 다시 시작되고 승인되지 않은 수신자는 타겟팅에서 고려되지 않습니다. 알림이 전송되면 로컬 관리자가 연락처를 승인할 수 있도록 활동이 큐에 추가됩니다.

      >[!NOTE]
      >
      >기본적으로 승인 프로세스가 시작되면 활동이 3일 동안 보류됩니다.

      또한 한 개 이상의 미리 알림을 추가하여 지역 감독관에게 마감일이 다가오고 있음을 알릴 수도 있습니다. 이렇게 하려면 **[!UICONTROL Add a reminder]** 링크를 클릭합니다.

* **[!UICONTROL Complementary set]**: a **[!UICONTROL Generate complement]** 옵션을 사용하면 승인되지 않은 모든 대상을 포함하는 두 번째 세트를 생성할 수 있습니다.

   >[!NOTE]
   >
   >이 옵션은 기본적으로 비활성화됩니다.

## 게재 피드백 보고서 {#delivery-feedback-report}

이 경우 **[!UICONTROL Local approval]** 활동은 게재 후 배치됩니다.

![](assets/local_validation_4.png)

게재 피드백 보고서의 경우 다음 필드를 입력해야 합니다.

![](assets/local_validation_workflow_4.png)

* 을(를) 선택합니다 **[!UICONTROL Specified in the transition]** 이전 활동 중에 게재를 입력한 경우 선택합니다. 선택 **[!UICONTROL Explicit]** 을 눌러 로컬 승인 활동에서 게재를 지정합니다.
* 게재 템플릿과 알림 이메일의 개체를 선택합니다. 기본 템플릿이 있습니다. **[!UICONTROL Local approval notification]**.

## 예: 워크플로우 게재 승인 {#example--approving-a-workflow-delivery}

이 예제에서는 워크플로우 게재에 대한 승인 프로세스를 설정하는 방법을 보여줍니다. 게재 워크플로우 만들기에 대한 자세한 내용은 [예: 게재 워크플로우](delivery.md#example--delivery-workflow) 섹션을 참조하십시오.

연산자는 다음 두 가지 방법 중 하나로 게재를 승인할 수 있습니다. 이메일 메시지 또는 콘솔을 통해 연결된 웹 페이지 사용.

* 웹 승인

   관리자 그룹 운영자에게 보낸 이메일을 통해 게재 대상을 승인할 수 있습니다. 메시지에 정의된 텍스트가 사용되고 JavaScript 표현식이 계산된 값으로 대체됩니다(이 경우 &#39;574&#39;)

   게재를 승인하려면 관련 링크를 클릭하고 Adobe Campaign 콘솔에 로그인합니다.

   ![](assets/new-workflow-valid-webaccess.png)

   선택한 후 **[!UICONTROL Submit]** 버튼을 클릭합니다.

   ![](assets/new-workflow-valid-webaccess-confirm.png)

* 콘솔을 통한 승인

   트리 구조에서 **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** 노드에는 현재 연결된 연산자가 승인할 작업 목록이 포함되어 있습니다. 목록에 한 줄이 표시됩니다. 응답하려면 이 줄을 두 번 클릭하십시오. 다음 창이 표시됩니다.

![](assets/new-workflow-7.png)

선택 **예**&#x200B;를 클릭한 다음 **[!UICONTROL Approve]**. 응답이 기록되었음을 알리는 메시지가 표시됩니다.

워크플로우 화면으로 돌아갑니다. 10초 정도 지나면 다이어그램이 다음과 같이 표시됩니다.

![](assets/new-workflow-8.png)

워크플로우가 **[!UICONTROL Delivery control]** 작업. 이 경우 은 이전에 만든 게재를 시작하는 것을 의미합니다. 워크플로우가 오류 없이 끝났습니다.
