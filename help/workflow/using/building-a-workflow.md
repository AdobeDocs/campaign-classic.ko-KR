---
product: campaign
title: 워크플로우 작성
description: 워크플로우 구축 방법 알아보기
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: 8ba20ccd-b03f-4c4f-87c1-a21e80d8e4be
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1624'
ht-degree: 3%

---

# 워크플로우 작성 {#building-a-workflow}

![](../../assets/common.svg)

이 섹션에서는 Campaign에서 워크플로우를 구축하는 주요 원칙과 모범 사례를 자세히 설명합니다.

* 워크플로우를 만들려면 다음을 참조하십시오 [새 워크플로우 만들기](#creating-a-new-workflow)
* 워크플로우 다이어그램을 디자인하려면 다음을 참조하십시오 [활동 추가 및 연결](#adding-and-linking-activities)
* 활동의 매개 변수 및 속성에 액세스하려면 다음을 참조하십시오 [활동 구성](#configuring-activities)
* 디자인 타겟팅 워크플로우의 내용은 [타겟팅 워크플로우](#targeting-workflows)
* 워크플로우를 사용하여 캠페인을 실행합니다. 자세한 내용은 [캠페인 워크플로우](#campaign-workflows)
* 기술 워크플로우에 액세스하여 만들 수 있습니다. 자세한 내용은 [기술 워크플로우](#technical-workflows)
* 템플릿을 사용하여 워크플로우를 만듭니다. 자세한 내용은 [워크플로우 템플릿](#workflow-templates)

## 새 워크플로우 만들기 {#creating-a-new-workflow}

에서 **[!UICONTROL Explorer]**&#x200B;워크플로우 폴더에 액세스합니다. 기본적으로 **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.

을(를) 클릭합니다. **[!UICONTROL New]** 워크플로우 목록 위에 있는 단추.

![](assets/create_a_wf_icon.png)

또는 다음을 사용할 수도 있습니다 **[!UICONTROL Create]** 워크플로우 개요의 단추(**[!UICONTROL Monitoring]** > **[!UICONTROL Workflow]** 링크를 클릭합니다.

![](assets/create_a_wf.png)

레이블을 입력하고 을(를) 클릭합니다. **[!UICONTROL Save]**.

>[!NOTE]
>
>워크플로우 활동 또는 워크플로우 자체의 내부 이름을 수정할 때는 워크플로우를 닫기 전에 워크플로우를 저장하여 새 내부 이름을 올바르게 고려할 수 있도록 합니다.

## 활동 추가 및 연결 {#adding-and-linking-activities}

이제 다양한 활동을 정의하고 이를 다이어그램에서 서로 연결해야 합니다. 이 구성 단계에서 다이어그램 레이블과 워크플로우 상태(편집 진행 중)를 볼 수 있습니다. 창의 아래쪽 섹션은 다이어그램을 편집하는 데만 사용됩니다. 여기에는 도구 모음, 활동 팔레트(왼쪽)와 다이어그램 자체(오른쪽)가 포함되어 있습니다.

![](assets/new-workflow-2.png)

>[!NOTE]
>
>팔레트가 표시되지 않으면 도구 모음에서 첫 번째 버튼을 클릭하여 표시합니다.

활동은 팔레트의 다른 탭 내에서 카테고리별로 그룹화됩니다. 사용 가능한 탭과 활동은 워크플로우 유형(기술, 타깃팅 또는 캠페인 워크플로우)에 따라 달라질 수 있습니다.

* 첫 번째 탭에는 타겟팅 및 데이터 조작 활동이 포함되어 있습니다. 이러한 활동은에 자세히 설명되어 있습니다 [타겟팅 활동](about-targeting-activities.md).
* 두 번째 탭에는 주로 다른 활동을 조정하는 데 사용되는 예약 활동이 포함되어 있습니다. 이러한 활동은에 자세히 설명되어 있습니다 [흐름 제어 활동](about-flow-control-activities.md).
* 세 번째 탭에는 워크플로우에서 사용할 수 있는 도구와 작업이 포함되어 있습니다. 이러한 활동은에 자세히 설명되어 있습니다 [작업 활동](about-action-activities.md).
* 네 번째 탭에는 이메일의 수신 또는 서버에 파일이 도착하는 것과 같이, 주어진 이벤트에 따라 달라지는 활동이 포함되어 있습니다. 이러한 활동은에 자세히 설명되어 있습니다 [이벤트 활동](about-event-activities.md).

다이어그램을 만들려면

1. 팔레트에서 활동을 선택하고 드래그 앤 드롭 작업을 사용하여 다이어그램으로 이동하여 활동을 추가합니다.

   추가 **시작** 활동 및 **배달** 활동 을 참조하십시오.

   ![](assets/new-workflow-3.png)

1. 를 끌어 활동을 서로 연결합니다 **시작** 활동을 전환하여 로 **배달** 활동.

   ![](assets/new-workflow-4.png)

   전환 끝에 새 활동을 배치하여 활동을 이전 활동에 자동으로 연결할 수 있습니다.

1. 필요한 활동을 추가하고 아래 다이어그램에 표시된 대로 서로 연결합니다.

   ![](assets/new-workflow-5.png)

>[!CAUTION]
>
>동일한 워크플로우 내에서 활동을 복사하고 붙여넣을 수 있습니다. 그러나 다른 워크플로우에서는 붙여넣기 활동을 복사하지 않는 것이 좋습니다. 게재 및 스케줄러와 같은 활동에 첨부된 일부 설정은 대상 워크플로우를 실행하는 동안 충돌과 오류가 발생할 수 있습니다. 대신 다음을 수행하는 것이 좋습니다  **복제** 워크플로우. 자세한 내용은 [워크플로우 복제](#duplicating-workflows).

다음 요소를 사용하여 차트의 표시 및 레이아웃을 변경할 수 있습니다.

* **도구 모음 사용**

   다이어그램 편집 도구 모음에서는 워크플로우의 레이아웃 및 실행 기능에 액세스할 수 있습니다.

   ![](assets/s_user_segmentation_wizard_10.png)

   이렇게 하면 편집 도구의 레이아웃을 조정할 수 있습니다. 팔레트의 표시 및 그래픽 객체의 개요, 크기 및 정렬

   ![](assets/s_user_segmentation_toolbar.png)

   고급 타깃팅 워크플로우 추적 및 실행과 관련된 아이콘은 다음 보기에서 자세히 설명합니다 [섹션](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **개체 정렬**

   아이콘을 정렬하려면 아이콘을 선택하고 **[!UICONTROL Align vertically]** 또는 **[!UICONTROL Align horizontally]** 아이콘.

   를 사용하십시오 **CTRL** 여러 개의 분산된 활동을 선택하거나 하나 이상의 활동을 선택 취소하는 키. 다이어그램 배경을 클릭하여 모든 항목을 선택 취소합니다.

* **이미지 관리**

   다이어그램의 배경 이미지와 다양한 활동과 관련된 배경 이미지를 사용자 지정할 수 있습니다. 을(를) 참조하십시오. [활동 이미지 관리](managing-activity-images.md).

## 활동 구성 {#configuring-activities}

활동을 두 번 클릭하여 구성하거나 마우스 오른쪽 단추를 클릭하고 을 선택합니다 **[!UICONTROL Open...]**.

>[!NOTE]
>
>캠페인 워크플로우 활동은 [이 섹션](about-activities.md).

첫 번째 탭에는 기본 구성이 포함되어 있습니다. 다음 **[!UICONTROL Advanced]** 탭에는 오류가 발생할 때 동작을 정의하고 활동에 대한 실행 기간을 지정하고 초기화 스크립트를 입력하는 데 특별히 사용되는 추가 매개 변수가 포함되어 있습니다.

활동을 더 잘 이해하고 워크플로우 정확성을 향상시키기 위해 활동에 설명을 입력할 수 있습니다. 연산자가 활동을 스크롤할 때 자동으로 표시됩니다.

![](assets/example1-comment.png)

## 타겟팅 워크플로우 {#targeting-workflows}

타겟팅 워크플로우를 사용하여 여러 게재 타겟을 만들 수 있습니다. 워크플로우 활동을 통해 쿼리를 만들고, 특정 기준에 따라 결합 또는 제외를 정의하고, 예약을 추가할 수 있습니다. 이 타겟팅의 결과는 게재 작업의 타겟으로 사용할 수 있는 목록으로 자동으로 전송될 수 있습니다

데이터 관리 옵션을 사용하면 이러한 활동 외에도 데이터를 조작하고 고급 기능에 액세스하여 복잡한 타겟팅 문제를 해결할 수 있습니다. 자세한 내용은 [데이터 관리](targeting-data.md#data-management).

이러한 모든 활동은 첫 번째 워크플로우 탭에서 찾을 수 있습니다.

>[!NOTE]
>
>타겟팅 활동은 [이 섹션](about-activities.md).

을 통해 타겟팅 워크플로우를 만들고 편집할 수 있습니다. **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** Adobe Campaign 트리의 노드 또는 **[!UICONTROL Profiles and Targets > Targeting workflows]** 홈 페이지의 메뉴.

![](assets/target_wf.png)

캠페인의 프레임워크 내에 있는 타깃팅 워크플로우는 모든 캠페인 워크플로우와 함께 저장됩니다.

### 타겟팅 워크플로우를 만드는 주요 단계 {#implementation-steps-}

타겟팅 워크플로우를 만드는 단계는 다음 섹션에 자세히 설명되어 있습니다.

1. **식별** 데이터베이스의 데이터 - [쿼리 만들기](targeting-data.md#creating-queries)
1. **준비** 게재 요구 사항을 충족하는 데이터 - 참조 [데이터 강화 및 수정](targeting-data.md#enriching-and-modifying-data)
1. **사용** 업데이트 또는 게재 내에서 수행할 데이터 - [데이터베이스 업데이트](how-to-use-workflow-data.md#updating-the-database)

타겟팅 중에 수행한 모든 데이터 보강 및 모든 핸들의 결과는 개인화 필드에 저장되고 액세스할 수 있으며, 특히 개인화된 메시지를 만들 때 사용할 수 있습니다. 자세한 내용은 [Target 데이터](data-life-cycle.md#target-data)

### 차원 타겟팅 및 필터링 {#targeting-and-filtering-dimensions}

데이터 세분화 작업 중에 타겟팅 키가 필터링 차원에 매핑됩니다. 타겟팅 차원을 사용하면 작업의 타겟팅된 모집단을 정의할 수 있습니다. 수신자, 계약 수혜자, 운영자, 가입자 등 필터링 차원을 사용하면 특정 기준에 따라 모집단을 선택할 수 있습니다. 계약자, 뉴스레터 구독자 등

예를 들어, 5년 이상 생명 보험 계약이 있는 클라이언트를 선택하려면 다음 타겟팅 차원을 선택합니다. **클라이언트** 및 다음 필터링 차원: **계약자**. 그런 다음 쿼리 활동 내에서 필터링 조건을 정의할 수 있습니다

타겟팅 차원 선택 단계 중에는 호환되는 필터링 차원만 인터페이스에 제공됩니다.

이 두 차원은 관련되어 있어야 합니다. 따라서, **[!UICONTROL Filtering dimension]** 목록은 첫 번째 필드에 지정된 타겟팅 차원에 따라 다릅니다.

예를 들어 수신자(**수신자**)에서 다음 필터링 차원을 사용할 수 있습니다.

![](assets/query_filter_target_dimensions_1.png)

기간 **웹 애플리케이션**, 목록에는 다음 필터링 차원이 포함됩니다.

![](assets/query_filter_target_dimensions_2.png)

## 캠페인 워크플로우 {#campaign-workflows}

각 캠페인에 대해 **[!UICONTROL Targeting and workflows]** 탭. 이러한 워크플로우는 캠페인에만 적용됩니다.

![](assets/wf-in-op-edit-delivery-tab.png)

이 탭에는 모든 워크플로우와 동일한 활동이 포함되어 있습니다. [자세히 알아보기](#implementation-steps-)

캠페인 워크플로우를 타겟팅 캠페인 외에, 사용 가능한 모든 채널에 대해 게재를 완전히 만들고 구성할 수 있습니다. 워크플로우에서 만든 후, 캠페인의 대시보드에서 이러한 게재를 사용할 수 있습니다. [자세히 알아보기](../../campaign/using/marketing-campaign-deliveries.md)

모든 캠페인 워크플로우는 **[!UICONTROL Administration > Production > Objects created automatically > Campaign workflows]** 노드 아래에 있어야 합니다.

![](assets/campaigns_wf.png)

캠페인 워크플로우 및 구현 예는 [이 페이지](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

## 기술 워크플로우 {#technical-workflows}

기술 워크플로우는 Adobe Campaign과 함께 기본적으로 제공됩니다. 서버에서 주기적으로 실행되도록 예약된 작업 또는 작업입니다. 이를 통해 데이터베이스 유지 관리를 수행하고, 게재에 대한 추적 정보를 전달하며, 게재에 대한 임시 프로세스를 설정할 수 있습니다. 기술 워크플로우는 **[!UICONTROL Administration > Production > Technical workflows]** 노드 아래에 있어야 합니다.

![](assets/navtree.png)

기술 워크플로우를 만드는 데 기본 템플릿을 사용할 수 있습니다. 필요에 맞게 구성할 수 있습니다.

다음 **[!UICONTROL Campaign process]** 하위 폴더는 캠페인 내에서 프로세스를 실행하는 데 필요한 워크플로우를 중앙 집중화합니다. 작업 통지, 재고 관리, 원가 계산 등

>[!NOTE]
>
>각 모듈에 설치된 기술 워크플로우 목록은 [전용 섹션](about-technical-workflows.md).

에서 다른 기술 워크플로우를 만들 수 있습니다 **[!UICONTROL Administration > Production > Technical workflows]** 트리 구조의 노드입니다. 하지만 이 프로세스는 전문가 사용자를 위해 예약되어 있습니다.

제공된 활동은 타깃팅 워크플로우와 동일합니다. [자세히 알아보기](#implementation-steps-)

## 워크플로우 템플릿 {#workflow-templates}

워크플로우 템플릿에는 속성의 전체 구성과 다이어그램 내에서 연결된 활동 범위가 포함되어 있습니다. 이 구성은 사전 구성된 특정 수의 요소를 포함하는 새 워크플로우를 만드는 데 다시 사용할 수 있습니다

기존 템플릿을 기반으로 새 워크플로우 템플릿을 만들거나 워크플로우를 템플릿으로 직접 변경할 수 있습니다.

워크플로우 템플릿은 **[!UICONTROL Resources > Templates > Workflow templates]** 노드 아래에 나열된 상태로 남아 있습니다.

![](assets/s_advuser_wf_template_tree.png)

템플릿 속성을 사용하면 일반적인 워크플로우 속성 외에 이 템플릿을 기반으로 만든 워크플로우의 실행 파일을 지정할 수 있습니다.

![](assets/s_advuser_wf_template_properties.png)

## 워크플로우 복제 {#duplicating-workflows}

다양한 유형의 워크플로우를 복제할 수 있습니다. 복제되고 나면 워크플로우의 수정 사항이 워크플로우의 복사본으로 옮겨지지 않습니다.

>[!CAUTION]
>
>워크플로우에서는 복사-붙여넣기를 사용할 수 있지만 다음을 사용하는 것이 좋습니다 **복제**. 활동을 복사하면 전체 구성이 유지됩니다. 게재 활동(이메일, SMS, 푸시 알림..)의 경우, 활동에 첨부된 게재 개체도 복사되어 충돌이 발생할 수 있습니다.

1. 워크플로우를 마우스 오른쪽 단추로 클릭합니다.
1. 클릭 **복제**.

   ![](assets/duplicate-workflows.png)

1. 워크플로우 창에서 워크플로우 레이블을 변경합니다.
1. **저장**&#x200B;을 클릭합니다.

캠페인 보기에서 중복 기능을 직접 사용할 수는 없습니다.

하지만 인스턴스에 모든 워크플로우를 표시하는 보기를 만들 수 있습니다. 이 보기에서 **복제 대상**.

**먼저 보기를 만들겠습니다.**

1. in **탐색기**&#x200B;에서 보기를 만들어야 하는 폴더로 이동합니다.
1. 마우스 오른쪽 단추를 클릭하고 로 이동합니다. **새 폴더 추가** > **프로세스**, 선택 **워크플로우**.

   ![](assets/add-new-folder-workflows.png)

새 폴더 **워크플로우** 가 만들어집니다.

1. 마우스 오른쪽 단추를 클릭하고 을 선택합니다 **속성**.
1. in **제한**, check **폴더는 보기입니다.** 을(를) 클릭합니다. **저장**.

   ![](assets/folder-is-a-view.png)

이제 폴더가 인스턴스의 모든 워크플로우로 채워집니다.

**캠페인 워크플로우 복제**

1. 워크플로우 보기에서 캠페인 워크플로우를 선택합니다.
1. 마우스 오른쪽 단추 클릭 **복제 대상**.
   ![](assets/duplicate-to-right-click.png)
1. 레이블을 변경합니다.
1. **저장**&#x200B;을 클릭합니다.

워크플로우 보기에서 복제한 워크플로우를 볼 수 있습니다.
