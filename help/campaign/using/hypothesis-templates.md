---
solution: Campaign Classic
product: campaign
title: 가설 템플릿
description: 가설 템플릿
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1435'
ht-degree: 0%

---


# 가설 템플릿{#hypothesis-templates}

## 가설 모델 만들기 {#creating-a-hypothesis-model}

가설 템플릿을 구성하면 전달 또는 오퍼에 대한 반응 측정 컨텍스트를 정의할 수 있습니다. 개인, 가설 및 거래 테이블 간의 관계를 정의하는 테이블을 비롯하여 다양한 측정 테이블이 참조되는 곳입니다.

가설 템플릿을 만들려면 다음 단계를 수행하십시오.

1. Adobe Campaign 탐색기에서 **[!UICONTROL Resources>Templates>Hypothesis templates]**&#x200B;을 클릭합니다.

   ![](assets/response_hypothesis_model_creation_001.png)

1. **[!UICONTROL New]**&#x200B;을 클릭하거나 템플릿 목록을 마우스 오른쪽 단추로 클릭하고 드롭다운 목록에서 **[!UICONTROL New]**&#x200B;을 선택합니다.
1. 가설 레이블을 입력합니다.
1. 템플릿이 **[!UICONTROL Hypothesis type]**&#x200B;을 통해 오퍼 또는 배달에서 가설을 제공하도록 지정되었는지 여부를 지정합니다.
1. **[!UICONTROL Delivery]** 유형 템플릿의 경우 제어 그룹과 함께 측정을 수행할지 아니면 제어 그룹 없이 측정을 수행할지 여부를 지정합니다(자세한 내용은 [가설 템플릿](#properties-of-a-hypothesis-template) 속성 참조).
1. **[!UICONTROL Delivery]** 유형 템플릿의 경우, 특정 채널을 선택하거나 **[!UICONTROL Channel]** 드롭다운 목록을 사용하여 Adobe Campaign에서 사용 가능한 모든 채널에 템플릿을 적용할 수 있습니다(자세한 내용은 [가설 템플릿](#properties-of-a-hypothesis-template)의 속성 참조).
1. 이 템플릿에서 만들 가설을 만들고 자동으로 실행할 **[!UICONTROL Execution folder]**&#x200B;을 선택합니다.
1. 실행 설정을 선택합니다(자세한 내용은 [가설 템플릿 실행 설정](#hypothesis-template-execution-settings) 참조).
1. 가설 계산 기간을 지정합니다(자세한 내용은 [가설 템플릿 실행 설정](#hypothesis-template-execution-settings) 참조).

   >[!CAUTION]
   >
   >이 기간은 연락처 날짜로부터 결정됩니다.

1. **[!UICONTROL Transactions]** 탭에서 가설 계산에 필요한 테이블과 필드를 지정합니다(자세한 내용은 [거래](#transactions) 참조).
1. 템플릿이 **[!UICONTROL Offer]** 유형 가설을 위해 구성된 경우 **[!UICONTROL Update offer proposition status]** 옵션을 활성화할 수 있습니다.이 경우 변경할 제안 제안의 상태를 선택합니다.
1. 가설 응용 프로그램의 범위를 지정합니다(자세한 내용은 [가설 경계](#hypothesis-perimeter) 참조).
1. 필요한 경우 스크립트를 사용하여 필터링을 완료하십시오. 이에 대한 자세한 내용은 [가설 경계](#hypothesis-perimeter) 참조).

### 가설 템플릿의 속성 {#properties-of-a-hypothesis-template}

템플릿의 **[!UICONTROL General]** 탭에서는 일반 템플릿 옵션을 지정할 수 있습니다. 사용 가능한 필드는 다음과 같습니다.

* **[!UICONTROL Hypothesis type]**:템플릿을 제공 또는 오퍼에 대한 가설을 지정할 것인지 여부를 결정할 수 있습니다.

   게재와 오퍼 모두에 적용되는 가설을 만들도록 선택할 수도 있습니다.

   >[!NOTE]
   >
   >템플릿이 오퍼에 적용되는 경우 **[!UICONTROL Update offer proposition status]** 옵션은 **[!UICONTROL Transactions]** 탭에서 사용할 수 있습니다.

* **[!UICONTROL Measurement with control group]**:전달 또는 캠페인에 대해 제어 그룹이 정의되었는지 여부를 나타내며 측정 지표에 포함할 수 있습니다. 배달을 받지 않는 제어 그룹은 배달을 받은 대상 모집단과 비교하여 게재 후 캠페인의 영향을 측정할 수 있습니다.

   >[!NOTE]
   >
   >템플릿이 제어 그룹을 고려하도록 구성되었지만 가설이 우려되는 전달 시 정의된 그룹이 없는 경우 결과가 타깃팅된 받는 사람만을 기반으로 합니다.

   제어 그룹 정의 및 구성에 대한 자세한 내용은 [제어 그룹 정의](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)를 참조하십시오.

* **[!UICONTROL Channel]**:드롭다운 목록에서 선택하여 특정 채널을 선택하거나 Adobe Campaign 콘솔의 모든 채널 **[!UICONTROL All channels]** 에서 가설 템플릿을 사용할 수 있도록 할 수 있습니다. 특정 채널에 대한 템플릿을 구성하는 경우 가설을 만들 때 채널당 제공을 자동으로 필터링할 수 있습니다([가설 만들기](../../campaign/using/creating-hypotheses.md) 참조).

   ![](assets/response_properties_001.png)

* **[!UICONTROL Execution folder]**:가설을 위한 실행 폴더를 지정할 수 있습니다.
* **[!UICONTROL Taken into account in campaign ROI calculation]**:관련 캠페인에 대한 ROI 계산에 가설 결과를 고려합니다.

### 가설 템플릿 실행 설정 {#hypothesis-template-execution-settings}

템플릿의 **[!UICONTROL General]** 탭에서도 가설 실행 매개 변수를 지정할 수 있습니다. 사용 가능한 옵션은 다음과 같습니다.

* **[!UICONTROL Schedule execution for a time of low activity]**:adobe campaign 성능을 최적화하기 위해 가설 시작을 예약할 수 있습니다. 이 옵션을 선택하면 캠페인의 처리 워크플로우는 가동 중지 시간 동안 가설을 계산합니다.

   ![](assets/response_exec_settings_002.png)

* **[!UICONTROL Priority]**:동시 실행이 있는 경우 가설 계산 순서를 구분하는 데 적용 레벨입니다.

   ![](assets/response_exec_settings_003.png)

* **[!UICONTROL Automatic execution]**:필요한 경우 가설 다시 계산을 예약할 수 있습니다(예를 들어 게재를 마칠 때까지 표시기를 정기적으로 업데이트하려면).

   ![](assets/response_exec_settings_001.png)

   일정을 지정하려면 다음 프로세스를 적용합니다.

   1. **[!UICONTROL Frequency of execution...]** 링크를 클릭한 다음 **[!UICONTROL Change...]** 단추를 클릭합니다.

      ![](assets/response_frequency_execution_001.png)

   1. 빈도, 관련 이벤트 및 유효성 기간을 구성합니다.

      ![](assets/response_frequency_execution_002.png)

   1. **[!UICONTROL Finish]**&#x200B;을 클릭하여 일정을 저장합니다.

      ![](assets/response_frequency_execution_003.png)

* **[!UICONTROL Log SQL queries in journal]**:이 함수는 전문가 사용자를 위해 예약되어 있습니다. 측정 가설 감사에 탭을 추가하여 SQL 쿼리를 표시할 수 있습니다. 이렇게 하면 시뮬레이션이 오류로 인해 끝날 경우 가능한 잘못된 기능을 감지할 수 있습니다.
* **[!UICONTROL Keep execution workflow]**:가설 계산 시작 시 자동으로 생성된 워크플로우를 유지할 수 있습니다. 이 옵션을 선택한 템플릿으로 만든 가설에서 생성된 워크플로우를 사용하여 프로세스를 진행할 수 있습니다.

   >[!CAUTION]
   >
   >이 옵션은 가설을 실행하는 동안 오류가 발생하는 경우 디버깅용으로만 활성화해야 합니다.\
   >또한 자동으로 생성된 워크플로우는 수정되지 않아야 합니다. 최종 수정은 나중에 계산을 위해 다른 곳에서 고려되지 않을 것이다.\
   >이 옵션을 선택한 경우 워크플로우를 실행한 후 삭제합니다.

### 트랜잭션 {#transactions}

이 탭에는 거래 측면에서 수신자 반응 내역을 저장할 수 있는 다양한 필드와 테이블이 포함되어 있습니다. 응답 관리 전용 테이블에 대한 자세한 내용은 [구성](../../configuration/using/about-schema-reference.md) 안내서를 참조하십시오.

* **[!UICONTROL Schema (reaction log storage)]**:받는 사람 반응 테이블을 선택합니다. Adobe Campaign의 기본 테이블은 **NmsRemaMatchRcp**&#x200B;입니다.
* **[!UICONTROL Transaction schema]**:거래 또는 구매 테이블 등 가설이 관심을 가지는 테이블을 선택합니다.
* **[!UICONTROL Querying schema]**:가설을 필터링하는 기준을 선택합니다.
* **[!UICONTROL Link to individuals]**:개인 및 트랜잭션 스키마로 사용되는 테이블 간의 링크를 선택합니다.
* **[!UICONTROL Link to the household]**:가설을 포함한 모든 구성원을 포함하려면 거래 스키마의 가문에 대한 링크를 선택합니다. 이 필드는 선택 사항입니다.
* **[!UICONTROL Transaction date]**:이 필드는 선택 사항이지만 가설 계산 범위를 정의할 수 있으므로 권장됩니다.
* **[!UICONTROL Measurement period]**:가설을 실행하고 구매 라인이 복구되는 시작 및 종료 날짜를 구성할 수 있습니다.

   가설이 게재와 연결되면 직접 우편 배달의 연락일 이후 또는 이메일 또는 SMS 전달의 배달 배달 배달 배달 날짜 이후 며칠 후에 자동으로 측정이 트리거됩니다.

   ![](assets/response_measurement_001.png)

   가설이 바로 시작될 경우, 즉시 이를 자극할 수 밖에 없다. 그렇지 않으면 가설 생성 날짜를 기반으로 하는 구성된 계산 종료 날짜를 기반으로 자동으로 트리거됩니다(전달[ 시 가설 만들기 참조).](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)

* **[!UICONTROL Transaction/Margin amount]**:이러한 필드는 선택 사항이며 매출 표시기를 자동으로 계산할 수  [있습니다(지표](../../campaign/using/hypothesis-tracking.md#indicators) 참조).
* **[!UICONTROL Unit amount]**:매출을 계산하기 위한 금액을 설정할 수 있습니다(지표  [참조](../../campaign/using/hypothesis-tracking.md#indicators)).

   ![](assets/response_transactions_001.png)

* **[!UICONTROL Additional measures and data]**:다른 테이블의 필드에서 추가 보고 측정값 또는 축을 지정할 수 있습니다.
* **[!UICONTROL Update offer proposition status]**:오퍼 수신자가 가설을 통해 식별되는 경우 오퍼 제안의 상태를 변경할 수 있습니다.

   ![](assets/response_offer_status_001.png)

### 가설 경계 {#hypothesis-perimeter}

거래 테이블과 가설이 관심을 가지는 필드를 정의했으면 필터를 사용하여 대상 거래 및 제공을 지정하여 가설을 세부적으로 조정할 수 있습니다. JavaScript 스크립트를 사용하여 트랜잭션 테이블에서 참조되는 제품을 명시적으로 지정할 수도 있습니다.

* **트랜잭션 필터링**:탭에서  **[!UICONTROL Scope]** 가설을 위한 필터를 구성할 수 있습니다. 방법은 다음과 같습니다.

   1. **[!UICONTROL Edit query]** 링크를 클릭합니다.

      ![](assets/response_scope_filtering_001.png)

   1. 필터링 조건을 지정합니다.

      ![](assets/response_scope_filtering_002.png)

   1. 가설이 염려할 거래를 선택합니다.

      ![](assets/response_scope_filtering_003.png)

* **받는 사람** 필터링:탭 **[!UICONTROL Scope]** 에서 다음과 같은 메시지와 연결된 정보(배달, 수신자, 이메일 주소, 서비스 등)로 가설을 제한할 수 있습니다.

   1. **[!UICONTROL Add a filter]** 링크를 클릭한 다음 **[!UICONTROL Edit query]**.

      ![](assets/response_scope_filtering_004.png)

   1. 필터링 조건을 지정합니다.

      ![](assets/response_scope_filtering_005.png)

   1. **[!UICONTROL Finish]**&#x200B;을 클릭하여 쿼리를 저장합니다.

      ![](assets/response_scope_filtering_006.png)

* **스크립트**:JavaScript 스크립트를 사용하여 실행 중에 가설 설정을 동적으로 오버로드할 수 있습니다.

   이렇게 하려면 **[!UICONTROL Advanced settings]** 링크를 클릭한 다음 원하는 스크립트를 입력합니다.

   >[!NOTE]
   >
   >이 옵션은 전문가 사용자용입니다.

   ![](assets/response_hypothesis_model_creation_011.png)

## 예:배달 {#example--creating-a-hypothesis-template-on-a-delivery}에 가설 템플릿 만들기

이 예에서는 DM 유형 전달에 가설 템플릿을 만듭니다. 가설을 기반으로 하는 거래 테이블(**구매**)에는 아티클이나 제품에 연결된 구매 라인이 포함되어 있습니다. 구매 테이블의 아티클 또는 제품에 대한 가설을 만들도록 모델을 구성하려고 합니다.

1. Adobe Campaign 탐색기에서 **[!UICONTROL Resources > Templates > Hypothesis templates]** 노드로 이동합니다.
1. 템플릿을 만들려면 **[!UICONTROL New]**&#x200B;을 클릭합니다.

   ![](assets/response_hypothesis_model_example_001.png)

1. 템플릿 레이블을 변경합니다.

   ![](assets/response_hypothesis_model_example_002.png)

1. 가설 유형으로 **[!UICONTROL Deliveries]**&#x200B;을 선택합니다.
1. 관련 상자를 선택하여 게재에 제어 그룹이 포함될 수 있도록 지정합니다.
1. **[!UICONTROL Direct mail]** 채널을 선택합니다.

   >[!NOTE]
   >
   >템플릿은 다이렉트 메일 배달에만 적용되므로 이 모델을 사용하여 만든 가설을 다른 배달 유형에 연결할 수 없습니다.

1. **[!UICONTROL Transactions]** 탭에서 수신자 반응 테이블을 선택합니다.

   ![](assets/response_hypothesis_model_example_006.png)

1. **[!UICONTROL Transactions schema]** 필드에서 구매 테이블을 선택합니다.

   ![](assets/response_hypothesis_model_example_007.png)

1. **[!UICONTROL Querying schema]** 필드에서 구매 라인을 선택합니다.

   ![](assets/response_hypothesis_model_example_008.png)

1. 구매 테이블에 연결된 받는 사람을 선택합니다.

   ![](assets/response_hypothesis_model_example_009.png)

1. 구매 날짜에 연결된 필드를 선택합니다.

   이를 통해 가설을 위한 시간대를 정의할 수 있습니다. 이 단계는 필수는 아니지만 권장됩니다.

   ![](assets/response_hypothesis_model_example_010.png)

1. 5~25일 계산 기간을 구성합니다.

   ![](assets/response_hypothesis_model_example_005.png)

1. **[!UICONTROL Scope]** 탭에서 **[!UICONTROL Edit query]**&#x200B;을 클릭하여 가설을 위한 필터를 만듭니다.

   ![](assets/response_hypothesis_model_example_011.png)

   이렇게 만들어진 템플릿을 사용하면 구매 테이블의 제품 또는 문서에 대한 가설을 실행할 수 있습니다.

1. 템플릿을 기록하려면 **[!UICONTROL Save]**&#x200B;을 클릭합니다.

