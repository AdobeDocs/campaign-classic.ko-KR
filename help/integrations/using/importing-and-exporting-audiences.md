---
product: campaign
title: 대상자 가져오기 및 내보내기
description: 대상자 가져오기 및 내보내기
feature: Audiences
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: c2293fc5-c9ba-4a73-8f39-fa7cdd06e8dd
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---


# 대상자 가져오기 및 내보내기{#importing-and-exporting-audiences}



## 대상자 가져오기 {#importing-an-audience}

수신자 목록을 통해 Audience Manager의 대상/세그먼트를 Adobe Campaign으로 가져올 수 있습니다.

1. Adobe Campaign 탐색기의 **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** 노드로 이동합니다.
1. 작업 표시줄에서 **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**&#x200B;을(를) 선택합니다.

   ![](assets/aam_import_audience.png)

1. 열려 있는 창에서 **[!UICONTROL Select a shared audience]**&#x200B;을(를) 클릭하여 다른 Adobe Experience Cloud 솔루션에서 사용할 수 있는 공유 대상/세그먼트 목록으로 이동합니다.
1. 대상을 선택하고 확인합니다. 대상자의 정보가 자동으로 완료됩니다.

   공유 대상자를 가져오려면 Admin Console에서 **[!UICONTROL Audience library]** 제품을 할당하고 Audience Manager의 관리자여야 합니다. 자세한 내용은 [Admin Console 설명서](https://helpx.adobe.com/kr/enterprise/managing/user-guide.html)를 참조하세요.

   ![](assets/aam_import_audience_3.png)

1. 필요한 데이터 형식을 정의하려면 **[!UICONTROL AMC Data source]** 필드에서 AMC 데이터 원본을 선택하십시오.

   ![](assets/aam_import_audience_2.png)

1. 대상자를 저장합니다.

대상자는 기술 워크플로우를 통해 가져옵니다. 가져온 목록에는 AMC 데이터 소스를 사용하여 조정할 수 있는 요소가 포함되어 있습니다. Adobe Campaign에서 인식되지 않는 요소는 가져오지 않습니다.

Audience Manager에서 직접 세그먼트를 가져오는 경우 가져오기 프로세스를 동기화하는 데 24~36시간이 소요됩니다. 이 기간이 지나면 Adobe Campaign에서 새 대상을 찾아 사용할 수 있습니다.

>[!NOTE]
>
>Adobe Analytics에서 Adobe Campaign으로 대상을 가져오는 경우 이러한 대상을 Audience Manager에서 먼저 공유해야 합니다. 이 프로세스는 12~24시간 걸리며, Campaign과의 24~36시간 동기화에 추가해야 합니다.
>
>이 경우 대상 공유 기간은 최대 60시간일 수 있습니다. Audience Manager의 Adobe Analytics 대상 공유에 대한 자세한 내용은 [Adobe Analytics 설명서](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html){target="_blank"}를 참조하세요.

대상 데이터는 동기화될 때마다 완전히 대체됩니다. 세그먼트만 가져올 수 있습니다. 키-값 쌍, 트레이트 및 규칙을 포함한 세분화된 데이터는 지원되지 않습니다.

## 대상자 내보내기 {#exporting-an-audience}

워크플로우를 사용하여 Adobe Campaign에서 Audience Manager로 대상을 내보낼 수 있습니다. 워크플로우를 만들고 사용하는 프로세스는 [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html?lang=ko){target="_blank"}에 자세히 설명되어 있습니다. 내보낸 대상은 세그먼트로 저장됩니다.

1. 새 타겟팅 워크플로우를 만듭니다.
1. 사용 가능한 여러 활동을 사용하여 수신자 집합을 타겟팅합니다.
1. 타깃팅 후 **[!UICONTROL Update shared audience]** 활동을 끌어다 놓은 다음 엽니다.

   ![](assets/aam_export_example.png)

1. **[!UICONTROL Select a shared audience]** 옵션을 통해 내보낼 대상을 정의합니다. 열리는 창에서 기존 대상자를 선택하거나 새 대상자를 만들 수 있습니다.

   기존 대상자를 선택하면 새 레코드만 대상자에 추가됩니다.

   받는 사람 목록을 새 대상으로 내보내려면 **[!UICONTROL Segment name]** 필드를 완료한 다음 **[!UICONTROL Create]**&#x200B;을(를) 클릭한 후 새로 만든 대상을 선택하십시오.

   창의 오른쪽 상단에 있는 확인 기호를 클릭한 다음 **[!UICONTROL OK]** 단추를 클릭하여 작업을 완료합니다.

1. 필요한 데이터 형식을 지정하려면 **[!UICONTROL AMC Data source]**&#x200B;을(를) 선택하십시오. 스키마는 자동으로 결정됩니다.

   ![](assets/aam_export_audience_activity.png)

1. 대상자를 저장합니다.

그런 다음 대상을 내보냅니다. 대상자 저장 활동에는 두 개의 아웃바운드 전환이 있습니다. 기본 전환에는 성공적으로 내보낸 수신자가 포함됩니다. 추가 전환에는 방문자 ID 또는 선언된 ID로 매핑될 수 없었던 수신자가 포함됩니다.

솔루션 간 동기화는 24-36시간이 소요됩니다. 이 기간이 지나면 새로운 대상을 찾아 다른 Adobe Experience Cloud 솔루션에서 재사용할 수 있습니다. Adobe Campaign 공유 대상 사용에 대한 자세한 내용은 이 [설명서](https://experienceleague.adobe.com/ko/docs/core-services/interface/services/audiences/create){target="_blank"}를 참조하세요.

>[!NOTE]
>
>조정하려면 레코드에 Adobe Experience Cloud ID(&#39;방문자 ID&#39; 또는 &#39;선언된 ID&#39;)가 있어야 합니다. Adobe Experience Cloud ID가 없는 레코드는 대상자를 내보내고 가져올 때 무시됩니다.
