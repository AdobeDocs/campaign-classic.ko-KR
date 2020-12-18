---
solution: Campaign Classic
product: campaign
title: 외부 신호
description: 외부 신호 워크플로우 활동에 대한 자세한 내용
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---


# 외부 신호{#external-signal}

**외부 신호** 활동을 사용하면 워크플로우의 작업 집합 실행을 일정에 맞게 트리거할 수 있습니다.

&#39;외부 신호&#39; 작업을 활성화하면 무한히 또는 지정된 기간이 끝날 때까지 일시 중지됩니다. 해당 전환은 SOAP 호출 **PostEvent(sessionToken, workflowId, 활동, 전환, 매개 변수, 완료)에 의해 활성화됩니다.** 매개  **[!UICONTROL complete]** 변수를 사용하면 작업이 완료되므로 후속 호출에 응답하지 않습니다.

PostEvent 함수에 대한 자세한 내용은 SOAP 호출에 대한 온라인 설명서를 참조하십시오.

신호를 받지 못할 경우 이벤트를 정의하기 위해 이 활동을 구성할 수 있습니다. 이렇게 하려면 활동을 편집하고 **[!UICONTROL Expiration]** 탭을 클릭합니다. **[!UICONTROL Insert]** 단추를 클릭하여 이벤트를 만들고 구성합니다.

![](assets/edit_signal.png)

만료 구성은 [만료](../../workflow/using/defining-approvals.md)에 자세히 설명되어 있습니다.

**지연** 필드를 사용하면 원하는 단위로 만료 지연을 지정할 수 있습니다. [대기](../../workflow/using/wait.md)를 참조하십시오.

각 라인은 만료 유형을 나타내며 전환과 일치합니다.

![](assets/external_sign_diag.png)

