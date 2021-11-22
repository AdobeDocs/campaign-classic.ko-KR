---
product: campaign
title: Adobe Campaign Classic의 모바일 앱 채널 기본 정보
description: 이 섹션에서는 Adobe Campaign Classic의 모바일 앱 채널에 대한 일반 정보를 제공합니다.
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 1%

---

# 모바일 앱 채널 시작{#about-mobile-app-channel}

![](../../assets/common.svg)

다음 **모바일 앱 채널** Adobe Campaign 플랫폼을 사용하여 앱을 통해 iOS 및 Android 단말기로 개인화된 푸시 알림을 전송할 수 있습니다.

>[!CAUTION]
>
>이 문서에서는 모바일 애플리케이션을 Adobe Campaign 플랫폼과 통합하는 프로세스에 대해 자세히 설명합니다. 모바일 애플리케이션을 만드는 방법 또는 알림 관리를 위해 구성하는 방법에 대한 정보는 제공하지 않습니다. 자세한 내용은 공식 Apple 를 참조하십시오 [설명서](https://developer.apple.com/) 및 Android [설명서](https://developer.android.com/index.html).

두 개의 게재 채널을 사용할 수 있습니다.

* Apple 모바일 장치로 알림을 전송할 수 있는 iOS 채널입니다.

   ![](assets/nmac_intro_2.png)

* Android 모바일 장치로 데이터 메시지를 보낼 수 있는 Android 채널입니다.

   ![](assets/nmac_intro_1.png)

해당 두 채널에 해당하는 캠페인 워크플로우에는 두 개의 게재 활동이 있습니다.

![](assets/nmac_intro_3.png)


>[!NOTE]
>
>트랜잭션 메시징에는 두 개의 트랜잭션 메시지 템플릿도 사용할 수 있습니다.

사용자가 애플리케이션 컨텍스트와 일치하는 화면을 표시하기 위해 알림을 활성화하면 의 애플리케이션 동작을 정의할 수 있습니다. 예제:

* 고객이 소포가 창고를 벗어났다는 것을 알리는 알림이 보내진다. 알림을 활성화하면 게재 관련 정보가 있는 페이지가 열립니다.
* 사용자가 장바구니에 항목을 추가했지만 구매를 완료하지 않고 애플리케이션을 종료했습니다. 알림이 전송되어 카트가 중단되었음을 나타냅니다. 알림이 활성화되면 항목이 화면에 표시됩니다.

>[!CAUTION]
>
>* 모바일 애플리케이션에 전송되는 알림이 Apple(Apple Push Notification Service) 및 Google(Firebase Cloud Messaging)에서 지정한 사전 요구 사항 및 조건을 준수하는지 확인해야 합니다.
>* 경고: 일부 국가에서는 수집된 데이터 유형 모바일 애플리케이션 및 처리 목적을 사용자에게 알려야 합니다. 입법을 확인해야 합니다.


다음 **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) 워크플로우는 모바일 장치에서 알림 구독 취소를 업데이트합니다. 이 워크플로우에 대한 자세한 내용은 [기술 워크플로우 목록](../../workflow/using/about-technical-workflows.md).

Adobe Campaign은 HTTP/2 APNs와 호환됩니다. 구성 단계에 대한 자세한 내용은 [이 섹션](configuring-the-mobile-application.md) 섹션을 참조하십시오.

게재를 만드는 방법에 대한 글로벌 정보는 [이 섹션](steps-about-delivery-creation-steps.md).

## 데이터 경로 {#data-path}

다음 스키마에서는 모바일 애플리케이션에서 Adobe Campaign과 데이터를 교환할 수 있도록 하는 단계를 자세히 설명합니다. 이 프로세스에는 다음의 세 가지 엔티티가 포함됩니다.

* 모바일 애플리케이션
* 알림 서비스: Android용 Apple 및 FCM(Firebase Cloud Messaging)용 APNs(Apple 푸시 알림 서비스)
* Adobe Campaign

알림 프로세스의 세 가지 주요 단계는 다음과 같습니다. Adobe Campaign(구독 수집), 게재 및 추적에서 애플리케이션 등록.

### 1단계: 구독 컬렉션 {#step-1--subscription-collection}

모바일 애플리케이션은 App Store 또는 Google Play에서 사용자가 다운로드합니다. 이 응용 프로그램에는 연결 설정(Android용 iOS 인증서 및 프로젝트 키) 및 통합 키가 포함되어 있습니다. 응용 프로그램을 처음 열 때(구성에 따라) 사용자에게 등록 정보를 입력하라는 메시지가 표시됩니다(@userKey: 예를 들어 이메일 또는 계정 번호입니다.) 동시에 애플리케이션은 알림 ID(푸시 ID)를 수집하기 위해 알림 서비스에 질문을 합니다. 이 모든 정보(연결 설정, 통합 키, 알림 식별자, userKey)는 Adobe Campaign으로 전송됩니다.

![](assets/nmac_register_view.png)

### 2단계: 배달 {#step-2--delivery}

마케터는 애플리케이션 구독자를 타겟팅합니다. 게재 프로세스는 알림 서비스(Android용 iOS 인증서 및 프로젝트 키), 알림 ID(푸시 ID) 및 알림 컨텐츠에 연결 설정을 전송합니다. 알림 서비스는 타깃팅된 단말로 알림을 보냅니다.

다음 정보는 Adobe Campaign에서 확인할 수 있습니다.

* Android만 해당: 알림(노출 횟수)을 표시한 장치 수
* Android 및 iOS: 알림 클릭 수

![](assets/nmac_delivery_view.png)

Adobe Campaign 서버는 iOS HTTP/2 커넥터용 443 포트의 APNs 서버에 연결할 수 있어야 합니다.

올바르게 작동하는지 확인하려면 다음 명령을 사용합니다.

* 테스트의 경우:

   ```
   api.development.push.apple.com:443
   ```

* 프로덕션:

   ```
   api.push.apple.com:443
   ```

iOS HTTP/2 커넥터를 사용하면 MTA 및 웹 서버가 포트 443의 APNs에 연결할 수 있어야 합니다.

프록시를 통해 iOS HTTP/2 커넥터를 사용해야 하는 경우 다음을 참조하십시오 [페이지](../../installation/using/file-res-management.md#proxy-connection-configuration).
