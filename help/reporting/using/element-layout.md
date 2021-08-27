---
product: campaign
title: 요소 레이아웃
description: 요소 레이아웃
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: 79d5c901-905b-4a0e-adb9-91fd6acb186f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 1%

---

# 요소 레이아웃{#element-layout}

![](../../assets/common.svg)

여기에 자세히 설명된 다양한 차트 외에도 [차트 유형과 변형](../../reporting/using/creating-a-chart.md#chart-types-and-variants) 표시를 조정하고 보고서 페이지에 요소를 추가할 수 있습니다.

컨테이너를 사용할 수 있습니다. 이렇게 하면 페이지의 여러 요소를 연결하고 레이아웃을 열 및/또는 셀로 구성할 수 있습니다. 사용 방법은 [이 섹션](../../web/using/defining-web-forms-layout.md#creating-containers)에 자세히 설명되어 있습니다.

트리 루트에서 보고서 레이아웃을 구성하고 각 컨테이너에 대해 오버로드를 수행할 수 있습니다. 페이지는 열로 정렬됩니다. 컨테이너도 열로 정렬됩니다. 정적 항목과 그래픽 항목만 셀로 정렬됩니다.

## 각 페이지에 대한 옵션 정의 {#defining-the-options-for-each-page}

보고서의 각 페이지에서 옵션을 사용할 수 있습니다.

**[!UICONTROL General]** 탭에서는 페이지의 제목을 변경하고, 범례 위치를 구성하고, 보고서 페이지 간을 탐색할 수 있습니다.

![](assets/s_ncs_advuser_report_wizard_022.png)

**[!UICONTROL Title]** 필드를 사용하면 보고서 페이지의 헤더에 있는 레이블을 개인화할 수 있습니다. 창의 제목은 보고서의 **[!UICONTROL Properties]** 창을 통해 구성할 수 있습니다. 자세한 내용은 [머리글 및 바닥글 추가](#adding-a-header-and-a-footer)를 참조하십시오.

**[!UICONTROL Display settings]** 옵션을 사용하면 보고서 페이지에서 컨트롤 캡션의 위치를 선택하고 페이지에 있는 열 수를 정의할 수 있습니다. 페이지 레이아웃에 대한 자세한 정보는 [이 섹션](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page)의 **항목 레이아웃** 섹션을 참조하십시오.

**[!UICONTROL Browse]** 섹션에서 다양한 옵션을 선택하여 한 보고서 페이지에서 다른 보고서 페이지로 브라우징을 인증합니다. **[!UICONTROL Disable next page]** 또는 **[!UICONTROL Disable previous page]** 옵션이 선택된 경우 **[!UICONTROL Next]** 및 **[!UICONTROL Previous]** 단추가 보고서 페이지에서 사라집니다.

## 머리글 및 바닥글 추가 {#adding-a-header-and-a-footer}

보고서 속성 창에서 다음과 같은 레이아웃 요소를 정의할 수도 있습니다. 창의 제목, 머리글과 바닥글의 HTML 콘텐츠입니다.

속성 창에 액세스하려면 보고서의 **[!UICONTROL Properties]** 버튼을 클릭합니다.

![](assets/reporting_properties.png)

**[!UICONTROL Page]** 탭을 사용하여 디스플레이를 개인화할 수 있습니다.

![](assets/s_ncs_advuser_report_properties_04.png)

이 탭에 구성된 컨텐츠는 모든 보고서 페이지에 표시됩니다.

**[!UICONTROL Texts]** 하위 탭을 사용하여 변수 컨텐츠를 정의할 수 있습니다. 보고서가 여러 언어로 사용하도록 설계된 경우 번역 주기 중에 고려됩니다.

이렇게 하면 텍스트 조각 목록을 만들고 식별자에 연결할 수 있습니다.

![](assets/s_ncs_advuser_report_properties_04a.png)

그런 다음 이러한 식별자를 보고서의 HTML 콘텐츠에 삽입합니다.

![](assets/s_ncs_advuser_report_properties_04b.png)

보고서가 표시될 때 해당 콘텐츠로 자동 교체됩니다.

HTML 텍스트와 마찬가지로, 이 운영 모드에서는 보고서에 사용된 텍스트를 중앙 집중화하고 번역을 관리할 수 있습니다. 이 탭에서 만든 텍스트는 Adobe Campaign 통합 번역 도구에 의해 자동으로 수집됩니다.
