---
solution: Campaign Classic
product: campaign
title: 기술 워크플로우
description: 기술 워크플로우
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 11%

---


# 기술 워크플로우{#technical-workflows}

트랜잭션 메시지 템플릿을 배포하기 전에 제어 인스턴스의 기술 워크플로우와 다른 실행 인스턴스가 실제로 만들어지고 시작되었는지 확인해야 합니다.

트랜잭션 메시지(메시지 센터)와 관련된 다양한 기술 작업 과정은 제어 인스턴스와 실행 인스턴스 간에 분류됩니다.

## 제어 인스턴스 워크플로 {#control-instance-workflows}

제어 인스턴스에서 실행 인스턴스가 하나 이상 등록되어 있는지 또는 여러 개 등록되어 있는지 관계없이 각 **[!UICONTROL Message Center execution instance]** 외부 계정에 대해 보관 워크플로우를 하나씩 만들어야 합니다. **[!UICONTROL Create the archiving workflow]** 단추를 클릭하여 워크플로우를 만들고 시작합니다.

![](assets/messagecenter_archiving_002.png)

그런 다음 **관리 > 프로덕션 > 메시지 센터** 폴더에서 이러한 워크플로우에 액세스할 수 있습니다. 생성되면 보관 워크플로우가 자동으로 시작됩니다.

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

## 실행 인스턴스 워크플로 {#execution-instance-workflows}

실행 인스턴스에서 트랜잭션 메시징에 대한 기술 워크플로우는 **관리 > 프로덕션 > 메시지 센터** 폴더에서 액세스할 수 있습니다. 그냥 시작만 하면 돼 목록의 워크플로우는 다음과 같습니다.

* **[!UICONTROL Processing batch events]** (내부 이름: **[!UICONTROL batchEventsProcessing]** ):이 워크플로우에서는 메시지 템플릿에 링크되기 전에 대기열에서 일괄 처리 이벤트를 분류할 수 있습니다.
* **[!UICONTROL Processing real time events]** (내부 이름: **[!UICONTROL rtEventsProcessing]** ):이 워크플로에서는 메시지 템플릿에 링크되기 전에 대기열에서 실시간 이벤트를 분류할 수 있습니다.
* **[!UICONTROL Update event status]** (내부 이름: **[!UICONTROL updateEventStatus]** ):이 워크플로우에서는 상태를 이벤트에 지정할 수 있습니다.

   다음 이벤트 상태를 사용할 수 있습니다.

   * **[!UICONTROL Pending]** :이벤트가 큐에 있습니다. 메시지 템플릿이 아직 할당되지 않았습니다.
   * **[!UICONTROL Pending delivery]** :이벤트가 큐에 있고, 메시지 템플릿이 할당되어 배달에서 처리 중입니다.
   * **[!UICONTROL Sent]** :이 상태는 배달 로그에서 복사됩니다. 배달이 전송되었음을 의미합니다.
   * **[!UICONTROL Ignored by the delivery]** :이 상태는 배달 로그에서 복사됩니다. 게재가 무시되었다는 뜻입니다.
   * **[!UICONTROL Delivery failed]** :이 상태는 배달 로그에서 복사됩니다. 게재에 실패했다는 뜻입니다.
   * **[!UICONTROL Event not taken into account]** :이벤트를 메시지 템플릿에 연결할 수 없습니다. 이벤트가 처리되지 않습니다.

