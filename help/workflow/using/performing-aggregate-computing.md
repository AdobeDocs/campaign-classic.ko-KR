---
product: campaign
title: 집계 컴퓨팅 수행
description: 쿼리에서 집계 컴퓨팅을 수행하는 방법을 알아봅니다
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 2%

---

# 집계 컴퓨팅 수행 {#performing-aggregate-computing}

![](../../assets/common.svg)

이 예제에서는 런던에 거주하는 수신자의 수를 성에 따라 계산하려고 합니다.

* 어떤 테이블을 선택해야 합니까?

   수신자 테이블(**nms:recipient**)

* 출력 열에서 어떤 필드를 선택해야 합니까?

   기본 키(개수 포함) 및 성별

* 필터링된 정보는 어떤 조건을 기준으로 합니까?

   런던에 사는 수신자에게서

이 예제를 만들려면 다음 단계를 적용합니다.

1. in **[!UICONTROL Data to extract]**&#x200B;을(를) 통해 기본 키의 수를 정의합니다(이전 예와 같이). 추가 **[!UICONTROL Gender]** 출력 열의 필드. 을(를) 확인합니다. **[!UICONTROL Group]** 옵션 **[!UICONTROL Gender]** 열. 이런 식으로 수신자들은 성별별로 그룹화됩니다.

   ![](assets/query_editor_nveau_27.png)

1. 에서 **[!UICONTROL Sorting]** 창 **[!UICONTROL Next]**: 여기서 정렬할 필요는 없습니다.
1. 데이터 필터링을 구성합니다. 여기서는 London에 거주하는 연락처로 선택을 제한하려고 합니다.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >값은 대/소문자를 구분합니다. 대문자 없이 조건에 &#39;London&#39; 값을 입력하고 수신자 목록에 대문자 &quot;London&quot;이라는 단어가 포함된 경우 쿼리가 실패합니다.

1. 에서 **[!UICONTROL Data formatting]** 창 **[!UICONTROL Next]**: 이 예에는 서식이 필요하지 않습니다.
1. 미리 보기 창에서 **[!UICONTROL Launch data preview]**.

   성별별로 각 정렬에 대해 세 개의 개별 값이 있습니다. **2개** 여성용 **1** 및 **0** 성별을 알 수 없는 시기 이 예제에는 10명의 여성, 16명의 남성과 2명의 성별을 알 수 없는 사람들이 포함되어 있습니다.

   ![](assets/query_editor_agregat_04.png)
