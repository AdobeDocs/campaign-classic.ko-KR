---
product: campaign
title: 외부 신호
description: 외부 신호 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# 외부 신호{#external-signal}



다음 **외부 신호** 활동을 사용하면 워크플로우에서 일정으로 작업 집합 실행을 트리거할 수 있습니다.

&#39;외부 신호&#39; 작업이 활성화되면 지정된 기간이 끝날 때까지 또는 무기한 일시 중지됩니다. 해당 전환은 SOAP 호출에 의해 활성화됩니다 **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** 다음 **[!UICONTROL complete]** 매개 변수를 사용하면 작업을 완료할 수 있으므로 후속 호출에 반응하지 않습니다.

PostEvent 함수에 대한 자세한 내용은 SOAP 호출과 관련된 온라인 설명서를 참조하십시오.

신호가 수신되지 않은 경우 이벤트를 정의하기 위해 이 활동을 구성할 수 있습니다. 이렇게 하려면 활동을 편집하고 **[!UICONTROL Expiration]** 탭. 다음을 클릭합니다. **[!UICONTROL Insert]** 버튼을 클릭하여 이벤트를 만들고 구성합니다.

![](assets/edit_signal.png)

만료 구성에 대해서는 다음에서 자세히 설명합니다. [만료](defining-approvals.md).

다음 **지연** 필드에서는 원하는 단위로 만료 지연을 지정할 수 있습니다. 다음을 참조하십시오 [대기](wait.md).

각 행은 만료 유형을 나타내며 전환과 일치합니다.

![](assets/external_sign_diag.png)
