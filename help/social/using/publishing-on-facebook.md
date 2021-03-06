---
product: campaign
title: Facebook 게시
description: facebook에 게시하는 방법 알아보기
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
exl-id: 84d6cb2e-c7f9-43d7-a98c-22613d456193
source-git-commit: b5334de18eca8fc1147ae0c42fe23a6932bf71d2
workflow-type: tm+mt
source-wordcount: '1138'
ht-degree: 3%

---

# Facebook 게시{#publishing-on-facebook}

![](../../assets/v7-only.svg)

구성이 완료되면 Social Marketing을 통해 Facebook 페이지의 벽에 게시물을 게시할 수 있습니다.

## 제한 사항 {#limitations}

다음 제한 사항은 Facebook에 고유합니다.

* 메시지는 1,000자를 초과할 수 없습니다.
* HTML은 지원되지 않습니다.

## 게재 만들기 {#creating-the-delivery}

을(를) 사용하여 새 게재를 만듭니다 **[!UICONTROL Publish to a brand page]** 게재 템플릿.

![](assets/social_facebook_delivery_001.png)

## 기본 대상 선택 {#selecting-the-main-target}

게시물을 게시할 페이지를 선택해야 합니다.

1. **[!UICONTROL To]** 링크를 클릭합니다.

   ![](assets/social_facebook_delivery_010.png)

1. **[!UICONTROL Add]** 버튼을 클릭합니다.

   ![](assets/social_facebook_delivery_011.png)

1. **[!UICONTROL A Facebook page]**&#x200B;을(를) 선택합니다.

   ![](assets/social_facebook_delivery_012.png)

1. 에서 **[!UICONTROL Folder]** 필드에서 Facebook 페이지가 포함된 서비스 폴더를 선택합니다. 기본적으로 페이지는 의 루트에 저장됩니다 **[!UICONTROL Facebook]** 서비스 폴더. 그런 다음 게시할 Facebook 페이지를 선택합니다.

   ![](assets/social_facebook_delivery_013.png)

## 증명 대상 선택 {#selecting-the-proof-target}

다음 **[!UICONTROL Target of the proofs]** 탭에서는 게재를 보내기 전에 테스트하기 위해 사용할 Facebook 페이지를 정의할 수 있습니다. 이를 위해 전용 Facebook 페이지를 만드는 것이 좋습니다. 비공개 Facebook 페이지 만들기에 대한 자세한 내용은 [이 페이지](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page). 증명 대상을 선택하려면 기본 대상과 동일한 단계를 적용합니다. [자세히 알아보기](#selecting-the-main-target)

![](assets/social_facebook_delivery_004.png)

>[!NOTE]
>
>모든 게재에 대해 동일한 Facebook 테스트 페이지를 사용하는 경우, **[!UICONTROL Publish to a brand page]** 게재 템플릿. **[!UICONTROL Resources > Templates > Delivery templates]** 노드 아래에 있어야 합니다. 증명 타겟은 각 새 게재에 대해 기본적으로 입력됩니다.

## 대상자 정의 {#defining-the-audience}

로컬 세그먼트를 사용하여 게시를 볼 수 있도록 허가된 공개 유형을 세분화하려면 세그먼트당 하나의 Facebook 페이지를 만드는 것이 좋습니다(예: Adobe Campaign 파리, Adobe Campaign 런던 등).

하지만 Facebook에서 사용하는 대상 필터를 사용할 수도 있습니다. 다음 **[!UICONTROL Audience]** 의 탭 **[!UICONTROL Select target window]** 에서는 네 가지 필터를 제공합니다.

* **[!UICONTROL Country]**
* **[!UICONTROL Regions]**
* **[!UICONTROL Cities]**
* **[!UICONTROL Languages]**

>[!CAUTION]
>
>이 기능은 주의해서 사용하십시오. 게재 보고서에서 **[!UICONTROL Number of fans]** 표시기에는 이러한 Facebook 필터가 고려되지 않습니다.
>
>Facebook은 대상 필터 목록과 해당 값을 변경할 수 있습니다.

## 메시지 콘텐츠 정의 {#defining-message-content}

을(를) 사용하여 게시 유형을 선택합니다 **[!UICONTROL Content type]** 드롭다운 메뉴

![](assets/social_facebook_delivery_006.png)

다음 유형의 게재를 사용할 수 있습니다.

* a **[!UICONTROL Status]**
* a **[!UICONTROL Status with a link]**
* a **[!UICONTROL Status with a YouTube link]**
* a **[!UICONTROL Photo album]**

### 상태 게시 {#publishing-a-status}

상태 유형 게재에는 아래 예와 같이 텍스트만 포함될 수 있습니다.

![](assets/social_create_facebook_wall_post_004.png)

입력 영역에 게시 상태를 입력합니다.

![](assets/social_facebook_delivery_015.png)

### 링크가 있는 상태 게시 {#publishing-a-status-with-a-link}

링크가 있는 상태 유형 전달에는 텍스트, 이미지 및 링크가 포함될 수 있습니다. 다음 섹션에서는 게재 편집 화면의 필드와 Facebook에 게시된 최종 게시물 간의 대칭 구조에 대해 자세히 설명합니다.

![](assets/social_facebook_delivery_007.png)

다양한 필드를 입력합니다.

>[!CAUTION]
>
>모든 URL은 **&quot;http://&quot;** 또는 **&quot;https://&quot;**.

1. 에서 **[!UICONTROL Status]** 필드에서 페이지 이름 아래에 표시할 텍스트를 입력합니다.
1. 에서 **[!UICONTROL Name]** 필드에서 발행물 제목을 입력합니다.
1. 에서 **[!UICONTROL Link]** 필드에서 게시가 가리키는 URL을 입력합니다.

   >[!NOTE]
   >
   >를 추가하려면 **[!UICONTROL Link]** 필드를 Facebook 애플리케이션 URL에 추가하여 홍보하는 것이 좋습니다.
   >
   >1. facebook 애플리케이션을 선택합니다 [https://developers.facebook.com/apps](https://developers.facebook.com/apps), 을(를) 선택하고 을(를) 선택합니다. **[!UICONTROL Settings > Basic]** 탭.
   >1. 을(를) 입력합니다. **[!UICONTROL Namespace]** 필드.
   >1. 을(를) 입력합니다. **[!UICONTROL Mobile Site URL]** 필드: 사용자가 스마트폰에서 게시 링크를 클릭하면 Facebook에 의해 이 필드에 정의된 URL로 자동으로 리디렉션됩니다.
   >1. facebook 디스플레이이 사용되는 장치(스마트폰 또는 PC)의 기능으로 개인화되도록 웹 애플리케이션을 만듭니다.
   >1. 로 이동합니다. **[!UICONTROL Link]** Adobe Campaign 콘솔을 통해 게시에 있는 필드에서 **[!UICONTROL Canvas page]** 필드.


1. 에서 **[!UICONTROL Image]** 필드에서 게시 왼쪽에 표시될 이미지의 URL을 입력합니다.

   >[!CAUTION]
   >
   >facebook에서 이미지를 업로드하려면 공개 인터넷 사이트에서 이미지를 호스팅해야 합니다.

1. 에서 **[!UICONTROL Caption]** 필드에서 게시 끝에 나타나는 텍스트를 입력합니다.
1. 로 이동합니다. **[!UICONTROL Description]** 필드를 입력하고 제목 아래에 표시할 텍스트를 입력합니다.

![](assets/social_facebook_delivery_005.png)

### YouTube 링크가 있는 상태 게시 {#publishing-a-status-with-a-youtube-link}

이 유형의 컨텐츠를 사용하면 YouTube 비디오에 대한 링크를 게시할 수 있습니다. 일반 링크가 있는 상태처럼 상태, 이름, 캡션, 설명 및 추가 링크를 정의할 수 있습니다. 이 이미지는 Facebook에 의해 자동으로 추가됩니다. 게재 편집 화면의 필드와 Facebook의 최종 게시 간의 대칭은 아래에 자세히 설명되어 있습니다.

![](assets/social_facebook_delivery_youtube_1.png)

다양한 필드를 입력합니다.

>[!CAUTION]
>
>모든 URL은 **&quot;http://&quot;** 또는 **&quot;https://&quot;**.

1. 에서 **[!UICONTROL Status]** 필드에서 페이지 이름 아래에 표시할 텍스트를 입력합니다.
1. 에서 **[!UICONTROL Name]** 필드에서 발행물 제목을 입력합니다.
1. 에서 **[!UICONTROL Video code]** 필드에 YouTube 비디오의 코드를 입력합니다. 예를 들어 &#39;https://www.youtube.com/watch?v=abc123456&#39;&#39; 링크의 경우 비디오 코드는 &#39;abc123456&#39;입니다.
1. 에서 **[!UICONTROL Caption]** 필드에서 게시 끝에 나타나는 텍스트를 입력합니다.
1. 로 이동합니다. **[!UICONTROL Description]** 필드를 입력하고 제목 아래에 표시할 텍스트를 입력합니다.

![](assets/social_facebook_delivery_youtube.png)

### 사진 앨범 게시 {#publishing-a-photo-album}

이 유형의 콘텐츠를 사용하면 사진 앨범을 게시할 수 있습니다. 각 사진에 대한 캡션과 앨범의 이름 및 설명을 추가할 수 있습니다. 게재 편집 화면의 필드와 Facebook의 최종 게시 간의 대칭은 아래에 자세히 설명되어 있습니다.

![](assets/social_facebook_delivery_photos_1.png)

다양한 필드를 입력합니다.

1. 을 입력하여 시작합니다. **[!UICONTROL Album name]**.
1. 그런 다음 **[!UICONTROL Description]** 사진 위에 표시되도록 합니다.
1. 사진을 추가하려면 **[!UICONTROL Add]** 버튼을 클릭하고 사진을 선택한 다음 를 클릭합니다 **[!UICONTROL Open]**.
1. 캡션을 각 사진에 추가할 수 있습니다.

![](assets/social_facebook_delivery_photos.png)

## 미리 보기 {#previewing}

다음 **[!UICONTROL Preview]** 탭에서는 게시의 렌더링을 볼 수 있습니다.

1. 을(를) 클릭합니다. **[!UICONTROL Preview]** 탭.
1. 을(를) 클릭합니다. **[!UICONTROL Test personalization]** 드롭다운 메뉴를 선택하고 **[!UICONTROL Service]**.
1. 에서 **[!UICONTROL Folder]** 필드에서 Facebook 페이지가 포함된 서비스 폴더를 선택합니다. 기본적으로 페이지는 의 루트에 저장됩니다 **[!UICONTROL Facebook]** 서비스 폴더.
1. 미리 보기를 테스트할 Facebook 페이지를 선택합니다.

![](assets/social_facebook_delivery_008.png)

>[!NOTE]
>
>미리 보기는 최종 Facebook 게시물과 약간 다를 수 있습니다. 게시의 정확한 렌더링을 위해 최종 게재 전에 증명을 보내는 것이 좋습니다. [자세히 알아보기](#sending-the-proof)

## 추적 구성 {#configuring-tracking}

추적은 게재 보고서와 **[!UICONTROL Edit > Tracking]** 게재 및 서비스의 탭입니다.

게재에 포함된 URL에 대한 클릭은 Adobe Campaign에서 측정합니다. 클릭 수 **[!UICONTROL Like]** 버튼, 댓글 수 및 팬 수는 Facebook에 의해 측정됩니다.

추적 구성은 이메일 게재와 동일합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../delivery/using/about-delivery-monitoring.md)을 참조하십시오.

>[!NOTE]
>
>에서 **[!UICONTROL Publish to a brand page]** 게재 템플릿, 추적은 기본적으로 활성화되어 있습니다.

## 증명 보내기 {#sending-the-proof}

개인 Facebook 테스트 페이지에서 발행물의 정확한 렌더링을 보려면 최종 게재 전에 게시 증명을 보내는 것이 좋습니다. 비공개 Facebook 테스트 페이지 만들기에 대한 자세한 내용은 [이 페이지](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page). 대상 증명을 선택하는 단계는 [이 섹션](#selecting-the-proof-target).

증명 게재는 이메일 게재와 동일합니다. [이 섹션](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)을 참조하십시오.

## 메시지 보내기 {#sending-the-message}

1. 컨텐츠가 승인되면 **[!UICONTROL Send]** 버튼을 클릭합니다.
1. 선택 **[!UICONTROL Deliver as soon as possible]** 을 클릭하고 **[!UICONTROL Analyze]** 버튼을 클릭합니다.

   >[!NOTE]
   >
   >다음 **[!UICONTROL Postpone the delivery]** 옵션을 사용하면 게재를 나중 날짜로 연기할 수 있습니다.

   ![](assets/social_facebook_delivery_009.png)

1. 분석이 완료되면 결과를 확인합니다.
1. 클릭 **[!UICONTROL Confirm delivery]**&#x200B;를 클릭한 다음 **[!UICONTROL Yes]**.

   ![](assets/social_facebook_delivery_016.png)
