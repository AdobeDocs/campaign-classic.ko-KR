---
product: campaign
title: Twitter에서 게시 구성
description: Twitter에서 게시 구성
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2d2a6e32-587d-4a7b-ba1c-d9140da53f64
source-git-commit: d891a235002d465f3b00fafa375d87d42ebafaa6
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 6%

---

# twitter에 게시할 구성 단계{#configuring-publishing-on-twitter}

![](../../assets/v7-only.svg)

Adobe Campaign에서 Twitter 계정에 트윗을 보내려면 이러한 계정에 대해 Adobe Campaign에 대한 쓰기 액세스 권한을 위임해야 합니다. 이렇게 하려면 다음 구성 단계를 적용합니다.

* twitter 계정을 만듭니다.
* 증명을 전송할 테스트 Twitter 계정을 만듭니다.
* twitter 계정당 하나의 Twitter 애플리케이션을 만듭니다.
* 각 Twitter 응용 프로그램에 대해 새 응용 프로그램을 만듭니다 **[!UICONTROL Twitter]** 유형 서비스.

![](assets/social_diagram_twitter_service.png)

## 전제 조건 {#prerequisites}

먼저 하나 이상의 Twitter 계정을 만들어 트윗을 로 보냅니다.

twitter 계정을 만들려면 [https://twitter.com](https://twitter.com){target=&quot;_blank&quot;}.

## twitter에서 테스트 계정 만들기 {#creating-a-test-account-on-twitter}

전송하는 데 사용할 수 있는 개인 Twitter 계정을 만듭니다 [트윗 증명](../../social/using/publishing-on-twitter.md#sending-the-proof). 비공개 Twitter 계정을 만들려면 아래 단계를 수행하십시오.

1. 새 Twitter 계정을 만듭니다.
1. 계정 액세스  **[!UICONTROL Settings]**.
1. 찾아보기 **[!UICONTROL Privacy & Safety]** 및 **[!UICONTROL Audience and Tagging]** 그리고 **[!UICONTROL Protect your Tweets]** 선택 사항입니다. 트윗 및 기타 계정 정보는 사용자를 따르는 사용자만 볼 수 있습니다.

![](assets/social_twitter_test_page.png)

## twitter 시 애플리케이션 만들기 {#creating-an-application-on-twitter}

Adobe Campaign에서 Twitter 계정에 트윗을 보내려면 Twitter 계정당 하나의 Twitter 애플리케이션을 만들어야 합니다. 그렇게 하려면 다음 단계를 적용합니다.

1. twitter 계정에 로그인합니다.
1. 인터넷 브라우저에 다음 주소를 입력합니다. [https://developer.twitter.com/en/apps](https://developer.twitter.com/en/apps).
1. 그런 다음 **[!UICONTROL Create an App]** 오른쪽에 있는 단추입니다.

   ![](assets/social_create_twitter_app_001.png)

1. 마법사가 프로세스를 안내합니다.

   이 애플리케이션에서 Adobe Campaign이 사용자 계정에 트윗을 보낼 수 있도록 하려면 **[!UICONTROL Permissions]** 응용 프로그램의 탭을 선택하고 을 선택합니다 **[!UICONTROL Read and Write]** 대상 **[!UICONTROL Access]** 섹션을 참조하십시오. 에서 **[!UICONTROL Settings]** 탭에서 다음을 수행해야 합니다 **[!UICONTROL Callback URL]** 필드가 비어 있습니다.

   ![](assets/social_create_twitter_app_002.png)

## Adobe Campaign에 대한 쓰기 액세스 위임 {#delegating-write-access-to-adobe-campaign}

각 Twitter 응용 프로그램에 대해 다른 응용 프로그램을 만들어야 합니다 **[!UICONTROL Twitter]** 응용 프로그램 설정을 포함할 서비스를 입력하십시오.

이 단계에는 Adobe Campaign 콘솔과 Twitter 계정에 로그온한 인터넷 브라우저에 대한 동시 액세스 권한이 필요합니다.

* in **Twitter**: 변환 전: [이 페이지](https://developer.twitter.com/en/portal/projects-and-apps)를 클릭하고 이전에 만든 앱을 선택하고 **앱 권한**.

   ![](assets/social_twitter_service_002.png)

   편집 **키 및 토큰** 탭을 사용하여 앱 세부 정보에 액세스합니다.

* in **Adobe Campaign**: 로 이동 **[!UICONTROL Profiles and targets]** 탭에서 **[!UICONTROL Services and Subscriptions]** 를 클릭하고 **[!UICONTROL Create]** 버튼을 클릭합니다.

   ![](assets/social_twitter_service_007.png)

1. 을(를) 선택합니다 **[!UICONTROL Twitter]** 유형.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >다음 **[!UICONTROL Synchronize subscriptions]** 옵션이 기본적으로 활성화되어 있습니다. 이 확인란을 선택하면 Twitter 계정 동기화 워크플로우가 표시됩니다( [twitter 계정 동기화](#synchronizing-twitter-accounts)) Twitter 팔로워를 복구하여 다이렉트 메시지를 보낼 수 있도록 합니다( 참조) [구독자에게 직접 메시지 보내기](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). 팔로워를 복구하지 않으려면 이 상자의 선택을 취소합니다.

1. 서비스의 레이블과 내부 이름을 입력합니다.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >다음 **[!UICONTROL Internal name]** 서비스의 이름은 Twitter 계정의 이름과 동일해야 합니다. 항목 오류가 없는지 확인하려면 아래 단계를 수행하십시오.

   * **[!UICONTROL Save]** 버튼을 클릭합니다.
   * 서비스 개요에서 방금 만든 Twitter 서비스를 클릭합니다.

   <!-- * Select the **[!UICONTROL Twitter page]** tab. The Twitter account should be displayed. 
    
      ![](assets/social_twitter_service_010.png)-->

1. 에서 **[!UICONTROL Visitor folder]** 필드에서 팔로워를 만들 폴더를 선택합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../social/using/publishing-on-twitter.md#operating-principle)을 참조하십시오. 기본적으로 팔로워는 **[!UICONTROL Visitors]** 폴더를 입력합니다.

   ![](assets/social_twitter_service_010_b.png)

1. twitter 시 의 컨텐츠를 복사합니다 **[!UICONTROL Consumer Key (API Key)]** 및 **[!UICONTROL Consumer Secret (API Secret)]** 필드에 붙여 넣습니다. **[!UICONTROL Consumer key]** 및 **[!UICONTROL Consumer secret]** campaign 클라이언트 콘솔 필드.

   ![](assets/social_twitter_service_012.png)

1. twitter 시 의 컨텐츠를 복사합니다 **[!UICONTROL Access Token]** 및 **[!UICONTROL Access Token Secret]** 필드에 붙여 넣습니다. **[!UICONTROL Access token]** 및 **[!UICONTROL Access token secret]** campaign 클라이언트 콘솔 필드.

   ![](assets/social_twitter_service_013.png)

1. Campaign 클라이언트 콘솔에서 **[!UICONTROL Save]**. 이제 Adobe Campaign에 대한 쓰기 액세스 권한을 위임했습니다.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>하나를 만들어야 합니다 **[!UICONTROL Twitter]** twitter 애플리케이션별 서비스입니다.

다음 **[!UICONTROL Twitter account Synchronization]** 워크플로우는 Adobe Campaign에서 Twitter 계정을 동기화합니다.

## twitter 계정 동기화 {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>워크플로우가 Twitter 구독자 목록을 복구하려면 **[!UICONTROL Twitter account synchronization]** 상자를 계정에 연결된 서비스의 편집 섹션에서 선택해야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](#delegating-write-access-to-adobe-campaign)을 참조하십시오.

다음 **[!UICONTROL Twitter account synchronization]** 워크플로우를 통해 액세스 **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** node를 사용하면 이전에 Adobe Campaign과 구성된 Twitter 계정을 동기화할 수 있습니다. 기본적으로 이 워크플로우는 매주 목요일 오전 7:30에 트리거됩니다.

>[!NOTE]
>
>예상 작업 처리를 실행하여 언제든지 워크플로우를 시작할 수 있습니다. 스케줄러를 편집하여 워크플로우 트리거 빈도를 변경할 수도 있습니다. 스케줄러에 대한 자세한 내용은 [이 섹션](../../workflow/using/scheduler.md).

이제 트윗을 Twitter 계정에 전송하고 팔로워에게 메시지를 보낼 수 있습니다. 자세한 정보는 이 [페이지](../../social/using/publishing-on-twitter.md)를 참조하십시오.
