---
solution: Campaign Classic
product: campaign
title: 워크플로우 정보
description: 작업 과정을 통해 프로세스를 자동화하고 데이터 및 고객을 관리하며 메시지 전송 등을 수행할 수 있습니다.
audience: workflow
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 20%

---


# 워크플로우 시작{#gs-workflows}

## 워크플로우 정보{#about-workflows}

Adobe Campaign에는 응용 프로그램 서버의 여러 모듈에 걸쳐 전체 프로세스 및 작업을 구성할 수 있는 워크플로우 모듈이 포함되어 있습니다. 이 포괄적인 그래픽 환경을 사용하면 세분화, 캠페인 실행, 파일 처리, 인력 참여 등의 프로세스를 디자인할 수 있습니다. 워크플로우 엔진은 이러한 프로세스를 실행하고 추적합니다.

예를 들어 워크플로우에서 서버에서 파일을 다운로드하고 압축을 해제한 다음 Adobe Campaign 데이터베이스에 포함된 레코드를 가져올 수 있습니다.

워크플로우에는 알림을 받거나 프로세스를 선택하고 승인할 수 있는 운영자가 한 명 이상 포함될 수도 있습니다. 이러한 방식으로 게재 작업을 만들고, 콘텐츠를 사용하여 작업하도록 한 명 이상의 운영자에게 작업을 할당하고, 대상을 지정하고, 게재를 시작하기 전에 증명을 승인할 수 있습니다.

워크플로우는 캠페인 관리 프로세스의 다양한 컨텍스트 및 단계 내에서 발생합니다.

Adobe Campaign은 워크플로우를 사용하여 다음을 수행합니다.

* 타깃팅 캠페인을 수행합니다. [자세히 알아보기](../../workflow/using/building-a-workflow.md#implementation-steps-)
* 캠페인 만들기:각 캠페인에 대해 **[!UICONTROL Workflow]** 탭을 사용하여 대상을 만들고 배달을 만들 수 있습니다. [자세히 알아보기](../../workflow/using/building-a-workflow.md#campaign-workflows)
* 기술 프로세스 수행:정리, 추적 정보 수집 또는 임시 계산. [자세히 알아보기](../../workflow/using/building-a-workflow.md#technical-workflows)

워크플로우는 프로세스 정의(발생할 것으로 보이는 작업을 나타내는 워크플로우 모델)와 이 프로세스의 인스턴스(실제로 일어나고 있는 일을 나타내는 워크플로우 인스턴스)를 모두 의미합니다.

워크플로우 템플릿은 수행할 다양한 작업과 이러한 작업이 서로 연결되는 방식을 설명합니다. 작업 템플릿을 활동이라고 하며 아이콘으로 표시됩니다. 전환으로 함께 연결됩니다.

![](assets/example1.png)

각 워크플로우에는 다음이 포함됩니다.

* **[!UICONTROL Activities]**

   활동은 작업 템플릿을 설명합니다. 사용할 수 있는 다양한 활동은 아이콘으로 다이어그램에 표시됩니다. 각 유형에는 공통 속성과 특정 속성이 있습니다. 예를 들어 모든 활동에는 이름과 레이블이 있지만 **[!UICONTROL Approval]** 활동에는 할당만 있습니다.

   워크플로우 다이어그램에서, 특정 활동은 특히 루프 또는 반복(주기) 작업이 있는 경우 여러 작업을 생성할 수 있습니다.

   모든 워크플로우 활동은 사용 사례 및 샘플을 포함하여 [이 섹션](../../workflow/using/about-activities.md)에 나열됩니다.

* **[!UICONTROL Transitions]**

   전환을 사용하면 활동을 연결하고 시퀀스를 정의할 수 있습니다. 전환은 소스 활동을 대상 활동에 연결합니다. 소스 활동에 따라 달라지는 다양한 전환 효과가 있습니다. 일부 전환에는 지속 시간, 조건 또는 필터와 같은 추가 매개 변수가 있습니다.

   대상 활동에 연결되지 않은 전환이 주황색으로 표시되고 화살표 머리는 다이아몬드로 표시됩니다.

   >[!NOTE]
   >
   >종료되지 않은 전환이 포함된 워크플로우는 계속 실행할 수 있습니다.경고 메시지가 생성되고 워크플로우가 전환에 도달하면 일시 정지되지만 오류가 생성되지 않습니다. 따라서 작업 과정이 완료되지 않고 작업을 시작하고 작업을 진행하면서 해당 워크플로우에 추가할 수 있습니다.

   워크플로우를 빌드하는 방법에 대한 자세한 내용은 [이 섹션](../../workflow/using/building-a-workflow.md)을 참조하십시오.

* **[!UICONTROL Worktables]**

   작업 테이블에는 변환에서 수행하는 모든 정보가 포함되어 있습니다. 각 워크플로우에서는 여러 작업 테이블을 사용합니다. 이러한 표에 전달된 데이터는 삭제되지 않는 한 워크플로우의 수명 주기 동안 가속화되고 사용할 수 있습니다. 실제로, 필요하지 않은 테이블은 워크플로우가 수동적으로 처리될 때마다 그리고 가장 큰 워크플로우가 실행되면서 서버가 오버로드되지 않도록 삭제됩니다.

   워크플로우 데이터 및 표에 대한 자세한 내용은 [이 섹션](../../workflow/using/how-to-use-workflow-data.md)을 참조하십시오.

## 주요 원칙 및 우수 사례{#principles-workflows}

워크플로우 프로세스를 자동화하는 지침과 모범 사례를 찾으려면 다음 섹션을 참조하십시오.

* [이 페이지](../../workflow/using/how-to-use-workflow-data.md)의 워크플로우 활동에 대해 자세히 알아보십시오.
* [이 섹션](../../workflow/using/building-a-workflow.md)에서 워크플로우를 빌드하는 방법을 알아봅니다.
* 워크플로우를 사용하여 [이 섹션](../../workflow/using/importing-data.md)에서 Campaign의 데이터를 가져오는 방법을 알아봅니다.
* 워크플로 우수 사례는 [이 페이지](../../workflow/using/workflow-best-practices.md)에 자세히 설명되어 있습니다.
* [이 섹션](../../workflow/using/starting-a-workflow.md)에서 워크플로우 실행에 대한 지침을 찾습니다.
* [이 페이지](../../workflow/using/monitoring-workflow-execution.md)에서 워크플로우를 모니터하는 방법을 알아봅니다.
* [이 페이지](../../workflow/using/managing-rights.md)에서 워크플로우를 사용하도록 사용자에게 액세스 권한을 부여하는 방법에 대해 학습합니다.
