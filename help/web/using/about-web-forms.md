---
product: campaign
title: 웹 양식 시작
description: Campaign에서 웹 양식 시작
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Landing Pages, Web Forms
exl-id: 63602bed-ace6-4632-a735-5d268a7d72d0
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 5%

---

# 웹 양식 시작{#about-web-forms}



Adobe Campaign은 웹 양식을 정의하고 게시하기 위한 그래픽 모듈을 통합하여 입력 및 선택 필드가 포함된 페이지를 만들고 데이터베이스에 데이터를 포함할 수 있습니다. 이를 통해 사용자가 정보를 보거나 입력할 수 있는 웹 페이지를 디자인하고 게시할 수 있습니다.

이 장에서는 웹 양식의 작성 및 관리, 필드 및 페이지 관리 방법과 저장 모드에 대해 자세히 설명합니다.

>[!CAUTION]
>
>개인 정보용으로 모든 외부 리소스에 HTTPS를 사용하는 것이 좋습니다.

## 웹 양식을 만드는 단계 {#steps-for-creating-a-web-form}

이 장에서는 **webForm** 사용 가능한 옵션 및 구성과 Adobe Campaign에 양식을 입력합니다. Adobe Campaign을 사용하면 이 웹 양식을 사용자가 사용할 수 있도록 만들 수 있을 뿐만 아니라 데이터베이스에 있는 답변을 수집 및 보관할 수 있습니다.

>[!CAUTION]
>
>웹 응용 프로그램 및 웹 양식을 구성할 때는 최소 900픽셀 세로 해상도가 필요합니다(예: 1600x900).

웹 양식은 **캠페인** 탭. Adobe Campaign 트리에서 **[!UICONTROL Resources > Online > Web Applications]** 노드 아래에 있어야 합니다.

웹 양식을 만들려면 **[!UICONTROL Create]** 단추를 클릭합니다.

![](assets/webapp_create_new.png)

웹 양식 서식 파일( **[!UICONTROL newWebForm]** 기본적으로 ).

![](assets/s_ncs_admin_survey_select_template.png)

그러면 양식의 대시보드로 이동합니다.

![](assets/webapp_empty_dashboard.png)

다음 **[!UICONTROL Edit]** 탭에서는 컨텐츠를 만들 수 있습니다.

![](assets/webapp_edit_tab.png)

웹 양식의 구성 및 내용을 정의하려면 다음 단계를 수행합니다.

* 먼저 필요한 페이지 및 컨트롤을 만듭니다. 입력 필드, 드롭다운 목록, HTML 컨텐츠 등

   이 단계는 아래에 자세히 설명되어 있습니다.

* 표시할 페이지 순서 및 조건을 정의합니다.

   이 단계는 [웹 양식 페이지 순서 정의](defining-web-forms-page-sequencing.md).

* 필요한 경우 컨텐츠를 번역합니다.

   이 단계는 [웹 양식 번역](translating-a-web-form.md).

## 웹 양식 디자인 정보 {#about-web-forms-designing}

양식의 페이지는 입력 영역(텍스트), 선택 필드(목록, 확인란 등)를 정의하고 구성할 수 있는 특정 편집기를 통해 만들어집니다. 및 정적 요소(이미지, HTML 콘텐츠 등)는 컨테이너로 그룹화할 수 있으며 사용자의 요구 사항에 맞게 레이아웃을 변경할 수 있습니다(자세한 내용은 [컨테이너 만들기](defining-web-forms-layout.md#creating-containers)).

다음 섹션에서는 양식 화면의 콘텐츠 및 레이아웃을 정의하는 방법을 자세히 설명합니다.

* [웹 양식에 필드 추가](adding-fields-to-a-web-form.md),
* [HTML 컨텐츠 삽입](static-elements-in-a-web-form.md#inserting-html-content),
* [웹 양식의 정적 요소](static-elements-in-a-web-form.md),
* [웹 양식 레이아웃 정의](defining-web-forms-layout.md).

>[!NOTE]
>
>* 페이지 디자인 중에 **[!UICONTROL Preview]** 탭. 변경 내용을 보려면 양식을 먼저 저장합니다. 모든 오류는 **[!UICONTROL Log]** 탭.
>* 페이지 표시 및 정보 저장소가 적절한 순서로 발생하는지 확인하려면 웹 양식에서 디버그 모드를 활성화합니다. 이렇게 하려면 로 이동합니다. **[!UICONTROL Preview]** 하위 탭에서 **[!UICONTROL Enable debug mode]** 상자: 수집된 모든 정보와 실행 오류가 각 페이지 하단에 표시됩니다.
>


### 도구 모음에서 아이콘 사용 {#using-the-icons-in-the-toolbar}

도구 모음에서 아이콘을 사용하거나 마우스 오른쪽 단추를 클릭하여 입력 영역을 삽입할 수도 있습니다.

![](assets/s_ncs_admin_webform_add_selection.png)

이 경우 추가할 필드 유형과 응답 저장소 모드를 선택하여 시작합니다.

![](assets/s_ncs_admin_webform_select_storage.png)

클릭 **[!UICONTROL Ok]** 을 눌러 선택 사항을 승인합니다.

![](assets/s_ncs_admin_webform_confirm_storage.png)
