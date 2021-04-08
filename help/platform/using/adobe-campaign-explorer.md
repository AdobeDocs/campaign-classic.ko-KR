---
solution: Campaign Classic
product: campaign
title: Adobe Campaign 탐색기 사용
description: 캠페인 탐색기 사용 방법 알아보기
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 21656cc2-15a1-4156-8897-ea4fe3e9b97f
translation-type: tm+mt
source-git-commit: d7eabfbebf016d2632d95d34a5b36719ccc1d88a
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 1%

---


# Adobe Campaign 탐색기 사용 {#using-adobe-campaign-explorer}

Adobe Campaign 탐색기는 도구 모음 아이콘을 통해 액세스할 수 있습니다. Adobe Campaign의 모든 Adobe Campaign 기능, 구성 화면 및 일부 플랫폼 요소의 보다 자세한 보기를 이용할 수 있습니다.

**[!UICONTROL Explorer]** 작업 영역은 다음 세 영역으로 분할됩니다.

![](assets/s_ncs_user_navigation.png)

**1 - 트리**:트리의 컨텐츠를 개인화할 수 있습니다(노드 추가, 이동 또는 삭제). 이 절차는 전문 사용자에게만 해당됩니다. 자세한 내용은 [이 섹션](#about-navigation-hierarchy)을 참조하십시오.

**2 - 목록**:이 목록을 필터링하거나 검색을 실행하거나 정보를 추가하거나 데이터를 정렬할 수 있습니다. [자세히 알아보기](adobe-campaign-ui-lists.md)

**3 - 세부** 사항:선택한 요소의 세부 사항을 표시할 수 있습니다. 오른쪽 상단의 아이콘을 사용하여 이 정보를 전체 화면 형식으로 표시할 수 있습니다.

## 폴더 및 탐색 트리{#about-navigation-hierarchy}

탐색 트리는 파일 브라우저(예: Windows 탐색기)와 같이 작동합니다. 폴더에는 하위 폴더가 있을 수 있습니다. 노드를 선택하면 노드에 해당하는 보기가 표시됩니다.

표시되는 보기는 선택한 행을 편집할 수 있는 스키마 및 입력 양식과 연결된 목록입니다.

![](assets/d_ncs_integration_navigation.png)

트리에 새 폴더를 추가하려면 폴더를 삽입할 분기의 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Add new folder]** 을 선택합니다. 바로 가기 메뉴에서 만들 파일 유형을 선택합니다.

![](assets/d_ncs_integration_navigation_create.png)

이 섹션](../../configuration/using/configuration.md)에서 캠페인 탐색 트리 [를 구성하는 방법을 알아봅니다.

이 섹션](access-management-folders.md)에서 [폴더에 대한 권한을 설정하는 방법에 대해 알아봅니다.

## 폴더 구성 우수 사례

* **기본 제공 폴더 사용**

   기본 제공 폴더를 사용하면 프로젝트에 참여하지 않는 사람들이 애플리케이션을 쉽게 사용하고 유지 관리하고 해결할 수 있습니다. 받는 사람, 목록, 배달 등에 대한 사용자 지정 폴더 구조를 만들 수는 없지만 관리, 프로필 및 Target, 캠페인 관리와 같은 표준 폴더를 사용해야 합니다.

* **하위 폴더 만들기**

   표준 폴더 아래에 기술 워크플로우 배치:관리/프로덕션/기술 워크플로우 및 워크플로우 유형별로 하위 디렉토리를 만듭니다.

* **이름 지정 규칙 설정**

   예를 들어 워크플로우 이름을 알파벳 순으로 지정하여 실행 순서로 정렬할 수 있습니다.

   예제:

   * A1 - 수신자를 가져오고 10:00부터 시작합니다.
   * A2 - 표 가져오기, 11:00부터 시작합니다.

* **사용자가 시작할 템플릿 만들기**

   사용자별로 고유한 배달 템플릿, 워크플로우 템플릿, 캠페인 템플릿을 만듭니다. 이 구조를 사용하면 시간을 절약하고 각 사용자에 대해 올바른 배달 매핑 및 유형이 사용되는지 확인할 수 있습니다.

## 화면 해상도 {#screen-resolution}

최적의 탐색 및 유용성을 위해 Adobe은 최소 1600x900픽셀의 화면 해상도를 사용하는 것이 좋습니다.

>[!CAUTION]
>
>1600x900 픽셀 이하의 해상도는 Adobe Campaign에서 지원합니다.

**[!UICONTROL Explorer]** 작업 영역에서 **[!UICONTROL Details]** 영역의 일부 부분이 잘린 것으로 나타나면 영역 위쪽의 화살표를 사용하여 확장하거나 **[!UICONTROL Enlarge]** 단추를 클릭합니다.

![](assets/s_ncs_user_resolution.png)

## 목록 검색 및 사용자 지정 {#browsing-lists}

이 섹션](adobe-campaign-ui-lists.md)에서 목록 [을(를) 검색하고, 관리하고, 사용자 지정하는 방법을 알아봅니다.
