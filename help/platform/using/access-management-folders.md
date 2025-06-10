---
product: campaign
title: Campaign 폴더 액세스 관리
description: Campaign 폴더에 대한 액세스 권한을 부여하고 보기를 만드는 방법을 알아봅니다
badge: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: Application Settings, Permissions
role: User, Admin
level: Beginner
exl-id: 0ba8a3d0-36d7-42f3-b281-0255e49b5fa3
source-git-commit: 6e83067cef2b08b5bee37610bfef515714756ada
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 2%

---

# 폴더 액세스 관리{#folder-access-management}



Explorer 탐색 트리의 각 폴더에는 읽기, 쓰기 및 삭제 액세스 권한이 첨부되어 있습니다. 파일에 액세스하려면 연산자 또는 연산자 그룹은 최소한 파일에 대한 읽기 액세스 권한을 가져야 합니다.

>[!NOTE]
>
>폴더 권한에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}를 참조하세요.


## 폴더 및 보기 {#folders-and-views}

### 폴더란? {#about-folders}

폴더는 Adobe Campaign 트리의 노드입니다. 이러한 노드는 **[!UICONTROL Add new folder]** 메뉴를 통해 트리를 마우스 오른쪽 단추로 클릭하여 만듭니다. 기본적으로 첫 번째 메뉴에서는 현재 컨텍스트에 해당하는 폴더를 추가할 수 있습니다.

![](assets/s_ncs_user_add_folder_in_tree.png)

Explorer 탐색 트리를 사용자 지정할 수 있습니다. 구성 단계 및 모범 사례를 이 섹션[&#128279;](adobe-campaign-workspace.md)에서 알아봅니다.

### 보기란 무엇입니까? {#about-views}

또한 뷰를 만들어 데이터에 대한 액세스를 제한하고 요구 사항에 맞게 트리의 콘텐츠를 구성할 수 있습니다. 그런 다음 보기에 권한을 할당할 수 있습니다.

뷰는 동일한 유형의 하나 이상의 다른 폴더에 물리적으로 저장된 레코드를 표시하는 폴더입니다. 예를 들어, 보기인 Campaign 폴더를 만들면 데이터베이스에 있는 모든 캠페인이 기본적으로 표시됩니다. 그런 다음 이 데이터를 필터링할 수 있습니다.

폴더를 보기로 변환하면 데이터베이스에 있는 폴더 유형에 해당하는 모든 데이터가 저장된 폴더와 관계없이 보기에 표시됩니다. 그런 다음 필터링하여 표시되는 데이터 목록을 제한할 수 있습니다.

>[!IMPORTANT]
>
>뷰에는 데이터가 포함되어 있으며 이에 대한 액세스 권한을 제공하지만 데이터는 실제로 뷰 폴더에 저장되지 않습니다. 연산자는 데이터 소스 폴더에서 원하는 작업에 대해 적절한 권한이 있어야 합니다(최소 읽기 액세스 권한).
>
>소스 폴더에 대한 액세스 권한을 부여하지 않고 보기에 대한 액세스 권한을 부여하려면 소스 폴더의 상위 노드에 대한 읽기 액세스 권한을 부여하지 마십시오.

뷰를 폴더와 구별하기 위해 각 뷰의 이름이 다른 색상(짙은 녹청)으로 표시됩니다.

![](assets/s_ncs_user_view_name_color.png)

### 폴더 추가 및 보기 만들기 {#adding-folders-and-creating-views}

>[!IMPORTANT]
>
>기본 제공 폴더는 보기로 표시해서는 안 됩니다.


아래 예에서는 특정 데이터를 표시하는 새 폴더를 만들겠습니다.

1. 새 **[!UICONTROL Deliveries]** 유형 폴더를 만들고 이름을 **Deliveries France**&#x200B;로 지정합니다.
1. 이 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Properties...]**&#x200B;을(를) 선택합니다.

   ![속성을 마우스 오른쪽 단추로 클릭하는 스크린샷](assets/s_ncs_user_add_folder_exple.png)

1. **[!UICONTROL Restriction]** 탭에서 **[!UICONTROL This folder is a view]**&#x200B;을(를) 선택합니다. 그러면 데이터베이스의 모든 게재가 표시됩니다.

   ![확인 중인 보기 상자를 표시하는 화면](assets/s_ncs_user_add_folder_exple01.png)

1. 창의 중간 섹션에 있는 쿼리 편집기에서 게재 필터 기준을 정의합니다. 그러면 정의된 필터에 해당하는 캠페인이 표시됩니다.

   >[!NOTE]
   >
   >쿼리 편집기가 [이 섹션](../../platform/using/about-queries-in-campaign.md)에 표시됩니다.

   다음 필터 조건 사용:

![다른 필터 조건을 보여 주는 스크린샷](assets/s_ncs_user_add_folder_exple00.png)

보기에 다음 게재가 표시됩니다.

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>[트랜잭션 메시지](../../message-center/using/about-transactional-messaging.md) 이벤트를 관리할 때 액세스 권한 문제로 이어질 수 있으므로 **[!UICONTROL Real time events]** 또는 **[!UICONTROL Batch events]** 폴더를 실행 인스턴스의 보기로 설정하지 않아야 합니다. 이벤트 컬렉션에 대한 자세한 내용은 [이 섹션](../../message-center/using/about-event-processing.md#event-collection)을 참조하세요.

<!--
## Permissions on a folder

### Edit permissions on a folder {#edit-permissions-on-a-folder}

To edit permissions on a specific folder of the tree, follow the steps below:

1. Right-click on the folder and select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_folder_properties.png)

1. Click the **[!UICONTROL Security]** tab to view authorizations on this folder.

   ![](assets/s_ncs_user_folder_properties_security.png)

### Modify permissions {#modify-permissions}

To modify permissions, you can:

* **Replace a group or an operator**. To do this, click one of the groups (or operators) with rights to the folder, and select a new group (or a new operator) from the drop-down list:

  ![](assets/s_ncs_user_folder_properties_security02.png)

* **Authorize a group or an operator**. To do this, click the **[!UICONTROL Add]** button and select the group or operator to which you want to assign authorizations for this folder.
* **Forbid a group or an operator**. To do this, click **[!UICONTROL Delete]** and select the group or operator from which you want to remove authorization for this folder.
* **Select the rights assigned to a group or an operator**. To do this, click the group or operator concerned, then select the access rights you want to grant and deselect the others.

  ![](assets/s_ncs_user_folder_properties_security03.png)

### Propagate permissions {#propagate-permissions}

You can propagate authorizations and access rights. To do this, select the **[!UICONTROL Propagate]** option in the folder properties.

The authorizations defined in this window will then be applied to all the sub-folders of the current node. You can then overload these authorizations for each of the sub-folders.

>[!NOTE]
>
>Clearing this option for a folder does not automatically clear it for the sub-folders. You must clear it explicitly for each of the sub-folders.

### Grant access to all operators {#grant-access-to-all-operators}

In the **[!UICONTROL Security]** tab, if the **[!UICONTROL System folder]** option is selected, all operators will have access to this data, regardless of their rights. If this option is cleared, you must explicitly add the operator (or their group) to the list of authorizations in order for them to have access.

![](assets/s_ncs_user_folder_properties_security03b.png)
-->