---
title: 템플릿 기본 정보
seo-title: 템플릿 기본 정보
description: 템플릿 기본 정보
seo-description: null
page-status-flag: never-activated
uuid: 13b5ad3a-aded-43b8-ae4d-c23aa7bc17bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: 22e289d0-c33c-4daa-a893-b292e523f30b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 템플릿 기본 정보{#about-templates}

배달 구성을 다시 사용하려면 배달 템플릿에 저장할 수 있습니다. 템플릿에 배달의 전체 또는 부분 구성이 포함될 수 있습니다.

배달 템플릿은 이 장에 설명된 대로, 또는 이벤트(설정된 시간에 실행, 서버에 파일 도착 등)에 따라 수동으로 실행할 수 있습니다. 배달 템플릿은 트리의 **[!UICONTROL Resources > Templates > Delivery templates]** 노드를 통해 구성할 수 있습니다.

![](assets/s_user_template_list.png)

템플릿에는 두 가지 유형이 있습니다.

1. Adobe Campaign 기본 제공 템플릿

   기본 템플릿은 시스템에서 삭제할 수 없습니다. 각 배달 채널에 대한 최소 구성이 포함됩니다. 그러나 관리자는 특정 기능을 제한하거나 사용자에게 기본값을 제공할 수 있습니다(활성화 추적, 보낸 사람 이메일 주소 등). 기본 시나리오는 템플릿 목록에 굵게 표시됩니다. 이를 수정하려면 해당 항목을 복제해야 합니다.

1. 사전 정의된 배달 템플릿

   Adobe Campaign 관리자는 새 배달 템플릿을 만들 수 있습니다. 연산자는(적절한 액세스 권한이 있는 사용자) 또는 서버 프로세스에서 자동으로 다시 사용할 수 있습니다. 예를 들어 이메일 배달 템플릿을 구성할 수 있으며, 사용자가 이 템플릿을 사용하여 배달을 만들 때 텍스트 또는 HTML 컨텐츠를 입력하고 전달하면 됩니다.다른 선택 사항은 관리자가 이미 정의했습니다.

>[!NOTE]
>
>사용 가능한 템플릿은 액세스 권한, 인스턴스 구성 및 컨텍스트에 따라 다릅니다. 예를 들어 정보 서비스를 만들 때 확인 메시지에 대한 배달 템플릿을 연결할 수 있습니다.그런 다음 대상 매핑이 구독 매핑인 템플릿에만 액세스할 수 있습니다. 자세한 내용은 대상 매핑 [선택 및](../../delivery/using/selecting-a-target-mapping.md) 서비스 및 가입 [](../../delivery/using/about-services-and-subscriptions.md)정보를 참조하십시오.
