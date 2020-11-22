---
solution: Campaign Classic
product: campaign
title: 예외
description: 제외 워크플로우 활동에 대한 자세한 내용
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---


# 예외{#exclusion}

제외 ****&#x200B;유형 활동은 하나 이상의 다른 타겟이 추출되는 기본 대상을 기반으로 대상을 만듭니다.

이 활동을 구성하려면 해당 레이블을 입력하고 기본 수신자 세트를 선택합니다.기본 세트의 모집단으로 결과를 만들 수 있습니다. 기본 집합에서 공유되는 프로파일과 시작 활동 중 하나 이상이 제외됩니다.

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>제외 활동 구성 및 사용에 대한 자세한 내용은 인구 [제외(제외)를 참조하십시오](../../workflow/using/targeting-data.md#excluding-a-population--exclusion-).

Check the **[!UICONTROL Generate complement]** option if you wish to exploit the remaining population. 그 보완에는 들어오는 주요 인구와 나가는 인구를 뺀 것이 포함될 것이다. 그러면 다음과 같이 활동에 추가 출력 전환이 추가됩니다.

![](assets/s_user_segmentation_exclu_compl.png)

## 제외 예 {#exclusion-examples}

다음 예제는 파리의 거주자를 제외하고 18~30세 사이의 수신자 목록을 작성하는 것입니다.

1. 두 쿼리 다음에 **[!UICONTROL Exclusion]** -type 활동을 삽입하고 엽니다. 첫 번째 쿼리는 파리에 거주하는 수신자를 대상으로 합니다. 두 번째 쿼리는 18세에서 30세 사이의 사람들을 대상으로 합니다.
1. 기본 세트를 입력합니다. 여기 메인 세트는 **18-30년 된** 질문입니다. 두 번째 세트와 관련된 요소는 최종 결과에서 제외됩니다.
1. 제외 후에 남아 있는 데이터를 이용하려면 **[!UICONTROL Generate complement]** 옵션을 선택합니다. 이 경우 18~30세 이상 프랑스 파리에 사는 수신자로 채워진다.
1. 제외 구성을 승인한 후 결과에 업데이트 목록 활동을 삽입합니다. 필요한 경우 보완에 대한 추가 목록 업데이트를 삽입할 수도 있습니다.
1. 워크플로우를 실행합니다. 이 예에서는 18~30세 사이의 수신자로 구성되지만 파리에 사는 수신자는 제외되어 보완하는 주소로 보내집니다.

   ![](assets/exclusion_example.png)

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수로 정의된 대상을 지정해야 합니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 집합은 제외로 인해 발생한 대상을 식별합니다. **[!UICONTROL tableName]** 는 대상 식별자를 기록하는 테이블 이름 **[!UICONTROL schema]** 으로, 모집단(일반적으로 nms:recipient)의 스키마이며 표의 요소 **[!UICONTROL recCount]** 수입니다.

보완과 연결된 전환에는 동일한 매개 변수가 있습니다.
