---
product: campaign
title: 모바일 앱 채널 시작
description: Adobe Campaign에서 모바일 앱 채널 시작
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 10%

---

# 모바일 앱 채널 시작{#about-mobile-app-channel}

**모바일 앱 채널**&#x200B;을 사용하면 Adobe Campaign 플랫폼을 사용하여 앱을 통해 iOS 및 Android 터미널에 개인화된 푸시 알림을 보낼 수 있습니다.

두 가지 게재 채널을 사용할 수 있습니다.

* Apple 모바일 장치로 알림을 전송할 수 있는 iOS 채널입니다.

  ![](assets/nmac_intro_2.png)

* Android 모바일 장치로 데이터 메시지를 보낼 수 있는 Android 채널입니다.

  ![](assets/nmac_intro_1.png)

  >[!IMPORTANT]
  >
  >Android FCM(Firebase Cloud Messaging) 서비스에 대한 몇 가지 중요한 변경 사항은 2024년에 릴리스될 예정이며 Adobe Campaign 구현에 영향을 미칠 수 있습니다. 이 변경 사항을 지원하려면 Android 푸시 메시지에 대한 구독 서비스 구성을 업데이트해야 할 수 있습니다. 이미 확인하고 조치를 취할 수 있습니다. 이 [Adobe Campaign v8 기술 정보](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=ko){target="_blank"}에서 자세히 알아보세요.

이 두 채널에 해당하는 두 가지 게재 활동이 캠페인 워크플로우에 있습니다. 트랜잭션 메시지에는 두 개의 트랜잭션 메시지 템플릿도 사용할 수 있습니다.

![](assets/nmac_intro_3.png)


사용자가 애플리케이션 컨텍스트와 일치하는 화면을 표시하기 위해 알림을 활성화할 때 대한 애플리케이션 동작을 정의할 수 있습니다. 예제:

* 고객에게 택배가 창고를 떠났음을 알리는 알림이 전송됩니다. 알림을 활성화하면 게재 관련 정보가 포함된 페이지가 열립니다.
* 사용자가 장바구니에 항목을 추가했지만 구매를 완료하지 않고 애플리케이션을 종료했습니다. 장바구니가 중단되었음을 알리는 알림이 전송됩니다. 알림을 활성화하면 항목이 화면에 표시됩니다.

>[!CAUTION]
>
>* 모바일 애플리케이션으로 전송된 알림이 Apple(Apple 푸시 알림 서비스) 및 Google(Firebase Cloud Messaging)에서 지정한 사전 요구 사항 및 조건을 준수하는지 확인해야 합니다.
>* 경고: 일부 국가에서는 수집된 데이터 유형 모바일 애플리케이션과 처리 목적을 사용자에게 알려야 합니다. 당신은 법률을 확인해야 합니다.

**[!UICONTROL NMAC opt-out management]**(mobileAppOptOutMgt) 워크플로는 모바일 장치에서 알림 구독 취소를 업데이트합니다. 이 워크플로에 대한 자세한 내용은 [기술 워크플로 목록](../../workflow/using/about-technical-workflows.md)을 참조하세요.

Adobe Campaign은 HTTP/2 APNs와 호환됩니다. 구성 단계에 대한 자세한 내용은 [이 섹션](configuring-the-mobile-application.md) 섹션을 참조하십시오.

게재를 만드는 방법에 대한 전체 정보는 [이 섹션](steps-about-delivery-creation-steps.md)을 참조하세요.


## 푸시 알림 채널 구성 {#push-notification-configuration}

Adobe Campaign을 사용하여 푸시 알림을 전송하려면 먼저 환경과 앱을 구성해야 합니다. Adobe Campaign을 사용하여 푸시 알림 전송을 시작하기 전에 모바일 앱과 Adobe Experience Platform의 태그에 대한 구성 및 통합이 제대로 되어 있는지 확인해야 합니다. Adobe Experience Platform Mobile SDK은 Android 및 iOS 호환 SDK를 통해 모바일에 대한 클라이언트측 통합 API를 제공합니다. SDK 구성은 데이터 수집 UI를 통해 관리되므로 유연한 구성과 확장 가능한 규칙 기반 통합을 이용할 수 있습니다. 자세한 내용은 [Adobe Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/push/push-settings)를 참조하세요.


## 데이터 경로 {#data-path}

다음 스키마에서는 모바일 애플리케이션이 Adobe Campaign과 데이터를 교환할 수 있는 단계를 자세히 설명합니다. 이 프로세스에는 다음 세 가지 엔티티가 포함됩니다.

* 모바일 애플리케이션
* 알림 서비스: Apple용 APNs(Apple 푸시 알림 서비스) 및 Android용 FCM(Firebase 클라우드 메시징)
* Adobe Campaign

알림 프로세스의 세 가지 주요 단계는 Adobe Campaign 애플리케이션 등록(구독 컬렉션), 게재 및 추적입니다.

### 1단계: 구독 컬렉션 {#step-1--subscription-collection}

모바일 애플리케이션은 App Store 또는 Google Play에서 사용자가 다운로드합니다. 이 응용 프로그램에는 연결 설정(iOS 인증서 및 Android용 프로젝트 키)과 통합 키가 포함되어 있습니다. 구성에 따라 애플리케이션을 처음 열면 등록 정보(@userKey: 이메일 또는 계정 번호)를 입력하라는 메시지가 표시될 수 있습니다. 동시에 애플리케이션은 알림 ID(푸시 ID)를 수집하기 위해 알림 서비스에 질문합니다. 이 모든 정보(연결 설정, 통합 키, 알림 식별자, userKey)는 Adobe Campaign으로 전송됩니다.

![](assets/nmac_register_view.png)

### 2단계: 게재 {#step-2--delivery}

마케터는 애플리케이션 구독자를 타겟팅합니다. 게재 프로세스는 연결 설정을 알림 서비스(Android용 iOS 인증서 및 프로젝트 키), 알림 ID(푸시 ID) 및 알림 콘텐츠로 보냅니다. 통지 서비스는 타겟팅된(targeted) 단말기들로 통지들을 전송한다.

Adobe Campaign에서는 다음 정보를 사용할 수 있습니다.

* Android만 해당: 알림을 표시한 장치 수(노출 횟수)
* Android 및 iOS: 알림 클릭 수

![](assets/nmac_delivery_view.png)

Adobe Campaign 서버는 iOS HTTP/2 커넥터용 443 포트의 APNs 서버에 연결할 수 있어야 합니다.

제대로 작동하는지 확인하려면 다음 명령을 사용합니다.

* 테스트의 경우:

  ```
  api.development.push.apple.com:443
  ```

* 프로덕션:

  ```
  api.push.apple.com:443
  ```

iOS HTTP/2 커넥터를 사용하면 MTA 및 웹 서버가 포트 443의 APNs에 연결할 수 있어야 합니다.

프록시를 통해 iOS HTTP/2 커넥터를 사용해야 하는 경우 이 [페이지](../../installation/using/file-res-management.md#proxy-connection-configuration)를 참조하세요.
