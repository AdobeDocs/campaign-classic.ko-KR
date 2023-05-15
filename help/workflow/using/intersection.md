---
product: campaign
title: 교차
description: 교차
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: f426bf02-9899-49eb-b699-728d51b57c64
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 13%

---

# 교차{#intersection}

>[!CONTEXTUALHELP]
>id="ac_workflow_intersection"
>title="교차 활동"
>abstract="교차 유형 활동은 수신된 대상의 교차점에서 대상을 만듭니다. 교차를 통해 모든 인바운드 활동 결과에 공통인 모집단만 추출할 수 있습니다."
>additional-url="https://video.tv.adobe.com/v/329373" text="데모 비디오 시청"




An **교차**-type 활동은 수신한 대상의 교차 지점에서 대상을 만듭니다.

교차를 통해 모든 인바운드 활동 결과에 공통인 모집단만 추출할 수 있습니다. 수신한 모든 결과가 있는 대상이 만들어집니다. 따라서 교차를 실행하기 전에 모든 이전 활동을 완료해야 합니다. 이 활동을 구성하려면 결과와 관련된 옵션뿐만 아니라 해당 활동에 대한 레이블을 입력해야 합니다.

![](assets/s_user_segmentation_inter.png)

교차 활동 구성 및 사용에 대한 자세한 내용은 다음을 참조하십시오 [결합 데이터 추출(교차)](targeting-data.md#extracting-joint-data--intersection-).

을(를) 확인합니다. **[!UICONTROL Generate complement]** 나머지 모집단을 처리하려는 경우 선택합니다. 보완 작업에는 모든 인바운드 활동의 결과에서 교차를 제외한 모든 인바운드 활동의 결과가 포함됩니다. 그런 다음 다음과 같이 활동에 추가 아웃바운드 전환이 추가됩니다.

![](assets/s_user_segmentation_inter_compl.png)

## 교차 예 {#intersection-example}

다음 예에서 교차 지점은 목록을 만들기 위해 세 개의 간단한 쿼리에 공통되는 수신자를 계산하기 위한 것입니다.

1. 세 개의 간단한 쿼리 후에 **[!UICONTROL Intersection]** -type activity.

   이 예제에서는 이 쿼리는 각각 18세에서 30세 사이의 남녀 수신자, 파리에 거주하는 수신자 및 18세에서 30세 사이의 수신자 등을 대상으로 합니다.

1. 교차를 구성합니다. 이렇게 하려면 **[!UICONTROL Keys only]** 쿼리로 인한 모집단에 일관된 데이터가 포함되므로 조정 방법을 사용합니다.
1. 쿼리에 대한 추가 데이터를 입력한 경우 관련 상자를 선택하여 수신자가 공유하는 데이터만 유지할 수 있습니다.
1. 나머지 데이터를 사용하려면(쿼리의 경우와 같지만 해당 교차점은 아님) **[!UICONTROL Generate complement]** 상자.
1. 교차 결과 뒤에 목록 업데이트 활동을 추가합니다. 원할 경우 보충 컴퓨터에 목록 업데이트를 추가할 수도 있습니다.
1. 워크플로우를 실행합니다. 여기에서 두 명의 수신자는 입력된 세 개의 쿼리 모두에 동시에 적용됩니다. 이 보수는 세 개의 쿼리 중 하나 또는 두 개에만 적용되는 5명의 수신자로 구성됩니다.

   교차 결과가 첫 번째 목록 업데이트로 전송됩니다. 보충 자료를 사용하도록 선택하면 두 번째 목록 업데이트로도 전송됩니다.

   ![](assets/intersection_example.png)

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수로 정의된 대상을 지정해야 합니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 집합은 교차로 결과 대상을 식별합니다. **[!UICONTROL tableName]** 는 대상 식별자를 기록하는 테이블의 이름입니다. **[!UICONTROL schema]** 는 모집단의 스키마입니다(일반적으로 **[!UICONTROL nms:recipient]**) 및 **[!UICONTROL recCount]** 는 테이블에 있는 요소의 수입니다.
