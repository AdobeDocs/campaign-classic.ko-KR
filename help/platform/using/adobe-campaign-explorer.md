---
product: campaign
title: Adobe Campaign Explorer 사용
description: Campaign Explorer 사용 방법 알아보기
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f91d69a4-b794-40f0-b450-de862d7333e2
source-git-commit: fdb840a9e6349f074378899e07f794b62fb5b054
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 1%

---

# Adobe Campaign 탐색기 사용 {#using-adobe-campaign-explorer}

![](../../assets/v7-only.svg)

도구 모음 아이콘을 통해 Adobe Campaign 탐색기에 액세스할 수 있습니다. 모든 Adobe Campaign 기능, 구성 화면 및 일부 플랫폼 요소에 대한 보다 자세한 보기를 Adobe Campaign에 액세스할 수 있습니다.

다음 **[!UICONTROL Explorer]** 작업 공간은 다음 세 영역으로 나누어집니다.

![](assets/s_ncs_user_navigation.png)

**1 - 트리**: 트리의 컨텐츠를 개인화할 수 있습니다(노드 추가, 이동 또는 삭제). 이 절차는 전문가 사용자만 사용할 수 있습니다. 자세한 내용은  [이 섹션](#about-navigation-hierarchy).)

**2 - 목록**: 이 목록을 필터링하거나, 검색을 실행하거나, 정보를 추가하거나, 데이터를 정렬할 수 있습니다. [자세히 알아보기](adobe-campaign-ui-lists.md)

**3 - 세부 정보**: 선택한 요소의 세부 사항을 표시할 수 있습니다. 오른쪽 상단 섹션의 아이콘을 사용하여 이 정보를 전체 화면 형식으로 표시할 수 있습니다.

## 폴더 및 탐색 트리{#about-navigation-hierarchy}

탐색 트리는 파일 브라우저(예: Windows 탐색기)와 같이 작동합니다. 폴더에는 하위 폴더가 포함될 수 있습니다. 노드를 선택하면 노드에 해당하는 뷰가 표시됩니다.

표시된 뷰는 선택한 라인을 편집할 수 있는 스키마 및 입력 양식과 연관된 목록입니다.

![](assets/d_ncs_integration_navigation.png)

트리에 새 폴더를 추가하려면 폴더를 삽입할 분기의 폴더를 마우스 오른쪽 단추로 클릭하고 을 선택합니다 **[!UICONTROL Add new folder]** . 바로 가기 메뉴에서 만들 파일 유형을 선택합니다.

![](assets/d_ncs_integration_navigation_create.png)

Campaign 탐색 트리를 구성하는 방법 알아보기 [이 섹션](../../configuration/using/configuration.md).

폴더에 대한 권한을 설정하는 방법 알아보기 [이 섹션](access-management-folders.md).

## 폴더 구성 우수 사례

* **기본 제공 폴더 사용**

   기본 제공 폴더를 사용하면 프로젝트에 관여하지 않는 사람들이 애플리케이션을 보다 쉽게 사용, 유지 관리 및 해결할 수 있습니다. 수신자, 목록, 게재 등에 대한 사용자 지정 폴더 구조를 만들지 않지만 관리, 프로필 및 Target, 캠페인 관리와 같은 표준 폴더를 사용해야 합니다.

* **하위 폴더 만들기**

   표준 폴더 아래에 기술 워크플로우 배치: 관리/프로덕션/기술 워크플로우 및 워크플로우 유형별로 하위 디렉토리를 만듭니다.

* **이름 지정 규칙 설정**

   예를 들어 실행 순서로 정렬되도록 워크플로우의 이름을 알파벳순으로 지정할 수 있습니다.

   예제:

   * A1 - 수신자 가져오기, 10:00부터 시작
   * A2 - 가져오기 티켓은 11시에 시작됩니다.

* **사용자가 시작할 템플릿 만들기**

   사용자별 게재 템플릿, 워크플로우 템플릿, 캠페인 템플릿을 만듭니다. 이 구조를 사용하면 시간을 절약할 수 있고, 각 사용자에 대해 올바른 게재 매핑 및 유형화가 사용되는지 확인할 수 있습니다.

## 화면 해상도 {#screen-resolution}

최적의 탐색 및 유용성을 위해 Adobe은 최소 1600x900픽셀의 화면 해상도를 사용하는 것이 좋습니다.

>[!CAUTION]
>
>1600x900픽셀 이하의 해상도는 Adobe Campaign에서 지원하지 않습니다.

에서 **[!UICONTROL Explorer]** 작업 공간(일부 부분이 **[!UICONTROL Details]** 영역이 잘리는 것 같습니다. 영역 위쪽에 있는 화살표를 사용하여 확장하거나 **[!UICONTROL Enlarge]** 버튼을 클릭합니다.

![](assets/s_ncs_user_resolution.png)

## 목록 찾아보기 및 사용자 지정 {#browsing-lists}

목록 검색, 관리 및 사용자 지정 방법을 알아봅니다 [이 섹션](adobe-campaign-ui-lists.md).
