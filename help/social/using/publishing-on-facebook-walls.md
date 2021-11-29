---
product: campaign
title: Facebook wall 게시
description: Facebook wall 게시
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2135a836-245f-406e-b351-c27d38e0f9fd
source-git-commit: b5334de18eca8fc1147ae0c42fe23a6932bf71d2
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 4%

---

# Facebook wall 게시{#publishing-on-facebook-walls}

![](../../assets/v7-only.svg)

Adobe Campaign에서 Facebook 벽으로 발행물을 보내려면 이러한 페이지에 대한 쓰기 액세스 권한을 Adobe Campaign에 위임해야 합니다. 여기에는 다음 구성 단계가 포함됩니다.

1. 하나 이상의 페이지로 Facebook 계정을 만듭니다.
1. 증명을 전송할 테스트 Facebook 페이지를 만듭니다.
1. Facebook 애플리케이션 만들기.
1. Adobe Campaign에 Facebook 애플리케이션 설정을 입력합니다. **[!UICONTROL Facebook routing]** 외부 계정.

## 필수 구성 요소 {#prerequisites}

먼저 Facebook 계정 및 여러 페이지를 만듭니다. 이러한 정보는 게시를 전송하는 데 사용됩니다.

* facebook 계정을 만들려면 [https://www.facebook.com](https://www.facebook.com) 링크를 클릭합니다.
* facebook 페이지를 만들려면 [https://www.facebook.com/pages/create](https://www.facebook.com/pages/create) 링크를 클릭합니다.

   동일한 Facebook 계정을 사용하여 모든 페이지를 관리하는 것이 좋습니다. 이렇게 하면 계정의 모든 페이지에 쓸 Facebook 애플리케이션과 하나의 외부 계정만 필요합니다.

   ![](assets/social_diagram_fb_external_account.png)

## 테스트 Facebook 페이지 만들기 {#creating-a-test-facebook-page}

게시 증명을 제공하기 위해 비공개 Facebook 페이지를 만드는 것이 좋습니다(자세한 내용은 다음을 참조하십시오.) [이 섹션](../../social/using/publishing-on-facebook.md#sending-the-proof).

1. 페이지를 관리하는 데 사용하는 Facebook 계정에 로그인합니다.
1. 새 Facebook 페이지를 만듭니다.
1. 을(를) 클릭합니다. **[!UICONTROL Settings]** 오른쪽 상단 모서리의 단추.
1. 에서 **[!UICONTROL General]** 탭에서 페이지의 가시성 매개 변수를 수정합니다. 확인 **[!UICONTROL Page unpublished]** 상자.
1. **[!UICONTROL Save Changes]** 버튼을 클릭합니다.

![](assets/social_facebook_test_page.png)

## Facebook 애플리케이션 만들기 {#creating-a-facebook-application}

Adobe Campaign이 페이지의 담벼락에 게시하려면 Facebook 애플리케이션을 만들어야 합니다. 그렇게 하려면 다음 단계를 적용합니다.

1. 페이지를 관리하는 데 사용하는 Facebook 계정에 로그인합니다.
1. 브라우저에 다음 주소를 입력합니다. [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!CAUTION]
   >
   >보유하고 있는 계정 유형에 따라 하나 이상의 승인이 필요할 수 있습니다.
   >
   >facebook 애플리케이션을 만들려면 **확인됨** Facebook 계정.

1. 을(를) 클릭합니다. **[!UICONTROL Add a New App]** 페이지의 오른쪽 상단 모서리에 있는 단추. 앱 이름과 연락처 이메일을 입력한 다음 보안 검사를 전달합니다.

   ![](assets/social_create_facebook_app_002.png)

1. 아래 **[!UICONTROL Settings > Basic]**&#x200B;를 클릭하고 **[!UICONTROL Add a platform]** 을(를) 선택하고 을(를) 선택합니다. **[!UICONTROL Facebook Web Games]** 유형.

   ![](assets/social_create_facebook_app_003.png)

1. 에서 **[!UICONTROL Products]** 왼쪽 메뉴에서 **[!UICONTROL Facebook Login]** 제품. 없는 경우 새 제품을 추가하고 을(를) 선택합니다 **[!UICONTROL Facebook Login]**.

   ![](assets/social_create_facebook_app_003bis.png)

1. 응용 프로그램이 만들어지면 **[!UICONTROL App Review]** 탭을 열고 애플리케이션을 게시합니다.

   ![](assets/social_create_facebook_app_004.png)

## Adobe Campaign에 대한 쓰기 액세스 위임 {#delegating-write-access-to-adobe-campaign}

페이지 벽에 게시하기 위해 Adobe Campaign에 대한 쓰기 액세스를 위임하려면 이전에 만든 Facebook 애플리케이션의 매개 변수를 입력해야 합니다.

이 단계에는 페이지 관리에 사용하는 Facebook 계정에 로그온한 Adobe Campaign 콘솔 및 인터넷 브라우저에 모두 액세스해야 합니다.

>[!CAUTION]
>
>Adobe Campaign 연산자는 이 구성을 수행할 관리 권한이 있어야 합니다.

* **Facebook**: 앞에서 만든 응용 프로그램 선택( [https://developers.facebook.com/apps](https://developers.facebook.com/apps))을 클릭하고 **[!UICONTROL Settings > Basic]** 탭.

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >만약 **[!UICONTROL Facebook Web Games]** 섹션이 나타나지 않으면 **[!UICONTROL Add Platform]** 단추 를 클릭하고 페이지 하단에서 을 선택합니다. **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: 로 이동 **[!UICONTROL Administration > Platform > External Accounts]** 트리의 노드에서 **[!UICONTROL Facebook routing]** 외부 계정을 클릭하고 **[!UICONTROL Connector]** 탭.

   ![](assets/social_facebook_external_account_001.png)

1. Adobe Campaign 콘솔에서 **[!UICONTROL Secure Canvas URL]** 필드에 붙여 넣습니다. **[!UICONTROL Secure Web Games URL (https)]** facebook의 필드(에서) **[!UICONTROL Facebook Web Games]** 섹션).

   ![](assets/social_facebook_external_account_006.png)

   >[!CAUTION]
   >
   >어떤 상황에서도 비보안 URL을 사용해서는 안 됩니다.

   이 URL을 복사하여 다음 아래에도 붙여넣습니다 **[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**. URL의 유효성을 검사하려면 애플리케이션을 저장하고 URL을 복사하여 **[!UICONTROL Redirect URI to Check]** 필드 및 클릭 **[!UICONTROL Check URI]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. facebook에서 **[!UICONTROL App ID]** 및 **[!UICONTROL App Secret]** 필드를 만들어 콘솔의 일치 필드에 붙여넣습니다.

   ![](assets/social_facebook_external_account_007.png)

1. facebook에서 **[!UICONTROL Save Changes]** 단추 를 클릭합니다.
1. Adobe Campaign 콘솔으로 이동하여 외부 계정을 저장합니다.

   >[!NOTE]
   >
   >다음 **[!UICONTROL Marketing URL]** 필드는 선택 사항입니다.

1. Adobe Campaign 콘솔에서 **[!UICONTROL Request the authorization from the application]** 의 맨 아래에 있는 링크 **[!UICONTROL Connector]** 탭. 다음 **[!UICONTROL Synchronize Facebook pages]** 워크플로우는 자동으로 트리거되고 관리자가 관리하는 모든 Facebook 페이지를 수집합니다. [자세히 알아보기](#synchronizing-facebook-pages)

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >기본적으로 페이지가 **[!UICONTROL Facebook]** 서비스 폴더(를 통해 사용 가능) **[!UICONTROL Profiles and Targets > Services and Subscriptions]** 노드 아래에 있어야 합니다. 다음 **[!UICONTROL Folder]** 필드 **[!UICONTROL Connector]** 탭에서는 동기화 후 Facebook 페이지가 만들어지는 서비스 폴더를 변경할 수 있습니다. 또한 **[!UICONTROL Filter]** 필드. 이 필드를 비워 두면 관리자가 관리하는 모든 Facebook 페이지가 동기화됩니다.

1. 다양한 Facebook 권한 설정과 함께 대화 상자가 표시됩니다. 이를 통해 Adobe Campaign은 게시물을 Facebook 계정 페이지에 보낼 수 있습니다.

   다양한 권한 요청을 수락합니다.

   ![](assets/social_facebook_external_account_003.png)

1. Adobe Campaign은 Facebook 계정 페이지의 벽면에 게시할 수 있는 권한이 부여되었습니다.

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>facebook 계정이 여러 페이지를 관리하는 경우 Facebook 계정의 모든 페이지에 쓰도록 하나의 외부 계정을 구성하면 됩니다. 새로운 각 Facebook 계정에 대해 새 계정을 만들어야 합니다 **[!UICONTROL Routing]** 외부 계정을 입력합니다.

다음 **[!UICONTROL Synchronization of Facebook pages]** 워크플로우는 Adobe Campaign을 통해 직접 담벼락에 게시할 수 있도록 Facebook 계정에서 관리하는 모든 페이지를 동기화합니다. [자세히 알아보기](#synchronizing-facebook-pages)

## facebook 페이지 동기화 {#synchronizing-facebook-pages}

다음 **[!UICONTROL Synchronization of Facebook pages]** 워크플로우를 통해 액세스 **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** node를 사용하면 이전에 구성된 Facebook 계정의 페이지를 Adobe Campaign에서 동기화할 수 있습니다. 기본적으로 이 워크플로우는 하루에 한 번 또는 관리자가 클릭하는 때마다 실행되도록 구성됩니다 **[!UICONTROL Request an authorization from the application]** 링크를 클릭합니다. [자세히 알아보기](#delegating-write-access-to-adobe-campaign)

동기화가 완료되면 수집된 페이지가 외부 계정에 입력한 서비스 폴더에 나타납니다. [자세히 알아보기](#delegating-write-access-to-adobe-campaign)).

기본적으로 페이지가 의 루트에 추가됩니다 **[!UICONTROL Facebook]** 를 통해 사용 가능한 서비스 폴더 **[!UICONTROL Profiles and Targets > Services and subscriptions]** 메뉴 아래의 제품에서 사용할 수 있습니다.

![](assets/social_facebook_service_002.png)

이제 Adobe Campaign을 통해 Facebook 페이지의 담벼락에 직접 게시할 수 있습니다. [자세히 알아보기](#publishing-on-facebook-walls)
