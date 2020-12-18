---
solution: Campaign Classic
product: campaign
title: 오퍼 승인 및 활성화
description: 오퍼 승인 및 활성화
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 2%

---


# 오퍼 승인 및 활성화{#approving-and-activating-an-offer}

오퍼 컨텐츠가 완료되면 이 컨텐츠가 라이브 환경에 복제되어 배달되도록 승인해야 합니다. 승인은 오퍼 컨텐츠 및 해당 자격에 관한 것입니다.

오퍼 대시보드의 배너는 오퍼가 승인 주기를 거쳐야 하는지 여부를 알려줍니다.

![](assets/offer_validate_001.png)

## 오퍼 컨텐츠 승인{#approving-offer-content}

오퍼 컨텐츠 승인이란 라이브 환경에서 사용할 수 있도록 하려는 표현을 선택하는 것을 의미합니다.

오퍼의 컨텐트에는 공간당 하나의 표현이 있습니다. 각 오퍼 공간에 자체 구조와 자체 렌더링 기능이 있기 때문에 오퍼 표현이 다를 수 있습니다.

사용 가능한 특정 공간에서 오퍼 컨텐츠를 승인하도록 선택하고 다른 공간에서 거부할 수 있습니다.

>[!IMPORTANT]
>
>오퍼의 컨텐츠 및 자격 조건이 승인되면 게시 워크플로우(오퍼 알림)가 자동으로 실행되고 해당 오퍼가 활성화된 모든 공간에서 실시간으로 제공됩니다.

오퍼 컨텐츠를 승인하려면 다음 단계를 적용합니다.

1. **[!UICONTROL Approval]** 단추를 클릭하고 팝업에서 **[!UICONTROL Approve content]**&#x200B;을 선택합니다.

   ![](assets/offer_validate_002.png)

1. 드롭다운 목록을 사용하여 계속 편집할 표현을 선택하거나 라이브 환경에 게시할 표현을 선택한 다음 **[!UICONTROL Content approval]**&#x200B;을 클릭합니다.

   ![](assets/offer_validate_003.png)

   오퍼 컨텐츠가 승인되면 오퍼 대시보드 테이블에서 정보가 업데이트됩니다.

   ![](assets/offer_validate_004.png)

   >[!NOTE]
   >
   >**[!UICONTROL Content approved]** 언급이 모든 오퍼 표현이 활성화되고 승인되었다는 의미는 아닙니다. 모든 오퍼가 활성화/승인되었는지 여부에 관계없이 컨텐츠 승인 프로세스가 달성되었음을 나타냅니다.

## 오퍼 자격 승인 {#approving-offer-eligibility}

오퍼 자격 승인이란 오퍼 가중치와 오퍼 내에 구성되거나 상위 카테고리에서 만든 규칙에서 상속된 자격 규칙을 수락하거나 거부하는 것을 의미합니다.

>[!IMPORTANT]
>
>오퍼의 컨텐츠 및 자격 조건이 승인되면 게시 워크플로우(오퍼 알림)가 자동으로 실행되고 해당 오퍼가 활성화된 모든 공간에서 실시간으로 제공됩니다.

* 규칙의 전체 목록은 **[!UICONTROL Schedule and eligibility rules]**&#x200B;을 클릭하여 볼 수 있습니다.

   ![](assets/offer_validate_005.png)

* 자격 조건 규칙을 변경하려면 **[!UICONTROL Reject]**&#x200B;을 클릭한 다음 **[!UICONTROL Eligibility approval]**&#x200B;을 클릭합니다.

   ![](assets/offer_validate_007.png)

   다양한 상태가 오퍼 대시보드에서 업데이트됩니다.

   ![](assets/offer_validate_006.png)

* 오퍼 자격 조건을 수락하려면 **[!UICONTROL Approve eligibility]**&#x200B;을 클릭합니다.

   ![](assets/offer_validate_008.png)

   자격 조건을 승인하고 필요한 경우 주석을 추가한 다음 **[!UICONTROL Eligibility approval]**&#x200B;을 클릭합니다.

   ![](assets/offer_validate_009.png)

   다양한 상태가 오퍼 대시보드에서 업데이트됩니다.

   ![](assets/offer_validate_010.png)

## 승인 추적 {#approval-tracking}

승인 추적은 오퍼 대시보드에서 사용할 수 있습니다. **[!UICONTROL Hide/display logs]**&#x200B;을 클릭하여 액세스합니다.

![](assets/offer_validate_012.png)

>[!NOTE]
>
>또한 검토자의 주석에 대한 세부 정보와 함께 오퍼의 **[!UICONTROL Audit]** 탭에서도 추적을 사용할 수 있습니다.

## 승인 {#restart-the-approval}을(를) 다시 시작합니다.

승인이 실행되면 다시 시작할 수 있습니다. 이렇게 하려면 다음 지침을 따르십시오.

1. 오퍼 대시보드에서 **[!UICONTROL Content approved]**&#x200B;을 클릭합니다.
1. 나타나는 **[!UICONTROL Edit]** 창에서 다시 시작할 승인을 선택한 다음 **[!UICONTROL Re-initialize approval to submit it again]**&#x200B;을 클릭합니다.
1. **[!UICONTROL Ok]**&#x200B;을 클릭하여 확인합니다.

![](assets/offer_validate_013.png)

## 오퍼 {#publishing-the-offer} 게시

오퍼의 컨텐츠와 자격 조건이 모두 승인되면 승인 주기가 완료된 각 오퍼에 대해 자동으로 실행되는 워크플로우에 의해 오퍼가 게시됩니다. 또한 **[!UICONTROL Offer notification]** 작업 과정은 필요할 경우 오퍼 카탈로그에 포함된 공간과 카테고리를 디자인 환경에서 라이브 환경으로 동기화하기 위해 1시간마다 실행됩니다.

디자인 환경에서 사용할 수 있는 오퍼의 대시보드에는 라이브 환경에서 일치하는 오퍼의 이름을 비롯하여 게시와 관련된 정보가 포함되어 있습니다.

![](assets/offer_golive_001.png)

라이브 환경에서 사용할 수 있는 오퍼를 표시하려면 오퍼 레이블을 클릭합니다.라이브 오퍼에는 관련된 모든 정보가 포함된 대시보드가 있습니다.

![](assets/offer_golive_002.png)

## 오퍼 {#disabling-an-offer} 비활성화

오퍼가 승인되면 비활성화할 수 있습니다.

이렇게 하려면 온라인 오퍼 대시보드나 온라인 상태로 이동하기 위해 기다리는 오퍼로 이동한 다음 **[!UICONTROL Disable offer]**&#x200B;을 클릭합니다.

**[!UICONTROL Eligibility]** 탭으로 이동하여 **[!UICONTROL Enabled]** 상자를 선택하여 범주를 직접 비활성화할 수도 있습니다.

>[!NOTE]
>
>디자인 환경에서 오퍼가 삭제되면 연결된 온라인 환경에서 오퍼가 자동으로 비활성화됩니다. 제안 보존 기간이 지나면 비활성화된 오퍼가 온라인 환경에서 삭제됩니다.

![](assets/offer_preview_deactivate.png)

