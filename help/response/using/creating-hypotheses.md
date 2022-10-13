---
product: campaign
title: 가설 만들기
description: Campaign 응답 관리자에서 가설을 만드는 방법을 알아봅니다
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: e0b3bc9f-5e81-463f-a59e-cd972a47109b
source-git-commit: 878ba2b532d5cb59af77b6450b12ae5d2ff149b2
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 3%

---

# 가설 만들기{#creating-hypotheses}

![](../../assets/common.svg)

가설을 캠페인 오퍼 또는 게재에 만들거나 연결하는 다양한 가능성이 있습니다.

* 를 통해 **[!UICONTROL Measurement hypotheses]** 기존 템플릿을 기반으로 새 가설을 만들어 기존 게재에 연결하여 폴더를 만듭니다.
* 를 통해 **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** 탭에서 사용할 수 있습니다.
* 를 통해 **[!UICONTROL Measurement]** 캠페인에서 만든 게재 옵션.

마케팅 캠페인이 실행되고 수신자가 게재를 받은 후에만 가설을 계산할 수 있습니다. 이 가설이 제안 제안을 기반으로 한다면 후자는 적어도 제시되어야 하며 여전히 활성화되어 있어야 합니다. 오퍼 및 게재 가식은 를 통해 만들어집니다 **[!UICONTROL Measurement hypotheses]** 폴더 및 는 가설 템플릿을 기반으로 합니다. 하지만 캠페인이 시작되기 전에 게재 또는 캠페인에서 직접 가설을 참조할 수 있습니다. 이 경우 실행 설정에 따라 마케팅 캠페인이 시작되면 가설이 자동으로 계산됩니다. [자세히 알아보기](hypothesis-templates.md#hypothesis-template-execution-settings)

## 즉시 게재 시 가설 만들기 {#creating-a-hypothesis-on-the-fly-on-a-delivery}

기존 게재에 대한 가설을 생성하려면 다음 프로세스를 적용합니다.

>[!NOTE]
>
>이 작업은 보류 중인 게재에만 수행할 수 있습니다.

1. Adobe Campaign 트리에서 **[!UICONTROL Campaign management > Measurement hypotheses]**.
1. 을(를) 클릭합니다. **[!UICONTROL New]** 가설 목록을 클릭하거나 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL New]** 를 클릭합니다.

   ![](assets/response_hypothesis_instance_creation_002.png)

1. 가설 창에서 앞에서 만든 템플릿을 선택합니다. [자세히 알아보기](hypothesis-templates.md)

   ![](assets/response_hypothesis_instance_creation_003.png)

   선택한 모델에 정의된 가설 컨텍스트가 창에 표시됩니다.

   >[!NOTE]
   >
   >템플릿에 정의되어 있지만 이 단계에서 표시되지 않는 설정은 메모리에 보관되며 진행 중인 가설을 재할당합니다.

   ![](assets/response_hypothesis_instance_creation_004.png)

1. 가설을 만들 게재를 선택합니다.

   ![](assets/response_hypothesis_instance_creation_005.png)

1. 가설을 편집하여 개인화할 수 있습니다 **[!UICONTROL General]**, **[!UICONTROL Transactions]** 및 **[!UICONTROL Scope]** 탭. [자세히 알아보기](hypothesis-templates.md#creating-a-hypothesis-model)
1. 를 클릭하여 가설을 시작합니다 **[!UICONTROL Start]**.

   측정을 수행하도록 워크플로우가 자동으로 생성됩니다. 가설 구성에 따라 이름이 자동으로 정의됩니다.

   >[!CAUTION]
   >
   >이 옵션을 선택하면 액세스할 수 있습니다 **[!UICONTROL Keep execution workflow]** 상자.\
   >가설을 실행하는 동안 오류가 발생하는 경우 디버깅 목적으로만 이 옵션을 활성화해야 합니다. 자동으로 생성된 워크플로우는 **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]** 폴더 아래에 표시됩니다.
   > 
   >또한 자동으로 생성된 워크플로우는 수정하면 안 됩니다. 최종 수정은 이후의 계산을 위해 다른 곳에서 고려되지 않습니다.
   >
   >이 옵션을 선택한 경우 워크플로우를 실행한 후 삭제합니다.

   ![](assets/response_hypothesis_instance_creation_006.png)

   계산이 완료되면 측정 지표가 자동으로 업데이트됩니다.

   ![](assets/response_hypothesis_instance_creation_007.png)

1. 필요한 경우 설정을 변경하고 가설을 다시 시작합니다.

## 캠페인 게재에서 가설 참조 {#referencing-a-hypothesis-in-a-campaign-delivery}

시작하기 전에 마케팅 캠페인에서 가설을 참조할 수 있습니다. 이 경우 가설 템플릿에 정의된 실행 설정에 따라 게재를 전송하면 가설이 자동으로 시작됩니다. 게재에서 가설을 생성하려면 다음 프로세스를 적용합니다.

1. 필요에 따라 하나 이상을 만들 수 있습니다 **[!UICONTROL Delivery]** 에 설명된 대로 유형 템플릿 [이 섹션](hypothesis-templates.md#creating-a-hypothesis-model)
1. 마케팅 캠페인 및 타겟팅 워크플로우를 만듭니다.
1. 게재 창에서 **[!UICONTROL Delivery measurement]** 아이콘.
1. 가설 템플릿을 선택합니다(모델에 구성된 쿼리가 가설 창에 표시됩니다.).

   모델에 구성된 날짜를 기준으로 캠페인이 완료되면 가설이 자동으로 계산됩니다. [자세히 알아보기](hypothesis-templates.md#hypothesis-template-execution-settings)

   ![](assets/response_hypothesis_instance_creation_008.png)

## 캠페인에 대한 게재에 기본 가설 추가 {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

캠페인 수준에서 가설을 직접 참조할 수 있습니다. 이 경우 가설이 캠페인에서 만든 모든 게재에 자동으로 연결됩니다. 방법은 다음과 같습니다.

1. 로 이동합니다. **[!UICONTROL Edit]** 캠페인 탭을 클릭합니다.
1. 측정 섹션에서 **[!UICONTROL Default hypotheses]** 탭.

   ![](assets/response_hypothesis_instance_creation_010.png)

1. 클릭 **[!UICONTROL Add]** 가설 템플릿을 선택합니다.

   ![](assets/response_hypothesis_instance_creation_011.png)

   이제 이 템플릿을 기반으로 한 가설이 캠페인에 대한 각 새로운 게재에서 기본적으로 참조됩니다.

   ![](assets/response_hypothesis_instance_creation_012.png)

가설 결과는 **[!UICONTROL General]** 및 **[!UICONTROL Reactions]** 가설 탭. [자세히 알아보기](hypothesis-tracking.md)

자세한 내용은 [이 샘플](#example--creating-a-hypothesis-linked-to-a-delivery).

## 오퍼에 대한 가설 만들기 {#creating-a-hypothesis-on-an-offer}

오퍼 제안에 대한 가설을 만드는 것은 즉시 게재 가설을 작성하는 것과 비슷합니다. 오퍼가 활성화된 한 가설이 실행될 수 있습니다. 계산 기간은 오퍼 제안 날짜를 기준으로 합니다. 가설을 통해 수신자를 구매에 연결할 수 있으면 오퍼 제안이 수락될 가능성이 있는 상태가 자동으로 변경될 수 있습니다. [자세히 알아보기](hypothesis-templates.md#transactions)

1. 하나 이상 만들기 **[!UICONTROL Offer]** 에 설명된 대로 유형 모델 [이 섹션](hypothesis-templates.md#creating-a-hypothesis-model).
1. 로 이동합니다. **[!UICONTROL Campaign management > Measurement hypotheses]** 노드 아래에 있어야 합니다.
1. 만들기 **[!UICONTROL Offers]** 이전에 만든 모델을 선택하여 가설을 입력합니다.

   ![](assets/response_hypothesis_instance_offer_001.png)

   모델에서 생성된 쿼리가 창에 나타납니다.

   ![](assets/response_hypothesis_instance_offer_003.png)

1. 가설을 만들 오퍼를 선택합니다.

   ![](assets/response_hypothesis_instance_offer_004.png)

1. 필요한 경우 쿼리를 세분화합니다.
1. 클릭 **[!UICONTROL Start]** 가설을 실행하기 위해.
1. 그 가설 결과는 그 가설 결과에서도 볼 수 있다 **[!UICONTROL General]** 및 **[!UICONTROL Reactions]** 탭. [자세히 알아보기](hypothesis-tracking.md)

   오퍼에 대한 가설이 **[!UICONTROL Measurement]** 탭.

   ![](assets/response_hypothesis_instance_offer_007.png)

   만약 **[!UICONTROL Update offer proposition status]** 가설 템플릿에서 옵션이 활성화되면 오퍼 제안 상태가 자동으로 변경되므로 캠페인의 영향에 대한 피드백을 제공합니다(자세한 내용은 다음을 참조하십시오) [트랜잭션](hypothesis-templates.md#transactions)).

## 예: 게재에 연결된 가설 만들기 {#example--creating-a-hypothesis-linked-to-a-delivery}

이 예에서는 게재에 연결된 가설을 만들려고 합니다. 이 가설은 이전에 만든 모델을 기반으로 합니다. [자세히 알아보기](hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery)

그런 다음 모델에서 상속된 쿼리를 세분화하여 구매 테이블의 특정 문서에 대한 가설을 만듭니다.

1. 캠페인 및 게재를 만듭니다. [자세히 알아보기](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)

   이 예제에서는 DM 유형 게재를 사용합니다.

1. 시드 주소 구성: 이전에 만든 가설 템플릿은 반응 결과에 컨트롤 그룹을 고려하도록 구성되었습니다.

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >자세한 정보는 [이 섹션](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)을 참조하십시오.

1. 를 엽니다. **[!UICONTROL Direct mail delivery]** 을 클릭하고 **[!UICONTROL Delivery measurement]** 아이콘을 클릭한 다음 **[!UICONTROL Add]**.

   ![](assets/response_hypothesis_delivery_example_002.png)

1. 드롭다운 목록에서 이전에 생성한 가설 템플릿을 선택합니다.

   ![](assets/response_hypothesis_delivery_example_004.png)

   모델에서 생성된 쿼리가 표시됩니다.

   ![](assets/response_hypothesis_delivery_example_005.png)

1. 클릭 **[!UICONTROL Edit query...]** 그리고 가설이 걱정할 제품을 입력하여 쿼리를 세분화합니다.

   ![](assets/response_hypothesis_delivery_example_006.png)

   가설이 의 게재와 연결되어 있는지 확인할 수 있습니다 **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** 캠페인 탭을 클릭합니다.

   ![](assets/response_hypothesis_delivery_example_008.png)

1. 타겟팅 워크플로우를 시작하고 캠페인이 완료될 때까지 필요한 검사를 실행합니다. [자세히 알아보기](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)

   ![](assets/response_hypothesis_delivery_example_009.png)

1. Adobe Campaign 트리에서 **[!UICONTROL Campaign management > Measurement hypotheses]** 노드 를 눌러 가설을 통해 계산된 지표를 확인합니다.

   ![](assets/response_hypothesis_delivery_example_010.png)
