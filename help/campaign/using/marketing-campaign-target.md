---
product: campaign
title: 마케팅 캠페인 타겟 대상자
description: 마케팅 캠페인 대상을 정의하는 방법 알아보기
role: User
feature: Campaigns, Audiences
exl-id: 04daa67c-4057-42a7-b993-a6eddf2b883d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 1%

---

# 캠페인 대상 선택 {#marketing-campaign-deliveries}

마케팅 캠페인에서 각 게재에 대해 다음을 정의할 수 있습니다.

* 대상자 - 자세한 내용 [워크플로우에서 대상자 만들기](#building-the-main-target-in-a-workflow) 및 [대상 모집단 선택](#selecting-the-target-population).
* 컨트롤 그룹 - 자세히 알아보기 [이 섹션](#defining-a-control-group).
* 시드 주소 - 자세한 내용 [이 섹션](../../delivery/using/about-seed-addresses.md).

이 정보 중 일부는 [캠페인 템플릿](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

게재 대상을 만들려면 데이터베이스에서 수신자에 대한 필터링 기준을 정의할 수 있습니다. 이 수신자 선택 모드는에 표시됩니다. [이 섹션](../../delivery/using/steps-defining-the-target-population.md).

## 그룹에 보내기

모집단을 목록으로 가져온 다음 게재에서 이 목록을 타겟팅할 수 있습니다. 이렇게 하려면 아래 단계를 수행합니다.

1. 관련 게재를 편집하고 **[!UICONTROL To]** 대상 모집단을 변경하는 링크입니다.

1. 다음에서 **[!UICONTROL Main target]** 탭에서 **[!UICONTROL Defined via the database]** 옵션 및 클릭 **[!UICONTROL Add]** 수신자를 선택합니다.

![](assets/s_user_target_group_add.png)

1. 선택 **[!UICONTROL A list of recipients]** 및 클릭 **[!UICONTROL Next]** 을 눌러 선택합니다.

![](assets/s_user_target_group_next.png)

## 캠페인 워크플로우에서 대상자 작성 {#building-the-main-target-in-a-workflow}

게재의 기본 대상은 캠페인 워크플로우에서도 정의할 수 있습니다. 이 그래픽 환경을 사용하면 쿼리, 테스트 및 연산자(결합, 중복 제거, 공유 등)를 사용하여 대상을 작성할 수 있습니다.

>[!IMPORTANT]
>
>캠페인에 28개 이상의 워크플로우를 추가해서는 안 됩니다. 이 제한을 초과하면 추가 워크플로우가 인터페이스에 표시되지 않고 오류를 생성할 수 있습니다.

### 워크플로 만들기 {#creating-a-targeting-workflow}

타겟팅은 워크플로우의 그래픽 시퀀스에서 필터링 조건의 조합을 통해 만들 수 있습니다. 요구 사항에 따라 타겟팅할 모집단과 하위 모집단을 만들 수 있습니다. 워크플로우 편집기를 표시하려면 **[!UICONTROL Targeting and workflows]** 캠페인 대시보드의 탭입니다.

![](assets/s_ncs_user_edit_op_wf_link.png)

대상 모집단은 워크플로우에 배치된 하나 이상의 쿼리를 통해 Adobe Campaign 데이터베이스에서 추출됩니다. 쿼리를 작성하는 방법에 대해 알아보려면 다음을 참조하십시오. [이 섹션](../../workflow/using/query.md).

유니온, 교차, 공유, 제외 등의 상자를 통해 쿼리를 시작하고 모집단을 공유할 수 있습니다.

작업공간 왼쪽에 있는 목록에서 객체를 선택하고 링크하여 대상을 구성합니다.

![](assets/s_ncs_user_edit_op_wf_tab_a.png)

다이어그램에서 대상 구성에 필요한 타깃팅 및 예약 쿼리를 다이어그램에 연결합니다. 구축이 진행되는 동안 타깃팅을 실행하여 데이터베이스에서 추출한 모집단을 확인할 수 있습니다.

>[!NOTE]
>
>쿼리를 정의하는 예제와 절차는에 나와 있습니다. [이 섹션](../../workflow/using/query.md).

편집기의 왼쪽 섹션에는 활동을 나타내는 그래픽 객체 라이브러리가 포함되어 있습니다. 첫 번째 탭에는 타깃팅 활동이 포함되어 있고 두 번째 탭에는 타깃팅 활동을 조정하는 데 간혹 사용되는 흐름 제어 활동이 포함되어 있습니다.

타겟팅 워크플로우 실행 및 서식 지정 기능은 다이어그램 편집기 도구 모음을 통해 액세스할 수 있습니다.

![](assets/s_user_campaign_segmentation05.png)

>[!NOTE]
>
>다이어그램을 빌드하는 데 사용할 수 있는 활동과 모든 디스플레이 및 레이아웃 기능은 [워크플로우로 자동화](../../workflow/using/architecture.md) 가이드.

단일 캠페인에 대해 여러 타겟팅 워크플로우를 만들 수 있습니다. 워크플로우를 추가하려면 다음 작업을 수행하십시오.

1. 워크플로우 만들기 영역의 왼쪽 상단 섹션으로 이동하여 마우스 오른쪽 버튼을 클릭하고 을 선택합니다. **[!UICONTROL Add]**. 다음을 사용할 수도 있습니다 **[!UICONTROL New]** 이 영역 위에 있는 단추입니다.

   ![](assets/s_ncs_user_add_a_wf.png)

1. 다음 항목 선택 **[!UICONTROL New workflow]** 템플릿을 만들고 이 워크플로의 이름을 지정합니다.
1. 클릭 **[!UICONTROL OK]** 을 클릭하여 워크플로 만들기를 확인한 다음 이 워크플로에 대한 다이어그램을 만듭니다.

### 워크플로우 실행 {#executing-a-workflow}

타겟팅 워크플로우는 **[!UICONTROL Start]** 적절한 권한이 있는 경우 도구 모음의 버튼입니다.

타겟팅은 스케줄(스케줄러) 또는 이벤트(외부 신호, 파일 가져오기 등)에 따라 자동 실행을 위해 프로그래밍될 수 있다.

타겟팅 워크플로우 실행과 관련된 작업(실행, 중지, 일시 중지 등) 은(는) **비동기** 프로세스: 명령이 저장되고 서버가 명령을 적용할 수 있는 즉시 적용됩니다.

도구 모음 아이콘을 사용하면 타겟팅 워크플로우 실행에 관한 작업을 수행할 수 있습니다.

* 시작 또는 재시작

   * 다음 **[!UICONTROL Start]** 아이콘을 사용하면 타겟팅 워크플로우를 시작할 수 있습니다. 이 아이콘을 클릭하면 입력 전환이 없는 모든 활동이 활성화됩니다(끝점 이동 제외).

     ![](assets/s_user_segmentation_start.png)

     서버는 상태와 같이 요청을 고려합니다.

     ![](assets/s_user_segmentation_start_status.png)

     프로세스 상태가 다음으로 변경됨 **[!UICONTROL Started]**.

   * 적절한 도구 모음 아이콘을 통해 타겟팅 워크플로우를 다시 시작할 수 있습니다. 이 명령은 다음과 같은 경우에 유용합니다. **[!UICONTROL Start]** 예를 들어 타겟팅 워크플로우 중지가 진행 중인 경우 아이콘을 사용할 수 없습니다. 이 경우 **[!UICONTROL Restart]** 다시 시작을 예상하는 아이콘입니다. 서버는 상태가 다음과 같이 요청을 고려합니다.

     ![](assets/s_user_segmentation_restart_status.png)

     그런 다음 프로세스가 **[!UICONTROL Started]** 상태.

* 중지 또는 일시 중지

   * 도구 모음 아이콘을 사용하면 진행 중인 타겟팅 워크플로우를 중지하거나 일시 중지할 수 있습니다.

     다음을 클릭: **[!UICONTROL Pause]**, 작업 진행 중 **[!UICONTROL are not]** 일시 중지되었지만 다음 다시 시작할 때까지 다른 활동이 실행되지 않습니다.

     ![](assets/s_user_segmentation_pause.png)

     서버는 상태가 다음과 같이 명령을 고려합니다.

     ![](assets/s_user_segmentation_pause_status.png)

     타겟팅 워크플로우 실행이 특정 활동에 도달하면 자동으로 일시 중지할 수도 있습니다. 이렇게 하려면 타겟팅 워크플로우를 일시 중지할 활동을 마우스 오른쪽 단추로 클릭하고 를 선택합니다 **[!UICONTROL Enable but do not execute]**.

     ![](assets/s_user_segmentation_donotexecute.png)

     이 구성은 특수 아이콘으로 표시됩니다.

     ![](assets/s_user_segmentation_pause_activity.png)

     >[!NOTE]
     >
     >이 옵션은 고급 타겟팅 캠페인 디자인 및 테스트 단계 중에 유용합니다.

     클릭 **[!UICONTROL Start]** 실행을 다시 시작합니다.

   * 다음을 클릭합니다. **[!UICONTROL Stop]** ( 진행 중인 실행을 중지하는 아이콘)

     ![](assets/s_user_segmentation_stop.png)

     서버는 상태가 다음과 같이 명령을 고려합니다.

     ![](assets/s_user_segmentation_stop_status.png)

  실행이 활동에 도달하면 타겟팅 워크플로우를 자동으로 중지할 수도 있습니다. 이렇게 하려면 타겟팅 워크플로우가 중단될 활동을 마우스 오른쪽 버튼으로 클릭하고 을 선택합니다. **[!UICONTROL Do not activate]**.

  ![](assets/s_user_segmentation_donotactivate.png)

  ![](assets/s_user_segmentation_unactivation.png)

  이 구성은 특수 아이콘으로 표시됩니다.

  >[!NOTE]
  >
  >이 옵션은 고급 타겟팅 캠페인 디자인 및 테스트 단계 중에 유용합니다.

* 무조건 정지

  탐색기에서 **[!UICONTROL Administration > Production > Object created automatically > Campaign workflows]** 모든 캠페인 워크플로우에 액세스하고 작업을 수행합니다.

  다음을 클릭하여 워크플로를 무조건 중단할 수 있습니다. **[!UICONTROL Actions]** 아이콘 및 선택 **[!UICONTROL Unconditional]** 멈춰. 이 작업은 캠페인 워크플로우를 종료합니다.

  ![](assets/s_user_segmentation_stop_unconditional.png)

## 컨트롤 그룹 추가 {#defining-a-control-group}

컨트롤 그룹은 게재를 받지 않는 모집단으로, 게재를 받은 대상 모집단의 행동과 비교하여 게재 후 행동 및 캠페인 영향을 추적하는 데 사용됩니다.

컨트롤 그룹은 주 대상에서 추출되거나 특정 그룹 또는 쿼리에서 추출될 수 있습니다.

### 캠페인에 대한 컨트롤 그룹 활성화 {#activating-the-control-group-for-a-campaign}

캠페인 수준에서 컨트롤 그룹을 정의할 수 있습니다. 이 경우 컨트롤 그룹은 해당 캠페인의 각 게재에 적용됩니다.

1. 관련 캠페인을 편집하고 **[!UICONTROL Edit]** 탭.
1. **[!UICONTROL Advanced campaign settings]**&#x200B;를 클릭합니다.

   ![](assets/s_ncs_user_edit_op_target.png)

1. 다음 항목 선택 **[!UICONTROL Enable and edit control group configuration]** 옵션을 선택합니다.
1. 클릭 **[!UICONTROL Edit...]** 컨트롤 그룹을 구성합니다.

   ![](assets/s_ncs_user_edit_op_general_tab_exe_target.png)

구성 절차는에 나와 있습니다. [주 대상에서 컨트롤 그룹 추출](#extracting-the-control-group-from-the-main-target) 및 [컨트롤 그룹 추가](#adding-a-population).

### 게재에 대한 컨트롤 그룹 활성화 {#activating-the-control-group-for-a-delivery}

게재 수준에서 컨트롤 그룹을 정의할 수 있습니다. 이 경우 컨트롤 그룹은 관련 캠페인의 각 게재에 적용됩니다.

기본적으로 캠페인 수준에서 정의된 컨트롤 그룹 구성은 해당 캠페인의 모든 게재에 적용됩니다. 그러나 개별 게재에 대해 컨트롤 그룹을 조정할 수 있습니다.

>[!NOTE]
>
>캠페인에 대한 컨트롤 그룹을 정의했으며 이 캠페인에 연결된 게재에도 구성한 경우 게재에 대해 정의된 컨트롤 그룹만 적용됩니다.

1. 관련 게재를 편집한 다음 **[!UICONTROL To]** 링크 **[!UICONTROL Email parameters]** 섹션.

   ![](assets/s_ncs_user_edit_op_target_del.png)

1. 다음을 클릭합니다. **[!UICONTROL Control group]** 탭을 누른 다음 선택 **[!UICONTROL Enable and edit control group configuration]**.
1. 클릭 **[!UICONTROL Edit...]** 컨트롤 그룹을 구성합니다.

구성 절차는에 나와 있습니다. [주 대상에서 컨트롤 그룹 추출](#extracting-the-control-group-from-the-main-target) 및 [컨트롤 그룹 추가](#adding-a-population).

### 주 대상에서 컨트롤 그룹 추출 {#extracting-the-control-group-from-the-main-target}

게재의 기본 대상에서 수신자를 추출할 수 있습니다. 이 경우 수신자는 이 구성의 영향을 받는 게재 작업 대상에서 제거됩니다. 이 추출은 무작위적이거나 수신자를 정렬한 결과일 수 있습니다.

![](assets/s_ncs_user_extract_from_target_population.png)

컨트롤 그룹을 추출하려면 캠페인 또는 게재에 대해 컨트롤 그룹을 활성화하고 다음 옵션 중 하나를 선택합니다. **[!UICONTROL Activate random sampling]** 또는 **[!UICONTROL Keep only the first records after sorting]**.

* **[!UICONTROL Activate random sampling]** : 이 옵션은 타깃팅된 모집단의 수신자에게 무작위 샘플링을 적용합니다. 그런 다음 임계값을 100으로 설정하면 대상 모집단에서 임의로 선택한 100명의 수신자로 컨트롤 그룹이 구성됩니다. 임의 샘플링은 데이터베이스 엔진에 따라 다릅니다.
* **[!UICONTROL Keep only the first records after sorting]** : 이 옵션을 사용하면 하나 이상의 정렬 명령을 기준으로 제한을 정의할 수 있습니다. 을(를) 선택하는 경우 **[!UICONTROL Age]** 필드를 정렬 기준으로 사용하고 100을 임계값으로 정의하면 컨트롤 그룹은 가장 최연소 수신자 100명으로 구성됩니다. 예를 들어 구매 횟수가 적은 수신자 또는 빈번한 구매를 수행하는 수신자를 포함하는 컨트롤 그룹을 정의하고, 해당 동작을 연락한 수신자의 행동과 비교하는 것이 좋습니다.

클릭 **[!UICONTROL Next]** 필요한 경우 정렬 순서를 정의하고 수신자 제한 모드를 선택합니다.

![](assets/s_ncs_user_edit_op_target_param.png)

이 구성은 타겟을 하위 집합으로 나눌 수 있는 워크플로우의 공유 활동과 같습니다. 컨트롤 그룹은 이러한 하위 집합 중 하나입니다. 다음을 참조하십시오. [이 섹션](../../workflow/using/architecture.md) 추가 정보.

### 새 모집단을 컨트롤 그룹으로 사용 {#adding-a-population}

컨트롤 그룹으로 사용할 새 모집단을 정의할 수 있습니다. 이 모집단은 수신자 그룹에서 가져오거나 특정 쿼리를 통해 만들 수 있습니다.

![](assets/s_ncs_user_add_to_target_population.png)

>[!NOTE]
>
>Adobe Campaign 쿼리 편집기는에 표시됩니다. [이 섹션](../../workflow/using/query.md).


#### 튜토리얼 비디오 {#create-email-video}

이 비디오에서는 Adobe Campaign에서 캠페인 및 이메일을 만드는 방법을 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

추가 캠페인 방법 비디오를 사용할 수 있습니다 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko).
