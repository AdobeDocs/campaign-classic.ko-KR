---
product: campaign
title: 대상 가져오기 및 내보내기
description: 대상 가져오기 및 내보내기
feature: Audiences, People Core Service Integration
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: c2293fc5-c9ba-4a73-8f39-fa7cdd06e8dd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 4%

---


# 대상 가져오기 및 내보내기{#importing-and-exporting-audiences}



## 대상자 가져오기 {#importing-an-audience}

수신자 목록을 통해 Audience Manager 또는 People 핵심 서비스의 대상/세그먼트를 Adobe Campaign으로 가져올 수 있습니다.

1. 로 이동 **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** Adobe Campaign 탐색기의 노드
1. 작업 표시줄에서 을 선택합니다. **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. 열려 있는 창에서 다음을 클릭합니다. **[!UICONTROL Select a shared audience]** 다른 Adobe Experience Cloud 솔루션에서 사용할 수 있는 공유 대상/세그먼트 목록으로 이동합니다.
1. 대상을 선택하고 확인합니다. 대상자의 정보가 자동으로 완료됩니다.

   공유 대상자를 가져오려면 다음을 할당해야 합니다. **[!UICONTROL Audience library]** admin console의 제품 및 Audience Manager의 관리자가 될 수 있습니다. 자세한 내용은 [Admin Console 설명서를 참조하십시오](https://helpx.adobe.com/kr/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. 에서 AMC 데이터 소스 선택 **[!UICONTROL AMC Data source]** 예상 데이터 유형을 정의하는 필드입니다.

   ![](assets/aam_import_audience_2.png)

1. 대상자를 저장합니다.

대상자는 기술 워크플로우를 통해 가져옵니다. 가져온 목록에는 AMC 데이터 소스를 사용하여 조정할 수 있는 요소가 포함되어 있습니다. Adobe Campaign에서 인식되지 않는 요소는 가져오지 않습니다.

People 핵심 서비스 또는 Audience Manager에서 직접 세그먼트를 가져오는 경우 가져오기 프로세스를 동기화하는 데 24~36시간이 소요됩니다. 이 기간이 지나면 Adobe Campaign에서 새 대상을 찾아 사용할 수 있습니다.

>[!NOTE]
>
>Adobe Analytics에서 Adobe Campaign으로 대상자를 가져오는 경우 이러한 대상자를 먼저 People 핵심 서비스 또는 Audience Manager에서 공유해야 합니다. 이 프로세스는 12~24시간 걸리며, Campaign과의 24~36시간 동기화에 추가해야 합니다.
>
>이 경우 대상 공유 기간은 최대 60시간일 수 있습니다. People 핵심 서비스 및 Audience Manager의 Adobe Analytics 대상 공유에 대한 자세한 내용은 다음을 참조하십시오. [Adobe Analytics 설명서](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html).

대상 데이터는 동기화될 때마다 완전히 대체됩니다. 세그먼트만 가져올 수 있습니다. 키-값 쌍, 트레이트 및 규칙을 포함한 세분화된 데이터는 지원되지 않습니다.

## 대상자 내보내기 {#exporting-an-audience}

워크플로우를 사용하여 Adobe Campaign에서 Audience Manager 또는 People 핵심 서비스로 대상을 내보낼 수 있습니다. 워크플로우를 만들고 사용하는 프로세스는에 자세히 설명되어 있습니다 [이 문서](../../workflow/using/building-a-workflow.md). 내보낸 대상은 People 핵심 서비스의 세그먼트로 저장됩니다.

1. 새 타겟팅 워크플로우를 만듭니다.
1. 사용 가능한 여러 활동을 사용하여 수신자 집합을 타겟팅합니다.
1. 타겟팅 후 을(를) 끌어다 놓습니다. **[!UICONTROL Update shared audience]** 활동을 실행한 다음 엽니다.

   ![](assets/aam_export_example.png)

1. 를 통해 내보낼 대상자를 정의합니다. **[!UICONTROL Select a shared audience]** 옵션을 선택합니다. 열리는 창에서 기존 대상자를 선택하거나 새 대상자를 만들 수 있습니다.

   기존 대상자를 선택하면 새 레코드만 대상자에 추가됩니다.

   새 대상자에서 수신자 목록을 내보내려면 **[!UICONTROL Segment name]** 필드를 클릭한 다음 클릭 **[!UICONTROL Create]** 새로 만든 대상자를 선택하기 전에.

   창의 오른쪽 상단에 있는 확인 기호를 클릭한 다음 **[!UICONTROL OK]** 단추를 클릭합니다.

1. 다음 항목 선택 **[!UICONTROL AMC Data source]** 예상 데이터 유형을 지정합니다. 스키마는 자동으로 결정됩니다.

   ![](assets/aam_export_audience_activity.png)

1. 대상자를 저장합니다.

그런 다음 대상을 내보냅니다. 대상자 저장 활동에는 두 개의 아웃바운드 전환이 있습니다. 기본 전환에는 성공적으로 내보낸 수신자가 포함됩니다. 추가 전환에는 방문자 ID 또는 선언된 ID로 매핑될 수 없었던 수신자가 포함됩니다.

Adobe Campaign과 People 핵심 서비스 간 동기화는 24-36시간이 소요됩니다. 이 기간이 지나면 People 핵심 서비스에서 새 대상자를 찾아 다른 Adobe Experience Cloud 솔루션에서 다시 사용할 수 있습니다. Adobe People 핵심 서비스에서 Adobe Campaign 공유 대상 사용에 대한 자세한 내용은 다음을 참조하십시오. [설명서](https://experienceleague.adobe.com/docs/core-services/interface/audiences/t-audience-create.html).

>[!NOTE]
>
>조정하려면 레코드에 Adobe Experience Cloud ID(&#39;방문자 ID&#39; 또는 &#39;선언된 ID&#39;)가 있어야 합니다. Adobe Experience Cloud ID가 없는 레코드는 대상자를 내보내고 가져올 때 무시됩니다.
