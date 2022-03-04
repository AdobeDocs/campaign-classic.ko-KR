---
product: campaign
title: 스크립트 만들기
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법을 알아봅니다
feature: A/B Testing
exl-id: 4143d1b7-0e2b-4672-ad57-e4d7f8fea028
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 4%

---

# 스크립트 만들기 {#step-5--creating-the-script}

![](../../assets/common.svg)

나머지 모집단에 대해 지정된 게재 콘텐츠 선택은 스크립트로 계산됩니다. 이 스크립트는 열림 비율이 가장 높은 게재 관련 정보를 복원하고 컨텐츠를 최종 게재에 복사합니다.

## 스크립트 예 {#example-of-a-script}

다음 스크립트는 타깃팅 워크플로우에서 그대로 사용할 수 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](#implementation)을 참조하십시오.

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

스크립트에 대한 자세한 내용은 [이 섹션](#details-of-the-script).

## 구현 {#implementation}

1. 다음 문서를 엽니다. **[!UICONTROL JavaScript code]** 활동.
1. 에 제공된 스크립트 복사 [스크립트 예](#example-of-a-script) 로 **[!UICONTROL JavaScript code]** 창을 엽니다.

   ![](assets/use_case_abtesting_configscript_002.png)

1. 에서 **[!UICONTROL Label]** 필드에서 스크립트 이름(예: )을 입력합니다.

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. 닫기 **[!UICONTROL JavaScript code]** 활동.
1. 워크플로우를 저장합니다.

## 스크립트 세부 정보 {#details-of-the-script}

이 섹션에서는 스크립트의 다양한 부분과 작동 모드에 대해 자세히 설명합니다.

* 스크립트의 첫 번째 부분은 질의입니다. 다음 **queryDef** 명령을 사용하면 **NmsDelivery** 테이블 타겟팅 워크플로우를 실행하고 예상 열기 수를 기준으로 정렬하여 생성된 게재 항목을 정렬하면 가장 높은 열기 비율이 있는 게재의 정보가 복구됩니다.

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

* 열기 수가 가장 높은 게재가 중복됩니다.

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* 복제한 게재의 레이블이 수정되고 단어 **최종** 가 추가됩니다.

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

* 게재가 데이터베이스에 저장됩니다.

   ```
   // save the delivery in database
   delivery.save()
   ```

* 복제한 게재의 고유 식별자는 워크플로우 변수에 저장됩니다.

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

## 기타 선택 기준 {#other-selection-criteria}

위의 예를 사용하면 이메일 열기 비율에 따라 게재 콘텐츠를 선택할 수 있습니다. 다른 게재별 지표를 기반으로 하여 조정하도록 할 수 있습니다.

* 최고의 클릭 처리량: `[indicators/@recipientClickRatio]`,
* 가장 높은 반응성 비율(이메일 열기 및 메시지 클릭): `[indicators/@reactivity]`,
* 가장 낮은 불만율: `[indicators/@refusedRatio]` sortDesc 속성에 false 값을 사용합니다.
* 가장 높은 전환율: `[indicators/@transactionRatio]`,
* 메시지 수신 후 방문한 페이지 수: `[indicators/@totalWebPage]`,
* 가장 낮은 구독 취소 비율: `[indicators/@optOutRatio]`,
* 트랜잭션 금액: `[indicators/@amount]`.

이제 최종 게재를 정의할 수 있습니다. [자세히 알아보기](a-b-testing-uc-final-delivery.md)
