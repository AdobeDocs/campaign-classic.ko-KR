---
product: campaign
title: iOS 장치에 대한 푸시 알림 만들기
description: iOS용 푸시 알림을 만드는 방법을 알아봅니다
feature: Push
exl-id: 4520504a-0d9f-4ea7-a5a8-0c07948af4f0
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 3%

---

# iOS에 대한 알림 만들기{#create-notifications-ios}

![](../../assets/common.svg)

이 섹션에서는 iOS 알림 전달과 관련된 요소에 대해 자세히 설명합니다. 게재 만들기에 대한 글로벌 개념은 [이 섹션](steps-about-delivery-creation-steps.md).

먼저 새 게재를 만듭니다.

![](assets/nmac_delivery_1.png)

iOS 장치에 대한 푸시 알림을 만들려면 아래 단계를 수행하십시오.

1. 을(를) 선택합니다 **[!UICONTROL Deliver on iOS]** 게재 템플릿.

   ![](assets/nmac_delivery_ios_1.png)

1. 알림 대상을 정의하려면 **[!UICONTROL To]** 링크를 클릭한 다음 **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >게재의 대상 모집단을 선택할 때의 자세한 프로세스가에 표시됩니다. [이 섹션](steps-defining-the-target-population.md).
   >
   >개인화 필드 사용에 대한 자세한 내용은 [이 섹션](about-personalization.md).
   >
   >시드 목록 포함에 대한 자세한 내용은 [시드 주소 기본 정보](about-seed-addresses.md).

1. 선택 **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**&#x200B;를 클릭하고, 모바일 애플리케이션과 관련된 서비스(이 경우 Neotrip)를 선택한 다음, 애플리케이션의 iOS 버전을 선택합니다.

   ![](assets/nmac_delivery_ios_3.png)

1. 알림 유형을 선택합니다. **[!UICONTROL Alert]**, **[!UICONTROL Badge]**, 또는 **[!UICONTROL Alert and badge]** 또는 **[!UICONTROL Silent Push]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >다음 **자동 푸시** 모드에서는 모바일 애플리케이션에 &quot;자동&quot; 알림을 보낼 수 있습니다. 사용자가 알림의 도착을 인식하지 못합니다. 애플리케이션에 직접 전송됩니다.

1. 에서 **[!UICONTROL Title]** 필드에서 알림에 표시할 제목의 레이블을 입력합니다. 알림 센터에서 사용할 수 있는 알림 목록에만 표시됩니다. 이 필드에서는 **제목** iOS 알림 페이로드의 매개 변수입니다.

1. HTTP/2 커넥터를 사용하는 경우 자막(값: **부제** iOS 알림 페이로드의 매개 변수)입니다. 자세한 내용은 [이 섹션](configuring-the-mobile-application.md).

1. 그런 다음 **[!UICONTROL Message]** 그리고 **[!UICONTROL Value of the badge]** 선택한 알림 유형에 따라 다릅니다.

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >**[!UICONTROL Badge]** 및 **[!UICONTROL Alert and badge]** 유형 알림을 사용하면 배지의 값(모바일 애플리케이션 로고 위의 번호)을 수정할 수 있습니다. 배지를 새로 고침하려면 0을 값으로 입력하기만 하면 됩니다. 필드가 비어 있으면 배지 값이 변경되지 않습니다.

1. 을(를) 클릭합니다. **[!UICONTROL Insert emoticon]** 푸시 알림에 이모티콘을 삽입하는 아이콘. 이모티콘 목록을 사용자 정의하려면 [이 섹션](customizing-emoticon-list.md)

1. 다음 **[!UICONTROL Action button]** 경고 알림에 나타나는 작업 단추에 대한 레이블을 정의할 수 있습니다(**action_loc_key** 페이로드 필드). iOS 응용 프로그램이 지역화할 수 있는 문자열(**Localizable.strings**) 을 입력하고 이 필드에 해당 키를 입력합니다. 응용 프로그램에서 지역화 가능한 텍스트를 관리하지 않는 경우 작업 단추에 표시할 레이블을 입력합니다. 지역화 가능한 문자열에 대한 자세한 내용은 [Apple 설명서](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1) .
1. 에서 **[!UICONTROL Play a sound]** 필드에서는 알림을 받을 때 모바일 단말이 재생할 사운드를 선택합니다.

   >[!NOTE]
   >
   >사운드는 응용 프로그램에 포함되고 서비스를 만들 때 정의해야 합니다. [이 섹션](configuring-the-mobile-application.md#configuring-external-account-ios)을 참조하십시오.

1. 에서 **[!UICONTROL Application variables]** 필드에서 각 변수의 값을 입력합니다. 애플리케이션 변수를 사용하면 알림 동작을 정의할 수 있습니다. 예를 들어 사용자가 알림을 활성화하면 표시되는 특정 애플리케이션 화면을 구성할 수 있습니다.

   >[!NOTE]
   >
   >애플리케이션 변수는 모바일 애플리케이션의 코드에 정의되어야 하며, 서비스를 만들 때 입력해야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](configuring-the-mobile-application.md)을 참조하십시오.

1. 알림이 구성되면 **[!UICONTROL Preview]** 탭을 클릭하여 알림을 미리 봅니다.

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >알림 스타일(배너 또는 경고)이 Adobe Campaign에 정의되지 않았습니다. 사용자가 iOS 설정에서 선택한 구성에 따라 달라집니다. 그러나 Adobe Campaign에서는 각 유형의 알림 스타일을 미리 볼 수 있습니다. 오른쪽 하단에 있는 화살표를 클릭하여 한 스타일에서 다른 스타일로 전환합니다.
   >
   >미리 보기에서는 iOS 10 모양과 느낌을 사용합니다.

증명을 보내고 최종 게재를 보내려면 이메일 게재와 동일한 프로세스를 사용합니다.

메시지를 보낸 후 게재를 모니터링하고 추적할 수 있습니다. 자세한 정보는 다음 섹션을 참조하십시오.

* [푸시 알림 격리](understanding-quarantine-management.md#push-notification-quarantines)
* [게재 모니터링](about-delivery-monitoring.md)
* [게재 실패 이해](understanding-delivery-failures.md)


## iOS 리치 알림 만들기 {#creating-ios-delivery}

iOS 10 이상을 사용하면 풍부한 알림을 생성할 수 있습니다. Adobe Campaign은 장치가 리치 알림을 표시할 수 있는 변수를 사용하여 알림을 전송할 수 있습니다.

이제 새 게재를 만들고 만든 모바일 애플리케이션에 연결해야 합니다.

1. 이동 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

   ![](assets/nmac_android_3.png)

1. 선택 **[!UICONTROL Deliver on iOS (ios)]** 에서 **[!UICONTROL Delivery template]** 드롭다운. 추가 **[!UICONTROL Label]** 게재할 수도 있습니다.

1. 클릭 **[!UICONTROL To]** 타겟팅할 모집단을 정의하려면 기본적으로 **[!UICONTROL Subscriber application]** 대상 매핑이 적용됩니다. 클릭 **[!UICONTROL Add]** 을 클릭하여 앞에서 만든 서비스를 선택합니다.

   ![](assets/nmac_ios_9.png)

1. 에서 **[!UICONTROL Target type]** 창, 선택 **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** 을(를) 클릭합니다. **[!UICONTROL Next]**.

1. 에서 **[!UICONTROL Service]** 드롭다운에서 앞에서 만든 서비스를 선택하고 타겟팅할 애플리케이션을 선택한 다음 **[!UICONTROL Finish]**.
다음 **[!UICONTROL Application variables]** 은 구성 단계 동안 추가된 내용에 따라 자동으로 추가됩니다.

   ![](assets/nmac_ios_6.png)

1. 리치 알림을 편집합니다.

   ![](assets/nmac_ios_7.png)

1. 을(를) 확인합니다. **[!UICONTROL Mutable content]** 알림 편집 창의 상자에서 모바일 애플리케이션에서 미디어 컨텐츠를 다운로드할 수 있습니다.

1. 클릭 **[!UICONTROL Save]** 게재를 보낼 수 있습니다.

구독자의 모바일 iOS 장치에서 수신한 경우 푸시 알림에 이미지 및 웹 페이지가 표시되어야 합니다.

![](assets/nmac_ios_8.png)
