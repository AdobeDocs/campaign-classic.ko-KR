---
product: campaign
title: 승인 정의
description: 승인을 사용하면 운영자가 워크플로우를 관리하는 결정을 하거나 워크플로우의 지속적인 실행을 확인할 수 있습니다
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Approvals
exl-id: 4d413d51-ae5d-4e5e-bfaf-4160a6075281
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 4%

---

# 승인 정의 {#defining-approvals}



승인을 사용하면 운영자가 워크플로우를 관리하는 결정을 하거나 워크플로우의 지속적인 실행을 확인할 수 있습니다.

메시지가 운영자 그룹에 전송되고 워크플로우는 재개하기 전에 응답을 기다립니다. 워크플로우가 중지되지 않고 다른 작업이 수행될 수 있습니다. 예를 들어 여러 개의 동시 승인이 보류 중일 수 있습니다.

승인에는 운영자가 선택할 수 있는 여러 옵션이 포함될 수 있습니다. 다만, 타기팅 수행 등 수행하고자 하는 과제를 운영자에게 제출하기 위해서는 선택횟수를 1회로 제한할 수 있다. 그러면 작업자는 작업이 수행된 후 응답할 수 있습니다(그런 다음 프로세스가 다시 시작됨). 다음 예에서는 이러한 승인 유형을 보여 줍니다.

![](assets/validation-1.png)

운영에서 승인이 필요한 모든 단계는 동일한 원칙에 기반한다.

![](assets/validation-1-in-op.png)

승인 예는에서 찾을 수 있습니다. [이 섹션](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

연산자는 두 가지 방법 중 하나로 응답할 수 있습니다. 즉, 이메일 메시지에 연결된 웹 페이지를 사용하거나 콘솔을 통해 확인합니다.

>[!NOTE]
>
>응답이 저장되면 수정되지 않을 수 있습니다.

## 이메일을 통한 승인 {#sending-emails}

응답이 가능한 웹 페이지에 대한 링크가 포함된 승인 메시지를 수신할 수 있다. 타겟팅된 운영자가 승인 이메일을 받으려면 운영자 이메일 주소가 완전해야 합니다. 그렇지 않은 경우 운영자는 콘솔을 사용하여 응답해야 합니다

운영자 관리는 이에 자세히 설명되어 있습니다 [섹션](../../platform/using/access-management.md).

승인 이메일은 지속적으로 전송됩니다. 기본 게재 템플릿은 입니다. **[!UICONTROL notifyAssignee]**: 다음에 저장됩니다. **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 폴더를 삭제합니다. 이 시나리오는 사용자 지정할 수 있으며, 사본을 만들고 각 활동에 대한 템플릿을 변경하는 것이 좋습니다.

이 템플릿을 통해 만든 게재는 **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** 폴더를 삭제합니다.

## 콘솔을 통한 승인 {#approval-via-the-console}

작업에서 승인할 요소가 캠페인 대시보드에 표시됩니다.

기술 워크플로우의 경우, 사용자가 승인할 수 있는 작업은 의 트리 구조에서 액세스할 수 있습니다. **[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]** 폴더를 삭제합니다.

![](assets/validation-node.png)

## 그룹 {#groups}

승인 은 연산자 그룹, 단일 연산자 또는 필터링 조건을 통해 선택한 연산자 세트에 할당됩니다.

1. 가장 간단한 형태의 승인의 경우 운영자가 응답하자마자 작업이 완료된다. 응답하려는 다른 운영자는 누군가가 이미 했다는 알림을 받게 됩니다.
1. 여러 승인의 경우 다음을 참조하십시오. [다중 승인](#multiple-approval).

승인을 위한 운영자 그룹은 명명된 개인이 아닌 역할 또는 기능으로 지정되어야 한다. 예를 들어 &quot;캠페인 예산&quot; 그룹은 &quot;Harry&#39;s group&quot;보다 선호됩니다. 작업을 승인할 수 있는 두 명 이상의 사람이 한 그룹에 있는 것이 좋습니다. 이와 같이 한 명이 부재하면 다른 한 명은 이에 응할 수 있다.

## 만료 {#expirations}

만료는 다른 유형의 활동, 특히 승인에서 사용되는 특정 전환입니다. 만료 기능을 사용하여 응답 없이 주어진 시간 후에 작업을 트리거할 수 있습니다. 예를 들어 워크플로우를 추적하고 다른 그룹에 승인을 할당하는 데 사용할 수도 있습니다.

활동 승인 속성의 두 번째 탭에서는 하나 이상의 만료를 정의할 수 있습니다. 실제로 여러 만료 유형을 정의할 수 있습니다.

![](assets/expiration.png)

새 만료를 추가하려면 **[!UICONTROL Add]**. 생성된 각 만료에 전환이 추가됩니다. 다음을 수행할 수 있습니다.

* 목록에서 셀을 클릭하거나 F2 키를 눌러 일반 매개변수를 직접 수정합니다.
* 또는 를 클릭하여 표현식을 편집합니다. **[!UICONTROL Detail...]** 단추를 클릭합니다.

>[!NOTE]
>
>만료는 시간 순서대로 처리되므로 순서를 지정할 필요는 없습니다.

다음 **[!UICONTROL Do not terminate the task]** 지연 시간이 초과되면 옵션은 승인을 활성 상태로 둡니다. 이 모드를 사용하면 승인을 활성 상태로 두는 동안 미리 알림을 관리할 수 있습니다. 운영자는 여전히 응답할 수 있습니다. 이 옵션은 기본적으로 비활성화되어 있으며, 이는 작업이 만료 시 완료된 것으로 간주되어 운영자가 더 이상 응답하지 않을 수 있음을 의미합니다.

다음과 같은 네 가지 유형의 만료를 만들 수 있습니다.

* **작업 시작 후 지연**: 만료는 승인이 활성화된 날짜에 지정된 시간을 추가하여 계산됩니다.
* **지정된 날짜 이후로 지연**: 지정한 날짜에 시간을 추가하여 만료가 계산됩니다.
* **지정된 날짜 이전으로 지연**: 만료는 지정한 날짜에서 시간을 빼서 계산됩니다.
* **스크립트로 계산된 만료**: 만료는 JavaScript를 사용하여 계산됩니다.

   다음 예제에서는 게재가 시작되기 24시간 전에 만료를 계산합니다( 로 식별됨). **vars.deliveryId**):

   ```
   var delivery = nms.delivery.get(vars.deliveryId)
   var expiration = delivery.scheduling.contactDate
   var oneDay = 1000*60*60*24
   expiration.setTime(expiration.getTime() - oneDay)
   return expiration
   ```

## 여러 승인 {#multiple-approval}

복수 승인은 모든 승인 운영자가 응답할 수 있는 메커니즘입니다. 각 응답에 대해 전환이 활성화됩니다.

복수 승인은 투표 또는 설문 조사 메커니즘에 유용합니다. 기한을 추가하여 주어진 기간 이후에 답변을 집계하고 결과를 처리할 수 있다.

## 필수 권한 {#required-rights}

그룹의 운영자가 승인 요청에 응답할 수 있으려면 적어도 다음 권한이 있어야 합니다.

* 워크플로우에 대한 쓰기 권한입니다.
* 승인할 작업이 포함된 폴더에 대한 읽기 및 쓰기 권한입니다.

워크플로 실행 그룹에는 이러한 권한이 있습니다. 이 그룹에 추가된 운영자는 승인 요청에 응답할 권한이 있습니다.
