---
solution: Campaign Classic
product: campaign
title: 마케팅 캠페인 대상 고객
description: 마케팅 캠페인의 고객을 정의하는 방법 학습
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 1%

---


# 캠페인 대상 선택 {#marketing-campaign-deliveries}

마케팅 캠페인에서 각 게재에 대해 다음을 정의할 수 있습니다.

* 대상 - [워크플로우](#building-the-main-target-in-a-workflow) 및 [대상 모집단 선택](#selecting-the-target-population)에서 대상 작성에 대해 자세히 알아보십시오.
* 제어 그룹 - [이 섹션](#defining-a-control-group)에서 자세히 알아보십시오.
* 시드 주소 - [이 섹션](../../delivery/using/about-seed-addresses.md)에서 자세히 알아보십시오.

이 정보 중 일부는 [캠페인 템플릿](../../campaign/using/marketing-campaign-templates.md#campaign-templates)에서 상속될 수 있습니다.

배달 대상을 빌드하려면 데이터베이스의 받는 사람에 대한 필터링 기준을 정의할 수 있습니다. 이 수신자 선택 모드는 [이 섹션](../../delivery/using/steps-defining-the-target-population.md)에 표시됩니다.

## 그룹으로 보내기

모집단을 목록으로 가져온 다음 게재에서 이 목록을 타깃팅할 수 있습니다. 이렇게 하려면 아래 단계를 수행합니다:

1. 관련 배달을 편집하고 **[!UICONTROL To]** 링크를 클릭하여 대상 모집단을 변경합니다.

1. **[!UICONTROL Main target]** 탭에서 **[!UICONTROL Defined via the database]** 옵션을 선택하고 **[!UICONTROL Add]**&#x200B;를 클릭하여 수신자를 선택합니다.

![](assets/s_user_target_group_add.png)

1. **[!UICONTROL A list of recipients]**&#x200B;을 선택하고 **[!UICONTROL Next]**&#x200B;을 클릭하여 선택합니다.

![](assets/s_user_target_group_next.png)

## 캠페인 워크플로우 {#building-the-main-target-in-a-workflow}에서 대상을 만듭니다.

게재의 기본 타겟은 캠페인 워크플로우에서 정의할 수도 있습니다.이 그래픽 환경에서는 쿼리, 테스트 및 연산자를 사용하여 대상을 만들 수 있습니다.결합, 중복 제거, 공유 등

>[!IMPORTANT]
>
>캠페인에는 28개 이상의 워크플로우를 추가할 수 없습니다. 이 제한 이후에는 추가 워크플로우가 인터페이스에 표시되지 않으며 오류를 생성할 수 있습니다.

### 워크플로 {#creating-a-targeting-workflow} 만들기

타깃팅은 워크플로우의 그래픽 시퀀스에서 필터링 조건을 조합하여 만들 수 있습니다. 요구 사항에 따라 타깃팅할 모집단 및 하위 모집단을 만들 수 있습니다. 워크플로우 편집기를 표시하려면 캠페인 대시보드에서 **[!UICONTROL Targeting and workflows]** 탭을 클릭합니다.

![](assets/s_ncs_user_edit_op_wf_link.png)

대상 채우기는 워크플로에 배치된 하나 이상의 쿼리를 통해 Adobe Campaign 데이터베이스에서 추출됩니다. 쿼리를 빌드하는 방법에 대해 알아보려면 [이 섹션](../../workflow/using/query.md)을 참조하십시오.

쿼리를 실행하고 결합, 교차, 공유, 제외 등과 같은 상자를 통해 모집단을 공유할 수 있습니다.

작업 영역의 왼쪽에 있는 목록에서 객체를 선택하고 이를 연결하여 대상을 구성합니다.

![](assets/s_ncs_user_edit_op_wf_tab_a.png)

다이어그램에서 대상 구성에 필요한 타깃팅 및 예약 쿼리를 다이어그램에 연결합니다. 데이터베이스에서 추출된 인구를 확인하기 위해 구성이 진행되는 동안 타깃팅을 실행할 수 있습니다.

>[!NOTE]
>
>쿼리 정의에 대한 예와 절차는 [이 섹션](../../workflow/using/query.md)에 있습니다.

편집기의 왼쪽 섹션에는 활동을 나타내는 그래픽 개체 라이브러리가 포함되어 있습니다. 첫 번째 탭에는 타깃팅 활동이 포함되어 있으며 두 번째 탭에는 때때로 타깃팅 활동을 조정하는 데 사용되는 흐름 제어 활동이 포함되어 있습니다.

타깃팅 워크플로우 실행 및 서식 기능은 다이어그램 편집기 도구 모음을 통해 액세스할 수 있습니다.

![](assets/s_user_campaign_segmentation05.png)

>[!NOTE]
>
>다이어그램과 모든 표시 및 레이아웃 기능을 만드는 데 사용할 수 있는 활동은 [워크플로우로 자동화](../../workflow/using/architecture.md) 안내서에 자세히 설명되어 있습니다.

단일 캠페인에 대해 여러 타깃팅 워크플로우를 만들 수 있습니다. 워크플로우를 추가하려면:

1. 워크플로우 생성 영역의 왼쪽 위 섹션으로 이동하여 마우스 오른쪽 버튼을 클릭하고 **[!UICONTROL Add]**&#x200B;을 선택합니다. 이 영역 위에 있는 **[!UICONTROL New]** 단추를 사용할 수도 있습니다.

   ![](assets/s_ncs_user_add_a_wf.png)

1. **[!UICONTROL New workflow]** 템플릿을 선택하고 이 워크플로우의 이름을 지정합니다.
1. **[!UICONTROL OK]**&#x200B;을 클릭하여 워크플로우 만들기를 확인한 다음 이 워크플로우에 대한 다이어그램을 만듭니다.

### 워크플로 {#executing-a-workflow} 실행

적절한 권한이 있는 경우 도구 모음의 **[!UICONTROL Start]** 단추를 통해 타깃팅 워크플로우를 수동으로 시작할 수 있습니다.

타깃팅은 일정(스케줄러) 또는 이벤트(외부 신호, 파일 가져오기 등)에 따라 자동 실행을 위해 프로그래밍할 수 있습니다.

타깃팅 워크플로우 실행과 관련된 작업(시작, 중지, 일시 중지 등) **비동기** 프로세스:명령이 저장되고 서버에서 해당 명령을 적용하는 즉시 적용됩니다.

도구 모음 아이콘을 사용하여 타깃팅 워크플로우의 실행에 대한 작업을 수행할 수 있습니다.

* 시작 또는 다시 시작

   * **[!UICONTROL Start]** 아이콘을 사용하여 타깃팅 워크플로우를 시작할 수 있습니다. 이 아이콘을 클릭하면 입력 전환이 없는 모든 활동이 활성화됩니다(끝점 이동 제외).

      ![](assets/s_user_segmentation_start.png)

      서버는 다음과 같이 해당 상태에 따라 요청을 고려합니다.

      ![](assets/s_user_segmentation_start_status.png)

      프로세스 상태가 **[!UICONTROL Started]**&#x200B;으로 변경됩니다.

   * 적절한 도구 모음 아이콘을 통해 타깃팅 워크플로우를 다시 시작할 수 있습니다. 이 명령은 타깃팅 워크플로우 중지가 진행 중인 경우와 같이 **[!UICONTROL Start]** 아이콘을 사용할 수 없는 경우에 유용합니다. 이 경우 **[!UICONTROL Restart]** 아이콘을 클릭하여 다시 시작을 예측하십시오. 서버는 다음과 같이 요청을 고려합니다.

      ![](assets/s_user_segmentation_restart_status.png)

      그런 다음 프로세스가 **[!UICONTROL Started]** 상태를 입력합니다.

* 중지 또는 일시 중지

   * 도구 모음 아이콘을 사용하여 진행 중인 타깃팅 워크플로우를 중지하거나 일시 중지할 수 있습니다.

      **[!UICONTROL Pause]**&#x200B;을(를) 클릭하면 진행 중인 작업이 **[!UICONTROL are not]** 일시 중지되지만 다음 다시 시작할 때까지 다른 활동이 시작되지 않습니다.

      ![](assets/s_user_segmentation_pause.png)

      서버는 다음과 같이 해당 상태를 확인하면서 명령을 고려합니다.

      ![](assets/s_user_segmentation_pause_status.png)

      특정 활동에 도달하면 타깃팅 워크플로우가 자동으로 일시 중지될 수도 있습니다. 이렇게 하려면 타깃팅 워크플로우를 일시 중지할 활동을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Enable but do not execute]**&#x200B;을 선택합니다.

      ![](assets/s_user_segmentation_donotexecute.png)

      이 구성은 특수 아이콘으로 표시됩니다.

      ![](assets/s_user_segmentation_pause_activity.png)

      >[!NOTE]
      >
      >이 옵션은 고급 타깃팅 캠페인 디자인 및 테스트 단계에서 유용합니다.

      **[!UICONTROL Start]**&#x200B;을 클릭하여 실행을 다시 시작합니다.

   * 진행 중인 실행을 중지하려면 **[!UICONTROL Stop]** 아이콘을 클릭합니다.

      ![](assets/s_user_segmentation_stop.png)

      서버는 다음과 같이 해당 상태를 확인하면서 명령을 고려합니다.

      ![](assets/s_user_segmentation_stop_status.png)
   실행이 활동에 도달하면 타깃팅 워크플로우를 자동으로 중지할 수도 있습니다. 이렇게 하려면 타깃팅 워크플로가 중지될 활동을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Do not activate]**&#x200B;을 선택합니다.

   ![](assets/s_user_segmentation_donotactivate.png)

   ![](assets/s_user_segmentation_unactivation.png)

   이 구성은 특수 아이콘으로 표시됩니다.

   >[!NOTE]
   >
   >이 옵션은 고급 타깃팅 캠페인 디자인 및 테스트 단계에서 유용합니다.

* 무조건적인 중단

   탐색기에서 **[!UICONTROL Administration > Production > Object created automatically > Campaign workflows]**&#x200B;을 선택하여 모든 캠페인 워크플로우에 액세스하고 작업합니다.

   **[!UICONTROL Actions]** 아이콘을 클릭하고 **[!UICONTROL Unconditional]** 중지를 선택하여 워크플로우를 무조건 중지할 수 있습니다. 이 작업은 캠페인 워크플로우가 종료됩니다.

   ![](assets/s_user_segmentation_stop_unconditional.png)

## 컨트롤 그룹 {#defining-a-control-group} 추가

제어 그룹은 배달을 받지 않는 모집단입니다.이 변수는 배달을 받은 타겟 모집단과 행동을 비교하여 배달 후 동작 및 캠페인 효과를 추적하는 데 사용됩니다.

제어 그룹은 기본 대상에서 추출하거나 특정 그룹 또는 쿼리에서 추출할 수 있습니다.

### 캠페인 {#activating-the-control-group-for-a-campaign}에 대한 제어 그룹 활성화

캠페인 수준에서 제어 그룹을 정의할 수 있습니다. 이 경우 제어 그룹이 해당 캠페인의 각 전달에 적용됩니다.

1. 필요한 캠페인을 편집하고 **[!UICONTROL Edit]** 탭을 클릭합니다.
1. **[!UICONTROL Advanced campaign settings]**&#x200B;을(를) 클릭합니다.

   ![](assets/s_ncs_user_edit_op_target.png)

1. **[!UICONTROL Enable and edit control group configuration]** 옵션을 선택합니다.
1. **[!UICONTROL Edit...]**&#x200B;을 클릭하여 제어 그룹을 구성합니다.

   ![](assets/s_ncs_user_edit_op_general_tab_exe_target.png)

구성 절차는 [기본 대상](#extracting-the-control-group-from-the-main-target) 및 [컨트롤 그룹 추가](#adding-a-population)에 있습니다.

### {#activating-the-control-group-for-a-delivery} 배달에 대한 제어 그룹 활성화

전달 수준에서 제어 그룹을 정의할 수 있습니다. 이 경우 제어 그룹이 해당 캠페인의 각 전달에 적용됩니다.

기본적으로 캠페인 수준에서 정의된 제어 그룹 구성은 해당 캠페인의 모든 게재에 적용됩니다. 하지만 개별 전달에 대해 제어 그룹을 조정할 수 있습니다.

>[!NOTE]
>
>캠페인에 대한 제어 그룹을 정의했고 이 캠페인에 연결된 게재에 대해서도 구성한 경우 게재에 대해 정의된 제어 그룹만 적용됩니다.

1. 필요한 배달을 편집한 다음 **[!UICONTROL Email parameters]** 섹션에서 **[!UICONTROL To]** 링크를 클릭합니다.

   ![](assets/s_ncs_user_edit_op_target_del.png)

1. **[!UICONTROL Control group]** 탭을 클릭한 다음 **[!UICONTROL Enable and edit control group configuration]**&#x200B;를 선택합니다.
1. **[!UICONTROL Edit...]**&#x200B;을 클릭하여 제어 그룹을 구성합니다.

구성 절차는 [기본 대상](#extracting-the-control-group-from-the-main-target) 및 [컨트롤 그룹 추가](#adding-a-population)에 있습니다.

### 기본 대상 {#extracting-the-control-group-from-the-main-target}에서 제어 그룹을 추출합니다.

전달의 기본 대상에서 수신자를 추출할 수 있습니다. 이 경우 받는 사람은 이 구성으로 영향을 받는 배달 작업의 대상에서 제거됩니다. 이 추출은 무작위이거나 수신자를 정렬한 결과일 수 있습니다.

![](assets/s_ncs_user_extract_from_target_population.png)

제어 그룹을 추출하려면 캠페인 또는 전달에 대한 제어 그룹을 활성화하고 다음 옵션 중 하나를 선택합니다.**[!UICONTROL Activate random sampling]** 또는 **[!UICONTROL Keep only the first records after sorting]**.

* **[!UICONTROL Activate random sampling]** :이 옵션은 타깃팅된 모집단에서 받는 사람에게 무작위 샘플링을 적용합니다. 그런 다음 임계값을 100으로 설정하면 제어 그룹은 타깃팅된 모집단에서 무작위로 선택된 100명의 수신자로 구성됩니다. 무작위 샘플링은 데이터베이스 엔진에 따라 다릅니다.
* **[!UICONTROL Keep only the first records after sorting]** : 이 옵션을 사용하면 하나 이상의 정렬 명령을 기준으로 제한을 정의할 수 있습니다. **[!UICONTROL Age]** 필드를 정렬 기준으로 선택한 다음 100을 임계값으로 정의하면 제어 그룹은 100명의 가장 어린 수신자로 구성됩니다. 예를 들어 구매를 거의 하지 않는 받는 사람 또는 구매를 자주 수행하는 받는 사람을 포함하는 제어 그룹을 정의하고 이러한 행동을 연락 받는 사람의 행동과 비교하는 것이 재미있을 수 있습니다.

**[!UICONTROL Next]**&#x200B;을 클릭하여 정렬 순서를 정의하고(필요한 경우) 수신자 제한 모드를 선택합니다.

![](assets/s_ncs_user_edit_op_target_param.png)

이 구성은 Workflow의 공유 활동과 같으며, 이를 통해 대상을 하위 세트로 분류할 수 있습니다. 제어 그룹은 이러한 하위 세트 중 하나입니다. 자세한 내용은 [이 섹션](../../workflow/using/architecture.md)을 참조하십시오.

### 새 모집단을 제어 그룹 {#adding-a-population}으로 사용

제어 그룹으로 사용할 새 모집단을 정의할 수 있습니다. 이 모집단은 수신자 그룹에서 가져올 수도 있고 특정 쿼리를 통해 만들 수도 있습니다.

![](assets/s_ncs_user_add_to_target_population.png)

>[!NOTE]
>
>Adobe Campaign 쿼리 편집기는 [이 섹션](../../workflow/using/query.md)에 있습니다.


#### 자습서 비디오 {#create-email-video}

이 비디오에서는 Adobe Campaign에서 캠페인 및 이메일을 만드는 방법을 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

추가 캠페인 방법 비디오는 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.