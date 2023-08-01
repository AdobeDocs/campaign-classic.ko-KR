---
product: campaign
title: 프로필 관리
description: 프로필 관리
feature: Profiles
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 2%

---

# 프로필 관리{#managing-profiles}



## 수신자 트리 {#recipient-tree}

고급 수신자 관리 기능에 액세스하려면 Adobe Campaign 트리를 편집해야 합니다. 이렇게 하려면 **[!UICONTROL Explorer]** 단추를 클릭합니다.

기본적으로 수신자는 **[!UICONTROL Profiles and targets]** Adobe Campaign 트리의 노드입니다. 동일한 노드에서 한 개 이상의 폴더 및 하위 폴더를 만들어 수신자 프로필을 저장할 수 있습니다.

각 노드는 폴더와 일치합니다. 각 폴더의 데이터는 서로 분할된 것으로 간주되어야 합니다. 즉, 여러 수신자 폴더의 경우 중복 요소 관리가 더 까다로워집니다.

>[!NOTE]
>
>데이터베이스에 있는 모든 수신자 목록을 표시하려면 뷰를 만들어야 합니다. 다음에서 자세히 알아보기 [폴더 및 보기](../../platform/using/access-management-folders.md).

## 수신자 이동 {#moving-recipients}

수신자를 한 명 이상 선택하고 수신자 목록에서 드래그하여 원하는 폴더에 놓을 수 있습니다. 이 작업을 확인하라는 경고 메시지가 표시됩니다.

## 수신자 복사 {#copying-a-recipient}

원하는 수신자를 마우스 오른쪽 단추로 클릭하고 를 선택하여 동일한 폴더에 있는 수신자를 복사할 수 있습니다 **[!UICONTROL Copy]**.

## 수신자 삭제 {#deleting-recipients}

수신자를 삭제하려면 수신자를 특정 폴더로 이동한 다음 이 폴더의 콘텐츠를 제거하십시오. 다음과 같습니다. **를 사용하지 않는 것이 좋습니다.** 다음 **[!UICONTROL Delete]** 이 경우 옵션입니다.

폴더를 제거하려면 **[!UICONTROL Actions > Purge folder]** 메뉴, 원하는 폴더를 마우스 오른쪽 단추로 클릭하여 액세스할 수 있습니다.

![](assets/s_ncs_user_purge_folder.png)

클릭 **[!UICONTROL Start]** 을 눌러 작업을 실행합니다. 창의 중간 섹션에는 진행률 상태가 아래와 같이 표시됩니다.

![](assets/s_ncs_user_purge_folder_start.png)
