---
solution: Campaign Classic
product: campaign
title: Adobe Campaign 작업 영역
description: Adobe Campaign 작업 영역
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '2157'
ht-degree: 2%

---


# Adobe Campaign 작업 영역{#adobe-campaign-workspace}

## Adobe Campaign 인터페이스 탐색 {#about-adobe-campaign-interface}

데이터베이스에 연결되면 대시보드인 Adobe Campaign 홈 페이지에 액세스합니다.이 단축키는 설치 및 일반 플랫폼 구성에 따라 기능에 액세스할 수 있는 링크와 단축키로 구성되어 있습니다.

홈 페이지의 중앙 섹션에서 링크를 사용하여 Campaign 온라인 문서 포털, 포럼 및 지원 웹 사이트에 액세스할 수 있습니다.

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png)[ 비디오에서 캠페인 작업 영역 살펴보기](#video)

>[!NOTE]
>
>인스턴스에서 사용할 수 있는 Adobe Campaign 기능은 설치된 모듈 및 추가 기능에 따라 다릅니다. 사용 권한 및 특정 구성에 따라 일부 옵션을 사용할 수도 없습니다.
>
>모듈 또는 Add-On을 설치하기 전에 사용권 계약을 확인하거나 Adobe 계정 담당자에게 문의하십시오.

### 콘솔 및 웹 액세스 {#console-and-web-access}

Adobe Campaign 플랫폼은 콘솔 또는 인터넷 브라우저를 통해 액세스할 수 있습니다.

웹 액세스는 콘솔과 비슷하지만 기능 세트가 줄어든 인터페이스를 제공합니다.

예를 들어, 지정된 연산자에 대해 캠페인은 콘솔에 다음 옵션이 표시됩니다.

![](assets/operation_from_console.png)

웹 액세스가 가능한 반면 이 옵션은 주로 보기를 활성화합니다.

![](assets/operation_from_web.png)

### 언어 {#languages}

Adobe Campaign Classic 인스턴스를 설치할 때 해당 언어가 선택됩니다.

![](assets/language.png)

5개 언어 중에서 선택할 수 있습니다.

* 영어(영국)
* 영어(미국)
* 프랑스어
* 독일어
* 일본어

Adobe Campaign Classic 인스턴스에 대해 선택한 언어는 날짜 및 시간 형식에 영향을 줄 수 있습니다. 자세한 정보는 이 [섹션](../../platform/using/adobe-campaign-workspace.md#date-and-time)을 참조하십시오.

인스턴스를 만드는 방법에 대한 자세한 내용은 이 [page](../../installation/using/creating-an-instance-and-logging-on.md)을 참조하십시오.

>[!CAUTION]
>
>인스턴스를 만든 후에는 언어를 변경할 수 없습니다.

## 탐색 기본 사항 {#navigation-basics}

### 페이지 탐색 중 {#browsing-pages}

플랫폼의 다양한 기능이 핵심 기능으로 분류됩니다.인터페이스의 상단 섹션에 있는 링크를 사용하여 액세스할 수 있습니다.

![](assets/overview_home.png)

액세스할 수 있는 핵심 기능 목록은 설치된 패키지 및 추가 기능과 액세스 권한에 따라 다릅니다.

각 기능에는 작업 관련 요구 사항 및 사용 컨텍스트에 따라 일련의 기능이 포함되어 있습니다. 예를 들어 **[!UICONTROL Profiles and targets]** 링크는 수신자 목록, 구독 서비스, 기존 타깃팅 워크플로우 및 이러한 요소를 만드는 단축키로 연결됩니다.

목록은 **[!UICONTROL Profiles and Targets]** 인터페이스의 왼쪽 섹션에 있는 **[!UICONTROL Lists]** 링크를 통해 사용할 수 있습니다.

![](assets/recipient_list_overview.png)

### 탭 {#using-tabs} 사용

* 핵심 기능 또는 링크를 클릭하면 관련 페이지가 현재 페이지로 바뀝니다. 이전 페이지로 돌아가려면 도구 모음에서 **[!UICONTROL Back]** 단추를 클릭합니다. 홈 페이지로 돌아가려면 **[!UICONTROL Home]** 단추를 클릭합니다.

   ![](assets/d_ncs_user_interface_back_home_buttons.png)

* 메뉴 또는 표시 화면 단축키(웹 애플리케이션, 프로그램, 전달, 보고서 등)의 경우 일치하는 페이지가 다른 탭에 표시됩니다. 탭을 사용하여 한 페이지에서 다른 페이지로 이동할 수 있습니다.

   ![](assets/d_ncs_user_interface_tabs.png)

### {#creating-an-element} 요소 만들기

각 핵심 기능 섹션에서 사용 가능한 요소 간을 탐색할 수 있습니다. 이렇게 하려면 **[!UICONTROL Browsing]** 섹션의 단축키를 사용합니다. **[!UICONTROL Other choices]** 링크를 사용하면 환경에 상관없이 다른 모든 페이지에 액세스할 수 있습니다.

새 요소(전달, 웹 애플리케이션, 워크플로우 등)를 만들 수 있습니다. 화면 왼쪽의 **[!UICONTROL Create]** 섹션에 있는 단축키를 사용합니다. 목록 위의 **[!UICONTROL Create]** 단추를 사용하여 목록에 새 요소를 추가합니다.

예를 들어 배달 페이지에서 **[!UICONTROL Create]** 단추를 사용하여 새 배달을 만듭니다.

![](assets/d_ncs_user_interface_tab_add_del.png)

## Adobe Campaign 탐색기 사용 {#using-adobe-campaign-explorer}

### Adobe Campaign 탐색기 {#about-adobe-campaign-explorer} 정보

Adobe Campaign 탐색기는 도구 모음 아이콘을 통해 액세스할 수 있습니다. Adobe Campaign의 모든 Adobe Campaign 기능, 구성 화면 및 일부 플랫폼 요소의 보다 자세한 보기를 이용할 수 있습니다.

**[!UICONTROL Explorer]** 작업 영역은 다음 세 영역으로 분할됩니다.

![](assets/s_ncs_user_navigation.png)

**1 - 트리**:트리의 컨텐츠를 개인화할 수 있습니다(노드 추가, 이동 또는 삭제). 이 절차는 전문 사용자에게만 해당됩니다. 자세한 정보는 이 [페이지](../../configuration/using/about-navigation-hierarchy.md)를 참조하십시오.

**2 - 목록**:이 목록을 필터링하거나 검색을 실행하거나 정보를 추가하거나 데이터를 정렬할 수 있습니다.

**3 - 세부** 사항:선택한 요소의 세부 사항을 표시할 수 있습니다. 오른쪽 상단의 아이콘을 사용하여 이 정보를 전체 화면 형식으로 표시할 수 있습니다.

### 화면 해상도 {#screen-resolution}

최적의 탐색 및 유용성을 위해 Adobe은 최소 1600x900픽셀의 화면 해상도를 사용하는 것이 좋습니다.

>[!CAUTION]
>
>1600x900픽셀 이하의 해상도는 Adobe Campaign에서 지원되지 않을 수 있습니다.

**[!UICONTROL Explorer]** 작업 영역에서 **[!UICONTROL Details]** 영역의 일부 부분이 잘린 것으로 나타나면 영역 위쪽의 화살표를 사용하여 확장하거나 **[!UICONTROL Enlarge]** 단추를 클릭합니다.

![](assets/s_ncs_user_resolution.png)

### 검색 목록 {#browsing-lists}

목록을 찾아보려면 **스크롤 막대**(가로 및 세로)를 사용하여 레코드 선택, **마우스 휠이** 또는 **화살표 키**&#x200B;를 변경하지 않고 스크롤할 수 있습니다.

>[!NOTE]
>
>목록 내용의 구성 및 개인화는 [목록 구성](#configuring-lists)에 있습니다.
>
>데이터를 정렬 및 필터링할 수도 있습니다. [필터링 옵션](../../platform/using/filtering-options.md)을 참조하십시오.

### 레코드 수 {#counting-records}

기본적으로 Adobe Campaign은 목록의 처음 200개의 레코드를 로드합니다. 즉, 표시되는 테이블이 모두 표시되는 것은 아닙니다. 목록에 있는 레코드 수의 카운트를 실행하고 더 많은 레코드를 로드할 수 있습니다.

목록 화면의 오른쪽 하단에서 **[!UICONTROL counter]**&#x200B;은 로드된 레코드 수와 데이터베이스의 총 레코드 수를 표시합니다(필터를 적용한 후).

![](assets/s_ncs_user_nb_200_0.png)

&quot;**?**&#x200B;오른쪽에 숫자 대신 나타나는 카운터를 클릭하여 계산을 시작합니다.

### 레코드 {#loading-more-records}을(를) 더 로드하는 중

추가 레코드(기본적으로 200개 줄)를 로드하고 표시하려면 **[!UICONTROL Continue loading]**&#x200B;을 클릭합니다.

![](assets/s_ncs_user_load_list.png)

모든 레코드를 로드하려면 목록을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Load all]** 을 선택합니다.

>[!CAUTION]
>
>레코드 수에 따라 전체 목록을 로드하는 시간이 길어질 수 있습니다.

### 레코드 {#change-default-number-of-records} 기본 수 변경

로드된 레코드의 기본 수를 변경하려면 목록 오른쪽 하단에 있는 **[!UICONTROL Configure list]**&#x200B;을 클릭합니다.

![](assets/s_ncs_user_configure_list.png)

목록 구성 창에서 &quot;고급 매개 변수&quot;(왼쪽 아래)를 클릭하고 검색할 줄 수를 변경합니다.

![](assets/s_ncs_user_configurelist_advancedparam.png)

## {#configuring-lists} 목록 구성

### 열 추가 {#add-columns}

목록에 열을 추가하는 방법에는 두 가지가 있습니다.

레코드 세부 사항에서 목록에 열을 빠르게 추가할 수 있습니다. 방법은 다음과 같습니다.

1. 세부 정보 화면에서 열에 표시할 필드를 마우스 오른쪽 단추로 클릭합니다.
1. **[!UICONTROL Add in the list]**&#x200B;을(를) 선택합니다.

   기존 열 오른쪽에 열이 추가됩니다.

![](assets/s_ncs_user_add_in_list.png)

열을 추가하는 또 다른 방법(예: 세부 사항 화면에 표시되지 않는 데이터를 표시하려면 목록 구성 창을 사용하는 방법) 방법은 다음과 같습니다.

1. 아래 및 목록 오른쪽에 있는 **[!UICONTROL Configure list]**&#x200B;을 클릭합니다.

   ![](assets/s_ncs_user_configure_list.png)

1. 목록 구성 창에서 **[!UICONTROL Available fields]** 목록에 추가할 필드를 두 번 클릭하여 **[!UICONTROL Output columns]**&#x200B;에 추가합니다.

   ![](assets/s_ncs_user_configurelist.png)

   >[!NOTE]
   >
   >기본적으로 고급 필드는 표시되지 않습니다. 이 필드를 표시하려면 아래 및 사용 가능한 필드 목록 오른쪽에 있는 **고급 필드 표시**&#x200B;를 클릭합니다.
   >
   >레이블은 표별로 표시된 다음 알파벳순으로 표시됩니다.
   >
   >사용 가능한 필드에서 검색을 실행하려면 **검색** 필드를 사용합니다. 자세한 내용은 [목록 정렬](#sorting-a-list)을 참조하십시오.
   >
   >필드는 특정 아이콘으로 식별됩니다.SQL 필드, 연결된 테이블, 계산된 필드 등 선택한 각 필드에 대해 사용 가능한 필드 목록 아래에 설명이 표시됩니다. [목록](#configuring-lists) 구성
   >
   >데이터를 정렬 및 필터링할 수도 있습니다. [필터링 옵션](../../platform/using/filtering-options.md)을 참조하십시오.

1. 각 열이 표시될 때 이 단계를 반복합니다.
1. 화살표를 사용하여 **표시 순서**&#x200B;를 수정합니다. 가장 높은 열은 레코드 목록의 왼쪽에 있습니다.

   ![](assets/s_ncs_user_columns_order_down.png)

1. 필요한 경우 **[!UICONTROL Distribution of values]**&#x200B;을 클릭하여 현재 폴더의 선택한 필드에 대한 값의 재파티션을 볼 수 있습니다.

   ![](assets/s_ncs_user_configurelist_values.png)

1. **[!UICONTROL OK]**&#x200B;을 클릭하여 구성을 확인하고 결과를 표시합니다.

### 새 열 {#create-a-new-column} 만들기

새 열을 만들어 목록에 추가 필드를 표시할 수 있습니다. 방법은 다음과 같습니다.

1. 아래 및 목록 오른쪽에 있는 **[!UICONTROL Configure the list]**&#x200B;을 클릭합니다.
1. 목록에 새 필드를 표시하려면 **[!UICONTROL Add]**&#x200B;을 클릭합니다.

### 열 {#remove-a-column} 제거

아래 및 목록 오른쪽에 있는 **[!UICONTROL Configure list]**&#x200B;을 사용하여 레코드 목록에서 하나 이상의 열을 마스크할 수 있습니다.

![](assets/s_ncs_user_configure_list.png)

목록 구성 창의 **[!UICONTROL Output columns]** 영역에서 마스크할 열을 선택하고 삭제 단추를 클릭합니다.

![](assets/s_ncs_user_removecolumn_icon.png)

마스크할 각 열에 대해 반복합니다. **[!UICONTROL OK]**&#x200B;을 클릭하여 구성을 확인하고 결과를 표시합니다.

### 열 너비 조정 {#adjust-column-width}

목록이 활성 상태인 경우(하나 이상의 줄이 선택된 경우) F9를 사용하여 모든 열을 화면에 표시할 수 있도록 열의 너비를 조정할 수 있습니다.

### 하위 폴더 레코드 표시 {#display-sub-folders-records}

목록을 표시할 수 있습니다.

* 선택한 폴더에만 포함된 레코드 중 하나,
* 또는 선택한 폴더 및 하위 폴더의 레코드.

한 표시 모드에서 다른 표시 모드로 전환하려면 도구 모음에서 **[!UICONTROL Display sub-levels]** 을 클릭합니다.

![](assets/s_ncs_user_display_children_icon.png)

### 목록 구성 {#saving-a-list-configuration} 저장

목록 구성은 워크스테이션 수준에서 로컬로 정의됩니다. 로컬 캐시가 지워지면 로컬 구성이 비활성화됩니다.

기본적으로 정의된 표시 매개 변수는 해당 폴더 유형의 모든 목록에 적용됩니다. 따라서 폴더에서 수신자 목록을 표시하는 방법을 수정하면 이 구성이 다른 모든 수신자 폴더에 적용됩니다.

그러나 동일한 유형의 다른 폴더에 둘 이상의 구성을 저장할 수 있습니다. 구성은 데이터가 포함된 폴더의 속성과 함께 저장되며 다시 적용할 수 있습니다.

예를 들어 배달 폴더의 경우 다음 표시를 구성할 수 있습니다.

![](assets/s_ncs_user_folder_save_config_1.png)

이 목록 구성을 다시 사용할 수 있도록 저장하려면 아래 단계를 따르십시오.

1. 표시된 데이터가 포함된 폴더를 마우스 오른쪽 단추로 클릭합니다.
1. **[!UICONTROL Properties]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL Advanced settings]**&#x200B;을 클릭한 다음 **[!UICONTROL Configuration]** 필드에 이름을 지정합니다.

   ![](assets/s_ncs_user_folder_save_config_2.png)

1. **[!UICONTROL OK]**&#x200B;을 클릭한 다음 **[!UICONTROL Save]**&#x200B;을 클릭합니다.

그런 다음 이 구성을 다른 **배달** 폴더에 적용할 수 있습니다.

![](assets/s_ncs_user_folder_save_config_3.png)

폴더 속성 창에서 **[!UICONTROL Save]**&#x200B;을 클릭합니다. 목록 표시가 지정된 구성과 일치하도록 수정되었습니다.

![](assets/s_ncs_user_folder_save_config_5.png)

## 목록 {#exporting-a-list} 내보내기

목록에서 데이터를 내보내려면 내보내기 마법사를 사용해야 합니다. 이 파일에 액세스하려면 목록에서 내보낼 요소를 선택하고 마우스 오른쪽 버튼을 클릭한 다음 **[!UICONTROL Export...]** 을 선택합니다.

가져오기 및 내보내기 함수의 사용에 대해서는 [일반 가져오기 및 내보내기](../../platform/using/about-generic-imports-exports.md)에 설명되어 있습니다.

>[!CAUTION]
>
>목록의 요소는 복사/붙여넣기 함수를 사용하여 내보내면 안 됩니다.

## 목록 정렬 {#sorting-a-list}

목록에는 대량의 데이터가 포함될 수 있습니다. 이러한 데이터를 정렬하거나 단순 또는 고급 필터를 적용할 수 있습니다. 정렬을 사용하면 데이터를 내림차순이나 오름차순으로 표시할 수 있습니다. 필터를 사용하면 선택한 데이터만 표시하도록 기준을 정의하고 결합할 수 있습니다.

열 헤더를 클릭하여 오름차순 또는 내림차순 정렬을 적용하거나 데이터 정렬을 취소합니다. 활성 정렬 상태 및 정렬 순서는 열 레이블 앞에 파란색 화살표로 표시됩니다. 열 레이블 앞의 빨간색 대시는 데이터베이스에서 인덱싱된 데이터에 정렬이 적용됨을 의미합니다. 이 정렬 방법은 정렬 작업을 최적화하는 데 사용됩니다.

정렬 기준을 구성하거나 결합할 수도 있습니다. 이렇게 하려면 아래 단계를 수행합니다:

1. **[!UICONTROL Configure list]** 아래 및 목록의 오른쪽에 있습니다.

   ![](assets/s_ncs_user_configure_list.png)

1. 목록 구성 창에서 **[!UICONTROL Sorting]** 탭을 클릭합니다.
1. 정렬할 필드와 정렬 방향(오름차순 또는 내림차순)을 선택합니다.

   ![](assets/s_ncs_user_configurelist_sort.png)

1. 정렬 우선 순위는 정렬 열의 순서로 정의됩니다. 우선 순위를 변경하려면 해당 아이콘을 사용하여 열 순서를 변경합니다.

   ![](assets/s_ncs_user_configurelist_move.png)

   정렬 우선 순위는 목록의 열 표시에 영향을 주지 않습니다.

1. **[!UICONTROL Ok]**&#x200B;을 클릭하여 이 구성을 확인하고 결과를 목록에 표시합니다.

### 요소 {#running-a-search} 검색

필드 목록 위에 있는 **[!UICONTROL Search]** 필드를 사용하여 편집기에서 사용 가능한 필드를 검색할 수 있습니다. 키보드에서 **Enter**&#x200B;를 누르거나 목록을 탐색합니다. 검색과 일치하는 필드에는 굵은 레이블이 표시됩니다.

>[!NOTE]
>
>목록에 있는 일부 데이터만 표시하는 필터를 만들 수 있습니다. [필터 만들기](../../platform/using/creating-filters.md)를 참조하십시오.

## 형식 및 단위 {#formats-and-units}

### 날짜 및 시간 {#date-and-time}

Adobe Campaign Classic 인스턴스의 언어는 날짜 및 시간 형식에 영향을 줍니다.

Campaign을 설치할 때 언어가 선택되고 이후에는 변경할 수 없습니다. 다음을 선택할 수 있습니다.영어(미국), 영어(EN), 프랑스어, 독일어 또는 일본어 자세한 정보는 이 [페이지](../../installation/using/creating-an-instance-and-logging-on.md)를 참조하십시오.

미국 영어와 영국 영어의 주요 차이점은 다음과 같습니다.

<table> 
 <thead> 
  <tr> 
   <th> 형식<br /> </th> 
   <th> 영어(미국)<br /> </th> 
   <th> 영어(EN)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 날짜<br /> </td> 
   <td> 주 시작 날짜<br /> </td> 
   <td> 주 시작 날짜<br /> </td> 
  </tr> 
  <tr> 
   <td> 짧은 날짜<br /> </td> 
   <td> <p>%2M/%2D/%4Y</p><p><strong>예:09/25/2018</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y</p><p><strong>예:25/09/2018</strong></p> </td> 
  </tr> 
  <tr> 
   <td> <br /> 시간이 있는 짧은 날짜 </td> 
   <td> <p>%2M/%2D/%4Y %I:%2N:%2S %P</p><p><strong>예:09/25/2018 10:47:25 PM</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y %2H:%2N:%2S</p><p><strong>예:25/09/2018 22:47:25</strong></p> </td> 
  </tr> 
 </tbody> 
</table>

### 열거형 {#add-values-in-an-enumeration}에 값 추가

드롭다운 목록이 있는 입력 필드를 사용하여 드롭다운 목록에 옵션으로 제공되는 열거형 값을 입력할 수 있습니다. 열거형 값은 저장된 후 드롭다운 목록에서 사용할 수 있습니다. 예를 들어 수신자 프로필의 **[!UICONTROL General]** 탭의 **[!UICONTROL City]** 필드에서 London을 입력할 수 있습니다. Enter 키를 눌러 이 값을 확인하면 필드와 연관된 열거형에 이 값을 저장할 것인지 묻는 메시지가 표시됩니다.

![](assets/s_ncs_user_wizard_email_bat_substitute_email.png)

**[!UICONTROL Yes]**&#x200B;을 클릭하면 관련 필드의 콤보 상자에서 이 값을 사용할 수 있습니다(이 경우:**[!UICONTROL London]**).

>[!NOTE]
>
>열거형(&#39;항목별 목록&#39;이라고도 함)은 관리자가 **[!UICONTROL Administration > Platform > Enumerations]** 섹션을 통해 관리합니다. 자세한 내용은 [열거형 관리](../../platform/using/managing-enumerations.md)를 참조하십시오.

### 기본 단위 {#default-units}

기간을 설명하는 필드(예: 배달 리소스의 유효성 기간, 작업의 승인 기한 등)에서 이 값은 다음 **units**&#x200B;으로 표시될 수 있습니다.

* **[!UICONTROL s]** 몇 초 동안
* **[!UICONTROL mn]** 몇 분 동안
* **[!UICONTROL h]** 몇 시간 동안
* **[!UICONTROL d]** 을 참조하십시오.

![](assets/enter_unit_sample.png)

## 자습서 비디오 {#video}

이 비디오는 Campaign Classic 작업 영역을 제공합니다.

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)

추가 Campaign Classic 방법 비디오는 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.
