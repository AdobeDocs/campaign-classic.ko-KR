---
product: campaign
title: 대상 가져오기 및 내보내기
description: 대상 가져오기 및 내보내기
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: c2293fc5-c9ba-4a73-8f39-fa7cdd06e8dd
source-git-commit: 515587695115c23d9b248ecb87a7ae89ea7c62a0
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 4%

---

# 대상 가져오기 및 내보내기{#importing-and-exporting-audiences}

## 대상자 가져오기 {#importing-an-audience}

수신자 목록을 통해 Audience Manager 또는 People 핵심 서비스의 대상/세그먼트를 Adobe Campaign으로 가져올 수 있습니다.

1. Adobe Campaign 탐색기의 **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** 노드로 이동합니다.
1. 작업 표시줄에서 **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]** 을 선택합니다.

   ![](assets/aam_import_audience.png)

1. 열리는 창에서 **[!UICONTROL Select a shared audience]** 을 클릭하여 다른 Adobe Experience Cloud 솔루션에서 사용할 수 있는 공유 대상/세그먼트 목록으로 이동합니다.
1. 대상을 선택하고 확인합니다. 대상자의 정보가 자동으로 완료됩니다.

   공유 대상을 가져오려면 Admin Console에서 **[!UICONTROL Audience library]** 제품을 할당받고 Audience Manager에서 관리자가 되어야 합니다. 자세한 내용은 [Admin Console 설명서를 참조하십시오](https://helpx.adobe.com/kr/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. **[!UICONTROL AMC Data source]** 필드에서 AMC 데이터 소스를 선택하여 예상되는 데이터 유형을 정의합니다.

   ![](assets/aam_import_audience_2.png)

1. 대상자를 저장합니다.

대상자는 기술 워크플로우를 통해 가져옵니다. 가져온 목록에는 AMC 데이터 소스를 사용하여 조정할 수 있는 요소가 포함되어 있습니다. Adobe Campaign에서 인식하지 못하는 요소는 가져올 수 없습니다.

세그먼트를 People 핵심 서비스 또는 Audience Manager에서 직접 가져올 때 가져오기 프로세스를 동기화하려면 24-36시간이 걸립니다. 이 기간 이후에는 Adobe Campaign에서 새 대상자를 찾아 사용할 수 있습니다.

>[!NOTE]
>
>Adobe Analytics에서 Adobe Campaign으로 대상자를 가져오는 경우, 이러한 대상자는 먼저 People 핵심 서비스 또는 Audience Manager에서 공유해야 합니다. 이 프로세스는 12-24시간이 걸리며, Campaign과의 24-36시간 동기화에 추가해야 합니다.
>
>이 경우 대상 공유 기간은 최대 60시간까지 될 수 있습니다. 사용자 핵심 서비스 및 Audience Manager에서 Adobe Analytics 대상 공유에 대한 자세한 내용은 [Adobe Analytics 설명서](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)를 참조하십시오.

대상 데이터는 동기화될 때마다 완전히 교체됩니다. 세그먼트만 가져올 수 있습니다. 키-값 쌍, 트레이트 및 규칙을 포함한 세부적인 데이터는 지원되지 않습니다.

## 대상 내보내기 {#exporting-an-audience}

워크플로우를 사용하여 대상을 Adobe Campaign에서 Audience Manager 또는 People 핵심 서비스로 내보낼 수 있습니다. 워크플로우를 만들고 사용하는 프로세스는 [이 문서](../../workflow/using/building-a-workflow.md)에 자세히 설명되어 있습니다. 내보낸 대상은 People 핵심 서비스에 세그먼트로 저장됩니다.

1. 새 타겟팅 워크플로우를 만듭니다.
1. 사용할 수 있는 다양한 활동을 사용하여 수신자 집합을 타겟팅합니다.
1. 타겟팅 후 **[!UICONTROL Update shared audience]** 활동을 끌어다 놓은 뒤 엽니다.

   ![](assets/aam_export_example.png)

1. **[!UICONTROL Select a shared audience]** 옵션을 통해 내보낼 대상자를 정의합니다. 열리는 창에서 기존 대상자를 선택하거나 새 대상자를 만들 수 있습니다.

   기존 대상자를 선택하면 새 레코드만 대상에 추가됩니다.

   새 대상에서 수신자 목록을 내보내려면 **[!UICONTROL Segment name]** 필드를 완료한 다음 새로 만든 대상자를 선택하기 전에 **[!UICONTROL Create]** 을(를) 클릭합니다.

   창 오른쪽 상단에 있는 확인 기호를 클릭한 다음 **[!UICONTROL OK]** 버튼을 클릭하여 작업을 완료합니다.

1. 필요한 데이터 유형을 지정하려면 **[!UICONTROL AMC Data source]** 을 선택합니다. 스키마가 자동으로 결정됩니다.

   ![](assets/aam_export_audience_activity.png)

1. 대상자를 저장합니다.

대상자를 내보냅니다. 대상자 저장 활동에는 두 개의 아웃바운드 전환이 있습니다. 기본 전환에는 성공적으로 내보낸 수신자가 포함되어 있습니다. 추가 전환에는 방문자 ID나 선언된 ID로 매핑되지 않은 수신자가 포함되어 있습니다.

Adobe Campaign과 People 핵심 서비스 간의 동기화는 24-36시간이 소요됩니다. 이 기간 이후에는 사람 핵심 서비스에서 새 대상자를 찾아 다른 Adobe Experience Cloud 솔루션에서 재사용할 수 있습니다. Adobe 사용자 핵심 서비스에서 Adobe Campaign 공유 대상을 사용하는 방법에 대한 자세한 내용은 이 [설명서](https://experienceleague.adobe.com/docs/core-services/interface/audiences/t-audience-create.html)를 참조하십시오.

>[!NOTE]
>
>조정하려면 레코드에 Adobe Experience Cloud ID(&#39;방문자 ID&#39; 또는 &#39;선언된 ID&#39;)가 있어야 합니다. 대상을 내보내고 가져올 때 Adobe Experience Cloud ID가 없는 레코드는 무시됩니다.
