---
product: campaign
title: 워크플로우를 사용하여 프로필 목록 만들기
description: 워크플로우에서 프로필 목록을 만드는 방법을 알아봅니다
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Workflows, Profiles
role: User
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 12%

---

# 워크플로우를 사용하여 프로필 목록 만들기{#creating-a-profile-list-with-a-workflow}


을(를) 만들려면 **[!UICONTROL List]** 새 수신자 테이블을 기반으로 목록을 입력합니다. 목록을 생성할 타겟팅 워크플로우를 만들어야 합니다.

Campaign 목록에 대한 자세한 내용은 [이 섹션](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

타겟팅 워크플로우를 만들고 사용자 지정 수신자 테이블에서 수신자를 업데이트하려면 아래 단계를 수행합니다.

1. 로 이동 **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** 탐색기의 노드입니다.
1. 새 타겟팅 워크플로우를 만듭니다.
1. 배치 **쿼리** 활동 뒤에 다음 **목록 업데이트** 활동.

   ![](assets/mapping_create_list_workflow01.png)

1. 를 두 번 클릭합니다. **쿼리** 활동을 클릭한 다음 **[!UICONTROL Edit the query]** 새 수신자 테이블의 스키마를 기준으로 타겟팅 차원을 선택하려면(이 예제에서는 다음 작업을 수행합니다. **개인**). **[!UICONTROL Finish]**&#x200B;을(를) 클릭하여 확인합니다.

   ![](assets/mapping_create_list_workflow03.png)

1. 를 두 번 클릭합니다. **목록 업데이트** 활동을 선택한 다음 **[!UICONTROL Create the list if necessary (Computed name)]** 라디오 단추.

   ![](assets/mapping_create_list_workflow02.png)

1. 새 목록의 생성 폴더를 선택합니다.
1. 워크플로우를 실행하여 목록을 만듭니다.
1. 을(를) 수행하는 동안 선택한 트리의 노드에서 결과 보기 **[!UICONTROL List update]** 활동.

   대시보드는 아래와 같이 목록의 기반이 되는 스키마를 지정합니다.

   ![](assets/mapping_list_view.png)
