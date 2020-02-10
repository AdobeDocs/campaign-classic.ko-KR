---
title: 그룹화 관리를 사용하여 쿼리
description: 그룹 관리를 사용하여 쿼리를 수행하는 방법 알아보기
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# 그룹화 관리를 사용하여 쿼리 {#querying-using-grouping-management}

이 예에서는 쿼리를 실행하여 이전 배달 동안 30회 이상 타깃팅된 모든 이메일 도메인을 찾으려고 합니다.

* 어떤 표를 선택해야 합니까?

   받는 사람 테이블(nms:recipient)

* 출력 열에서 선택할 필드를 선택하십시오.

   이메일 도메인 및 기본 키(카운트 포함)

* 데이터 그룹화

   기본 키 수가 30개 이상인 이메일 도메인을 기반으로 합니다. 이 작업은 **[!UICONTROL Group by + Having]** 옵션과 함께 수행됩니다. **[!UICONTROL Group by + Having]** 데이터(&quot;그룹별&quot;)를 그룹화하고 그룹화된 항목(&quot;having&quot;)을 선택할 수 있습니다.

이 예를 만들려면 다음 단계를 적용합니다.

1. 을 **[!UICONTROL Generic query editor]** 열고 수신자 테이블(**nms:recipient**)을 선택합니다.

   ![](assets/query_editor_02.png)

1. 창에서 **[!UICONTROL Data to extract]** 및 **[!UICONTROL Email domain]** **[!UICONTROL Primary key]** 필드를 선택합니다. 필드에서 카운트를 **[!UICONTROL Primary key]** 실행합니다.

   주요 키 수에 대한 자세한 내용은 [이 섹션을](../../platform/using/defining-filter-conditions.md#building-expressions)참조하십시오.

1. 체크 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 상자를 선택합니다.

   ![](assets/query_editor_nveau_29.png)

1. 창에서 이메일 도메인을 내림차순으로 정렬합니다. **[!UICONTROL Sorting]** 이렇게 하려면 **[!UICONTROL Yes]** 열을 **[!UICONTROL Descending sort]** 확인하십시오. 클릭 **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_70.png)

1. 에서 **[!UICONTROL Data filtering]**&#x200B;을 선택합니다 **[!UICONTROL Filtering conditions]**. 창으로 **[!UICONTROL Target elements]** 이동하여 을 클릭합니다 **[!UICONTROL Next]**.
1. 창에서 을 클릭하여 **[!UICONTROL Data grouping]** 을 **[!UICONTROL Email domain]** **[!UICONTROL Add]**&#x200B;선택합니다.

   이 데이터 그룹화 창은 **[!UICONTROL Handle groupings (GROUP BY + HAVING]**) 상자를 선택한 경우에만 표시됩니다.

   ![](assets/query_editor_blacklist_04.png)

1. 30번 이상 타깃팅된 이메일 도메인만 결과로 반환하도록 하기 때문에 **[!UICONTROL Grouping condition]** 창에서 기본 키 개수를 30보다 크게 표시합니다.

   이 창은 **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** 상자를 선택하면 나타납니다.여기에서 그룹화 결과가 필터링됩니다(HAVING).

   ![](assets/query_editor_blacklist_05.png)

1. 창에서 다음을 **[!UICONTROL Data formatting]** 클릭합니다 **[!UICONTROL Next]**.여기에 서식을 지정할 필요가 없습니다.
1. 데이터 미리 보기 창에서 **[!UICONTROL Launch data preview]**&#x200B;다음을 클릭합니다.여기에서 30회 이상 타깃팅된 세 개의 서로 다른 이메일 도메인이 반환됩니다.

   ![](assets/query_editor_blacklist_06.png)
