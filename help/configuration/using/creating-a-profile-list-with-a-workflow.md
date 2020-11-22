---
solution: Campaign Classic
product: campaign
title: 워크플로우를 사용하여 프로필 목록 만들기
description: 워크플로우에서 프로필 목록을 만드는 방법 살펴보기
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 10%

---


# 워크플로우를 사용하여 프로필 목록 만들기{#creating-a-profile-list-with-a-workflow}

새 수신자 테이블을 기반으로 **[!UICONTROL List]** 유형 목록을 만들려면 목록을 생성하는 타깃팅 워크플로우를 만들어야 합니다.

Campaign의 목록에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

타깃팅 워크플로우를 만들고 사용자 지정 수신자 테이블에서 수신자를 업데이트하려면 아래 단계를 따르십시오.

1. 탐색기의 **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** 노드로 이동합니다.
1. 새 타깃팅 워크플로우를 만듭니다.
1. 쿼리 **활동** 뒤에 목록 업데이트 **활동을** 배치합니다.

   ![](assets/mapping_create_list_workflow01.png)

1. 쿼리 **활동** 을 두 번 클릭한 다음 **[!UICONTROL Edit the query]** 을 클릭하여 새 수신자 테이블의 스키마를 기반으로 타게팅 차원을 선택합니다(예: **개인**). 을 **[!UICONTROL Finish]** 클릭하여 확인합니다.

   ![](assets/mapping_create_list_workflow03.png)

1. 목록 업데이트 **활동을 두 번** 클릭한 다음 **[!UICONTROL Create the list if necessary (Computed name)]** 라디오 단추를 선택합니다.

   ![](assets/mapping_create_list_workflow02.png)

1. 새 목록에 사용할 만들기 폴더를 선택합니다.
1. 워크플로우를 실행하여 목록을 만듭니다.
1. 활동 중에 선택한 트리 노드에서 결과를 **[!UICONTROL List update]** 봅니다.

   대시보드는 아래와 같이 목록이 기반으로 하는 스키마를 지정합니다.

   ![](assets/mapping_list_view.png)


