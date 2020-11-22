---
solution: Campaign Classic
product: campaign
title: A/B 테스트
description: A/B 테스트
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1347'
ht-degree: 1%

---


# A/B 테스트{#a-b-testing}

이메일 전달에 필요한 컨텐츠가 여러 개 있고 타깃팅된 모집단에게 가장 큰 영향을 미치는 버전을 확인하려면 다른 버전을 일부 수신자에게 보낸 다음 성공률이 가장 높은 버전을 선택하고 나머지 수신자에게 보낼 수 있습니다.

이 사용 사례에서는 타깃팅 워크플로우를 통해 두 개의 이메일 배달 컨텐츠를 비교하려고 합니다. 메시지 및 텍스트는 두 전달 모두에서 동일합니다.레이아웃만 변경됩니다.

타깃팅된 모집단:두 개의 테스트 그룹과 나머지 모집단. 각 테스트 그룹에 다른 버전의 배달이 전송됩니다. 배달을 수행한 후 가장 높은 공개 비율의 결과를 수집하기 전에 5일 대기 기간이 구성됩니다. 점수가 가장 높은 전달 내용은 스크립트로 복구되고 테스트 그룹으로 사용되지 않은 모집단으로 전송됩니다.

가장 적합한 배달을 결정하는 기준은 사용자의 요구 사항에 맞게 변경할 수 있습니다. 개방 비율, 클릭스루 비율, 구독 비율, 재활동 등이 될 수 있습니다.

또한 이 사용 사례에 자세히 설명된 테스트는 두 개의 배달에만 해당되지만 필요한 만큼 여러 버전을 테스트할 수 있습니다. 워크플로우에 활동을 추가하면 됩니다.

A/B 테스트를 만들려면 다음 단계를 적용합니다.

* [1단계:타깃팅 워크플로우 만들기](#step-1--creating-a-targeting-workflow)
* [2단계:모집단 샘플 구성](#step-2--configuring-population-samples)
* [3단계:두 개의 배달 템플릿 만들기](#step-3--creating-two-delivery-templates)
* [4단계:워크플로우에서 배달 구성](#step-4--configuring-the-deliveries-in-the-workflow)
* [5단계:스크립트 만들기](#step-5--creating-the-script)
* [7단계:워크플로우 시작](#step-7--starting-the-workflow)
* [8단계:결과](#step-8--analyzing-the-result)분석

## Step 1: Creating a targeting workflow {#step-1--creating-a-targeting-workflow}

캠페인의 **[!UICONTROL Targeting and Workflows]** 탭에서 워크플로우를 만들어야 합니다. 두 **[!UICONTROL Query]** 활동, 활동, **[!UICONTROL Split]** 활동, **[!UICONTROL Email delivery]** 활동 및 활동에 연결된 활동 **[!UICONTROL Wait]** 으로 **[!UICONTROL JavaScript code]** **[!UICONTROL Delivery]** 구성됩니다.

1. 아직 캠페인을 만들지 않은 경우 캠페인을 만드십시오(자세한 내용은 이 [섹션](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)참조).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. **[!UICONTROL Targeting and Workflows]** 탭으로 이동합니다. 

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 기존 워크플로우의 레이블을 변경하거나 클릭하여 새 워크플로우 **[!UICONTROL Add]** 를 만듭니다(자세한 내용은 이 [섹션](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)참조).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 작업 과정에 **[!UICONTROL Query]** (**[!UICONTROL Target]** 탭), ( **[!UICONTROL Split]** 탭), (**[!UICONTROL Target]** 탭 **[!UICONTROL Email deliveries]** ), (**[!UICONTROL Deliveries]** 탭, 활동( **[!UICONTROL Wait]** 탭), 활동(Tab),**[!UICONTROL Flow Control]** **[!UICONTROL JavaScript code]****[!UICONTROL Actions]** **[!UICONTROL Delivery]****[!UICONTROL Actions]** 활동(AD), 활동(AC), 활동(AD), 마우스 활동(AA), Twitter 활동(A) 및 두 개의 마우스 활동(Tap)을 포함하여 활동을 드래그 앤 드롭합니다.

![](assets/use_case_abtesting_targetwkfl_004.png)

## 2단계:모집단 샘플 구성 {#step-2--configuring-population-samples}

### 쿼리 활동 구성 {#configuring-the-query-activity}

* Double-click the **[!UICONTROL Query]** activity.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* 링크를 **[!UICONTROL Edit query]** 클릭하고 타깃팅할 수신자를 선택합니다.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* 활동을 **[!UICONTROL Query]** 활동에 **[!UICONTROL Split]** 연결합니다.

   ![](assets/use_case_abtesting_createrecipients_003.png)

### 분할 활동 구성 {#configuring-the-split-activity}

이 활동을 통해 여러 모집단을 만들 수 있습니다.배달 A를 받는 사람, 배달 B를 받는 사람 및 나머지 모집단을 말합니다. 임의 선택을 사용하면 각 게재의 모집단의 일부만을 타깃팅할 수 있습니다.

1. 모집단 A 생성:

   * Double-click the **[!UICONTROL Split]** activity.

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * 기존 탭에서 레이블을 인구 A로 변경합니다.

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * 옵션을 **[!UICONTROL Limit the selected records]** 선택합니다.

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * 링크를 **[!UICONTROL Edit]** 클릭하고 선택한 **[!UICONTROL Activate random sampling]**&#x200B;다음 을 클릭합니다 **[!UICONTROL Next]**.

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * 임계값을 10%로 설정한 다음 을 클릭합니다 **[!UICONTROL Finish]**.

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. 모집단 B 생성:

   * 인구 B **[!UICONTROL Add]** 에 대한 새 탭을 만들려면 을 클릭합니다.

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * 모집단 수를 이전에 비해 10%로 제한합니다.

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. 나머지 채우기 만들기:

   * **[!UICONTROL General]** 탭으로 이동합니다. 

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * **[!UICONTROL Generate complement]**&#x200B;을(를) 선택합니다.

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * 이 모집단에 A와 B가 포함되지 않도록 레이블을 변경하고 을 클릭하여 활동 **[!UICONTROL OK]** 을 닫습니다.

      ![](assets/use_case_abtesting_createrecipients_013.png)

## 3단계:두 개의 배달 템플릿 만들기 {#step-3--creating-two-delivery-templates}

이제 두 개의 전달 템플릿을 만들고 싶습니다. 각 템플릿은 활동에 연결된 **[!UICONTROL Email delivery]** 활동에서 **[!UICONTROL Split]** 참조됩니다. 자세한 정보는 이 [섹션](../../delivery/using/about-templates.md)을 참조하십시오.

1. Go to the **[!UICONTROL Resources > Delivery template]** folder.
1. 배달 템플릿을 **[!UICONTROL Email]** 복제합니다.

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. 배달 A에 사용할 컨텐츠를 만듭니다.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. 배달 B에 대한 템플릿을 만들려면 이 프로세스를 반복합니다.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

## 4단계:워크플로우에서 배달 구성 {#step-4--configuring-the-deliveries-in-the-workflow}

다음 단계는 배달을 구성하는 것입니다. 이전 단계에서 생성된 세 개의 인구를 대상으로 숙명됩니다. [2단계:모집단 샘플](#step-2--configuring-population-samples)구성 처음 두 배달에서는 서로 다른 컨텐츠를 모집단 A와 B로 보낼 수 있습니다. 세 번째 배달은 A와 B를 전혀 받지 않은 모집단 전체에 대해 수행됩니다. 컨텐츠는 스크립트로 계산되며 가장 높은 공개 비율의 점수가 높은 A 또는 B와 동일합니다. 배달 A 및 B의 결과를 확인하려면 세 번째 게재에 대한 대기 기간을 구성해야 합니다. 세 번째 배달에는 **[!UICONTROL Wait]** 활동이 포함되어 있습니다.

1. 활동 **[!UICONTROL Split]** 으로 이동하여 채우기 A로 전환되는 전환 대상을 워크플로우에 이미 있는 이메일 배달 중 하나에 연결합니다.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. 배달을 두 번 클릭하여 엽니다.
1. 드롭다운 목록을 사용하여 배달 A에 사용할 템플릿을 선택합니다.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. 배달 **[!UICONTROL Continue]** 을 보려면 을 클릭하고 저장합니다.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. 인구 B로 지정되는 **[!UICONTROL Split]** 활동의 전환을 두 번째 이메일 배달에 연결합니다.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. 배달을 열고 배달 B에서 템플릿을 선택한 다음 배달을 저장합니다.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. 나머지 모집단에 대한 전환을 활동에 **[!UICONTROL Wait]** 연결합니다.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. 활동을 열고 **[!UICONTROL Wait]** 5일 대기 기간을 구성합니다.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. 활동을 **[!UICONTROL Wait]** 활동에 **[!UICONTROL JavaScript code]** 연결합니다.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

## 5단계:스크립트 만들기 {#step-5--creating-the-script}

나머지 모집단에 대해 지정되는 전달 컨텐츠 선택은 스크립트로 계산됩니다. 이 스크립트는 가장 높은 열기 비율로 배달에 대한 정보를 복구한 후 컨텐츠를 최종 배달에 복사합니다.

### 스크립트 예 {#example-of-a-script}

다음 스크립트는 타깃팅 워크플로우에서와 같이 사용할 수 있습니다. For more on this, refer to [Implementation](#implementation).

```
 // query the database to find the winner (best open rate)
   var winner = xtk.queryDef.create(
     <queryDef schema="nms:delivery" operation="get">
       <select>
         <node expr="@id"/>
         <node expr="@label"/>
         <node expr="[@operation-id]"/>
         <node expr="[@workflow-id]"/>
       </select>
       <where>
         <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
       </where>
       <orderBy>
         <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
       </orderBy>
     </queryDef>).ExecuteQuery()
   
   // create a new delivery object and initialize it by doing a copy of
   // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)

   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"

   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]

   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
 
   // save the delivery in database
   delivery.save()
 
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
```

스크립트에 대한 자세한 설명은 스크립트 [세부 정보를 참조하십시오](#details-of-the-script).

### 구현 {#implementation}

1. 활동을 **[!UICONTROL JavaScript code]** 엽니다.
1. 스크립트 [예제에 제공된 스크립트를 창에](#example-of-a-script) 복사합니다 **[!UICONTROL JavaScript code]** .

   ![](assets/use_case_abtesting_configscript_002.png)

1. 필드에 스크립트 이름(예: **[!UICONTROL Label]**

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. 활동을 **[!UICONTROL JavaScript code]** 닫습니다.
1. 워크플로우 저장

### 스크립트 세부 사항 {#details-of-the-script}

이 섹션에서는 스크립트의 다양한 부분과 해당 작동 모드에 대해 자세히 설명합니다.

* 스크립트의 첫 번째 부분은 쿼리입니다. queryDef ******명령을 사용하면 타깃팅 워크플로우를 실행하여 생성된 배달** 을 NmsDelivery테이블에서 복구할 수 있고 예상 열률을 기반으로 해당 배달을 정렬하면 가장 높은 열률을 갖는 배달의 정보가 복구됩니다.

   ```
   // query the database to find the winner (best open rate)
      var winner = xtk.queryDef.create(
        <queryDef schema="nms:delivery" operation="get">
          <select>
            <node expr="@id"/>
            <node expr="@label"/>
            <node expr="[@operation-id]"/>
          </select>
          <where>
            <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
          </where>
          <orderBy>
            <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
          </orderBy>
        </queryDef>).ExecuteQuery()
   ```

* 가장 높은 공개 비율을 갖는 배달이 중복됩니다.

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* 복제된 게재의 레이블이 수정되고 **final** 이라는 단어가 추가됩니다.

   ```
   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"
   ```

* 게재가 캠페인 대시보드에 복사됩니다.

   ```
   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]
   ```

   ```
   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
   ```

* 배달이 데이터베이스에 저장됩니다.

   ```
   // save the delivery in database
   delivery.save()
   ```

* 복제된 게재의 고유 식별자는 워크플로우 변수에 저장됩니다.

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

### 기타 선택 기준 {#other-selection-criteria}

위의 예에서는 이메일 열기 비율에 따라 배달을 선택할 수 있습니다. 다른 배달별 지표에 기초하여 적용할 수 있습니다.

* Best click throughput: `[indicators/@recipientClickRatio]`,
* 최대 재활동 비율(이메일 열기 및 메시지 클릭): `[indicators/@reactivity]`,
* 가장 낮은 불만률: `[indicators/@refusedRatio]` sortDesc 속성에 대해 false 값 사용),
* 가장 높은 전환율: `[indicators/@transactionRatio]`,
* 메시지 수신 후 방문한 페이지 수: `[indicators/@totalWebPage]`,
* 최저 구독 취소 속도: `[indicators/@optOutRatio]`,
* 거래 금액: `[indicators/@amount]`.

## 6단계:최종 배달 정의 {#step-6--defining-the-final-delivery}

A/B 테스트 우승자를 선택하기 위해 스크립트가 만들어지면 최종 전달의 매개 변수를 정의할 수 있습니다.

1. 활동을 나머지 활동에 **[!UICONTROL JavaScript code]** **[!UICONTROL Delivery]** 연결합니다.
1. 활동을 **[!UICONTROL Delivery]** 엽니다.
1. 이 활동 **[!UICONTROL Generate an outbound transition]** 으로 워크플로우를 완료하려면 옵션의 선택을 취소하십시오.
1. 다른 옵션은 기본값으로 둡니다.

   ![](assets/ab_test_final_delivery.png)

전환(활동을 통해 정의됨)에 지정된 전달을 준비하면 다음 단계에 설명된 대로 승인하고 전송을 시작할 수 있게 됩니다. **[!UICONTROL Javascript Code]**

## 7단계:워크플로우 시작 {#step-7--starting-the-workflow}

1. 워크플로우 **[!UICONTROL Start]** 를 클릭합니다.

   ![](assets/use_case_abtesting_startwkfl_001.png)

1. 캠페인 대시보드를 통해 배달 A 및 B에 대한 타겟 및 컨텐츠를 승인합니다.
1. 배달 확인
1. 5일 기간이 끝날 때까지 기다렸다가 배달 시작 결과 후 계산된 컨텐츠를 확인합니다.

   ![](assets/use_case_abtesting_startwkfl_002.png)

   이 경우 템플릿 B가 선택되었습니다.

1. 세 번째 게재의 컨텐츠가 결정되면 타겟과 컨텐트를 승인합니다.

## 8단계:결과 분석 {#step-8--analyzing-the-result}

테스트 배달이 전송되면 전송한 수신자와 해당 수신자가 열렸는지 여부를 확인할 수 있습니다.

* 타깃팅된 수신자를 확인하려면 캠페인 대시보드를 통해 배달을 열고 **[!UICONTROL Delivery]** 탭을 클릭합니다.

   ![](assets/use_case_abtesting_analysis_001.png)

* 배송이 열렸는지 확인하려면 **[!UICONTROL Tracking]** 탭으로 이동합니다.

   ![](assets/use_case_abtesting_analysis_002.png)

* 다른 게재와 비교해 보십시오.

   ![](assets/use_case_abtesting_analysis_003.png)

이 예에서는, 배달 B가 가장 높은 공개 비율을 기록했습니다. 즉, 컨텐츠 B가 최종 전달에 사용됩니다.

![](assets/use_case_abtesting_analysis_004.png)

