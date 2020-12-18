---
solution: Campaign Classic
product: campaign
title: 프로필 관리
description: 프로필 관리
audience: platform
content-type: reference
topic-tags: profile-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 2%

---


# 프로필 관리{#managing-profiles}

## 받는 사람 트리 {#recipient-tree}

고급 수신자 관리 기능에 액세스하려면 Adobe Campaign 트리를 편집해야 합니다. 이렇게 하려면 도구 모음에서 **[!UICONTROL Explorer]** 단추를 클릭합니다.

기본적으로 수신자는 Adobe Campaign 트리의 **[!UICONTROL Profiles and targets]** 노드에 저장됩니다. 동일한 노드에서 하나 이상의 폴더 및 하위 폴더를 만들어 수신자 프로필을 저장할 수 있습니다.

각 노드가 폴더와 일치합니다. 각 폴더의 데이터는 서로 분할된 것으로 간주되어야 합니다. 즉, 여러 수신자 폴더에 대해 두 배 관리가 더 까다로워집니다.

>[!NOTE]
>
>데이터베이스에 있는 모든 받는 사람 목록을 표시하려면 뷰를 만들어야 합니다. [폴더 및 보기](../../platform/using/access-management.md#folders-and-views)를 참조하십시오.

## 받는 사람 이동 중 {#moving-recipients}

수신자를 하나 이상 선택하고 수신자 목록에서 수신자를 드래그하여 원하는 폴더에 놓을 수 있습니다. 이 작업을 확인하는 경고 메시지가 표시됩니다.

## 받는 사람 {#copying-a-recipient} 복사

원하는 수신자를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Copy]**&#x200B;을 선택하여 동일한 폴더에 있는 수신자를 복사할 수 있습니다.

## 받는 사람 {#deleting-recipients} 삭제

받는 사람을 삭제하려면 받는 사람을 특정 폴더로 이동한 다음 이 폴더의 콘텐트를 제거합니다. 이 경우에는 **이(가)**[!UICONTROL Delete]**옵션을 사용하지 않는 것이 좋습니다.**

폴더를 삭제하려면 원하는 폴더를 마우스 오른쪽 단추로 클릭하여 액세스하는 **[!UICONTROL Actions > Purge folder]** 메뉴를 사용합니다.

![](assets/s_ncs_user_purge_folder.png)

**[!UICONTROL Start]**&#x200B;을 클릭하여 작업을 시작합니다. 창의 가운데 섹션은 아래와 같이 진행 상태를 표시합니다.

![](assets/s_ncs_user_purge_folder_start.png)

