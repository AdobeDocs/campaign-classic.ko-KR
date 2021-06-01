---
product: campaign
title: Twitter에서 게시
description: Twitter에서 게시
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
exl-id: e030c029-d1ee-4749-94e3-6bdfc8d89a34
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 5%

---

# Twitter에서 게시{#publishing-on-twitter}

## twitter 계정에 게시 {#publishing-on-your-twitter-accounts}

구성이 완료되면 Social Marketing에서 트윗을 Twitter 계정에 보낼 수 있습니다.

### 제한 사항 {#limitations}

다음 제한 사항은 Twitter에 고유한 제한 사항입니다.

* 메시지는 140자를 초과할 수 없습니다.
* HTML 형식은 지원되지 않습니다.

### 게재 만들기 {#creating-the-delivery}

**[!UICONTROL Tweet (twitter)]** 게재 템플릿을 기반으로 새 게재를 만듭니다.

![](assets/social_twitter_delivery_001.png)

### 기본 대상 {#selecting-the-main-target} 선택

트윗을 전송할 계정을 선택합니다.

1. **[!UICONTROL To]** 링크를 클릭합니다.

   ![](assets/social_twitter_delivery_002.png)

1. **[!UICONTROL Add]** 버튼을 클릭합니다.

   ![](assets/social_twitter_delivery_006.png)

1. **[!UICONTROL A Twitter account]**&#x200B;을(를) 선택합니다.

   ![](assets/social_twitter_delivery_007.png)

1. **[!UICONTROL Folder]** 필드에서 Twitter 계정이 포함된 서비스 폴더를 선택합니다. 그런 다음 트윗을 보낼 Twitter 계정을 선택합니다.

   ![](assets/social_twitter_delivery_011.png)

### 증명 {#selecting-the-target-of-the-proof} 대상 선택

**[!UICONTROL Target of the proofs]** 탭에서는 최종 게재 전에 테스트 게재에 사용할 Twitter 계정을 정의할 수 있습니다. 따라서 증명 보내기에 전용 개인 Twitter 계정을 만드는 것이 좋습니다. 개인 Twitter 계정을 만드는 방법에 대한 자세한 내용은 [Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)에 테스트 계정 만들기를 참조하십시오. 증명 대상을 선택하는 단계는 기본 대상을 선택하는 단계와 동일합니다. [Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)에 테스트 계정 만들기를 참조하십시오.

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>모든 게재에 대해 동일한 Twitter 테스트 계정을 사용하는 경우 **[!UICONTROL Resources > Templates > Delivery templates]** 노드를 통해 액세스되는 **[!UICONTROL Tweet]** 게재 템플릿에 증명 대상을 저장할 수 있습니다. 그런 다음 증명 타겟을 새로 게재할 때마다 기본적으로 입력됩니다.

### 메시지 콘텐츠 정의 {#defining-the-message-content}

**[!UICONTROL Content]** 탭에 트윗의 컨텐츠를 입력합니다.

![](assets/social_twitter_delivery_005.png)

### 미리 보기 {#viewing-the-preview} 보기

**[!UICONTROL Preview]** 탭에서는 트윗의 렌더링을 볼 수 있습니다.

1. **[!UICONTROL Preview]** 탭을 클릭합니다.
1. **[!UICONTROL Test personalization]** 드롭다운 메뉴를 클릭하고 **[!UICONTROL Service]** 을 선택합니다.
1. **[!UICONTROL Folder]** 필드에서 Twitter 계정이 포함된 서비스 폴더를 선택합니다.
1. 미리 보기를 테스트할 Twitter 계정을 선택합니다.

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>미리 보기는 최종 트윗과 약간 다를 수 있습니다. 최종 게재 전에 증명을 보내 트윗의 정확한 렌더링을 확인하는 것이 좋습니다. [증명 보내기](#sending-the-proof)를 참조하십시오.

### 추적 구성 {#configuring-tracking}

추적은 게재 보고서와 게재 및 서비스의 **[!UICONTROL Edit > Tracking]** 탭에서 볼 수 있습니다.

추적 구성은 이메일 게재와 동일합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../delivery/using/about-delivery-monitoring.md)을 참조하십시오.

>[!NOTE]
>
>**[!UICONTROL Tweet]** 게재 템플릿에서 추적이 기본적으로 활성화됩니다.

>[!IMPORTANT]
>
>트윗을 분석하는 로봇과 실제로 클릭하는 사용자 간의 차이를 알 수 없습니다.

### 증명 {#sending-the-proof} 보내기

개인 Twitter 테스트 페이지에서 발행물의 정확한 렌더링을 얻으려면 최종 게재 전에 발행물 증명을 보내는 것이 좋습니다. 비공개 Twitter 계정 만들기에 대한 자세한 내용은 [Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)에 테스트 계정 만들기를 참조하십시오. 증명 대상을 선택하는 단계는 [증명 대상 선택](#selecting-the-target-of-the-proof)에 자세히 설명되어 있습니다.

증명 게재는 이메일 게재와 동일합니다. [이 섹션](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)을 참조하십시오.

### 메시지 {#sending-the-message} 보내기

1. 컨텐츠가 승인되면 **[!UICONTROL Send]** 버튼을 클릭합니다.
1. **[!UICONTROL Deliver as soon as possible]** 을 선택하고 **[!UICONTROL Analyze]** 버튼을 클릭합니다.

   >[!NOTE]
   >
   >**[!UICONTROL Postpone the delivery]** 옵션을 사용하면 배달을 나중 날짜로 연기할 수 있습니다.

   ![](assets/social_twitter_delivery_012.png)

1. 분석이 완료되면 결과를 확인합니다.
1. **[!UICONTROL Confirm delivery]** 을 클릭한 다음 **[!UICONTROL Yes]** 를 클릭합니다.

![](assets/social_facebook_delivery_016.png)

## 구독자에게 직접 메시지 보내기 {#sending-direct-messages-to-subscribers}

### 운영 원칙 {#operating-principle}

**[!UICONTROL Synchronize Twitter accounts]** 워크플로우([Twitter 계정 동기화](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts) 참조)는 직접 메시지를 보낼 수 있도록 Twitter 구독자 목록을 복구합니다. 복구된 팔로워는 특정 테이블에 저장됩니다.방문자 테이블입니다. twitter 팔로워의 목록을 표시하려면 **[!UICONTROL Profiles and Targets > Visitors]** 노드로 이동합니다.

![](assets/social_twitter_visitors_001.png)

>[!IMPORTANT]
>
>워크플로우가 Twitter 팔로워 목록을 복구하려면 계정에 연결된 서비스의 편집 화면에서 **[!UICONTROL Synchronize Twitter accounts]** 상자를 선택해야 합니다. 자세한 내용은 다음을 참조하십시오.[Adobe Campaign](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign)에 대한 쓰기 액세스 권한을 위임합니다.

Adobe Campaign은 각 팔로어에 대해 다음 정보를 복구합니다.

* **[!UICONTROL Origin]**:소셜 네트워크 이름(이 **** 경우 Twitter)
* **[!UICONTROL External ID]**:사용자 식별자
* **[!UICONTROL User name]**:사용자의 계정 이름
* **[!UICONTROL Full name]**:사용자 이름
* **[!UICONTROL Language]**:사용자 언어
* **[!UICONTROL Number of friends]**:팔로워 수
* **[!UICONTROL Time zone]**:사용자 시간대
* **[!UICONTROL Verified]**:이 필드는 사용자가 확인된 Twitter 계정을 가지고 있는지 여부를 나타냅니다

### 제한 사항 {#limitations-1}

다음 제한 사항은 Twitter에 고유한 제한 사항입니다.

* 메시지는 140자를 초과할 수 없습니다.
* HTML은 지원되지 않습니다.
* 하루에 250개 이상의 직접 메시지를 보낼 수 없습니다. 이 임계값을 초과하지 않도록 여러 파도로 전달할 수 있습니다. 웨이브 게재 는 이메일 게재와 같이 구성됩니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)을 참조하십시오.

### 게재 만들기 {#creating-the-delivery-}

**[!UICONTROL Tweet (Direct Message)]** 게재 템플릿을 기반으로 새 게재를 만듭니다.

![](assets/social_twitter_delivery_010.png)

### 기본 대상 {#selecting-the-main-target-1} 선택

직접 메시지를 보낼 팔로워를 선택합니다.

1. **[!UICONTROL To]** 링크를 클릭합니다.

   ![](assets/social_twitter_delivery_016.png)

1. **[!UICONTROL Add]** 버튼을 클릭합니다.

   ![](assets/social_twitter_delivery_006.png)

1. 타겟팅 유형을 선택합니다.

   ![](assets/social_twitter_delivery_017.png)

   * 모든 계정 팔로워에게 직접 메시지를 보내려면 **[!UICONTROL Twitter subscribers]** 을 선택합니다.

      >[!IMPORTANT]
      >
      >하루에 250개 이상의 메시지를 보낼 수 없습니다. twitter 계정에 팔로워가 250명이 넘는 경우 웨이브를 전달하는 것이 좋습니다. 여기에는 이메일 게재와 동일한 프로세스가 포함됩니다. [이 섹션](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)을 참조하십시오.

   * 쿼리를 정의하고 결과를 보려면 **[!UICONTROL Filter conditions]** 을 선택합니다. 이 옵션은 이메일 게재와 동일합니다. 자세한 내용은 [이 섹션](../../platform/using/defining-filter-conditions.md)을 참조하십시오.

      ![](assets/social_twitter_delivery_018.png)

### 증명 {#selecting-the-target-of-the-proof-1} 대상 선택

**[!UICONTROL Target of the proofs]** 탭에서는 직접 메시지 증명을 받을 팔로워를 선택할 수 있습니다. 선택 프로세스는 기본 타겟과 동일합니다. [기본 대상 선택](#selecting-the-main-target)을 참조하십시오.

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>모든 직접 메시지 증명을 동일한 Twitter 종단자에게 보내려면 **[!UICONTROL Resources > Templates > Delivery templates]** 노드를 통해 액세스하는 **[!UICONTROL Tweet (Direct Message)]** 게재 템플릿에서 증명 대상을 저장할 수 있습니다. 그런 다음 증명 타겟을 새로 게재할 때마다 기본적으로 입력됩니다.

### 메시지 콘텐츠 정의 {#defining-message-content-}

**[!UICONTROL Content]** 탭에 트윗의 컨텐츠를 입력합니다.

![](assets/social_twitter_delivery_015.png)

개인화 필드는 이메일 게재와 동일한 방법으로 사용할 수 있습니다. 예를 들어 메시지 본문에 팔로워 이름을 추가할 수 있습니다. 컨텐츠 개인화는 [이 섹션](../../delivery/using/about-personalization.md)에 자세히 설명되어 있습니다.

![](assets/social_twitter_delivery_021.png)

다음 단계는 Twitter 계정에 트윗을 전송하는 것과 동일합니다. twitter 계정에 게시](#publishing-on-your-twitter-accounts)를 참조하십시오.[
