---
product: campaign
title: 조건부 콘텐츠 정의
description: 조건부 콘텐츠 정의
feature: Reporting
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 8%

---

# 조건부 콘텐츠 정의{#defining-a-conditional-content}

![](../../assets/common.svg)

특정 보고서 항목 또는 페이지 표시를 조건화할 수 있습니다.

특정 항목을 조건부 항목으로 만들려면 가시성 설정을 조정하십시오. 자세한 내용은 [조건 항목 표시](#conditioning-item-display).

하나 이상의 페이지를 조건부 표시하려면 **[!UICONTROL Test]** 유형 활동. 자세한 내용은 [조건 페이지 표시](#conditioning-page-display).

## 조건 항목 표시 {#conditioning-item-display}

보고서 일부 조건부 표시를 만들려면 가시성 조건을 정의해야 합니다. 이러한 항목이 충족되지 않으면 항목이 표시되지 않습니다.

가시성 조건은 운영자 상태, 보고서 페이지에서 선택하거나 입력한 항목에 따라 달라질 수 있습니다.

페이지에 있는 항목의 조건부 표시를 보여주는 예는 다음과 같습니다. [이 섹션](../../web/using/form-rendering.md#defining-fields-conditional-display).

다음 예에서 표시 조건은 언어에 따라 다릅니다.

![](assets/reporting_display_condition.png)

## 조건 페이지 표시 {#conditioning-page-display}

보고서 차트에서 **[!UICONTROL Test]** 활동을 사용하면 하나 이상의 조건에 따라 페이지 시퀀스를 변경할 수 있습니다.

이 활동은 다음과 같은 운영 원칙을 기반으로 합니다.

1. 배치 **[!UICONTROL Test]** 차트에서 편집하고 편집합니다.
1. 을(를) 클릭합니다. **[!UICONTROL Add]** 가능한 여러 사례를 만드는 단추입니다.

   ![](assets/reporting_test_sample.png)

   각 경우에 대해 출력 전환이 **[!UICONTROL Test]** 활동.

   ![](assets/reporting_test_transitions.png)

1. 을(를) 선택합니다 **[!UICONTROL Enable default transition]** 전환을 추가하려면 구성된 조건 중 하나가 충족되지 않는 경우 선택합니다.

   이 작업에 대한 자세한 정보는 [이 섹션](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)을 참조하십시오.

A **[!UICONTROL Test]** 활동은 차트의 시작 부분에 배치하여 예를 들어 컨텍스트 또는 운영자 프로필에 따라 표시를 조건으로 지정할 수 있습니다.
