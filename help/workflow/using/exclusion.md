---
title: 예외
seo-title: 예외
description: 예외
seo-description: null
page-status-flag: never-activated
uuid: e4f54a0b-2fec-4415-986b-83c8928ed174
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: acab51f3-686b-4d2b-bb02-8fbfae36b1ba
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 예외{#exclusion}

제외 **유형**&#x200B;활동은 하나 이상의 다른 대상이 추출되는 기본 대상을 기반으로 대상을 만듭니다.

이 활동을 구성하려면 해당 레이블을 입력하고 기본 수신자 세트를 선택합니다.기본 세트의 모집단을 사용하여 결과를 구성할 수 있습니다. 기본 세트와 시작 활동 중 하나 이상이 공유하는 프로필은 제외됩니다.

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>제외 활동 구성 및 사용에 대한 자세한 내용은 인구 [제외(제외)](../../workflow/using/targeting-data.md#excluding-a-population--exclusion-)를 참조하십시오.

나머지 인구를 이용하려면 **[!UICONTROL Generate complement]** 옵션을 선택합니다. 이 보수는 들어오는 주 모집단에서 나가는 인구를 뺀 것을 포함한다. 그러면 다음과 같이 추가 출력 전환이 활동에 추가됩니다.

![](assets/s_user_segmentation_exclu_compl.png)

## 제외 예 {#exclusion-examples}

다음 예에서는 파리의 거주자를 제외하고 18세에서 30세 사이의 수신자 목록을 취합하려고 합니다.

1. 두 쿼리 다음에 **[!UICONTROL Exclusion]** -type 활동을 삽입하고 엽니다. 첫 번째 쿼리는 파리에 거주하는 수신자를 대상으로 합니다. 두 번째 쿼리는 18세에서 30세 사람들을 대상으로 합니다.
1. 기본 세트를 입력합니다. 18-30 **년 된** 쿼리는 여기에 있습니다. 두 번째 세트와 관련된 요소는 최종 결과에서 제외됩니다.
1. 제외 이후에 남아 있는 데이터를 활용하려면 **[!UICONTROL Generate complement]** 옵션을 선택합니다. 이 경우 18세에서 30세 사이의 수신자들이 파리에 살고 있다.
1. 제외 구성을 승인한 후 결과에 업데이트 목록 활동을 삽입합니다. 필요한 경우 보완 목록에 대한 추가 목록 업데이트를 삽입할 수도 있습니다.
1. 워크플로우를 실행합니다. 이 예에서는 18세에서 30세 사이의 수신자로 구성되지만 파리에 거주하는 수신자는 제외되어 보수로 보내집니다.

   ![](assets/exclusion_example.png)

블랙 리스트 가져오기 예제는 **읽기**&#x200B;목록에 [있는 제외 유형 활동을](../../workflow/using/read-list.md)사용합니다.

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수에 의해 정의된 대상을 지정해야 합니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 집합은 제외로 인해 발생한 대상을 식별합니다. **[!UICONTROL tableName]** 는 대상 식별자를 기록하는 테이블의 이름이며 **[!UICONTROL schema]** 모집단(일반적으로 nms:recipient)의 스키마이며 **[!UICONTROL recCount]** 표의 요소 수입니다.

보수와 연결된 전환에는 동일한 매개 변수가 있습니다.
