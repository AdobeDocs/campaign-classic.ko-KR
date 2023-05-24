---
product: campaign
title: 집계 컴퓨팅 수행
description: 쿼리에서 집계 컴퓨팅을 수행하는 방법에 대해 알아봅니다
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 2%

---

# 집계 컴퓨팅 수행 {#performing-aggregate-computing}



이 예제에서는 성별에 따라 런던에 거주하는 수신자 수를 세려고 합니다.

* 어떤 테이블을 선택해야 합니까?

   수신자 테이블 (**nms:recipient**)

* 출력 열에서 어떤 필드를 선택해야 합니까?

   기본 키(개수 포함) 및 성별

* 필터링된 정보는 어떤 조건을 기반으로 합니까?

   London에 거주하는 수신자 기준

이 예제를 만들려면 다음 단계를 적용합니다.

1. 위치 **[!UICONTROL Data to extract]**&#x200B;는 이전 예제와 같이 기본 키의 개수를 정의합니다. 추가 **[!UICONTROL Gender]** 출력 열의 필드. 다음 확인: **[!UICONTROL Group]** 의 옵션 **[!UICONTROL Gender]** 열. 이렇게 하면 수신자를 성별에 따라 그룹화합니다.

   ![](assets/query_editor_nveau_27.png)

1. 다음에서 **[!UICONTROL Sorting]** 창에서 다음을 클릭: **[!UICONTROL Next]**: 여기에서 정렬할 필요가 없습니다.
1. 데이터 필터링을 구성합니다. 여기서는 런던에 거주하는 연락처로 선택을 제한합니다.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >값은 대/소문자를 구분합니다. 대문자가 없는 조건에 &#39;London&#39; 값을 입력하고 수신자 목록에 대문자가 있는 단어 &quot;London&quot;이 포함된 경우 쿼리가 실패합니다.

1. 다음에서 **[!UICONTROL Data formatting]** 창에서 다음을 클릭: **[!UICONTROL Next]**: 이 예제에서는 형식이 필요하지 않습니다.
1. 미리보기 창에서 다음을 클릭합니다. **[!UICONTROL Launch data preview]**.

   성별로 정렬되는 값에는 세 가지가 있습니다. **2** 여성용으로는, **1** 남성용 및 **0** 성별을 알 수 없는 경우. 이 예에서는 여성 10명, 남성 16명, 성별이 알려지지 않은 2명의 명단이 포함되어 있다.

   ![](assets/query_editor_agregat_04.png)
