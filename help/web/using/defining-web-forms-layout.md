---
solution: Campaign Classic
product: campaign
title: 웹 양식 레이아웃 정의
description: 웹 양식 레이아웃 정의
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 2%

---


# 웹 양식 레이아웃 정의{#defining-web-forms-layout}

## 컨테이너 만들기 {#creating-containers}

컨테이너를 사용하여 페이지의 필드를 결합하고 레이아웃을 구성할 수 있습니다.를 클릭하여 페이지의 요소를 구성합니다.

양식의 각 페이지에 대해, 컨테이너는 도구 모음의 **[!UICONTROL Containers]** 단추를 통해 만들어집니다.

![](assets/s_ncs_admin_survey_containers_add.png)

최종 렌더링에 레이블을 추가하지 않고 페이지의 요소를 그룹화하는 데 컨테이너를 사용합니다. 요소는 컨테이너 하위 트리로 그룹화됩니다. 표준 컨테이너를 사용하여 레이아웃을 관리할 수 있습니다.

예제:

![](assets/s_ncs_admin_survey_containers_std_arbo.png)

레이블의 위치는 계층의 컨테이너 아래에 있는 요소에 적용됩니다. 필요한 경우 각 요소에 대해 오버로드될 수 있습니다. 레이아웃을 변경할 열을 추가하거나 제거합니다. [페이지](#positioning-the-fields-on-the-page)에 필드 배치를 참조하십시오.

위의 예에서 렌더링은 다음과 같습니다.

![](assets/s_ncs_admin_survey_containers_std_ex.png)

## {#positioning-the-fields-on-the-page} 페이지에 필드 배치

웹 양식의 레이아웃은 각 컨테이너의 페이지별로 정의되며 필요한 경우 오버로드할 수 있습니다.

페이지는 열로 분류됩니다.각 페이지에는 특정 개수의 열이 있습니다. 페이지의 각 필드는 **n** 셀을 차지합니다. 또한 컨테이너는 특정 수의 열을 차지하며 컨테이너가 포함하는 필드는 특정 수의 셀을 차지합니다.

기본적으로 페이지는 단일 열에 구축되며 각 요소는 하나의 셀을 차지합니다. 즉, 각 필드는 아래와 같이 전체 줄을 점유하며 서로 아래에 표시됩니다.

![](assets/s_ncs_admin_survey_container_ex.png)

다음 예제에서는 기본 구성이 유지됩니다. 이 페이지는 4개의 컨테이너를 포함하는 단일 열을 차지합니다.

![](assets/s_ncs_admin_survey_container_ex0.png)

각 컨테이너는 하나의 열을 차지하며 각 요소는 하나의 셀을 차지합니다.

![](assets/s_ncs_admin_survey_container_ex0a.png)

렌더링은 다음과 같습니다.

![](assets/s_ncs_admin_survey_container_ex0_rend.png)

다음 렌더링을 얻기 위해 디스플레이 매개변수를 조정할 수 있습니다.

![](assets/s_ncs_admin_survey_container_ex1_rend.png)

위의 렌더링 예에서 각 입력 필드, 제목 및 이미지는 컨테이너 열에 하나의 셀을 차지합니다.

각 컨테이너에서 서식을 수정할 수 있습니다. 이 예에서는 컨테이너 4의 컨텐츠를 2개의 열에 분산하고 요소를 배포할 수 있습니다.

![](assets/s_ncs_admin_survey_container_ex2_rend.png)

제목과 목록은 각각 한 셀(따라서 컨테이너의 전체 줄)을 차지하며 이 확인란은 두 셀 위로 확장됩니다. 입력 필드에 속하는 셀의 수는 필드 유형에 따라 **[!UICONTROL General]** 탭 또는 **[!UICONTROL Advanced]** 탭에 정의됩니다.

![](assets/s_ncs_admin_survey_container_ex2.png)

## 레이블 {#defining-the-position-of-labels} 위치 정의

양식에서 필드 및 레이블 정렬을 정의할 수 있습니다.

기본적으로 페이지의 필드 및 기타 컨텐츠에 대한 표시 매개 변수는 양식의 일반 구성, 페이지 구성 또는 상위 컨테이너가 있는 경우 상위 컨테이너의 구성에서 상속됩니다.

전체 양식의 전역 표시 매개 변수는 양식 속성 상자에 지정됩니다. **[!UICONTROL Rendering]** 탭에서는 레이블 위치를 선택할 수 있습니다.

![](assets/s_ncs_admin_survey_label_position.png)

이 위치는 **[!UICONTROL Advanced]** 탭을 통해 각 페이지, 각 컨테이너 및 각 필드에 대해 오버로드될 수 있습니다.

다음 할당이 지원됩니다.

* 상속됨:정렬은 상위 요소(기본값)에서 상속됩니다. 즉, 상위 컨테이너가 있는 경우 또는 다른 페이지에서 상속됩니다.
* 왼쪽/오른쪽:레이블은 필드의 오른쪽 또는 왼쪽에 배치됩니다.
* 위/아래:레이블은 필드 위 또는 아래에 있습니다.
* 숨김:레이블이 표시되지 않습니다.

