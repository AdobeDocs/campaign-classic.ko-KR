---
solution: Campaign Classic
product: campaign
title: 워크플로우 관리
description: 워크플로우 관리
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 4%

---


# 워크플로우 관리{#managing-workflows}

기본적으로 새 워크플로우는 미리 구성된 워크플로우 템플릿을 기반으로 하며 수신자 테이블(nms:recipient)을 기반으로 합니다. **Nms_DefaultRcpSchema** 옵션([인터페이스 구성](../../configuration/using/configuring-the-interface.md) 섹션 참조)에서 참조한 받는 사람의 사용자 정의 테이블을 기반으로 수신자가 자동으로 표시되도록 하려면 새 워크플로 템플릿을 만들어야 합니다.

**[!UICONTROL Resources > Templates > Workflow templates]** 노드를 통해 새 템플릿을 만듭니다. 템플릿의 속성에서 제공된 차원이 외부 받는 사람 테이블과 일치합니다.

최근 만든 템플릿을 기반으로 새 워크플로우를 설정하면 워크플로우의 전역 타깃팅 및 필터링 차원에 대해 기본적으로 개인화된 테이블이 선택됩니다.

따라서 워크플로우에서 사용되는 모든 활동은 추가적인 수동 구성 없이 사용자 지정 테이블을 사용합니다.

워크플로우에 대한 자세한 내용은 [이 섹션](../../workflow/using/about-workflows.md)을 참조하십시오.

![](assets/cfg_external_table_workflow.png)

