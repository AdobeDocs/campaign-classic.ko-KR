---
product: campaign
title: 추가 구성
description: Adobe Campaign Classic에서 트랜잭션 메시지를 보내는 추가 구성을 설정하는 방법에 대해 알아봅니다
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
TQID: 'https://experienceleague.adobe.com/TJ5R6T1pu5JQU5SaGoWRgZLG2m29TWWPVB8nniorRUg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 758d5159759b19f7ef32e8cc8f6237547599e727
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 2%
---
# 추가 구성 {#mc-additional-configurations}

이 페이지에서는 Campaign Classic v7의 트랜잭션 메시지에 대한 추가 구성을 다룹니다.

>[!NOTE]
>
>Campaign v7에서 v8로 전환하는 과정의 일부로 Campaign Classic 설명서 세트가 간소화 및 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다. 트랜잭션 메시지 이벤트 제거 및 기술 워크플로우에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/config/settings/transactional-msg-settings){target=_blank}를 참조하세요.
>
>[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/config/settings/transactional-msg-settings){target=_blank}

## 임계값 모니터링 {#monitoring-thresholds}

**메시지 센터 서비스 수준** 및 **메시지 센터 처리 시간** 보고서에 표시되는 표시기의 경고 임계값(주황색) 및 경고 임계값(빨간색)을 구성할 수 있습니다([트랜잭션 메시지 보고서 액세스](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"}(Campaign v8 설명서).

이렇게 하려면 아래 단계를 수행합니다.

1. **실행 인스턴스**&#x200B;에서 배포 마법사를 엽니다.

1. **[!UICONTROL Message Center]** 페이지로 이동합니다.

1. 화살표를 사용하여 임계값을 변경합니다.

   ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>큐에 대기 중인 이벤트 수가 Adobe Campaign 프로세스 모니터링 페이지의 [시스템 표시기](../../production/using/monitoring-processes.md#system-indicators) 섹션에 표시됩니다. 배포 마법사에 대한 자세한 내용은 [이 섹션](../../installation/using/deploying-an-instance.md#deployment-assistant)을 참조하세요.

## 기술 워크플로 {#technical-workflows}

트랜잭션 메시지 템플릿을 배포하기 전에 제어 인스턴스 및 다른 실행 인스턴스의 기술 워크플로우가 실제로 생성 및 시작되었는지 확인해야 합니다.

### 워크플로우 일정 보관

컨트롤 인스턴스에서 실행되는 **보관 워크플로** 일정을 수정하지 마십시오. 그렇지 않으면 실행 인스턴스에서 가져오는 일부 추적 데이터가 손실될 수 있습니다.

보관 워크플로 일정을 수정하는 경우 실행 인스턴스의 **추적 워크플로** 일정도 컨트롤 인스턴스의 보관 워크플로 일정과 일치하도록 변경해야 합니다.

## 멀티브랜딩 구성 {#configuring-multibranding}

이 섹션에서는 Adobe Campaign에서 트랜잭션 메시지에 대해 브랜드당 추적 및 미러 페이지 URL을 구성하는 한 가지 솔루션에 대해 설명합니다.

### 호환성 정보 {#compatibility-note}

이 레거시 브랜딩 구성은 Campaign v8에 도입된 새 [중앙 브랜딩](https://experienceleague.adobe.com/docs/campaign-web/v8/conf/branding/branding-gs.html?lang=ko){target="_blank"} 모델과 호환되지 않습니다.

기존 환경에서 이 레거시 구성을 사용하는 경우 이를 새 중앙 집중식 브랜딩 모델로 직접 마이그레이션할 수 없습니다. 새 시스템을 채택하려면 브랜딩 설정을 완전히 다시 구현해야 합니다.

### 필수 구성 요소 {#prerequisites}

* 모든 호스트를 인스턴스(`config-<instance>.xml`)의 구성 파일에 추가해야 합니다.
* 각 브랜드에는 하위 도메인을 할당해야 합니다.
* HTTPS 페이지에서 웹 추적이 수행되는 경우 모든 브랜드에 대해 HTTPS 인증서가 있어야 합니다.

멀티브랜딩을 구성하려면 실행 인스턴스와 제어 인스턴스를 모두 구성해야 합니다.

### 실행 인스턴스 {#execution-instance}

실행 인스턴스에서 아래 단계를 수행합니다.

1. 브랜드당 하나의 외부 계정을 만듭니다.

   >[!NOTE]
   >
   >[이 섹션](../../message-center/using/configuring-instances.md#control-instance)에서 실행 인스턴스 유형 외부 계정을 만드는 방법을 알아봅니다.

1. nms:extAccount 스키마를 확장하여 추적 URL 추가:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >[스키마 확장](../../configuration/using/extending-a-schema.md) 섹션에서 기존 스키마를 확장하는 방법을 알아보세요.

1. nms:extAccount 양식 수정:

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

이렇게 하려면 아래 단계를 수행합니다.

1. [실행 인스턴스](#execution-instance)에 정의된 내부 이름과 동일한 외부 계정을 브랜드당 하나씩 만듭니다(1단계).

1. 브랜드별 게재 템플릿을 만듭니다. [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html?lang=ko){target="_blank"}를 참조하세요.

1. 게재 템플릿의 **[!UICONTROL Properties]**&#x200B;에서 라우팅을 브랜드의 외부 계정으로 설정합니다.
