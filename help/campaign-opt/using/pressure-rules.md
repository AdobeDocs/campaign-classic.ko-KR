---
product: campaign
title: 압력 규칙
description: 압력 규칙
feature: Fatigue Management, Typology Rules
exl-id: c23212f2-fdf8-4820-b389-546f7c84db27
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '3285'
ht-degree: 4%

---

# 압력 규칙{#pressure-rules}

![](../../assets/v7-only.svg)

## 마케팅 피로도 기본 정보 {#about-marketing-fatigue}

판매 압력 관리 를 구현하면 마케팅 피로도 알려진 데이터베이스에서 모집단을 지나치게 모집하지 않도록 할 수 있습니다. 이를 위해 수신자당 최대 메시지 수를 정의할 수 있습니다. 또한 타깃팅된 대상자에게 최상의 메시지를 보내기 위해 캠페인 간 중재 규칙을 구현할 수도 있습니다.

**압력** 예를 들어 마케팅 피로도 관리를 위해 규칙을 사용하여 모집단에 보낼 문자 수를 2개로 제한하고, 구독자 그룹의 관심사와 가장 일치하는 커뮤니케이션을 선택하고, 불만있는 고객에게 SMS를 보내지 않습니다.

캠페인은 정의된 임계값과 메시지 가중치를 기반으로 선택됩니다.

* 임계값은 지정된 기간 내에 지정된 수신자에 대해 허가된 최대 게재 수입니다. 설정하거나 변수를 설정할 수 있습니다. 유형화 규칙 설정에서 설정되거나 계산됩니다. 을(를) 참조하십시오. [최대 메시지 수](#maximum-number-of-messages).
* 게재 가중치를 사용하면 압력 관리 프레임워크 내에서 우선 순위가 가장 높은 게재를 식별할 수 있습니다. 가중치가 가장 높은 메시지는 우선 순위가 있습니다. 을(를) 참조하십시오. [메시지 가중치](#message-weight).

중재는 진행 중인 캠페인보다 가중치가 높은 예약된 캠페인이 과도한 프로필 요청을 초래하지 않도록 확인하는 데 이루어집니다. 이 경우 프로필이 게재에서 제외됩니다.

중재 기준(메시지 가중치 및/또는 임계값)은 다음 두 가지 정보 유형에 따라 달라질 수 있습니다.

* 수신자 환경 설정(선언적 정보): 뉴스레터 가입, 수신자 상태(고객 또는 잠재 고객),
* 받는 사람 행동: 구매, 방문한 링크 등

대상 메시지를 정의하는 중재 규칙은 분석 단계에서 적용됩니다. 각 수신자 및 관련 기간 동안 다음 공식이 참인 경우 메시지가 전송됩니다. **(보낸 메시지 수) + (가중치가 큰 메시지 수) &lt; 임계값**.

그렇지 않으면 수신자가 **[!UICONTROL Excluded by arbitration]**. 자세한 내용은 [중재 후 제외](#exclusion-after-arbitration).

## 압력 규칙 만들기 {#creating-a-pressure-rule}

Adobe Campaign을 사용하여 캠페인 간의 중재를 설정하려면 캠페인 유형화를 만들고 연결된 유형화 규칙을 정의하여 시작합니다(**압력** 규칙)만 사용할 수 있습니다.

**[!UICONTROL Pressure]** 유형화 규칙을 만들고 구성하려면 다음 단계를 수행합니다.

1. 캠페인 유형화 규칙 목록에서 **[!UICONTROL New]** 아이콘 위에 표시됩니다.

   ![](assets/campaign_opt_create_a_rule_01.png)

1. 에서 **[!UICONTROL General]** 새 규칙의 탭에서 **압력** 규칙을 입력하고 그 이름과 설명을 입력합니다.

   ![](assets/campaign_opt_create_a_rule_02.png)

1. 필요한 경우 실행 순서를 변경합니다. 여러 유형화 규칙을 **[!UICONTROL Typology]** 이렇게 하면 순서가 낮은 규칙이 먼저 적용됩니다. 자세한 내용은 [실행 순서](applying-rules.md#execution-order).
1. 에서 **[!UICONTROL Calculation parameters]** 섹션에서 다음 일별 재중재 실행 이외에 타깃팅을 저장하려면 빈도를 정의합니다. 자세한 내용은 [계산 빈도 조정](applying-rules.md#adjusting-calculation-frequency).
1. 을(를) 클릭합니다. **[!UICONTROL Pressure]** 탭하고 유형화 규칙이 적용되는 달력 기간을 선택합니다.

   ![](assets/campaign_opt_create_a_rule_03.png)

   해당 기간에 연락 날짜가 포함된 게재에 규칙이 적용됩니다.

   >[!NOTE]
   >
   >예약된 게재는 **[!UICONTROL Take the deliveries into account in the provisional calendar]** 옵션이 선택되어 있습니다. 자세한 내용은 [기간 설정](#setting-the-period).
   >
   >이 옵션은 Campaign v8에서는 사용할 수 없습니다.

1. 가장 많은 메시지 수를 계산하는 방법을 정의합니다.

   임계값은 관련 기간 동안 수신자에게 보낼 수 있는 최대 메시지 수를 나타냅니다.

   기본적으로 임계값은 일정하며 규칙에서 허가한 최대 메시지 수를 표시해야 합니다.

   ![](assets/campaign_opt_create_a_rule_03b.png)

   변수 임계값을 정의하려면 **[!UICONTROL Depends on the recipient]** 값에서 **[!UICONTROL Type of threshold]** 필드를 작성하고 오른쪽의 아이콘을 사용하여 표현식 편집기를 엽니다.

   ![](assets/campaign_opt_create_a_rule_04.png)

   자세한 내용은 [최대 메시지 수](#maximum-number-of-messages).

1. 게재 가중치를 계산하는 방법을 지정합니다.

   각 게재에는 가중치(즉, 우선 순위 수준을 나타내는 값)가 있습니다. 이를 통해 캠페인 간의 중재를 수행할 수 있습니다. 가중치는 유형화 규칙 및/또는 해당 속성에 정의된 공식을 사용하여 계산됩니다. 자세한 내용은 [메시지 가중치](#message-weight).

1. 기본적으로 모든 메시지는 임계값 계산에 고려됩니다. 다음 **[!UICONTROL Restriction]** 탭에서는 유형화 규칙에 관련된 메시지를 필터링할 수 있습니다.

   * 이 탭의 상단 섹션에서 관련 수신자를 제한할 수 있습니다.
   * 이 탭의 아래 섹션에서 계산할 메시지를 필터링할 수 있습니다.

      다음 예제에서는 **새 연락처** 폴더부터 시작하여 및 게재를 고려합니다. **뉴스레터** 걱정됩니다.
   ![](assets/campaign_opt_create_a_rule_05.png)

1. 다음 **[!UICONTROL Typologies]** 탭에서는 이 규칙을 적용하거나 규칙을 하나 이상의 기존 유형화에 연결하는 캠페인 유형화를 볼 수 있습니다. 자세한 내용은 [유형화 적용](about-campaign-typologies.md#applying-typologies).

## 임계값 및 가중치 정의 {#defining-thresholds-and-weights}

### 최대 메시지 수 {#maximum-number-of-messages}

각 압력 규칙은 특정 기간 동안 한 수신자에게 보낼 수 있는 최대 메시지 수, 즉 임계값을 정의합니다. 이 임계값에 도달하면, 고려된 기간이 끝날 때까지 더 이상 게재할 수 없습니다. 이 프로세스를 사용하면 메시지가 설정된 임계값을 초과하는 경우 게재 시 수신자를 자동으로 제외하여 과도한 요청을 방지할 수 있습니다.

임계값은 상수 또는 변수가 있는 수식으로 계산될 수 있습니다. 즉, 특정 기간 동안 임계값은 수신자마다 또는 심지어 동일한 수신자에 대해서도 다를 수 있습니다.

![](assets/campaign_opt_create_a_rule_threshold.png)

>[!CAUTION]
>
>입력 **0** 임계값은 고려된 기간 동안 대상 모집단에 대한 모든 게재를 방지합니다.

**예제:**

수신자가 속한 세그먼트에 따라 허용된 메시지 수를 인덱싱할 수 있습니다. 즉, 웹 세그먼트에 속하는 수신자는 다른 수신자보다 더 많은 메시지를 받을 수 있습니다. An **[!UICONTROL Iif (@origin='Web', 5, 3)]** 유형 수식은 수신자에게 5개의 메시지를 전달하고 다른 세그먼트에 대해서는 3개의 메시지를 게재하도록 허용합니다. 구성은 다음과 같습니다.

![](assets/campaign_opt_pressure_sample.png)

임계값을 정의하려면 타겟팅 차원에 연결된 차원을 사용할 수 있습니다. 예를 들어 방문자 표에 저장된 수신자 프로필로 전달된 메시지를 포함하려면 방문자 테이블에 대한 자세한 내용은 [이 섹션](../../surveys/using/use-case--creating-a-refer-a-friend-form.md)) 또는 매주 두 개 이상의 메시지를 동일한 가구에 보내지 않기 위해(여러 이메일 주소를 참조할 수 있음) 수신자의 차원과 연결된 차원에서 식별됩니다.

이렇게 하려면 을(를) 선택합니다. **[!UICONTROL Count messages on a linked dimension]** 옵션을 선택한 다음 방문자 또는 연락처 테이블을 선택합니다.

### 메시지 가중치 {#message-weight}

각 게재에는 우선 순위 수준을 나타내는 가중치가 있습니다. 기본적으로 게재 가중치는 5로 설정됩니다. 압력 규칙을 사용하여 게재의 가중치를 정의할 수 있습니다.

가중치는 수신자에 맞게 수식을 통해 설정하거나 계산할 수 있습니다. 예를 들어 수신자 관심사에 따라 게재 가중치를 정의할 수 있습니다.

>[!CAUTION]
>
>유형화 규칙에 정의된 가중치는 **[!UICONTROL Properties]** 탭. 을(를) 클릭합니다. **[!UICONTROL Typology]** 탭하여 캠페인 유형화를 선택하고, 필요한 경우 적용할 가중치를 지정합니다.\
>그러나 A 유형화 규칙에 선언된 가중치는 B 유형화 규칙을 계산하는 데 사용되지 않습니다. 이 가중치는 A 규칙을 사용하는 게재에만 적용됩니다.

**예제:**

다음 예에서는 음악의 뉴스레터 가중치를 수신자의 성향 점수와 연결하려고 합니다. 방법은 다음과 같습니다.

1. 수신자 성향 점수를 저장할 새 필드를 만듭니다. 필드, **@Music** 이 경우 은 설문 조사 및 온라인 설문 조사, 수집된 추적 데이터 등에 대한 응답으로 보강됩니다.
1. 이 필드를 기반으로 메시지 가중치를 계산하기 위해 유형화 규칙을 만듭니다.

   ![](assets/campaign_opt_pressure_weight_sample.png)

1. 이 규칙을 다음 항목이 있는 메시지에 적용합니다. 뉴스레터, 특별 오퍼 등 이러한 게재의 가중치는 따라서 게재의 우선 순위 수준은 각 수신자의 성향 점수에 따라 달라집니다.

## 기간 설정 {#setting-the-period}

압력 규칙은 **n**-일 순환 기간.

기간은 **[!UICONTROL Pressure]** 규칙의 탭입니다. 일 수를 지정하고 필요한 경우 적용할 그룹화 유형(일, 주, 월, 분기 등)을 선택할 수 있습니다.

그룹화 유형을 사용하면 **[!UICONTROL Period considered]** 해당 기간에 대한 날짜의 전체 일, 달력 주, 달력 월 또는 달력 연도로 필드를 추가합니다.

예를 들어, 매주 2개의 메시지의 임계값을 정의하고 각 달력 월을 그룹화하는 압력 규칙은 동일한 주 내에 2개 이상의 메시지를 전달하지 않고 동일한 달력 월 내에 메시지를 전달하지 못하도록 합니다. 경고: 기간이 2개월과 겹치는 경우 계산 임계값은 이러한 두 달력의 게재를 고려하므로 두 번째 달 동안 모든 새 게재를 방지할 수 있습니다.

기본적으로 임계값을 계산할 때 이미 전송된 게재만 고려됩니다. Campaign Classic v7에서 **[!UICONTROL Take the deliveries into account in the provisional calendar]** 관련 기간에 대해 예약된 게재도 고려하려는 경우 선택 사항입니다. 이 경우 고려된 기간이 두 배로 증가하여 이전 게재뿐만 아니라 미래 게재도 통합할 수 있습니다.

2주 기간을 고려하여 게재를 제한하려면 다음 중 하나를 수행할 수 있습니다.

1. Enter 키 **15d** 에서 **[!UICONTROL Concerned period]** 필드: 규칙이 적용되는 게재 일자 이전 최대 2주 전까지 전송된 게재는 계산에 고려됩니다.

또는

1. Enter 키 **7d** 에서 **[!UICONTROL Period considered]** 필드를 확인하고 **[!UICONTROL Take the deliveries into account in the provisional calendar]** 옵션: 규칙이 적용되는 게재 일자 이전 최대 7일까지 전송된 게재 및 게재 일자 이후 최대 7일까지 예약된 게재가 계산에 고려됩니다.

   >[!AVAILABILITY]
   >이 메서드는 Campaign v8에서는 사용할 수 없습니다.

기간 시작 날짜는 데이터베이스가 구성되는 방식에 따라 다릅니다.

예를 들어 날짜 12/11 게재에 그룹화하지 않고 15일 압력 규칙을 적용하는 경우 11/27과 12/12 사이에서 게재고려됩니다. 압력 규칙이 임시 달력의 게재를 고려하면 11/27과 12/27 사이에 예약된 모든 게재가 고려됩니다. 마지막으로, 규칙에서 달력 개월당 그룹을 구성하는 경우, 11월과 12월의 모든 게재가 임계값 계산(11/1에서 12/31)을 고려하게 됩니다.


**빈번한 사례**

현재 달력 주의 게재가 고려되지 않도록 하고, 계산 임계값에 대한 이전 주의 게재도 고려하지 않도록 하려면 을(를) 지정합니다. **[!UICONTROL Period considered]** &#39;0&#39;에서 &#39;1주일 그룹화&#39;를 **[!UICONTROL Period type]**.

기간이 0보다 큰 경우(예: 1) 계산 임계값은 이전 날짜의 게재를 고려할 수 있습니다. 따라서 이전 날짜가 이전 달력 주에 해당되고 선택한 기간 유형이 &#39;달력 주당 그룹화&#39;인 경우 계산 임계값에 대해 이전 주가 모두 고려됩니다.

**예제:**

2주 기간당 3개의 메시지로 모집단을 제한하는 달력 월을 날짜로 그룹화하는 압력 규칙을 만들려고 합니다.

![](assets/campaign_opt_pressure_period_sample_1a.png)

05/30, 06/3, 06/8, 06/12, 06/22 및 06/30으로 예약된 동일한 무게의 뉴스레터 6개를 가져오겠습니다.

![](assets/campaign_opt_pressure_period_sample_0.png)

6월 12일과 30일로 예정된 게재는 전송되지 않습니다. 06/12 게재은 2주 기간당 3개의 메시지 임계값인 3을 초과하며 30번째 게재는 달력 개월당 허용된 통신 임계값을 초과합니다.

![](assets/campaign_opt_pressure_period_sample_1.png)

이러한 게재에 대한 모든 수신자는 분석 단계 중 중재에 의해 제외됩니다.

![](assets/campaign_opt_pressure_period_sample_2.png)

동일한 규칙의 경우 분기당 게재를 그룹화하는 경우 **뉴스레터 번호 5** 또한 제외되며 전송되지 않습니다.

마지막으로 선택한 그룹이 없으면 **뉴스레터 번호 4** 최초 3개의 뉴스레터와 동일한 2주 기간으로 예정되었으므로 이 메시지는 전송되지 않습니다.

>[!NOTE]
>
>유형화 규칙의 정의를 변경할 때 **시뮬레이션** 게재에 미치는 영향을 제어하고 게재가 서로에게 미치는 영향을 모니터링합니다. 자세한 내용은 [캠페인 시뮬레이션](campaign-simulations.md).

## 중재 후 제외 {#exclusion-after-arbitration}

중재는 매일 밤 **[!UICONTROL Forecasting]** 기술 워크플로우 및 **[!UICONTROL Campaign jobs]** 워크플로우.

다음 **[!UICONTROL Forecasting]** 워크플로우는 분석 중에 유형화 규칙을 적용할 수 있도록 진행 중인 기간(시작 날짜부터 현재 날짜까지)의 데이터를 미리 계산합니다. 또한 매일 밤 중재에 대한 제외 카운터를 다시 계산한다.

따라서 Adobe Campaign은 각 수신자에 대해 전송할 메시지 수가 해당 기간 동안 이미 전송된 메시지 수를 고려하여 임계값을 초과하지 않는지 확인합니다. 이 정보는 **표시기**, 게재 시 모든 계산이 업데이트됩니다.

이 수가 임계값을 초과하는 경우 캠페인 유형화에 정의된 중재 규칙이 적용되며 수신자는 가중치가 낮은 캠페인에서 제외됩니다.

![](assets/campaign_opt_pressure_exclusion.png)

>[!NOTE]
>
>여러 게재에 동일한 점수가 있는 경우, 가장 이른 날짜에 예약된 캠페인이 전송됩니다.

## 압력 규칙의 사용 사례 {#use-cases-on-pressure-rules}

### 기준에 따라 임계값 조정 {#adapting-the-threshold-based-on-criterion}

고객에게 매주 4개 이상의 메시지와 잠재 고객에게 매주 2개 이상의 메시지를 게재하지 않도록 유형화 규칙을 만들려고 합니다.

고객 및 잠재 고객을 식별하려면 **[!UICONTROL Status]** 이 필드에는 잠재 고객의 경우 0과 고객의 경우 1이 포함됩니다.

규칙을 만들려면 다음 단계를 적용합니다.

1. 새 만들기 **압력** 유형화 규칙을 입력합니다.
1. 편집 **[!UICONTROL Pressure]** 탭: 에서 **[!UICONTROL Maximum number of messages]** 섹션에서 각 수신자에 따라 임계값을 계산하는 수식을 생성하려고 합니다. 을(를) 선택합니다 **[!UICONTROL Depends on the recipient]** 값에서 **[!UICONTROL Threshold type]** 필드를 클릭한 다음 **[!UICONTROL Edit expression]** 오른쪽 **[!UICONTROL Formula]** 필드.

   을(를) 클릭합니다. **[!UICONTROL Advanced parameters]** 버튼을 눌러 계산 공식을 정의합니다.

   ![](assets/campaign_opt_pressure_sample_1_1.png)

1. 을(를) 선택합니다 **[!UICONTROL Edit the formula using an expression]** 옵션을 선택하고 **[!UICONTROL Next]**.

   ![](assets/campaign_opt_pressure_sample_1_2.png)

1. 함수 목록에서 **Iif** 함수 내에 있어야 합니다 **[!UICONTROL Others]** 노드 아래에 있어야 합니다.

   그런 다음 수신자의 이름을 선택합니다 **상태** 에서 **[!UICONTROL Available fields]** 섹션을 참조하십시오.

   ![](assets/campaign_opt_pressure_sample_1_3.png)

   다음 공식을 입력합니다. **Iif(@status=0,2,4)**

   ![](assets/campaign_opt_pressure_sample_1_4.png)

   이 수식을 사용하면 상태가 0인 경우 값 2를 할당하고 다른 모든 상태에 대해 값 4를 할당할 수 있습니다.

   수식을 승인하려면 **[!UICONTROL Finish]**&#x200B;을(를) 클릭합니다.

1. 규칙을 적용할 기간을 지정합니다. 이 경우 7일 동안 매주 메시지 수를 카운트합니다.

   ![](assets/campaign_opt_pressure_sample_1_5.png)

1. 규칙을 저장하여 생성을 승인합니다.

이제 방금 만든 규칙을 게재에 적용하기 위해 유형화에 연결합니다. 방법은 다음과 같습니다.

1. 캠페인 유형화를 만듭니다.
1. 로 이동합니다. **[!UICONTROL Rules]** 탭에서 **[!UICONTROL Add]** 버튼을 클릭하고 방금 만든 규칙을 선택합니다.

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. 유형화를 저장합니다. 기존 유형화 목록에 추가됩니까?

게재에서 이 유형화를 사용하려면 게재 속성의 **[!UICONTROL Typology]** 아래와 같이 탭합니다.

![](assets/campaign_opt_pressure_sample_1_7.png)

>[!NOTE]
>
>이 템플릿을 사용하여 만든 모든 게재에 자동으로 적용되도록 게재 템플릿에서 유형화를 정의할 수 있습니다.

게재 분석 중에 이미 보낸 게재 수에 따라 해당되는 경우 게재 수신자는 게재에서 제외됩니다. 이 정보를 보려면 다음을 수행할 수 있습니다.

* 분석 결과 보기:

   ![](assets/campaign_opt_pressure_sample_1_8.png)

* 게재를 편집하고 을(를) 클릭합니다. **[!UICONTROL Delivery]** 탭 및 **[!UICONTROL Exclusions]** 하위 탭:

   ![](assets/campaign_opt_pressure_sample_1_9.png)

* 을(를) 클릭합니다. **[!UICONTROL Audit]** 탭을 클릭한 다음 **[!UICONTROL Causes of exclusions]** 하위 탭에서 제외 수와 적용된 유형화 규칙을 표시합니다.

   ![](assets/campaign_opt_pressure_sample_1_10.png)

### 동작을 기준으로 게재 가중치 계산 {#calculating-the-delivery-weight-based-on-behavior}

수신자 행동에 따라 압력 규칙을 정의할 수 있습니다. 따라서, 게재 가중치는 수신자마다 다른 기준에 맞게 조정될 수 있다. 예를 들어, 수신자가 여러분의 인터넷 사이트를 방문했는지, 마지막 뉴스레터의 특정 섹션을 클릭했는지, 정보 서비스를 구독했는지 또는 설문 조사, 온라인 게임 등에 대한 답변을 기반으로 메시지를 전송할지를 결정할 수 있습니다.

다음 예제에서는 가중치가 5인 게재를 만들려고 합니다. 이 가중치는 수신자 행동을 기반으로 성향 점수로 보강됩니다. 이 사이트에서 이미 주문한 고객은 점수 5점을 받게 되며 온라인 주문을 한 적이 없는 고객은 점수 4점을 받게 됩니다.

이 유형의 구성을 수행하려면 수식을 사용하여 메시지 가중치를 정의해야 합니다. 성향 점수와 설문 조사 응답에 대한 정보는 데이터 모델에서 액세스할 수 있어야 합니다. 이 예제에서는 **성향** 필드가 추가되었습니다.

다음 구성 단계를 적용합니다.

1. 새 만들기 **압력** 유형화 규칙을 입력합니다.
1. 편집 **[!UICONTROL Pressure]** 탭. 각 개별 수신자를 기반으로 하는 임계값 수식을 생성하려고 합니다. 를 클릭합니다. **[!UICONTROL Edit expression]** 아이콘 을 클릭합니다. **[!UICONTROL Weight formula]** 필드.

   ![](assets/campaign_opt_pressure_sample_2_1.png)

1. 기본적으로 값 **5개** 표현식 편집기의 위쪽 섹션에 표시됩니다. 이 가중치에 각 수신자의 성향 점수를 추가하려고 합니다. 5의 오른쪽에 커서를 놓고 **+** 문자를 선택하고 **성향** 필드.

   ![](assets/campaign_opt_pressure_sample_2_2.png)

1. 그런 다음 이미 구매한 수신자의 값을 더 높게 추가합니다. 그들에게, 배달되는 것의 무게는 5를 증가시켜야 하고, 다른 사람들에게는 4만 증가시켜야만 합니다.

   ![](assets/campaign_opt_pressure_sample_2_3.png)

1. 클릭 **[!UICONTROL Finish]** 을 눌러 이 규칙을 저장합니다.
1. 규칙을 캠페인 유형화에 연결하고 게재에서 이 유형화를 참조하여 승인합니다.

### 가중치가 가장 높은 메시지만 전송 {#sending-only-the-highest-weighted-messages}

동일한 주 내에 하루에 메시지 2개로 제한되는 2개 이하의 메시지를 각 수신자에게 전송하려고 하며 가중치가 높은 메시지만 배달할 수 있습니다.

이렇게 하려면 동일한 수신자에 대해 서로 다른 가중치를 사용하여 여러 게재를 예약하고 가중치가 낮은 게재를 제외하도록 압력 규칙을 적용해야 합니다.

먼저 압력 규칙을 구성합니다.

1. 압력 규칙을 만듭니다. 자세한 내용은 [압력 규칙 만들기](#creating-a-pressure-rule).
1. 에서 **[!UICONTROL General]** 탭에서 을 선택합니다 **[!UICONTROL Re-apply the rule at the start of personalization]** 선택 사항입니다.

   ![](assets/campaign_opt_pressure_example_5.png)

   이 옵션은 **[!UICONTROL Frequency]** 필드를 작성하고 개인화 단계 동안 규칙을 자동으로 적용합니다. 자세한 내용은 [계산 빈도 조정](applying-rules.md#adjusting-calculation-frequency).

1. 에서 **[!UICONTROL Pressure]** 탭, 선택 **[!UICONTROL 7d]** 로서의 **[!UICONTROL Period considered]** 및 **[!UICONTROL Grouping per day]** 로서의 **[!UICONTROL Period type]**.
1. 을(를) 선택합니다 **[!UICONTROL Take the deliveries into account in the provisional calendar]** 예약된 게재를 포함하는 옵션.

   ![](assets/campaign_opt_pressure_example_1.png)

   게재 일자 이전 최대 7일까지 전송된 게재 및 게재 일자 이후 최대 7일까지 예약된 게재가 계산에 고려됩니다. 자세한 내용은 [기간 설정](#setting-the-period).

   >[!AVAILABILITY]
   >Campaign v8에서는 예약된 게재를 고려할 수 없습니다.

1. 에서 **[!UICONTROL Typologies]** 탭에서 규칙을 캠페인 유형화에 연결합니다.
1. 변경 내용을 저장합니다.

이제 압력 규칙을 적용할 각 게재에 대한 워크플로우를 만들고 구성합니다.

1. 캠페인 만들기. 이 작업에 대한 자세한 정보는 [이 섹션](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)을 참조하십시오.
1. 에서 **[!UICONTROL Targeting and workflows]** 캠페인의 탭에서 다음을 추가합니다 **쿼리** 활동을 워크플로우에 추가합니다. 이 활동 사용에 대한 자세한 내용은 [이 섹션](../../workflow/using/query.md).
1. 추가 **[!UICONTROL Email delivery]** 활동을 워크플로우에 추가하고 엽니다. 이 활동 사용에 대한 자세한 내용은 [이 섹션](../../workflow/using/delivery.md).
1. 로 이동합니다. **[!UICONTROL Approvals]** 의 탭 **[!UICONTROL Delivery properties]** 모든 승인을 비활성화합니다.

   ![](assets/campaign_opt_pressure_example_2.png)

1. 에서 **[!UICONTROL Typology]** 의 탭 **[!UICONTROL Delivery properties]**&#x200B;에서 규칙을 적용하려면 campaign 유형화를 참조하십시오. 게재의 가중치를 정의합니다.

   ![](assets/campaign_opt_pressure_example_3.png)

1. 게재에서 **[!UICONTROL Scheduling]** 을(를) 선택합니다. **[!UICONTROL Schedule delivery (automatic execution when the scheduled date is reached)]**. 이 예에서 **[!UICONTROL Use a calculation formula]** 선택 사항입니다.
1. 추출 날짜를 10분(현재 날짜 + 10분)으로 설정합니다.
1. 연락 날짜를 다음 날(현재 날짜 + 1일)로 설정합니다.

   ![](assets/campaign_opt_pressure_example_4.png)

   압력 규칙 제외를 성공적으로 구현하려면 연락 날짜 및 시간 전뿐만 아니라 야간 중재가 다시 적용되기 전에 추출 날짜 및 시간을 설정해야 합니다. 자세한 내용은 [중재 후 제외](#exclusion-after-arbitration).

1. 선택 취소 **[!UICONTROL Confirm the delivery before sending]** 옵션을 선택하고 변경 내용을 저장합니다.
1. 전송할 각 게재에 대해 유사하게 진행합니다. 각 게재에 대해 원하는 가중치를 설정해야 합니다.
1. 관련 워크플로우를 실행하여 게재를 준비하고 전송합니다.

야간 중재 기능이 적용되면, 동일한 수신자에 대해 가중치가 낮은 게재가 제외됩니다. 전송 시 가중치가 가장 높은 게재만 고려됩니다. 자세한 내용은 [메시지 가중치](#message-weight).

주 중에 이미 해당 수신자에게 전자 메일이 전송되었으므로 아래 표에는 두 개의 추가 게재에 적용할 수 있는 구성의 예가 나와 있습니다.

<table> 
 <thead> 
  <tr> 
   <th> 게재<br /> </th> 
   <th> 승인<br /> </th> 
   <th> 두께<br /> </th> 
   <th> 추출 날짜/시간<br /> </th> 
   <th> 연락 날짜<br /> </th> 
   <th> 배달 시작 날짜/시간<br /> </th> 
   <th> 중재 워크플로우 실행 날짜/시간<br /> </th> 
   <th> 배달 상태<br /> </th> 
   <th> 전송 전송(날짜/시간)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 배달 1<br /> </td> 
   <td> 비활성화<br /> </td> 
   <td> 5<br /> </td> 
   <td> 오후 3시<br /> </td> 
   <td> 오전 8시(다음날)<br /> </td> 
   <td> 오후 2시<br /> </td> 
   <td> 매일 밤<br /> </td> 
   <td> 제외됨<br /> </td> 
   <td> 제외됨<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달 2<br /> </td> 
   <td> 비활성화<br /> </td> 
   <td> 10<br /> </td> 
   <td> 오후 4시<br /> </td> 
   <td> 오전 9시(다음날)<br /> </td> 
   <td> 오후 2시<br /> </td> 
   <td> 매일 밤<br /> </td> 
   <td> 전송됨<br /> </td> 
   <td> 오전 9시(다음날)<br /> </td> 
  </tr> 
 </tbody> 
</table>

두 게재에 대한 추출 날짜가 지나면 야간 중재가 두 게재의 연락 날짜 전에 다시 적용됩니다. 이렇게 하면 이미 전송된 모든 게재(게재를 처리하는 수신자, 광범위한 로그를 통해 기록된 수신자) 또는 전송 예약된 게재(예측 로그를 통해 기록된 게재를 받을 수 있는 수신자)를 찾을 수 있습니다.

압력 규칙에 정의된 기간 동안 모든 전송 및 잠재적 게재가 나열되면 Adobe Campaign은 먼저 가장 높은 가중치를 사용하여 가중치를 기준으로 정렬합니다. 압력 규칙에 설정된 임계값에 도달하면(동일한 주 내에 2개 이하의 이메일이 아님) 수신자가 게재에서 제외됩니다.
