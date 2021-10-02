---
product: campaign
title: 템플릿 정보
description: 템플릿 정보
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: 8b970705f0da6a9e09de9fadb3e1a8c5f4814f9f
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 2%

---

# 템플릿 정보{#about-templates}

![](../../assets/common.svg)

게재 구성을 재사용하기 위해 게재 템플릿에 저장할 수 있습니다. 템플릿에는 게재의 전체 또는 일부 구성이 포함될 수 있습니다.

게재 템플릿은 이 장에 설명된 대로 수동으로 실행하거나 이벤트(설정된 시간에 시작됨, 서버에 파일이 도착할 때 등)에 따라 실행할 수 있습니다. 트리의 **[!UICONTROL Resources > Templates > Delivery templates]** 노드를 통해 게재 템플릿을 구성할 수 있습니다.

![](assets/s_user_template_list.png)

템플릿에는 두 가지 유형이 있습니다.

1. Adobe Campaign 기본 제공 템플릿

   기본 템플릿은 시스템에서 삭제할 수 없습니다. 각 게재 채널에 대한 최소 구성이 포함됩니다. 그러나 관리자는 사용자에게 특정 기능을 제한하거나 기본값을 제공할 수 있습니다(추적 활성화, 보낸 사람 이메일 주소 등). 기본 시나리오는 템플릿 목록에서 굵게 표시됩니다. 이를 수정하려면 복제해야 합니다.

1. 사전 정의된 게재 템플릿

   Adobe Campaign 관리자는 새 게재 템플릿을 만들 수 있습니다. 운영자(적절한 액세스 권한이 있는 사용자)가 사용하거나 서버 프로세스에 의해 자동으로 재사용할 수 있습니다. 예를 들어 이메일 게재 템플릿을 구성할 수 있으며, 사용자가 이 템플릿을 사용하여 게재를 만들 때 텍스트나 HTML 컨텐츠를 입력한 다음 게재하면 됩니다. 관리자가 다른 선택 사항을 이미 정의했습니다.

>[!NOTE]
>
>사용 가능한 템플릿은 액세스 권한, 인스턴스 구성 및 컨텍스트에 따라 다릅니다. 예를 들어 정보 서비스를 만들 때 확인 메시지에 게재 템플릿을 연결할 수 있습니다. 그런 다음 대상 매핑이 구독 매핑인 템플릿에만 액세스할 수 있습니다. 자세한 내용은 [대상 매핑 선택](selecting-a-target-mapping.md) 및 [서비스 및 구독 정보](about-services-and-subscriptions.md)를 참조하십시오.
