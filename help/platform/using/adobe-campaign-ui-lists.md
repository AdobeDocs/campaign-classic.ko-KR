---
product: campaign
title: 목록 관리 및 사용자 지정
description: 목록 검색 및 구성 방법 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Audiences, Data Management
exl-id: 21656cc2-15a1-4156-8897-ea4fe3e9b97f
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1151'
ht-degree: 2%

---

# 목록 관리 및 사용자 지정{#manage-and-customize-lists}



탐색기를 사용하여 Campaign 데이터베이스의 레코드 목록에 액세스할 수 있습니다. 이러한 목록을 필터링하고, 검색을 실행하고, 정보를 추가하고, 데이터를 필터링하고 정렬할 수 있습니다.

## 레코드 수 {#counting-records}

기본적으로 Adobe Campaign은 목록의 처음 200개의 레코드를 로드합니다. 즉, 표시에서 보고 있는 테이블의 모든 레코드가 표시되지는 않습니다. 목록에 있는 레코드 수 개수를 실행하고 더 많은 레코드를 로드할 수 있습니다.

목록 화면의 오른쪽 하단에서 **[!UICONTROL counter]** 로드된 레코드 수와 데이터베이스에 있는 총 레코드 수를 표시합니다(필터를 적용한 후).

![](assets/s_ncs_user_nb_200_0.png)

인 경우&#x200B;**?**&#x200B;오른쪽에 있는 숫자 대신 &quot;&quot;가 나타나면 카운터를 클릭하여 계산을 시작합니다.

### 더 많은 레코드 로드 {#loading-more-records}

추가 레코드(기본적으로 200줄)를 로드하여 표시하려면 다음을 클릭합니다. **[!UICONTROL Continue loading]**.

![](assets/s_ncs_user_load_list.png)

모든 레코드를 로드하려면 목록을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Load all]**.

>[!CAUTION]
>
>레코드 수에 따라 전체 목록을 로드하는 시간이 길어질 수 있습니다.

### 기본 레코드 수 변경 {#change-default-number-of-records}

로드된 기본 레코드 수를 변경하려면 **[!UICONTROL Configure list]** 목록의 오른쪽 하단 모서리에 있습니다.

![](assets/s_ncs_user_configure_list.png)

목록 구성 창에서 **[!UICONTROL Advanced parameters]** (왼쪽 하단) 및 검색할 라인의 수를 변경합니다.

![](assets/s_ncs_user_configurelist_advancedparam.png)

## 목록 구성 {#configuring-lists}

### 열 추가 {#add-columns}

목록에 열을 추가하는 방법에는 두 가지가 있습니다.

레코드의 세부 정보에서 목록에 열을 빠르게 추가할 수 있습니다. 방법은 다음과 같습니다.

1. 세부 정보 화면에서 열에 표시할 필드를 마우스 오른쪽 단추로 클릭합니다.
1. **[!UICONTROL Add in the list]**&#x200B;을(를) 선택합니다.

   열이 기존 열의 오른쪽에 추가됩니다.

![](assets/s_ncs_user_add_in_list.png)

예를 들어 세부 정보 화면에 표시되지 않는 데이터를 표시하려는 경우 열을 추가하는 또 다른 방법은 목록 구성 창을 사용하는 것입니다. 방법은 다음과 같습니다.

1. 클릭 **[!UICONTROL Configure list]** 목록 아래와 오른쪽에 있습니다.

   ![](assets/s_ncs_user_configure_list.png)

1. 목록 구성 창에서 추가할 필드를 두 번 클릭합니다. **[!UICONTROL Available fields]** 목록에 추가하기 **[!UICONTROL Output columns]**.

   ![](assets/s_ncs_user_configurelist.png)

   >[!NOTE]
   >
   >기본적으로 고급 필드는 표시되지 않습니다. 이를 표시하려면 다음을 클릭합니다. **고급 필드 표시** 사용 가능한 필드 목록의 아래쪽과 오른쪽에.
   >
   >레이블은 표로 표시된 다음 알파벳순으로 표시됩니다.
   >
   >사용 **검색** 사용 가능한 필드에서 검색을 실행하는 필드입니다. 자세한 내용은 다음을 참조하십시오. [이 섹션](#sorting-a-list).
   >
   >필드는 SQL 필드, 연결된 테이블, 계산된 필드 등의 특정 아이콘으로 식별됩니다. 선택한 각 필드에 대해 사용 가능한 필드 목록 아래에 설명이 표시됩니다. [자세히 알아보기](#configuring-lists)
   >
   >데이터를 정렬 및 필터링할 수도 있습니다. [이 섹션](../../platform/using/filtering-options.md)을 참조하십시오.

1. 표시할 각 열에 대해 이 작업을 반복합니다.
1. 화살표를 사용하여 **표시 순서**. 가장 높은 열은 레코드 목록의 왼쪽에 있습니다.

   ![](assets/s_ncs_user_columns_order_down.png)

1. 필요한 경우 **[!UICONTROL Distribution of values]** 현재 폴더의 선택한 필드에 대한 값 재분할을 봅니다.

   ![](assets/s_ncs_user_configurelist_values.png)

1. 클릭 **[!UICONTROL OK]** 구성을 확인하고 결과를 표시합니다.

### 새 열 만들기 {#create-a-new-column}

새 열을 만들어 목록에 추가 필드를 표시할 수 있습니다. 방법은 다음과 같습니다.

1. 클릭 **[!UICONTROL Configure the list]** 목록 아래와 오른쪽에 있습니다.
1. 클릭 **[!UICONTROL Add]** 새 필드를 목록에 표시합니다.

### 열 제거 {#remove-a-column}

다음을 사용하여 레코드 목록에서 하나 이상의 열을 마스킹할 수 있습니다. **[!UICONTROL Configure list]** 목록 아래와 오른쪽에 있습니다.

![](assets/s_ncs_user_configure_list.png)

목록 구성 창의 목록에서 마스킹할 열을 선택합니다 **[!UICONTROL Output columns]** zone 을 설정하고 delete 버튼을 클릭합니다.

![](assets/s_ncs_user_removecolumn_icon.png)

마스킹할 각 열에 대해 이 작업을 반복합니다. 클릭 **[!UICONTROL OK]** 구성을 확인하고 결과를 표시합니다.

### 열 너비 조정 {#adjust-column-width}

목록이 활성 상태인 경우(즉, 하나 이상의 줄이 선택된 경우) F9 키를 사용하여 모든 열이 화면에 표시되도록 열의 너비를 조정할 수 있습니다.

### 하위 폴더에 데이터 표시 {#display-sub-folders-records}

목록은 다음을 표시할 수 있습니다.

* 선택한 폴더에만 포함된 레코드
* 또는 선택한 폴더 및 해당 하위 폴더의 레코드입니다.

한 디스플레이 모드에서 다른 디스플레이 모드로 전환하려면 **[!UICONTROL Display sub-levels]** 을 클릭합니다.

![](assets/s_ncs_user_display_children_icon.png)

## 목록 구성 저장 {#saving-a-list-configuration}

목록 구성은 워크스테이션 수준에서 로컬로 정의됩니다. 로컬 캐시가 지워지면 로컬 구성이 비활성화됩니다.

기본적으로 정의된 디스플레이 매개변수는 해당 폴더 유형을 가진 모든 목록에 적용됩니다. 따라서 폴더에서 수신자 목록이 표시되는 방법을 수정하면 이 구성이 다른 모든 수신자 폴더에 적용됩니다.

그러나 동일한 유형의 다른 폴더에 적용할 구성을 두 개 이상 저장할 수 있습니다. 구성은 데이터가 포함된 폴더의 속성과 함께 저장되며 다시 적용할 수 있습니다.

예를 들어 게재 폴더의 경우 다음 표시를 구성할 수 있습니다.

![](assets/s_ncs_user_folder_save_config_1.png)

재사용할 수 있도록 이 목록 구성을 저장하려면 아래 단계를 수행합니다.

1. 표시된 데이터가 포함된 폴더를 마우스 오른쪽 단추로 클릭합니다.
1. **[!UICONTROL Properties]**&#x200B;을(를) 선택합니다.
1. 클릭 **[!UICONTROL Advanced settings]** 이름을 지정한 다음 **[!UICONTROL Configuration]** 필드.

   ![](assets/s_ncs_user_folder_save_config_2.png)

1. 클릭 **[!UICONTROL OK]** 그런 다음 을 클릭합니다. **[!UICONTROL Save]**.

그런 다음 이 구성을 다른 페이지에 적용할 수 있습니다 **게재** 폴더:

![](assets/s_ncs_user_folder_save_config_3.png)

클릭 **[!UICONTROL Save]** 폴더 속성 창에서 액세스합니다. 목록 표시가 지정된 구성과 일치하도록 수정됩니다.

![](assets/s_ncs_user_folder_save_config_5.png)

## 목록 내보내기 {#exporting-a-list}

목록에서 데이터를 내보내려면 내보내기 마법사를 사용해야 합니다. 액세스하려면 목록에서 내보낼 요소를 선택하고 마우스 오른쪽 버튼을 클릭한 다음 를 선택합니다 **[!UICONTROL Export...]**.

에서는 가져오기 및 내보내기 기능 사용에 대해 설명합니다 [일반 가져오기 및 내보내기](../../platform/using/about-generic-imports-exports.md).

>[!CAUTION]
>
>목록의 요소는 복사/붙여넣기 기능을 사용하여 내보낼 수 없습니다.

## 목록 정렬 {#sorting-a-list}

목록에는 많은 양의 데이터가 포함될 수 있습니다. 이러한 데이터를 정렬하거나 단순 또는 고급 필터를 적용할 수 있습니다. 정렬을 사용하여 데이터를 오름차순 또는 내림차순으로 표시할 수 있습니다. 필터를 사용하면 기준을 정의하고 결합하여 선택한 데이터만 표시할 수 있습니다.

오름차순 또는 내림차순 정렬을 적용하거나 데이터 정렬을 취소하려면 열 헤더를 클릭합니다. 활성 정렬 상태 및 정렬 순서는 열 레이블 앞에 파란색 화살표로 표시됩니다. 열 레이블 앞에 빨간색 대시가 있으면 데이터베이스에서 인덱싱된 데이터에 정렬이 적용됨을 의미합니다. 이 정렬 방법은 정렬 작업을 최적화하는 데 사용됩니다.

정렬을 구성하거나 정렬 기준을 결합할 수도 있습니다. 이렇게 하려면 아래 단계를 수행합니다:

1. **[!UICONTROL Configure list]** 목록 아래와 오른쪽에 있습니다.

   ![](assets/s_ncs_user_configure_list.png)

1. 목록 구성 창에서 **[!UICONTROL Sorting]** 탭.
1. 정렬할 필드와 정렬 방향(오름차순 또는 내림차순)을 선택합니다.

   ![](assets/s_ncs_user_configurelist_sort.png)

1. 정렬 우선순위는 정렬 열의 순서로 정의됩니다. 우선 순위를 변경하려면 해당 아이콘을 사용하여 열의 순서를 변경합니다.

   ![](assets/s_ncs_user_configurelist_move.png)

   정렬 우선 순위는 목록의 열 표시에 영향을 주지 않습니다.

1. 클릭 **[!UICONTROL Ok]** 이 구성을 확인하고 결과를 목록에 표시합니다.

### 요소 검색 중 {#running-a-search}

를 사용하여 편집기에서 사용 가능한 필드 검색을 실행할 수 있습니다. **[!UICONTROL Search]** 필드 목록 위에 있는 필드입니다. 누르기 **입력** 키보드에서 또는 목록을 탐색합니다. 검색과 일치하는 필드에 굵은 레이블이 표시됩니다.

>[!NOTE]
>
>필터를 만들어 목록의 일부 데이터만 표시할 수 있습니다. [자세히 알아보기](../../platform/using/creating-filters.md)
