---
product: campaign
title: 그룹 관리를 사용한 쿼리
description: 그룹 관리를 사용하여 쿼리를 수행하는 방법에 대해 알아봅니다
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
feature: Query Editor, Workflows
exl-id: 23bccb48-60ab-46c9-be26-2fa35243d61e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 4%

---

# 그룹 관리를 사용한 쿼리 {#querying-using-grouping-management}



이 예제에서는 쿼리를 실행하여 이전 게재 중 30번 이상 타겟팅된 모든 이메일 도메인을 찾으려고 합니다.

* 어떤 테이블을 선택해야 합니까?

  수신자 테이블(nms:recipient)

* 출력 열에서 선택할 필드입니까?

  이메일 도메인 및 기본 키(개수 포함)

* 데이터 그룹화하시겠습니까?

  기본 키 수가 30개를 초과하는 이메일 도메인 기준. 이 작업은 **[!UICONTROL Group by + Having]** 옵션을 선택합니다. **[!UICONTROL Group by + Having]** 데이터를 그룹화(&quot;그룹화 기준&quot;)하고 그룹화된 항목(&quot;있음&quot;)을 선택할 수 있습니다.

이 예제를 만들려면 다음 단계를 적용합니다.

1. 를 엽니다. **[!UICONTROL Generic query editor]** 수신자 테이블(**nms:recipient**).

   ![](assets/query_editor_02.png)

1. 다음에서 **[!UICONTROL Data to extract]** 창에서 **[!UICONTROL Email domain]** 및 **[!UICONTROL Primary key]** 필드. 다음에 대한 카운트 실행 **[!UICONTROL Primary key]** 필드.

   기본 키 수에 대한 자세한 내용은 [이 섹션](../../platform/using/defining-filter-conditions.md#building-expressions).

1. 다음 확인: **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 상자.

   ![](assets/query_editor_nveau_29.png)

1. 다음에서 **[!UICONTROL Sorting]** 창에서 이메일 도메인을 내림차순으로 정렬합니다. 이렇게 하려면 다음을 확인하십시오. **[!UICONTROL Yes]** 다음에서 **[!UICONTROL Descending sort]** 열. **[!UICONTROL Next]**&#x200B;를 클릭합니다.

   ![](assets/query_editor_nveau_70.png)

1. **[!UICONTROL Data filtering]**&#x200B;에서 **[!UICONTROL Filtering conditions]**&#x200B;을(를) 선택합니다. 로 이동 **[!UICONTROL Target elements]** 창에서 클릭 **[!UICONTROL Next]**.
1. 다음에서 **[!UICONTROL Data grouping]** 창에서 **[!UICONTROL Email domain]** 다음을 클릭: **[!UICONTROL Add]**.

   이 데이터 그룹화 창은 **[!UICONTROL Handle groupings (GROUP BY + HAVING]**) 상자를 선택했습니다.

   ![](assets/query_editor_blocklist_04.png)

1. 다음에서 **[!UICONTROL Grouping condition]** 30번 이상 타겟팅된 이메일 도메인만 결과로 반환되기를 원하므로 창에서 30보다 큰 기본 키 수를 나타냅니다.

   이 창은 **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** 확인란이 선택됨: 그룹화 결과가 필터링되는 위치입니다(있음).

   ![](assets/query_editor_blocklist_05.png)

1. 다음에서 **[!UICONTROL Data formatting]** 창에서 다음을 클릭: **[!UICONTROL Next]**: 여기에는 서식이 필요하지 않습니다.
1. 데이터 미리보기 창에서 다음을 클릭합니다. **[!UICONTROL Launch data preview]**: 여기에서 30회 이상 타겟팅된 세 개의 다른 이메일 도메인이 반환됩니다.

   ![](assets/query_editor_blocklist_06.png)
