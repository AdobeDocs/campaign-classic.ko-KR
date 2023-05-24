---
product: campaign
title: 워크플로우 관리
description: 워크플로우 관리
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 4%

---

# 워크플로우 관리{#managing-workflows}



기본적으로 새 워크플로우는 사전 구성된 워크플로 템플릿을 기반으로 하며 수신자 테이블(nms:recipient)을 기반으로 합니다. 에서 참조한 수신자의 사용자 지정 테이블을 기반으로 하여 자동으로 수신자를 검색할 수 있도록 해줍니다 **Nms_DefaultRcpSchema** 옵션(참조) [인터페이스 구성](../../configuration/using/configuring-the-interface.md) 섹션), 새 워크플로우 템플릿을 만들어야 합니다.

을(를) 통해 새 템플릿 만들기 **[!UICONTROL Resources > Templates > Workflow templates]** 노드. 템플릿의 속성에서 제공된 차원은 외부 수신자 테이블과 일치합니다.

최근에 만든 템플릿을 기반으로 새 워크플로우를 만들면 워크플로우의 전역 타깃팅 및 필터링 차원에 대해 기본적으로 개인화된 테이블이 선택됩니다.

따라서 워크플로우에 사용된 모든 활동은 추가적인 수동 구성 없이 사용자 지정 테이블을 사용합니다.

워크플로우에 대한 자세한 내용은 [이 섹션](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
