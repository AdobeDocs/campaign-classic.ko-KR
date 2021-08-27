---
product: campaign
title: Twitter에서 게시 구성
description: Twitter에서 게시 구성
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2d2a6e32-587d-4a7b-ba1c-d9140da53f64
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 3%

---

# Twitter에서 게시 구성{#configuring-publishing-on-twitter}

![](../../assets/v7-only.svg)

Adobe Campaign에서 Twitter 계정에 트윗을 보내려면 이러한 계정에 대해 Adobe Campaign에 대한 쓰기 액세스 권한을 위임해야 합니다. 이렇게 하려면 다음 구성 단계를 적용합니다.

* twitter 계정을 만듭니다.
* 증명을 전송할 테스트 Twitter 계정을 만듭니다.
* twitter 계정당 하나의 Twitter 애플리케이션을 만듭니다.
* 각 Twitter 응용 프로그램에 대해 새 **[!UICONTROL Twitter]** 유형 서비스를 만듭니다.

![](assets/social_diagram_twitter_service.png)

## 필수 구성 요소 {#prerequisites}

먼저 하나 이상의 Twitter 계정을 만들어 트윗을 로 보냅니다.

twitter 계정을 만들려면 [https://twitter.com](https://twitter.com)로 이동하십시오.

## twitter에 테스트 계정 만들기 {#creating-a-test-account-on-twitter}

트윗 증명을 보내는 데 사용할 수 있는 비공개 Twitter 계정을 만드는 것이 좋습니다(자세한 내용은 [증명 보내기](../../social/using/publishing-on-twitter.md#sending-the-proof) 참조).

* 새 Twitter 계정을 만듭니다.
* 오른쪽 상단 모서리의 메뉴를 클릭하고 **[!UICONTROL Settings]** 을 선택합니다.
* **[!UICONTROL Security and privacy]** 탭을 선택하고 **[!UICONTROL Protect my Tweets]** 상자를 선택합니다.
* 페이지 하단에 있는 **[!UICONTROL Save Changes]** 단추를 클릭합니다.

![](assets/social_twitter_test_page.png)

## twitter 시 애플리케이션 만들기 {#creating-an-application-on-twitter}

Adobe Campaign에서 Twitter 계정에 트윗을 보내려면 Twitter 계정당 하나의 Twitter 애플리케이션을 만들어야 합니다. 그렇게 하려면 다음 단계를 적용합니다.

1. twitter 계정에 로그인합니다.
1. 인터넷 브라우저에 다음 주소를 입력합니다. [https://apps.twitter.com/](https://apps.twitter.com/)
1. 그런 다음 오른쪽의 **[!UICONTROL Create New App]** 버튼을 클릭합니다.

   ![](assets/social_create_twitter_app_001.png)

1. 마법사가 프로세스를 안내합니다.

   이 애플리케이션에서 Adobe Campaign이 계정에 트윗을 보낼 수 있도록 하려면 애플리케이션의 **[!UICONTROL Permissions]** 탭으로 이동하여 **[!UICONTROL Access]** 섹션에 대해 **[!UICONTROL Read and Write]** 를 선택합니다. **[!UICONTROL Settings]** 탭에서 **[!UICONTROL Callback URL]** 필드를 비워 두어야 합니다.

   ![](assets/social_create_twitter_app_002.png)

## Adobe Campaign에 대한 쓰기 액세스 위임 {#delegating-write-access-to-adobe-campaign}

각 Twitter 응용 프로그램에 대해 응용 프로그램 설정을 포함할 다른 **[!UICONTROL Twitter]** 유형 서비스를 만들어야 합니다.

이 단계에는 Adobe Campaign 콘솔과 Twitter 계정에 로그온한 인터넷 브라우저에 대한 동시 액세스 권한이 필요합니다.

* **Twitter**: 앞에서 만든 애플리케이션([https://dev.twitter.com/apps](https://dev.twitter.com/apps))을 선택하고 탭을  **[!UICONTROL Keys and Access Tokens]** 클릭합니다.

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**: 탭으로  **[!UICONTROL Profiles and targets]** 이동하여 링크를  **[!UICONTROL Services and Subscriptions]** 클릭하고 버튼을  **[!UICONTROL Create]** 클릭합니다.

   ![](assets/social_twitter_service_007.png)

1. **[!UICONTROL Twitter]** 유형을 선택합니다.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >기본적으로 **[!UICONTROL Synchronize subscriptions]** 옵션이 활성화되어 있습니다. 이 확인란을 선택하면 Twitter 계정 동기화 워크플로우( [Twitter 계정 동기화](#synchronizing-twitter-accounts) 참조)가 직접 메시지를 전송할 수 있도록 Twitter 팔로워 목록을 복구합니다( [구독자에게 직접 메시지 보내기](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers) 참조). 팔로워를 복구하지 않으려면 이 상자의 선택을 취소합니다.

1. 서비스의 레이블과 내부 이름을 입력합니다.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >서비스의 **[!UICONTROL Internal name]**&#x200B;은(는) Twitter 계정의 이름과 동일해야 합니다. 항목 오류가 없는지 확인하려면 아래 단계를 수행하십시오.

   * **[!UICONTROL Save]** 버튼을 클릭합니다.
   * 서비스 개요에서 방금 만든 Twitter 유형 서비스를 클릭합니다.
   * **[!UICONTROL Twitter page]** 탭을 선택합니다. twitter 계정이 표시됩니다.

      ![](assets/social_twitter_service_010.png)

1. **[!UICONTROL Visitor folder]** 필드에서 팔로워가 생성될 방문자 폴더를 선택합니다. 자세한 내용은 [운영 원칙](../../social/using/publishing-on-twitter.md#operating-principle)을 참조하십시오. 기본적으로 **[!UICONTROL Visitors]** 폴더의 루트에 팔로워가 만들어집니다.

   ![](assets/social_twitter_service_010_b.png)

1. twitter 시 **[!UICONTROL Consumer Key (API Key)]** 및 **[!UICONTROL Consumer Secret (API Secret)]** 필드의 내용을 복사하여 콘솔의 **[!UICONTROL Consumer key]** 및 **[!UICONTROL Consumer secret]** 필드에 붙여넣습니다.

   ![](assets/social_twitter_service_012.png)

1. twitter 시 **[!UICONTROL Access Token]** 및 **[!UICONTROL Access Token Secret]** 필드의 내용을 복사하여 콘솔의 **[!UICONTROL Access token]** 및 **[!UICONTROL Access token secret]** 필드에 붙여넣습니다.

   ![](assets/social_twitter_service_013.png)

1. Adobe Campaign 콘솔에서 **[!UICONTROL Save]** 을 클릭합니다. 이제 Adobe Campaign에 대한 쓰기 액세스 위임을 완료했습니다.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>twitter 응용 프로그램당 하나의 **[!UICONTROL Twitter]** 유형 서비스를 만들어야 합니다.

**[!UICONTROL Twitter account Synchronization]** 워크플로우는 Adobe Campaign에서 Twitter 계정을 동기화합니다. 자세한 내용은 [Facebook 페이지 동기화](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages)를 참조하십시오.

## twitter 계정 동기화 {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>워크플로우가 Twitter 구독자 목록을 복구하려면 계정에 연결된 서비스의 편집 섹션에서 **[!UICONTROL Twitter account synchronization]** 상자를 선택해야 합니다. 자세한 내용은 [Adobe Campaign에 대한 쓰기 액세스 위임](#delegating-write-access-to-adobe-campaign)을 참조하십시오.

**[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** 노드를 통해 액세스하는 **[!UICONTROL Twitter account synchronization]** 워크플로우에서는 이전에 Adobe Campaign과 구성한 Twitter 계정을 동기화할 수 있습니다. 기본적으로 이 워크플로우는 매주 목요일 오전 7:30에 트리거됩니다.

>[!NOTE]
>
>예상 작업 처리를 실행하여 언제든지 워크플로우를 시작할 수 있습니다. 스케줄러를 편집하여 워크플로우 트리거 빈도를 변경할 수도 있습니다. 스케줄러에 대한 자세한 정보는 [이 섹션](../../workflow/using/scheduler.md)을 참조하십시오.

이제 트윗을 Twitter 계정에 전송하고 팔로워에게 메시지를 보낼 수 있습니다. 자세한 내용은 다음을 참조하십시오. [Twitter](../../social/using/publishing-on-twitter.md)에 게시.
