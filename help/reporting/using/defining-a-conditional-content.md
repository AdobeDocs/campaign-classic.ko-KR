---
solution: Campaign Classic
product: campaign
title: 조건부 콘텐츠 정의
description: 조건부 콘텐츠 정의
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 8%

---


# 조건부 콘텐츠 정의{#defining-a-conditional-content}

특정 보고서 항목 또는 페이지의 표시를 조건화할 수 있습니다.

특정 항목을 조건부 항목으로 만들려면 가시성 설정을 조정합니다. 자세한 내용은 [에어컨 항목 표시](#conditioning-item-display)를 참조하십시오.

하나 이상의 페이지를 조건부 표시하려면 **[!UICONTROL Test]** 유형 활동을 사용하십시오. 자세한 내용은 [Conditioning page display](#conditioning-page-display)을 참조하십시오.

## 조절 항목 표시 {#conditioning-item-display}

보고서 일부를 조건부 표시로 만들려면 가시성 조건을 정의해야 합니다.이러한 항목이 충족되지 않으면 항목이 표시되지 않습니다.

가시성 조건은 연산자 상태에 따라 보고서 페이지에서 선택하거나 입력한 항목에 따라 달라질 수 있습니다.

페이지에 있는 항목의 조건부 표시를 보여주는 예는 [이 섹션](../../web/using/form-rendering.md#defining-fields-conditional-display)에 있습니다.

다음 예에서 표시 조건은 언어에 따라 달라집니다.

![](assets/reporting_display_condition.png)

## 조절 페이지 표시 {#conditioning-page-display}

보고서 차트에서 **[!UICONTROL Test]** 활동을 사용하면 하나 이상의 조건에 따라 페이지 시퀀스를 변경할 수 있습니다.

이 활동은 다음과 같은 운영 원칙을 기반으로 합니다.

1. 차트에 **[!UICONTROL Test]**&#x200B;을 놓고 편집합니다.
1. **[!UICONTROL Add]** 단추를 클릭하여 가능한 다양한 사례를 만듭니다.

   ![](assets/reporting_test_sample.png)

   각 경우에 대해 출력 전환이 **[!UICONTROL Test]** 활동에 추가됩니다.

   ![](assets/reporting_test_transitions.png)

1. 구성된 조건 중 하나가 충족되지 않는 경우 전환을 추가하려면 **[!UICONTROL Enable default transition]**&#x200B;을 선택합니다.

   이 작업에 대한 자세한 정보는 [이 섹션](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)을 참조하십시오.

**[!UICONTROL Test]** 활동은 차트의 시작 부분에 배치하여 컨텍스트 또는 연산자 프로필에 따라 디스플레이를 조건으로 지정할 수 있습니다.
