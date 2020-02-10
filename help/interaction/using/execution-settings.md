---
title: 실행 설정
seo-title: 실행 설정
description: 실행 설정
seo-description: null
page-status-flag: never-activated
uuid: a6549091-0c33-4fe1-adde-de3b285dd456
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: simulating-offers
discoiquuid: 52b5d5a9-10dc-4601-8fe4-962a2334322b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 실행 설정{#execution-settings}

시뮬레이션을 만들 때 필요한 경우 실행 설정을 지정할 수 있습니다. 이러한 설정을 사용하면 우선 순위에 따라 활동이 낮은 시간 동안 시뮬레이션을 실행하거나 로그에 SQL 쿼리를 기록할 수 있습니다. 이 단계는 선택 사항입니다.

이러한 설정은 나중에 시뮬레이션 창의 **[!UICONTROL General]** 탭에서 변경할 수 있습니다.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** :Adobe Campaign 성과를 최적화하기 위해 선택한 우선 순위(낮음, 평균 또는 높음)를 기반으로 시뮬레이션을 예약할 수 있습니다.
* **[!UICONTROL Priority]** :시뮬레이션에 적용된 수준으로 일정을 잡습니다. 이 **[!UICONTROL Schedule execution for a time of low activity]** 옵션을 선택하면 캠페인 처리 워크플로에서 캠페인을 시작할 활동이 낮은 시간을 선택합니다.
* **[!UICONTROL Log SQL queries in the journal]** :이 기능은 전문가 사용자만을 위한 것입니다. SQL 쿼리를 표시하는 로그에 탭을 추가하여 시뮬레이션이 오류로 인해 끝날 경우 가능한 잘못된 함수를 감지할 수 있습니다.

