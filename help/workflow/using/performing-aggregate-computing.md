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

이 예에서는 런던에 사는 성별로 받는 사람의 수를 계산하려고 합니다.

* 어떤 표를 선택해야 합니까?

   받는 사람 테이블(**nms:recipient**)

* 출력 열에서 선택해야 하는 필드는 무엇입니까?

   기본 키(카운트 포함) 및 성별

* 어떤 조건을 기준으로 필터링됩니까?

   런던에 거주하는 수신자에 근거해서

이 예제를 만들려면 다음 단계를 수행하십시오.

1. 에서 기본 키 **[!UICONTROL Data to extract]**&#x200B;에 대한 카운트를 정의합니다(이전 예에서 보듯이). 출력 열에 **[!UICONTROL Gender]** 필드를 추가합니다. 열에서 **[!UICONTROL Group]** 옵션을 **[!UICONTROL Gender]** 선택합니다. 이렇게 해서 받는 사람은 성별별로 분류된다.

   ![](assets/query_editor_nveau_27.png)

1. 창에서 **[!UICONTROL Sorting]** 다음을 클릭합니다 **[!UICONTROL Next]**.여기에서 정렬할 필요가 없습니다.
1. 데이터 필터링을 구성합니다. 여기에서 London에 거주하는 연락처로 선택 사항을 제한하려는 경우

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >값은 대/소문자를 구분합니다. &#39;London&#39; 값이 대문자 없이 조건에 입력되고 수신자 목록에 대문자 문자가 포함된 &quot;London&quot;이라는 단어가 포함된 경우 쿼리가 실패합니다.

1. 창에서 **[!UICONTROL Data formatting]** 다음을 클릭합니다 **[!UICONTROL Next]**.이 예에는 서식이 필요하지 않습니다.
1. 미리 보기 창에서 을 클릭합니다 **[!UICONTROL Launch data preview]**.

   성별별로 각 정렬에 대해 세 개의 별도 값이 있습니다. **여성** , 남성 **1** , 성별 **이 알려지지 않은 경우** 0. 이 예에서는 10명의 여성, 16명의 남성 및 2명의 성이 알려지지 않은 사람들이 포함되어 있습니다.

   ![](assets/query_editor_agregat_04.png)
