---
product: campaign
title: 워크플로를 사용하여 프로필 목록 만들기
description: 워크플로우에서 프로필 목록을 만드는 방법을 알아봅니다
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Workflows, Profiles
role: User
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 11%

---

# 워크플로를 사용하여 프로필 목록 만들기{#creating-a-profile-list-with-a-workflow}


새 받는 사람 테이블을 기반으로 **[!UICONTROL List]** 형식 목록을 만들려면 목록을 생성할 타깃팅 워크플로우를 만들어야 합니다.

Campaign의 목록에 대한 자세한 내용은 [이 섹션](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign)을 참조하세요.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

타겟팅 워크플로우를 만들고 사용자 지정 수신자 테이블에서 수신자를 업데이트하려면 아래 단계를 수행합니다.

1. 탐색기의 **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** 노드로 이동합니다.
1. 새 타겟팅 워크플로우를 만듭니다.
1. **쿼리** 활동 뒤에 **목록 업데이트** 활동을 넣으십시오.

   ![](assets/mapping_create_list_workflow01.png)

1. **쿼리** 활동을 두 번 클릭한 다음 **[!UICONTROL Edit the query]**&#x200B;을(를) 클릭하여 새 수신자 테이블의 스키마를 기준으로 타겟팅 차원을 선택합니다(예: **개인**). **[!UICONTROL Finish]**&#x200B;을(를) 클릭하여 확인합니다.

   ![](assets/mapping_create_list_workflow03.png)

1. **목록 업데이트** 활동을 두 번 클릭한 다음 **[!UICONTROL Create the list if necessary (Computed name)]** 라디오 단추를 선택합니다.

   ![](assets/mapping_create_list_workflow02.png)

1. 새 목록의 생성 폴더를 선택합니다.
1. 워크플로우를 실행하여 목록을 만듭니다.
1. **[!UICONTROL List update]** 활동 중에 선택한 트리의 노드에서 결과를 봅니다.

   대시보드는 아래와 같이 목록의 기반이 되는 스키마를 지정합니다.

   ![](assets/mapping_list_view.png)
