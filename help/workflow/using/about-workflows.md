---
title: 워크플로우 정보
description: 워크플로우를 통해 프로세스를 자동화하고 데이터 및 고객을 관리하며 메시지 전송 등을 할 수 있습니다.
page-status-flag: never-activated
uuid: 19adb0e5-042d-47a0-9f92-24e4b3045dbe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: introduction
discoiquuid: 868940d1-f19d-4e9a-bffa-8654abb4441c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 16%

---


# 워크플로우 시작하기{#gs-workflows}

## 워크플로우 정보{#about-workflows}

Adobe Campaign에는 애플리케이션 서버의 여러 모듈에 걸쳐 전체 프로세스 및 작업을 구성할 수 있는 워크플로우 모듈이 포함되어 있습니다. 이 포괄적인 그래픽 환경을 사용하면 세분화, 캠페인 실행, 파일 처리, 인력 참여 등의 프로세스를 디자인할 수 있습니다. 워크플로우 엔진은 이러한 프로세스를 실행하고 추적합니다.

예를 들어 워크플로우에서 서버에서 파일을 다운로드하고 압축을 해제한 다음 Adobe Campaign 데이터베이스에 포함된 레코드를 가져올 수 있습니다.

워크플로우에는 알림을 받거나 프로세스를 선택하고 승인할 수 있는 운영자가 한 명 이상 포함될 수도 있습니다. 이러한 방식으로 게재 작업을 만들고, 콘텐츠를 사용하여 작업하도록 한 명 이상의 운영자에게 작업을 할당하고, 대상을 지정하고, 게재를 시작하기 전에 증명을 승인할 수 있습니다.

워크플로우는 캠페인 관리 프로세스의 다양한 컨텍스트 및 단계 내에서 발생합니다.

Adobe Campaign은 워크플로우를 사용하여 다음을 수행합니다.

* 타깃팅 캠페인 수행 For more on this, refer to [Implementation steps](../../workflow/using/building-a-workflow.md#implementation-steps-).
* 캠페인 구축:각 캠페인에 대해 **[!UICONTROL Workflow]** 탭을 사용하여 타겟을 만들고 배달을 만들 수 있습니다. For more on this, refer to [Campaign workflows](../../workflow/using/building-a-workflow.md#campaign-workflows).
* 기술 프로세스 수행:정리, 추적 정보 수집 또는 임시 계산. For more on this, refer to [Technical workflows](../../workflow/using/building-a-workflow.md#technical-workflows).

워크플로우는 프로세스 정의(발생할 것을 나타내는 워크플로우 모델)와 이 프로세스의 인스턴스(실제로 일어나고 있는 일을 나타내는 워크플로우 인스턴스)를 모두 의미합니다.

워크플로우 템플릿은 수행할 다양한 작업과 이러한 작업이 서로 연결되는 방식을 설명합니다. 작업 템플릿은 활동이라고 하며 아이콘으로 표시됩니다. 전환 효과로 서로 연결되어 있습니다.

![](assets/example1.png)

각 워크플로우에는 다음이 포함됩니다.

* **[!UICONTROL Activities]**

   활동은 작업 템플릿에 대해 설명합니다. 사용할 수 있는 다양한 활동은 아이콘으로 다이어그램에 표시됩니다. 각 유형에는 공통 속성과 특정 속성이 있습니다. 예를 들어 모든 활동에는 이름과 레이블이 있지만 **[!UICONTROL Approval]** 활동에만 할당이 있습니다.

   워크플로우 다이어그램에서, 특정 활동은 루프 또는 반복(주기) 작업이 있을 때 여러 작업을 생성할 수 있습니다.

   사용 사례 및 샘플을 포함하여 모든 워크플로우 활동이 [이 섹션에](../../workflow/using/about-activities.md)나열되어 있습니다.

* **[!UICONTROL Transitions]**

   전환 기능을 사용하면 활동을 연결하고 시퀀스를 정의할 수 있습니다. 전환은 소스 활동을 대상 활동에 연결합니다. 소스 활동에 따라 달라지는 다양한 전환 효과가 있습니다. 일부 전환에는 지속 시간, 조건 또는 필터와 같은 추가 매개 변수가 있습니다.

   대상 활동에 연결되지 않은 전환 색상이 주황색으로 표시되고 화살표 머리는 다이아몬드로 표시됩니다.

   >[!NOTE]
   >
   >종료되지 않은 전환이 포함된 워크플로우는 계속 실행할 수 있습니다.경고 메시지가 생성되고 워크플로우가 전환에 도달하면 일시 정지되지만 오류가 생성되지 않습니다. 따라서 작업 과정이 완료되지 않고 작업을 시작하고 작업을 진행하면서 워크플로우를 추가할 수 있습니다.

   워크플로우 구축 방법에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../workflow/using/building-a-workflow.md).

* **[!UICONTROL Worktables]**

   이 작업표는 전환에서 수행하는 모든 정보를 포함합니다. 각 워크플로우에서는 여러 개의 작업 테이블을 사용합니다. 이러한 표에 전달된 데이터는 삭제되지 않는 한 워크플로우의 라이프 사이클 동안 가속화되고 사용할 수 있습니다. 실제로 불필요한 테이블은 워크플로우가 수동적으로 시작될 때마다 제거되고, 대규모 워크플로우가 실행되는 동안에는 서버 과부하를 방지할 수 있습니다.

   워크플로우 데이터 및 표에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../workflow/using/how-to-use-workflow-data.md).

## 주요 원칙 및 모범 사례{#principles-workflows}

워크플로우 프로세스를 자동화하는 데 도움이 되는 지침과 모범 사례를 살펴보려면 다음 섹션을 참조하십시오.

* 이 [페이지의 워크플로우 활동에 대해 자세히 알아보십시오](../../workflow/using/how-to-use-workflow-data.md).
* 이 섹션에서 워크플로우를 구축하는 방법을 [알아봅니다](../../workflow/using/building-a-workflow.md).
* 워크플로우를 사용하여 [이 섹션의 Campaign에서 데이터를 가져오는 방법을 알아봅니다](../../workflow/using/importing-data.md).
* 워크플로우 우수 사례는 [이 페이지에 자세히 설명되어 있습니다](../../workflow/using/workflow-best-practices.md).
* 이 섹션에서 워크플로우 실행에 대한 지침 [을 살펴보십시오](../../workflow/using/starting-a-workflow.md).
* 이 [페이지에서 워크플로우를 모니터링하는 방법을 학습합니다](../../workflow/using/monitoring-workflow-execution.md).
* 사용자에게 [이 페이지의 워크플로우를 사용할 수 있는 액세스 권한을 부여하는 방법에 대해 알아보십시오](../../workflow/using/managing-rights.md).
