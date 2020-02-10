---
title: 교차
seo-title: 교차
description: 교차
seo-description: null
page-status-flag: never-activated
uuid: a8ff7a66-6c12-4e3c-ad45-d11b34ca64ff
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: d0dd9c74-aad5-452e-a11d-c231dacd2aec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 교차{#intersection}

교차 **유형**&#x200B;활동은 수신한 대상의 교차로부터 대상을 만듭니다.

교차를 사용하면 모든 인바운드 활동 결과에 공통인 모집단만 추출할 수 있습니다. 수신한 모든 결과가 있는 대상이 생성됩니다.따라서 교차를 실행하려면 모든 이전 활동이 완료되어야 합니다. 이 활동을 구성하려면 결과에 대한 레이블과 옵션을 입력해야 합니다.

![](assets/s_user_segmentation_inter.png)

교차 활동 구성 및 사용에 대한 자세한 내용은 연결 데이터 [추출(교차)을](../../workflow/using/targeting-data.md#extracting-joint-data--intersection-)참조하십시오.

나머지 모집단을 처리하려면 **[!UICONTROL Generate complement]** 옵션을 선택합니다. 보수는 모든 인바운드 활동의 결과 결합에서 교차를 뺀 값을 포함합니다. 그러면 다음과 같이 활동에 추가 아웃바운드 전환이 추가됩니다.

![](assets/s_user_segmentation_inter_compl.png)

## 교차 예 {#intersection-example}

다음 예에서 교차점의 목적은 목록을 만들기 위해 세 개의 간단한 쿼리에 공통으로 받는 사람을 계산하는 것입니다.

1. 세 개의 간단한 쿼리 후에 **[!UICONTROL Intersection]** -type 활동을 삽입합니다.

   이 예에서;이번 조사는 18세에서 30세 사이 의 남녀 수급자를 대상으로 실시됐다.

1. 교차를 구성합니다. 이렇게 하려면 쿼리에서 발생한 모집단에 일관된 데이터가 포함되므로 **[!UICONTROL Keys only]** 조정 방법을 선택합니다.
1. 쿼리에 대한 추가 데이터를 입력한 경우 관련 상자를 선택하여 받는 사람이 공유하는 데이터만 유지하도록 선택할 수 있습니다.
1. 나머지 데이터를 사용하려면(검색과 관련되지만 교차점은 아님) **[!UICONTROL Generate complement]** 상자를 선택합니다.
1. 교차 결과 후에 목록 업데이트 활동을 추가합니다. 또한 사용하려는 경우 목록 업데이트를 보정에 추가할 수도 있습니다.
1. 워크플로우를 실행합니다. 여기에서 두 명의 받는 사람이 동시에 세 개의 입력 쿼리에 적용됩니다. 보수는 세 개의 쿼리 중 한 개 또는 두 개만 지원하는 5명의 수신자로 구성됩니다.

   교차 결과가 첫 번째 목록 업데이트로 전송됩니다. 보완 사용을 선택한 경우 두 번째 목록 업데이트에도 전송됩니다.

   ![](assets/intersection_example.png)

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수에 의해 정의된 대상을 지정해야 합니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 집합은 교차로 결과 대상을 식별합니다. **[!UICONTROL tableName]** 는 대상 식별자를 기록하는 테이블의 이름이며 **[!UICONTROL schema]** 모집단(일반적으로 **[!UICONTROL nms:recipient]**)의 스키마이며 **[!UICONTROL recCount]** 표의 요소 수입니다.
