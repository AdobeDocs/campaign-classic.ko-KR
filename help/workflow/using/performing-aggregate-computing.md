---
solution: Campaign Classic
product: campaign
title: 집계 컴퓨팅 수행
description: 쿼리에서 집계 계산을 수행하는 방법 알아보기
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 2%

---


# 집계 컴퓨팅 수행 {#performing-aggregate-computing}

이 예에서는 런던에 거주하는 수신자의 수를 성에 따라 계산하려고 합니다.

* 어떤 표를 선택해야 합니까?

   받는 사람 테이블(**nms:recipient**)

* 출력 열에서 어떤 필드를 선택해야 합니까?

   기본 키(카운트 포함) 및 성별

* 어떤 조건에 따라 정보가 필터링됩니까?

   런던에 살고 있는 수신자를 바탕으로

이 예제를 만들려면 다음 단계를 수행하십시오.

1. **[!UICONTROL Data to extract]**&#x200B;에서 기본 키에 대한 카운트를 정의합니다(이전 예와 같이). 출력 열에 **[!UICONTROL Gender]** 필드를 추가합니다. **[!UICONTROL Gender]** 열에서 **[!UICONTROL Group]** 옵션을 선택합니다. 이렇게 해서 받는 사람은 성별로 분류될 것이다.

   ![](assets/query_editor_nveau_27.png)

1. **[!UICONTROL Sorting]** 창에서 **[!UICONTROL Next]**:여기에서 정렬할 필요가 없습니다.
1. 데이터 필터링을 구성합니다. 여기에서 선택한 항목을 런던에 거주하는 연락처로 제한할 수 있습니다.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >값은 대/소문자를 구분합니다. &#39;London&#39; 값이 대문자 없이 조건에 입력되고 받는 사람 목록에 대문자 문자가 포함된 &quot;London&quot;이라는 단어가 포함된 경우 쿼리가 실패합니다.

1. **[!UICONTROL Data formatting]** 창에서 **[!UICONTROL Next]**:이 예에는 서식이 필요하지 않습니다.
1. 미리 보기 창에서 **[!UICONTROL Launch data preview]**&#x200B;을 클릭합니다.

   성별별로 각 정렬에 대해 세 개의 개별 값이 있습니다.성별을 알 수 없는 경우 **2**, 여성은 **1**, 성은 **0**&#x200B;입니다. 이 예에서 목록에는 성이 알려지지 않은 10명의 여성, 16명의 남성 및 2명이 포함되어 있습니다.

   ![](assets/query_editor_agregat_04.png)
