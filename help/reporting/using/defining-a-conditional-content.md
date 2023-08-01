---
product: campaign
title: 조건부 콘텐츠 정의
description: 조건부 콘텐츠 정의
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Reporting, Monitoring
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 8%

---

# 조건부 콘텐츠 정의{#defining-a-conditional-content}



특정 보고서 항목 또는 페이지의 표시를 조정할 수 있습니다.

특정 항목을 조건부로 만들려면 표시 설정을 조정합니다. 자세한 내용은 다음을 참조하십시오. [조건 항목 표시](#conditioning-item-display).

하나 이상의 페이지 표시를 조건부로 하려면 **[!UICONTROL Test]** 활동을 입력합니다. 자세한 내용은 다음을 참조하십시오. [조건 페이지 표시](#conditioning-page-display).

## 조건 항목 표시 {#conditioning-item-display}

보고서 일부를 조건부로 표시하려면 가시성 조건을 정의해야 합니다. 이러한 조건이 충족되지 않으면 항목이 표시되지 않습니다.

가시성 조건은 운영자 상태, 보고서 페이지에서 선택하거나 입력한 항목에 따라 달라질 수 있습니다.

페이지에 있는 항목의 조건부 표시를 보여 주는 예제는에 나와 있습니다 [이 섹션](../../web/using/form-rendering.md#defining-fields-conditional-display).

다음 예에서 표시 조건은 언어에 따라 다릅니다.

![](assets/reporting_display_condition.png)

## 조건 페이지 표시 {#conditioning-page-display}

보고서 차트에서 **[!UICONTROL Test]** 활동을 사용하면 하나 이상의 조건에 따라 페이지 순서를 변경할 수 있습니다.

이 활동은 다음 운영 원칙을 기반으로 합니다.

1. 배치 **[!UICONTROL Test]** 차트에서 만들고 편집합니다.
1. 다음을 클릭합니다. **[!UICONTROL Add]** 단추를 클릭하여 가능한 다양한 사례를 만듭니다.

   ![](assets/reporting_test_sample.png)

   각 경우에 대해 출력 전환이 **[!UICONTROL Test]** 활동.

   ![](assets/reporting_test_transitions.png)

1. 다음 항목 선택 **[!UICONTROL Enable default transition]** 구성된 조건 중 하나가 충족되지 않는 경우 전환을 추가합니다.

   이 작업에 대한 자세한 정보는 [이 섹션](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)을 참조하십시오.

A **[!UICONTROL Test]** 활동은 차트 시작 부분에 배치하여 컨텍스트 또는 연산자 프로필에 따라 표시를 조정할 수 있습니다.
