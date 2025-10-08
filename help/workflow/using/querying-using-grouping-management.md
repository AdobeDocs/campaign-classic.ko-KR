---
product: campaign
title: 그룹 관리를 사용한 쿼리
description: 그룹 관리를 사용하여 쿼리를 수행하는 방법에 대해 알아봅니다
feature: Query Editor, Workflows
hide: true
hidefromtoc: true
exl-id: 23bccb48-60ab-46c9-be26-2fa35243d61e
source-git-commit: 9df46ed923831ffdfb28acddfbc371cecafb251c
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 3%

---

# 그룹 관리를 사용한 쿼리 {#querying-using-grouping-management}



이 예제에서는 쿼리를 실행하여 이전 게재 중 30번 이상 타겟팅된 모든 이메일 도메인을 찾으려고 합니다.

* 어떤 테이블을 선택해야 합니까?

  받는 사람 테이블(nms:recipient)

* 출력 열에서 선택할 필드입니까?

  이메일 도메인 및 기본 키(개수 포함)

* 데이터 그룹화하시겠습니까?

  기본 키 수가 30개를 초과하는 이메일 도메인 기준. 이 작업은 **[!UICONTROL Group by + Having]** 옵션을 사용하여 수행됩니다. **[!UICONTROL Group by + Having]**&#x200B;을(를) 사용하면 데이터를 그룹화(&quot;그룹화 기준&quot;)하고 그룹화된 항목(&quot;있음&quot;)을 선택할 수 있습니다.

이 예제를 만들려면 다음 단계를 적용합니다.

1. **[!UICONTROL Generic query editor]**&#x200B;을(를) 열고 수신자 테이블(**nms:recipient**)을 선택합니다.

   ![](assets/query_editor_02.png)

1. **[!UICONTROL Data to extract]** 창에서 **[!UICONTROL Email domain]** 및 **[!UICONTROL Primary key]** 필드를 선택합니다. **[!UICONTROL Primary key]** 필드에서 개수를 실행합니다.

   기본 키 수에 대한 자세한 정보는 [이 섹션](../../platform/using/about-queries-in-campaign.md)을 참조하세요.

1. **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 상자를 선택합니다.

   ![](assets/query_editor_nveau_29.png)

1. **[!UICONTROL Sorting]** 창에서 전자 메일 도메인을 내림차순으로 정렬합니다. 이렇게 하려면 **[!UICONTROL Yes]** 열에서 **[!UICONTROL Descending sort]**&#x200B;을(를) 확인하십시오. **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/query_editor_nveau_70.png)

1. **[!UICONTROL Data filtering]**&#x200B;에서 **[!UICONTROL Filtering conditions]**&#x200B;을(를) 선택합니다. **[!UICONTROL Target elements]** 창으로 이동하여 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Data grouping]** 창에서 **[!UICONTROL Email domain]**&#x200B;을(를) 클릭하여 **[!UICONTROL Add]**&#x200B;을(를) 선택합니다.

   이 데이터 그룹화 창은 **[!UICONTROL Handle groupings (GROUP BY + HAVING])** 상자를 선택한 경우에만 표시됩니다.

   ![](assets/query_editor_blocklist_04.png)

1. 30번 이상 타겟팅된 전자 메일 도메인만 결과로 반환되기를 원하므로 **[!UICONTROL Grouping condition]** 창에서 기본 키 수를 30보다 크게 지정하십시오.

   **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** 상자를 선택하면 이 창이 나타납니다. 이 창에서 그룹화 결과가 필터링됩니다(HAVING).

   ![](assets/query_editor_blocklist_05.png)

1. **[!UICONTROL Data formatting]** 창에서 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다. 여기에는 서식이 필요하지 않습니다.
1. 데이터 미리 보기 창에서 **[!UICONTROL Launch data preview]**&#x200B;을(를) 클릭합니다. 여기에서 30번 이상 타깃팅된 세 개의 다른 전자 메일 도메인이 반환됩니다.

   ![](assets/query_editor_blocklist_06.png)
