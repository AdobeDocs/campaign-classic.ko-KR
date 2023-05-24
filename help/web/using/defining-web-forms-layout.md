---
product: campaign
title: 웹 양식 레이아웃 정의
description: 웹 양식 레이아웃 정의
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Forms
exl-id: 23ca17f8-de1a-4f9c-8357-3965dc3329b1
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 2%

---

# 웹 양식 레이아웃 정의{#defining-web-forms-layout}



## 컨테이너 만들기 {#creating-containers}

컨테이너를 사용하여 페이지의 필드를 결합하고 레이아웃을 구성할 수 있습니다. 따라서 페이지에서 요소를 구성할 수 있습니다.

양식의 각 페이지에 대해 컨테이너는 **[!UICONTROL Containers]** 도구 모음의 단추.

![](assets/s_ncs_admin_survey_containers_add.png)

최종 렌더링에 레이블을 추가하지 않고 컨테이너를 사용하여 페이지 요소를 그룹화합니다. 요소는 컨테이너 하위 트리로 그룹화됩니다. 표준 컨테이너를 사용하여 레이아웃을 관리할 수 있습니다.

예제:

![](assets/s_ncs_admin_survey_containers_std_arbo.png)

레이블의 위치는 계층 구조에서 컨테이너 아래에 배치된 요소에 적용됩니다. 필요한 경우 각 요소에 대해 오버로드될 수 있습니다. 열을 추가하거나 제거하여 레이아웃을 변경합니다. 다음을 참조하십시오 [페이지에서 필드 위치 지정](#positioning-the-fields-on-the-page).

위의 예에서 렌더링은 다음과 같습니다.

![](assets/s_ncs_admin_survey_containers_std_ex.png)

## 페이지에서 필드 위치 지정 {#positioning-the-fields-on-the-page}

웹 양식의 레이아웃은 각 컨테이너에서 페이지별로 정의되며 필요한 경우 오버로드될 수 있습니다.

페이지는 열로 분류됩니다. 각 페이지에는 특정 수의 열이 포함됩니다. 페이지의 각 필드는 다음과 같습니다 **n** 셀. 컨테이너는 또한 특정 수의 열을 차지하고 포함된 필드는 특정 수의 셀을 차지합니다.

기본적으로 페이지는 단일 열에 작성되며 각 요소는 하나의 셀을 차지합니다. 즉, 아래와 같이 필드가 한 줄 아래에 표시되고 각 필드는 전체 줄을 차지합니다.

![](assets/s_ncs_admin_survey_container_ex.png)

다음 예에서는 기본 구성이 유지됩니다. 페이지는 4개의 컨테이너를 포함하는 단일 열을 차지합니다.

![](assets/s_ncs_admin_survey_container_ex0.png)

각 컨테이너는 하나의 열을 차지하고 각 요소는 하나의 셀을 차지합니다.

![](assets/s_ncs_admin_survey_container_ex0a.png)

렌더링은 다음과 같습니다.

![](assets/s_ncs_admin_survey_container_ex0_rend.png)

디스플레이 매개변수를 조정하여 다음 렌더링을 얻을 수 있습니다.

![](assets/s_ncs_admin_survey_container_ex1_rend.png)

위의 렌더링 예에서 각 입력 필드, 제목 및 이미지는 컨테이너의 열에서 하나의 셀을 차지합니다.

각 컨테이너에서 서식을 수정할 수 있습니다. 이 예제에서는 컨테이너 4의 내용을 두 열에 분산하고 요소를 배포할 수 있습니다.

![](assets/s_ncs_admin_survey_container_ex2_rend.png)

제목과 목록은 각각 하나의 셀(따라서 컨테이너의 전체 라인)을 차지하며 확인란은 두 개의 셀에 걸쳐 있습니다. 입력 필드에 속하는 셀 수는 **[!UICONTROL General]** 탭 또는 **[!UICONTROL Advanced]** 필드 유형에 따라 탭을 선택합니다.

![](assets/s_ncs_admin_survey_container_ex2.png)

## 레이블의 위치 정의 {#defining-the-position-of-labels}

양식의 필드 및 레이블 정렬을 정의할 수 있습니다.

기본적으로 필드 및 페이지의 다른 컨텐츠에 대한 표시 매개 변수는 양식의 일반 구성, 페이지의 구성 또는 상위 컨테이너의 구성(있는 경우)에서 상속됩니다.

전체 양식에 대한 글로벌 표시 매개 변수는 양식 속성 상자에 지정됩니다. 다음 **[!UICONTROL Rendering]** 탭에서는 레이블의 위치를 선택할 수 있습니다.

![](assets/s_ncs_admin_survey_label_position.png)

이 위치는 를 통해 각 페이지, 각 컨테이너 및 각 필드에 대해 오버로드될 수 있습니다. **[!UICONTROL Advanced]** 탭.

지원되는 정렬은 다음과 같습니다.

* 상속됨: 정렬은 상위 요소(기본값), 즉 상위 컨테이너(있는 경우) 또는 페이지에서 상속됩니다.
* 왼쪽/오른쪽: 필드의 오른쪽 또는 왼쪽에 레이블이 배치됩니다.
* 위/아래: 레이블이 필드의 위나 아래에 위치합니다.
* 숨김: 레이블이 표시되지 않습니다.
