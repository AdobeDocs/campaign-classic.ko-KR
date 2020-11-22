---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic의 모바일 앱 채널 정보
description: 이 섹션에서는 Adobe Campaign Classic의 모바일 앱 채널과 관련된 일반 정보를 제공합니다.
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 5%

---


# 모바일 앱 채널 기본 정보{#about-mobile-app-channel}

>[!CAUTION]
>
>이 문서에서는 모바일 애플리케이션을 Adobe Campaign 플랫폼과 통합하는 프로세스에 대해 자세히 설명합니다. 모바일 애플리케이션을 만드는 방법 또는 알림을 관리하기 위해 구성하는 방법에 대한 정보는 제공하지 않습니다. 자세한 내용은 공식 Apple [문서](https://developer.apple.com/) 및 Android [설명서를 참조하십시오](https://developer.android.com/index.html).

아래 섹션에서는 모바일 앱 채널에 맞는 정보를 제공합니다.

배달을 만드는 방법에 대한 자세한 내용은[이 섹션을 참조하십시오](../../delivery/using/steps-about-delivery-creation-steps.md).

모바일 **앱 채널을** 사용하면 Adobe Campaign 플랫폼을 사용하여 앱을 통해 iOS 및 Android 터미널에 개인화된 알림을 전송할 수 있습니다. 두 개의 전달 채널을 사용할 수 있습니다.

* Apple 모바일 장치에 알림을 보낼 수 있는 iOS 채널.

   ![](assets/nmac_intro_2.png)

* Android 모바일 장치로 데이터 메시지를 전송할 수 있는 Android 채널

   ![](assets/nmac_intro_1.png)

이러한 두 채널에 해당하는 캠페인 워크플로우에는 두 개의 배달 활동이 있습니다.

![](assets/nmac_intro_3.png)

>[!NOTE]
>
>트랜잭션 메시징에는 두 가지 트랜잭션 메시지 템플릿을 사용할 수도 있습니다.

사용자가 알림을 활성화하여 응용 프로그램 컨텍스트와 일치하는 화면을 표시하는 응용 프로그램 동작을 정의할 수 있습니다. 예제:

* 소포가 창고를 나갔다는 통보를 고객에게 보내왔다. 알림을 활성화하면 게재 관련 정보가 있는 페이지가 열립니다.
* 사용자가 장바구니에 품목을 추가했지만 구매를 완료하지 않고 애플리케이션을 떠났습니다. 카트가 포기되었다는 알림이 발송됩니다. 알림을 활성화하면 항목이 화면에 표시됩니다.

>[!CAUTION]
>
>* 모바일 응용 프로그램으로 보낸 알림이 Apple(Apple Push Notification 서비스) 및 Google(Firebase Cloud Messaging)에서 지정한 사전 요구 사항 및 조건을 충족하는지 확인해야 합니다.
>* 경고:일부 국가에서는 수집된 데이터 유형 모바일 응용 프로그램과 처리 목적을 사용자에게 알려야 합니다. 입법을 확인해야 합니다


(mobileAppOptOutMgt) **[!UICONTROL NMAC opt-out management]** 작업 과정은 모바일 장치에서 알림 구독 취소를 업데이트합니다. For more information on this workflow, refer to the [Workflows guide](../../workflow/using/mobile-app-channel.md).

Adobe Campaign은 바이너리 및 HTTP/2 APN과 호환됩니다. 구성 단계에 대한 자세한 내용은 Adobe Campaign에서 [모바일 애플리케이션 구성 섹션을](../../delivery/using/configuring-the-mobile-application.md) 참조하십시오.

## 데이터 경로 {#data-path}

다음 스키마는 모바일 응용 프로그램이 Adobe Campaign과 데이터를 교환할 수 있도록 하는 단계를 자세히 설명합니다. 이 프로세스에는 다음 세 개의 개체가 포함됩니다.

* 모바일 애플리케이션
* 알림 서비스:Apple 및 Android용 FCM(Firebase Cloud Messaging)용 APNs(Apple Push Notification 서비스)
* Adobe Campaign

알림 프로세스의 세 가지 주요 단계는 다음과 같습니다.adobe campaign(구독 컬렉션), 배송 및 추적에서 애플리케이션 등록

### 1단계:구독 컬렉션 {#step-1--subscription-collection}

모바일 응용 프로그램은 사용자가 App Store 또는 Google Play에서 다운로드됩니다. 이 응용 프로그램에는 연결 설정(Android용 iOS 인증서 및 프로젝트 키)과 통합 키가 포함되어 있습니다. 응용 프로그램을 처음 열 때(구성에 따라) 사용자에게 등록 정보(@userKey:이메일 또는 계정 번호 참조). 동시에 응용 프로그램은 알림 ID(푸시 ID)를 수집하기 위해 알림 서비스에 질문을 합니다. 이 모든 정보(연결 설정, 통합 키, 알림 식별자, userKey)는 Adobe Campaign으로 전송됩니다.

![](assets/nmac_register_view.png)

### 2단계:전달 {#step-2--delivery}

마케터는 애플리케이션 가입자를 타깃팅합니다. 배달 프로세스는 알림 서비스(Android용 iOS 인증서 및 프로젝트 키), 알림 ID(푸시 ID) 및 알림의 컨텐츠로 연결 설정을 보냅니다. 알림 서비스는 타깃팅된 터미널에 알림을 보냅니다.

다음 정보는 Adobe Campaign에서 확인할 수 있습니다.

* Android만 해당:알림을 표시한 장치 수(노출 수)
* Android 및 iOS:알림에 대한 클릭 수

![](assets/nmac_delivery_view.png)

Adobe Campaign 서버는 다음 포트에서 APNs 서버에 연결할 수 있어야 합니다.

* iOS 이진 커넥터에 대한 2195(전송) 및 2186(피드백 서비스)
* iOS HTTP/2 커넥터용 443

   >[!NOTE]
   >
   > Campaign 20.3 릴리스부터 iOS 레거시 바이너리 커넥터는 사용되지 않습니다. 이 커넥터를 사용하는 경우 그에 따라 구현을 조정해야 합니다. [자세히 알아보기](https://helpx.adobe.com/kr/campaign/kb/migrate-to-apns-http2.html)

제대로 작동하는지 확인하려면 다음 명령을 사용하십시오.

* 테스트의 경우:

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* 제작 중:

   ```
   telnet gateway.push.apple.com
   ```

iOS 이진 커넥터를 사용하는 경우 MTA 및 웹 서버가 포트 2195(전송)의 APN에 연결할 수 있어야 하며, 워크플로우 서버는 포트 2196(피드백 서비스)의 APNs에 연결할 수 있어야 합니다.

iOS HTTP/2 커넥터를 사용하는 경우 MTA, 웹 서버 및 워크플로우 서버가 포트 443의 APNs에 연결할 수 있어야 합니다.

