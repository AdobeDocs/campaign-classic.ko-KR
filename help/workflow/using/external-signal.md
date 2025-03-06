---
product: campaign
title: 외부 신호
description: 외부 신호 워크플로우 활동에 대해 자세히 알아보기
feature: Workflows
hide: true
hidefromtoc: true
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# 외부 신호{#external-signal}



**외부 신호** 활동을 사용하면 일정에 따라 워크플로우에서 작업 집합의 실행을 트리거할 수 있습니다.

&#39;외부 신호&#39; 작업이 활성화되면 지정된 기간이 끝날 때까지 또는 무기한 일시 중지됩니다. 해당 전환은 SOAP 호출 **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete)에 의해 활성화됩니다.** **[!UICONTROL complete]** 매개 변수를 사용하면 작업을 완료할 수 있으므로 후속 호출에 반응하지 않습니다.

PostEvent 함수에 대한 자세한 내용은 SOAP 호출과 관련된 온라인 설명서를 참조하십시오.

신호가 수신되지 않은 경우 이벤트를 정의하기 위해 이 활동을 구성할 수 있습니다. 이렇게 하려면 활동을 편집하고 **[!UICONTROL Expiration]** 탭을 클릭하십시오. 이벤트를 만들고 구성하려면 **[!UICONTROL Insert]** 단추를 클릭하십시오.

![](assets/edit_signal.png)

만료 구성은 [만료](defining-approvals.md)에 자세히 설명되어 있습니다.

**지연** 필드를 사용하면 선택한 단위로 만료 지연을 지정할 수 있습니다. [대기](wait.md)를 참조하십시오.

각 행은 만료 유형을 나타내며 전환과 일치합니다.

![](assets/external_sign_diag.png)
