---
product: campaign
title: 실행 설정
description: 실행 설정
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---

# 실행 설정{#execution-settings}



시뮬레이션을 만들 때 필요한 경우 실행 설정을 지정할 수 있습니다. 이러한 설정을 사용하면 우선 순위에 따라 활동이 적은 시간에 시뮬레이션을 실행하거나 로그에 SQL 쿼리를 기록할 수 있습니다. 이 단계는 선택 사항입니다.

이러한 설정은 의 뒷부분에서 변경할 수 있습니다. **[!UICONTROL General]** 시뮬레이션 창의 탭.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** : Adobe Campaign 성능을 최적화하기 위해 선택한 우선 순위(낮음, 평균 또는 높음)를 기반으로 시뮬레이션을 예약할 수 있습니다.
* **[!UICONTROL Priority]** : 시뮬레이션을 예약하기 위해 시뮬레이션에 적용되는 레벨입니다. 다음의 경우 **[!UICONTROL Schedule execution for a time of low activity]** 옵션을 선택하면 캠페인 처리 워크플로우가 활동이 적은 시간을 선택하여 캠페인을 시작합니다.
* **[!UICONTROL Log SQL queries in the journal]** : 이 기능은 전문가 사용자만을 위한 것입니다. 이 옵션을 사용하면 SQL 쿼리를 표시하는 로그에 탭을 추가하여 시뮬레이션이 오류와 함께 완료될 경우 가능한 오작동을 감지할 수 있습니다.
