---
product: campaign
title: 목록 관리 및 사용자 지정
description: 목록 검색 및 구성 방법 알아보기
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 21656cc2-15a1-4156-8897-ea4fe3e9b97f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1151'
ht-degree: 2%

---

# 목록 관리 및 사용자 지정{#manage-and-customize-lists}

![](../../assets/common.svg)

탐색기를 사용하여 Campaign 데이터베이스의 레코드 목록에 액세스할 수 있습니다. 이러한 목록을 필터링하고, 검색을 실행하고, 정보를 추가하고, 데이터를 필터링하고, 정렬할 수 있습니다.

## 레코드 수 {#counting-records}

기본적으로 Adobe Campaign은 목록의 처음 200개의 레코드를 로드합니다. 즉, 표시 시 보고 있는 테이블의 모든 레코드가 반드시 표시되지 않습니다. 목록의 레코드 수 개수를 실행하고 더 많은 레코드를 로드할 수 있습니다.

목록 화면의 오른쪽 아래에서 **[!UICONTROL counter]** 는 로드된 레코드 수와 데이터베이스의 총 레코드 수를 표시합니다(필터를 적용한 후).

![](assets/s_ncs_user_nb_200_0.png)

다음과 같은 경우&#x200B;**?**&#x200B;오른쪽에 있는 숫자 대신 &quot;이(가) 나타나고 카운터를 클릭하여 계산을 시작합니다.

### 더 많은 레코드 로드 {#loading-more-records}

추가 레코드(기본적으로 200개 줄)를 로드하려면 **[!UICONTROL Continue loading]**.

![](assets/s_ncs_user_load_list.png)

모든 레코드를 로드하려면 목록을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Load all]**.

>[!CAUTION]
>
>레코드 수에 따라 전체 목록을 로드하는 시간이 길어질 수 있습니다.

### 기본 레코드 수 변경 {#change-default-number-of-records}

로드된 기본 레코드 수를 변경하려면 **[!UICONTROL Configure list]** 목록의 오른쪽 아래 모서리에 있습니다.

![](assets/s_ncs_user_configure_list.png)

목록 구성 창에서 **[!UICONTROL Advanced parameters]** (왼쪽 아래) 검색할 라인의 수를 변경합니다.

![](assets/s_ncs_user_configurelist_advancedparam.png)

## 목록 구성 {#configuring-lists}

### 열 추가 {#add-columns}

목록에 열을 추가하는 방법에는 두 가지가 있습니다.

레코드의 세부 정보에서 목록에 열을 빠르게 추가할 수 있습니다. 방법은 다음과 같습니다.

1. 세부 사항 화면에서 열에 표시할 필드를 마우스 오른쪽 단추로 클릭합니다.
1. **[!UICONTROL Add in the list]**&#x200B;을(를) 선택합니다.

   열이 기존 열 오른쪽에 추가됩니다.

![](assets/s_ncs_user_add_in_list.png)

예를 들어, 세부 사항 화면에 표시되지 않는 데이터를 표시하려면 목록 구성 창을 사용하는 것이 열을 추가하는 다른 방법입니다. 방법은 다음과 같습니다.

1. 클릭 **[!UICONTROL Configure list]** 아래와 목록의 오른쪽에 있습니다.

   ![](assets/s_ncs_user_configure_list.png)

1. 목록 구성 창에서 **[!UICONTROL Available fields]** 목록에 추가하여 **[!UICONTROL Output columns]**.

   ![](assets/s_ncs_user_configurelist.png)

   >[!NOTE]
   >
   >기본적으로 고급 필드는 표시되지 않습니다. 이를 표시하려면 **고급 필드 표시** 사용 가능한 필드 목록 오른쪽의 아래 및 를 가리킵니다.
   >
   >레이블은 표 다음에 알파벳 순서로 표시됩니다.
   >
   >를 사용하십시오 **검색** 필드를 사용하여 사용 가능한 필드에서 검색을 실행합니다. 자세한 내용은 [이 섹션](#sorting-a-list).
   >
   >필드는 특정 아이콘으로 식별됩니다. SQL 필드, 연결된 테이블, 계산된 필드 등 선택한 각 필드에 대해 사용 가능한 필드 목록 아래에 설명이 표시됩니다. [자세히 알아보기](#configuring-lists)
   >
   >데이터를 정렬 및 필터링할 수도 있습니다. [이 섹션](../../platform/using/filtering-options.md)을 참조하십시오.

1. 각 열을 반복하여 표시합니다.
1. 화살표를 사용하여 **표시 순서**. 가장 높은 열은 레코드 목록의 왼쪽에 있습니다.

   ![](assets/s_ncs_user_columns_order_down.png)

1. 필요한 경우 을(를) 클릭합니다. **[!UICONTROL Distribution of values]** 를 클릭하여 현재 폴더의 선택한 필드에 대한 값 재분할을 확인합니다.

   ![](assets/s_ncs_user_configurelist_values.png)

1. 클릭 **[!UICONTROL OK]** 구성을 확인하고 결과를 표시합니다.

### 새 열 만들기 {#create-a-new-column}

목록에 추가 필드를 표시할 새 열을 만들 수 있습니다. 방법은 다음과 같습니다.

1. 클릭 **[!UICONTROL Configure the list]** 아래와 목록의 오른쪽에 있습니다.
1. 클릭 **[!UICONTROL Add]** 를 클릭하여 목록에 새 필드를 표시합니다.

### 열 제거 {#remove-a-column}

를 사용하여 레코드 목록에 하나 이상의 열을 마스크할 수 있습니다 **[!UICONTROL Configure list]** 아래와 목록의 오른쪽에 있습니다.

![](assets/s_ncs_user_configure_list.png)

목록 구성 창에서 **[!UICONTROL Output columns]** 영역을 선택하고 삭제 단추를 클릭합니다.

![](assets/s_ncs_user_removecolumn_icon.png)

각 열의 마스킹에 대해 이 작업을 반복합니다. 클릭 **[!UICONTROL OK]** 구성을 확인하고 결과를 표시합니다.

### 열 너비 조정 {#adjust-column-width}

목록이 활성화되면, 즉, 하나 이상의 줄을 선택하면 F9를 사용하여 모든 열이 화면에 표시되도록 열의 너비를 조정할 수 있습니다.

### 하위 폴더에 데이터 표시 {#display-sub-folders-records}

목록을 표시할 수 있습니다.

* 선택한 폴더에만 포함된 레코드
* 또는 선택한 폴더 및 해당 하위 폴더의 레코드

한 디스플레이 모드에서 다른 디스플레이 모드로 전환하려면 **[!UICONTROL Display sub-levels]** 클릭합니다.

![](assets/s_ncs_user_display_children_icon.png)

## 목록 구성 저장 {#saving-a-list-configuration}

목록 구성은 워크스테이션 수준에서 로컬로 정의됩니다. 로컬 캐시가 지워지면 로컬 구성이 비활성화됩니다.

기본적으로 정의된 표시 매개 변수는 해당 폴더 유형이 있는 모든 목록에 적용됩니다. 따라서 폴더에서 수신자 목록이 표시되는 방식을 수정하면 이 구성이 다른 모든 수신자 폴더에 적용됩니다.

그러나 동일한 유형의 다른 폴더에 적용할 구성을 두 개 이상 저장할 수 있습니다. 구성은 데이터가 포함된 폴더의 속성과 함께 저장되며 다시 적용할 수 있습니다.

예를 들어 게재 폴더의 경우 다음 표시를 구성할 수 있습니다.

![](assets/s_ncs_user_folder_save_config_1.png)

이 목록 구성을 다시 사용할 수 있도록 저장하려면 아래 단계를 따르십시오.

1. 표시된 데이터가 포함된 폴더를 마우스 오른쪽 단추로 클릭합니다.
1. **[!UICONTROL Properties]**&#x200B;을(를) 선택합니다.
1. 클릭 **[!UICONTROL Advanced settings]** 그런 다음 **[!UICONTROL Configuration]** 필드.

   ![](assets/s_ncs_user_folder_save_config_2.png)

1. 클릭 **[!UICONTROL OK]** 을 클릭한 다음 **[!UICONTROL Save]**.

그런 다음 이 구성을 다른 구성 요소에 적용할 수 있습니다 **배달** 폴더:

![](assets/s_ncs_user_folder_save_config_3.png)

클릭 **[!UICONTROL Save]** 폴더 속성 창에서 클릭합니다. 지정된 구성과 일치하도록 목록 표시가 수정되었습니다.

![](assets/s_ncs_user_folder_save_config_5.png)

## 목록 내보내기 {#exporting-a-list}

목록에서 데이터를 내보내려면 내보내기 마법사를 사용해야 합니다. 액세스하려면 목록에서 내보낼 요소를 선택하고 마우스 오른쪽 버튼을 클릭한 다음 을(를) 선택합니다 **[!UICONTROL Export...]**.

가져오기 및 내보내기 기능의 사용은 [일반 가져오기 및 내보내기](../../platform/using/about-generic-imports-exports.md).

>[!CAUTION]
>
>목록의 요소는 복사/붙여넣기 함수를 사용하여 내보낼 수 없습니다.

## 목록 정렬 {#sorting-a-list}

목록에는 많은 양의 데이터가 포함될 수 있습니다. 이러한 데이터를 정렬하거나 단순 또는 고급 필터를 적용할 수 있습니다. 정렬을 사용하면 데이터를 오름차순이나 내림차순으로 표시할 수 있습니다. 필터를 사용하여 선택한 데이터만 표시하도록 기준을 정의하고 결합할 수 있습니다.

오름차순 또는 내림차순 정렬을 적용하거나 데이터 정렬을 취소하려면 열 헤더를 클릭합니다. 활성 정렬 상태 및 정렬 순서는 열 레이블 앞에 파란색 화살표로 표시됩니다. 열 레이블 앞의 빨간색 대시는 정렬이 데이터베이스에서 인덱싱된 데이터에 적용됨을 의미합니다. 이 정렬 방법은 정렬 작업을 최적화하는 데 사용됩니다.

정렬 기준을 구성하거나 결합할 수도 있습니다. 이렇게 하려면 아래 단계를 수행합니다:

1. **[!UICONTROL Configure list]** 아래와 목록의 오른쪽에 있습니다.

   ![](assets/s_ncs_user_configure_list.png)

1. 목록 구성 창에서 **[!UICONTROL Sorting]** 탭.
1. 정렬할 필드와 정렬 방향(오름차순 또는 내림차순)을 선택합니다.

   ![](assets/s_ncs_user_configurelist_sort.png)

1. 정렬 우선순위는 정렬 열의 순서대로 정의됩니다. 우선 순위를 변경하려면 해당 아이콘을 사용하여 열 순서를 변경합니다.

   ![](assets/s_ncs_user_configurelist_move.png)

   정렬 우선순위는 목록에 있는 열 표시에 영향을 주지 않습니다.

1. 클릭 **[!UICONTROL Ok]** 이 구성을 확인하고 결과를 목록에 표시합니다.

### 요소 검색 {#running-a-search}

를 사용하여 편집기에서 사용 가능한 필드 검색을 실행할 수 있습니다 **[!UICONTROL Search]** 필드 목록 위에 있는 필드입니다. 누르기 **Enter 키** 키보드에서 또는 목록을 찾습니다. 검색과 일치하는 필드에는 굵은 레이블이 있습니다.

>[!NOTE]
>
>필터를 만들어 일부 데이터만 목록에 표시할 수 있습니다. [자세히 알아보기](../../platform/using/creating-filters.md)
