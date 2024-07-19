---
product: campaign
title: 표시기 만들기
description: 표시기 만들기
feature: Reporting, Monitoring
hide: true
hidefromtoc: true
exl-id: e4806bb8-de9d-47e4-8b37-d6c0565b7f5a
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 2%

---

# 표시기 만들기{#creating-indicators}



큐브가 작동하도록 하려면 관련 차원과 측정 단위를 식별하고 큐브에 만들어야 합니다.

큐브를 생성하려면 다음 단계를 적용합니다.

1. 작업 테이블을 선택합니다. [작업 테이블 선택](#selecting-the-work-table)을 참조하세요.
1. 차원을 정의합니다. [차원 정의](#defining-dimensions)를 참조하세요.
1. 측정값을 정의합니다. [지표 작성](#building-indicators)을 참조하세요.
1. 집계 만들기(선택 사항). [집계 계산 및 사용](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates)을 참조하세요.

이 예에서는 보고서에서 간단한 큐브를 빠르게 생성하여 해당 측정 단위를 내보내는 방법을 보여 줍니다.

구현 단계는 아래에 자세히 설명되어 있습니다. 이 장의 다른 섹션에서는 전체 옵션 및 설명을 사용할 수 있습니다.

## 작업 테이블 선택 {#selecting-the-work-table}

큐브를 만들려면 큐브 목록 위에 있는 **[!UICONTROL New]** 단추를 클릭합니다.

![](assets/s_advuser_cube_create.png)

팩트 스키마(즉, 탐색할 요소가 포함된 스키마)를 선택합니다. 이 예제에서는 **Recipient** 테이블을 선택합니다.

![](assets/s_advuser_cube_wz_02.png)

큐브를 만들려면 **[!UICONTROL Save]**&#x200B;을(를) 클릭하십시오. 큐브는 큐브 목록에 나타나고 적절한 탭을 사용하여 구성할 수 있습니다.

**[!UICONTROL Filter the source data...]** 링크를 클릭하여 이 큐브의 계산을 데이터베이스의 선택된 데이터에 적용합니다.

![](assets/s_advuser_cube_wz_03.png)

## 차원 정의 {#defining-dimensions}

Dimension은 관련 팩트 스키마를 기반으로 각 큐브에 대해 정의된 분석 축과 일치합니다. 시간(연도, 월, 날짜 등), 제품 또는 계약의 분류(가족, 참조 등), 인구 세그먼트(도시, 연령 그룹, 상태 등)와 같이 분석에서 탐색한 차원입니다.

이 분석 축은 큐브의 **[!UICONTROL Dimension]** 탭에서 정의됩니다.

**[!UICONTROL Add]** 단추를 클릭하여 새 차원을 만든 다음 **[!UICONTROL Expression field]**&#x200B;에서 **[!UICONTROL Edit expression]** 아이콘을 클릭하여 관련 데이터가 포함된 필드를 선택합니다.

![](assets/s_advuser_cube_wz_04.png)

* 받는 사람 **나이**&#x200B;을(를) 선택하여 시작합니다. 이 필드의 경우, 나이를 그룹화하고 정보를 더 쉽게 읽을 수 있도록 비닝을 정의할 수 있습니다. 여러 개의 별도 값이 있을 가능성이 있는 경우 비닝을 사용하는 것이 좋습니다.

  이렇게 하려면 **[!UICONTROL Enable binning]** 옵션을 선택하십시오. 빈 모드는 [데이터 빈](../../reporting/using/concepts-and-methodology.md#data-binning)에 자세히 설명되어 있습니다.

  ![](assets/s_advuser_cube_wz_05.png)

* **날짜** 유형 차원을 추가합니다. 여기에서는 수신자 프로필 생성 날짜를 표시하려고 합니다

  이렇게 하려면 **[!UICONTROL Add]**&#x200B;을(를) 클릭하고 받는 사람 테이블에서 **[!UICONTROL Creation date]** 필드를 선택합니다.

  ![](assets/s_advuser_cube_wz_06.png)

  날짜 표시 모드를 선택할 수 있습니다. 이렇게 하려면 사용할 계층과 생성할 레벨을 선택합니다.

  ![](assets/s_advuser_cube_wz_07.png)

  이 예제에서는 주, 학기/월을 동시에 사용할 수 없으므로 연도, 월, 일만 표시하려고 합니다. 이러한 수준은 호환되지 않습니다.

* 수신자의 도시를 기준으로 데이터를 분석할 다른 차원을 만듭니다

  이렇게 하려면 새 차원을 추가하고 수신자 스키마의 **[!UICONTROL Location]** 노드에서 도시를 선택합니다.

  ![](assets/s_advuser_cube_wz_08.png)

  비닝을 활성화하면 정보를 더 쉽게 읽고 값을 열거에 연결할 수 있습니다.

  ![](assets/s_advuser_cube_wz_09.png)

  드롭다운 목록에서 열거형을 선택합니다

  ![](assets/s_advuser_cube_wz_10.png)

  열거형의 값만 표시됩니다. 다른 항목은 **[!UICONTROL Label of the other values]** 필드에 정의된 레이블 아래에 그룹화됩니다.

  자세한 내용은 [동적으로 빈 관리](../../reporting/using/concepts-and-methodology.md#dynamically-managing-bins)를 참조하세요.

## 지표 작성 {#building-indicators}

차원이 정의되면 셀에 표시할 값에 대한 계산 모드를 지정해야 합니다. 이렇게 하려면 **[!UICONTROL Measures]** 탭에서 일치하는 지표를 만듭니다. 큐브를 사용할 보고서에 표시할 열이 있는 수만큼 측정값을 만듭니다.

그렇게 하려면 다음 단계를 적용합니다.

1. **[!UICONTROL Add]** 버튼을 클릭합니다.
1. 적용할 측정 유형과 공식을 선택합니다. 여기에서는 수령자 중 여성의 수를 세고자 한다.

   이 측정은 팩트 스키마를 기반으로 하며 **[!UICONTROL Count]** 연산자를 사용합니다.

   ![](assets/s_advuser_cube_wz_11.png)

   **[!UICONTROL Filter the measure data...]** 링크를 사용하면 여성만 선택할 수 있습니다. 측정값 정의 및 사용 가능한 옵션에 대한 자세한 내용은 [측정값 정의](../../reporting/using/concepts-and-methodology.md#defining-measures)를 참조하십시오.

   ![](assets/s_advuser_cube_wz_12.png)

1. 측정값의 레이블을 입력하고 저장합니다.

   ![](assets/s_advuser_cube_wz_13.png)

1. 큐브를 저장합니다.

## 큐브를 기반으로 보고서 만들기 {#creating-a-report-based-on-a-cube}

큐브가 구성되면 새 보고서를 만들기 위한 템플릿으로 사용할 수 있습니다.

방법은 다음과 같습니다.

1. **[!UICONTROL Reports]** 탭의 **[!UICONTROL Create]** 단추를 클릭하고 방금 만든 큐브를 선택합니다.

   ![](assets/s_advuser_cube_wz_14.png)

1. 확인하려면 **[!UICONTROL Create]** 단추를 클릭하세요. 이렇게 하면 보고서 구성 및 보기 페이지로 이동합니다.

   기본적으로 처음 사용 가능한 두 차원은 행과 열로 제공되지만 값은 테이블에 표시되지 않습니다. 테이블을 생성하려면 기본 아이콘을 누릅니다.

   ![](assets/s_advuser_cube_wz_15.png)

1. 차원의 축을 전환하고, 삭제하고, 새 측정값을 추가하는 등의 작업을 수행할 수 있습니다. 가능한 작업은 [이 페이지](../../reporting/using/using-cubes-to-explore-data.md)에 자세히 설명되어 있습니다.

   이렇게 하려면 적절한 아이콘을 사용합니다.

   ![](assets/s_advuser_cube_wz_16.png)
