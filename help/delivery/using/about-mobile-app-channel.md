---
title: Adobe Campaign Classic의 모바일 앱 채널 정보
description: 이 섹션에서는 Adobe Campaign Classic의 모바일 앱 채널에 대한 일반 정보를 제공합니다.
page-status-flag: never-activated
uuid: e8d26b33-dc7c-4abd-956a-92f419a117e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 6b3fe8b9-dae6-4f8e-83e1-3376c0fe72a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c581f22261af7e083f6bd47e603d17d2d71e7ce6

---


# 모바일 앱 채널 정보{#about-mobile-app-channel}

>[!CAUTION]
>
>이 문서에서는 모바일 애플리케이션을 Adobe Campaign 플랫폼과 통합하는 프로세스에 대해 자세히 설명합니다. 모바일 애플리케이션을 만드는 방법 또는 알림을 관리하기 위해 구성하는 방법에 대한 정보는 제공하지 않습니다. 자세한 내용은 공식 Apple(https://developer.apple.com/) 및 Android([https://developer.android.com/index.html](https://developer.apple.com/)) 설명서를[참조하십시오](https://developer.android.com/index.html).

아래 섹션에서는 모바일 앱 채널에 대한 정보를 제공합니다. 배달을 만드는 방법에 대한 글로벌 정보는[이 섹션을](../../delivery/using/steps-about-delivery-creation-steps.md)참조하십시오.

모바일 **앱** 채널을 사용하면 Adobe Campaign 플랫폼을 사용하여 앱을 통해 개인화된 알림을 iOS 및 Android 터미널로 전송할 수 있습니다. 두 개의 전달 채널을 사용할 수 있습니다.

* Apple 모바일 장치에 알림을 보낼 수 있는 iOS 채널입니다.

   ![](assets/nmac_intro_2.png)

* Android 모바일 장치로 데이터 메시지를 전송할 수 있는 Android 채널입니다.

   ![](assets/nmac_intro_1.png)

이러한 두 채널에 해당하는 캠페인 워크플로우에는 두 가지 배달 활동이 있습니다.

![](assets/nmac_intro_3.png)

>[!NOTE]
>
>트랜잭션 메시지 템플릿에는 두 가지 트랜잭션 메시지 템플릿이 있습니다.

사용자가 알림을 활성화하여 응용 프로그램 컨텍스트와 일치하는 화면을 표시하는 응용 프로그램 동작을 정의할 수 있습니다. 예:

* 소포가 창고를 떠났다는 통보를 고객에게 보냅니다. 알림을 활성화하면 게재 관련 정보가 있는 페이지가 열립니다.
* 사용자가 장바구니에 품목을 추가했지만 구매를 완료하지 않고 애플리케이션을 종료했습니다. 카트가 중단되었음을 알리는 알림이 전송됩니다. 알림을 활성화하면 항목이 화면에 표시됩니다.

>[!CAUTION]
>
>* 모바일 응용 프로그램으로 보낸 알림이 Apple(Apple Push Notification 서비스) 및 Google(Google Cloud Messaging)에서 지정한 사전 요구 사항 및 조건을 준수하는지 확인해야 합니다.
>* 경고:일부 국가에서는 수집된 데이터 유형 모바일 응용 프로그램과 처리 목적을 사용자에게 알려야 합니다. 당신은 그 법안을 확인해야 합니다.


(mobileAppOptOutMgt) **[!UICONTROL NMAC opt-out management]** 워크플로우는 모바일 장치에서 알림 구독 취소를 업데이트합니다. 이 워크플로우에 대한 자세한 내용은 워크플로우 [안내서를](../../workflow/using/mobile-app-channel.md)참조하십시오.

Adobe Campaign은 바이너리 및 HTTP/2 APNS와 호환됩니다. 구성 단계에 대한 자세한 내용은 커넥터 [섹션을 참조하십시오](../../delivery/using/setting-up-mobile-app-channel.md#connectors) .
