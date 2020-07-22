---
title: 증분 쿼리를 사용한 분기별 목록 업데이트
description: 이 경우 수신자 목록을 자동으로 업데이트하는 데 증분 쿼리를 사용합니다.
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: aa192d975a08246ba684940fff3d33853d7d9345
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---


# 증분 쿼리를 사용한 분기별 목록 업데이트 {#quarterly-list-update}

다음 예에서는 수신자 목록을 자동으로 업데이트하는 데 [증분 쿼리를](../../workflow/using/incremental-query.md) 사용합니다. 이러한 수신자는 계절별 마케팅 캠페인의 일부로 타깃팅됩니다.

이러한 캠페인은 관련 스포츠 활동을 제공하기 위해 매 시즌 초에 시작되므로, 이러한 목록은 분기마다 업데이트됩니다. 하지만 여기에 있는 수신자는 이 캠페인으로 9개월마다 한 번만 타깃팅되어야 합니다. 이를 통해 수신자의 자격 주기를 단축할 수 있고 수년 동안 여러 계절에 맞는 활동을 제공할 수 있습니다.

![](assets/incremental_query_example.png)

1. 새로운 워크플로우에 목록 업데이트 활동과 함께 증분 쿼리를 추가합니다.
1. 쿼리 **[!UICONTROL Incremental query]** 만들기에 지정된 활동 탭 [을 구성합니다](../../workflow/using/query.md#creating-a-query).
1. 탭을 **[!UICONTROL Scheduling & History]** 선택한 다음 270일 내역을 지정합니다. 이미 타깃팅된 수신자는 270일 동안 또는 약 9개월 동안 타깃팅되지 않습니다.

   Then click the **[!UICONTROL Change...]** button.

1. 각 시즌이 시작되기 전에 목록을 업데이트하려면 을 선택합니다 **[!UICONTROL Monthly]**.
1. 다음 화면에서 3월, 6월, 9월 및 12월을 선택합니다. 월의 20일을 선택하고 워크플로우를 실행할 시간을 선택합니다.
1. 그런 다음 질의에 대한 유효 기간을 선택합니다. 예를 들어 이 활동을 영구적으로 활성화하려면 선택합니다 **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. 증분 쿼리를 승인한 후 목록 업데이트에 설명된 대로 목록 업데이트 활동을 [구성합니다](../../workflow/using/list-update.md).

따라서 각 시즌이 시작되기 직전에 워크플로우가 자동으로 시작됩니다. 이 목록은 새로운 자격 조건을 갖춘 수신자가 오퍼를 받을 수 있도록 업데이트됩니다.
