---
product: campaign
title: 워크플로 구축
description: 워크플로우 구축 방법 알아보기
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 8ba20ccd-b03f-4c4f-87c1-a21e80d8e4be
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1624'
ht-degree: 4%

---

# 워크플로 구축 {#building-a-workflow}



이 섹션에서는 Campaign에서 워크플로우를 빌드하는 주요 원칙과 모범 사례를 자세히 설명합니다.

* 워크플로우를 만듭니다. [새 워크플로우 만들기](#creating-a-new-workflow)를 참조하십시오.
* 워크플로 다이어그램을 디자인합니다. [활동 추가 및 연결](#adding-and-linking-activities)을 참조하세요.
* 활동의 매개 변수 및 속성에 액세스합니다. [활동 구성](#configuring-activities)을 참조하십시오.
* 타깃팅 워크플로를 디자인합니다. [타깃팅 워크플로](#targeting-workflows)를 참조하십시오.
* 워크플로우를 사용하여 캠페인을 실행하십시오. [캠페인 워크플로우](#campaign-workflows)를 참조하십시오.
* 기술 워크플로우에 액세스하고 만듭니다. [기술 워크플로우](#technical-workflows)를 참조하십시오.
* 템플릿을 사용하여 워크플로를 만드십시오. [워크플로 템플릿](#workflow-templates) 참조

## 새 워크플로우 만들기 {#creating-a-new-workflow}

**[!UICONTROL Explorer]**&#x200B;에서 워크플로 폴더에 액세스합니다. 기본적으로 **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**&#x200B;를 사용할 수 있습니다.

워크플로 목록 위에 있는 **[!UICONTROL New]** 단추를 클릭합니다.

![](assets/create_a_wf_icon.png)

또는 워크플로 개요(**[!UICONTROL Monitoring]** > **[!UICONTROL Workflow]** 링크)에서 **[!UICONTROL Create]** 단추를 사용할 수도 있습니다.

![](assets/create_a_wf.png)

레이블을 입력하고 **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

>[!NOTE]
>
>워크플로우 활동의 내부 이름 또는 워크플로우 자체를 수정하는 경우, 새 내부 이름을 올바르게 고려할 수 있도록 워크플로우를 닫기 전에 워크플로우를 저장해야 합니다.

## 활동 추가 및 연결 {#adding-and-linking-activities}

이제 다양한 활동을 정의하고 이를 다이어그램에서 함께 연결해야 합니다. 이 구성 단계에서는 다이어그램 레이블 및 워크플로 상태(편집 진행 중)를 볼 수 있습니다. 창의 아래 섹션은 다이어그램을 편집하는 데만 사용됩니다. 여기에는 도구 모음, 활동 팔레트(왼쪽) 및 다이어그램 자체(오른쪽)가 포함되어 있습니다.

![](assets/new-workflow-2.png)

>[!NOTE]
>
>팔레트가 표시되지 않으면 도구 모음의 첫 번째 버튼을 클릭하여 표시합니다.

활동은 팔레트의 다른 탭 내에서 카테고리별로 그룹화됩니다. 사용 가능한 탭 및 활동은 워크플로우 유형(기술, 타겟팅 또는 캠페인 워크플로우)에 따라 달라질 수 있습니다.

* 첫 번째 탭에는 타겟팅 및 데이터 조작 활동이 포함되어 있습니다. 이러한 활동은 [타기팅 활동](about-targeting-activities.md)에 자세히 설명되어 있습니다.
* 두 번째 탭에는 주로 다른 활동을 조정하는 데 사용되는 예약 활동이 포함되어 있습니다. 이러한 활동은 [흐름 제어 활동](about-flow-control-activities.md)에 자세히 설명되어 있습니다.
* 세 번째 탭에는 워크플로우에서 사용할 수 있는 도구와 작업이 포함되어 있습니다. 이러한 활동은 [작업 활동](about-action-activities.md)에 자세히 설명되어 있습니다.
* 네 번째 탭에는 전자 메일 수신 또는 서버에서의 파일 도착과 같이 주어진 이벤트에 의존하는 활동이 포함되어 있습니다. 이러한 활동은 [이벤트 활동](about-event-activities.md)에 자세히 설명되어 있습니다.

다이어그램을 만들려면

1. 팔레트에서 활동을 선택하고 끌어서 놓기 작업을 사용하여 다이어그램으로 이동하여 활동을 추가합니다.

   **시작** 활동을 추가한 다음 다이어그램에 **배달** 활동을 추가하십시오.

   ![](assets/new-workflow-3.png)

1. **시작** 활동 전환을 끌어서 **게재** 활동에 놓아 활동을 함께 연결합니다.

   ![](assets/new-workflow-4.png)

   전환 끝에 새 활동을 배치하여 활동을 이전 활동에 자동으로 연결할 수 있습니다.

1. 아래 다이어그램에 표시된 대로 필요한 활동을 추가하고 함께 연결합니다.

   ![](assets/new-workflow-5.png)

>[!CAUTION]
>
>동일한 워크플로우 내에서 활동을 복사하여 붙여넣을 수 있습니다. 하지만 다른 워크플로우에서는 붙여넣기 활동을 복사하지 않는 것이 좋습니다. 게재 및 스케줄러와 같은 활동에 첨부된 일부 설정은 대상 워크플로우를 실행하는 동안 충돌 및 오류를 초래할 수 있습니다. 대신 워크플로우를 **복제**&#x200B;하는 것이 좋습니다. 자세한 내용은 [워크플로 복제](#duplicating-workflows)를 참조하십시오.

다음 요소를 사용하여 차트의 표시 및 레이아웃을 변경할 수 있습니다.

* **도구 모음 사용**

  다이어그램 편집 도구 모음을 사용하면 워크플로우의 레이아웃 및 실행 기능에 액세스할 수 있습니다.

  ![](assets/s_user_segmentation_wizard_10.png)

  이렇게 하면 팔레트 표시와 그래픽 객체의 개요, 크기 및 정렬과 같은 편집 도구의 레이아웃을 조정할 수 있습니다.

  ![](assets/s_user_segmentation_toolbar.png)

  진행률 및 로그 표시와 관련된 아이콘은 다음 섹션에 자세히 설명되어 있습니다.

   * [진행 상황 표시](../../workflow/using/monitoring-workflow-execution.md#displaying-progress)
   * [로그 표시](../../workflow/using/monitoring-workflow-execution.md#displaying-logs)

* **개체 정렬**

  아이콘을 정렬하려면 해당 아이콘을 선택하고 **[!UICONTROL Align vertically]** 또는 **[!UICONTROL Align horizontally]** 아이콘을 클릭합니다.

  **CTRL** 키를 사용하여 흩어져 있는 여러 활동을 선택하거나 하나 이상의 활동을 선택 취소하십시오. 다이어그램 배경을 클릭하여 모든 항목을 선택 취소합니다.

* **이미지 관리**

  다이어그램의 배경 이미지와 다양한 활동과 관련된 배경 이미지를 사용자 지정할 수 있습니다. [활동 이미지 변경](managing-activity-images.md)을 참조하세요.

## 활동 구성 {#configuring-activities}

활동을 두 번 클릭하여 구성하거나 마우스 오른쪽 단추를 클릭하고 **[!UICONTROL Open...]**&#x200B;을(를) 선택합니다.

>[!NOTE]
>
>캠페인 워크플로우 활동에 대해서는 [이 섹션](about-activities.md)에 자세히 설명되어 있습니다.

첫 번째 탭에는 기본 구성이 포함되어 있습니다. **[!UICONTROL Advanced]** 탭에는 추가 매개 변수가 포함되어 있습니다. 이 매개 변수는 특히 오류가 발생할 때 동작을 정의하고, 활동의 실행 기간을 지정하고, 초기화 스크립트를 입력하는 데 사용됩니다.

활동을 더 잘 이해하고 워크플로우 가독성을 향상시키기 위해 활동에 주석을 입력할 수 있습니다. 주석은 운영자가 활동을 스크롤할 때 자동으로 표시됩니다.

![](assets/example1-comment.png)

## 타겟팅 워크플로 {#targeting-workflows}

타겟팅 워크플로우를 사용하면 여러 게재 타겟을 구축할 수 있습니다. 워크플로우 활동 덕분에 쿼리를 만들고, 특정 기준에 따라 유니온 또는 제외를 정의하고, 예약을 추가할 수 있습니다. 이 타겟팅의 결과는 게재 작업의 타겟이 될 수 있는 목록으로 자동으로 전송될 수 있습니다

이러한 활동 외에도 데이터 관리 옵션을 사용하면 데이터를 조작하고 고급 기능에 액세스하여 복잡한 타겟팅 문제를 해결할 수 있습니다. 자세한 내용은 [데이터 관리](targeting-data.md#data-management)를 참조하세요.

이러한 모든 활동은 첫 번째 워크플로우 탭에서 찾을 수 있습니다.

>[!NOTE]
>
>타깃팅 활동이 [이 섹션](about-activities.md)에 자세히 설명되어 있습니다.

타깃팅 워크플로는 Adobe Campaign 트리의 **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** 노드 또는 홈 페이지의 **[!UICONTROL Profiles and Targets > Targeting workflows]** 메뉴를 통해 만들고 편집할 수 있습니다.

![](assets/target_wf.png)

캠페인 프레임워크 내의 타겟팅 워크플로우는 모든 캠페인 워크플로우와 함께 저장됩니다.

### 타겟팅 워크플로우를 만드는 주요 단계 {#implementation-steps-}

타겟팅 워크플로우를 만드는 단계는 다음 섹션에 자세히 설명되어 있습니다.

1. 데이터베이스에서 **데이터 식별** - [쿼리 만들기](targeting-data.md#creating-queries) 참조
1. 게재 요구 사항을 충족하도록 **데이터 준비** - [데이터 강화 및 수정](targeting-data.md#enriching-and-modifying-data) 참조
1. **업데이트 또는 게재 내에서 데이터를 사용**&#x200B;합니다. [데이터베이스 업데이트](how-to-use-workflow-data.md#updating-the-database)를 참조하세요.

타겟팅 중에 수행되는 모든 보강 및 모든 처리의 결과는 개인화 필드에 저장되고 액세스할 수 있습니다. 특히 개인화된 메시지를 만들 때 사용할 수 있습니다. 자세한 내용은 [대상 데이터](data-life-cycle.md#target-data)를 참조하세요.

### 차원 타겟팅 및 필터링 {#targeting-and-filtering-dimensions}

데이터 세분화 작업 중에 타겟팅 키는 필터링 차원에 매핑됩니다. 타기팅 차원을 사용하면 수신자, 약정 수혜자, 운영자, 구독자 등 작업에서 타기팅하는 집단을 정의할 수 있습니다. 필터링 차원을 사용하면 약정 소유자, 뉴스레터 구독자 등 특정 기준에 따라 모집단을 선택할 수 있습니다.

예를 들어, 5년 이상 생명 보험 계약을 보유한 클라이언트를 선택하려면 다음 대상 차원을 선택합니다. **클라이언트** 및 필터링 차원: **계약 소유자**. 그런 다음 쿼리 활동 내에 필터링 조건을 정의할 수 있습니다

타겟팅 차원 선택 단계 동안 호환되는 필터링 차원만 인터페이스에서 제공됩니다.

이 두 차원은 관련되어야 합니다. 따라서 **[!UICONTROL Filtering dimension]** 목록의 콘텐츠는 첫 번째 필드에 지정된 타겟팅 차원에 따라 다릅니다.

예를 들어 수신자(**recipient**)의 경우 다음 필터링 차원을 사용할 수 있습니다.

![](assets/query_filter_target_dimensions_1.png)

**웹 응용 프로그램**&#x200B;의 경우 목록에 다음 필터링 차원이 포함됩니다.

![](assets/query_filter_target_dimensions_2.png)

## 캠페인 워크플로 {#campaign-workflows}

각 캠페인에 대해 **[!UICONTROL Targeting and workflows]** 탭에서 실행할 워크플로우를 만들 수 있습니다. 이러한 워크플로우는 캠페인에만 적용됩니다.

![](assets/wf-in-op-edit-delivery-tab.png)

이 탭에는 모든 워크플로우와 동일한 활동이 포함되어 있습니다. [자세히 알아보기](#implementation-steps-)

캠페인 워크플로우를 사용하면 타깃팅 캠페인 외에도 사용 가능한 모든 채널에 대한 게재를 전적으로 만들고 구성할 수 있습니다. 워크플로우에서 게재를 만들면 캠페인의 대시보드에서 이러한 게재를 사용할 수 있습니다. [자세히 알아보기](../../campaign/using/marketing-campaign-deliveries.md)

모든 캠페인 워크플로는 **[!UICONTROL Administration > Production > Objects created automatically > Campaign workflows]** 노드에서 중앙 집중화됩니다.

![](assets/campaigns_wf.png)

캠페인 워크플로우 및 구현 예제는 [이 페이지](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)에 자세히 설명되어 있습니다.

## 기술 워크플로 {#technical-workflows}

기술 워크플로우는 Adobe Campaign과 함께 즉시 제공됩니다. 서버에서 주기적으로 실행되도록 예약된 작업 또는 작업입니다. 이를 통해 데이터베이스 유지 관리를 수행하고, 게재에 대한 추적 정보를 전달하고, 게재에 대한 임시 프로세스를 설정할 수 있습니다. 기술 워크플로우는 **[!UICONTROL Administration > Production > Technical workflows]** 노드를 통해 구성됩니다.

![](assets/navtree.png)

기술 워크플로우를 만드는 데 기본 템플릿을 사용할 수 있습니다. 필요에 맞게 구성할 수 있습니다.

**[!UICONTROL Campaign process]** 하위 폴더는 캠페인 내에서 프로세스를 실행하는 데 필요한 워크플로(작업 알림, 재고 관리, 비용 계산 등)를 중앙 집중화합니다.

>[!NOTE]
>
>각 모듈과 함께 설치된 기술 워크플로우 목록은 [전용 섹션](about-technical-workflows.md)에서 사용할 수 있습니다.

트리 구조의 **[!UICONTROL Administration > Production > Technical workflows]** 노드에서 다른 기술 워크플로우를 만들 수 있습니다. 그러나 이 프로세스는 전문가 사용자용으로 예약되어 있습니다.

제공되는 활동은 타겟팅 워크플로우와 동일합니다. [자세히 알아보기](#implementation-steps-)

## 워크플로 템플릿 {#workflow-templates}

워크플로우 템플릿에는 속성의 전체 구성과 다이어그램 내에서 연결되는 다양한 활동이 포함됩니다. 이 구성은 특정 수의 사전 구성된 요소를 포함하는 새 워크플로를 만드는 데 재사용할 수 있습니다

기존 템플릿을 기반으로 새 워크플로우 템플릿을 만들거나 워크플로우를 템플릿으로 직접 변경할 수 있습니다.

워크플로 템플릿은 Adobe Campaign 트리의 **[!UICONTROL Resources > Templates > Workflow templates]** 노드에 저장됩니다.

![](assets/s_advuser_wf_template_tree.png)

일반적인 워크플로우 속성 외에도 템플릿 속성을 사용하여 이 템플릿을 기반으로 만든 워크플로우의 실행 파일을 지정할 수 있습니다.

![](assets/s_advuser_wf_template_properties.png)

## 중복 워크플로우 {#duplicating-workflows}

다양한 유형의 워크플로우를 복제할 수 있습니다. 복제되고 나면 워크플로우의 수정 사항이 워크플로우의 복사본으로 옮겨지지 않습니다.

>[!CAUTION]
>
>워크플로우에서는 복사-붙여넣기를 사용할 수 있지만 **복제**&#x200B;를 사용하는 것이 좋습니다. 활동을 복사하면 전체 구성이 유지됩니다. 게재 활동(이메일, SMS, 푸시 알림...)의 경우 활동에 첨부된 게재 개체도 복사되며 이로 인해 충돌이 발생할 수 있습니다.

1. 워크플로우를 마우스 오른쪽 버튼으로 클릭합니다.
1. **복제**&#x200B;를 클릭합니다.

   ![](assets/duplicate-workflows.png)

1. 워크플로우 창에서 워크플로우 레이블을 변경합니다.
1. **저장**&#x200B;을 클릭합니다.

중복 기능은 캠페인 보기에서 직접 사용할 수 없습니다.

하지만 인스턴스의 모든 워크플로를 표시하는 보기를 만들 수 있습니다. 이 보기에서 **복제 대상**&#x200B;을 사용하여 워크플로우를 복제할 수 있습니다.

**보기 만들기**

1. **탐색기**&#x200B;에서 보기를 만드는 데 필요한 폴더로 이동합니다.
1. 마우스 오른쪽 단추를 클릭하고 **새 폴더 추가** > **프로세스**(으)로 이동한 다음 **워크플로**&#x200B;를 선택합니다.

   ![](assets/add-new-folder-workflows.png)

새 폴더 **워크플로**&#x200B;가 만들어집니다.

1. 마우스 오른쪽 단추를 클릭하고 **속성**&#x200B;을 선택합니다.
1. **제한**&#x200B;에서 **폴더가 보기임**&#x200B;을 확인하고 **저장**&#x200B;을 클릭하세요.

   ![](assets/folder-is-a-view.png)

이제 폴더가 인스턴스의 모든 워크플로우로 채워집니다.

**캠페인 워크플로우 복제**

1. 워크플로우 보기에서 캠페인 워크플로우를 선택합니다.
1. **복제 대상**&#x200B;을 마우스 오른쪽 단추로 클릭합니다.
   ![](assets/duplicate-to-right-click.png)
1. 레이블을 변경합니다.
1. **저장**&#x200B;을 클릭합니다.

워크플로우 보기에서 복제된 워크플로우를 볼 수 있습니다.
