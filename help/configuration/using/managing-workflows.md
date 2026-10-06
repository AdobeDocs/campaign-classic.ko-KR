---
product: campaign
title: 워크플로 관리
description: 워크플로 관리
feature: Workflows, Configuration
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
TQID: 'https://experienceleague.adobe.com/dpHtLw4PYGg35t-ihmw9LGUSbjgeNloUhGXp9KPJaRU'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 4%
---
# 워크플로 관리{#managing-workflows}



기본적으로 새 워크플로는 사전 구성된 워크플로 템플릿을 기반으로 하며 받는 사람 테이블(nms:recipient)을 기반으로 합니다. **Nms_DefaultRcpSchema** 옵션([인터페이스 구성](../../configuration/using/configuring-the-interface.md) 섹션 참조)에서 참조된 수신자의 사용자 지정 테이블을 기반으로 수신자를 자동으로 만들려면 새 워크플로 템플릿을 만들어야 합니다.

**[!UICONTROL Resources > Templates > Workflow templates]** 노드를 통해 새 템플릿을 만듭니다. 템플릿의 속성에서 제공된 차원은 외부 수신자 테이블과 일치합니다.

최근에 만든 템플릿을 기반으로 새 워크플로우를 만들면 워크플로우의 전역 타깃팅 및 필터링 차원에 대해 기본적으로 개인화된 테이블이 선택됩니다.

따라서 워크플로우에 사용된 모든 활동은 추가적인 수동 구성 없이 사용자 지정 테이블을 사용합니다.

워크플로우에 대한 자세한 내용은 [이 섹션](../../workflow/using/about-workflows.md)을 참조하세요.

![](assets/cfg_external_table_workflow.png)
