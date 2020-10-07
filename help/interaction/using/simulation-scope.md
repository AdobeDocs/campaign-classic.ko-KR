---
title: 시뮬레이션 범위
seo-title: 시뮬레이션 범위
description: 시뮬레이션 범위
seo-description: null
page-status-flag: never-activated
uuid: d3145926-0a7e-455f-9b93-55be1b2a0518
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: simulating-offers
discoiquuid: ef658468-e20b-45d9-a714-c152e55c1c79
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 3%

---


# 시뮬레이션 범위{#simulation-scope}

## 범위 정의 {#definition-of-the-scope}

탭을 열어 설정을 선택합니다 **[!UICONTROL Scope]** .

다음 항목은 필수입니다.

* 환경 또는 오퍼 카테고리
* 공간을 제공합니다.
* 연락처 날짜. 연락처 날짜에 적합하지 않은 오퍼는 고려되지 않습니다.
* Target.

   대상에 필터를 구성하지 않으면 전체 수신자 테이블이 고려됩니다.

* 대상당 시뮬레이션할 제안 수입니다.

   수령인은 이 많은 제안을 받을 것이다. 예를 들어 5를 입력하면 각 수신자는 최대 5개의 오퍼 제안을 받게 됩니다.

   ![](assets/offer_simulation_009.png)

시뮬레이션에 사용할 오퍼를 세분화하려면 하나 또는 여러 개의 테마(카테고리에 미리 지정됨)를 추가할 수 있습니다.

또한 모든 오퍼에 대해 시뮬레이션을 수행하거나 온라인 오퍼에 대해서만 실행할 수 있습니다. 원하는 경우 일부 필터를 사용하여 선택 영역을 변경할 수 있습니다.

>[!NOTE]
>
>연락처 날짜를 지정해야 합니다. 이렇게 하면 상호 작용 엔진이 선택한 환경 또는 카테고리의 오퍼를 정렬할 수 있습니다. 날짜가 구성되지 않으면 시뮬레이션에서 오류가 발생합니다.

## 보고 축 추가 {#adding-reporting-axes}

타겟 또는 **[!UICONTROL Calculations]** 탭을 통해 오퍼에 보고 축을 추가하여 시뮬레이션 분석을 향상시킬 수 있습니다.

이렇게 하려면 **[!UICONTROL Add]** 단추를 클릭하고 적절한 필드를 선택합니다. 시뮬레이션을 계산하는 데 축이 사용되며 분석 보고서에 표시됩니다. For more on this, refer to [Simulation tracking](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)

