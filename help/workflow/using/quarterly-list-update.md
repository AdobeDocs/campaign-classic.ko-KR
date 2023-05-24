---
product: campaign
title: 증분 쿼리를 사용한 분기별 목록 업데이트
description: 이 사용 사례에서는 수신자 목록을 자동으로 업데이트하는 데 증분 쿼리를 사용합니다
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 0d3e7046-313a-42a6-9155-3365e8d60bac
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 5%

---

# 증분 쿼리를 사용한 분기별 목록 업데이트 {#quarterly-list-update}



다음 예제에서는 [증분 쿼리](incremental-query.md) 수신자 목록을 자동으로 업데이트하는 데 사용됩니다. 이러한 수신자는 시즌 마케팅 캠페인의 일부로 타겟팅됩니다.

이러한 캠페인은 매 시즌이 시작될 때 관련 스포츠 활동을 제공하기 위해 시작되므로, 이러한 목록은 분기마다 업데이트됩니다. 단, 여기에서 수신자는 이 캠페인에 의해 9개월에 한 번만 타겟팅되어야 합니다. 이를 통해 수신자의 자격 빈도를 확장하고 년 간 다양한 시즌에 대한 활동을 제공할 수 있습니다.

![](assets/incremental_query_example.png)

1. 증분 쿼리와 목록 업데이트 활동을 새 워크플로우에 추가합니다.
1. 구성 **[!UICONTROL Incremental query]** 에 지정된 활동의 탭 [쿼리 만들기](query.md#creating-a-query).
1. 다음 항목 선택 **[!UICONTROL Scheduling & History]** 을 탭한 다음 270일 내역을 지정합니다. 이미 타겟팅된 수신자는 270일 또는 약 9개월 동안 더 이상 타겟팅되지 않습니다.

   그런 다음 **[!UICONTROL Change...]** 단추를 클릭합니다.

1. 각 시즌이 시작되기 전에 목록이 업데이트되도록 하려면 다음을 선택합니다. **[!UICONTROL Monthly]**.
1. 다음 화면에서 3월, 6월, 9월 및 12월을 선택합니다. 월의 20일을 선택하고 워크플로우를 시작할 시간을 선택합니다.
1. 그런 다음 질의에 대한 유효 기간을 선택합니다. 예를 들어 이 활동을 영구적으로 활성화하려면 을 선택합니다. **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. 증분 쿼리를 승인한 후에서 설명한 대로 목록 업데이트 활동을 구성합니다 [목록 업데이트](list-update.md).

따라서 워크플로우는 각 시즌이 시작되기 바로 전에 자동으로 시작됩니다. 이 목록은 오퍼를 받을 수 있는 신규 수신자로 업데이트됩니다.
