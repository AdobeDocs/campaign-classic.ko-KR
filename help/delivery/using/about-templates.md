---
product: campaign
title: 템플릿 정보
description: 게재 템플릿 시작
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Delivery Templates
role: User
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 2%

---

# 템플릿 정보{#about-templates}

게재 구성은 다시 사용하기 위해 게재 템플릿에 저장할 수 있습니다. 템플릿에는 게재의 전체 또는 일부 구성이 포함될 수 있습니다.

게재 템플릿은 이 장에 설명된 대로 수동으로 실행하거나 이벤트(설정된 시간에 시작, 서버에 파일 도착 등)에 따라 실행할 수 있습니다. 게재 템플릿은 **[!UICONTROL Resources > Templates > Delivery templates]** 트리의 노드.

![](assets/s_user_template_list.png)

템플릿에는 두 가지 유형이 있습니다.

1. Adobe Campaign 기본 게재 템플릿

   시스템에서 기본 템플릿을 삭제해서는 안 됩니다. 여기에는 각 게재 채널에 대한 최소 구성이 포함됩니다. 그러나 관리자는 특정 기능을 제한하거나 사용자에게 기본값(추적 활성화, 보낸 사람 이메일 주소 등)을 제공할 수 있습니다. 기본 시나리오는 템플릿 목록에 굵게 표시됩니다. 수정하려면 파일을 복제해야 합니다.

1. 사전 정의된 게재 템플릿

   Adobe Campaign 관리자는 새 게재 템플릿을 만들 수 있습니다. 운영자(적절한 액세스 권한이 있는 사람)가 사용하거나 서버 프로세스에 의해 자동으로 재사용할 수 있습니다. 예를 들어 이메일 게재 템플릿을 구성할 수 있으며, 사용자가 이 템플릿을 사용하여 게재를 만들 때 텍스트 또는 HTML 콘텐츠를 입력한 다음 게재하면 됩니다. 다른 선택 사항은 관리자가 이미 정의했습니다.

>[!NOTE]
>
>사용 가능한 템플릿은 액세스 권한, 인스턴스 구성 및 컨텍스트에 따라 다릅니다. 예를 들어, 정보 서비스를 생성할 때 확인 메시지에 대한 전달 템플릿을 연결할 수 있습니다. 그런 다음 대상 매핑이 구독 매핑인 템플릿에만 액세스할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [대상 매핑 선택](selecting-a-target-mapping.md) 및 [서비스 및 구독](about-services-and-subscriptions.md).
