---
title: 외부 신호
seo-title: 외부 신호
description: 외부 신호
seo-description: null
page-status-flag: never-activated
uuid: dbe6624a-70cf-4ac4-adfd-bc72db9bb3f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 3739593f-056c-4165-87ef-63c812bd3c43
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 외부 신호{#external-signal}

외부 **신호** 활동을 사용하면 워크플로우의 작업 세트 실행을 일정에 맞게 트리거할 수 있습니다.

&#39;외부 신호&#39; 작업이 활성화되면 무한히 또는 지정된 기간이 끝날 때까지 일시 중지됩니다. SOAP 호출 PostEvent(sessionToken, workflowId, **활동, 전환, 매개 변수, 완료)에 의해 전환이 활성화됩니다.** 이 **[!UICONTROL complete]** 매개 변수를 사용하면 작업이 완료되므로 후속 호출에 응답하지 않습니다.

PostEvent 함수에 대한 자세한 내용은 SOAP 호출에 대한 온라인 설명서를 참조하십시오.

수신되지 않은 경우 이벤트를 정의하기 위해 이 활동을 구성할 수 있습니다. 이렇게 하려면 활동을 편집하고 **[!UICONTROL Expiration]** 탭을 클릭합니다. 이벤트를 만들고 구성하려면 **[!UICONTROL Insert]** 단추를 클릭합니다.

![](assets/edit_signal.png)

만료에 대한 구성은 만료에 [자세히 설명되어 있습니다](../../workflow/using/executing-a-workflow.md#expirations).

지연 **필드를** 사용하면 원하는 단위로 만료 지연을 지정할 수 있습니다. 기다리기를 [참조하십시오](../../workflow/using/wait.md).

각 줄은 만료 유형을 나타내며 전환과 일치합니다.

![](assets/external_sign_diag.png)

