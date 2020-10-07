---
title: 그룹 관리를 사용하여 쿼리
description: 그룹 관리를 사용하여 쿼리를 수행하는 방법 알아보기
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---


# 그룹 관리를 사용하여 쿼리 {#querying-using-grouping-management}

이 예에서는 이전 배달 중 30회 이상 타깃팅된 모든 이메일 도메인을 찾기 위해 쿼리를 실행하려 합니다.

* 어떤 표를 선택해야 합니까?

   받는 사람 테이블(nms:recipient)

* 출력 열에서 선택할 필드를 선택하십시오.

   이메일 도메인 및 기본 키(카운트 포함)

* 데이터 그룹화

   기본 키 개수가 30개 이상인 이메일 도메인을 기준으로 합니다. 이 작업은 **[!UICONTROL Group by + Having]** 선택 사항과 함께 수행됩니다. **[!UICONTROL Group by + Having]** 데이터(&quot;그룹별&quot;)를 그룹화하고 그룹화된 항목(&quot;having&quot;)을 선택할 수 있도록 해줍니다.

이 예제를 만들려면 다음 단계를 수행하십시오.

1. 을 열고 수신자 표( **[!UICONTROL Generic query editor]** nms:recipient ****)를 선택합니다.

   ![](assets/query_editor_02.png)

1. 창에서 **[!UICONTROL Data to extract]** 및 **[!UICONTROL Email domain]** **[!UICONTROL Primary key]** 필드를 선택합니다. 필드에서 카운트를 **[!UICONTROL Primary key]** 실행합니다.

   기본 키 카운트에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../platform/using/defining-filter-conditions.md#building-expressions).

1. 체크 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 상자를

   ![](assets/query_editor_nveau_29.png)

1. 창에서 **[!UICONTROL Sorting]** 이메일 도메인을 내림차순으로 정렬합니다. 이렇게 하려면 열 **[!UICONTROL Yes]** 을 **[!UICONTROL Descending sort]** 확인하십시오. **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/query_editor_nveau_70.png)

1. **[!UICONTROL Data filtering]**&#x200B;에서 **[!UICONTROL Filtering conditions]**&#x200B;을(를) 선택합니다. 창으로 **[!UICONTROL Target elements]** 가서 을 클릭합니다 **[!UICONTROL Next]**.
1. 창에서 **[!UICONTROL Data grouping]** 을 클릭하여 **[!UICONTROL Email domain]** 을 선택합니다 **[!UICONTROL Add]**.

   이 데이터 그룹 창은) 상자를 선택한 경우에만 **[!UICONTROL Handle groupings (GROUP BY + HAVING]**&#x200B;표시됩니다.

   ![](assets/query_editor_blocklist_04.png)

1. 30번 이상 타깃팅된 이메일 도메인만 결과로 반환하도록 하기 때문에 **[!UICONTROL Grouping condition]** 창에서 기본 키 카운트가 30보다 큰 값을 표시합니다.

   이 창은 **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** 상자를 선택하면 나타납니다.이 위치에서 그룹 결과가 필터링됩니다(HAVING).

   ![](assets/query_editor_blocklist_05.png)

1. 창에서 **[!UICONTROL Data formatting]** 다음을 클릭합니다 **[!UICONTROL Next]**.여기에 서식을 지정할 필요가 없습니다.
1. 데이터 미리 보기 창에서 다음을 클릭합니다 **[!UICONTROL Launch data preview]**.여기에서 30회 이상 타깃팅된 세 개의 다른 이메일 도메인이 반환됩니다.

   ![](assets/query_editor_blocklist_06.png)
