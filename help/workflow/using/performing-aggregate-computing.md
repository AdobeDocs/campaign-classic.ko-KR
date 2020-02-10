---
title: 집계 컴퓨팅 수행
description: 쿼리에서 집계 계산을 수행하는 방법 알아보기
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


# 집계 컴퓨팅 수행 {#performing-aggregate-computing}

이 예에서는 성에 따라 런던에 거주하는 수신자의 수를 계산하려고 합니다.

* 어떤 표를 선택해야 합니까?

   받는 사람 테이블(**nms:recipient**)

* 출력 열에서 선택해야 하는 필드는 무엇입니까?

   기본 키(카운트 포함) 및 성별

* 어떤 조건을 기준으로 필터링됩니까?

   런던에 거주하는 수신자를 기준으로

이 예를 만들려면 다음 단계를 적용합니다.

1. 에서 기본 키에 대한 카운트를 **[!UICONTROL Data to extract]**&#x200B;정의합니다(이전 예에서 보듯이). 출력 열에 필드를 **[!UICONTROL Gender]** 추가합니다. 열에서 **[!UICONTROL Group]** 옵션을 **[!UICONTROL Gender]** 선택합니다. 이렇게 하면 수신자는 성별별로 분류됩니다.

   ![](assets/query_editor_nveau_27.png)

1. 창에서 다음을 **[!UICONTROL Sorting]** 클릭합니다 **[!UICONTROL Next]**.여기에서 정렬할 필요가 없습니다.
1. 데이터 필터링을 구성합니다. 여기에서 London에 거주하는 연락처로 선택 사항을 제한할 수 있습니다.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >값은 대소문자를 구분합니다. &#39;London&#39; 값이 대문자 없이 조건에 입력되고 수신자 목록에 대문자 문자가 포함된 &quot;London&quot;이라는 단어가 포함된 경우 쿼리가 실패합니다.

1. 창에서 다음을 **[!UICONTROL Data formatting]** 클릭합니다 **[!UICONTROL Next]**.이 예에는 서식이 필요하지 않습니다.
1. 미리 보기 창에서 을 클릭합니다 **[!UICONTROL Launch data preview]**.

   성별별로 각 정렬에 대해 세 개의 개별 값이 있습니다.여성은 **** 2 **,** 남성은 1, **성은** 0이될 때. 이 예에서는 10명의 여성, 16명의 남성 및 2명의 성별을 알 수 없습니다.

   ![](assets/query_editor_agregat_04.png)
