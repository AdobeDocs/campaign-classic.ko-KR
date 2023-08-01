---
product: campaign
title: 시뮬레이션 범위
description: 시뮬레이션 범위
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: 4f6b3de2-3fdf-441d-925d-476e20e75c6f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 5%

---

# 시뮬레이션 범위{#simulation-scope}



## 범위 정의 {#definition-of-the-scope}

를 엽니다. **[!UICONTROL Scope]** 탭을 클릭하여 설정을 선택합니다.

다음 항목은 필수입니다.

* 환경 또는 오퍼 카테고리입니다.
* 오퍼 공간.
* 연락일. 연락 날짜에 적합하지 않은 오퍼는 고려되지 않습니다.
* 대상 집단.

  타겟에서 필터를 구성하지 않으면 전체 수신자 표가 고려됩니다.

* 대상당 시뮬레이션할 제안 수입니다.

  수신자는 이 많은 제안을 받게 됩니다. 예를 들어 5를 입력하면 각 수신자는 최대 5개의 오퍼 제안을 받습니다.

  ![](assets/offer_simulation_009.png)

시뮬레이션을 위해 고려할 오퍼를 세분화하기 위해 하나 이상의 테마(카테고리에 미리 지정됨)를 추가할 수 있습니다.

모든 오퍼에서 또는 온라인 오퍼에서만 시뮬레이션을 수행하도록 선택할 수도 있습니다. 원하는 경우 일부 필터를 사용하여 선택 내용을 변경할 수 있습니다.

>[!NOTE]
>
>연락 날짜를 지정해야 합니다. 이렇게 하면 상호 작용 엔진이 선택한 환경 또는 범주의 오퍼를 정렬할 수 있습니다. 구성된 날짜가 없으면 시뮬레이션에서 오류가 발생합니다.

## 보고 축 추가 {#adding-reporting-axes}

를 통해 타겟 또는 오퍼 자체에 대한 보고 축을 추가하여 시뮬레이션 분석을 향상시킬 수 있습니다. **[!UICONTROL Calculations]** 탭.

이렇게 하려면 **[!UICONTROL Add]** 버튼을 클릭하고 적절한 필드를 선택합니다. 축은 시뮬레이션을 계산하는 데 사용되며 분석 보고서에 표시됩니다. 자세한 내용은 다음을 참조하십시오. [시뮬레이션 추적](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)
