---
title: 기술 워크플로우
seo-title: 기술 워크플로우
description: 기술 워크플로우
seo-description: null
page-status-flag: never-activated
uuid: dfd1b180-86b5-4740-9bad-a0e210f433c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 2e648e63-06d2-4e8f-9934-066a41d18eac
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 기술 워크플로우{#technical-workflows}

트랜잭션 메시지 템플릿을 배포하기 전에 제어 인스턴스와 다른 실행 인스턴스의 기술 워크플로우가 실제로 만들어지고 시작되었는지 확인해야 합니다.

트랜잭션 메시지(메시지 센터)와 관련된 다양한 기술 워크플로우는 제어 인스턴스와 실행 인스턴스 간에 분류됩니다.

## 인스턴스 워크플로우 제어 {#control-instance-workflows}

제어 인스턴스에서 실행 인스턴스당 보관 워크플로우를 하나씩 만들어야 합니다. 그런 다음 관리 > 프로덕션 > 메시지 센터 **폴더에서 보관 워크플로우에 액세스할 수** 있습니다. 일단 만들어지면 보관 워크플로우가 자동으로 시작됩니다.

**분산 아키텍처**

하나 또는 여러 개의 실행 인스턴스가 등록된 경우 제어 인스턴스에서 각 **[!UICONTROL Message Center execution instance]** 외부 계정에 대해 보관 워크플로우를 하나씩 만들어야 합니다. 이 **[!UICONTROL Create the archiving workflow]** 단추를 클릭하여 워크플로우를 만들고 시작합니다.

![](assets/messagecenter_archiving_002.png)

**최소 아키텍처**

제어 및 실행 모듈이 동일한 인스턴스에 설치되면 배포 마법사를 사용하여 보관 워크플로우를 만들어야 합니다. 이 **[!UICONTROL Create the archiving workflow]** 단추를 클릭하여 워크플로우를 만들고 시작합니다.

![](assets/messagecenter_archiving_001.png)

## 실행 인스턴스 워크플로우 {#execution-instance-workflows}

실행 인스턴스에서 트랜잭션 메시징에 대한 기술 워크플로우는 관리 > 프로덕션 > 메시지 센터 **폴더에서 액세스할 수** 있습니다. 그냥 시작만 하면 돼 목록의 워크플로우는 다음과 같습니다.

* **[!UICONTROL Processing batch events]** (내부 이름:): **[!UICONTROL batchEventsProcessing]** 이 작업 과정을 사용하면 큐에서 일괄 처리 이벤트가 메시지 템플릿에 링크되기 전에 이를 분류할 수 있습니다.
* **[!UICONTROL Processing real time events]** (내부 이름:): **[!UICONTROL rtEventsProcessing]** 이 작업 과정을 사용하면 대기열에서 실시간 이벤트를 메시지 템플릿에 링크하기 전에 분류할 수 있습니다.
* **[!UICONTROL Update event status]** (내부 이름:): **[!UICONTROL updateEventStatus]** 이 워크플로우에서는 상태를 이벤트에 지정할 수 있습니다.

   다음 이벤트 상태를 사용할 수 있습니다.

   * **[!UICONTROL Pending]** :이벤트가 대기열에 있습니다. 메시지 템플릿이 아직 지정되지 않았습니다.
   * **[!UICONTROL Pending delivery]** :이벤트가 대기열에 있고 메시지 템플릿이 할당되어 전달에 의해 처리되는 중입니다.
   * **[!UICONTROL Sent]** :이 상태는 배달 로그에서 복사됩니다. 배달이 전송되었음을 의미합니다.
   * **[!UICONTROL Ignored by the delivery]** :이 상태는 배달 로그에서 복사됩니다. 배달이 무시되었음을 의미합니다.
   * **[!UICONTROL Delivery failed]** :이 상태는 배달 로그에서 복사됩니다. 배달이 실패했다는 뜻입니다.
   * **[!UICONTROL Event not taken into account]** :이벤트를 메시지 템플릿에 연결할 수 없습니다. 이벤트가 처리되지 않습니다.

