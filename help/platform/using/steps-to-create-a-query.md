---
title: 쿼리를 만드는 단계
seo-title: 쿼리를 만드는 단계
description: 쿼리를 만드는 단계
seo-description: null
page-status-flag: never-activated
uuid: 9668f49c-2da7-42c8-8728-8d644c787935
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: creating-queries
discoiquuid: d538f489-f1ae-4682-9c21-d0300bd42b26
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 3%

---


# 쿼리를 만드는 단계{#steps-to-create-a-query}

Adobe Campaign에서 쿼리를 작성하는 단계는 다음과 같습니다.

1. 작업 테이블을 선택합니다. 1단계 [- 테이블 선택을 참조하십시오](#step-1---choose-a-table).
1. 추출할 데이터를 선택합니다. 2단계 [- 추출할 데이터 선택을 참조하십시오](#step-2---choose-data-to-extract).
1. 데이터 정렬 순서를 정의합니다. 3단계 [- 데이터 정렬을 참조하십시오](#step-3---sort-data).
1. 데이터를 필터링합니다. 4단계 - [데이터 필터링을 참조하십시오](#step-4---filter-data).
1. 데이터 형식을 지정합니다. 5단계 [- 데이터 형식을 참조하십시오](#step-5---format-data).
1. 결과를 표시합니다. 6단계 [- 데이터 미리 보기를 참조하십시오](#step-6---preview-data).

>[!NOTE]
>
>이러한 모든 단계는 일반 쿼리 편집기에서 사용할 수 있습니다. 쿼리가 다른 컨텍스트에서 작성되면 일부 단계를 제외할 수 있습니다.\
>쿼리 활동은 [이 섹션에 표시됩니다](../../workflow/using/query.md).

## 1단계 - 테이블 선택 {#step-1---choose-a-table}

창에서 쿼리할 데이터가 들어 있는 테이블을 **[!UICONTROL Document type]** 선택합니다. 필요한 경우 필터 필드 또는 **[!UICONTROL Filters]** 단추를 사용하여 데이터를 필터링합니다.

![](assets/query_editor_nveau_21.png)

## 2단계 - 추출할 데이터 선택 {#step-2---choose-data-to-extract}

창에서 **[!UICONTROL Data to extract]** 표시할 데이터를 선택합니다.이러한 필드는 출력 열을 구성합니다.

예를 들어, select **[!UICONTROL Age]**, **[!UICONTROL Primary key]****[!UICONTROL Email domain]** , and **[!UICONTROL City]**&#x200B;를 선택합니다. 결과는 이 선택에 따라 구성됩니다. 창 오른쪽의 파란색 화살표를 사용하여 열 순서를 변경합니다.

![](assets/query_editor_nveau_01.png)

공식을 식에 삽입하거나 집계 함수에서 프로세스를 실행하여 표현식을 편집할 수 있습니다. 이렇게 하려면 열 **[!UICONTROL Expression]** 필드를 클릭한 다음 선택합니다 **[!UICONTROL Edit expression]**.

![](assets/query_editor_nveau_97.png)

출력 열 데이터를 그룹화할 수 있습니다.이렇게 하려면 창 **[!UICONTROL Yes]** 의 **[!UICONTROL Group]** 열을 **[!UICONTROL Data to extract]** 확인하십시오. 이 함수는 선택한 그룹화 축 주위에 결과를 생성합니다. 그룹화가 있는 쿼리의 예는 [이 섹션에서 사용할 수 있습니다](../../workflow/using/querying-delivery-information.md).

![](assets/query_editor_nveau_56.png)

* 이 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 함수를 사용하면 &quot;그룹화 기준&quot;을 지정하고 그룹화된(&quot;having&quot;)을 선택할 수 있습니다. 이 함수는 출력 열의 모든 필드에 적용됩니다. 예를 들어 이 옵션을 사용하면 출력 열의 모든 선택 사항을 그룹화하고 35에서 50까지의 수신자와 같은 특정 유형의 정보를 복구할 수 있습니다.

   이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/querying-using-grouping-management.md)을 참조하십시오.

* 이 **[!UICONTROL Remove duplicate rows (DISTINCT)]** 함수를 사용하면 출력 열에서 얻은 동일한 결과를 중복 제거할 수 있습니다. 예를 들어 출력 열에서 성, 이름 및 이메일 필드를 선택하여 인구 조사를 수행하는 경우 동일한 데이터가 있는 필드는 데이터베이스에 여러 번 입력되었음을 의미하므로 해당 정보가 동일한 대상이 제거됩니다.오직 한 가지 결과만이 고려될 것이다.

## 3단계 - 데이터 정렬 {#step-3---sort-data}

창 **[!UICONTROL Sorting]** 을 사용하면 열 컨텐츠를 정렬할 수 있습니다. 화살표를 사용하여 열 순서를 변경합니다.

* 이 열을 사용하면 **[!UICONTROL Sorting]** 열 내용을 간단하게 정렬하고 A에서 Z까지 또는 오름차순으로 정렬할 수 있습니다.
* 컨텐츠는 Z부터 A까지 정렬되며 내림차순으로 정렬합니다. **[!UICONTROL Descending sort]** 레코드 매출을 볼 때 다음과 같이 유용합니다.목록의 맨 위에 가장 높은 숫자가 표시됩니다.

이 예에서 데이터는 수신자의 연령에 따라 오름차순으로 정렬됩니다.

![](assets/query_editor_nveau_57.png)

## 4단계 - 데이터 필터링 {#step-4---filter-data}

쿼리 편집기를 사용하면 데이터를 필터링하여 검색을 세분화할 수 있습니다.

제공되는 필터는 쿼리가 관련된 테이블에 따라 다릅니다.

![](assets/query_editor_nveau_09.png)

섹션을 선택하면 **[!UICONTROL Filtering conditions]** 다음 섹션에 액세스할 수 **[!UICONTROL Target elements]** 있습니다.이렇게 하면 수집할 데이터를 필터링하는 방법을 정의할 수 있습니다.

* 새 필터를 만들려면 데이터를 선택하려면 확인할 공식을 만드는 데 필요한 필드, 연산자 및 값을 선택합니다. 여러 조건을 결합할 수 있습니다(자세한 내용은 필터 조건 [정의를 참조하십시오](../../platform/using/defining-filter-conditions.md)).
* 이전에 저장한 필터를 사용하려면 **[!UICONTROL Add]** 단추를 클릭하여 드롭다운 목록을 열고 원하는 필터를 **[!UICONTROL Predefined filter]** 선택합니다.

   ![](assets/query_editor_15.png)

* 에서 만든 필터는 다른 쿼리 응용 프로그램 **[!UICONTROL Generic query editor]** 에서 사용할 수 있고 그 반대의 경우도 사용할 수 있습니다. 필터를 저장하려면 아이콘을 **[!UICONTROL Save]** 클릭합니다.

   >[!NOTE]
   >
   >필터 만들기 및 사용에 대한 자세한 내용은 [필터링 옵션을 참조하십시오](../../platform/using/filtering-options.md).

다음 예에서 보듯이 모든 영어 사용 수신자를 복구하려면 다음을 선택합니다.&quot;수신자 언어 **는 EN과** 같습니다.&quot;

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>값 필드에 다음 공식을 입력하여 옵션에 직접 액세스할 수 **있습니다** . **$(options:OPTION_NAME)**.

필터링 조건 결과를 보려면 **[!UICONTROL Preview]** 탭을 클릭합니다. 이 경우 모든 영어 사용 수신자는 이름, 이름 및 이메일 주소로 표시됩니다.

![](assets/query_editor_nveau_98.png)

SQL 언어에 익숙한 사용자는 클릭하여 SQL **[!UICONTROL Generate SQL query]** 에서 쿼리를 볼 수 있습니다.

![](assets/query_editor_nveau_99.png)

## 5단계 - 데이터 형식 지정 {#step-5---format-data}

제한 필터를 구성하면 창에 **[!UICONTROL Data formatting]** 액세스합니다. 이 창에서는 출력 열을 다시 정렬하고 데이터를 변형하고 열 레이블의 상단/하단 문자를 변경할 수 있습니다. 계산된 필드를 사용하여 최종 결과에 공식을 적용할 수도 있습니다.

>[!NOTE]
>
>계산된 필드 유형에 대한 자세한 내용은 계산된 필드 [만들기를 참조하십시오](../../platform/using/defining-filter-conditions.md#creating-calculated-fields).

선택 취소된 열은 데이터 미리 보기 창에 표시되지 않습니다.

![](assets/query_editor_nveau_10.png)

열 **[!UICONTROL Transformation]** 을 사용하면 열 레이블을 대/소문자로 변경할 수 있습니다. 열을 선택하고 열을 **[!UICONTROL Transformation]** 클릭합니다. 다음을 선택할 수 있습니다.

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## 6단계 - 데이터 미리 보기 {#step-6---preview-data}

그 **[!UICONTROL Data preview]** 창문은 마지막 단계이다. 쿼리 결과 **[!UICONTROL Start the preview of the data]** 를 얻으려면 클릭합니다. 열 또는 XML 형식으로 사용할 수 있습니다. SQL 형식으로 쿼리를 보려면 **[!UICONTROL Generated SQL queries]** 탭을 클릭합니다.

이 예에서 데이터는 수신자의 연령에 따라 오름차순으로 정렬됩니다.

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>기본적으로 처음 200개 라인만 창에 **[!UICONTROL Data preview]** 표시됩니다. 이 값을 변경하려면 상자에 숫자를 **[!UICONTROL Lines to display]** 입력하고 을 클릭합니다 **[!UICONTROL Start the preview of the data]**.

