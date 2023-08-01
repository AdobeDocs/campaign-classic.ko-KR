---
product: campaign
title: 추가 구성
description: Adobe Campaign Classic에서 트랜잭션 메시지를 보내는 추가 구성을 설정하는 방법에 대해 알아봅니다
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '754'
ht-degree: 7%

---

# 추가 구성 {#mc-additional-configurations}



## 임계값 모니터링 {#monitoring-thresholds}

다음에 표시되는 표시기의 경고 임계값(주황색) 및 경고 임계값(빨간색)을 구성할 수 있습니다. **메시지 센터 서비스 수준** 및 **메시지 센터 처리 시간** 보고서(참조: [트랜잭션 메시지 보고서 액세스](../../message-center/using/about-transactional-messaging-reports.md)).

이렇게 하려면 아래 단계를 수행합니다:

1. 에서 배포 마법사를 엽니다. **실행 인스턴스**.

1. 로 이동 **[!UICONTROL Message Center]** 페이지를 가리키도록 업데이트하는 중입니다.

1. 화살표를 사용하여 임계값을 변경합니다.

   ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>대기열에 보류 중인 이벤트 수가 [시스템 지표](../../production/using/monitoring-processes.md#system-indicators) Adobe Campaign 섹션에 있는 마지막 항목이 될 필요가 없습니다. 배포 마법사에 대한 자세한 내용은 [이 섹션](../../installation/using/deploying-an-instance.md#deployment-wizard).

## 이벤트 제거 {#purging-events}

다음을 사용할 수 있습니다. [배포 마법사](../../production/using/database-cleanup-workflow.md#deployment-wizard) 데이터베이스에 데이터를 저장할 기간을 구성합니다.

이벤트 삭제는 다음을 통해 자동으로 수행됩니다. [데이터베이스 정리 워크플로우](../../production/using/database-cleanup-workflow.md). 이 워크플로우는 실행 인스턴스에 수신 및 저장된 이벤트와 제어 인스턴스에 보관된 이벤트를 삭제합니다.

화살표를 적절하게 사용하여 제거 설정을 변경합니다.

컨트롤 인스턴스의 이벤트 제거 설정:

![](assets/messagecenter_delete_events_001.png)

실행 인스턴스에 대한 이벤트 제거 설정:

![](assets/messagecenter_delete_events_002.png)

데이터베이스 정리 워크플로우에 대한 자세한 내용은 [이 섹션](../../production/using/database-cleanup-workflow.md).


## 기술 워크플로우 {#technical-workflows}

트랜잭션 메시지 템플릿을 배포하기 전에 제어 인스턴스 및 다른 실행 인스턴스의 기술 워크플로우가 실제로 생성 및 시작되었는지 확인해야 합니다.

트랜잭션 메시지(메시지 센터)와 관련된 다양한 기술 워크플로는 제어 인스턴스와 실행 인스턴스 간에 분류됩니다.

### 인스턴스 워크플로 제어 {#control-instance-workflows}

제어 인스턴스에서는 실행 인스턴스가 하나 또는 여러 개 등록되었는지 여부에 관계없이 각 인스턴스에 대해 하나의 보관 워크플로우를 만들어야 합니다 **[!UICONTROL Message Center execution instance]** 외부 계정입니다. 다음을 클릭합니다. **[!UICONTROL Create the archiving workflow]** 단추를 클릭하여 워크플로우를 만들고 시작합니다.

![](assets/messagecenter_archiving_002.png)

그런 다음 워크플로우에서에 액세스할 수 있습니다 **관리 > 프로덕션 > 메시지 센터** 폴더를 삭제합니다. 워크플로우가 만들어지면 자동으로 보관 워크플로가 시작됩니다.

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

### 실행 인스턴스 워크플로 {#execution-instance-workflows}

실행 인스턴스에서 트랜잭션 메시지를 위한 기술 워크플로우에 액세스할 수 있습니다. **관리 > 프로덕션 > 메시지 센터** 폴더를 삭제합니다. 그냥 시작하기만 하면 돼 목록의 워크플로는 다음과 같습니다.

* **[!UICONTROL Processing batch events]** (내부 이름: **[!UICONTROL batchEventsProcessing]** ): 이 워크플로우를 사용하면 메시지 템플릿에 연결되기 전에 대기열의 일괄 처리 이벤트를 분류할 수 있습니다.
* **[!UICONTROL Processing real time events]** (내부 이름: **[!UICONTROL rtEventsProcessing]** ): 이 워크플로우를 사용하면 메시지 템플릿에 연결되기 전에 대기열의 실시간 이벤트를 분류할 수 있습니다.
* **[!UICONTROL Update event status]** (내부 이름: **[!UICONTROL updateEventStatus]** ): 이 워크플로우를 사용하면 이벤트에 상태를 지정할 수 있습니다.

  다음 이벤트 상태를 사용할 수 있습니다.

   * **[!UICONTROL Pending]** : 이벤트가 큐에 있습니다. 메시지 템플릿이 아직 할당되지 않았습니다.
   * **[!UICONTROL Pending delivery]** : 이벤트가 큐에 있고 메시지 템플릿이 할당되어 게재에 의해 처리되는 중입니다.
   * **[!UICONTROL Sent]** : 이 상태는 게재 로그에서 복사됩니다. 게재가 전송되었음을 의미합니다.
   * **[!UICONTROL Ignored by the delivery]** : 이 상태는 게재 로그에서 복사됩니다. 게재가 무시되었다는 뜻입니다.
   * **[!UICONTROL Delivery failed]** : 이 상태는 게재 로그에서 복사됩니다. 게재에 실패했다는 뜻입니다.
   * **[!UICONTROL Event not taken into account]** : 이벤트를 메시지 템플릿에 연결할 수 없습니다. 이벤트가 처리되지 않습니다.

## 멀티브랜딩 구성 {#configuring-multibranding}

이 섹션에서는 Adobe Campaign에서 트랜잭션 메시지에 대해 브랜드당 추적 및 미러 페이지 URL을 구성하는 한 가지 솔루션에 대해 설명합니다.

### 전제 조건 {#prerequisites}

* 모든 호스트는 인스턴스의 구성 파일에 추가해야 합니다(`config-<instance>.xml`).
* 각 브랜드에는 하위 도메인을 할당해야 합니다.
* HTTPS 페이지에서 웹 추적이 수행되는 경우 모든 브랜드에 대해 HTTPS 인증서가 있어야 합니다.

멀티브랜딩을 구성하려면 실행 인스턴스와 제어 인스턴스를 모두 구성해야 합니다.

### 실행 인스턴스 {#execution-instance}

실행 인스턴스에서 아래 단계를 수행합니다.

1. 브랜드당 하나의 외부 계정을 만듭니다.

   >[!NOTE]
   >
   >에서 실행 인스턴스 유형 외부 계정을 만드는 방법을 알아봅니다. [이 섹션](../../message-center/using/configuring-instances.md#control-instance).

1. nms:extAccount 스키마를 확장하여 추적 URL 추가:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >에서 기존 스키마를 확장하는 방법 알아보기 [스키마 확장](../../configuration/using/extending-a-schema.md) 섹션.

1. nms:extAccount 양식을 수정합니다.

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. 글로벌 옵션 대신 외부 계정을 사용하도록 NmsTracking_OpenFormula 및 NmsTracking_ClickFormula 옵션을 수정합니다.

   이렇게 하려면 다음을 바꾸십시오.

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   포함:

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >이러한 변경 사항은 업그레이드 시 충돌로 이어질 수 있습니다. 이러한 수식을 새 버전과 수동으로 병합해야 할 수 있습니다.

### 컨트롤 인스턴스 {#control-instance}

제어 인스턴스에서는 게재 템플릿과 외부 계정을 연결해야 합니다.

이렇게 하려면 아래 단계를 수행합니다:

1. 에 정의된 것과 동일한 내부 이름을 사용하는 브랜드당 하나의 외부 계정을 만듭니다. [실행 인스턴스](#execution-instance) (1단계)

1. 브랜드당 하나의 기본 게재 템플릿을 만듭니다.

   >[!NOTE]
   >
   >    에서 게재 템플릿을 만드는 방법을 알아봅니다 [이 섹션](../../delivery/using/creating-a-delivery-template.md#creating-a-new-template).

1. 게재 템플릿의 **[!UICONTROL Properties]**&#x200B;를 클릭하고 라우팅을 브랜드의 외부 계정으로 설정합니다.
