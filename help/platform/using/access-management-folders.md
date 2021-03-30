---
solution: Campaign Classic
product: campaign
title: 캠페인 폴더에 대한 액세스 관리
description: 캠페인 폴더에 대한 액세스 권한을 부여하고 보기를 만드는 방법을 알아봅니다.
feature: 응용 프로그램 설정
role: 비즈니스 전문가, 관리자
level: 초급
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 0%

---


# 폴더 액세스 관리{#folder-access-management}

탐색기 탐색 트리의 각 폴더에는 연결된 액세스 권한이 읽기, 쓰기 및 삭제됩니다. 파일에 액세스하려면 연산자 또는 연산자 그룹이 파일에 대한 읽기 권한을 적어도 가져야 합니다.

## 폴더 및 보기 {#folders-and-views}

### {#about-folders} 폴더란 무엇입니까?

폴더는 Adobe Campaign 트리의 노드입니다. 이러한 노드는 **[!UICONTROL Add new folder]** 메뉴를 통해 트리를 마우스 오른쪽 단추로 클릭하여 만들어집니다. 기본적으로 첫 번째 메뉴를 사용하면 현재 컨텍스트에 해당하는 폴더를 추가할 수 있습니다.

![](assets/s_ncs_user_add_folder_in_tree.png)

탐색기 탐색 트리를 사용자 정의할 수 있습니다. 이 섹션](adobe-campaign-workspace.md)에서 구성 단계 및 우수 사례 [에 대해 알아봅니다.

### {#about-views} 보기란 무엇입니까?

또한 데이터에 대한 액세스를 제한하고 트리 내용을 요구 사항에 맞게 구성하기 위해 보기를 만들 수 있습니다. 그런 다음 보기에 권한을 할당할 수 있습니다.

보기는 같은 유형의 다른 폴더 하나 이상에 물리적으로 저장되는 레코드를 표시하는 폴더입니다. 예를 들어 뷰인 캠페인 폴더를 만드는 경우 기본적으로 데이터베이스에 있는 모든 캠페인이 원점에 상관없이 표시됩니다. 그런 다음 이 데이터를 필터링할 수 있습니다.

폴더를 보기로 변환할 때 데이터베이스에 있는 폴더 유형에 해당하는 모든 데이터가 저장되는 폴더에 관계없이 뷰에 표시됩니다. 그런 다음 필터링하여 표시되는 데이터 목록을 제한할 수 있습니다.

>[!IMPORTANT]
>
>보기에는 데이터가 들어 있고 데이터에 대한 액세스 권한을 제공하지만 데이터는 보기 폴더에 물리적으로 저장되지 않습니다. 연산자는 데이터 소스 폴더에서 원하는 작업에 대한 적절한 권한을 가지고 있어야 합니다(읽기 액세스 최소).
>
>소스 폴더에 대한 액세스 권한을 부여하지 않고 뷰에 대한 액세스를 제공하려면 소스 폴더의 부모 노드에 대한 읽기 액세스 권한을 부여하지 마십시오.

뷰를 폴더와 구분하기 위해 각 보기의 이름이 다른 색상(어두운 영역)으로 표시됩니다.

![](assets/s_ncs_user_view_name_color.png)

### 폴더 추가 및 보기 만들기 {#adding-folders-and-creating-views}

아래 예에서는 특정 데이터를 표시하는 새 폴더를 만듭니다.

1. 새 **[!UICONTROL Deliveries]** 유형 폴더를 만들고 이름을 **배달 프랑스**&#x200B;로 지정합니다.
1. 이 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Properties...]**&#x200B;을 선택합니다.

   ![](assets/s_ncs_user_add_folder_exple.png)

1. **[!UICONTROL Restriction]** 탭에서 **[!UICONTROL This folder is a view]**&#x200B;를 선택합니다. 그러면 데이터베이스의 모든 배달이 표시됩니다.

   ![](assets/s_ncs_user_add_folder_exple01.png)

1. 창의 가운데 섹션에 있는 쿼리 편집기에서 배달 필터 기준을 정의합니다.그러면 정의된 필터에 해당하는 캠페인이 표시됩니다.

   >[!NOTE]
   >
   >쿼리 편집기는 [이 섹션](../../platform/using/about-queries-in-campaign.md)에 있습니다.

   다음 필터 조건 사용:

![](assets/s_ncs_user_add_folder_exple00.png)

다음 배달이 보기에 표시됩니다.

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>[트랜잭션 메시징](../../message-center/using/about-transactional-messaging.md) 이벤트를 관리할 때 액세스 권한 문제가 발생할 수 있으므로 **[!UICONTROL Real time events]** 또는 **[!UICONTROL Batch events]** 폴더를 실행 인스턴스에서 보기로 설정할 수 없습니다. 이벤트 컬렉션에 대한 자세한 내용은 [이 섹션](../../message-center/using/event-collection.md)을 참조하십시오.



## 폴더에 대한 권한

### {#edit-permissions-on-a-folder} 폴더에 대한 권한 편집

트리의 특정 폴더에 대한 권한을 편집하려면 아래 절차를 따르십시오.

1. 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Properties...]**&#x200B;을 선택합니다.

   ![](assets/s_ncs_user_folder_properties.png)

1. 이 폴더의 승인을 보려면 **[!UICONTROL Security]** 탭을 클릭합니다.

   ![](assets/s_ncs_user_folder_properties_security.png)

### 권한 수정 {#modify-permissions}

권한을 수정하려면 다음을 수행합니다.

* **그룹 또는 연산자를 바꿉니다**. 이렇게 하려면 폴더에 대한 권한이 있는 그룹(또는 연산자) 중 하나를 클릭하고 드롭다운 목록에서 새 그룹(또는 새 연산자)을 선택합니다.

   ![](assets/s_ncs_user_folder_properties_security02.png)

* **그룹 또는 연산자를 승인합니다**. 이렇게 하려면 **[!UICONTROL Add]** 단추를 클릭하고 이 폴더에 대한 승인을 할당할 그룹 또는 연산자를 선택합니다.
* **그룹 또는 연산자** 금지. 이렇게 하려면 **[!UICONTROL Delete]**&#x200B;을 클릭하고 이 폴더에 대한 권한을 제거할 그룹 또는 연산자를 선택합니다.
* **그룹 또는 연산자에 할당된 권한을 선택합니다**. 이렇게 하려면 해당 그룹 또는 연산자를 클릭한 다음 부여할 액세스 권한을 선택하고 다른 권한을 선택 취소합니다.

   ![](assets/s_ncs_user_folder_properties_security03.png)

### 권한 전달 {#propagate-permissions}

인증 및 액세스 권한을 전파할 수 있습니다. 이렇게 하려면 폴더 속성에서 **[!UICONTROL Propagate]** 옵션을 선택합니다.

그러면 이 창에 정의된 인증이 현재 노드의 모든 하위 폴더에 적용됩니다. 그런 다음 하위 폴더 각각에 대해 이러한 승인을 오버로드할 수 있습니다.

>[!NOTE]
>
>폴더에 대해 이 옵션을 지우면 하위 폴더에 대해 자동으로 지워지지 않습니다. 각 하위 폴더에 대해 명시적으로 지우십시오.

### 모든 연산자 {#grant-access-to-all-operators}에 대한 액세스 권한 부여

**[!UICONTROL Security]** 탭에서 **[!UICONTROL System folder]** 옵션을 선택하면 모든 연산자가 해당 권한에 상관없이 이 데이터에 액세스할 수 있습니다. 이 옵션이 선택되어 있으면 연산자(또는 해당 그룹)를 인증 목록에 명시적으로 추가해야 사용자가 액세스할 수 있습니다.

![](assets/s_ncs_user_folder_properties_security03b.png)
