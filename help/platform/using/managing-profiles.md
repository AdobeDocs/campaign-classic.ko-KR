---
product: campaign
title: 프로필 관리
description: 프로필 관리
feature: Profiles
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
hide: true
hidefromtoc: true
source-git-commit: 471018f09e5a14635fcce07aeca1e2cf48d9144f
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 2%

---

# 프로필 관리{#managing-profiles}



## 수신자 트리 {#recipient-tree}

고급 수신자 관리 기능에 액세스하려면 Adobe Campaign 트리를 편집해야 합니다. 이렇게 하려면 도구 모음에서 **[!UICONTROL Explorer]** 단추를 클릭합니다.

기본적으로 수신자는 Adobe Campaign 트리의 **[!UICONTROL Profiles and targets]** 노드에 저장됩니다. 동일한 노드에서 한 개 이상의 폴더 및 하위 폴더를 만들어 수신자 프로필을 저장할 수 있습니다.

각 노드는 폴더와 일치합니다. 각 폴더의 데이터는 서로 분할된 것으로 간주되어야 합니다. 즉, 여러 수신자 폴더의 경우 중복 요소 관리가 더 까다로워집니다.

>[!NOTE]
>
> * 데이터베이스에 있는 모든 수신자 목록을 표시하려면 뷰를 만들어야 합니다. [폴더 및 보기](../../platform/using/access-management-folders.md)에서 자세히 알아보세요.
> * 프로필 관리 방법에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}를 참조하세요.


<!--
## Move recipients {#moving-recipients}

You can select one or more recipients, drag them from the recipient list, and drop them in the desired folder. A warning message asks you to confirm this action.

## Copy a recipient {#copying-a-recipient}

You can copy a recipient in the same folder by right-clicking the desired recipient and selecting **[!UICONTROL Copy]**.

## Delete recipients {#deleting-recipients}

To delete recipients, move them to a specific folder and then purge the content of this folder. It is **strongly recommended not to use** the **[!UICONTROL Delete]** option in this case.

To purge a folder, use the **[!UICONTROL Actions > Purge folder]** menu, accessed by right-clicking the desired folder.

![](assets/s_ncs_user_purge_folder.png)

Click **[!UICONTROL Start]** to launch the operation. The middle section of the window displays the progress status, as shown below:

![](assets/s_ncs_user_purge_folder_start.png)
-->