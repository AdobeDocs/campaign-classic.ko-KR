---
title: 워크플로우 관리
seo-title: 워크플로우 관리
description: 워크플로우 관리
seo-description: null
page-status-flag: never-activated
uuid: 8b6320c0-1aae-4acd-a698-03f9bebd916d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ee724240-c337-489d-a21b-5f3aec1f247a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 워크플로우 관리{#managing-workflows}

기본적으로 새 워크플로우는 미리 구성된 워크플로우 템플릿(nms:recipient)을 기반으로 합니다. Nms_DefaultRcpSchema 옵션에서 참조되는 사용자 지정 **테이블을** 자동으로 기반으로 하려면(인터페이스 [섹션 구성 참조)](../../configuration/using/configuring-the-interface.md) 새 워크플로템플릿을 만들어야 합니다.

노드를 통해 새 템플릿을 **[!UICONTROL Resources > Templates > Workflow templates]** 만듭니다. 템플릿의 속성에서 제공된 차원은 외부 받는 사람 테이블과 일치합니다.

최근에 만든 템플릿을 기반으로 새로운 워크플로우를 설정하면, 워크플로우의 전역 타깃팅 및 필터링 차원에 대해 기본적으로 개인화된 테이블이 선택됩니다.

따라서 워크플로우에서 사용되는 모든 활동은 추가적인 수동 구성 없이 사용자 정의 테이블을 사용합니다.

For more information on workflows, refer to [this section](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)

