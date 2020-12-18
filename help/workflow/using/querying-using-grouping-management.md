---
solution: Campaign Classic
product: campaign
title: 그룹 관리를 사용하여 쿼리
description: 그룹 관리를 사용하여 쿼리를 수행하는 방법 알아보기
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---


# 그룹 관리를 사용하여 쿼리 {#querying-using-grouping-management}

이 예에서는 이전 배달 중 30회 이상 타깃팅된 모든 이메일 도메인을 찾기 위한 쿼리를 실행하려 합니다.

* 어떤 표를 선택해야 합니까?

   받는 사람 테이블(nms:recipient)

* 출력 열에서 선택할 필드를 선택하십시오.

   이메일 도메인 및 기본 키(카운트 포함)

* 데이터 그룹화

   기본 키가 30개가 넘는 이메일 도메인을 기반으로 합니다. 이 작업은 **[!UICONTROL Group by + Having]** 옵션과 함께 수행됩니다. **[!UICONTROL Group by + Having]** 데이터(&quot;그룹화 기준&quot;)를 그룹화하고 그룹화된(&quot;포함&quot;)을 선택할 수 있습니다.

이 예제를 만들려면 다음 단계를 수행하십시오.

1. **[!UICONTROL Generic query editor]**&#x200B;을(를) 열고 수신자 테이블(**nms:recipient**)을 선택합니다.

   ![](assets/query_editor_02.png)

1. **[!UICONTROL Data to extract]** 창에서 **[!UICONTROL Email domain]** 및 **[!UICONTROL Primary key]** 필드를 선택합니다. **[!UICONTROL Primary key]** 필드에서 카운트를 실행합니다.

   기본 키 카운트에 대한 자세한 내용은 [이 섹션](../../platform/using/defining-filter-conditions.md#building-expressions)을 참조하십시오.

1. **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 상자를 선택합니다.

   ![](assets/query_editor_nveau_29.png)

1. **[!UICONTROL Sorting]** 창에서 이메일 도메인을 내림차순으로 정렬합니다. 이렇게 하려면 **[!UICONTROL Descending sort]** 열에서 **[!UICONTROL Yes]**&#x200B;을 선택합니다. **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/query_editor_nveau_70.png)

1. **[!UICONTROL Data filtering]**&#x200B;에서 **[!UICONTROL Filtering conditions]**&#x200B;을(를) 선택합니다. **[!UICONTROL Target elements]** 창으로 이동하여 **[!UICONTROL Next]**&#x200B;을 클릭합니다.
1. **[!UICONTROL Data grouping]** 창에서 **[!UICONTROL Add]**&#x200B;를 클릭하여 **[!UICONTROL Email domain]**&#x200B;을 선택합니다.

   이 데이터 그룹화 창은 **[!UICONTROL Handle groupings (GROUP BY + HAVING]**) 상자를 선택한 경우에만 표시됩니다.

   ![](assets/query_editor_blocklist_04.png)

1. 30회 이상 타깃팅된 이메일 도메인만 결과로 반환하도록 하기 때문에 **[!UICONTROL Grouping condition]** 창에서 기본 키 카운트를 30보다 크게 표시합니다.

   이 창은 **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** 상자를 선택하면 나타납니다.그룹화 결과가 필터링되는(HAVING) 영역입니다.

   ![](assets/query_editor_blocklist_05.png)

1. **[!UICONTROL Data formatting]** 창에서 **[!UICONTROL Next]**:여기에 서식을 지정할 필요가 없습니다.
1. 데이터 미리 보기 창에서 **[!UICONTROL Launch data preview]**:여기에서 30회 이상 타깃팅된 서로 다른 3개의 이메일 도메인이 반환됩니다.

   ![](assets/query_editor_blocklist_06.png)
