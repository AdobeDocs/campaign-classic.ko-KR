---
solution: Campaign Classic
product: campaign
title: 증분 쿼리를 사용한 분기별 목록 업데이트
description: 이 경우 수신자 목록을 자동으로 업데이트하는 데 증분 쿼리가 사용됩니다.
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 5%

---


# 증분 쿼리를 사용한 분기별 목록 업데이트 {#quarterly-list-update}

다음 예에서 [증분 쿼리](../../workflow/using/incremental-query.md)는 수신자 목록을 자동으로 업데이트하는 데 사용됩니다. 이러한 수신자는 계절별 마케팅 캠페인의 일부로 타깃팅됩니다.

이러한 캠페인은 관련 스포츠 활동을 제공하기 위해 매 시즌 초에 시작되므로, 이러한 목록은 분기마다 업데이트됩니다. 하지만 여기에서 수신자는 이 캠페인으로 9개월마다 한 번만 타깃팅되어야 합니다. 이 기능을 사용하면 수신자의 자격 주기를 단축할 수 있고 수년 동안 여러 계절에 맞는 활동을 제공할 수 있습니다.

![](assets/incremental_query_example.png)

1. 새 워크플로우에 증분 쿼리와 목록 업데이트 활동을 추가합니다.
1. [쿼리](../../workflow/using/query.md#creating-a-query)에 지정된 대로 활동의 **[!UICONTROL Incremental query]** 탭을 구성합니다.
1. **[!UICONTROL Scheduling & History]** 탭을 선택한 다음 270일 내역을 지정합니다. 이미 타깃팅된 수신자는 더 이상 270일 또는 약 9개월 동안 타깃팅되지 않습니다.

   그런 다음 **[!UICONTROL Change...]** 단추를 클릭합니다.

1. 각 시즌이 시작되기 전에 목록을 업데이트하려면 **[!UICONTROL Monthly]**&#x200B;을 선택합니다.
1. 다음 화면에서 3월, 6월, 9월 및 12월을 선택합니다. 해당 월의 20일을 선택하고 Workflow를 실행할 시간을 선택합니다.
1. 그런 다음 쿼리의 유효 기간을 선택합니다. 예를 들어 이 활동을 영구적으로 활성화하려면 **[!UICONTROL Permanent validity]**&#x200B;을 선택합니다.

   ![](assets/incremental_query_example_2.png)

1. 증분 쿼리를 승인한 후 [목록 업데이트](../../workflow/using/list-update.md)에 설명된 대로 목록 업데이트 활동을 구성합니다.

따라서 각 계절의 시작 바로 전에 워크플로우가 자동으로 시작됩니다. 오퍼를 수신할 자격이 있는 새 수신자로 목록이 업데이트됩니다.
