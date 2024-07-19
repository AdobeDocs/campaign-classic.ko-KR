---
product: campaign
title: Adobe Campaign 탐색기 사용
description: Campaign 탐색기 사용 방법 알아보기
feature: Overview
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f91d69a4-b794-40f0-b450-de862d7333e2
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 1%

---

# Adobe Campaign 탐색기 사용 {#using-adobe-campaign-explorer}



Adobe Campaign 탐색기는 도구 모음 아이콘을 통해 액세스할 수 있습니다. Adobe Campaign 모든 Adobe Campaign 기능, 구성 화면 및 일부 플랫폼 요소에 대한 자세한 보기에 액세스할 수 있습니다.

**[!UICONTROL Explorer]** 작업 영역은 세 개의 영역으로 나뉩니다.

![](assets/s_ncs_user_navigation.png)

**1 - 트리**: 트리의 콘텐츠(노드 추가, 이동 또는 삭제)를 개인화할 수 있습니다. 이 절차는 전문가 사용자만을 위한 것입니다. 자세한 내용은 [이 섹션](#about-navigation-hierarchy)을 참조하세요.

**2 - 목록**: 이 목록을 필터링하거나, 검색을 실행하거나, 정보를 추가하거나, 데이터를 정렬할 수 있습니다. [자세히 알아보기](adobe-campaign-ui-lists.md).

**3 - 세부 정보**: 선택한 요소의 세부 정보를 표시할 수 있습니다. 오른쪽 위의 아이콘을 사용하면 이 정보를 전체 화면 형식으로 표시할 수 있습니다.

## 폴더 및 탐색 트리{#about-navigation-hierarchy}

탐색 트리는 파일 브라우저(예: Windows 탐색기)처럼 작동합니다. 폴더에는 하위 폴더가 포함될 수 있습니다. 노드를 선택하면 해당 노드에 해당하는 보기가 표시됩니다.

표시된 보기는 선택한 줄을 편집하기 위한 스키마 및 입력 양식과 관련된 목록입니다.

![](assets/d_ncs_integration_navigation.png)

새 폴더를 트리에 추가하려면 폴더를 삽입할 분기의 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Add new folder]** 을(를) 선택합니다. 바로 가기 메뉴에서 생성할 파일 유형을 선택합니다.

![](assets/d_ncs_integration_navigation_create.png)

이 섹션](../../configuration/using/configuration.md)에서 Campaign 탐색 트리 [을(를) 구성하는 방법을 알아봅니다.

폴더 [에 대한 사용 권한을 설정하는 방법은 이 섹션](access-management-folders.md)을 참조하세요.

## 폴더 구성 모범 사례

* **기본 제공 폴더 사용**

  기본 제공 폴더를 사용하면 프로젝트에 관여하지 않는 사람들이 응용 프로그램을 쉽게 사용하고 유지 관리하며 문제를 해결할 수 있습니다. 수신자, 목록, 게재 등에 대한 사용자 정의 폴더 구조를 만들지 않고 관리, 프로필 및 타겟, 캠페인 관리와 같은 표준 폴더를 사용해야 합니다.

* **하위 폴더 만들기**

  기술 워크플로우를 표준 폴더(관리/프로덕션/기술 워크플로우)에 배치하고 워크플로우 유형별로 하위 디렉토리를 만듭니다.

* **명명 규칙 설정**

  예를 들어 실행 순서에 따라 정렬되어 표시되도록 워크플로의 이름을 알파벳 순서로 지정할 수 있습니다.

  예제:

   * A1 - 수신자 가져오기, 10:00에 시작;
   * A2 - 11:00에 시작하는 티켓 가져오기.

* **사용자가 시작할 템플릿 만들기**

  사용자 고유의 게재 템플릿, 워크플로우 템플릿, 캠페인 템플릿을 만듭니다. 이 구조를 사용하면 시간을 절약하고 각 사용자에게 적합한 게재 매핑 및 유형화를 사용할 수 있습니다.

## 화면 해상도 {#screen-resolution}

Adobe 최적의 탐색과 유용성을 위해 최소 1600x900픽셀의 화면 해상도를 사용하는 것이 좋습니다.

>[!CAUTION]
>
>Adobe Campaign에서는 1600x900 픽셀 이하의 해상도를 지원하지 않습니다.

**[!UICONTROL Explorer]** 작업 영역에서 **[!UICONTROL Details]** 영역의 일부 부분이 잘린 것처럼 보이는 경우 영역 위의 화살표를 사용하여 확장하거나 **[!UICONTROL Enlarge]** 단추를 클릭합니다.

![](assets/s_ncs_user_resolution.png)

## 목록 찾아보기 및 사용자 지정 {#browsing-lists}

이 섹션](adobe-campaign-ui-lists.md)에서 [ 목록을 검색, 관리 및 사용자 지정하는 방법을 알아보세요.
