---
title: 로컬 승인
seo-title: 로컬 승인
description: 로컬 승인
seo-description: null
page-status-flag: never-activated
uuid: 4de59c8a-e229-4c8d-acab-2b116cafb70b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: a223641e-93e1-42ef-bb6b-8e1a0f8f6a65
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 로컬 승인{#local-approval}

타깃팅 워크플로우에 통합되면, **[!UICONTROL Local approval]** 활동을 통해 전달이 전송되기 전에 수신자 승인 프로세스를 설정할 수 있습니다.

![](assets/local_validation_0.png)

>[!CAUTION]
>
>이 활동을 사용하려면 캠페인 옵션인 분산 마케팅 모듈을 구매해야 합니다. 사용권 계약을 확인하십시오.

배포 템플릿이 있는 **[!UICONTROL Local approval]** 활동의 예는 로컬 승인 활동 [사용을](../../workflow/using/using-the-local-approval-activity.md)참조하십시오.

활동 및 **[!UICONTROL Action to execute]** 필드에 대한 레이블을 입력하여 시작합니다.

![](assets/local_validation_1.png)

* 전달 전에 지역 감독자에게 알림 이메일을 전송하여 해당 지역 관리자에게 할당된 받는 사람을 승인하도록 요청하는 옵션을 **[!UICONTROL Target approval notification]** 선택합니다.

   ![](assets/local_validation_intro_2.png)

* **증분 쿼리**:쿼리를 수행하고 실행을 계획할 수 있습니다. 증분 [쿼리](../../workflow/using/incremental-query.md) 섹션을 참조하십시오.

   ![](assets/local_validation_intro_3.png)

## Target 승인 알림 {#target-approval-notification}

이 경우 업스트림 타깃팅과 배달 사이에 **[!UICONTROL Local approval]** 활동이 배치됩니다.

![](assets/local_validation_2.png)

대상 승인에 대한 알림의 경우 입력할 필드는 다음과 같습니다.

![](assets/local_validation_3.png)

* **[!UICONTROL Distribution context]**:유형 활동을 사용하여 타깃팅된 인구를 제한하는 **[!UICONTROL Specified in the transition]** **[!UICONTROL Split]** 경우 옵션을 선택합니다. 이 경우 배포 템플릿은 분할 활동에 입력됩니다. 타깃팅된 인구를 제한하지 않는 경우, 여기에서 **[!UICONTROL Explicit]** 옵션을 선택하고 **[!UICONTROL Data distribution]** 필드에 배포 템플릿을 입력합니다.

   데이터 배포 템플릿 만들기에 대한 자세한 내용은 데이터 [배포당 하위 집합 레코드 수 제한을](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution)참조하십시오.

* **[!UICONTROL Approval management]**

   * 이메일 알림에 사용할 게재 템플릿과 제목을 선택합니다. 기본 템플릿을 사용할 수 있습니다. **[!UICONTROL Local approval notification]** Adobe 승인 및 피드백 알림의 수신자 목록 위에 표시되는 설명을 추가할 수도 있습니다.
   * 승인 최종 기한(승인 시작 날짜나 기한)에 해당하는 **[!UICONTROL Approval type]** 항목을 지정합니다. 이 날짜에 워크플로우가 다시 시작되고 승인되지 않은 수신자는 타깃팅에서 고려되지 않습니다. 알림이 전송되면 지역 관리자가 연락처를 승인할 수 있도록 활동이 큐에 올라가 있습니다.

      >[!NOTE]
      >
      >기본적으로 승인 프로세스가 시작되면 활동이 3일 동안 보류됩니다.

      또한 하나 이상의 미리 알림을 추가하여 마감일이 다가오고 있음을 지역 감독관에게 알릴 수도 있습니다. 이렇게 하려면 **[!UICONTROL Add a reminder]** 링크를 클릭합니다.

* **[!UICONTROL Complementary set]**:이 **[!UICONTROL Generate complement]** 옵션을 사용하면 승인되지 않은 모든 대상을 포함하는 두 번째 세트를 생성할 수 있습니다.

   >[!NOTE]
   >
   >이 옵션은 기본적으로 비활성화됩니다.

## 전달 피드백 보고서 {#delivery-feedback-report}

이 경우, **[!UICONTROL Local approval]** 활동은 배달 후에 배치됩니다.

![](assets/local_validation_4.png)

배달 피드백 보고서의 경우 다음 필드를 입력해야 합니다.

![](assets/local_validation_workflow_4.png)

* 이전 활동 중에 배달을 입력한 경우 **[!UICONTROL Specified in the transition]** 옵션을 선택합니다. 로컬 승인 활동에서 배달을 **[!UICONTROL Explicit]** 지정하려면 선택합니다.
* 배달 템플릿 및 알림 이메일의 개체를 선택합니다. 기본 템플릿이 있습니다. **[!UICONTROL Local approval notification]** Adobe

## 예:워크플로우 전달 승인 {#example--approving-a-workflow-delivery}

이 예에서는 워크플로우 전달에 대한 승인 프로세스를 설정하는 방법을 보여줍니다. 배달 워크플로우 만들기에 대한 자세한 내용은 다음 예를 [참조하십시오.전달 워크플로우](../../workflow/using/delivery.md#example--delivery-workflow) 섹션.

연산자는 다음 두 가지 방법 중 하나로 배달을 승인할 수 있습니다.이메일 메시지 또는 콘솔을 통해 링크된 웹 페이지를 사용합니다.

* 웹 승인

   관리자 그룹의 운영자에게 보낸 이메일을 통해 배달 대상을 승인할 수 있습니다. 메시지는 정의된 텍스트를 사용하며 JavaScript 표현식은 계산된 값으로 대체됩니다(이 경우 &#39;574&#39;).

   배달을 승인하려면 관련 링크를 클릭하고 Adobe Campaign 콘솔에 로그온합니다.

   ![](assets/new-workflow-valid-webaccess.png)

   선택하고 **[!UICONTROL Submit]** 단추를 클릭합니다.

   ![](assets/new-workflow-valid-webaccess-confirm.png)

* 콘솔을 통한 승인

   트리 구조에서는 **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** 노드에 현재 연결된 연산자가 승인할 작업 목록이 포함되어 있습니다. 목록에 한 줄이 표시됩니다. 응답하려면 이 줄을 두 번 클릭합니다. 다음 창이 표시됩니다.

![](assets/new-workflow-7.png)

예를 **선택한**&#x200B;다음 을 클릭합니다 **[!UICONTROL Approve]**. 응답이 기록되었음을 알리는 메시지가 표시됩니다.

워크플로우 화면으로 돌아갑니다.10초 후 다이어그램은 다음과 같이 표시됩니다.

![](assets/new-workflow-8.png)

워크플로우가 작업을 실행했으며 이 경우 이전에 만든 배달을 시작하는 것을 의미합니다. **[!UICONTROL Delivery control]** 워크플로우가 오류 없이 완료되었습니다.
