---
product: campaign
title: Campaign 폴더 액세스 관리
description: Campaign 폴더에 대한 액세스 권한을 부여하고 보기를 만드는 방법을 알아봅니다
badge: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: Application Settings, Permissions
role: User, Admin
level: Beginner
exl-id: 0ba8a3d0-36d7-42f3-b281-0255e49b5fa3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 1%

---

# 폴더 액세스 관리{#folder-access-management}



Explorer 탐색 트리의 각 폴더에는 읽기, 쓰기 및 삭제 액세스 권한이 첨부되어 있습니다. 파일에 액세스하려면 연산자 또는 연산자 그룹은 최소한 파일에 대한 읽기 액세스 권한을 가져야 합니다.

## 폴더 및 보기 {#folders-and-views}

### 폴더란? {#about-folders}

폴더는 Adobe Campaign 트리의 노드입니다. 이러한 노드는 트리를 마우스 오른쪽 버튼으로 클릭하고 **[!UICONTROL Add new folder]** 메뉴 아래의 제품에서 사용할 수 있습니다. 기본적으로 첫 번째 메뉴에서는 현재 컨텍스트에 해당하는 폴더를 추가할 수 있습니다.

![](assets/s_ncs_user_add_folder_in_tree.png)

Explorer 탐색 트리를 사용자 지정할 수 있습니다. 구성 단계 및 모범 사례 알아보기 [이 섹션에서](adobe-campaign-workspace.md).

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

아래 예에서는 특정 데이터를 표시하는 새 폴더를 만들겠습니다.

1. 새로 만들기 **[!UICONTROL Deliveries]** 폴더를 입력하고 이름을 지정합니다. **게재 프랑스**.
1. 이 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_add_folder_exple.png)

1. **[!UICONTROL Restriction]** 탭에서 **[!UICONTROL This folder is a view]**&#x200B;를 선택합니다. 그러면 데이터베이스의 모든 게재가 표시됩니다.

   ![](assets/s_ncs_user_add_folder_exple01.png)

1. 창의 중간 섹션에 있는 쿼리 편집기에서 게재 필터 기준을 정의합니다. 그러면 정의된 필터에 해당하는 캠페인이 표시됩니다.

   >[!NOTE]
   >
   >쿼리 편집기는에 표시됩니다. [이 섹션](../../platform/using/about-queries-in-campaign.md).

   다음 필터 조건 사용:

![](assets/s_ncs_user_add_folder_exple00.png)

보기에 다음 게재가 표시됩니다.

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>관리 시 [트랜잭션 메시지](../../message-center/using/about-transactional-messaging.md) events, **[!UICONTROL Real time events]** 또는 **[!UICONTROL Batch events]** 폴더는 액세스 권한 문제가 발생할 수 있으므로 실행 인스턴스에 대한 보기로 설정하지 말아야 합니다. 이벤트 컬렉션에 대한 자세한 내용은 [이 섹션](../../message-center/using/about-event-processing.md#event-collection).

## 폴더에 대한 권한

### 폴더에 대한 권한 편집 {#edit-permissions-on-a-folder}

트리의 특정 폴더에 대한 권한을 편집하려면 아래 단계를 따르십시오.

1. 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_folder_properties.png)

1. 다음을 클릭합니다. **[!UICONTROL Security]** 이 폴더에 대한 권한을 보려면 탭하십시오.

   ![](assets/s_ncs_user_folder_properties_security.png)

### 권한 수정 {#modify-permissions}

권한을 수정하려면 다음을 수행합니다.

* **그룹 또는 연산자 바꾸기**. 이렇게 하려면 폴더에 대한 권한이 있는 그룹(또는 연산자) 중 하나를 클릭하고 드롭다운 목록에서 새 그룹(또는 새 연산자)을 선택합니다.

   ![](assets/s_ncs_user_folder_properties_security02.png)

* **그룹 또는 운영자 승인**. 이렇게 하려면 **[!UICONTROL Add]** 버튼을 클릭하고 이 폴더에 권한을 할당할 그룹 또는 연산자를 선택합니다.
* **그룹 또는 연산자 금지**. 이렇게 하려면 다음을 클릭하십시오. **[!UICONTROL Delete]** 이 폴더에 대한 인증을 제거할 그룹 또는 연산자를 선택합니다.
* **그룹 또는 연산자에 할당된 권한 선택**. 이렇게 하려면 관련 그룹 또는 연산자를 클릭한 다음 부여할 액세스 권한을 선택하고 나머지 권한은 선택 해제합니다.

   ![](assets/s_ncs_user_folder_properties_security03.png)

### 권한 전파 {#propagate-permissions}

권한 부여 및 액세스 권한을 전파할 수 있습니다. 이렇게 하려면 **[!UICONTROL Propagate]** 폴더 속성의 옵션입니다.

이 창에서 정의된 권한이 현재 노드의 모든 하위 폴더에 적용됩니다. 그런 다음 각 하위 폴더에 대해 이러한 권한을 오버로드할 수 있습니다.

>[!NOTE]
>
>폴더에 대해 이 옵션을 지우면 하위 폴더에 대해 자동으로 지워지지 않습니다. 각 하위 폴더에 대해 명시적으로 지워야 합니다.

### 모든 운영자에게 액세스 권한 부여 {#grant-access-to-all-operators}

다음에서 **[!UICONTROL Security]** 탭입니다. **[!UICONTROL System folder]** 옵션을 선택하면 해당 권한에 관계없이 모든 연산자가 이 데이터에 액세스할 수 있습니다. 이 옵션을 선택하지 않은 경우 운영자(또는 해당 그룹)가 액세스할 수 있도록 승인 목록에 명시적으로 추가해야 합니다.

![](assets/s_ncs_user_folder_properties_security03b.png)
