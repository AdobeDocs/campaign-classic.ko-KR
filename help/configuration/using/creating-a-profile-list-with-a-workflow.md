---
title: 워크플로우를 사용하여 프로필 목록 만들기
seo-title: 워크플로우를 사용하여 프로필 목록 만들기
description: 워크플로우를 사용하여 프로필 목록 만들기
seo-description: null
page-status-flag: never-activated
uuid: a30f7217-fe82-4290-b1e6-e7a126a316c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ba42c3cf-31fc-4fbc-b230-a2b3982328c5
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 19%

---


# 워크플로우를 사용하여 프로필 목록 만들기{#creating-a-profile-list-with-a-workflow}

새 수신자 테이블을 기반으로 **[!UICONTROL List]** 유형 목록을 만들려면 목록을 생성하는 타깃팅 워크플로우를 만들어야 합니다. Campaign의 목록에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

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

>[!NOTE]
>
>수신자 목록 [만들기 비디오를 참조할 수도](https://docs.adobe.com/content/help/ko-KR/campaign-classic-learn/tutorials/getting-started/creating-a-list-of-recipients.html) 있습니다.

