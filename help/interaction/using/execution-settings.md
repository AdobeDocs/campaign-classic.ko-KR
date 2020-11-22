---
solution: Campaign Classic
product: campaign
title: 실행 설정
description: 실행 설정
audience: interaction
content-type: reference
topic-tags: simulating-offers
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---


# 실행 설정{#execution-settings}

시뮬레이션을 만들 때 필요한 경우 실행 설정을 지정할 수 있습니다. 이러한 설정을 사용하면 우선 순위에 따라 활동이 낮은 시간 동안 시뮬레이션을 실행하거나 로그에 SQL 쿼리를 기록할 수 있습니다. 이 단계는 선택 사항입니다.

이러한 설정은 나중에 시뮬레이션 창의 **[!UICONTROL General]** 탭에서 변경할 수 있습니다.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** :adobe campaign 성능을 최적화하기 위해 선택한 우선 순위(낮음, 평균 또는 높음)를 기반으로 시뮬레이션을 예약할 수 있습니다.
* **[!UICONTROL Priority]** :시뮬레이션에 적용되는 수준으로 일정을 잡습니다. 이 **[!UICONTROL Schedule execution for a time of low activity]** 옵션이 선택되어 있으면 캠페인 처리 워크플로우에서 캠페인을 시작할 활동이 낮은 시간을 선택합니다.
* **[!UICONTROL Log SQL queries in the journal]** :이 기능은 전문가 사용자에게만 제공됩니다. SQL 쿼리를 표시하는 로그에 탭을 추가하여 시뮬레이션이 오류와 함께 끝나면 가능한 잘못된 함수를 감지할 수 있습니다.

