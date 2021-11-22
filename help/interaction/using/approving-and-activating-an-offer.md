---
product: campaign
title: 오퍼 승인 및 활성화
description: 오퍼 승인 및 활성화
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: cf7649fe-f62a-4dfa-a19e-9c1ca545e3e3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 2%

---

# 오퍼 승인 및 활성화{#approving-and-activating-an-offer}

![](../../assets/v7-only.svg)

오퍼 컨텐츠가 완료되고 나면 라이브 환경에 복제되고 배달되도록 하려면 오퍼 컨텐츠를 승인해야 합니다. 승인 은 오퍼 콘텐츠 및 해당 자격 조건과 관련이 있습니다.

오퍼 대시보드의 배너는 오퍼가 승인 절차를 거쳤는지 여부를 알려줍니다.

![](assets/offer_validate_001.png)

## 오퍼 컨텐츠 승인 {#approving-offer-content}

오퍼 컨텐츠 승인이란 라이브 환경에서 사용할 수 있도록 하려는 표시를 선택하는 것을 의미합니다.

오퍼의 컨텐츠는 공간당 하나의 표현을 갖습니다. 각 오퍼 공간에는 자체 구조와 자체 렌더링 기능이 있으므로 오퍼 표현이 다를 수 있습니다.

사용 가능한 특정 공간에서 오퍼 컨텐츠를 승인하고 다른 공간에서 거부하도록 선택할 수 있습니다.

>[!IMPORTANT]
>
>오퍼의 컨텐츠 및 자격이 승인되면 게시 워크플로우(오퍼 알림)가 자동으로 실행되고 오퍼가 활성화된 모든 공간에서 실시간으로 사용할 수 있습니다.

오퍼 컨텐츠를 승인하려면 다음 단계를 적용합니다.

1. 을(를) 클릭합니다. **[!UICONTROL Approval]** 단추를 누르고 선택합니다. **[!UICONTROL Approve content]** 팝업.

   ![](assets/offer_validate_002.png)

1. 드롭다운 목록을 사용하여 계속 편집할 표현 또는 라이브 환경에 게시할 표현을 선택한 다음 를 클릭합니다 **[!UICONTROL Content approval]**.

   ![](assets/offer_validate_003.png)

   오퍼 컨텐츠가 승인되면 오퍼 대시보드 테이블에서 정보가 업데이트됩니다.

   ![](assets/offer_validate_004.png)

   >[!NOTE]
   >
   >다음 **[!UICONTROL Content approved]** 언급이 모든 오퍼 표현이 활성화 및 승인되었음을 의미하지는 않습니다. 모든 오퍼가 활성화/승인되었는지 여부에 상관없이 컨텐츠 승인 프로세스가 달성되었음을 나타냅니다.

## 오퍼 자격 승인 {#approving-offer-eligibility}

오퍼 자격 승인이란 오퍼 가중치 및 자격 규칙이 오퍼에도 구성되거나 상위 카테고리에서 생성된 규칙에서 상속되는 것을 수락 또는 거부하는 것을 의미합니다.

>[!IMPORTANT]
>
>오퍼의 컨텐츠 및 자격이 승인되면 게시 워크플로우(오퍼 알림)가 자동으로 실행되고 오퍼가 활성화된 모든 공간에서 실시간으로 사용할 수 있습니다.

* 규칙 전체 목록은 **[!UICONTROL Schedule and eligibility rules]**.

   ![](assets/offer_validate_005.png)

* 자격 규칙을 변경하려면 **[!UICONTROL Reject]**&#x200B;를 클릭한 다음 **[!UICONTROL Eligibility approval]**.

   ![](assets/offer_validate_007.png)

   다양한 상태가 오퍼 대시보드에서 업데이트됩니다.

   ![](assets/offer_validate_006.png)

* 오퍼 자격 조건을 수락하려면 **[!UICONTROL Approve eligibility]**.

   ![](assets/offer_validate_008.png)

   자격 승인, 필요한 경우 주석을 추가한 다음 **[!UICONTROL Eligibility approval]**.

   ![](assets/offer_validate_009.png)

   다양한 상태가 오퍼 대시보드에서 업데이트됩니다.

   ![](assets/offer_validate_010.png)

## 승인 추적 {#approval-tracking}

승인 추적은 오퍼 대시보드에서 사용할 수 있습니다. 클릭 **[!UICONTROL Hide/display logs]** 액세스해야 합니다.

![](assets/offer_validate_012.png)

>[!NOTE]
>
>추적은 **[!UICONTROL Audit]** 검토자의 주석에 대한 세부 정보가 있는 오퍼의 탭입니다.

## 승인을 다시 시작합니다 {#restart-the-approval}

승인이 실행되면 다시 시작할 수 있습니다. 이렇게 하려면 다음 지침을 따르십시오.

1. 클릭 **[!UICONTROL Content approved]** 를 반환합니다.
1. 에서 **[!UICONTROL Edit]** 창이 나타나면 재시작할 승인을 선택한 다음 **[!UICONTROL Re-initialize approval to submit it again]**.
1. 을 클릭하여 확인 **[!UICONTROL Ok]**.

![](assets/offer_validate_013.png)

## 오퍼 게시 {#publishing-the-offer}

오퍼의 컨텐츠와 자격 조건이 모두 승인되면 승인 주기가 완료된 각 오퍼에 대해 자동으로 실행되는 워크플로우에 의해 오퍼가 게시됩니다. 다음 **[!UICONTROL Offer notification]** 또한 워크플로우는 필요한 경우 오퍼 카탈로그에 포함된 공간과 카테고리를 디자인 환경에서 라이브 환경으로 동기화하기 위해 매시간마다 실행됩니다.

디자인 환경에서 사용할 수 있는 오퍼의 대시보드에는 라이브 환경에서 일치하는 오퍼의 이름을 포함하여 게시와 관련된 정보가 포함되어 있습니다.

![](assets/offer_golive_001.png)

라이브 환경에서 사용할 수 있는 오퍼를 표시하려면 오퍼 레이블을 클릭합니다. 라이브 오퍼에는 모든 관련 정보가 포함된 대시보드가 있습니다.

![](assets/offer_golive_002.png)

## 오퍼 비활성화 {#disabling-an-offer}

오퍼가 승인되면 비활성화할 수 있습니다.

이렇게 하려면 온라인 오퍼 또는 온라인 상태를 유지하기 위해 대기 중인 오퍼를 위한 대시보드로 이동한 다음 를 클릭합니다 **[!UICONTROL Disable offer]**.

로 이동하여 카테고리를 직접 비활성화할 수도 있습니다 **[!UICONTROL Eligibility]** 탭 및 확인 **[!UICONTROL Enabled]** 상자.

>[!NOTE]
>
>디자인 환경에서 오퍼가 삭제되면 연결된 온라인 환경에서 자동으로 비활성화됩니다. 제안 유지 기간 이후에는 비활성화된 오퍼가 온라인 환경에서 삭제됩니다.

![](assets/offer_preview_deactivate.png)
