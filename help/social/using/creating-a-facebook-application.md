---
product: campaign
title: Facebook 애플리케이션 만들기
description: Facebook 애플리케이션 만들기
audience: social
content-type: reference
topic-tags: configuration
exl-id: 5c11bd0f-2df7-4c7f-b682-955fedf8e664
source-git-commit: d891a235002d465f3b00fafa375d87d42ebafaa6
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 5%

---

# Facebook 애플리케이션 만들기{#creating-a-facebook-application}

![](../../assets/v7-only.svg)

Campaign Social 마케팅 모듈은 웹 애플리케이션을 사용하여 Facebook 애플리케이션에 개인화된 컨텐츠를 표시할 수 있도록 하므로, 이 소셜 미디어를 통해 잠재 고객을 더 쉽게 확보할 수 있습니다. facebook 유형 웹 애플리케이션의 자세한 예는 다음을 참조하십시오 [이 페이지](../../social/using/examples-of-facebook-apps.md).

>[!NOTE]
>
>파트너가 개발한 Facebook 애플리케이션과 Adobe Campaign을 통합할 수도 있습니다. 이 경우 Adobe Campaign 웹 애플리케이션을 사용하여 Facebook 프로필을 획득할 필요가 없습니다. [자세히 알아보기](#configuring-external-accounts)

![](assets/social_webapp_fb_000.png)

구성 단계는 다음과 같습니다.

1. 하나 이상의 Facebook 애플리케이션을 만듭니다.
1. 을(를) 입력합니다. **[!UICONTROL terms of service]** 및 **[!UICONTROL Privacy policy]** facebook 권한 요청 화면에 표시되는 링크입니다. [자세히 알아보기](#entering-the-terms-of-service-and-privacy-policy-links)
1. 각 Facebook 응용 프로그램에 대해 **[!UICONTROL Facebook Connect]** 외부 계정을 입력합니다. [자세히 알아보기](#configuring-external-accounts)
1. 각 Facebook 애플리케이션에 대해 Adobe Campaign에서 Facebook 유형 웹 애플리케이션을 만듭니다. [자세히 알아보기](#creating-a-facebook-type-web-application)
1. facebook 애플리케이션이 Facebook 페이지에서 탭으로 표시되도록 구성합니다. [자세히 알아보기](#configuring-facebook-tabs)

## 외부 계정 구성 {#configuring-external-accounts}

각 Facebook 애플리케이션에 대해 **[!UICONTROL Facebook Connect]** 외부 계정을 입력합니다.

이 단계에는 Adobe Campaign 콘솔 및 Facebook 관리자 계정에 액세스해야 합니다.

* 설정 **Facebook**: 앞에서 만든 응용 프로그램 선택( [https://developers.facebook.com/apps](https://developers.facebook.com/apps))을 클릭하고 **[!UICONTROL Settings]** > **[!UICONTROL Basic]** 탭.

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >만약 **[!UICONTROL Facebook Web Games]** 섹션이 나타나지 않으면 **[!UICONTROL Add Platform]** 단추 를 클릭하고 페이지 하단에서 을 선택합니다. **[!UICONTROL Facebook Web Games]**.

* 설정 **Adobe Campaign**: 찾아보기 **[!UICONTROL Administration > Platform > External accounts]** 을(를) 클릭합니다. **[!UICONTROL New]**.

   ![](assets/social_webapp_fb_005.png)

1. 레이블과 내부 이름을 입력하고 **[!UICONTROL Facebook Connect]** 유형.

   ![](assets/social_webapp_fb_006.png)

1. 애플리케이션 호스팅 모드를 선택합니다. **[!UICONTROL hosted by a partner]** 또는 **[!UICONTROL hosted by this instance]**.

   ![](assets/social_webapp_fb_012.png)

   **파트너가 호스팅하는 애플리케이션**

   파트너가 개발한 Facebook 애플리케이션과 Adobe Campaign을 통합할 수 있습니다. 이 경우 Adobe Campaign 웹 애플리케이션을 사용하여 Facebook 프로필을 획득할 필요가 없습니다. facebook 사용자가 애플리케이션을 설치하면 키(액세스 토큰)가 생성됩니다. 파트너는 웹 서비스를 호출하여 이 액세스 토큰을 Adobe Campaign에 전달합니다. 그런 다음 Adobe Campaign은 이 토큰을 사용하여 Facebook 데이터베이스에 로그온하고 애플리케이션을 통해 사용자가 공유한 데이터를 수집합니다.

   >[!NOTE]
   >
   >웹 서비스의 매개 변수는 여기에서 사용할 수 있는 WSDL 파일에 자세히 설명되어 있습니다. **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   타사 애플리케이션을 Adobe Campaign에 통합하려면 의 컨텐츠를 복사해야 합니다 **[!UICONTROL App ID]** 및 **[!UICONTROL App Secret]** Facebook 필드에 붙여 넣습니다. **[!UICONTROL Application ID]** 및 **[!UICONTROL Application secret]** 콘솔의 필드입니다.

   ![](assets/social_facebook_external_account_013.png)

   **이 인스턴스에 의해 호스팅되는 응용 프로그램**

   이 인스턴스에서 애플리케이션을 호스팅하려면(타사 애플리케이션이 없는 경우) Adobe Campaign 웹 애플리케이션을 사용하여 Facebook 프로필을 가져와야 합니다. 자세한 정보는 이 [페이지](../../social/using/examples-of-facebook-apps.md)를 참조하십시오.

   Adobe Campaign 콘솔에서 **[!UICONTROL Secure Canvas URL]** 필드에 붙여 넣습니다. **[!UICONTROL Facebook Web games (https)]** facebook의 필드(에서) **[!UICONTROL Facebook Web Games]** 섹션).

   ![](assets/social_facebook_external_account_009.png)

   >[!CAUTION]
   >
   >비보안 URL을 사용하지 마십시오.

   facebook에서 **[!UICONTROL App ID]** 및 **[!UICONTROL App Secret]** 필드에 붙여 넣습니다. **[!UICONTROL Application ID]** 및 **[!UICONTROL Application secret]** 콘솔의 필드.

   ![](assets/social_facebook_external_account_008.png)

1. facebook에서 **[!UICONTROL Save Changes]** 단추 를 클릭합니다.
1. Adobe Campaign 콘솔에서 **[!UICONTROL Subscribe]** 버튼을 클릭하여 Adobe Campaign에서 팬이 이 애플리케이션을 통해 체크인할 때마다 데이터를 실시간으로 복구할 수 있습니다.  [자세히 알아보기](../../social/using/examples-of-facebook-apps.md)

   ![](assets/social_webapp_fb_013.png)

## 서비스 약관 및 개인 정보 보호 정책 링크를 입력합니다 {#entering-the-terms-of-service-and-privacy-policy-links}

를 추가하는 것이 좋습니다 **[!UICONTROL Terms of service]** 및 **[!UICONTROL Privacy policy]** facebook 권한 요청 화면에 표시되는 링크입니다.

![](assets/social_fb_terms_of_services_001.png)

구성 단계는 다음과 같습니다.

1. 다음 주소를 입력합니다. [https://developers.facebook.com/apps](https://developers.facebook.com/apps)그런 다음 Facebook 애플리케이션을 선택합니다.
1. 을(를) 선택합니다 **[!UICONTROL Settings > Basic]** 탭을 선택하고 를 입력합니다 **[!UICONTROL Privacy Policy URL]** 및 **[!UICONTROL Terms of Service URL]** 필드.

   ![](assets/social_fb_terms_of_services.png)

## facebook 유형 웹 애플리케이션 만들기 {#creating-a-facebook-type-web-application}

Adobe Campaign Facebook 애플리케이션을 사용하면 Facebook 애플리케이션에서 개인화된 컨텐츠를 표시할 수 있습니다. 각 Facebook 애플리케이션의 경우 Adobe Campaign에서 웹 애플리케이션을 만들어야 합니다. facebook 웹 애플리케이션을 만들려면 다음과 같이 진행합니다.

1. 로 이동합니다. **[!UICONTROL Social networks]** 탭에서 **[!UICONTROL Applications]** 링크를 클릭한 다음 **[!UICONTROL Create]** 버튼을 클릭합니다.

   ![](assets/social_webapp_001.png)

1. 목록에서 Facebook 웹 애플리케이션 템플릿을 선택하고 레이블을 입력합니다.

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >기본적으로 제공되는 4개의 Facebook 웹 애플리케이션 템플릿은 다음과 같습니다.
   >
   >* **[!UICONTROL New Facebook application]**: 빈 응용 프로그램에서 시작하려면 이 템플릿을 선택합니다.
   >* **[!UICONTROL Pre-entered form]**: 사용자가 프로필의 데이터를 사용하여 양식 필드를 자동으로 채울 수 있는 &quot;Facebook 로그인&quot; 단추가 있는 facebook 애플리케이션입니다. 이를 통해 사용자는 양식을 보다 신속하게 완료하고 브랜드가 더 나은 품질 정보를 얻을 수 있습니다.
   >* **[!UICONTROL "Canvas page" competition]**: 사용자에게 더 나은 시각적 경험을 위해 화면에 표시되는 facebook 애플리케이션입니다.
   >* **[!UICONTROL "Page Tab" competition]**: Facebook 애플리케이션은 브랜드 페이지 탭에 완전히 통합됩니다.


1. 에서 **[!UICONTROL Application]** 필드에서 Facebook 애플리케이션에 연결된 외부 계정을 입력합니다. [자세히 알아보기](#configuring-external-accounts)

   ![](assets/social_webapp_005.png)

1. 을(를) 선택합니다 **[!UICONTROL Edit]** 탭을 클릭한 다음 웹 애플리케이션을 편집합니다. [자세히 알아보기](../../social/using/examples-of-facebook-apps.md)

   ![](assets/social_webapp_003.png)

1. 웹 응용 프로그램이 완료되면 **[!UICONTROL Dashboard]** 탭을 클릭한 다음 **[!UICONTROL Publish]** 온라인으로 게시하려면 다음을 수행하십시오.

   ![](assets/social_webapp_004.png)

## facebook 탭 구성 {#configuring-facebook-tabs}

facebook 페이지에 탭으로 표시되도록 Facebook 애플리케이션을 구성할 수 있습니다. 그렇게 하려면 다음 단계를 적용합니다.

1. facebook 애플리케이션 선택([https://developers.facebook.com/apps](https://developers.facebook.com/apps))을 클릭하고 **[!UICONTROL Settings > Basic]** 탭.

   ![](assets/social_webapp_fb_008.png)

1. 페이지 하단에서 **[!UICONTROL Add Platform]** 단추를 클릭하고 **[!UICONTROL Page Tab]**.

   ![](assets/social_webapp_fb_008bis.png)

1. 에서 **[!UICONTROL Page Tab Name]** 필드 **[!UICONTROL Page Tab]** 섹션에서 Facebook 페이지에 표시할 레이블을 입력합니다.

   ![](assets/social_webapp_fb_001.png)

1. 에서 **[!UICONTROL Secure Page Tab URL]** 필드에서는 웹 응용 프로그램의 공개 URL을 입력하고, 이 URL은 **[!UICONTROL Dashboard]** 웹 응용 프로그램의 탭입니다. facebook 유형 웹 애플리케이션 만들기에 대한 자세한 내용은 [이 섹션](#creating-a-facebook-type-web-application).

   ![](assets/social_webapp_fb_002.png)

1. 설정 **[!UICONTROL Dashboard]** 웹 응용 프로그램에서 **[!UICONTROL Add a page tab]** 링크를 클릭합니다.

   ![](assets/social_webapp_fb_0010.png)

1. 탭을 추가할 Facebook 페이지를 선택하고 **[!UICONTROL Add Page Tab]**.

   ![](assets/social_webapp_fb_0011.png)
