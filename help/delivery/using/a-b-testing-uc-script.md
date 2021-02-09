---
solution: Campaign Classic
product: campaign
title: 스크립트 만들기
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법을 살펴볼 수 있습니다.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---


# 스크립트 {#step-5--creating-the-script} 만들기

나머지 모집단에 대해 지정할 전달 내용의 선택은 스크립트로 계산됩니다. 이 스크립트는 게재에 대한 정보를 연 중 가장 높은 비율로 복원하고 컨텐츠를 최종 전달으로 복사합니다.

## 스크립트 {#example-of-a-script} 예

다음 스크립트는 타깃팅 워크플로우에서와 같이 사용할 수 있습니다. 자세한 내용은 [구현](#implementation)을 참조하십시오.

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

스크립트에 대한 자세한 설명은 [스크립트 세부 정보](#details-of-the-script)를 참조하십시오.

## 구현 {#implementation}

1. **[!UICONTROL JavaScript code]** 활동을 엽니다.
1. [스크립트 예](#example-of-a-script)에서 제공된 스크립트를 **[!UICONTROL JavaScript code]** 창에 복사합니다.

   ![](assets/use_case_abtesting_configscript_002.png)

1. **[!UICONTROL Label]** 필드에 스크립트 이름(예:

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. **[!UICONTROL JavaScript code]** 활동을 닫습니다.
1. 워크플로우를 저장합니다.

## 스크립트 {#details-of-the-script} 세부 정보

이 섹션에서는 스크립트의 다양한 부분과 해당 운영 모드에 대해 자세히 설명합니다.

* 스크립트의 첫 번째 부분은 쿼리입니다. **queryDef** 명령을 사용하면 타게팅 워크플로우를 실행하여 만든 배달을 **NmsDelivery** 테이블에서 복구할 수 있고 예상 열률을 기준으로 배달을 정렬하면 최대 개수의 게재에서 정보가 복구됩니다.

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

* 연 횟수가 가장 높은 배달은 중복됩니다.

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* 중복된 배달의 레이블이 수정되고 **final**&#x200B;이라는 단어가 추가됩니다.

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

* 중복 게재의 고유 식별자는 워크플로우 변수에 저장됩니다.

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

## 기타 선택 기준 {#other-selection-criteria}

위의 예를 사용하면 이메일 열기 비율에 따라 전달 컨텐츠를 선택할 수 있습니다. 다음과 같은 다른 배달별 지표를 기준으로 자신을 기준으로 조정할 수 있습니다.

* 최고의 클릭 처리량:`[indicators/@recipientClickRatio]`,
* 최대 재활동 비율(이메일 열기 및 메시지 클릭):`[indicators/@reactivity]`,
* 최저 불만 비율:`[indicators/@refusedRatio]`(sortDesc 속성에 대해 false 값 사용),
* 가장 높은 전환율:`[indicators/@transactionRatio]`,
* 메시지 수신을 따라 방문한 페이지 수:`[indicators/@totalWebPage]`,
* 최저 구독 취소 비율:`[indicators/@optOutRatio]`,
* 거래 금액:`[indicators/@amount]`.
