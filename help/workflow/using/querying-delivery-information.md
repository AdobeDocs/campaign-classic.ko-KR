---
title: 게재 정보 쿼리
description: 배달 정보를 쿼리하는 방법 학습
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 1%

---


# 게재 정보 쿼리 {#querying-delivery-information}

## 특정 전달에 대한 클릭 수 {#number-of-clicks-for-a-specific-delivery}

이 예에서는 특정 전달에 대한 클릭 수를 복구하려고 합니다. 이러한 클릭은 지정된 기간 동안 수집된 수신자 추적 로그로 인해 기록됩니다. 수신자는 이메일 주소를 통해 식별됩니다. 이 쿼리는 테이블을 **[!UICONTROL Recipient tracking logs]** 사용합니다.

* 어떤 표를 선택해야 합니까?

   받는 사람 로그 추적 테이블(**[!UICONTROL nms:trackingLogRcp]**)

* 출력 열에 대해 선택할 필드를 선택하십시오.

   기본 키(카운트 포함) 및 이메일

* 어떤 기준을 기준으로 정보를 필터링합니까?

   배달 레이블의 특정 기간 및 요소

이 예제를 실행하려면 다음 단계를 수행하십시오.

1. 스키마를 열고 **[!UICONTROL Generic query editor]** 스키마를 **[!UICONTROL Recipient tracking logs]** 선택합니다.

   ![](assets/query_editor_tracklog_05.png)

1. 창에서 정보를 수집하기 위한 집계를 만들고 **[!UICONTROL Data to extract]** 싶습니다. 이렇게 하려면 기본 키(기본 요소 위에 있음)를 **[!UICONTROL Recipient tracking logs]** 추가합니다.추적 로그 수는 이 **[!UICONTROL Primary key]** 필드에 적용됩니다. 편집된 표현식이 됩니다 **[!UICONTROL x=count(primary key)]**. 다양한 추적 로그의 합을 하나의 이메일 주소로 연결합니다.

   방법은 다음과 같습니다.

   * 필드 오른쪽에 있는 **[!UICONTROL Add]** 아이콘을 **[!UICONTROL Output columns]** 클릭합니다. 창 **[!UICONTROL Formula type]** 에서 **[!UICONTROL Edit the formula using an expression]** 옵션을 선택하고 을 클릭합니다 **[!UICONTROL Next]**. In the **[!UICONTROL Field to select]** window, click **[!UICONTROL Advanced selection]**.

      ![](assets/query_editor_tracklog_06.png)

   * 창에서 **[!UICONTROL Formula type]** 집계 함수에서 프로세스를 실행합니다. 이 프로세스는 기본 키 카운트가 됩니다.

      섹션 **[!UICONTROL Process on an aggregate function]** 에서 **[!UICONTROL Aggregate]** 를 선택하고 을 클릭합니다 **[!UICONTROL Count]**.

      ![](assets/query_editor_nveau_18.png)

      **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   * 필드를 **[!UICONTROL Primary key (@id)]** 선택합니다. 출력 **[!UICONTROL count (primary key)]** 열이 구성됩니다.

      ![](assets/query_editor_nveau_19.png)

1. 출력 열에 표시할 다른 필드를 선택합니다. 열에서 **[!UICONTROL Available fields]** 노드를 열고 **[!UICONTROL Recipient]** 선택합니다 **[!UICONTROL Email]**. 이메일 **[!UICONTROL Group]** 주소로 추적 로그를 **[!UICONTROL Yes]** 그룹화하려면 다음을 선택합니다.이 그룹은 각 로그를 수신자에게 연결합니다.

   ![](assets/query_editor_nveau_20.png)

1. 가장 활성화된 받는 사람(추적 로그가 가장 많은 사람)이 먼저 표시되도록 열 정렬을 구성합니다. 열 **[!UICONTROL Yes]** 을 **[!UICONTROL Descending sort]** 체크인하세요

   ![](assets/query_editor_nveau_64.png)

1. 그런 다음 관심 있는 로그(예: 2주 미만이고 판매 관련 게재와 관련된 로그)를 필터링해야 합니다.

   방법은 다음과 같습니다.

   * 데이터 필터링을 구성합니다. 이렇게 하려면 을 선택한 **[!UICONTROL Filter conditions]** 다음 을 클릭합니다 **[!UICONTROL Next]**.

      ![](assets/query_editor_nveau_22.png)

   * 특정 전달에 대해 지정된 기간 동안 추적 로그를 복구합니다. 세 가지 필터링 조건이 필요합니다.현재 날짜 전 2주 및 현재 날짜 전일 사이의 검색 기간을 설정하는 두 가지 날짜 조건및 검색을 특정 게재로 제한하는 다른 조건.

      창에서 **[!UICONTROL Target element]** 추적 로그를 고려할 시작 날짜를 구성합니다. **[!UICONTROL Add]**&#x200B;을(를) 클릭합니다. 조건 라인이 표시됩니다. 함수를 **[!UICONTROL Expression]** 클릭하여 열을 **[!UICONTROL Edit expression]** 편집합니다. 창에서 **[!UICONTROL Field to select]** 선택합니다 **[!UICONTROL Date (@logDate)]**.

      ![](assets/query_editor_nveau_23.png)

      연산자를 **[!UICONTROL greater than]** 선택합니다. 열에서 **[!UICONTROL Value]** 을 **[!UICONTROL Edit expression]**&#x200B;클릭하고 **[!UICONTROL Formula type]** 창에서 을 선택합니다 **[!UICONTROL Process on dates]**. 마지막으로 &quot;15&quot; **[!UICONTROL Current date minus n days]**&#x200B;를 입력합니다.

      **[!UICONTROL Finish]**&#x200B;을(를) 클릭합니다.

      ![](assets/query_editor_nveau_24.png)

   * 추적 로그 검색 종료 날짜를 선택하려면 을 클릭하여 두 번째 조건을 만듭니다 **[!UICONTROL Add]**. 열에서 **[!UICONTROL Expression]** 다시 **[!UICONTROL Date (@logDate)]** 선택합니다.

      연산자를 **[!UICONTROL less than]** 선택합니다. In the **[!UICONTROL Value]** column, click **[!UICONTROL Edit expression]**. 날짜 처리를 위해 **[!UICONTROL Formula type]** 창으로 이동하여 &quot;1&quot;을 입력합니다 **[!UICONTROL Current date minus n days]**.

      **[!UICONTROL Finish]**&#x200B;을(를) 클릭합니다.

      ![](assets/query_editor_nveau_65.png)

      이제 세 번째 필터 조건(예: 쿼리가 염려하는 배달 레이블)을 구성하려고 합니다.

   * 다른 필터링 조건을 만들려면 **[!UICONTROL Add]** 함수를 클릭합니다. In the **[!UICONTROL Expression]** column, click **[!UICONTROL Edit expression]**. 창 **[!UICONTROL Field to select]** 에서 노드 **[!UICONTROL Label]** 에서 선택합니다 **[!UICONTROL Delivery]** .

      **[!UICONTROL Finish]**&#x200B;을(를) 클릭합니다.

      ![](assets/query_editor_nveau_66.png)

      &quot;sales&quot;라는 단어가 포함된 배달을 찾습니다. 정확한 레이블을 기억할 수 없으므로 연산자를 선택하고 열에 &quot;sales&quot;를 입력할 수 **[!UICONTROL contains]** **[!UICONTROL Value]** 있습니다.

      ![](assets/query_editor_nveau_25.png)

1. 창으로 **[!UICONTROL Next]** 이동할 때까지 을 **[!UICONTROL Data preview]** 클릭합니다.여기에 서식을 지정할 필요가 없습니다.
1. 각 배달 받는 사람 **[!UICONTROL Data preview]** **[!UICONTROL Start the preview of the data]** 에 대한 추적 로그 수를 보려면 창에서 을 클릭합니다.

   결과가 내림차순으로 표시됩니다.

   ![](assets/query_editor_tracklog_04.png)

   사용자의 최대 로그 수는 이 전달에 6개입니다. 5명의 다른 사용자가 이메일 배달 이메일을 열거나 이메일에 있는 링크 중 하나를 클릭했습니다.

## 배달을 열지 않은 받는 사람 {#recipients-who-did-not-open-any-delivery}

이 예에서는 지난 7일 동안 이메일을 열지 않은 수신자를 필터링하려고 합니다.

이 예제를 만들려면 다음 단계를 수행하십시오.

1. 워크플로우에서 **[!UICONTROL Query]** 활동을 드래그하여 놓고 활동을 엽니다.
1. 타겟 및 필터링 차원 **[!UICONTROL Edit query]** 을 클릭하고 설정합니다 **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. 을 **[!UICONTROL Filtering conditions]** 선택하고 을 클릭합니다 **[!UICONTROL Next]**.
1. Click the **[!UICONTROL Add]** button and select **[!UICONTROL Tracking logs]**.
1. 표현식 **[!UICONTROL Operator]** 을 **[!UICONTROL Tracking logs]** 로 설정합니다 **[!UICONTROL Do not exist such as]**.

   ![](assets/query_open_1.png)

1. 다른 표현식을 추가합니다. 카테고리 **[!UICONTROL Type]** 에서 **[!UICONTROL URL]** 선택합니다.
1. 그런 다음, **[!UICONTROL Operator]** 를 **[!UICONTROL equal to]** 설정하고 **[!UICONTROL Value]** 로 **[!UICONTROL Open]**&#x200B;설정합니다.

   ![](assets/query_open_2.png)

1. 다른 표현식을 추가하고 선택합니다 **[!UICONTROL Date]**. **[!UICONTROL Operator]** 을(를) 로 설정해야 합니다 **[!UICONTROL on or after]**.

   ![](assets/query_open_3.png)

1. 지난 7일 동안 값을 설정하려면 필드에 있는 **[!UICONTROL Edit expression]** 단추를 **[!UICONTROL Value]** 클릭합니다.
1. 카테고리에서 타깃팅할 일 수 **[!UICONTROL Function]** **[!UICONTROL Current date minus n days]** 를 선택하고 추가합니다. 여기, 우리는 지난 7일을 목표로 하고 있습니다.

   ![](assets/query_open_4.png)

아웃바운드 전환에는 지난 7일 동안 이메일을 열지 않은 수신자가 포함됩니다.

반면에 하나 이상의 이메일을 연 수신자를 필터링하려면 쿼리는 다음과 같아야 합니다. 이 경우 이 설정을 로 **[!UICONTROL Filtering dimension]** 설정해야 합니다 **[!UICONTROL Tracking logs (Recipients)]**.

![](assets/query_open_5.png)

## 배달을 연 받는 사람 {#recipients-who-have-opened-a-delivery}

다음 예에서는 지난 2주 이내에 배달을 연 프로파일을 타깃팅하는 방법을 보여줍니다.

1. 배달을 연 프로파일을 타깃팅하려면 추적 로그를 사용해야 합니다. 연결된 테이블에 저장됩니다.아래에서와 같이 필드의 드롭다운 목록에서 이 테이블을 선택하여 **[!UICONTROL Filtering dimension]** 시작합니다.

   ![](assets/s_advuser_query_sample1.0.png)

1. 필터링 조건에 대해, 추적 로그의 하위 트리 구조에 표시된 기준의 **[!UICONTROL Edit expression]** 아이콘을 클릭합니다. 필드를 **[!UICONTROL Date]** 선택합니다.

   ![](assets/s_advuser_query_sample1.1.png)

   Click **[!UICONTROL Finish]** to confirm selection.

   2주 미만의 추적 로그만 복구하려면 연산자를 **[!UICONTROL Greater than]** 선택합니다.

   ![](assets/s_advuser_query_sample1.4.png)

   그런 다음 열의 **[!UICONTROL Edit expression]** 아이콘을 **[!UICONTROL Value]** 클릭하여 적용할 계산 공식을 정의합니다. 공식을 **[!UICONTROL Current date minus n days]** 선택하고 관련 필드에 15를 입력합니다.

   ![](assets/s_advuser_query_sample1.5.png)

   공식 창의 **[!UICONTROL Finish]** 단추를 클릭합니다. 필터링 창에서 **[!UICONTROL Preview]** 탭을 클릭하여 타깃팅 기준을 확인합니다.

   ![](assets/s_advuser_query_sample1.6.png)

## 배달 후 받는 사람의 동작 필터링 {#filtering-recipients--behavior-folllowing-a-delivery}

워크플로우에서 **[!UICONTROL Query]** 및 **[!UICONTROL Split]** 상자를 사용하여 이전 전달 후 동작을 선택할 수 있습니다. 이 선택 사항은 **[!UICONTROL Delivery recipient]** 필터를 통해 수행됩니다.

* 이 예제의 목표

   배달 워크플로우에서는 첫 번째 이메일 통신을 처리하는 여러 가지 방법이 있습니다. 이 유형의 작업은 **[!UICONTROL Split]** 상자 사용과 관련되어 있습니다.

* 컨텍스트

   &quot;여름 스포츠 행사&quot; 배달을 보냅니다. 배달된 지 4일 후, 다른 두 가지 배달이 전송됩니다. 그 중 하나는 &quot;수상 스포츠 제안&quot;이고, 다른 하나는 첫 &quot;여름 스포츠 제안&quot; 전달의 후속 단계입니다.

   &quot;워터스포츠 오퍼&quot; 배달은 첫 번째 배달에서 &quot;watersports&quot; 링크를 클릭한 수신자에게 전송됩니다. 이러한 클릭은 수신자가 주제에 관심이 있음을 보여줍니다. 그들을 비슷한 제안으로 이끄는 것은 말이 된다. 그러나 &quot;여름 스포츠 오퍼&quot;에서 클릭하지 않은 수신자는 동일한 컨텐츠를 다시 받게 됩니다.

다음 단계에서는 두 가지 다른 동작을 통합하여 **[!UICONTROL Split]** 상자를 구성하는 방법을 보여 줍니다.

1. 워크플로우에 **[!UICONTROL Split]** 상자를 삽입합니다. 이 상자는 첫 번째 배달의 수신자를 다음 두 개의 배달로 분류합니다. 분류는 첫 번째 배달 중 받는 사람 동작과 연결된 필터링 조건을 기반으로 합니다.

   ![](assets/query_editor_ex_09.png)

1. 상자를 **[!UICONTROL Split]** 엽니다. 탭에서 **[!UICONTROL General]** 레이블을 입력합니다. **예를 들어 동작을** 기반으로 분할할 수 있습니다.

   ![](assets/query_editor_ex_04.png)

1. 탭에서 첫 번째 분할 분기를 **[!UICONTROL Subsets]** 정의합니다. 예를 들어, 이 분기의 **클릭됨** 레이블을 입력합니다.
1. 옵션을 **[!UICONTROL Add a filtering condition on the incoming population]** 선택합니다. **[!UICONTROL Edit]**&#x200B;을(를) 클릭합니다.
1. 창에서 **[!UICONTROL Targeting and filtering dimension]** 필터 **[!UICONTROL Recipients of a delivery]** 를 두 번 클릭합니다.

   ![](assets/query_editor_ex_05.png)

1. 창에서 **[!UICONTROL Target element]** 이 분기에 적용할 동작을 선택합니다. **[!UICONTROL Recipients having clicked (email)]**.

   아래에서 옵션을 **[!UICONTROL Delivery specified by the transition]** 선택합니다. 이 기능은 첫 번째 배달 중에 타깃팅된 사람을 자동으로 복구합니다.

   이것은 &quot;워터스포츠 행사&quot; 배달입니다.

   ![](assets/query_editor_ex_08.png)

1. 두 번째 분기를 정의합니다. 이 분기에는 첫 번째 배달을 위한 것과 동일한 컨텐츠가 포함된 후속 이메일이 포함됩니다. 탭으로 **[!UICONTROL Subsets]** 가서 을 클릭하여 **[!UICONTROL Add]** 만듭니다.

   ![](assets/query_editor_ex_06.png)

1. 다른 하위 탭이 표시됩니다. 이름을 &quot;**클릭하지**&#x200B;않음&quot;으로 지정합니다.
1. **[!UICONTROL Add a filtering condition for the incoming population]**&#x200B;을(를) 클릭합니다. 그 다음 **[!UICONTROL Edit...]**&#x200B;을(를) 클릭합니다.

   ![](assets/query_editor_ex_07.png)

1. 창 **[!UICONTROL Delivery recipients]** 을 **[!UICONTROL Targeting and filtering dimension]** 클릭합니다.
1. 창에서 **[!UICONTROL Target element]** 동작을 **[!UICONTROL Recipients who did not click (email)]** 선택합니다. 마지막 분기에 대해 표시된 대로 **[!UICONTROL Delivery specified by the transition]** 옵션을 선택합니다.

   이제 **[!UICONTROL Split]** 상자가 완전히 구성됩니다.

   ![](assets/query_editor_ex_03.png)

다음은 기본적으로 구성된 다양한 구성 요소 목록입니다.

* **[!UICONTROL All recipients]**
* **[!UICONTROL Recipients of successfully sent messages,]**
* **[!UICONTROL Recipients who opened or clicked (email),]**
* **[!UICONTROL Recipients who clicked (email),]**
* **[!UICONTROL Recipients of a failed message,]**
* **[!UICONTROL Recipients who didn't open or click (email),]**
* **[!UICONTROL Recipients who didn't click (email).]**

   ![](assets/query_editor_ex_02.png)
