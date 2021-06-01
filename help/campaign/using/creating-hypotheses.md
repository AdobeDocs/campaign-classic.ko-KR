---
product: campaign
title: 가설 만들기
description: Campaign 응답 관리자에서 가설을 만드는 방법을 알아봅니다
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: e0b3bc9f-5e81-463f-a59e-cd972a47109b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1051'
ht-degree: 0%

---

# 가설 만들기{#creating-hypotheses}

가설을 캠페인 오퍼 또는 게재에 만들거나 연결하는 다양한 가능성이 있습니다.

* 기존 템플릿을 기반으로 새 가설을 만들고 기존 게재에 연결하여 **[!UICONTROL Measurement hypotheses]** 폴더를 통해 이 가설을 작성할 수 있습니다.
* 캠페인의 **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** 탭을 통해.
* 캠페인에서 만든 게재의 **[!UICONTROL Measurement]** 옵션을 통해.

마케팅 캠페인이 실행되고 수신자가 게재를 받은 후에만 가설을 계산할 수 있습니다. 이 가설이 제안 제안을 기반으로 한다면 후자는 적어도 제시되어야 하며 여전히 활성화되어 있어야 합니다. 오퍼 및 게재 가설이 **[!UICONTROL Measurement hypotheses]** 폴더를 통해 작성되며 가설 템플릿을 기반으로 합니다. 하지만 캠페인이 시작되기 전에 게재 또는 캠페인에서 직접 가설을 참조할 수 있습니다. 이 경우 실행 설정에 따라 마케팅 캠페인이 시작되면 가설이 자동으로 계산됩니다(자세한 내용은 [가설 템플릿 실행 설정](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings) 참조).

## 전달 {#creating-a-hypothesis-on-the-fly-on-a-delivery} 시 즉시 가설 만들기

기존 게재에 대한 가설을 생성하려면 다음 프로세스를 적용합니다.

>[!NOTE]
>
>이 작업은 보류 중인 게재에만 수행할 수 있습니다.

1. Adobe Campaign 트리에서 **[!UICONTROL Campaign management > Measurement hypotheses]** 로 이동합니다.
1. **[!UICONTROL New]** 단추를 클릭하거나 가설 목록을 마우스 오른쪽 단추로 클릭하고 드롭다운 목록에서 **[!UICONTROL New]** 를 선택합니다.

   ![](assets/response_hypothesis_instance_creation_002.png)

1. 가설 창에서 이전에 만든 템플릿을 선택합니다( [가설 템플릿](../../campaign/using/hypothesis-templates.md) 참조).

   ![](assets/response_hypothesis_instance_creation_003.png)

   선택한 모델에 정의된 가설 컨텍스트가 창에 표시됩니다.

   >[!NOTE]
   >
   >템플릿에 정의된 설정이며 이 단계에서 표시되지 않는 설정은 메모리에 유지되며 진행 중인 가설을 다시 지정합니다.

   ![](assets/response_hypothesis_instance_creation_004.png)

1. 가설을 만들 게재를 선택합니다.

   ![](assets/response_hypothesis_instance_creation_005.png)

1. **[!UICONTROL General]**, **[!UICONTROL Transactions]** 및 **[!UICONTROL Scope]** 탭을 편집하여 가설을 개인화할 수 있습니다. 자세한 내용은 [가설 모델 만들기](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)를 참조하십시오.
1. **[!UICONTROL Start]** 을 클릭하여 가설을 시작합니다.

   측정을 수행하도록 워크플로우가 자동으로 생성됩니다. 가설 구성에 따라 이름이 자동으로 정의됩니다.

   >[!CAUTION]
   >
   >**[!UICONTROL Keep execution workflow]** 상자를 선택한 경우 액세스할 수 있습니다.\
   >가설을 실행하는 동안 오류가 발생하는 경우 디버깅 목적으로만 이 옵션을 활성화해야 합니다. 자동으로 생성된 워크플로우는 Adobe Campaign 탐색기의 **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]** 폴더에 저장됩니다.
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

1. 필요에 따라 [이 섹션](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)에 설명된 대로 하나 이상의 **[!UICONTROL Delivery]** 유형 템플릿을 만들 수 있습니다
1. 마케팅 캠페인 및 타겟팅 워크플로우를 만듭니다.
1. 게재 창에서 **[!UICONTROL Delivery measurement]** 아이콘을 클릭합니다.
1. 가설 템플릿을 선택합니다(모델에 구성된 쿼리가 가설 창에 표시됩니다.).

   모델이 구성된 날짜를 기반으로, 캠페인이 끝나면 가설이 자동으로 계산됩니다([가설 템플릿 실행 설정](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings) 참조).

   ![](assets/response_hypothesis_instance_creation_008.png)

## 캠페인 {#adding-a-default-hypothesis-to-deliveries-for-a-campaign} 게재에 기본 가설을 추가합니다.

캠페인 수준에서 가설을 직접 참조할 수 있습니다. 이 경우 가설이 캠페인에서 만든 모든 게재에 자동으로 연결됩니다. 방법은 다음과 같습니다.

1. 캠페인의 **[!UICONTROL Edit]** 탭으로 이동합니다.
1. 측정 섹션에서 **[!UICONTROL Default hypotheses]** 탭을 클릭합니다.

   ![](assets/response_hypothesis_instance_creation_010.png)

1. **[!UICONTROL Add]** 을 클릭하고 가설 템플릿을 선택합니다.

   ![](assets/response_hypothesis_instance_creation_011.png)

   이제 이 템플릿을 기반으로 한 가설이 캠페인에 대한 각 새로운 게재에서 기본적으로 참조됩니다.

   ![](assets/response_hypothesis_instance_creation_012.png)

가설 결과는 가설 **[!UICONTROL General]** 및 **[!UICONTROL Reactions]** 탭에서 볼 수 있습니다( [가설 추적](../../campaign/using/hypothesis-tracking.md) 참조)

자세한 내용은 [이 샘플](#example--creating-a-hypothesis-linked-to-a-delivery)을 참조하십시오.

## 오퍼 {#creating-a-hypothesis-on-an-offer}에 가설을 만듭니다

오퍼 제안에 대한 가설을 만드는 것은 즉시 게재 가설을 작성하는 것과 비슷합니다. 오퍼가 활성화된 한 가설이 실행될 수 있습니다. 계산 기간은 오퍼 제안 날짜를 기준으로 합니다. 가설을 통해 수신자를 구매에 연결할 수 있으면 수락될 가능성이 있는 오퍼 제안 상태가 자동으로 변경될 수 있습니다(자세한 내용은 [트랜잭션](../../campaign/using/hypothesis-templates.md#transactions) 참조).

1. [이 섹션](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)에 설명된 대로 하나 이상의 **[!UICONTROL Offer]** 유형 모델을 만듭니다.
1. **[!UICONTROL Campaign management > Measurement hypotheses]** 노드로 이동합니다.
1. 이전에 만든 모델을 선택하여 **[!UICONTROL Offers]** 유형 가설을 만듭니다.

   ![](assets/response_hypothesis_instance_offer_001.png)

   모델에서 생성된 쿼리가 창에 나타납니다.

   ![](assets/response_hypothesis_instance_offer_003.png)

1. 가설을 만들 오퍼를 선택합니다.

   ![](assets/response_hypothesis_instance_offer_004.png)

1. 필요한 경우 쿼리를 세분화합니다.
1. **[!UICONTROL Start]** 을 클릭하여 가설을 실행합니다.
1. 가설 결과는 **[!UICONTROL General]** 및 **[!UICONTROL Reactions]** 탭에서 볼 수 있습니다( [가설 추적](../../campaign/using/hypothesis-tracking.md) 참조).

   오퍼에 대한 가설이 **[!UICONTROL Measurement]** 탭에서 참조됩니다.

   ![](assets/response_hypothesis_instance_offer_007.png)

   가설 템플릿에서 **[!UICONTROL Update offer proposition status]** 옵션이 활성화된 경우, 오퍼 제안 상태가 자동으로 변경되므로 캠페인의 영향에 대한 피드백을 제공합니다(자세한 내용은 [트랜잭션](../../campaign/using/hypothesis-templates.md#transactions) 참조).

## 예:게재 {#example--creating-a-hypothesis-linked-to-a-delivery}에 연결된 가설 만들기

이 예에서는 게재에 연결된 가설을 만들려고 합니다. 이 가설은 이전에 만든 모델을 기반으로 합니다( [이 샘플](../../campaign/using/hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery) 참조). 그런 다음 모델에서 상속된 쿼리를 세분화하여 구매 테이블의 특정 문서에 대한 가설을 만듭니다.

1. 캠페인 및 게재 만들기(자세한 내용은 [마케팅 캠페인 만들기](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign))를 참조하십시오.

   이 예제에서는 DM 유형 게재를 사용합니다.

1. 시드 주소 구성:이전에 만든 가설 템플릿은 반응 결과에 컨트롤 그룹을 고려하도록 구성되었습니다.

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >자세한 내용은 [컨트롤 그룹 정의](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)를 참조하십시오.

1. **[!UICONTROL Direct mail delivery]** 을 열고 **[!UICONTROL Delivery measurement]** 아이콘을 클릭한 다음 **[!UICONTROL Add]** 를 클릭합니다.

   ![](assets/response_hypothesis_delivery_example_002.png)

1. 드롭다운 목록에서 이전에 생성한 가설 템플릿을 선택합니다.

   ![](assets/response_hypothesis_delivery_example_004.png)

   모델에서 생성된 쿼리가 표시됩니다.

   ![](assets/response_hypothesis_delivery_example_005.png)

1. **[!UICONTROL Edit query...]** 을 클릭하고 가설이 우려되는 제품을 입력하여 쿼리를 세분화합니다.

   ![](assets/response_hypothesis_delivery_example_006.png)

   캠페인의 **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** 탭에서 가설이 게재와 연결되어 있는지 확인할 수 있습니다.

   ![](assets/response_hypothesis_delivery_example_008.png)

1. 타겟팅 워크플로우를 시작하고 캠페인이 완료될 때까지 필요한 검사를 실행합니다(자세한 내용은 [이 섹션](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery) 참조).

   ![](assets/response_hypothesis_delivery_example_009.png)

1. Adobe Campaign 트리에서 **[!UICONTROL Campaign management > Measurement hypotheses]** 노드로 이동하여 가설을 통해 계산된 지표를 확인합니다.

   ![](assets/response_hypothesis_delivery_example_010.png)
