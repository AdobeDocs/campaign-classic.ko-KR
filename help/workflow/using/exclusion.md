---
product: campaign
title: 예외
description: 제외 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: f4fe97d9-6571-4aa5-8022-b0af9d5a6a13
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 예외{#exclusion}



An **제외**-type 활동은 하나 이상의 다른 타겟이 추출되는 기본 타겟을 기반으로 타겟을 생성합니다.

이 활동을 구성하려면 해당 레이블을 입력하고 기본 수신자 세트를 선택합니다. 기본 세트의 모집단을 사용하면 결과를 구성할 수 있습니다. 기본 세트와 하나 이상의 시작 활동에 의해 공유된 프로필은 제외됩니다.

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>제외 활동 구성 및 사용에 대한 자세한 내용은 을 참조하십시오. [모집단 제외(제외)](targeting-data.md#excluding-a-population--exclusion-).

다음 확인: **[!UICONTROL Generate complement]** 나머지 모집단을 활용하려면 옵션을 선택합니다. 보조 항목에는 주 유입 인구에서 이탈 인구를 뺀 값이 포함됩니다. 그런 다음 다음과 같이 추가 출력 전환이 활동에 추가됩니다.

![](assets/s_user_segmentation_exclu_compl.png)

## 제외 예 {#exclusion-examples}

다음 예제에서는 파리 거주자를 제외하면서 18세에서 30세 사이의 수신자 목록을 컴파일합니다.

1. 삽입 및 열기 **[!UICONTROL Exclusion]** -두 개의 쿼리 다음에 활동을 입력합니다. 첫 번째 쿼리는 파리에 거주하는 수신자를 타겟팅합니다. 두 번째 쿼리는 18세에서 30세를 대상으로 한다.
1. 메인 세트를 입력합니다. 메인 세트는 다음과 같습니다 **18-30세** 쿼리. 두 번째 세트에 속하는 요소는 최종 결과에서 제외됩니다.
1. 다음 확인: **[!UICONTROL Generate complement]** 제외 후 남아 있는 데이터를 활용하려면 옵션을 선택합니다. 이 경우 보완체는 파리에 거주하는 만 18세에서 30세의 수급자로 구성된다.
1. 제외 구성을 승인한 다음 업데이트 목록 활동을 결과에 삽입합니다. 필요한 경우 보충 자료에 추가 목록 업데이트를 삽입할 수도 있습니다.
1. 워크플로우를 실행합니다. 이 예에서 결과는 18세에서 30세 사이의 수신자로 구성되지만 파리에 거주하는 수신자는 제외되어 보충 자료로 전송됩니다.

   ![](assets/exclusion_example.png)

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수로 정의된 대상을 지정해야 합니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 세트는 제외로 인한 대상을 식별합니다. **[!UICONTROL tableName]** 는 대상 식별자를 기록하는 테이블의 이름입니다. **[!UICONTROL schema]** 모집단의 스키마(일반적으로 nms:recipient)이며, **[!UICONTROL recCount]** 는 테이블에 있는 요소의 수입니다.

보체와 관련된 전환은 동일한 매개 변수를 갖는다.
