---
title: 다중 브랜딩 구성
seo-title: 다중 브랜딩 구성
description: 다중 브랜딩 구성
seo-description: null
page-status-flag: never-activated
uuid: 61b4235c-da03-4da8-b14b-7ffb12c8d4c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 907d82c8-9262-4952-b8df-21144dd55824
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d5eac80743d4cc82cdf55aa9287e8bb4fcc84356

---


# 다중 브랜딩 구성{#configuring-multibranding}

이 섹션에서는 Adobe Campaign의 트랜잭션 메시지에 대한 브랜드당 추적 및 페이지 URL을 미러링하는 하나의 솔루션에 대해 설명합니다.

## 사전 요구 사항 {#prerequisites}

* 모든 호스트를 인스턴스의 구성 파일(`config-<instance>.xml`)에 추가해야 합니다.
* 각 브랜드에 하위 도메인이 할당되어야 합니다.
* 웹 추적이 HTTPS 페이지에서 이루어지는 경우 모든 브랜드에 대한 HTTPS 인증서가 있어야 합니다.

## 일반적인 프로세스 {#typical-process}

다중 브랜딩을 구성하려면 실행 인스턴스와 제어 인스턴스를 모두 구성해야 합니다. 실행 인스턴스에서 아래 단계를 수행합니다.

1. 브랜드당 하나의 외부 계정을 만들 수 있습니다.

   >[!NOTE]
   >
   >실행 인스턴스 유형 외부 계정 만들기는 제어 인스턴스 [섹션에](../../message-center/using/creating-a-shared-connection.md#control-instance) 표시됩니다.

1. nms:extAccount 스키마를 확장하여 추적 URL을 추가합니다.

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >기존 스키마 확장은 스키마 확장 [섹션에](../../configuration/using/extending-a-schema.md) 표시됩니다.

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

1. 전역 옵션 대신 외부 계정을 사용하도록 NmsTracking_OpenFormula 및 NmsTracking_ClickFormula 옵션을 수정합니다.

   이렇게 하려면 다음을 바꾸십시오.

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   with:

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!CAUTION]
   >
   >이러한 변경 사항은 업그레이드 시 충돌을 초래할 수 있습니다. 이러한 수식을 새 버전과 수동으로 병합해야 할 수도 있습니다.

제어 인스턴스에서 배달 템플릿과 외부 계정을 연결해야 합니다. 이렇게 하려면 다음을 수행해야 합니다.

1. 1단계에서 정의된 것과 동일한 내부 이름으로 브랜드당 하나의 외부 계정을 만듭니다.
1. 브랜드당 하나의 기본 제공 템플릿을 만들 수 있습니다.
1. 배달 템플릿의 **[!UICONTROL Properties]** 에서 라우팅을 브랜드의 외부 계정으로 설정합니다.

