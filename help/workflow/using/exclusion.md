---
product: campaign
title: 예외
description: 제외 워크플로우 활동에 대해 자세히 알아보기
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: f4fe97d9-6571-4aa5-8022-b0af9d5a6a13
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 예외{#exclusion}

![](../../assets/common.svg)

**제외** 유형 활동은 하나 이상의 다른 대상이 추출되는 기본 대상을 기반으로 대상을 만듭니다.

이 활동을 구성하려면 해당 레이블을 입력하고 기본 수신자 세트를 선택합니다. 기본 세트의 모집단을 사용하여 결과를 구성할 수 있습니다. 기본 집합에서 공유한 프로필과 시작 활동 중 하나 이상이 제외됩니다.

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>제외 활동 구성 및 사용에 대한 자세한 내용은 [모집단 제외(제외)](targeting-data.md#excluding-a-population--exclusion-)를 참조하십시오.

나머지 모집단을 활용하려면 **[!UICONTROL Generate complement]** 옵션을 선택합니다. 이 보수 안에는 들어오는 주요 모집단에서 보내는 모집단을 뺀 수가 포함될 것이다. 그러면 다음과 같이 활동에 추가 출력 전환이 추가됩니다.

![](assets/s_user_segmentation_exclu_compl.png)

## 제외 예 {#exclusion-examples}

다음 예제에서는 Paris 거주자를 제외하고 18세에서 30세 사이의 수신자 목록을 컴파일하려고 합니다.

1. 두 쿼리 다음에 나오는 **[!UICONTROL Exclusion]** -type 활동을 삽입하고 엽니다. 첫 번째 쿼리는 파리에 거주하는 수신자를 타겟으로 합니다. 두 번째 쿼리는 18세에서 30세 사이의 사람들을 대상으로 합니다.
1. 기본 세트를 입력합니다. 여기에서 기본 집합은 **18-30년** 쿼리입니다. 두 번째 세트와 관련된 요소는 최종 결과에서 제외됩니다.
1. 제외 후 남은 데이터를 활용하려면 **[!UICONTROL Generate complement]** 옵션을 선택합니다. 이 경우, 그 보수는 파리에 사는 18세에서 30세 사이의 수신자들로 구성되어 있다.
1. 제외 구성을 승인한 후 결과에 업데이트 목록 활동을 삽입합니다. 필요한 경우 보완 목록에 추가 목록 업데이트를 삽입할 수도 있습니다.
1. 워크플로우를 실행합니다. 이 예제에서 그 결과는 18~30세의 수신자로 구성되지만 Paris에 있는 수신자는 제외되어 보수로 전송됩니다.

   ![](assets/exclusion_example.png)

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수로 정의된 대상을 지정해야 합니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 집합은 제외로 인한 대상을 식별합니다. **[!UICONTROL tableName]** 는 대상 식별자를 기록하는 테이블의 이름이며  **[!UICONTROL schema]** 는 모집단의 스키마(일반적으로 nms:recipient)이며  **[!UICONTROL recCount]** 표에 있는 요소의 수입니다.

보어와 연관된 전환에는 동일한 매개 변수가 있습니다.
