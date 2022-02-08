---
product: campaign
title: 워크플로우를 사용하여 프로필 목록 만들기
description: 워크플로우에서 프로필 목록을 만드는 방법을 알아봅니다
feature: Workflows
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 10%

---

# 워크플로우를 사용하여 프로필 목록 만들기{#creating-a-profile-list-with-a-workflow}

![](../../assets/common.svg)

을(를) 만들려면 **[!UICONTROL List]** 새 수신자 테이블을 기반으로 목록을 입력하면 목록을 생성할 타겟팅 워크플로우를 만들어야 합니다.

Campaign의 목록에 대한 자세한 내용은 [이 섹션](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

사용자 지정 수신자 테이블에서 타겟팅 워크플로우를 만들고 수신자를 업데이트하려면 아래 단계를 따르십시오.

1. 로 이동합니다. **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** 노드 아래에 있는 노드 아래에 있는 노드 아래에 있는 노드 아래에 있는 노드 아래에 있는 노드 아래에 있는 노드 이름을 지정합니다.
1. 새 타겟팅 워크플로우를 만듭니다.
1. 배치 **쿼리** 활동 다음에 **목록 업데이트** 활동.

   ![](assets/mapping_create_list_workflow01.png)

1. 를 두 번 클릭합니다. **쿼리** 활동을 클릭한 다음 **[!UICONTROL Edit the query]** 새 수신자 테이블의 스키마를 기반으로 타겟팅 차원을 선택하려면 다음을 수행하십시오. **개인**). 클릭 **[!UICONTROL Finish]** 확인합니다.

   ![](assets/mapping_create_list_workflow03.png)

1. 를 두 번 클릭합니다. **목록 업데이트** 활동을 선택한 다음 **[!UICONTROL Create the list if necessary (Computed name)]** 라디오 단추입니다.

   ![](assets/mapping_create_list_workflow02.png)

1. 새 목록에 대한 만들기 폴더를 선택합니다.
1. 워크플로우를 실행하여 목록을 만듭니다.
1. 다음 중 선택한 트리의 노드에서 결과를 확인합니다. **[!UICONTROL List update]** 활동.

   대시보드는 아래와 같이 목록이 기반으로 하는 스키마를 지정합니다.

   ![](assets/mapping_list_view.png)
